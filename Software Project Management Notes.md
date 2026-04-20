# 📋 Software Project Management Notes

**Marks:** 30 | **Priority:** 🟡 MEDIUM  
**Related:** [[Software Project Management PYQ]] | [[Software Project Management QB]] | [[README]]

---

## 📌 Table of Contents

1. [[#Unit 1 – Basics of Project Management]]
2. [[#Unit 2 – Project Life Cycle]]
3. [[#Unit 3 – Scope Time and Cost Management]]
4. [[#Unit 4 – Quality Management]]
5. [[#Unit 5 – Human Resource Management]]
6. [[#Unit 6 – Software Metrics]]
7. [[#Unit 7 – CMM PSP and TSP]]
8. [[#Unit 8 – Risk and Communication Management]]
9. [[#🔥 Most Expected Questions]]

---

## Unit 1 – Basics of Project Management

### 1.1 What is a Project? (⭐ IMPORTANT)

**Definition:**  
A project is a **temporary endeavor** undertaken to create a **unique product, service, or result**, with a defined beginning and end.

**Characteristics of a project:**
- **Temporary** – has a defined start and end date
- **Unique** – creates something that did not exist before
- **Goal-oriented** – has specific objectives
- **Resources** – uses people, time, money, materials
- **Progressive elaboration** – details are developed as project progresses

**Examples:**
- Developing a mobile banking app
- Building an e-commerce website
- Implementing a new HR system
- Migrating data to cloud

---

### 1.2 What is Project Management? (⭐ IMPORTANT)

**Definition:**  
Project management is the **application of knowledge, skills, tools, and techniques** to project activities to meet project requirements. It ensures the project is completed within scope, time, and cost.

**Key functions:**
- Planning (what, when, who, how)
- Organizing (structure, teams)
- Leading (motivating, directing)
- Controlling (tracking, corrective action)

---

### 1.3 Key Objectives of Project Management (⭐ REPEATED)

- Complete project **on time** (within schedule)
- Complete within **budget** (within cost)
- Meet **quality standards**
- Achieve **project scope** (all deliverables)
- Ensure **customer satisfaction**
- Efficient **resource utilization**

---

### 1.4 Types of Project Management Tools (⭐ IMPORTANT)

| Tool | Purpose |
|---|---|
| **Gantt Chart** | Visual timeline of tasks and their durations |
| **PERT Chart** | Shows task dependencies and critical path |
| **WBS (Work Breakdown Structure)** | Hierarchical decomposition of project scope |
| **CPM (Critical Path Method)** | Identifies longest sequence of tasks |
| **MS Project / Jira / Trello** | Software tools for planning and tracking |

---

### 1.5 Organizational Structures (⭐ IMPORTANT)

| Type | PM Authority | Resource Control | Communication |
|---|---|---|---|
| **Functional** | Low (functional manager in charge) | Functional manager | Formal, hierarchical |
| **Matrix (Weak)** | Low | Functional manager | Mixed |
| **Matrix (Balanced)** | Medium | Shared | Mixed |
| **Matrix (Strong)** | High | PM | Direct |
| **Projectized** | Very High | PM | Direct, fast |
| **Composite** | Varies | Varies | Mixed |

---

### 1.6 Triple Constraint (⭐ VERY IMPORTANT)

**Definition:**  
Every project is constrained by three factors. Changing one affects the others.

```
           Scope
            /\
           /  \
          /    \
         /      \
        /________\
      Time      Cost

Quality is at the center — affected by all three
```

- **Scope** – What needs to be done
- **Time** – How long it will take
- **Cost** – How much it will cost
- **Quality** – How well it needs to be done

**Example:**
- If you **add scope** (more features) → need more **time** or more **cost**
- If you **reduce time** → need more **cost** (overtime) or **reduce scope**

---

## Unit 2 – Project Life Cycle

### 2.1 Project Life Cycle Phases (⭐ VERY IMPORTANT – REPEATED)

The project life cycle consists of **5 phases**:

```
Initiation → Planning → Execution → Monitoring & Control → Closure
```

#### Phase 1: Initiation
- **Purpose:** Define and authorize the project
- **Activities:**
  - Identify need/problem
  - Conduct feasibility study
  - Define high-level scope
  - Identify key stakeholders
  - Create Project Charter
- **Output:** Project Charter, Stakeholder Register

#### Phase 2: Planning
- **Purpose:** Define the roadmap for the project
- **Activities:**
  - Define detailed scope
  - Create Work Breakdown Structure (WBS)
  - Estimate costs and time
  - Identify risks
  - Create project schedule (Gantt chart)
  - Plan communications
- **Output:** Project Management Plan

#### Phase 3: Execution
- **Purpose:** Do the actual work
- **Activities:**
  - Develop the product/service
  - Manage team
  - Manage stakeholders
  - Quality assurance
  - Procurement
- **Output:** Deliverables, Work performance data

#### Phase 4: Monitoring & Control
- **Purpose:** Track and manage project performance
- **Activities:**
  - Compare actual vs planned
  - Manage changes
  - Report performance
  - Control scope, cost, time, quality
- **Output:** Change requests, Performance reports

#### Phase 5: Closure
- **Purpose:** Formally close the project
- **Activities:**
  - Deliver final product
  - Get customer acceptance
  - Release project team
  - Document lessons learned
  - Archive project documents
- **Output:** Final product, Lessons learned, Closed procurements

---

## Unit 3 – Scope, Time, and Cost Management

### 3.1 Scope Management (⭐ VERY IMPORTANT)

**Definition:**  
Scope management ensures the project includes **all the work required, and only the work required**, to complete the project successfully.

**Scope management processes:**

| Process | Description |
|---|---|
| **Scope Planning** | How scope will be defined and managed |
| **Scope Definition** | Detailed description of what's included/excluded |
| **Create WBS** | Break work into smaller manageable pieces |
| **Scope Verification** | Get stakeholder acceptance of deliverables |
| **Scope Control** | Monitor and manage scope changes |

**Scope creep:**  
Uncontrolled addition of features without adjusting time/cost. Major cause of project failure.

---

### 3.2 Work Breakdown Structure (WBS) (⭐ IMPORTANT)

**Definition:**  
WBS is a **hierarchical decomposition** of the total scope of work into smaller, manageable components.

```
Project: E-Commerce Website
│
├── Frontend Development
│   ├── Home Page
│   ├── Product Listing Page
│   └── Checkout Page
│
├── Backend Development
│   ├── User Authentication
│   ├── Product Management API
│   └── Payment Integration
│
├── Database Design
│   ├── User Schema
│   └── Product Schema
│
└── Testing
    ├── Unit Testing
    ├── Integration Testing
    └── User Acceptance Testing
```

**Benefits:**
- Makes project manageable
- Clear ownership for each task
- Easier to estimate costs and time
- Basis for scheduling

---

### 3.3 Time Management

**Definition:**  
Time management involves **planning, scheduling, and controlling** the project timeline to ensure on-time delivery.

**Processes:**
1. Define activities (from WBS)
2. Sequence activities (dependencies)
3. Estimate durations
4. Develop schedule
5. Control schedule

**Tools:**

**Gantt Chart:**
- Bar chart showing tasks vs time
- Horizontal bars show start, end, duration
- Shows task dependencies and overlaps

**CPM (Critical Path Method):**
- Identifies the **longest path** through the project
- Tasks on critical path have **zero float** (no slack)
- Delay in critical path = project delayed

**PERT Chart:**
- Shows task dependencies as a network
- Uses three estimates: optimistic, pessimistic, most likely
- Formula: `Expected time = (O + 4M + P) / 6`

---

### 3.4 Cost Management (⭐ IMPORTANT)

**Definition:**  
Cost management involves **estimating, budgeting, and controlling costs** to keep the project within the approved budget.

**Processes:**
1. **Cost Estimating** – how much each activity will cost
2. **Cost Budgeting** – aggregate estimates into overall budget
3. **Cost Control** – monitor actual costs vs budget

**Estimation techniques:**

| Technique | Description | Accuracy |
|---|---|---|
| **Analogous** | Based on similar past projects | Low-Medium |
| **Parametric** | Statistical models (cost per unit) | Medium |
| **Bottom-up** | Estimate each work package, then add up | High |
| **Three-point** | (Optimistic + 4×Most Likely + Pessimistic) / 6 | High |

**Earned Value Management (EVM):**
- **PV** (Planned Value) – budgeted cost of planned work
- **EV** (Earned Value) – budgeted cost of work performed
- **AC** (Actual Cost) – actual cost of work performed
- **CV** (Cost Variance) = EV - AC (negative = over budget)
- **SV** (Schedule Variance) = EV - PV (negative = behind schedule)

---

## Unit 4 – Quality Management

### 4.1 Quality Concepts (⭐ VERY IMPORTANT)

**Three Processes:**

#### Quality Planning
- **What:** Define what quality means for THIS project
- **When:** During planning phase
- **Output:** Quality management plan, quality metrics
- **Example:** "All pages must load in < 2 seconds"

#### Quality Assurance (QA)
- **What:** Audit processes to ensure standards are being followed
- **Focus:** **Process-oriented** (how we build it)
- **Goal:** **Prevent defects** before they occur
- **When:** During execution
- **Example:** Code reviews, following coding standards, training

#### Quality Control (QC)
- **What:** Monitor and test specific deliverables
- **Focus:** **Product-oriented** (what we built)
- **Goal:** **Detect defects** in the product
- **When:** During or after execution
- **Example:** Testing software, checking outputs against requirements

**QA vs QC Summary:**

| Feature | QA | QC |
|---|---|---|
| Focus | Process | Product |
| Goal | Prevention | Detection |
| When | During development | After/during development |
| Done by | QA team, everyone | QC/Test team |
| Example | Code standards, reviews | Testing, inspection |

---

### 4.2 Quality Tools

- **Pareto Chart** – 80% of problems come from 20% of causes
- **Control Charts** – show if process is in control over time
- **Fishbone (Ishikawa) Diagram** – root cause analysis
- **Flowcharts** – document processes
- **Benchmarking** – compare against best practices
- **Six Sigma** – methodology to reduce defects (3.4 defects per million)

---

## Unit 5 – Human Resource Management

### 5.1 Organizational Planning (⭐ IMPORTANT)

**Definition:**  
Identifying, documenting, and assigning **project roles, responsibilities, and reporting relationships**.

**Outputs:**
- **Responsibility Assignment Matrix (RAM)** – who does what
- **Organizational chart** – hierarchy
- **Job descriptions** – roles and skills needed
- **Staffing management plan** – when to acquire/release team

---

### 5.2 Staff Acquisition Process (⭐ IMPORTANT)

**Definition:**  
Getting the right people with the right skills for the project.

**Steps:**
1. **Identify** required skills and roles
2. **Recruit** – internal transfer or external hiring
3. **Select** – interviews, assessments
4. **Train** – fill skill gaps
5. **Assign** – assign to specific tasks
6. **Release** – plan how/when team members leave

---

### 5.3 Stakeholder Management (⭐ VERY IMPORTANT)

**Definition:**  
Stakeholders are **individuals or organizations** that are affected by or can affect the project's outcome.

**Types:**
- **Internal:** Project team, managers, executives
- **External:** Customers, vendors, regulatory bodies, public

**Stakeholder Management Steps:**
1. **Identify** – who are the stakeholders?
2. **Analyze** – what is their interest and power?
3. **Plan** – how to engage each stakeholder?
4. **Manage** – communicate, resolve concerns
5. **Monitor** – ongoing engagement

**Power-Interest Grid:**
```
         High Power
              │
  Manage      │    Manage
  Closely     │    Closely
  (satisfy)   │    (key players)
              │
──────────────┼──────────────── High Interest
              │
  Monitor     │    Keep
  (minimum    │    Informed
   effort)    │
              │
         Low Power
```

---

### 5.4 Conflict Management

**Sources of conflict:** Schedules, priorities, technical opinions, resources, cost

**Conflict resolution techniques (in order of preference):**
1. **Problem solving** (win-win) – address root cause
2. **Compromising** – each side gives up something
3. **Smoothing** – downplay differences, emphasize agreement
4. **Forcing** – PM imposes a solution (win-lose)
5. **Withdrawal** – avoid the conflict (temporary)

---

## Unit 6 – Software Metrics

### 6.1 What are Software Metrics? (⭐ IMPORTANT)

**Definition:**  
Software metrics are **quantitative measures** used to assess, control, and improve software development processes and products.

**Purposes:**
- Measure quality
- Estimate effort and cost
- Track progress
- Improve productivity
- Make informed decisions

**Types of metrics:**

| Type | Measures | Examples |
|---|---|---|
| **Product metrics** | Software product itself | Lines of code, complexity, defect density |
| **Process metrics** | Development process | Defect detection rate, review coverage |
| **Project metrics** | Project management | Cost variance, schedule variance |

---

### 6.2 Size-Oriented Metrics (LOC) (⭐ IMPORTANT)

**Lines of Code (LOC)** – counts the number of lines in source code

```
Productivity = LOC / person-month
Quality      = Defects / KLOC  (KLOC = 1000 lines of code)
Cost         = $/LOC
```

**Limitations of LOC:**
- Language-dependent (more lines in C than Python for same functionality)
- Bad programmers can inflate LOC
- Does not measure design quality

---

### 6.3 Function-Oriented Metrics (⭐ IMPORTANT)

**Function Points (FP)** – measure functionality delivered to user

**Components counted:**
1. External inputs (user data entry)
2. External outputs (reports, screens)
3. External queries (input/output pairs)
4. Internal logical files (data stored)
5. External interface files (data from other systems)

```
FP = Count × Complexity weight

Productivity = FP / person-month
Quality      = Defects / FP
Cost         = $ / FP
```

**Advantage over LOC:** Language-independent — works for any programming language

---

## Unit 7 – CMM, PSP, and TSP

### 7.1 Capability Maturity Model (CMM) (⭐ VERY VERY IMPORTANT)

**Definition:**  
CMM is a **framework developed by SEI (Software Engineering Institute)** to improve software development processes. It provides a structured path for organizations to improve from chaotic to optimized processes.

**Five Levels:**

| Level | Name | Description | Key Feature |
|---|---|---|---|
| 1 | **Initial** | Unpredictable, chaotic, ad hoc | Depends on individuals, "heroes" |
| 2 | **Managed** | Basic project management exists | Repeatable for similar projects |
| 3 | **Defined** | Standard processes across organization | Documented standards and procedures |
| 4 | **Quantitatively Managed** | Processes measured and controlled | Uses data and metrics |
| 5 | **Optimizing** | Continuous process improvement | Innovation and defect prevention |

**Diagram:**
```
Level 5: Optimizing      ████████████████████  ← Continuous improvement
Level 4: Quantitative    ████████████████      ← Measured processes
Level 3: Defined         ████████████          ← Standard processes
Level 2: Managed         ████████              ← Basic PM
Level 1: Initial         ████                  ← Chaotic (entry point)
```

**Key points to remember:**
- Most companies start at Level 1
- Moving up requires structured improvement effort
- Most mature software companies are at Level 3-4
- Level 5 is rare (NASA, Infosys)

---

### 7.2 Key Process Areas (KPAs) (⭐ IMPORTANT)

**Definition:**  
KPAs are **specific areas of improvement** required to achieve each CMM maturity level.

| Level | Key Process Areas |
|---|---|
| **Level 2** | Requirements Management, Project Planning, Project Tracking, Quality Assurance, Configuration Management |
| **Level 3** | Training, Software Product Engineering, Peer Reviews, Intergroup Coordination, Organization Process Focus |
| **Level 4** | Quantitative Process Management, Software Quality Management |
| **Level 5** | Defect Prevention, Technology Change Management, Process Change Management |

**Role of KPAs:**
- Improve process quality
- Standardize development practices
- Reduce defects
- Increase productivity
- Provide roadmap for improvement

---

### 7.3 PSP vs TSP (⭐ IMPORTANT)

| Feature | PSP (Personal Software Process) | TSP (Team Software Process) |
|---|---|---|
| **Level** | Individual | Team |
| **Focus** | Personal productivity and quality | Team performance and coordination |
| **Developed by** | Watts Humphrey (SEI) | Watts Humphrey (SEI) |
| **Goal** | Improve individual developer skills | Improve team-level process |
| **Data collected** | Time spent, defects, size | Team metrics, integration data |
| **When used** | Individual coding tasks | Team projects and sprints |

**PSP activities:**
- Planning (estimate size, time, defects)
- Development (design, code, test)
- Postmortem (analyze what happened)

**TSP activities:**
- Team launch (roles, goals, plans)
- Development cycles
- Team reviews and tracking

---

## Unit 8 – Risk and Communication Management

### 8.1 Risk Management (⭐ IMPORTANT)

**Definition:**  
Risk management is the systematic process of **identifying, analyzing, and responding** to project risks.

**Types of risks:**
- **Schedule risk** – tasks taking longer than expected
- **Technical risk** – technology doesn't work as planned
- **Resource risk** – key team members leave
- **Cost risk** – expenses exceed budget
- **External risk** – regulatory changes, market shifts

**Risk Management Process:**

| Step | Description |
|---|---|
| **Identify** | List all possible risks (brainstorm, checklists) |
| **Analyze** (Qualitative) | Rate each risk: Probability × Impact |
| **Analyze** (Quantitative) | Numerical analysis (Monte Carlo simulation) |
| **Plan Responses** | Define how to handle each risk |
| **Monitor & Control** | Track risks throughout project |

**Risk Response Strategies:**

| Strategy | Meaning | Example |
|---|---|---|
| **Avoid** | Eliminate the risk entirely | Change project scope to avoid risky area |
| **Mitigate** | Reduce probability or impact | More testing, prototype early |
| **Transfer** | Shift risk to third party | Insurance, outsource risky work |
| **Accept** | Acknowledge risk, no action | Set aside contingency budget |

**Risk register:**
| Risk | Probability | Impact | Score | Response |
|---|---|---|---|---|
| Key dev leaves | 20% | High | 8 | Cross-train team |
| API changes | 30% | Medium | 6 | Pin API version |

---

### 8.2 Importance of Risk Management (⭐ REPEATED)

- Identifies potential problems **before they occur**
- Reduces project failure rate
- Improves planning and decision-making
- Saves cost (preventive action is cheaper than crisis management)
- Increases stakeholder confidence

---

### 8.3 Communication Management (⭐ IMPORTANT)

**Definition:**  
Communication management ensures the **right information reaches the right people at the right time**.

**Importance:**
- Ensures all stakeholders are informed
- Reduces misunderstandings and conflicts
- Enables timely decisions
- Tracks project progress
- Builds team cohesion

**Communication processes:**
1. **Planning** – who needs what information, when, how
2. **Information Distribution** – making information available
3. **Performance Reporting** – collecting and distributing progress reports
4. **Managing Stakeholders** – satisfying needs and expectations

**Communication channels formula:**
```
Channels = n × (n-1) / 2
Where n = number of people

Example: 5 people → 5 × 4 / 2 = 10 channels
```

---

### 8.4 Information Distribution (⭐ REPEATED)

**Definition:**  
Making relevant information **available to project stakeholders** in a timely manner.

**Methods:**
- Meetings (team, status, steering committee)
- Email updates
- Status reports
- Project dashboards
- Intranet/SharePoint
- Direct communication

**Information to distribute:**
- Project status and progress
- Issues and risks
- Schedule updates
- Budget status
- Change requests

---

### 8.5 Solicitation and Procurement

**Solicitation:**  
The process of **obtaining information, quotations, or proposals** from potential vendors/suppliers.

**Documents used:**
- **RFP** (Request for Proposal) – detailed requirements, get full proposals
- **RFQ** (Request for Quotation) – get price quotes for specific items
- **RFI** (Request for Information) – gather market information

**Procurement process:**
1. Plan procurement (make or buy decision)
2. Conduct procurements (solicit sellers)
3. Select sellers
4. Administer contracts
5. Close contracts

---

## 🔥 Most Expected Questions

| Question | Marks | Frequency |
|---|---|---|
| CMM levels explanation | 4–5 | ⭐⭐⭐ |
| Project life cycle phases | 5 | ⭐⭐⭐ |
| QA vs QC | 4 | ⭐⭐⭐ |
| KPAs role | 3 | ⭐⭐ |
| Scope management process | 4 | ⭐⭐ |
| Risk management + strategies | 4–5 | ⭐⭐ |
| Stakeholder management | 3–4 | ⭐⭐ |
| PSP vs TSP | 4 | ⭐⭐ |
| Software metrics (LOC, FP) | 3–4 | ⭐⭐ |
| Information distribution | 3 | ⭐⭐ |
| Triple constraint | 2–3 | ⭐⭐ |
| Solicitation | 3 | ⭐ |

---

## 📝 Quick Revision Summary

```
SPM = delivering projects on time, within budget, meeting quality

Project = Temporary + Unique + Goal-oriented

Life Cycle: Initiation → Planning → Execution → Monitor → Closure

Triple Constraint: Scope ↔ Time ↔ Cost (change one → affects others)

Quality:
  QA = process focused = PREVENT defects
  QC = product focused = DETECT defects

CMM Levels:
  1 Initial (chaotic) → 2 Managed → 3 Defined → 4 Quantitative → 5 Optimizing

PSP = Individual level process improvement
TSP = Team level process improvement

Risk Responses: Avoid | Mitigate | Transfer | Accept

Communication = right info to right people at right time
Channels = n(n-1)/2
```

---

**See also:** [[Software Project Management PYQ]] | [[Software Project Management QB]] | [[README]]
