# CommandBridge Safety Policy

## Purpose
CommandBridge is a powerful local automation tool. This safety policy exists to reduce accidental harm while preserving user freedom and control.

Safety is implemented through **layered protections**, not hard restrictions.

---

## Disclaimer and Limitation of Responsibility

CommandBridge is a powerful local automation tool that can control applications, files, and system input on the user’s machine.

By using CommandBridge, the user acknowledges and agrees that:

- All actions are executed **locally on the user’s own system**
- The user is fully responsible for any commands they enter
- The software performs actions **as requested by the user**, either directly or through AI-assisted interpretation
- Automation actions may be destructive if misused, including file deletion or data modification

CommandBridge is provided **“as is”**, without warranty of any kind, express or implied. The developer assumes no responsibility for data loss, system damage, unintended behavior, or consequences resulting from use or misuse of the software.

It is the user’s responsibility to:
- Review commands before execution
- Confirm high-impact actions when prompted
- Maintain backups of important data
- Use the software in compliance with applicable laws and policies

Use of CommandBridge constitutes acceptance of these terms.

---

## Safety Layers

### 1. Hard Rules
These rules are enforced before any AI evaluation.

Examples:
- Protected system directories cannot be modified
- Core operating system files cannot be deleted
- Certain irreversible operations are flagged automatically

These rules cannot be overridden.

---

### 2. AI Risk Assessment
The AI evaluates each command for:
- Potential system impact
- Data sensitivity
- Destructive behavior

The AI returns:
- A risk level (low, medium, high)
- A plain-language explanation

---

### 3. User Confirmation
High-impact actions require explicit confirmation, such as:
- File deletion
- Email sending
- Overwriting data
- Bulk operations

The user must approve before execution continues.

---

## Operating Modes

### Safe Mode
- Read-only actions by default
- Destructive actions blocked or heavily confirmed

---

### Hardcore Mode
- Most actions allowed
- Confirmations still required for destructive operations
- Intended for advanced or trusted use

Mode selection is controlled locally through configuration. If you are in hardcode mode, you are taking on the risk of anything that occurs as a result.

---

## Logging and Accountability
All actions are logged locally, including:
- User command
- Safety evaluation
- Execution steps
- Errors or cancellations

Logs provide transparency and aid debugging.

---

## Philosophy
The goal is not to prevent powerful actions, but to prevent accidental or unclear ones. The user remains in control at all times.