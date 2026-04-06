---
name: project-learner
description: |
  Help users quickly understand and get started with the current working directory project. Use this skill when users want to: (1) Learn about a new codebase, (2) Get a project overview or architecture explanation, (3) Understand project structure, tech stack, or dependencies, (4) Get a quick-start guide for development setup, (5) Understand core business logic or workflows, (6) Ask questions like "what is this project", "how does this work", "help me understand this codebase", "give me an overview", or "how do I get started".
---

# Project Learner

Analyze the current working directory project and help users quickly understand and get started.

## Workflow

### Step 1: Project Discovery

Gather essential project information by examining these files (in order of priority):

1. **Package/Config files** (identify tech stack):
   - `package.json`, `composer.json`, `Cargo.toml`, `go.mod`, `pom.xml`, `build.gradle`
   - `pyproject.toml`, `setup.py`, `requirements.txt`
   - `Gemfile`, `pubspec.yaml`, `*.csproj`, `*.sln`

2. **Documentation** (understand purpose):
   - `README.md`, `README.*`, `docs/`
   - `CONTRIBUTING.md`, `ARCHITECTURE.md`

3. **Configuration** (understand setup):
   - `.env.example`, `docker-compose.yml`, `Dockerfile`
   - Config directories: `config/`, `.config/`

4. **Directory structure** (understand organization):
   - Use `ls` or glob to map top-level directories
   - Identify patterns: `src/`, `lib/`, `app/`, `components/`, `services/`, `models/`

### Step 2: Generate Project Overview

After discovery, produce a structured analysis covering:

#### 2.1 Project Identity
- Project name and brief description
- Primary purpose/problem it solves
- Target users or use cases

#### 2.2 Tech Stack
- Programming language(s)
- Framework(s) and major libraries
- Database/storage (if applicable)
- Build tools and package manager

#### 2.3 Architecture Overview
- High-level architecture pattern (MVC, microservices, monolith, etc.)
- Key directories and their purposes
- Entry points (main files, index files)
- Core modules/components

#### 2.4 Core Business Logic
- Identify main domain concepts
- Key workflows or data flows
- Important abstractions or patterns used

### Step 3: Quick-Start Guide

Provide actionable steps to get started:

1. **Prerequisites**: Required tools, versions, system dependencies
2. **Installation**: Commands to install dependencies
3. **Configuration**: Required env vars or config files
4. **Running**: Commands to start development/run the project
5. **Testing**: How to run tests (if applicable)
6. **Common Tasks**: Frequently used commands or scripts

### Step 4: Answer Follow-up Questions

Be ready to dive deeper into:
- Specific modules or components
- How certain features work
- Where to make specific changes
- Debugging or troubleshooting tips

## Output Format

Structure the output as:

```
## Project Overview: [Project Name]

### What is this project?
[Brief description]

### Tech Stack
- Language: [...]
- Framework: [...]
- [Other relevant tech]

### Project Structure
[Directory tree or key folders explanation]

### Architecture
[High-level architecture explanation]

### Core Concepts
[Key domain concepts and business logic]

### Quick Start

1. Prerequisites
   [Required tools]

2. Installation
   [Commands]

3. Configuration
   [Setup steps]

4. Running
   [Start commands]

### Key Files to Explore
[List of important files for deeper understanding]
```

## References

- **Tech Stack Patterns**: See [references/tech-stack-patterns.md](references/tech-stack-patterns.md) for quick lookup of framework/language detection patterns

## Guidelines

- Prioritize accuracy over completeness - only include information you can verify from the codebase
- Use the project's own terminology and naming conventions
- If the project lacks documentation, note this and provide what can be inferred from code
- For large projects, focus on the most important parts first
- Adapt language to user's preference (detected from their query)
- Keep explanations concise but informative
