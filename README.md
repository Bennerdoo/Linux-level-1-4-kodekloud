# KodeKloud Engineer - Linux Tasks & Solutions (Levels 1 - 4)

Welcome to the **KodeKloud Engineer - Linux Tasks (Level 1 - 4)** repository! This project documents step-by-step solutions, Linux System Administration commands, cloud configurations, and practical notes for real-world DevOps tasks across Levels 1 through 4 on KodeKloud (xFusionCorp Industries / Nautilus infrastructure).

---

## 📌 Repository Overview

This repository serves as a practical handbook for Linux System Administration, DevOps automation, and AWS Cloud operations across KodeKloud's **Level 1 to Level 4** Linux Engineer labs. Each guide includes task specifications, step-by-step terminal execution, verification commands, and key administrative notes.

---

## 📁 Repository Structure

```text
.
├── Level 1/
│   ├── day 1 - Custom Apache user setup.md
│   ├── Day 2 - Group Creation and User Assignment.md
│   ├── Day 3 - Linux User Setup with Non-Interactive Shell.md
│   └── Day 4 - Service User Creation without Home Directory.md
├── Level 2/   # (Upcoming / In-Progress)
├── Level 3/   # (Upcoming / In-Progress)
└── Level 4/   # (Upcoming / In-Progress)
```

---

## 📑 Completed Tasks & Topics

| Day | Task Title | Domain | Core Commands / Key Concepts |
|---|---|---|---|
| **Day 1** | [Custom Apache User Setup](<./Level 1/day 1 - Custom Apache user setup.md>) | User Management | `useradd -u -d -m`, custom UID, custom home directory |
| **Day 2** | [Group Creation and User Assignment](<./Level 1/Day 2 - Group Creation and User Assignment.md>) | Access Control | `groupadd`, `usermod -aG`, `useradd -G`, `id` |
| **Day 3** | [Subnet Creation under Default VPC](<./Level 1/Day 3 - Linux User Setup with Non-Interactive Shell.md>) | AWS Cloud Infrastructure | AWS VPC Dashboard, Subnet Creation, IPv4 CIDR allocation |
| **Day 4** | [Service User Creation without Home Directory](<./Level 1/Day 4 - Service User Creation without Home Directory.md>) | Security & Service Accounts | `useradd -M`, `/etc/passwd`, home directory validation |

---

## 🛠️ Core Concepts Covered

- **Linux Account & Security Management**:
  - Creating system users with explicit UIDs and custom home directories (`-u`, `-d`).
  - Configuring non-interactive/service user accounts without dedicated home directories (`-M`).
  - Managing secondary group memberships using `usermod -aG` without overwriting existing groups.
- **System Verification & Inspection**:
  - Verifying user parameters with `id <username>` and inspecting `/etc/passwd`.
  - Checking file/directory ownership using `ls -ld`.
- **AWS Infrastructure**:
  - Provisioning VPC subnets for incremental cloud migration strategy.

---

## 🚀 How to Use

1. Browse to the [`Level 1/`](./Level%201/) folder.
2. Select any day's Markdown file to view the problem statement, SSH requirements, step-by-step command sequence, and output verification instructions.

---

## 👤 Author

- GitHub: [@Bennerdoo](https://github.com/Bennerdoo)
