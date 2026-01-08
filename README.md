# GitHub Copilot for Repository Management Quest

## Quest Overview

Welcome to the **GitHub Copilot for Repository Management Quest** — an interactive learning experience designed for content developers who want to master GitHub Copilot's native features for repository management workflows. This quest simulates real-world scenarios using **real Microsoft Learn documentation**, covering common challenges like taking over unfamiliar repositories, triaging issue backlogs, and managing complex pull requests.

**What makes this quest unique:** You'll work with actual Microsoft Learn modules while mastering GitHub Copilot's workspace agent, custom agents, PR review, and external integrations (MCP tools).

## Learning Objectives

By completing this quest, you will:

1. **Master GitHub Copilot workspace exploration** — Use `@workspace` to quickly understand unfamiliar repositories
2. **Create custom agents and prompts** — Build specialized AI assistants for documentation tasks
3. **Implement efficient issue management** — Use Copilot to categorize, prioritize, and triage issues
4. **Develop PR review skills** — Leverage native Copilot PR review and `#pr` context
5. **Configure advanced agents** — Use tool permissions, model selection, and structured outputs
6. **Integrate external tools** — Use MCP (Model Context Protocol) for documentation verification

## Quest Structure

| Part | Duration | Scenarios | Focus |
|------|----------|-----------|-------|
| **[Part 1: Fundamentals](part-1-fundamentals/README.md)** | ~60 min | Module 0, Scenarios 1-2 | Workspace setup, exploration, issue triage |
| **[Part 2: Advanced](part-2-advanced/README.md)** | ~80 min | Scenarios 3-4 | PR review, advanced agents, MCP tools |

**Total Time:** ~2.5 hours (can be done in separate sessions)

### Scenario Overview

| Scenario | Name | Challenge |
|----------|------|-----------|
| **Module 0** | Workspace Preparation | Create custom agents and reusable prompts |
| **Scenario 1** | The Inheritance | Take over an unfamiliar documentation repository |
| **Scenario 2** | The Backlog Battle | Triage 12+ open issues efficiently |
| **Scenario 3** | The Big Merge | Review a large PR with native Copilot features |
| **Scenario 4** | The Agent Arsenal | Configure advanced agents with MCP integration |

---

## Prerequisites

- **Git fundamentals**: Basic understanding of repositories, commits, branches, and pull requests
- **Markdown knowledge**: Familiarity with markdown syntax
- **GitHub Copilot**: Active GitHub Copilot subscription (individual, business, or enterprise)
- **Tools**: VS Code with GitHub Copilot extensions, Git client, GitHub account

### Key Terms

| Term | Definition |
|------|------------|
| **Repository** | A folder containing your project's files, history, and version control data |
| **Fork** | A personal copy of someone else's repository on your GitHub account |
| **Clone** | Downloading a repository from GitHub to your local computer |
| **Branch** | A parallel version of your repository for isolated changes |
| **Pull Request (PR)** | A proposal to merge changes from one branch into another |
| **Issue** | A task, bug report, or feature request in a repository's issue tracker |

### GitHub Copilot Customization Features

| Feature | Location | Format | Use Case |
|---------|----------|--------|----------|
| **Agents** | `.github/agents/` | `.agent.md` | Specialized roles (e.g., Documentation Auditor) |
| **Prompts** | `.github/prompts/` | `.prompt.md` | Reusable templates (e.g., Content Audit) |
| **Instructions** | `.github/copilot-instructions.md` | Markdown | Repository-wide guidance for Copilot |
| **MCP Tools** | VS Code settings | JSON config | External integrations (GitHub, Microsoft Docs) |

---

## Getting Started

### 1. Install Prerequisites

1. **VS Code** — Download from https://code.visualstudio.com/
2. **GitHub Copilot extensions** — Install both:
   - [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
   - [GitHub Copilot Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat)
3. **Activate Copilot** — Sign in and link to your enterprise license: https://copilot.github.microsoft.com/
4. **Add MCP servers** (required for Part 2):
   - GitHub MCP server
   - Microsoft.docs.mcp server
   - See: https://code.visualstudio.com/mcp

### 2. Fork and Clone

1. **Fork this repository** — Click "Fork" at the top-right of this page
2. **Clone your fork**:

   ```bash
   git clone https://github.com/[your-username]/github-repo-management-quest-learn.git
   cd github-repo-management-quest-learn
   code .
   ```

### 3. Create Sample Content

Run the GitHub Actions workflows to create sample issues and PRs:

1. Go to your fork's **Actions** tab
2. Run **"Setup Quest Issues"** — Creates sample issues for Scenario 2
3. Run **"Setup Quest PR"** — Creates sample PR for Scenario 3

### 4. Verify Setup

- ✅ Repository open in VS Code with Copilot active
- ✅ Sample issues visible in **Issues** tab (labeled `quest-sample`)
- ✅ Sample PR visible in **Pull Requests** tab

---

## Start the Quest

| Ready for... | Go to... |
|--------------|----------|
| **Part 1** (first time) | [Part 1: Fundamentals](part-1-fundamentals/README.md) |
| **Part 2** (completed Part 1) | [Part 2: Advanced](part-2-advanced/README.md) |

---

## Keeping Your Fork Updated

If your fork falls behind:

1. Go to your fork on GitHub.com
2. Click **Sync fork** → **Update branch**
3. Pull changes locally: `git pull`

---

**Quest Version:** 2.0  
**Last Updated:** 2025-01-06  
**Content:** Microsoft Learn  
**Estimated Time:** ~2.5 hours (Part 1: 60 min, Part 2: 80 min)  
**Difficulty:** Beginner to Advanced
