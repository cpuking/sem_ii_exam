# 🔥 DevOps – Q1 (10 marks, EASY)

Solve any 5 → I’ll give ALL.

---

## 🔹 a) Plan Phase in DevOps

**Answer:**  
Plan phase involves:

- Defining requirements
    
- Project planning
    
- Task scheduling
    

**Tools:**

- Jira
    
- Trello
    

---

## 🔹 b) CI & CD

**Answer:**

- **CI (Continuous Integration):** Code is merged frequently
    
- **CD (Continuous Delivery):** Code is automatically deployed
    

---

## 🔹 c) Waterfall vs Agile

**Answer:**

|Waterfall|Agile|
|---|---|
|Sequential|Iterative|
|Rigid|Flexible|
|Late testing|Continuous testing|

---

## 🔹 d) Advantages & Disadvantages of DevOps

**Advantages:**

- Faster delivery
    
- Better collaboration
    

**Disadvantages:**

- Complex setup
    
- Requires skilled team
    

---

## 🔹 e) GitHub + VS Code

**Answer:**

- Install Git
    
- Connect GitHub account
    
- Clone repo
    
- Use commit & push
    

---

## 🔹 f) /lib and /mnt

**Answer:**

- `/lib` → system libraries
    
- `/mnt` → mount external drives
    

---

## 🔹 g) Linux Distributions

**Answer:**

- Ubuntu
    
- Fedora
    
- Debian
    
- CentOS
    

---

# 🎯 MOST IMPORTANT (Q1)

👉 Always comes:

- CI/CD ✅
    
- DevOps lifecycle ✅
    
- Linux basics ✅
    

---

# 🔥 Q2 (IMPORTANT)

---

## 🔹 Role of Source Control Tools

**Answer (4 marks):**

- Tracks code changes
    
- Enables collaboration
    
- Maintains version history
    
- Supports branching
    

Example: Git

---

## 🔹 RPM vs Debian

**Answer (3 marks):**

|RPM|Debian|
|---|---|
|RedHat based|Debian/Ubuntu|
|Uses `.rpm`|Uses `.deb`|
|yum/dnf|apt|

---

## 🔹 Shell Script (IMPORTANT)

**Answer (3 marks):**

```bash
#!/bin/bash

while true
do
  echo "$(date) $(uptime) $(free -m) $(df -h)" >> stats.tsv
  sleep 300
done
```

👉 Key points:

- Infinite loop
    
- Logs every 5 min
    

---

# 🔥 Q3 (VERY IMPORTANT – GIT + DOCKER)

---

## 🔹 Git Commands (HIGH CHANCE)

**Answer:**

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

# Branch
git branch issue53
git checkout issue53

# C3
touch index.html
git add .
git commit -m "C3"

git push origin issue53
```

---

## 🔹 Hotfix Branch + Git Commands

**Answer:**

- **Hotfix branch:** Fix urgent bugs in production
    

Commands:

- `git status` → shows changes
    
- `git add` → stage changes
    
- `git commit` → save changes
    

---

## 🔹 Dockerize Node App (VERY IMPORTANT)

**Answer:**

### Steps:

1. Create app
    
2. Create Dockerfile
    
3. Build image
    
4. Run container
    

### Dockerfile:

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

---

# 🔥 Q4 (DOCKER COMMANDS)

---

## 🔹 Create Network + MongoDB

```bash
docker network create mynet
docker run -d --name mongo --network mynet mongo
```

---

## 🔹 Connect Containers

**Answer:**

- Create network
    
- Run containers on same network
    
- Use container names
    

---

## 🔹 PostgreSQL Commands

```bash
docker run -d --name postgres-user2 -e POSTGRES_PASSWORD=pass postgres
docker stop postgres-user2
docker rm postgres-user2
```

---

# 🔥 Q5 (ADVANCED – OPTIONAL BUT SCORING)

---

## 🔹 docker-compose.yml

```yaml
version: '3'
services:
  mongo:
    image: mongo
    ports:
      - "27017:27017"

  mongo-express:
    image: mongo-express
    ports:
      - "8081:8081"
```

---

## 🔹 Terraform EC2

```hcl
provider "aws" {
  region = "ap-east-1"
}

resource "aws_instance" "app" {
  ami           = "ami-03bb6a80sdff"
  instance_type = "t3.micro"

  tags = {
    Name = "AppServerInstance"
  }
}
```

---

## 🔹 variables.tf

```hcl
variable "instance_name" {
  default = "AppServerInstance"
}
```

---

# 🚀 DEVOPS FINAL ANALYSIS

From PYQ:

### 🔥 MOST IMPORTANT:

- CI/CD ✅
    
- Git commands ✅
    
- Docker basics ✅
    
- Linux basics ✅
    

👉 That’s enough for **20+/30 easily**

---

# 🎯 FINAL STRATEGY (ALL SUBJECTS DONE)

You now have:

- SPM ✅
    
- FP ✅
    
- FSD ✅
    
- DevOps ✅
    

---

# 🚀 WHAT YOU SHOULD DO NEXT

1. Revise these answers
    
2. Practice writing 1–2 answers per subject
    
3. Focus on repeated topics
    

---
