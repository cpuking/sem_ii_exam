# ⚙️ DevOps Notes

**Marks:** 30 | **Priority:** 🟡 MEDIUM  
**Related:** [[DevOps PYQ]] | [[DevOps QB]] | [[README]]

---

## 📌 Table of Contents

1. [[#Unit 1 – DevOps Fundamentals]]
2. [[#Unit 2 – Linux Basics]]
3. [[#Unit 3 – Git and Version Control]]
4. [[#Unit 4 – Docker]]
5. [[#Unit 5 – CI CD and Automation]]
6. [[#Unit 6 – Infrastructure as Code Terraform]]
7. [[#🔥 Most Expected Questions]]

---

## Unit 1 – DevOps Fundamentals

### 1.1 What is DevOps? (⭐ IMPORTANT)

**Definition:**  
DevOps is a **set of practices, tools, and cultural philosophies** that automates and integrates the processes between **software development (Dev)** and **IT operations (Ops)** teams, enabling organizations to deliver applications and services faster and more reliably.

**Key goals:**
- Faster software delivery
- Better collaboration between teams
- Higher deployment frequency
- Faster recovery from failures
- Continuous improvement

---

### 1.2 DevOps Lifecycle (⭐ VERY IMPORTANT)

The DevOps lifecycle is a continuous loop of 8 phases:

```
     Plan → Code → Build → Test → Release → Deploy → Operate → Monitor
       ↑                                                              ↓
       └──────────────────── (feedback loop) ──────────────────────┘
```

| Phase | Description | Tools |
|---|---|---|
| **Plan** | Define requirements, project planning, task scheduling | Jira, Trello |
| **Code** | Write and review code | Git, VS Code, GitHub |
| **Build** | Compile code, run unit tests, generate artifacts | Maven, Gradle, npm |
| **Test** | Automated testing (unit, integration, load) | Selenium, JUnit, Postman |
| **Release** | Approve and prepare for deployment | Jenkins, GitLab CI |
| **Deploy** | Push to production/staging environments | Docker, Kubernetes, Ansible |
| **Operate** | Monitor and maintain running systems | Nagios, Prometheus |
| **Monitor** | Collect metrics, logs, feedback | Grafana, ELK Stack |

---

### 1.3 Waterfall vs Agile vs DevOps (⭐ IMPORTANT)

| Feature | Waterfall | Agile | DevOps |
|---|---|---|---|
| Development | Sequential | Iterative sprints | Continuous |
| Testing | End of project | Each sprint | Continuous automated |
| Deployment | Once, at end | End of sprint | Multiple times/day |
| Flexibility | Rigid | Flexible | Highly flexible |
| Collaboration | Siloed teams | Dev team | Dev + Ops unified |
| Feedback | Very late | After each sprint | Continuous |
| Risk | High (late discovery) | Medium | Low |

---

### 1.4 Advantages and Disadvantages of DevOps

**Advantages:**
- Faster software delivery
- Better team collaboration
- Higher quality software (continuous testing)
- Faster bug detection and resolution
- More reliable releases
- Better customer satisfaction

**Disadvantages:**
- Complex initial setup
- Requires skilled team (both Dev and Ops knowledge)
- Security concerns (more frequent deployments)
- High upfront investment in tooling
- Cultural shift is difficult

---

### 1.5 CI/CD (⭐ VERY IMPORTANT)

#### Continuous Integration (CI)
**Definition:**  
CI is the practice of **frequently merging code changes** into a shared repository, with each merge triggering **automated builds and tests**.

```
Developer commits code
        ↓
Trigger automated build
        ↓
Run automated tests
        ↓
If tests pass → code is integrated
If tests fail → developer is notified
```

**Benefits:**
- Detect bugs early
- Prevent "integration hell"
- Always have working code

#### Continuous Delivery (CD)
**Definition:**  
CD extends CI — after code passes all tests, it is **automatically prepared for release** to production. The deployment to production still requires **manual approval**.

#### Continuous Deployment
**Definition:**  
Goes one step further — every change that passes automated tests is **automatically deployed to production** with NO manual step.

| | CI | Continuous Delivery | Continuous Deployment |
|---|---|---|---|
| Build automated | ✅ | ✅ | ✅ |
| Test automated | ✅ | ✅ | ✅ |
| Release to staging | Manual/Auto | Automatic | Automatic |
| Release to production | Manual | Manual approval | Automatic |

**CI/CD Tools:**
- **Jenkins** – open-source automation server
- **GitLab CI/CD** – built into GitLab
- **GitHub Actions** – built into GitHub
- **CircleCI**, **Travis CI**

---

## Unit 2 – Linux Basics

### 2.1 What is Linux?

**Definition:**  
Linux is an **open-source, Unix-like operating system kernel** first created by Linus Torvalds in 1991. A Linux distribution (distro) is the kernel + additional software.

**Popular Linux distributions:**

| Distribution | Based on | Package manager | Used for |
|---|---|---|---|
| Ubuntu | Debian | apt | General purpose, beginners |
| Debian | – | apt | Stable servers |
| Fedora | Red Hat | dnf | Developers |
| CentOS / RHEL | Red Hat | yum / dnf | Enterprise servers |
| Arch Linux | – | pacman | Advanced users |
| Kali Linux | Debian | apt | Security/hacking |

---

### 2.2 Advantages of Linux

- **Open source** – free to use and modify
- **Secure** – fewer viruses, strong permissions
- **Stable** – rarely crashes
- **Customizable** – modify anything
- **Multi-user** – many users can use simultaneously
- **Performance** – efficient resource usage
- **Command line power** – automate anything

---

### 2.3 Linux Directory Structure (⭐ IMPORTANT)

Linux uses a hierarchical file system starting from `/` (root).

| Directory | Purpose |
|---|---|
| `/` | Root of the entire file system |
| `/bin` | Essential user binaries (ls, cp, cat) |
| `/sbin` | System binaries (shutdown, fdisk) |
| `/etc` | Configuration files |
| `/home` | User home directories (`/home/harsh`) |
| `/var` | Variable data – logs, databases, spool files |
| `/tmp` | Temporary files (cleared on reboot) |
| `/usr` | User-installed programs and data |
| `/lib` | Shared system libraries (like DLLs in Windows) |
| `/mnt` | Mount point for external drives/devices |
| `/dev` | Device files (hard disks, USB) |
| `/proc` | Virtual filesystem with process/system info |
| `/opt` | Optional third-party software |
| `/root` | Home directory for root user |

---

### 2.4 Linux: Everything is a File

**Definition:**  
In Linux, **everything is treated as a file** — not just documents, but also:
- Devices (`/dev/sda` = hard disk)
- Processes (`/proc/1234` = process with PID 1234)
- Network sockets
- Directories (special kind of file)

This unified design simplifies how programs interact with the system.

---

### 2.5 Important Linux Commands (⭐ IMPORTANT)

```bash
# File operations
ls -la              # list files with details
cd /home/harsh      # change directory
pwd                 # print current directory
mkdir mydir         # make directory
cp file1 file2      # copy file
mv file1 file2      # move/rename file
rm -rf folder/      # ⚠️ force delete folder and all contents
cat file.txt        # display file contents
touch file.txt      # create empty file

# System info
uptime              # how long system has been running
free -m             # memory usage in MB
df -h               # disk usage in human-readable format
top                 # real-time process monitor
ps aux              # list all running processes
cat /proc/uptime    # detailed uptime info (seconds)
uname -a            # system information

# Permissions
chmod 755 file.sh   # change permissions (rwxr-xr-x)
chown user:group f  # change file owner

# Package management
# Ubuntu/Debian
sudo apt update
sudo apt install nginx

# Fedora/CentOS
sudo yum install nginx
sudo dnf install nginx
```

---

### 2.6 Package Management: RPM vs Debian (⭐ IMPORTANT)

| Feature | RPM (Red Hat) | Debian |
|---|---|---|
| Distros | RHEL, CentOS, Fedora | Ubuntu, Debian, Mint |
| File format | `.rpm` | `.deb` |
| Package manager | `yum` (old), `dnf` (new) | `apt` |
| Install command | `yum install pkg` | `apt install pkg` |
| Remove command | `yum remove pkg` | `apt remove pkg` |
| Query command | `rpm -q pkg` | `dpkg -l pkg` |

---

### 2.7 Shell Scripting (⭐ VERY IMPORTANT – GUARANTEED)

**Shell script for system monitoring (logs every 5 minutes):**

```bash
#!/bin/bash
# System stats logger
# Logs: timestamp, uptime, memory, disk usage every 5 minutes

while true
do
    # Append stats to file
    echo "$(date) | $(uptime) | $(free -m | grep Mem) | $(df -h /)" >> stats.tsv
    
    # Sort by timestamp (newest first)
    sort -r stats.tsv -o stats.tsv
    
    # Wait 5 minutes (300 seconds)
    sleep 300
done
```

**Explanation of each part:**
- `#!/bin/bash` – shebang, tells OS to use bash interpreter
- `while true; do ... done` – infinite loop
- `$(date)` – current date and time
- `$(uptime)` – system uptime info
- `$(free -m)` – memory usage in MB
- `$(df -h /)` – disk usage of root partition
- `>> stats.tsv` – append (not overwrite) to TSV file
- `sort -r` – sort in reverse order
- `sleep 300` – pause for 5 minutes

**Simple hello world script:**
```bash
#!/bin/bash
echo "Hello, World!"
name="Harsh"
echo "Hello, $name!"

# If-else
if [ $name == "Harsh" ]; then
    echo "Welcome Harsh!"
else
    echo "Who are you?"
fi

# For loop
for i in 1 2 3 4 5; do
    echo "Number: $i"
done
```

---

## Unit 3 – Git and Version Control

### 3.1 What is Version Control? (⭐ IMPORTANT)

**Definition:**  
Version control is a system that **tracks changes to files over time**, allowing you to recall specific versions later, collaborate with others, and undo mistakes.

**Benefits:**
- Full history of every change
- Multiple people can work simultaneously
- Easy to undo mistakes
- Branching for parallel development
- Code backup

---

### 3.2 Git vs GitHub vs GitLab

| | Git | GitHub | GitLab |
|---|---|---|---|
| What is it? | Version control tool | Cloud platform for Git repos | Cloud platform for Git repos |
| Where does it run? | Locally on your machine | Cloud (Microsoft) | Cloud / Self-hosted |
| Free? | ✅ | ✅ (public repos) | ✅ |
| CI/CD built-in? | ❌ | ✅ GitHub Actions | ✅ GitLab CI/CD |
| Key feature | Core VCS | Pull Requests, Community | DevOps integration |

---

### 3.3 Core Git Commands (⭐ VERY IMPORTANT)

```bash
# Setup
git config --global user.name "Harsh"
git config --global user.email "harsh@example.com"

# Initialize
git init                  # create new repo
git clone <url>           # clone existing repo

# Basic workflow
git status                # see what's changed
git add file.txt          # stage specific file
git add .                 # stage all changes
git commit -m "message"   # commit staged changes
git log                   # view commit history
git log --oneline         # compact history

# Remote
git remote add origin <url>   # connect to remote
git push origin main           # push to remote
git pull origin main           # pull from remote
git fetch                       # download but don't merge

# Branching
git branch                  # list branches
git branch feature-login    # create new branch
git checkout feature-login  # switch to branch
git checkout -b new-branch  # create AND switch
git merge feature-login     # merge branch into current
git branch -d feature-login # delete branch

# Undoing
git diff                    # see unstaged changes
git restore file.txt        # discard unstaged changes
git reset HEAD file.txt     # unstage a file
git revert <commit-hash>    # undo a commit safely
```

---

### 3.4 Git Branching Workflow (⭐ IMPORTANT – DIAGRAM QUESTION)

**Typical workflow:**

```bash
# Start: you're on main branch

# C0 – initial commit
echo "<h1>Hello</h1>" >> README.md
git add .
git commit -m "C0: initial commit"

# C1 – add file
touch file.txt
git add .
git commit -m "C1: add file.txt"

# C2 – update file
echo "update content" >> file.txt
git add .
git commit -m "C2: update file.txt"

# Create feature branch
git branch issue53
git checkout issue53
# or in one step: git checkout -b issue53

# C3 – work on feature branch
touch index.html
echo "<h1>Feature page</h1>" >> index.html
git add .
git commit -m "C3: add index.html (issue53)"

# Push feature branch
git push origin issue53

# Merge back to main
git checkout main
git merge issue53

# Push main
git push origin main
```

---

### 3.5 Hotfix Branch (⭐ IMPORTANT)

**Definition:**  
A hotfix branch is a **short-lived branch** created directly from `main`/`master` to **fix urgent bugs in production** without waiting for the next planned release.

```bash
# Bug found in production!
git checkout main           # start from production code
git checkout -b hotfix/bug-fix-login  # create hotfix branch

# Fix the bug
# ... make changes ...
git add .
git commit -m "Fix: login authentication bug"

# Deploy hotfix
git checkout main
git merge hotfix/bug-fix-login
git push origin main

# Also merge into develop branch (so fix is not lost)
git checkout develop
git merge hotfix/bug-fix-login

# Delete hotfix branch
git branch -d hotfix/bug-fix-login
```

---

### 3.6 GitHub + VS Code Integration (⭐ IMPORTANT)

**Setup steps:**
1. Install **Git** from git-scm.com
2. Open VS Code → install **GitLens** extension (optional)
3. Sign into GitHub in VS Code
4. Configure identity:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```
5. Clone a repository:
   ```bash
   git clone https://github.com/user/repo.git
   ```
6. Open in VS Code: `code .`
7. Use Source Control panel (Ctrl+Shift+G) or terminal

---

## Unit 4 – Docker

### 4.1 What is Docker? (⭐ VERY IMPORTANT)

**Definition:**  
Docker is a **containerization platform** that packages an application and all its dependencies into a **container**, ensuring it runs **consistently** across different environments.

**Key analogy:**
- Without Docker: "It works on my machine" 😤
- With Docker: "It works everywhere" ✅

---

### 4.2 Docker Architecture

```
┌─────────────────────────────────────┐
│            Docker Host              │
│                                     │
│  ┌──────────────────────────────┐   │
│  │       Docker Daemon          │   │
│  └──────────────────────────────┘   │
│                                     │
│  ┌──────────┐  ┌──────────┐         │
│  │Container │  │Container │         │
│  │  App A   │  │  App B   │         │
│  └──────────┘  └──────────┘         │
│                                     │
│  ┌──────────────────────────────┐   │
│  │      Docker Images           │   │
│  └──────────────────────────────┘   │
└─────────────────────────────────────┘
```

**Key concepts:**
- **Image** – blueprint for a container (like a class)
- **Container** – running instance of an image (like an object)
- **Dockerfile** – text file with instructions to build an image
- **Docker Hub** – public registry for images
- **Docker Engine** – runtime that runs containers

---

### 4.3 Docker vs Virtual Machine

| Feature | Docker (Container) | Virtual Machine |
|---|---|---|
| Start time | Seconds | Minutes |
| Size | MBs | GBs |
| OS | Shares host OS kernel | Full OS per VM |
| Isolation | Process-level | Full machine-level |
| Performance | Near-native | Overhead |
| Portability | ✅ Very portable | ❌ Less portable |

---

### 4.4 Dockerfile (⭐ VERY IMPORTANT)

**Definition:**  
A Dockerfile is a **text file containing instructions** to build a Docker image.

**Dockerize a Node.js app:**

```dockerfile
# Use Node.js 18 as base image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package files first (for caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy rest of application code
COPY . .

# Expose port the app listens on
EXPOSE 3000

# Command to run when container starts
CMD ["node", "app.js"]
```

**Build and run:**
```bash
# Build image from Dockerfile
docker build -t my-node-app .

# Run container from image
docker run -p 3000:3000 my-node-app

# Run in background (detached mode)
docker run -d -p 3000:3000 --name my-app my-node-app
```

---

### 4.5 Docker Commands (⭐ VERY IMPORTANT)

```bash
# Images
docker pull nginx               # download image from Docker Hub
docker images                   # list local images
docker rmi nginx                # remove image
docker build -t myapp .         # build image from Dockerfile

# Containers
docker run nginx                # create and start container
docker run -d nginx             # run in background (detached)
docker run -d -p 8080:80 nginx  # map port host:container
docker run -it ubuntu bash      # interactive terminal
docker ps                       # list running containers
docker ps -a                    # list all containers (including stopped)
docker stop container-name      # stop container gracefully
docker kill container-name      # force stop container
docker rm container-name        # remove stopped container
docker rm -f container-name     # force remove running container

# Inspect
docker logs container-name      # view container logs
docker logs -f container-name   # follow logs in real-time
docker exec -it container bash  # open shell in running container
docker inspect container-name   # detailed container info

# Cleanup
docker system prune             # remove all unused resources
docker container prune          # remove all stopped containers
```

---

### 4.6 Docker Networking (⭐ IMPORTANT)

```bash
# Create a custom network
docker network create mongo-net

# List networks
docker network ls

# Run MongoDB on the network
docker run -d \
  --name mongo \
  --network mongo-net \
  mongo

# Run Mongo Express (GUI) on same network
docker run -d \
  --name mongo-express \
  --network mongo-net \
  -p 8081:8081 \
  -e ME_CONFIG_MONGODB_SERVER=mongo \
  mongo-express

# Now access Mongo Express at http://localhost:8081
```

**Why networking matters:**
- Containers on same network can communicate using **container names** (not IP addresses)
- Isolates container groups from each other
- Safer than exposing all ports

---

### 4.7 PostgreSQL with Docker (⭐ IMPORTANT)

```bash
# Pull PostgreSQL image
docker pull postgres

# Run PostgreSQL container (User 1)
docker run -d \
  --name postgres-user1 \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_PASSWORD=mypassword \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  postgres

# Connect to PostgreSQL via terminal
docker exec -it postgres-user1 psql -U myuser -d mydb

# Inside psql
CREATE TABLE users (id SERIAL PRIMARY KEY, name VARCHAR(100));
INSERT INTO users (name) VALUES ('Harsh');
SELECT * FROM users;
\q  # quit

# Stop and remove container
docker stop postgres-user1
docker rm postgres-user1

# Run second instance (User 2) on different port
docker run -d \
  --name postgres-user2 \
  -e POSTGRES_PASSWORD=pass2 \
  -p 5433:5432 \
  postgres
```

---

### 4.8 Docker Compose (⭐ IMPORTANT)

**Definition:**  
Docker Compose is a tool for **defining and running multi-container applications** using a single `docker-compose.yml` file.

**docker-compose.yml for MongoDB + Mongo Express:**

```yaml
version: '3.8'

services:
  # MongoDB database
  mongo:
    image: mongo
    container_name: mongodb
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    volumes:
      - mongo-data:/data/db   # persistent storage

  # MongoDB GUI
  mongo-express:
    image: mongo-express
    container_name: mongo-express
    ports:
      - "8081:8081"
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: password
      ME_CONFIG_MONGODB_SERVER: mongo  # use container name
    depends_on:
      - mongo  # start mongo first

volumes:
  mongo-data:  # named volume for persistence
```

**Docker Compose commands:**
```bash
docker-compose up          # start all services
docker-compose up -d       # start in background
docker-compose down        # stop and remove containers
docker-compose down -v     # also remove volumes
docker-compose logs        # view logs
docker-compose ps          # list running services
```

---

### 4.9 Orchestration (⭐ IMPORTANT)

**Definition:**  
Container orchestration **automates deployment, scaling, and management** of containerized applications across multiple hosts.

**Tools:**
- **Kubernetes (K8s)** – most popular, Google-developed
- **Docker Swarm** – simpler, built into Docker

**Why orchestration is needed:**
- Managing hundreds of containers manually is impossible
- Need to auto-restart failed containers
- Need to scale up/down based on traffic
- Load balancing across containers
- Rolling updates with zero downtime

---

## Unit 5 – CI/CD and Automation

### 5.1 Jenkins Pipeline

**Definition:**  
Jenkins is an **open-source automation server** used to build CI/CD pipelines.

**Basic Jenkinsfile:**
```groovy
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker build -t myapp .'
                sh 'docker push myapp'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
```

---

### 5.2 Ansible (Configuration Management)

**Definition:**  
Ansible is an **agentless automation tool** for configuration management, application deployment, and task automation.

**Simple playbook:**
```yaml
# deploy.yml
- hosts: webservers
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present

    - name: Start nginx
      service:
        name: nginx
        state: started
```

---

## Unit 6 – Infrastructure as Code (Terraform)

### 6.1 What is Terraform? (⭐ OPTIONAL BUT SCORING)

**Definition:**  
Terraform is an **Infrastructure as Code (IaC)** tool by HashiCorp that allows defining and provisioning cloud infrastructure using configuration files.

**Why IaC?**
- Infrastructure defined in code → version controlled
- Reproducible environments
- No manual clicking in cloud console
- Consistent across dev/staging/production

**EC2 Instance configuration:**

```hcl
# main.tf

# Provider – which cloud to use
provider "aws" {
  region = "ap-south-1"  # Mumbai region
}

# Resource – what to create
resource "aws_instance" "app_server" {
  ami           = "ami-00bb6a80f"  # Amazon Machine Image
  instance_type = "t2.micro"       # free tier eligible

  tags = {
    Name        = "AppServerInstance"
    Environment = "production"
  }
}
```

```hcl
# variables.tf

variable "instance_name" {
  description = "Name tag for EC2 instance"
  type        = string
  default     = "AppServerInstance"
}

variable "instance_type" {
  description = "EC2 instance type"
  type        = string
  default     = "t2.micro"
}
```

**Terraform commands:**
```bash
terraform init      # download providers
terraform plan      # preview changes
terraform apply     # create resources
terraform destroy   # delete resources
```

---

## 🔥 Most Expected Questions

| Question | Marks | Frequency |
|---|---|---|
| CI/CD explanation | 3–5 | ⭐⭐⭐ |
| Git commands (diagram) | 7–10 | ⭐⭐⭐ |
| Shell script (system monitor) | 3–5 | ⭐⭐⭐ |
| Dockerize Node.js app (Dockerfile) | 5–7 | ⭐⭐⭐ |
| Docker networking (MongoDB) | 3–5 | ⭐⭐ |
| Docker Compose YAML | 5 | ⭐⭐ |
| DevOps lifecycle phases | 3–5 | ⭐⭐ |
| Linux directories | 2–3 | ⭐⭐ |
| RPM vs Debian | 3 | ⭐⭐ |
| Terraform EC2 | 3–5 | ⭐ |

---

## 📝 Quick Revision Summary

```
DevOps = Dev + Ops unified, faster delivery, CI/CD

Lifecycle: Plan→Code→Build→Test→Release→Deploy→Operate→Monitor

CI  = merge code frequently + auto build/test
CD  = auto prepare for release (manual deploy)
CD+ = auto deploy to production

Linux:
  /lib = libraries | /mnt = mount | /etc = config | /var = logs
  Everything is a file
  RPM (.rpm, yum/dnf) vs Debian (.deb, apt)

Git:
  init → add → commit → push | branch → checkout → merge
  Hotfix = urgent production fix branch

Docker:
  Image (blueprint) → Container (running instance)
  Dockerfile → docker build → docker run
  Networks: containers on same network talk by name
  docker-compose: multi-container apps in YAML

Terraform: IaC for cloud infra (AWS EC2 etc.)
```

---

**See also:** [[DevOps PYQ]] | [[DevOps QB]] | [[README]]
