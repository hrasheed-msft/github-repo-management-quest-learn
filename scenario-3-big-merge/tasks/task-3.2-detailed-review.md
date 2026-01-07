# Task 3.2: Detailed Content Review with GitHub Copilot

**Duration:** 15 minutes  
**Difficulty:** Intermediate  
**GitHub Copilot Features:** Native Copilot Code Review, `#pr` context, @workspace

## Objective

Conduct a detailed review of high-priority files from the PR, starting with native Copilot feedback and then using `#pr` context for deeper investigation.

## Prerequisites

- Completed Task 3.1 with Copilot's review feedback available
- PR open on GitHub.com with Copilot's inline comments visible
- Your `pr-review.md` from Task 3.1

## Tasks

### Step 1: Apply Copilot's One-Click Suggestions

**On GitHub.com:**

1. Navigate to the PR's **Files changed** tab
2. Look for Copilot's inline comments (marked with Copilot icon)
3. For each suggestion:
   - **Accept:** Click **Apply suggestion** to create a commit
   - **Reject:** Click 👎 to provide feedback
   - **Investigate:** Note it for deeper analysis in Step 2

> **Tip:** Applied suggestions create commits automatically and are tracked in PR history.

---

### Step 2: Deep Dive on Technical Accuracy

Use VS Code with `#pr` context to investigate issues Copilot flagged:

```
#pr Review the new markdown files for technical accuracy:
1. Are Fabric data agent concepts explained correctly?
2. Are PySpark/SQL code examples syntactically correct?
3. Would the code examples work in a Fabric notebook?
4. Are there any missing prerequisites or dependencies?

For each issue, provide the file, what's wrong, and severity (blocker/major/minor).
```

---

### Step 3: Validate Cross-References and Links

```
#pr Check for broken links and cross-reference issues:
1. Do all internal links point to files that exist?
2. Are the index.yml unit references correct?
3. Are there any orphaned references to deleted files?

List any broken links with the source file and recommended fix.
```

---

### Step 4: Check Formatting Consistency

```
#pr Review the changed files for formatting consistency:
- Do all code blocks have language specifiers (python, sql, yaml)?
- Is heading hierarchy correct (H1 → H2 → H3)?
- Are there any TODO or placeholder markers?
- Is terminology consistent (Microsoft Fabric vs just Fabric)?

Summarize formatting issues found.
```

---

### Step 5: Create Issue Summary

Add a "Detailed Review Findings" section to your `pr-review.md`:

| Category | Issues Found | Severity | Notes |
|----------|--------------|----------|-------|
| Technical Accuracy | | | |
| Broken Links | | | |
| Code Examples | | | |
| Formatting | | | |

---

## Success Criteria

- [ ] Applied or rejected Copilot's inline suggestions
- [ ] Verified technical accuracy of code examples
- [ ] Checked for broken cross-references
- [ ] Identified formatting inconsistencies
- [ ] Documented all issues with severity ratings

---

You've completed Scenario 3! Return to the [Scenario 3 README](../README.md) or explore the other scenarios.
