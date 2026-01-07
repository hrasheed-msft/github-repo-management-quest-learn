# Scenario 3: The Big Merge

## The Story

It's Wednesday afternoon, and you receive a notification:

> **@sarah_fabric** has submitted Pull Request #127: "Major Microsoft Fabric module updates - new Copilot content and restructuring"
>
> +847 additions, -312 deletions across 18 files

You click through and see that Sarah, an enthusiastic content developer, has submitted a massive PR that includes:

- 3 brand new units for the `introduction-to-copilot-fabric` module
- Updates to 8 existing module files across Fabric content
- Restructured knowledge check questions
- New code examples for data engineering scenarios
- Updated cross-references between modules

Your manager messages you:

> "This looks great, but can you review it? We need to merge by Friday for the Fabric update cycle, but we can't afford to introduce errors or inconsistencies. Can you do a thorough review and work with Sarah to get this ready?"

**Your mission:** Efficiently review this complex PR, identify issues, provide constructive feedback, and ensure it meets Microsoft Learn quality standards before merging.

## Scenario Overview

**Duration:** 30 minutes
**Difficulty:** Intermediate
**Focus:** AI-assisted PR review and collaborative feedback

## Learning Objectives

By completing this scenario, you will:

1. Learn to efficiently review large pull requests using AI assistance
2. Identify style inconsistencies, technical inaccuracies, and content issues
3. Provide constructive, actionable feedback to contributors
4. Validate cross-references and ensure documentation coherence
5. Balance thoroughness with speed in PR reviews
6. Develop effective PR review workflows

## The Pull Request

Before starting this scenario, ensure the sample PR has been created by running the **Setup Quest PR** workflow (`.github/workflows/setup-quest-pr.yml`). This creates a real pull request in your repository with:

- **3 new content files:** Advanced scenarios, best practices, and troubleshooting for Copilot data agents
- **1 modified file:** Updated index.yml with new units
- **Intentional issues:** YAML errors, typos, broken links, and terminology inconsistencies for you to find

> **Note:** Look for the PR titled `[Quest Sample] Add advanced Copilot data agent content` in your repository's Pull Requests tab.

## Native GitHub Copilot Features for PR Review

GitHub now provides **native Copilot code review** capabilities that should be your first choice:

### Copilot as a PR Reviewer (Recommended)
1. Open the PR on GitHub.com
2. In the **Reviewers** dropdown, select **Copilot**
3. Copilot automatically analyzes the PR and leaves review comments with suggested fixes
4. Apply suggestions with one click, or dismiss them

### Automatic Copilot Reviews
Repository admins can configure automatic Copilot reviews for all PRs:
- Go to **Settings > Copilot > Code review**
- Enable automatic reviews for specific file patterns

### Custom Review Instructions
Add custom instructions for Copilot code review in `.github/copilot-instructions.md`:
```markdown
When performing a code review, apply the checks in the Microsoft Learn style guide.
When performing a code review, focus on YAML structure and cross-references.
```

> **Best Practice:** Use native Copilot code review first, then supplement with @workspace analysis in VS Code for deeper investigation.

## Your Tasks

### Task 3.1: High-Level PR Review (15 minutes)

**File:** [tasks/task-3.1-initial-review.md](tasks/task-3.1-initial-review.md)

Use **GitHub Copilot's native PR review** as your starting point, then perform deeper analysis with @workspace.

**Key Questions:**

- What is the overall goal of this PR?
- Does it accomplish what it claims to do?
- Are the changes appropriately scoped?
- What areas need detailed review?

### Task 3.2: Detailed Content Review (15 minutes)

**File:** [tasks/task-3.2-detailed-review.md](tasks/task-3.2-detailed-review.md)

Conduct a detailed review focusing on:

- Technical accuracy of Fabric concepts
- Style consistency with Microsoft Learn standards
- YAML metadata formatting
- Code example validation
- Cross-references and link validation
- Constructive feedback for the contributor

---

## Feature Priority Guide

