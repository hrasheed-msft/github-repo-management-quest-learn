# Task 3.1: Initial PR Review with GitHub Copilot

**Duration:** 15 minutes  
**Difficulty:** Intermediate  
**GitHub Copilot Features:** Native Copilot Code Review, Copilot Chat, `#pr` context

## Objective

Perform an initial high-level review of the sample PR using GitHub Copilot's **native code review feature** as your primary method.

## Prerequisites

**Before starting:** Run the "Setup Quest PR" workflow to create the sample PR:
1. Go to **Actions** tab → Select "Setup Quest PR" → Click "Run workflow"
2. Navigate to **Pull Requests** tab to find the created PR

## Tasks

### Step 1: Request Native Copilot PR Review

**On GitHub.com:**

1. Open the PR titled `[Quest Sample] Add advanced Copilot data agent content`
2. Click the **Reviewers** gear icon in the right sidebar
3. Select **Copilot** from the dropdown
4. Wait ~30 seconds for Copilot to analyze the PR
5. Review Copilot's inline comments on the **Files changed** tab

**What Native Copilot Review Provides:**
- Inline comments on potential issues
- Suggested fixes you can apply with one click
- Comments visible to all collaborators

> **Note:** Copilot leaves a "Comment" review (not Approve/Request Changes), so it won't block merging.

---

### Step 2: Configure Custom Review Instructions (Optional)

To tailor Copilot's review focus, create `.github/copilot-instructions.md`:

```markdown
When performing a code review, apply the following checks:

- Verify YAML frontmatter follows Microsoft Learn schema
- Check that ms.date values are within the last 12 months
- Ensure all internal links use relative paths
- Verify code blocks specify language (python, sql, yaml)
- Flag any placeholder text like TODO, TBD, or [INSERT]
```

Copilot will use these instructions for all future code reviews.

---

### Step 3: Ask Copilot About PR Scope and Risk

**Choose your preferred method:**

**Option A: Copilot Chat on GitHub.com**

Click the Copilot icon on the PR page and ask:
```
Summarize what this PR does and identify high-risk files that need careful review
```

**Option B: VS Code with `#pr` Context**

Open the PR in the GitHub Pull Requests panel and use Copilot Chat:
```
#pr Analyze the scope of this PR. What are the high-risk changes and which areas need the most careful review?
```

---

### Step 4: Spot Check Content Quality

Ask Copilot to review the new files for quality issues:

```
#pr Review the new markdown files for quality issues: writing clarity, formatting consistency, TODO markers, and code block formatting. What patterns of issues exist across the PR?
```

---

### Step 5: Create Preliminary Assessment

Ask Copilot for an overall recommendation:

```
#pr Based on this PR, provide a preliminary assessment: should it be approved, request changes, or needs major work? What are the top 3 concerns?
```

**Create `pr-review.md`** with your findings:
- PR Overview (what it does)
- High-risk files identified
- Quality issues found
- Preliminary recommendation

---

## Success Criteria

- [ ] Requested native Copilot review and reviewed its inline comments
- [ ] Identified high-risk files and areas needing detailed review
- [ ] Spot-checked quality of new content
- [ ] Created preliminary assessment with top concerns

---

**Ready for the next step?** Continue to [Task 3.2: Detailed Content Review](task-3.2-detailed-review.md).
