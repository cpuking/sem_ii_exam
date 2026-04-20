> 📌 **Exam Strategy:** Git + Docker + Shell Script = **20–25/30 guaranteed** Tags: #devops #exam #questionbank

---

# 📋 TABLE OF CONTENTS

- [[#SHORT ANSWERS (2–3 Marks)]]
- [[#LONG ANSWERS (5–7 Marks)]]
- [[#SHELL SCRIPT – GUARANTEED]]
- [[#GIT – VERY VERY IMPORTANT]]
- [[#DOCKER – VERY HIGH PROBABILITY]]
- [[#TERRAFORM – OPTIONAL BUT SCORING]]
- [[#FINAL STRATEGY]]

---

# ✅ SHORT ANSWERS (2–3 Marks)

---

## ⭐ 1. Build Phase in DevOps `IMPORTANT`

**Definition:** The **Build Phase** is the stage in the DevOps pipeline where source code is transformed into executable artifacts ready for testing and deployment.

**What happens in Build Phase:**

|Step|Description|
|---|---|
|Compile|Source code is compiled into bytecode/binary|
|Package|Code is packaged (JAR, WAR, Docker image)|
|Unit Test|Automated unit tests are executed|
|Artifact|Build output is stored in artifact repository|

**Build Tools:**

|Tool|Language|Description|
|---|---|---|
|Maven|Java|Uses `pom.xml`, dependency management|
|Gradle|Java/Kotlin|Faster builds, flexible scripting|
|npm|Node.js|JavaScript package manager|
|Make|C/C++|Classic Unix build tool|

**Why Build Phase matters in DevOps:**

- Catches compilation errors early
- Ensures code integrates correctly (CI)
- Produces consistent, reproducible builds
- Triggers automated tests before deployment

> 📝 **2-mark answer:** Build phase compiles code, runs unit tests, and generates executable artifacts using tools like Maven and Gradle.

---

## ⭐ 2. GitHub vs GitLab (Collaboration) `IMPORTANT`

**Definition:** Both are **Git-based platform** for version control and DevOps collaboration, but differ in features and focus.

|Feature|GitHub|GitLab|
|---|---|---|
|Owned by|Microsoft|GitLab Inc.|
|Primary focus|Open source hosting|Full DevOps platform|
|CI/CD|GitHub Actions|GitLab CI/CD (built-in)|
|Pull/Merge Requests|Pull Requests|Merge Requests|
|Self-hosting|GitHub Enterprise|GitLab CE (free)|
|Issue tracking|✅ Yes|✅ Yes|
|Package registry|✅ Yes|✅ Yes|
|Container registry|✅ Yes|✅ Yes|

**Key Collaboration Features (common to both):**

- Version control with branching
- Code review via Pull/Merge Requests
- Issue tracking and project boards
- Team access controls and permissions
- Webhooks and integrations

> 📝 **2-mark answer:** GitHub and GitLab enable team collaboration through version control, pull/merge requests, and issue tracking, allowing multiple developers to work simultaneously on the same codebase.

---

## ⭐ 3. SDLC Phases `IMPORTANT`

**Definition:** **Software Development Life Cycle (SDLC)** is a structured process for planning, creating, testing, and deploying software.

**Phases (write as numbered list in exam):**

|Phase|Key Activities|Output|
|---|---|---|
|1. Requirement|Gathering user needs, feasibility|SRS Document|
|2. Design|System architecture, UI design|Design Document|
|3. Development|Writing code, unit testing|Source Code|
|4. Testing|Integration, system, UAT testing|Test Reports|
|5. Deployment|Release to production|Live Application|
|6. Maintenance|Bug fixes, updates, monitoring|Updated Software|

**SDLC Models:**

- Waterfall – sequential
- Agile – iterative sprints
- DevOps – continuous delivery

> 📝 **2-mark answer:** SDLC has 6 phases: Requirement → Design → Development → Testing → Deployment → Maintenance.

---

## ⭐ 4. Orchestration `IMPORTANT`

**Definition:** **Container Orchestration** is the automated management of containerized applications across multiple hosts — handling deployment, scaling, networking, and self-healing.

**Why Orchestration is needed:**

- Manual container management doesn't scale
- Need automatic restart if container crashes
- Need load balancing across containers
- Need service discovery between containers

**Key Orchestration Functions:**

|Function|Description|
|---|---|
|Scheduling|Decides which host runs which container|
|Scaling|Auto scale up/down based on load|
|Load balancing|Distributes traffic evenly|
|Self-healing|Restarts failed containers automatically|
|Service discovery|Containers find each other by name|
|Rolling updates|Deploy new versions without downtime|

**Orchestration Tools:**

|Tool|By|Best For|
|---|---|---|
|Kubernetes (K8s)|Google/CNCF|Production, large scale|
|Docker Swarm|Docker Inc.|Simple setups|
|Apache Mesos|Apache|Data-heavy workloads|

> 📝 **2-mark answer:** Orchestration automates container management tasks like scheduling, scaling, and self-healing. Tools: Kubernetes, Docker Swarm.

---

## ⭐ 5. Linux Directories `IMPORTANT`

**Key Filesystem Directories (FHS – Filesystem Hierarchy Standard):**

|Directory|Purpose|Example Contents|
|---|---|---|
|`/`|Root directory|Everything starts here|
|`/bin`|Essential binaries|`ls`, `cp`, `mv`|
|`/sbin`|System binaries|`fsck`, `reboot`|
|`/etc`|Configuration files|`nginx.conf`, `hosts`|
|`/home`|User home directories|`/home/harsh/`|
|`/var`|Variable data (logs)|`/var/log/syslog`|
|`/tmp`|Temporary files|Cleared on reboot|
|`/lib`|Shared system libraries|`.so` files|
|`/usr`|User programs|`/usr/bin/python3`|
|`/mnt`|Mount point for drives|USB, external disks|
|`/proc`|Kernel/process info|`/proc/cpuinfo`|
|`/dev`|Device files|`/dev/sda`, `/dev/null`|
|`/opt`|Optional software|Third-party apps|
|`/boot`|Boot files|`vmlinuz`, `grub`|

> 📝 **2-mark answer:** `/etc` = config files, `/var` = logs, `/lib` = libraries, `/mnt` = mount external drives, `/proc` = kernel/process info.

---

## ⭐ 6. Linux Advantages `IMPORTANT`

|Advantage|Explanation|
|---|---|
|**Open Source**|Free to use, modify, distribute|
|**Secure**|Permission-based access, low malware risk|
|**Stable**|Can run for years without reboot|
|**Customizable**|Choose kernel, DE, packages freely|
|**Multi-user**|Multiple users simultaneously|
|**Lightweight**|Runs on old/minimal hardware|
|**CLI Power**|Shell scripting for automation|
|**Package Manager**|`apt`, `yum` for easy software install|

> 📝 **2-mark answer:** Linux is open source, secure, stable, and highly customizable, making it ideal for servers and DevOps environments.

---

## ⭐ 7. Linux – Everything is a File `VERY IMPORTANT`

**Answer: TRUE**

In Linux, the philosophy "**everything is a file**" means:

|Entity|File Path Example|Description|
|---|---|---|
|Regular file|`/home/user/doc.txt`|Normal file|
|Directory|`/home/user/`|A special file listing contents|
|Device (disk)|`/dev/sda`|Hard disk as file|
|Device (null)|`/dev/null`|Discard output|
|Process info|`/proc/1234/status`|Process as file|
|Network socket|Socket files|Network as file|
|Hardware ports|`/dev/ttyS0`|Serial port as file|

**Why this matters:**

- Uniform interface: same read/write operations for all
- Simplifies programming and scripting
- Tools like `cat`, `grep`, `echo` work on anything
- Enables powerful pipelines: `cat /proc/cpuinfo | grep processor`

> 📝 **2-mark answer:** In Linux, everything including devices, processes, and hardware is represented as a file, providing a uniform interface for all I/O operations.

---

## ⭐ 8. Linux Commands – Purpose `IMPORTANT`

**System Monitoring Commands:**

|Command|Purpose|Example Output|
|---|---|---|
|`uptime`|Shows how long system has been running|`14:22:01 up 3 days, 2:14`|
|`cat /proc/uptime`|Raw uptime in seconds|`258000.14 512000.33`|
|`top`|Real-time process monitor|CPU, memory per process|
|`htop`|Enhanced interactive process viewer|Color-coded resource usage|
|`free -m`|Memory usage in MB|Used/free RAM|
|`df -h`|Disk space usage (human readable)|Per-partition usage|
|`uname -a`|Kernel and OS info|Kernel version|
|`whoami`|Current logged-in user|`harsh`|

**File Operation Commands:**

|Command|Purpose|Risk Level|
|---|---|---|
|`rm -rf *`|Recursively delete ALL files|⚠️ EXTREMELY DANGEROUS|
|`rm -rf /`|Delete entire filesystem|☠️ CATASTROPHIC|
|`cp -r src dst`|Copy directory recursively|Safe|
|`mv file dest`|Move/rename file|Safe|
|`chmod 755 file`|Set permissions|Moderate|
|`chown user file`|Change file owner|Moderate|

> ⚠️ `rm -rf *` is irreversible — no Recycle Bin in Linux!

> 📝 **2-mark answer:** `uptime` shows system running time; `cat /proc/uptime` gives raw uptime in seconds; `rm -rf *` deletes all files recursively and is irreversible.

---

# 🔥 LONG ANSWERS (5–7 Marks)

---

## ⭐ 1. Role of Deployment Tools `IMPORTANT`

**Definition:** Deployment tools automate the process of releasing software from development/staging environments to production, ensuring consistent and error-free delivery.

**Why Deployment Tools are Needed:**

- Manual deployment is slow and error-prone
- Need repeatable, consistent process across environments
- Zero-downtime deployments
- Rollback capability if something fails

**Key Functions of Deployment Tools:**

|Function|Description|
|---|---|
|Automation|Deploy without manual intervention|
|Configuration Management|Manage server configs consistently|
|Environment Management|Dev → Staging → Production|
|Rollback|Revert to previous version on failure|
|Monitoring|Track deployment health|
|Parallel Execution|Deploy to multiple servers simultaneously|

**Major Deployment Tools:**

|Tool|Type|Key Feature|
|---|---|---|
|**Jenkins**|CI/CD server|Pipeline as code, plugin-rich|
|**Ansible**|Config management|Agentless, YAML playbooks|
|**Chef**|Config management|Ruby-based cookbooks|
|**Puppet**|Config management|Declarative manifests|
|**Spinnaker**|CD platform|Multi-cloud deployments|
|**ArgoCD**|GitOps CD|Kubernetes-native|
|**Octopus Deploy**|Release management|Complex deployment patterns|

**Jenkins Pipeline Example:**

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { sh 'mvn clean package' }
        }
        stage('Test') {
            steps { sh 'mvn test' }
        }
        stage('Deploy') {
            steps { sh 'ansible-playbook deploy.yml' }
        }
    }
}
```

**Ansible Playbook Example:**

```yaml
- name: Deploy Web Application
  hosts: webservers
  tasks:
    - name: Copy application files
      copy:
        src: /build/app.jar
        dest: /opt/app/app.jar
    - name: Restart application service
      service:
        name: myapp
        state: restarted
```

**Benefits Summary:**

- Reduces deployment time from hours to minutes
- Eliminates "it works on my machine" problems
- Enables Continuous Delivery
- Provides deployment audit trail

> 📝 **5-mark answer:** Explain definition + 4 functions + 2 tools with examples. Draw a simple pipeline diagram for extra marks.

---

## ⭐ 2. Source Control / Version Control Tools `REPEATED`

**Definition:** Source Control (Version Control) systems track and manage changes to code over time, enabling teams to collaborate and maintain history.

**Key Functions:**

|Function|Description|
|---|---|
|Track Changes|Every change is recorded with author and timestamp|
|Versioning|Maintain multiple versions of codebase|
|Branching|Work on features/fixes in isolation|
|Merging|Combine changes from different branches|
|Rollback|Revert to any previous state|
|Collaboration|Multiple developers on same codebase|
|Blame|Know who changed which line and when|

**Types of Version Control:**

|Type|Description|Example|
|---|---|---|
|Local|On single machine|RCS|
|Centralized|Single server|SVN, CVS|
|Distributed|Every clone is full repo|Git, Mercurial|

**Git – Most Used VCS:**

|Command|Purpose|
|---|---|
|`git init`|Initialize new repository|
|`git clone <url>`|Copy remote repo locally|
|`git add .`|Stage all changes|
|`git commit -m "msg"`|Save changes with message|
|`git push origin main`|Upload to remote|
|`git pull`|Download and merge changes|
|`git branch <name>`|Create new branch|
|`git merge <branch>`|Merge branch into current|
|`git log --oneline`|View compact history|
|`git diff`|See unstaged changes|

**Git Workflow (Feature Branch Model):**

```
main ──●──────────────────────●── (merge)
        \                    /
feature  ●──●──●──●──●──●──●
         C1 C2 C3 C4 C5 C6 C7
```

**Popular Source Control Platforms:**

|Platform|Hosting|Special Feature|
|---|---|---|
|GitHub|Cloud|Largest open-source community|
|GitLab|Cloud/Self-hosted|Full DevOps platform|
|Bitbucket|Cloud|Jira integration|
|Azure DevOps|Cloud|Microsoft ecosystem|

> 📝 **5-mark answer:** Definition + types + Git commands table + Git workflow description. Mention branching and merging.

---

## ⭐ 3. RPM vs Debian Package Management `IMPORTANT`

**Definition:** Package management systems handle software installation, updates, and removal on Linux systems.

**Comparison Table:**

|Feature|RPM (RedHat Package Manager)|Debian (dpkg/apt)|
|---|---|---|
|Based On|Red Hat Enterprise Linux|Debian GNU/Linux|
|Distributions|RHEL, CentOS, Fedora, Amazon Linux|Ubuntu, Debian, Linux Mint|
|Package Extension|`.rpm`|`.deb`|
|Low-level tool|`rpm`|`dpkg`|
|High-level tool (resolver)|`yum` / `dnf`|`apt` / `apt-get`|
|Package query|`rpm -qa`|`dpkg -l`|
|Install|`rpm -ivh pkg.rpm`|`dpkg -i pkg.deb`|
|Install with deps|`yum install pkg`|`apt install pkg`|
|Update all|`yum update`|`apt upgrade`|
|Remove|`yum remove pkg`|`apt remove pkg`|
|Search|`yum search pkg`|`apt search pkg`|
|Repo config|`/etc/yum.repos.d/`|`/etc/apt/sources.list`|

**Common Commands Comparison:**

```bash
# Install a package
yum install nginx          # RPM-based
apt install nginx          # Debian-based

# Update system
yum update                 # RPM-based
apt update && apt upgrade  # Debian-based

# Remove package
yum remove nginx           # RPM-based
apt remove nginx           # Debian-based
```

> 📝 **5-mark answer:** Write definition + full comparison table + at least 3 command examples for each.

---

# 🔥 SHELL SCRIPT – GUARANTEED QUESTION

> This exact question or a variant **appears every year**. Memorize the script + explanation.

---

## ⭐ System Monitoring Script `GUARANTEED`

**Question:** Write a shell script to monitor system performance and log it to a file.

**Script:**

```bash
#!/bin/bash
# System Monitoring Script
# Logs: Date | Uptime | Memory | Disk Usage
# Output: stats.tsv (Tab-Separated Values)
# Runs: Every 5 minutes (300 seconds), indefinitely

while true
do
    echo "$(date) | $(uptime) | $(free -m | grep Mem) | $(df -h /)" >> stats.tsv
    sort -r stats.tsv -o stats.tsv
    sleep 300
done
```

**Line-by-Line Explanation:**

|Line|Purpose|
|---|---|
|`#!/bin/bash`|Shebang – specifies bash as interpreter|
|`while true`|Infinite loop – runs forever|
|`$(date)`|Current date and time|
|`$(uptime)`|System uptime and load average|
|`$(free -m)`|Memory usage in megabytes|
|`$(df -h /)`|Disk usage of root partition|
|`>> stats.tsv`|Append output to TSV file (not overwrite)|
|`sort -r ... -o`|Sort file in reverse (newest first), save in-place|
|`sleep 300`|Wait 300 seconds (5 minutes) before next iteration|

**Key Points to Write in Exam:**

1. Uses an **infinite loop** (`while true`) — runs continuously
2. Collects 4 metrics: date, uptime, memory, disk
3. Appends to **TSV (Tab-Separated Values)** file
4. **Sorted in reverse** so latest entry is at top
5. **5-minute interval** between collections (`sleep 300`)
6. Non-destructive: uses `>>` (append), not `>` (overwrite)

**Additional Shell Script Concepts:**

```bash
# Variables
NAME="DevOps"
echo "Hello $NAME"

# If condition
if [ $1 -gt 10 ]; then
    echo "Greater than 10"
else
    echo "Not greater"
fi

# For loop
for i in 1 2 3 4 5; do
    echo "Count: $i"
done

# Function
greet() {
    echo "Hello, $1"
}
greet "Harsh"

# Check if file exists
if [ -f "/etc/nginx/nginx.conf" ]; then
    echo "Config exists"
fi
```

> 📝 **5-mark answer:** Write the script + table of explanations + 5 key points. Full marks guaranteed.

---

# 🔥 GIT – VERY VERY IMPORTANT

---

## ⭐ Git Commands – Diagram Question `GUARANTEED`

**Question:** Write Git commands to create commits C0, C1, C2, create branch `issue53`, make commit C3, and push.

**Complete Answer:**

```bash
# ── INITIAL SETUP ──────────────────────────────
git init
git config user.name "YourName"
git config user.email "you@example.com"

# ── COMMIT C0 ──────────────────────────────────
echo "<h1>Hello</h1>" >> README.md
git add .
git commit -m "C0: Initial README"

# ── COMMIT C1 ──────────────────────────────────
touch file.txt
git add .
git commit -m "C1: Add file.txt"

# ── COMMIT C2 ──────────────────────────────────
echo "update" >> file.txt
git add .
git commit -m "C2: Update file.txt"

# ── CREATE AND SWITCH TO BRANCH ────────────────
git branch issue53
git checkout issue53
# OR (modern shorthand):
# git checkout -b issue53

# ── COMMIT C3 (on issue53 branch) ──────────────
touch index.html
echo "update" >> README.md
git add .
git commit -m "C3: Add index.html on issue53"

# ── PUSH BRANCH TO REMOTE ──────────────────────
git push origin issue53
```

**What This Looks Like (Branch Diagram):**

```
main    ──●──●──●
           C0 C1 C2
                  \
issue53            ●── (pushed)
                   C3
```

---

## ⭐ Hotfix Branch Workflow `IMPORTANT`

**Definition:** A **hotfix branch** is created from `main`/`master` to fix a critical bug in production **without going through the full feature branch process**.

**When to use:** Production is broken and needs immediate fix.

**Hotfix Workflow:**

```bash
# 1. Create hotfix branch from main (production)
git checkout main
git checkout -b hotfix/login-bug

# 2. Fix the bug
vim app.js
git add .
git commit -m "Fix: resolve login null pointer exception"

# 3. Merge back to main (production fix)
git checkout main
git merge hotfix/login-bug

# 4. Also merge to develop (so fix is in next release)
git checkout develop
git merge hotfix/login-bug

# 5. Delete hotfix branch
git branch -d hotfix/login-bug

# 6. Tag the production release
git tag -a v1.0.1 -m "Hotfix: login bug"
git push origin main --tags
```

**Key Git Commands Summary:**

|Command|Purpose|
|---|---|
|`git status`|Show staged/unstaged/untracked files|
|`git add <file>`|Stage specific file|
|`git add .`|Stage all changes|
|`git commit -m "msg"`|Commit with message|
|`git log`|Full commit history|
|`git log --oneline`|Compact history|
|`git diff`|Unstaged changes|
|`git diff --staged`|Staged changes|
|`git stash`|Temporarily save changes|
|`git stash pop`|Restore stashed changes|
|`git reset HEAD~1`|Undo last commit (keep changes)|
|`git revert <hash>`|Undo commit with new commit|

---

## ⭐ Git Branching – Full Reference `ADVANCED`

**Branching Strategies:**

|Strategy|When Used|Branches|
|---|---|---|
|Git Flow|Scheduled releases|main, develop, feature, release, hotfix|
|GitHub Flow|Continuous delivery|main, feature|
|Trunk-based|High-frequency deploys|main (+ short-lived feature)|

**All Branching Commands:**

```bash
git branch                    # List local branches
git branch -a                 # List all (local + remote)
git branch feature/login      # Create branch
git checkout feature/login    # Switch to branch
git checkout -b feature/login # Create + switch
git branch -d feature/login   # Delete (safe)
git branch -D feature/login   # Force delete
git push -u origin main       # Push + set upstream
git pull origin main          # Pull latest from remote
git merge feature/login       # Merge into current branch
git rebase main               # Rebase onto main
```

---

# 🔥 DOCKER – VERY HIGH PROBABILITY

---

## ⭐ Docker Core Concepts `MUST KNOW`

**Key Terms:**

|Term|Definition|
|---|---|
|Image|Read-only template for creating containers|
|Container|Running instance of an image|
|Dockerfile|Script to build a Docker image|
|Registry|Storage for images (Docker Hub)|
|Volume|Persistent data storage|
|Network|Communication between containers|
|Compose|Multi-container app definition|

---

## ⭐ Dockerize a Node.js App `IMPORTANT`

**Dockerfile:**

```dockerfile
# Use official Node.js 18 base image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package files first (layer caching optimization)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy remaining source code
COPY . .

# Expose application port
EXPOSE 3000

# Command to run the application
CMD ["node", "app.js"]
```

**Explanation of each instruction:**

|Instruction|Purpose|
|---|---|
|`FROM`|Base image to build upon|
|`WORKDIR`|Sets working directory (creates if not exists)|
|`COPY`|Copy files from host to container|
|`RUN`|Execute command during build|
|`EXPOSE`|Documents which port app listens on|
|`CMD`|Default command when container starts|
|`ENV`|Set environment variables|
|`ARG`|Build-time variables|

**Build and Run:**

```bash
# Build image
docker build -t my-node-app .

# Run container
docker run -d -p 3000:3000 --name my-app my-node-app

# View logs
docker logs my-app

# Enter container shell
docker exec -it my-app bash
```

---

## ⭐ Docker Networking – MongoDB Setup `IMPORTANT`

**Create Network + Run MongoDB:**

```bash
# Step 1: Create a custom Docker network
docker network create mongo-net

# Step 2: Run MongoDB container on the network
docker run -d \
  --name mongo \
  --network mongo-net \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=secret \
  -v mongo-data:/data/db \
  mongo:latest

# Step 3: Run Mongo Express (web UI for MongoDB)
docker run -d \
  --name mongo-express \
  --network mongo-net \
  -p 8081:8081 \
  -e ME_CONFIG_MONGODB_SERVER=mongo \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=secret \
  mongo-express

# Access Mongo Express at http://localhost:8081
```

**Why custom network?**

- Containers on same network can communicate by **container name**
- `mongo-express` connects to `mongo` using hostname `mongo`
- Isolated from other Docker networks (security)

---

## ⭐ PostgreSQL with Docker `IMPORTANT`

```bash
# Pull PostgreSQL image
docker pull postgres:latest

# Run PostgreSQL container
docker run -d \
  --name postgres-user1 \
  -e POSTGRES_PASSWORD=pass \
  -e POSTGRES_USER=admin \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  -v pgdata:/var/lib/postgresql/data \
  postgres:latest

# Connect to PostgreSQL using psql
docker exec -it postgres-user1 psql -U postgres

# Inside psql:
# \l          → list databases
# \c mydb     → connect to database
# \dt         → list tables
# \q          → quit

# Stop and remove container
docker stop postgres-user1
docker rm postgres-user1

# Remove volume (delete data permanently)
docker volume rm pgdata
```

**Essential Docker Commands:**

|Command|Purpose|
|---|---|
|`docker ps`|List running containers|
|`docker ps -a`|List all containers|
|`docker images`|List all images|
|`docker pull <image>`|Download image|
|`docker rmi <image>`|Remove image|
|`docker stop <name>`|Stop container|
|`docker rm <name>`|Remove container|
|`docker logs <name>`|View container logs|
|`docker inspect <name>`|Detailed container info|
|`docker network ls`|List networks|
|`docker volume ls`|List volumes|

---

## ⭐ Docker Compose `BONUS – HIGH PROBABILITY`

**What is Docker Compose?** A tool to define and run **multi-container** applications using a YAML file.

```yaml
# docker-compose.yml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - mongo
    environment:
      - MONGO_URL=mongodb://mongo:27017/mydb
    networks:
      - app-net

  mongo:
    image: mongo:latest
    volumes:
      - mongo-data:/data/db
    networks:
      - app-net

networks:
  app-net:

volumes:
  mongo-data:
```

```bash
docker compose up -d      # Start all services
docker compose down       # Stop all services
docker compose logs       # View logs
docker compose ps         # List containers
```

---

# 🔥 TERRAFORM – OPTIONAL BUT SCORING

---

## ⭐ Terraform Basics `SCORING`

**Definition:** Terraform is an **Infrastructure as Code (IaC)** tool by HashiCorp that lets you define and provision cloud infrastructure using declarative configuration files.

**Key Concepts:**

|Concept|Description|
|---|---|
|Provider|Cloud platform plugin (AWS, Azure, GCP)|
|Resource|Infrastructure component to create|
|State|Terraform's record of real infrastructure|
|Plan|Preview of changes before applying|
|Apply|Execute the changes|
|Destroy|Tear down infrastructure|

**EC2 Instance Configuration:**

```hcl
# Configure AWS Provider
provider "aws" {
  region = "ap-south-1"   # Mumbai region
}

# Create EC2 Instance
resource "aws_instance" "app" {
  ami           = "ami-00bb6a80f01cf6abc"  # Amazon Linux 2 AMI
  instance_type = "t2.micro"               # Free tier eligible

  tags = {
    Name        = "AppServerInstance"
    Environment = "Production"
    ManagedBy   = "Terraform"
  }
}

# Output the public IP
output "public_ip" {
  value = aws_instance.app.public_ip
}
```

**Terraform Workflow Commands:**

```bash
terraform init      # Initialize (download providers)
terraform fmt       # Format code
terraform validate  # Check syntax
terraform plan      # Preview changes
terraform apply     # Create/update resources
terraform destroy   # Delete all resources
terraform show      # Show current state
```

**Terraform vs Ansible:**

|Feature|Terraform|Ansible|
|---|---|---|
|Purpose|Provision infrastructure|Configure software|
|Type|Declarative|Procedural|
|State|Maintains state file|Stateless|
|Best for|Cloud infra (VMs, networks)|App deployment, config|

---

# 🚀 FINAL EXAM STRATEGY

---

## 🔥 GUARANTEED QUESTIONS (From QB + PYQ)

|Topic|Marks|Difficulty|Priority|
|---|---|---|---|
|Git commands (diagram)|5–7|Easy|🔴 Must|
|Shell script|5–7|Easy|🔴 Must|
|Docker commands|5–7|Medium|🔴 Must|
|CI/CD lifecycle|5|Easy|🔴 Must|
|Orchestration|2–3|Easy|🟡 Important|
|Linux directories/commands|2–3|Easy|🟡 Important|
|RPM vs Debian|3–5|Easy|🟡 Important|
|Terraform EC2|5–7|Medium|🟢 Optional|

## 🎯 MINIMUM VIABLE PREP

Prepare only these 3 topics → score **20–25/30 easily**:

1. **Git commands** – init, add, commit, branch, push
2. **Docker basics** – Dockerfile, run, network, postgres
3. **Shell script** – the monitoring script with explanation

## 📅 REVISION ORDER (Last Day)

```
Hour 1: Git commands + branching + hotfix
Hour 2: Docker Dockerfile + networking + postgres
Hour 3: Shell script (memorize + understand)
Hour 4: Short answers (Linux + SDLC + Orchestration)
```

---

> 🔗 **Related Notes:** [[Full Stack Development QB]] | [[Functional Programming QB]] | [[Software Project Management QB]]