When reviewing PRs, use features in this order:

| Priority | Feature | When to Use |
|----------|---------|-------------|
| 1️⃣ | **Native Copilot PR Review** | First step - add Copilot as reviewer |
| 2️⃣ | **Custom Instructions** | Configure in `.github/copilot-instructions.md` |
| 3️⃣ | **@workspace in VS Code** | Deep dive into specific concerns |
| 4️⃣ | **Copilot Coding Agent** | Ask Copilot to fix issues it finds |

## How to Approach This Scenario

### Step 0: Set Up the Scenario

Run the **Setup Quest PR** workflow to create the sample PR:

1. Go to Actions tab in your repository
2. Select "Setup Quest PR" workflow
3. Click "Run workflow"
4. Wait for the PR to be created
5. Navigate to the Pull Requests tab to find it

### Step 1: Understand the Baseline

Review the `learn-pr/wwl/implement-fabric-data-agents` module to understand the current state before the PR.

### Step 2: Review the Changes

Open the sample PR and examine the Files Changed tab to see all proposed changes.

### Step 3: Use AI Strategically

Use AI to:

- Compare before/after versions quickly
- Check consistency across multiple YAML and markdown files
- Validate technical accuracy of code examples
- Generate detailed feedback

### Step 4: Think Like a Reviewer

Your goal is to:

- Ensure quality (catch errors)
- Maintain consistency (with existing Learn content)
- Help the contributor (constructive feedback)
- Move quickly (release deadline)

### Step 5: Write Actionable Feedback

Make your feedback:

- Specific (point to exact files and issues)
- Actionable (suggest concrete fixes)
- Prioritized (must-fix vs nice-to-have)
- Balanced (positive + constructive)

## Success Criteria

You've successfully completed this scenario when you can:

- ✅ Explain the purpose and scope of the PR
- ✅ Identify at least 10 specific issues across the changes
- ✅ Categorize issues by type and severity
- ✅ Validate that cross-references work correctly
- ✅ Provide clear, actionable feedback to the contributor
- ✅ Recommend whether to approve, request changes, or reject
- ✅ Estimate effort required for fixes

## Tips for Success

1. **Start with the big picture**: Understand what the PR is trying to accomplish before diving into details
2. **Use diff view mentally**: Think "what changed and why"
3. **Leverage AI for patterns**: Use AI to find consistency issues across files
4. **Validate, don't just trust**: Spot-check AI findings for accuracy
5. **Be specific and kind**: Good feedback is detailed and encouraging
6. **Prioritize ruthlessly**: Not everything needs to be fixed pre-merge

## Time Management

- **Task 3.1 (Initial Review)**: 15 minutes - Get the big picture
- **Task 3.2 (Detailed Review)**: 20 minutes - Find specific issues
- **Task 3.3 (Cross-References)**: 10 minutes - Validate links
- **Task 3.4 (Feedback)**: 15 minutes - Write comprehensive review
- **Buffer**: 10 minutes for synthesis and polish

## What's Different from Previous Scenarios?

In Scenario 1, you audited an entire repository.
In Scenario 2, you triaged an issue backlog.
In Scenario 3, you're reviewing *changes* - focusing on deltas, not the whole codebase.

This requires:
- Understanding what changed and why
- Considering impact on existing content
- Balancing thoroughness with speed
- Collaborating with a contributor

## What's Next?

After completing this scenario, you'll be ready to:
- Review PRs confidently and efficiently
- Provide valuable feedback that helps contributors improve
- Make informed approve/request changes decisions
- Move on to **Scenario 4: The Agent Arsenal** where you'll build multi-agent workflows

## Need Help?

- **Stuck on a task?** Check the hints section in each task file
- **Want to see solutions?** Review the solution guides in `solutions/`
- **Questions about PR review best practices?** See `../../resources/best-practices.md`

---

**Ready to begin?** Start with [Task 3.1: High-Level PR Review](tasks/task-3.1-initial-review.md)
