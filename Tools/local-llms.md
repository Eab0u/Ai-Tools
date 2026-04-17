# Running LLMs Locally

## What It Is
Running LLMs locally means downloading and running AI language models directly on your own machine — no API calls, no cost per token, no internet required after setup. Two main tools for this are Ollama and Docker Model Runner.

## Cost Profile
- **Both tools**: Free and open source
- **No per-token costs**: Unlike OpenAI or Anthropic APIs
- **Hardware dependent**: Larger models require more RAM and ideally a GPU

## Speed
- No network latency — responses come from your own machine
- Speed depends on model size and your hardware specs
- GPU dramatically improves performance but is not required for smaller models

## Best For
- Projects involving sensitive data that cannot be sent to external APIs
- Replacing OpenAI/Anthropic API calls with a free local alternative
- Prototyping and testing AI features without incurring API costs
- Containerized applications that need an embedded AI model

## Not Ideal For
- Tasks requiring frontier model quality (use Claude Opus or GPT-4 for that)
- Very large models on machines with limited RAM
- Production apps where reliability and quality are critical

## Key Concept: Quantization
Models are compressed using quantization — reducing the precision of model weights so they run on normal hardware. You lose a little quality but the model becomes dramatically smaller. A rough rule: you need about as much free RAM as the model file size (e.g. a 8GB model needs ~8GB free RAM).

---

## Method 1: Ollama

### What It Is
Ollama is the most popular tool for downloading and running open source models locally. It exposes a REST API on your machine that your code can call just like any other API.

### How To Install
1. Go to ollama.com and download for your OS
2. Open Ollama (check system tray on Windows to confirm it's running)
3. Verify in terminal: `ollama`

### Key Commands
```bash
ollama pull <model-name>     # download a model
ollama run <model-name>      # run model interactively in terminal
ollama ls                    # list all downloaded models
/bye                         # exit interactive mode
```

### Using Ollama From Code (Python)

**Option 1: Direct HTTP request**
```python
import requests

response = requests.post("http://localhost:11434/api/chat", json={
    "model": "smallm2:135m",
    "stream": False,
    "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Write 500 words about the fall of Rome."}
    ]
})

print(response.json()["message"]["content"])
```

**Option 2: Ollama Python module**
```bash
pip install ollama
```
```python
import ollama

response = ollama.chat(
    model="smallm2:135m",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Write 500 words about the fall of Rome."}
    ]
)

print(response["message"]["content"])
```

- Ollama runs on port **11434** by default
- System messages give the model context and instructions
- User messages are what the model directly responds to

---

## Method 2: Docker Model Runner

### What It Is
Docker Model Runner is a newer, more optimized way to run local LLMs built directly into Docker Desktop. It is generally preferred over Ollama — better GPU support, works inside containerized applications, and integrates naturally with Docker Compose for deployment.

### How To Set Up
1. Install Docker Desktop (free at docker.com)
2. Open Docker Desktop > Settings > AI
3. Enable Docker Model Runner
4. Enable host-side TCP support
5. Set cores to "All"
6. If settings not visible: go to Beta Features and enable Docker MCP Toolkit first

### Pulling and Running Models
**Via UI**: Docker Desktop > Models > Docker Hub > search > Download > Run

**Via terminal:**
```bash
docker model pull <model-name>    # download a model
docker model run <model-name>     # run interactively
docker model list                 # list local models
/bye                              # exit interactive mode
```

### Using Docker Model Runner From Code

**Option 1: Direct HTTP request**
```python
# Same as Ollama but port 12434 instead of 11434
response = requests.post("http://localhost:12434/engines/llama.cpp/v1/chat/completions", json={
    "model": "ai/smallm2",
    "messages": [
        {"role": "user", "content": "Explain how transformers work."}
    ]
})
```

**Option 2: OpenAI module with overridden base URL**
```python
from openai import OpenAI

client = OpenAI(base_url="http://localhost:12434/engines/llama.cpp/v1", api_key="none")

response = client.chat.completions.create(
    model="ai/smallm2",
    messages=[{"role": "user", "content": "Explain how transformers work."}]
)

print(response.choices[0].message.content)
```

- Docker Model Runner runs on port **12434**
- You can use the OpenAI Python module and just redirect it to your local machine instead of OpenAI's servers
- Models are referenced as `ai/<model-name>` in Docker Model Runner

---

## Ollama vs Docker Model Runner

| | Ollama | Docker Model Runner |
|---|---|---|
| Ease of setup | Very easy | Easy (requires Docker Desktop) |
| GPU support | Good | Better |
| Works in containers | No | Yes |
| UI | Terminal only | Terminal + Docker Desktop GUI |
| Port | 11434 | 12434 |
| Best for | Quick local testing | Containerized apps, deployment |

## Where It Fits in the Stack

- **Replacing OpenAI/Anthropic API**: Point your existing API calls at localhost instead — same code, zero cost
- **Docker Compose**: Docker Model Runner can be defined as a service in your compose file alongside your backend and database
- **Sensitive data projects**: Everything stays on your machine, nothing leaves
- **Claude Code + Anti-Gravity**: Use as a free inference backend when Claude tokens run out on low-stakes tasks

## Tips
- Start with a small model (under 1GB) to test your setup before downloading larger ones
- Check ChatGPT or Claude with your machine specs to find out which model sizes you can run
- Docker Model Runner is preferred for any project you plan to deploy or containerize
- The OpenAI module redirect trick means you can swap between local and cloud models by just changing one URL
- Models are found at ollama.com/search (Ollama) or hub.docker.com (Docker Model Runner)
