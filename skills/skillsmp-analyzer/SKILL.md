---
name: skillsmp-analyzer
description: Analyze skills from skillsmp.com website. Use when user provides a skillsmp.com URL (e.g., https://skillsmp.com/zh/skills/...) and wants to understand what the skill does, its domain (frontend/backend/other), target use cases, and programming languages involved.
---

# SkillsMP Skill Analyzer

Analyze skills hosted on skillsmp.com to extract key information.

## Workflow

1. **Receive URL**: User provides a skillsmp.com skill URL
2. **Fetch Content**: Attempt to fetch the page content using WebFetch tool
3. **Handle Access Issues**: If blocked by Cloudflare or other protection:
   - Ask user to manually copy and paste the skill content from the webpage
   - Alternatively, ask user to provide the raw skill file content
4. **Analyze Content**: Parse the skill content and extract:
   - **Problem Solved**: What problem does this skill address?
   - **Domain**: Frontend, Backend, DevOps, Data Science, AI/ML, or Other
   - **Programming Languages**: Languages mentioned or required
   - **Target Users**: Who would benefit from this skill?
   - **Key Features**: Main capabilities provided

## Analysis Template

When analyzing a skill, provide output in this format:

```
## Skill Analysis

**Name**: [Skill name]

**Problem Solved**: 
[Description of the problem this skill addresses]

**Domain**: 
[Frontend | Backend | Full-stack | DevOps | Data Science | AI/ML | Other]

**Programming Languages**: 
[List of languages, e.g., Python, JavaScript, TypeScript]

**Target Users**: 
[Who would use this skill]

**Key Features**:
- [Feature 1]
- [Feature 2]
- [Feature 3]

**Summary**:
[1-2 sentence summary of the skill]
```

## Fallback Instructions

If WebFetch fails (403, timeout, etc.):

1. Inform user that direct access is blocked
2. Request user to:
   - Open the URL in browser
   - Copy the skill content (usually displayed as markdown)
   - Paste it into the chat
3. Proceed with analysis once content is provided

## Domain Classification Guide

- **Frontend**: React, Vue, CSS, HTML, browser APIs, UI/UX
- **Backend**: Node.js, Python, databases, APIs, servers
- **Full-stack**: Combination of frontend and backend
- **DevOps**: CI/CD, Docker, Kubernetes, cloud deployment
- **Data Science**: Data analysis, visualization, pandas, notebooks
- **AI/ML**: Machine learning, LLMs, model training, prompts
- **Other**: Documentation, workflows, general productivity
