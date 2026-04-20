# 🔥 DevOps – Previous Year Questions

**Subject:** DevOps | **Marks:** 30  
**Related:** [[DevOps Notes]] | [[DevOps QB]] | [[README]]

---

## Q1 – Short Answers (10 marks) — Attempt any 5

*Each 2 marks. Keep answers short but structured.*

---

### a) Plan Phase in DevOps *(2 marks)*
→ See: [[DevOps Notes#1.2 DevOps Lifecycle]]

**Answer:**  
The Plan phase involves:
- Defining project requirements
- Creating project roadmap
- Task scheduling and prioritization

**Tools:** Jira, Trello, Azure DevOps

---

### b) CI & CD *(2 marks)*
→ See: [[DevOps Notes#1.5 CI/CD]]

**Answer:**
- **CI (Continuous Integration):** Code is merged frequently into shared repo; each merge triggers automated build + test
- **CD (Continuous Delivery):** After CI, code is automatically prepared for release (manual deploy approval)
- **Continuous Deployment:** Automatically deploys to production without manual step

---

### c) Waterfall vs Agile *(2 marks)*
→ See: [[DevOps Notes#1.3 Waterfall vs Agile vs DevOps]]

| Feature | Waterfall | Agile |
|---|---|---|
| Process | Sequential phases | Iterative sprints |
| Flexibility | Rigid | Flexible |
| Testing | End of project | Each sprint |
| Feedback | Very late | After each sprint |

---

### d) Advantages & Disadvantages of DevOps *(2 marks)*
→ See: [[DevOps Notes#1.4 Advantages and Disadvantages of DevOps]]

**Advantages:** Faster delivery, better collaboration, higher quality, faster bug fixes  
**Disadvantages:** Complex setup, requires skilled team, high initial cost

---

### e) GitHub + VS Code Integration *(2 marks)*
→ See: [[DevOps Notes#3.6 GitHub VS Code Integration]]

**Answer:**
1. Install Git from git-scm.com
2. Configure: `git config --global user.name "Name"`
3. Clone repo: `git clone <url>`
4. Open in VS Code: `code .`
5. Use Source Control panel (Ctrl+Shift+G) or terminal

---

### f) /lib and /mnt *(2 marks)*
→ See: [[DevOps Notes#2.3 Linux Directory Structure]]

- `/lib` → shared system libraries needed by binaries (like DLLs in Windows)
- `/mnt` → mount point for external drives/USB devices/network shares

---

### g) Linux Distributions *(2 marks)*
→ See: [[DevOps Notes#2.1 What is Linux?]]

| Distribution | Package Manager | Use case |
|---|---|---|
| Ubuntu | apt | General purpose |
| Fedora | dnf | Developers |
| CentOS | yum | Enterprise servers |
| Debian | apt | Stable servers |
| Kali | apt | Security testing |

---

## Q2 – Important Theory (10 marks)

---

### Role of Source Control Tools *(4 marks)*
→ See: [[DevOps Notes#3.1 What is Version Control?]]

**Answer:**  
Source control tools (like Git) are essential in DevOps for:
1. **Tracking changes** – full history of every code modification
2. **Enabling collaboration** – multiple developers work simultaneously
3. **Version management** – roll back to any previous state
4. **Branching** – develop features in isolation, merge when ready
5. **Backup** – code is stored remotely, never lost

**Example:** Git + GitHub workflow: `branch → commit → push → pull request → merge`

---

### RPM vs Debian *(3 marks)*
→ See: [[DevOps Notes#2.6 Package Management RPM vs Debian]]

| Feature | RPM | Debian |
|---|---|---|
| Based on | Red Hat | Debian/Ubuntu |
| File format | `.rpm` | `.deb` |
| Package manager | `yum` / `dnf` | `apt` |
| Install | `yum install pkg` | `apt install pkg` |
| Distros | RHEL, CentOS, Fedora | Ubuntu, Debian, Mint |

---

### Shell Script – System Monitor *(3 marks)*
→ See: [[DevOps Notes#2.7 Shell Scripting]]

**Answer:**
```bash
#!/bin/bash
# Logs system stats every 5 minutes

while true
do
    echo "$(date) | $(uptime) | $(free -m | grep Mem) | $(df -h /)" >> stats.tsv
    sort -r stats.tsv -o stats.tsv   # sort newest first
    sleep 300                          # wait 5 minutes
done
```

**Key points:**
- `#!/bin/bash` = shebang (specifies interpreter)
- `while true` = infinite loop
- `$(date)` = current timestamp
- `$(uptime)` = system running time
- `$(free -m)` = memory usage in MB
- `$(df -h)` = disk usage human-readable
- `>> stats.tsv` = append to file (not overwrite)
- `sleep 300` = pause 5 minutes (300 seconds)

---

## Q3 – Git + Docker (10 marks)

---

### Git Commands – Branching Diagram *(5 marks)*
→ See: [[DevOps Notes#3.4 Git Branching Workflow]]

**Answer:**
```bash
# C0 – initial commit on main
echo "<h1>Hello World</h1>" >> README.md
git add .
git commit -m "C0: initial README"

# C1 – add new file
touch file.txt
git add .
git commit -m "C1: add file.txt"

# C2 – update file
echo "some content" >> file.txt
git add .
git commit -m "C2: update file.txt"

# Create and switch to feature branch
git branch issue53
git checkout issue53
# or: git checkout -b issue53

# C3 – work on feature (on issue53 branch)
touch index.html
echo "<h1>Feature Page</h1>" >> index.html
git add .
git commit -m "C3: add index.html (issue53)"

# Push feature branch to remote
git push origin issue53

# Merge back to main
git checkout main
git merge issue53
git push origin main
```

---

### Hotfix Branch + Git Commands *(3 marks)*
→ See: [[DevOps Notes#3.5 Hotfix Branch]]

**Answer:**

A hotfix branch is used to **fix urgent bugs directly in production**.

```bash
git checkout main                    # start from production
git checkout -b hotfix/login-bug     # create hotfix branch

# Fix the bug...
git add .
git commit -m "Fix: resolve login authentication bug"

git checkout main
git merge hotfix/login-bug           # deploy fix
git push origin main

git branch -d hotfix/login-bug       # cleanup
```

**Key Git commands:**

| Command | Purpose |
|---|---|
| `git status` | shows changed files (staged/unstaged) |
| `git add .` | stage all changes |
| `git commit -m "msg"` | save staged changes |
| `git log --oneline` | compact commit history |
| `git diff` | see unstaged changes |

---

### Dockerize Node.js App *(5 marks)*
→ See: [[DevOps Notes#4.4 Dockerfile]]

**Answer:**

**Step 1: Create the app (app.js)**
```js
const http = require('http');
const server = http.createServer((req, res) => {
    res.end('Hello from Docker!');
});
server.listen(3000);
```

**Step 2: Create Dockerfile**
```dockerfile
# Base image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Expose port
EXPOSE 3000

# Run command
CMD ["node", "app.js"]
```

**Step 3: Build and run**
```bash
# Build image
docker build -t my-node-app .

# Run container
docker run -d -p 3000:3000 --name my-app my-node-app

# Check it works
curl http://localhost:3000
```

---

## Q4 – Docker Commands (10 marks)

---

### Create Network + MongoDB *(4 marks)*
→ See: [[DevOps Notes#4.6 Docker Networking]]

**Answer:**
```bash
# Create custom network
docker network create mongo-net

# Run MongoDB on the network
docker run -d \
  --name mongodb \
  --network mongo-net \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  mongo

# Run Mongo Express GUI on same network
docker run -d \
  --name mongo-express \
  --network mongo-net \
  -p 8081:8081 \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
  -e ME_CONFIG_MONGODB_SERVER=mongodb \
  mongo-express

# Access at http://localhost:8081
```

**Why same network?** Containers on same network communicate by name, no IP needed.

---

### PostgreSQL Docker Commands *(4 marks)*
→ See: [[DevOps Notes#4.7 PostgreSQL with Docker]]

**Answer:**
```bash
# Pull image
docker pull postgres

# Run container (user1)
docker run -d \
  --name postgres-user1 \
  -e POSTGRES_USER=user1 \
  -e POSTGRES_PASSWORD=password1 \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  postgres

# Connect to psql shell
docker exec -it postgres-user1 psql -U user1 -d mydb

# Run queries in psql
CREATE TABLE students (id SERIAL, name VARCHAR(100));
INSERT INTO students (name) VALUES ('Harsh');
SELECT * FROM students;
\q   # quit

# Stop and remove
docker stop postgres-user1
docker rm postgres-user1
```

---

## Q5 – Advanced (10 marks)

---

### docker-compose.yml *(5 marks)*
→ See: [[DevOps Notes#4.8 Docker Compose]]

```yaml
version: '3.8'

services:
  mongo:
    image: mongo
    container_name: mongodb
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    volumes:
      - mongo-data:/data/db

  mongo-express:
    image: mongo-express
    container_name: mongo-express
    ports:
      - "8081:8081"
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: password
      ME_CONFIG_MONGODB_SERVER: mongo
    depends_on:
      - mongo

volumes:
  mongo-data:
```

**Commands:**
```bash
docker-compose up -d      # start all services in background
docker-compose down       # stop and remove
docker-compose logs -f    # follow logs
```

---

### Terraform EC2 *(5 marks)*
→ See: [[DevOps Notes#6.1 What is Terraform?]]

**main.tf:**
```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "app_server" {
  ami           = "ami-00bb6a80f"
  instance_type = "t2.micro"

  tags = {
    Name        = var.instance_name
    Environment = "production"
  }
}
```

**variables.tf:**
```hcl
variable "instance_name" {
  description = "Name tag for EC2 instance"
  type        = string
  default     = "AppServerInstance"
}
```

**Commands:**
```bash
terraform init      # initialize
terraform plan      # preview changes
terraform apply     # create resources
terraform destroy   # delete resources
```

---

## 🏆 Most Repeated Topics (Ranked)

1. 🥇 **Git branching + commands (diagram)** – GUARANTEED
2. 🥇 **Shell script (system monitor)** – GUARANTEED
3. 🥇 **Dockerize Node.js (Dockerfile)** – GUARANTEED
4. 🥈 **CI/CD explanation**
5. 🥈 **Docker networking + MongoDB**
6. 🥈 **Docker Compose YAML**
7. 🥉 **Linux directories + commands**
8. 🥉 **Terraform EC2**

---

**See also:** [[DevOps Notes]] | [[DevOps QB]] | [[README]]
