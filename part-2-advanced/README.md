# Part 2: Advanced GitHub Copilot Workflows

## Overview

Welcome to **Part 2** of the GitHub Copilot Repository Management Quest! This session builds on Part 1 fundamentals to tackle **AI-assisted PR reviews** and **advanced agent configuration** for enterprise-scale documentation management.

**Duration:** ~60 minutes  
**Difficulty:** Intermediate to Advanced  
**Prerequisites:** Completed Part 1 (or equivalent Copilot experience)

---

## Before You Start: Prerequisites Checklist

### ✅ Setup from Part 1

Ensure you have the following from Part 1:

| Requirement | How to Verify |
|-------------|---------------|
| **Forked repository** | Your fork exists at `github.com/[your-username]/github-repo-management-quest-learn` |
| **VS Code with Copilot** | GitHub Copilot and Copilot Chat extensions installed and active |
| **MCP servers configured** | GitHub and Microsoft.docs.mcp servers added in VS Code settings |
| **Repository cloned locally** | Folder open in VS Code with Copilot active |

### ✅ Sample Content Created

Part 2 requires the **sample PR** created by GitHub Actions:

1. Go to your repository's **Actions** tab on GitHub
2. Run **"Setup Quest PR"** workflow (if not already done)
3. Verify: Check **Pull Requests** tab for PR titled `[Quest Sample] Add advanced Copilot data agent content`

> **Don't have the sample PR?** Run the workflow now—it takes about 30 seconds.

---

## Recap: What You Learned in Part 1

### Module 0: Workspace Preparation

| Concept | What You Learned |
|---------|------------------|
| **Custom Agents** | Created `.agent.md` files in `.github/agents/` with specialized personas |
| **Reusable Prompts** | Created `.prompt.md` files in `.github/prompts/` for consistent templates |
| **Agent Invocation** | Used `@agent-name` in Copilot Chat to activate specialized agents |
| **Prompt Usage** | Used `#prompt:` to invoke saved prompts |

### Scenario 1: Repository Exploration

| Concept | What You Learned |
|---------|------------------|
| **@workspace** | Query entire repository for understanding unfamiliar codebases |
| **Repository Audit** | Use Copilot to analyze structure, find issues, assess quality |
| **Content Analysis** | Identify patterns, gaps, and improvement opportunities |

### Scenario 2: Issue Triage

| Concept | What You Learned |
|---------|------------------|
| **Issue Categorization** | Use Copilot to classify issues by type, priority, effort |
| **Duplicate Detection** | Identify related or duplicate issues across backlog |
| **Bulk Analysis** | Process multiple issues efficiently with AI assistance |

---

## What You'll Learn in Part 2

Part 2 introduces **native GitHub Copilot features** for PR review and **advanced agent configuration** that goes beyond basics.

### Scenario 3: The Big Merge (30 minutes)

**Challenge:** Review a large PR with 18 changed files, find issues, and provide constructive feedback before the Friday deadline.

| Skill | What You'll Learn |
|-------|-------------------|
| **Native Copilot PR Review** | Add Copilot as a reviewer directly on GitHub.com |
| **Custom Review Instructions** | Configure `.github/copilot-instructions.md` for tailored reviews |
| **`#pr` Context** | Use VS Code's GitHub Pull Requests extension for deep analysis |
| **One-Click Fixes** | Apply Copilot's suggested changes instantly |

**Tasks:**
- Task 3.1: Initial PR Review (15 min) — Use native Copilot review + scope analysis
- Task 3.2: Detailed Content Review (15 min) — Technical accuracy, links, formatting

### Scenario 4: The Agent Arsenal (40 minutes)

**Challenge:** Configure advanced agents with enterprise-grade capabilities and external integrations.

| Skill | What You'll Learn |
|-------|-------------------|
| **Tool Permissions** | Configure `tools: ["read", "search", "edit"]` to control agent capabilities |
| **Model Selection** | Use `model: o1` vs `gpt-4o` for different reasoning needs |
| **Platform Targeting** | Target agents to `vscode` or `github-copilot` platforms |
| **Structured Output** | Create JSON-formatted outputs for automation and pipelines |
| **MCP Tools** | Use Microsoft Docs MCP to search and verify against official documentation |

**Tasks:**
- Task 4.1: Advanced Agent Configuration (20 min) — Tools, models, structured output
- Task 4.2: MCP Tools and External Integrations (20 min) — Docs search, verification workflows

---

## Part 2 Lab Structure

| Section | Duration | Focus |
|---------|----------|-------|
| **Prerequisites Check** | 5 min | Verify setup, create sample PR if needed |
| **Scenario 3: The Big Merge** | 30 min | Native Copilot PR review, `#pr` context |
| **Scenario 4: Agent Arsenal** | 40 min | Advanced configuration, MCP tools |
| **Wrap-up** | 5 min | Review, Q&A, next steps |

**Total Time:** ~80 minutes

---

## Key Differences: Part 1 vs Part 2

| Aspect | Part 1 (Fundamentals) | Part 2 (Advanced) |
|--------|----------------------|-------------------|
| **Agent Creation** | Basic name/description | Tools, models, targeting, structured output |
| **Copilot Usage** | @workspace exploration | Native PR review, `#pr` context |
| **Scope** | Local workspace analysis | External integrations (MCP, Microsoft Docs) |
| **Output** | Freeform responses | Structured JSON for automation |
| **Focus** | Understanding repositories | Reviewing PRs, validating accuracy |

---

## Getting Started

Ready to begin Part 2?

1. **Verify prerequisites** using the checklist above
2. **Start with Scenario 3:** [The Big Merge](../scenario-3-big-merge/README.md)
3. **Then continue to Scenario 4:** [The Agent Arsenal](../scenario-4-agent-arsenal/README.md)

---

## Quick Reference: New Features in Part 2

### Native Copilot PR Review

```text
On GitHub.com:
1. Open PR → Reviewers dropdown → Select "Copilot"
2. Wait ~30 seconds for analysis
3. Review inline comments on Files Changed tab
4. Apply suggestions with one click
```

### Custom Instructions File

Create `.github/copilot-instructions.md`:

```markdown
When performing a code review, apply these checks:
- Verify YAML frontmatter follows Microsoft Learn schema
- Check ms.date values are within 12 months
- Ensure code blocks specify language
- Flag TODO/TBD placeholder text
```

### Agent Tool Configuration

```markdown
---
name: Content Auditor
description: Read-only auditor that cannot modify files
tools: ["read", "search"]  # No "edit" = safe exploration
---
```

### MCP Docs Search

```text
What are the current best practices for Fabric lakehouses? 
Search Microsoft Learn for the latest guidance.
```

---

**Let's begin!** Start with [Scenario 3: The Big Merge](../scenario-3-big-merge/README.md).
