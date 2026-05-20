# CLIANT

# AI-Powered Linux Terminal Assistant

CLIANT (CLI Agent) is an intelligent AI-powered Linux terminal assistant designed to simplify Linux command-line interaction using natural language.

Instead of memorizing Linux commands, users can type simple instructions such as:

```text
show files
install neovim
check memory usage
```

CLIANT converts these requests into executable Linux commands using a local Large Language Model (LLM).

The project is specially designed for:

- beginners learning Linux
- students exploring terminal workflows
- developers wanting AI-assisted CLI automation
- offline Linux AI assistance

CLIANT runs fully locally using Ollama and lightweight LLMs such as Qwen2.5 3B.

---

# Features

## Natural Language Linux Commands

Example:

```text
> show files
```

CLIANT executes:

```bash
ls -la
```

---

## Direct Command Mode

Use:

```text
::command
```

Example:

```text
::pwd
```

This skips AI processing and directly executes the command.

---

## Safety System

CLIANT includes:

- dangerous command detection
- confirmation prompts
- recursive safety checks
- command risk classification

Commands such as:

```text
rm -rf /
mkfs
```

are blocked automatically.

---

## Background Tasks

Long-running commands can execute in the background.

---

## Auto Repair System

If commands fail:

- CLIANT analyzes the error
- gathers system information
- generates fixes
- retries automatically

---

## Session Memory

CLIANT remembers:

- previous tasks
- executed commands
- user habits
- local command mappings

This improves future responses.

---

# Tech Stack

## Language

- Python 3

## AI Runtime

- Ollama

## LLM

- Qwen2.5 3B

## Linux Features

- subprocess management
- background execution
- command validation
- session memory
- auto-repair loops

---

# Project Goal

CLIANT is built primarily for students and beginners who want to learn Linux safely and interactively.

The project helps users:

- understand terminal workflows
- reduce fear of Linux terminals
- learn real Linux commands
- automate repetitive tasks
- explore Linux safely

CLIANT acts as both:

- an AI terminal assistant
- a Linux learning companion

---

# Quick Installation

## Download Package

Extract:

```text
cliant-package.zip
```

Go into:

```bash
cd cliant-package
```

---

## Make Installer Executable

```bash
chmod +x cliant-installer.sh
```

---

## Run Installer

```bash
./cliant-installer.sh
```

---

## Reload Terminal

```bash
source ~/.bashrc
```

---

## Start CLIANT

```bash
cliant
```

---

# Manual Setup Guide (If Installer Fails)

This section explains how to setup CLIANT completely from scratch.

---

# Step 1 — Clone Repository

Clone the project:

```bash
git clone <your-repository-url>
```

Go into the repository:

```bash
cd CLIANT
```

---

# Step 2 — Install Python

Check Python:

```bash
python3 --version
```

If Python is missing:

## Arch Linux

```bash
sudo pacman -S python
```

## Ubuntu / Debian

```bash
sudo apt install python3 python3-pip python3-venv
```

## Fedora

```bash
sudo dnf install python3 python3-pip
```

---

# Step 3 — Install Ollama

Install Ollama:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Verify installation:

```bash
ollama --version
```

---

# Step 4 — Start Ollama

Run:

```bash
ollama serve
```

Keep it running.

Or run in background:

```bash
nohup ollama serve > /dev/null 2>&1 &
```

---

# Step 5 — Download AI Model

Download the model used by CLIANT:

```bash
ollama pull qwen2.5:3b
```

Wait until download completes.

---

# Step 6 — Create CLIANT Data Directory

Create required directories:

```bash
mkdir -p ~/.local/share/cliant
mkdir -p ~/.local/bin
```

---

# Step 7 — Create Virtual Environment

Inside the repository:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

---

# Step 8 — Install Dependencies

Install requirements:

```bash
pip install -r requirements.txt
```

---

# Step 9 — Prepare CLIANT Executable

Make CLIANT executable:

```bash
chmod +x cliant
```

---

# Step 10 — Copy CLIANT Into User Directory

Copy executable:

```bash
cp cliant ~/.local/share/cliant/cliant
```

---

# Step 11 — Create Global Launcher

Create launcher file:

```bash
nano ~/.local/bin/cliant
```

Paste:

```bash
#!/bin/bash
"$HOME/CLIANT/venv/bin/python" "$HOME/.local/share/cliant/cliant" "$@"
```

Save the file.

---

# Step 12 — Make Launcher Executable

```bash
chmod +x ~/.local/bin/cliant
```

---

# Step 13 — Add CLIANT To PATH

Open:

```bash
nano ~/.bashrc
```

Add:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Save and reload:

```bash
source ~/.bashrc
```

---

# Step 14 — Verify Installation

Check:

```bash
which cliant
```

Expected:

```text
/home/<user>/.local/bin/cliant
```

---

# Step 15 — Start CLIANT

Run:

```bash
cliant
```

You should see:

```text
CLIANT session started.
```

---

# Example Usage

## Natural Language

```text
> show files
```

---

## Direct Commands

```text
> ::pwd
```

---

## Multi-Step Tasks

```text
> install docker and start the service
```

CLIANT automatically creates a task plan.

---

# Built-In Commands

## Show Running Tasks

```text
show running tasks
```

---

## Show Completed Tasks

```text
show completed tasks
```

---

## Enable Dry Run

```text
dry-run on
```

Commands will be simulated only.

---

## Disable Dry Run

```text
dry-run off
```

---

## Show Session Memory

```text
show session
```

---

## Clear Session Memory

```text
clear session
```

---

# File Structure

Installed CLIANT files:

```text
~/.local/share/cliant/
│
├── cliant
├── sessionMemory.json
├── localCommandMappings.json
└── userCommandProfiles.json
```

Global launcher:

```text
~/.local/bin/cliant
```

---

# Troubleshooting

# Ollama Not Found

Check:

```bash
ollama --version
```

If missing:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

---

# Model Not Found

Run:

```bash
ollama pull qwen2.5:3b
```

---

# PATH Issues

Check:

```bash
echo $PATH
```

Ensure:

```text
$HOME/.local/bin
```

exists in PATH.

---

# Permission Errors

Never install CLIANT into:

```text
/usr/local/bin
```

without proper permissions.

Use:

```text
~/.local/bin
```

instead.

---

# Virtual Environment Problems

Recreate environment:

```bash
rm -rf venv
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

# Educational Purpose

CLIANT is designed as an educational Linux assistant.

The project encourages users to:

- learn Linux safely
- observe real commands
- understand terminal workflows
- improve command-line confidence
- explore Linux interactively

It combines:

- AI
- operating systems
- Linux automation
- local LLM inference
- command-line tooling

into a beginner-friendly learning platform.

---

# Future Improvements

Planned upgrades include:

- fine-tuned Linux LLM
- embeddings-based memory
- voice interaction
- plugin system
- GUI dashboard
- package manager abstraction
- command verification engine
- multi-agent architecture

---

# License

This project is open-source and intended for educational and research purposes.

