# Docker

## What It Is
Docker is a tool that packages your code, dependencies, and environment settings into a portable "container" that runs the same way on any machine. It solves the classic "works on my machine" problem by ensuring everyone runs the exact same environment.

## Cost Profile
- **Docker Desktop**: Free for personal use
- **Docker Build Cloud**: Paid, for teams needing faster build times (up to 39x faster)
- No ongoing API costs — everything runs locally
- Docker Hub (image registry): Free tier available

## Speed
- Container startup: near-instant once image is built
- Image build: moderate, depends on project size
- Layer caching: dramatically speeds up rebuilds (unchanged layers are skipped)
- Docker Build Cloud: up to 39x faster builds for complex projects, shared cache across team

## Best For
- Ensuring consistent environments across dev, staging, and production
- Onboarding teammates without "install everything manually" setup
- Running multiple services (backend, database, frontend) together via Docker Compose
- Any project that will be deployed to a server or cloud environment
- Internship/team projects where your code needs to run on other people's machines

## Not Ideal For
- Simple scripts with no dependencies that run anywhere anyway
- Projects where a local install is genuinely simpler and there's no deployment target

## Key Concepts

### Images vs Containers
- **Image**: The recipe. Contains everything needed to run your code (runtime, dependencies, config). Built once, reused many times.
- **Container**: The actual running meal made from that recipe. One image can spin up multiple containers.
- **Dockerfile**: The file where you write the recipe (instructions to build the image).

### Layer Caching
Every step in your Dockerfile is a layer. Docker checks if a layer changed:
- Layer unchanged: use cache, skip it
- Layer changed: redo it and everything after it

This is why you copy `package.json` and run `npm install` BEFORE copying your actual code. Your dependencies don't change every time you edit code, so Docker caches that layer and skips reinstalling every build.

### Dockerfile Keywords
| Keyword | What It Does |
|---|---|
| `FROM` | Sets the base image to start from (e.g. `node:22`) |
| `WORKDIR` | Sets the working directory inside the container |
| `COPY` | Copies files from your machine into the image |
| `RUN` | Runs a command during the image build step |
| `CMD` | The command that starts the container (runs at container launch, not build) |
| `ENV` | Sets environment variables |
| `EXPOSE` | Declares which port the container listens on |

### .dockerignore
Works like `.gitignore`. Prevents unnecessary files from being copied into your image. Always add `node_modules` here — it's large and gets reinstalled inside the container anyway.

## How To Install

1. Go to docker.com and download Docker Desktop for your OS
2. Install and open Docker Desktop
3. Verify in terminal: `docker --version`
4. Install the Docker extension in VS Code (language support, autocomplete, GUI for containers)

## Step-By-Step: Dockerize a Node App

### Step 1: Create the Dockerfile
```dockerfile
FROM node:22

WORKDIR /app

# Copy package files first (layer caching optimization)
COPY package*.json ./
RUN npm install

# Copy the rest of the code
COPY . .

ENV PORT=3000
EXPOSE 3000

CMD ["npm", "start"]
```

### Step 2: Create .dockerignore
```
node_modules
.env
.git
```

### Step 3: Build the Image
```bash
docker build -t my-app-name .
# -t = tag (name for your image)
# . = look for Dockerfile in current directory
```

### Step 4: Run the Container
```bash
docker run -p 3000:3000 my-app-name
# -p = port forwarding: left is your machine, right is the container
```

### Step 5: Debug
- Open Docker Desktop, find your running container (green dot), click it
- View logs, run terminal commands, check resource usage
- Or in terminal: `docker exec -it <container-id> bash`

## Docker Compose (Multiple Services)

When your app has a backend + database + frontend, each gets its own container. Docker Compose manages them all together.

### docker-compose.yml Example
```yaml
services:
  backend:
    build: .
    ports:
      - "3000:3000"

  database:
    image: postgres
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

### Key Compose Commands
```bash
docker compose up      # start all containers
docker compose down    # stop and remove all containers
docker compose logs    # view logs across all services
```

### Volumes
Containers lose all data when stopped. Volumes are folders on your machine that Docker mounts into the container so data persists across restarts and can be shared between containers.

## Docker Scout (Security Scanning)

Docker's built-in vulnerability scanner. Analyzes packages inside your image and flags known security issues.

```bash
docker scout quickview my-app-name
```

Or in Docker Desktop: Images > click your image > Vulnerabilities tab > Start Analysis.

## Key Commands Reference

```bash
# Images
docker build -t <name> .        # build image from Dockerfile
docker images                   # list all images
docker rmi <image-id>           # delete an image

# Containers
docker run -p 3000:3000 <name>  # run a container
docker ps                       # list running containers
docker ps -a                    # list all containers (including stopped)
docker stop <container-id>      # stop a container
docker rm <container-id>        # delete a container
docker logs <container-id>      # view container logs
docker exec -it <id> bash       # open terminal inside container

# Compose
docker compose up               # start all services
docker compose down             # stop all services
docker compose up --build       # rebuild images then start
```

## Where It Fits in the Stack

Docker is infrastructure, not a build tool. It sits underneath everything else:
- **Claude Code + Anti-Gravity**: Claude can write your Dockerfile and docker-compose.yml
- **GitHub Actions (CI/CD)**: CI pipelines often build and test Docker images automatically on every push
- **Vercel**: Handles its own containerization for Next.js, so Docker is less relevant there
- **Any backend deployment** (AWS, Railway, Render, DigitalOcean): Docker is the standard way to ship your app

## Tips
- Always set up `.dockerignore` before building — copying `node_modules` into an image is a common beginner mistake
- Copy `package.json` and run `npm install` before `COPY . .` to maximize layer cache hits
- Use `CMD` not `RUN` to start your server — `RUN` happens at build time, `CMD` happens at container launch
- Docker Desktop's GUI is the easiest way to debug logs and check running containers
- For team projects: if your teammate can run `docker compose up` and the app just works, you've done it right
