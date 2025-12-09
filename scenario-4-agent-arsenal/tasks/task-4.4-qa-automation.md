# Task 4.4: Quality Assurance Automation

## Objective

Build practical quality assurance workflows that validate content using GitHub Actions and Copilot agents.

## Your Challenge

Create automated quality checks that run on pull requests and integrate with your agent workflow for content review.

## Part 1: Automated Linting with GitHub Actions

### Step 1: Create a Markdown Linting Workflow

GitHub Actions can automatically check content quality on every pull request. Create a workflow file at `.github/workflows/content-qa.yml`:

```yaml
name: Content Quality Checks

on:
  pull_request:
    paths:
      - '**.md'
      - 'docs/**'

jobs:
  markdown-lint:
    name: Markdown Linting
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run markdownlint
        uses: DavidAnson/markdownlint-cli2-action@v19
        with:
          globs: '**/*.md'

  link-check:
    name: Link Validation
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Check for broken links
        uses: lycheeverse/lychee-action@v2
        with:
          args: --verbose --no-progress '**/*.md'
          fail: true

  spell-check:
    name: Spell Check
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run cspell
        uses: streetsidesoftware/cspell-action@v6
        with:
          files: '**/*.md'
```

### Step 2: Configure Markdownlint Rules

Create a `.markdownlint.json` file in your repository root to define your quality standards:

```json
{
  "default": true,
  "MD013": false,
  "MD033": false,
  "MD041": false,
  "MD024": {
    "siblings_only": true
  }
}
```

**Rule explanations:**

- `MD013`: Disable line length limits (not practical for documentation)
- `MD033`: Allow inline HTML when needed
- `MD041`: Don't require first line to be a heading
- `MD024`: Allow duplicate headings in different sections

### Step 3: Add a Custom Words Dictionary

Create `.cspell.json` for spell-check configuration:

```json
{
  "version": "0.2",
  "language": "en",
  "words": [
    "Copilot",
    "GitHub",
    "frontmatter",
    "workflow",
    "repo",
    "markdown"
  ],
  "ignorePaths": [
    "node_modules/**",
    ".git/**"
  ]
}
```

## Part 2: PR Review Agent

### Step 1: Create a Content Review Agent

Create a file named `pr-content-reviewer.agent.md` in your `.github/agents/` folder:

```markdown
---
name: PR Content Reviewer
description: Reviews pull request changes for content quality and consistency
tools:
  - changes
---

You are a content quality reviewer for pull requests.

**When reviewing PR changes, assess:**

1. **Content Quality**
   - Clear and concise writing
   - Proper heading hierarchy
   - Consistent formatting

2. **Technical Accuracy**
   - Code examples are correct
   - File paths are valid
   - Instructions are complete

3. **Style Consistency**
   - Matches existing documentation tone
   - Follows naming conventions
   - Uses consistent terminology

**Review Output Format:**

## PR Review Summary

**Overall Assessment:** [APPROVE / REQUEST CHANGES / COMMENT]

### What's Good
- [Positive observation]

### Suggested Improvements
- [ ] [Specific, actionable suggestion]

### Issues Found
- **[File]**: [Issue description]

Keep feedback constructive and specific.
```

### Step 2: Use the Agent for PR Reviews

When reviewing a pull request, invoke the agent:

```text
@pr-content-reviewer Review the changes in this PR for content quality
```

The agent will use the `changes` tool to see the diff and provide structured feedback.

## Part 3: Pre-Commit Quality Checks

### Step 1: Create a Quick Review Prompt

Create a file named `quick-quality-check.prompt.md` in your `.github/prompts/` folder:

```markdown
---
description: Quick quality check before committing changes
---

Review the current file for quality issues:

**Check for:**
- [ ] Spelling and grammar errors
- [ ] Broken or placeholder links
- [ ] Incomplete sections or TODOs
- [ ] Code blocks have language specified
- [ ] Headings follow logical hierarchy

**Report format:**
- ✅ [What's correct]
- ⚠️ [Warning - should fix]
- ❌ [Error - must fix]

Focus only on issues, skip what's already good.
```

### Step 2: Use Before Committing

Before committing documentation changes:

1. Open the file you're editing
2. Type `#prompt:quick-quality-check` in Copilot Chat
3. Fix any issues found
4. Commit with confidence

