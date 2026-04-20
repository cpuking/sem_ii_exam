# 🔥 DEVOPS QUESTION BANK – SMART BREAKDOWN

---

# ✅ 🔹 SHORT ANSWERS (2–3 MARKS)

---

## ⭐ 1. Build Phase in DevOps (IMPORTANT)

**Answer:**

The build phase involves:

- Compiling code
    
- Generating executable files
    
- Running unit tests
    

**Tools:**

- Maven
    
- Gradle
    

---

## ⭐ 2. GitHub vs GitLab (Collaboration)

**Answer:**

- Version control
    
- Team collaboration
    
- Pull requests / Merge requests
    
- Issue tracking
    

👉 Enables multiple developers to work together

---

## ⭐ 3. SDLC Phases

**Answer:**

1. Requirement
    
2. Design
    
3. Development
    
4. Testing
    
5. Deployment
    
6. Maintenance
    

---

## ⭐ 4. Orchestration (IMPORTANT)

**Answer:**

Orchestration automates container management.

**Tools:**

- Kubernetes
    
- Docker Swarm
    

---

## ⭐ 5. Linux Directories

**Answer:**

- `/lib` → system libraries
    
- `/mnt` → mount external drives
    
- `/etc` → configuration files
    
- `/var` → logs and variable data
    

---

## ⭐ 6. Linux Advantages

**Answer:**

- Open source
    
- Secure
    
- Stable
    
- Customizable
    

---

## ⭐ 7. Linux = Everything is File (VERY IMPORTANT)

**Answer:**  
TRUE  
👉 Devices, processes, and files are treated as files in Linux

---

## ⭐ 8. Command Purpose (IMPORTANT)

**Answer:**

- `uptime` → shows system running time
    
- `cat /proc/uptime` → detailed uptime info
    
- `rm -rf *` → deletes all files (⚠️ dangerous)
    

---

# 🎯 MOST EXPECTED SHORT QUESTIONS

From QB:

- Build phase ✅
    
- Orchestration ✅
    
- Linux directories ✅
    
- Commands (uptime etc.) ✅
    

---

# 🔥 🔹 LONG ANSWERS (VERY IMPORTANT)

---

## ⭐ 1. Role of Deployment Tools

**Answer:**

Deployment tools:

- Automate application deployment
    
- Reduce manual errors
    
- Ensure consistency
    

Examples:

- Jenkins
    
- Ansible
    

---

## ⭐ 2. Source Control Tools (REPEATED)

**Answer:**

- Track changes
    
- Maintain versions
    
- Enable collaboration
    
- Support branching
    

Example: Git

---

## ⭐ 3. RPM vs Debian

**Answer:**

|RPM|Debian|
|---|---|
|RedHat based|Ubuntu based|
|`.rpm`|`.deb`|
|yum/dnf|apt|

---

# 🔥 🔹 SHELL SCRIPT (VERY IMPORTANT – GUARANTEED)

From QB + PYQ same question appears

---

## ⭐ System Monitoring Script

```bash
#!/bin/bash

while true
do
  echo "$(date) | $(uptime) | $(free -m) | $(df -h)" >> stats.tsv
  sort -r stats.tsv -o stats.tsv
  sleep 300
done
```

👉 Write these points:

- Infinite loop
    
- Runs every 5 minutes
    
- Stores in TSV
    
- Sorted by timestamp
    

---

# 🔥 🔹 GIT QUESTIONS (VERY VERY IMPORTANT)

---

## ⭐ Git Commands (Diagram Question – GUARANTEED)

From diagram (page 2 & 6)

---

### ✅ Answer:

```bash
# C0
echo "<h1>Hello</h1>" >> README.md
git add .
git commit -m "C0"

# C1
touch file.txt
git add .
git commit -m "C1"

# C2
echo "update" >> file.txt
git add .
git commit -m "C2"

# Create branch
git branch issue53
git checkout issue53

# C3
touch index.html
echo "update" >> README.md
git add .
git commit -m "C3"

git push origin issue53
```

---

## ⭐ Hotfix Branch + Commands

**Answer:**

- Hotfix → used to fix urgent production bugs
    

Commands:

- `git status` → shows changes
    
- `git add` → stage files
    
- `git commit` → save changes
    

---

## ⭐ Git Branching (ADVANCED)

**Answer:**

- `git checkout` → switch branch
    
- `git log` → view history
    
- `git push -u origin main` → push branch
    

---

# 🔥 🔹 DOCKER (VERY HIGH PROBABILITY)

---

## ⭐ Dockerize Node App

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

---

## ⭐ Create Network + Mongo

```bash
docker network create mongo-net
docker run -d --name mongo --network mongo-net mongo
```

---

## ⭐ Connect Containers

**Answer:**

- Create network
    
- Run containers in same network
    
- Use container names
    

---

## ⭐ Mongo Express

```bash
docker run -d --name mongo-express \
--network mongo-net \
-p 8081:8081 mongo-express
```

---

## ⭐ PostgreSQL Commands (IMPORTANT)

```bash
docker pull postgres

docker run -d --name postgres-user1 \
-e POSTGRES_PASSWORD=pass postgres

docker exec -it postgres-user1 psql -U postgres

docker stop postgres-user1
docker rm postgres-user1
```

---

# 🔥 🔹 TERRAFORM (OPTIONAL BUT SCORING)

---

## ⭐ EC2 Configuration

```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "app" {
  ami           = "ami-00bb6a80f"
  instance_type = "t2.micro"

  tags = {
    Name = "AppServerInstance"
  }
}
```

---

# 🚀 FINAL ANALYSIS (VERY IMPORTANT)

From QB + PYQ:

### 🔥 GUARANTEED QUESTIONS:

- Git commands (diagram) ✅
    
- Shell script ✅
    
- Docker commands ✅
    
- CI/CD / lifecycle ✅
    

---

# ⚠️ REAL STRATEGY

If you only prepare:

- Git commands
    
- Docker basics
    
- Shell script
    

👉 You’ll score **20–25 / 30 easily**

---
