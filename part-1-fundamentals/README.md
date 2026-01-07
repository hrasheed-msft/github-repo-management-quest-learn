# Part 1: GitHub Copilot Fundamentals for Repository Management

## Overview

Welcome to **Part 1** of the GitHub Copilot Repository Management Quest! This 60-minute lab introduces you to the core GitHub Copilot features for managing documentation repositories efficiently.

**Duration:** ~60 minutes  
**Difficulty:** Beginner to Intermediate  
**Prerequisites:** VS Code with GitHub Copilot extension, GitHub account

## What You'll Learn

By completing Part 1, you will:

1. **Configure your workspace** with custom agents and prompts for documentation tasks
2. **Explore unfamiliar repositories** using GitHub Copilot's `@workspace` agent
3. **Audit content quality** with AI-assisted analysis and reporting
4. **Triage issues efficiently** using AI-powered categorization and prioritization

## Lab Structure

| Module | Duration | Focus |
|--------|----------|-------|
| **Quick Setup** | 5 min | Fork repo, run setup workflows |
| **Module 0: Workspace Preparation** | 10 min | Create agents and prompts |
| **Scenario 1: The Inheritance** | 25 min | Repository exploration and audit |
| **Scenario 2: The Backlog Battle** | 15 min | Issue categorization and triage |
| **Wrap-up** | 5 min | Reflection and next steps |

---

## Quick Setup (5 minutes)

### 1. Fork and Clone the Repository

```bash
# Fork via GitHub UI first, then:
git clone https://github.com/[your-username]/github-repo-management-quest-learn.git
cd github-repo-management-quest-learn
code .
```

### 2. Run Setup Workflows

In your forked repository on GitHub:

1. Go to **Actions** tab
2. Run **"Setup Quest Issues"** workflow (creates sample issues for Scenario 2)
3. Run **"Setup Quest PR"** workflow (creates sample PR for Part 2)

### 3. Verify Setup

- ✅ Repository open in VS Code
- ✅ GitHub Copilot icon visible in status bar
- ✅ Sample issues visible in Issues tab (labeled `quest-sample`)

---

## Module 0: Workspace Preparation (10 minutes)

Create custom agents and prompts to specialize Copilot for documentation tasks.

### Create a Custom Agent

Create `.github/agents/documentation-auditor.agent.md`:

```markdown
---
name: Documentation Auditor
description: Analyzes documentation for quality issues and improvements
---

You are a documentation auditor specializing in Microsoft Learn content. Focus on:
- Content completeness and structure
- Outdated information (check ms.date values)
- Broken links and missing includes
- Formatting and style consistency

Provide actionable recommendations with specific file paths and line numbers.
```

### Create a Reusable Prompt

Create `.github/prompts/content-audit.prompt.md`:

```markdown
---
name: Content Audit
description: Comprehensive analysis of repository content
---

Analyze this repository's documentation for:
1. Structure and organization
2. Content gaps or missing sections
3. Outdated information (ms.date older than 12 months)
4. Broken or suspicious links

Provide: Executive summary, Key findings, Quick wins (under 30 min to fix)
```

### Test Your Configuration

Open Copilot Chat (`Ctrl+Shift+I`) and try:

```
@documentation-auditor Analyze the structure of the learn-pr/wwl folder
```

**Full Task Details:** [module-0-workspace-prep/tasks/task-0.1-intro.md](../module-0-workspace-prep/tasks/task-0.1-intro.md)

---

## Scenario 1: The Inheritance (25 minutes)

### The Story

You've just been assigned to take over a documentation repository containing Microsoft Learn training modules. Your mission: understand what you've inherited and create an improvement plan.

### Task 1.1: Repository Exploration (10 min)

Use `@workspace` to map the repository structure:

```
@workspace Give me an overview of this repository. What types of content does it contain? How is it organized?
```

```
@workspace What Microsoft Learn modules are in the learn-pr/wwl folder? List them by topic area.
```

**Skills:** Using `@workspace` for repository-wide context, understanding folder structures

**Full Task Details:** [scenario-1-inheritance/tasks/task-1.1-explore.md](../scenario-1-inheritance/tasks/task-1.1-explore.md)