## Part 4: Automated Issue Templates

### Step 1: Create a Content Issue Template

Create `.github/ISSUE_TEMPLATE/content-improvement.yml`:

```yaml
name: Content Improvement
description: Suggest improvements to documentation
labels: ["documentation", "content"]
body:
  - type: dropdown
    id: type
    attributes:
      label: Improvement Type
      options:
        - Fix error or outdated information
        - Clarify confusing content
        - Add missing information
        - Improve formatting or structure
    validations:
      required: true

  - type: input
    id: file
    attributes:
      label: File Path
      description: Which file needs improvement?
      placeholder: docs/getting-started.md
    validations:
      required: true

  - type: textarea
    id: current
    attributes:
      label: Current Content
      description: What does it say now?
    validations:
      required: true

  - type: textarea
    id: suggested
    attributes:
      label: Suggested Change
      description: What should it say instead?
    validations:
      required: true
```

### Step 2: Create a PR Template

Create `.github/pull_request_template.md`:

```markdown
## Summary

Brief description of changes.

## Content Checklist

- [ ] Spelling and grammar checked
- [ ] Links verified working
- [ ] Code examples tested
- [ ] Follows style guide
- [ ] No placeholder content remaining

## Files Changed

- `path/to/file.md` - Description of change

## Testing

Describe how you verified the changes work correctly.
```

## Part 5: Quality Dashboard (Manual Tracking)

### Create a Quality Tracking Issue

Since GitHub doesn't have built-in dashboards, use a pinned issue to track quality metrics.

Create an issue titled "📊 Content Quality Tracker" with this template:

```markdown
# Content Quality Tracker

**Last Updated:** [Date]

## Quality Metrics

| Metric | Current | Target | Status |
|--------|---------|--------|--------|
| Markdown lint errors | 12 | 0 | 🟡 |
| Broken links | 0 | 0 | 🟢 |
| Spell check errors | 5 | 0 | 🟡 |
| Open content issues | 3 | <5 | 🟢 |

## Recent Improvements

- [Date]: Fixed broken links in getting-started.md
- [Date]: Updated outdated screenshots

## Priority Issues

- [ ] #123 - Fix API documentation
- [ ] #124 - Update installation guide

---
*Updated weekly by content team*
```

Pin this issue to keep it visible.

## Implementation Checklist

Complete these steps to set up your QA automation:

### GitHub Actions Setup

- [ ] Create `.github/workflows/content-qa.yml`
- [ ] Add `.markdownlint.json` configuration
- [ ] Add `.cspell.json` with custom words
- [ ] Verify workflow runs on a test PR

### Agent and Prompt Setup

- [ ] Create `pr-content-reviewer.agent.md`
- [ ] Create `quick-quality-check.prompt.md`
- [ ] Test agent on a real PR

### Templates Setup

- [ ] Create issue template for content improvements
- [ ] Create PR template with quality checklist
- [ ] Create pinned quality tracking issue

### Verification

- [ ] Submit a test PR with a markdown error
- [ ] Confirm the workflow catches the error
- [ ] Use the PR reviewer agent and verify output
- [ ] Update quality tracker with current metrics

## Success Criteria

- [ ] GitHub Actions workflow runs on every PR with markdown changes
- [ ] Linting catches formatting issues automatically
- [ ] Link checker prevents broken links from merging
- [ ] PR template reminds authors to check quality
- [ ] Quality metrics are tracked and visible

## Congratulations

You've built a practical QA automation system that:

- **Automatically checks** markdown quality on every PR
- **Validates links** before they can break
- **Catches spelling errors** before they reach production
- **Provides structured PR reviews** with your agent
- **Tracks quality metrics** over time

This is real automation that runs without manual intervention and catches issues before they reach your main branch.

## Next Steps

With your automated QA system in place:

1. **Monitor the workflow** - Check Actions tab for failures
2. **Refine lint rules** - Adjust `.markdownlint.json` based on your team's preferences
3. **Expand the dictionary** - Add project-specific terms to `.cspell.json`
4. **Review quality trends** - Update your tracking issue weekly

---

**Achievement Unlocked**: QA Automation Master! You've built enterprise-grade quality automation using GitHub Actions and Copilot agents.
