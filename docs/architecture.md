# CommandBridge Architecture

## Overview
CommandBridge is a **local-first desktop automation agent** designed to translate natural-language user commands into real actions on the user’s own computer.

The system is intentionally split so that:
- **AI is responsible for reasoning and decision-making**
- **Local code is responsible for execution**

All automation occurs on the user’s machine. There is no server-side execution, no cloud backend, and no remote control layer. The only optional external dependency is an AI model used for reasoning and planning.

---

## High-Level Execution Flow

The CommandBridge pipeline follows a clear, linear flow:

User Input  
→ Safety Review  
→ Planning  
→ Local Execution  
→ Logging and Feedback  

Each stage has a single responsibility and communicates only with adjacent stages.

---

## Core Design Principles

### 1. Local-First Execution
CommandBridge runs entirely on the user’s system. This includes:
- Mouse and keyboard input
- Browser automation
- File system access
- Application control

No system actions are executed remotely.

---

### 2. AI as the Brain, Not the Hands
AI is used only for **interpretation and reasoning**, including:
- Understanding user intent
- Evaluating safety and risk
- Generating structured execution plans

AI never directly controls the operating system. All real actions are performed by deterministic local code.

---

### 3. Capability-Based Design
CommandBridge does not define individual commands or scenarios.

Instead, it exposes a small set of **capabilities**, such as:
- Browser interaction
- Operating system control
- File system operations
- Mouse and keyboard input
- Email interaction

The AI dynamically combines these capabilities to fulfill user requests. This approach avoids hardcoding behaviors while keeping execution predictable.

---

### 4. Safety Before Execution
Every command is evaluated for risk before execution.  
High-impact or destructive actions require explicit user confirmation.

Safety checks occur before any system-level action is taken.

---

### 5. Visibility and Transparency
All actions are:
- Executed visibly on screen
- Logged locally
- Reported back to the user in real time

This ensures the user always understands what the system is doing.

---

## Component Architecture

### User Interface Layer (`ui/`)
Responsibilities:
- Accept free-form user input
- Display execution status and logs
- Present warnings and confirmation dialogs

The UI does not perform automation or AI reasoning. It communicates only with the Orchestrator.

---

### Agent Layer (`agent/`)
Responsibilities:
- Coordinate the execution pipeline
- Perform safety evaluation
- Generate execution plans
- Maintain short-term contextual memory

This layer may call AI models but does not interact directly with the operating system.

---

### Actions Layer (`actions/`)
Responsibilities:
- Perform all real-world execution
- Control mouse and keyboard input
- Interact with the browser
- Manage files and applications

This layer contains no AI logic. It executes instructions passed to it in a controlled and observable manner.

---

### Core Layer (`core/`)
Responsibilities:
- Application configuration
- Logging and auditing
- Shared data models
- Error handling and exceptions

This layer supports all other components.

---

## Example Execution

Command:
> “Open Gmail and summarize my last 5 emails”

Execution flow:
1. The UI sends the command to the Orchestrator  
2. The Safety module evaluates potential risk  
3. The Planner generates a structured execution plan  
4. The Actions layer executes browser and text operations locally  
5. Results and logs are displayed to the user  

---

## Architectural Summary
CommandBridge separates **reasoning from execution**, favors **local control**, and prioritizes **user visibility and safety**. The architecture is modular by design, allowing new capabilities to be added without restructuring the system.

The result is a powerful, flexible automation tool that remains understandable, debuggable, and user-controlled.