### Task 1.2: Content Quality Audit (10 min)

Use Copilot to find quality issues:

```
@workspace Analyze the learn-pr/wwl modules for potential issues like outdated ms.date values, broken includes, or inconsistent metadata.
```

```
@documentation-auditor Review the get-started-lakehouses module for content quality issues.
```

**Skills:** Targeted issue detection, pattern recognition, using custom agents

**Full Task Details:** [scenario-1-inheritance/tasks/task-1.2-audit.md](../scenario-1-inheritance/tasks/task-1.2-audit.md)

### Task 1.3: Generate Audit Report (5 min)

Create a comprehensive report using your prompt:

```
#prompt:content-audit Analyze the learn-pr/wwl folder focusing on Fabric-related modules.
```

**Skills:** Generating structured reports, prioritizing findings

**Full Task Details:** [scenario-1-inheritance/tasks/task-1.3-report.md](../scenario-1-inheritance/tasks/task-1.3-report.md)

---

## Scenario 2: The Backlog Battle (15 minutes)

### The Story

Your documentation repository has accumulated 12+ open issues. They range from broken images to outdated content to accessibility concerns. Your challenge: efficiently categorize and prioritize these issues.

### Task 2.1: Issue Categorization (10 min)

Open the **Issues** tab in your forked repository. You should see sample issues with the `quest-sample` label.

Use Copilot to analyze and categorize:

```
@workspace Analyze the GitHub issues in this repository with the quest-sample label. For each issue, identify:
1. Type (bug, content, accessibility, enhancement)
2. Priority (P0-Critical, P1-High, P2-Medium, P3-Low)
3. Effort estimate (XS, S, M, L)
4. Quick win? (Yes/No)
```

**Skills:** Bulk issue analysis, consistent categorization, priority-based triage

**Full Task Details:** [scenario-2-backlog-battle/tasks/task-2.1-categorize.md](../scenario-2-backlog-battle/tasks/task-2.1-categorize.md)

### Task 2.2: Identify Quick Wins (5 min)

Find issues that can be fixed immediately:

```
@workspace From the quest-sample issues, which ones are quick wins that can be fixed in under 30 minutes? List them with the specific fix needed.
```

**Skills:** Identifying low-hanging fruit, creating action plans

**Full Task Details:** [scenario-2-backlog-battle/tasks/task-2.2-duplicates.md](../scenario-2-backlog-battle/tasks/task-2.2-duplicates.md)

---

## Wrap-up (5 minutes)

### What You Accomplished

- ✅ Created custom agents and prompts for documentation work
- ✅ Explored and mapped a repository using `@workspace`
- ✅ Identified content issues with AI assistance
- ✅ Generated an audit report
- ✅ Triaged issues using AI-powered categorization

### Key Takeaways

1. **`@workspace` provides repository-wide context** — essential for understanding unfamiliar repos
2. **Custom agents specialize Copilot's expertise** — focus on specific tasks
3. **Prompts ensure consistent output** — reusable templates for common workflows
4. **AI accelerates triage but doesn't replace judgment** — validate findings

---

## Continue to Part 2

Ready to tackle advanced workflows? **Part 2** covers:

- Native GitHub Copilot PR review on GitHub.com
- `#pr` context for deep PR analysis in VS Code
- Advanced agent configuration (tools, models, structured output)
- MCP tools for documentation verification

**Next:** [Part 2: Advanced Copilot Workflows](../part-2-advanced/README.md)

---

## Quick Reference

### Essential Commands

| Command | Purpose |
|---------|---------|
| `@workspace [query]` | Query with full repository context |
| `@documentation-auditor [query]` | Use your custom audit agent |
| `#prompt:content-audit` | Run your audit prompt |
| `Ctrl+Shift+I` | Open Copilot Chat |

### Files to Reference

- **Module 0 Tasks:** `module-0-workspace-prep/tasks/`
- **Scenario 1 Tasks:** `scenario-1-inheritance/tasks/`
- **Scenario 2 Tasks:** `scenario-2-backlog-battle/tasks/`
- **Learn Content:** `learn-pr/wwl/` (Microsoft Learn modules)
