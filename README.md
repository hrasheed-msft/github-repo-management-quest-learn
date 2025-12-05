# GitHub Copilot for Repository Management Quest

## Quest Overview

Welcome to the **GitHub Copilot for Repository Management Quest** - an interactive learning experience designed for content developers who want to master GitHub Copilot's native features for repository management workflows. This quest simulates real-world scenarios using **real Microsoft Learn documentation**, covering common challenges like taking over unfamiliar repositories, triaging issue backlogs, and managing complex pull requests.

**What makes this quest unique:** You'll work with actual Microsoft Learn modules while mastering GitHub Copilot's workspace agent, issue analysis, PR summarization, and automated code generation features.

## 🎯 Two-Part Lab Structure

This quest is designed as **two 60-minute labs** that can be completed independently or as a full learning experience:

| Lab | Duration | Focus | Scenarios |
|-----|----------|-------|-----------|
| **[Part 1: Fundamentals](part-1-fundamentals/README.md)** | 60 min | Core Copilot skills | Workspace setup + Scenarios 1-2 |
| **[Part 2: Advanced](part-2-advanced/README.md)** | 60 min | Advanced automation | Custom agents + Scenarios 3-4 |

**Start here:** Choose the lab that matches your experience level and time available!

## Learning Objectives

By completing this quest, you will:

1. **Master GitHub Copilot workspace exploration** - Use Copilot's @workspace agent to quickly understand unfamiliar repositories and Microsoft Learn documentation structures
2. **Implement efficient issue management** - Use Copilot to analyze issues, categorize, prioritize, and suggest fixes
3. **Develop advanced PR review skills** - Leverage GitHub Copilot's PR summaries, review suggestions, and inline chat for efficient pull request reviews
4. **Create documentation standards** - Establish quality standards with Copilot-assisted reviews and automated checks
5. **Build practical workflows** - Develop repeatable processes using GitHub Copilot's native capabilities

## Quest Structure

This quest uses **real Microsoft Learn modules** in the `learn-pr/wwl/` folder and contains a foundational module plus four progressive scenarios:

- **Module 0: Workspace Preparation** - Customize your GitHub Copilot workspace with agents and reusable prompts using examples from Microsoft Learn documentation.
- **Scenario 1: The Inheritance** - Take over an unfamiliar Microsoft Fabric documentation repository. Use Copilot to explore the module structure, identify issues, and create an improvement plan.
- **Scenario 2: The Backlog Battle** - Triage 12 open issues in a Microsoft Learn repository. Categorize, prioritize, identify duplicates, and create fix proposals.
- **Scenario 3: The Big Merge** - Review a pull request adding new Copilot for Fabric documentation. Identify content issues, validate cross-references, and provide constructive feedback.
- **Scenario 4: The Agent Arsenal** - Build a comprehensive agent ecosystem with specialized documentation agents that work together for enterprise-scale workflows.

## Prerequisites

- **Git fundamentals**: Basic understanding of repositories, commits, branches, and pull requests
- **Markdown knowledge**: Familiarity with markdown syntax and documentation
- **GitHub Copilot**: Active GitHub Copilot subscription (individual, business, or enterprise)
- **Tools**: VS Code with GitHub Copilot extension, Git client, GitHub account

## Getting Started

### Setup Requirements

1. **Install VS Code** - Download from https://code.visualstudio.com/
2. **Install GitHub Copilot extensions** - Install GitHub Copilot *and* Copilot Chat (2 extensions)
    - https://marketplace.visualstudio.com/items?itemName=GitHub.copilot
    - https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
1. **Activate GitHub Copilot** - Sign in with your GitHub account and link your account with your GitHub enterprise license: https://copilot.github.microsoft.com/
1. Add two MCP servers in the GitHub Copilot extension - - https://code.visualstudio.com/mcp
    - GitHub
    - Microsoft.docs.mcp

### Repository Setup

1. **Fork this repository** to your own GitHub account:
   - Click the "Fork" button at the top-right of this repository
   - Choose your account as the destination for the fork

2. **Clone your fork** (replace `[your-username]` with your GitHub username):
   ```bash
   git clone https://github.com/[your-username]/github-repo-management-quest-learn.git
   cd github-repo-management-quest-learn
   code .
   ```

3. **Create sample content** by running the setup workflows:

   **Option A: Using GitHub Web Interface (Recommended)**
   - Go to your forked repository on GitHub
   - Navigate to the **Actions** tab
   - You'll see two workflows: "Setup Quest Issues" and "Setup Quest PR"
   
   **To create sample issues for Scenario 3:**
   - Click on "Setup Quest Issues" workflow
   - Click "Run workflow" button
   - Select "scenario-3" from the dropdown
   - Click the green "Run workflow" button
   - Wait for the workflow to complete (creates 8 sample issues)

   **To create sample PR for Scenario 2:**
   - Click on "Setup Quest PR" workflow  
   - Click "Run workflow" button
   - Select your preferred PR size (small/medium/large)
   - Click the green "Run workflow" button
   - Wait for the workflow to complete (creates 1 sample pull request)

   **Option B: Using GitHub CLI (if you have it installed)**
   ```bash
   # Create sample issues
   gh workflow run setup-quest-issues.yml --field scenario=scenario-3

   # Create sample PR
   gh workflow run setup-quest-pr.yml --field pr_size=medium
   ```

4. **Verify setup**:
   - Check the **Issues** tab - you should see sample issues labeled "quest-sample"
   - Check the **Pull requests** tab - you should see 1 sample PR labeled "quest-sample"

## Next Steps

Ready to begin?

## Activities for Learning Lab Academy 12/5 Live Session

- [Module 0 - Repo Preparation](module-0-workspace-prep/tasks/task-0.1-intro.md)
- [Scenario 1: Audit](scenario-1-inheritance/tasks/task-1.2-audit.md)
- [Scenario 1: Agent Analysis](scenario-1-inheritance/tasks/task-1.5-agent-analysis.md)
- [Scenario 2: Categorize](scenario-2-backlog-battle/tasks/task-2.1-categorize.md)
- [Scenario 2: Automated Fixes](scenario-2-backlog-battle/tasks/task-2.4-automated-fixes.md)

---

**Quest Version:** 2.0
**Last Updated:** 2025-12-04
**Content:** Microsoft Learn
**Estimated Completion Time:** 2 hours (1 hour per part)
**Difficulty Level:** Beginner to Advanced
