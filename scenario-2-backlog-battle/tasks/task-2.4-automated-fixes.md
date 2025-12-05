# Task 2.4: Automated Issue Fixes with GitHub Copilot (Issue-to-PR Workflow)

**Duration:** 20 minutes  
**Difficulty:** Intermediate-Advanced  
**GitHub Copilot Features:** Assign Issue to Copilot, Copilot Coding Agent, @workspace, automated fix generation

## Objective

Use GitHub Copilot's powerful **issue-to-PR workflow** to automatically generate pull requests that fix simple issues—demonstrating GitHub Copilot's most impressive repository management capability.

## Context

In your backlog analysis, you identified several "quick win" issues that are simple, mechanical fixes:
- Typos in documentation
- Broken links
- Missing code imports in examples
- Simple formatting issues
- Outdated version numbers

Traditionally, even simple fixes require:
1. Reading the issue
2. Finding the file
3. Making the change
4. Creating a branch
5. Committing
6. Creating a PR
7. Writing PR description

**This takes 10-15 minutes per issue.**

---

## Part A: Assign Issue to Copilot (GitHub.com)

The fastest way to fix simple issues is to **assign them directly to GitHub Copilot** on GitHub.com. Copilot will analyze the issue, generate a fix, create a branch, and open a pull request—all automatically!

### How It Works

1. **Navigate to an issue** on GitHub.com
2. **Click the "Assignees" section** in the right sidebar
3. **Select "Copilot"** from the assignee list (or type `copilot`)
4. **Copilot goes to work:**
   - Analyzes the issue description
   - Identifies relevant files in the repository
   - Generates the fix
   - Creates a new branch
   - Opens a pull request with a description

### Try It: Assign a Typo Issue to Copilot

1. **Find a simple issue** in your repository (e.g., a typo or broken link from the `quest-sample` issues)

2. **Open the issue on GitHub.com**

3. **Assign to Copilot:**
   - Click **Assignees** → Select **Copilot**
   - Or use the keyboard shortcut: Press `a` then type `copilot`

   ![Assign issue to Copilot](../../media/assign_to_copilot.png)

4. **Watch Copilot work:**
   - A comment appears: "Copilot is working on this issue..."
   - Within seconds to minutes, a PR link appears
   - The issue shows the linked PR

5. **Review the PR:**
   - Navigate to the pull request Copilot created
   - Review the changes (Files changed tab)
   - Check that the fix is correct
   - Merge if satisfied, or request changes

### Example: Typo Fix via Assign to Copilot

**Issue:** "Typo in docs/getting-started.md - 'experiance' should be 'experience'"

**What Copilot does automatically:**

```text
✅ Creates branch: copilot/fix-typo-experiance
✅ Edits: docs/getting-started.md (line 12)
✅ Changes: "experiance" → "experience"  
✅ Opens PR: "Fix typo in getting-started.md"
✅ PR description: "Fixes typo reported in #23. Changed 'experiance' to 'experience'."
✅ Links: Closes #23
```

**Your action:** Review and merge. Done in 30 seconds!

### Best Practices for Assign to Copilot

| ✅ Works Well For | ❌ Not Ideal For |
|------------------|-----------------|
| Typo fixes | Complex logic changes |
| Broken link updates | Multi-file refactoring |
| Missing imports | Security-sensitive code |
| Simple formatting | Architectural decisions |
| Version number updates | Changes needing discussion |

> **Tip:** Write clear, specific issue descriptions. The better Copilot understands the issue, the better the fix!

---

## Part B: Same Workflow in VS Code

You can achieve the same issue-to-PR workflow using **Copilot Chat in VS Code**. This gives you more control over the process and lets you review/refine fixes before creating the PR.

### When to Use VS Code Instead

- You want to **preview the fix** before committing
- You need to **refine or customize** Copilot's suggestion
- The fix requires **context from multiple files**
- You want to **batch multiple fixes** together
- You prefer working in your editor

### Setup

1. **Open VS Code with your repository**

2. **Open Copilot Chat:** `Ctrl+Shift+I` (Cmd+Shift+I on Mac)

---

### VS Code Task 1: Fix Simple Typo

**Scenario:** An issue reports a typo in `docs/getting-started.md`: "experiance" should be "experience"

**GitHub Copilot Chat Prompt:**

```text
@workspace Issue #23 reports a typo in the getting-started guide.

Issue description: "The word 'experiance' on line 12 of docs/getting-started.md should be 'experience'"

Please:
1. Find the file and the typo
2. Show me the current line
3. Provide the corrected line
4. Suggest the exact edit I should make

After I confirm, help me create a PR to fix this.
```

**What Copilot Does:**

- Locates the exact file and line
- Identifies the typo
- Provides corrected text
- Helps create branch and PR

**Follow-up:**

```text
@workspace Create a pull request description for this typo fix. Include:
- What was fixed
- Which issue it closes
- Keep it concise (it's just a typo)

Format for GitHub PR.
```

**Example PR Description Copilot Generates:**

```markdown
## Fix typo in getting started guide

Fixed spelling error: "experiance" → "experience"

**Changes:**
- docs/getting-started.md line 12

**Closes #23**

---
Small documentation fix to improve readability.
```

**Deliverable:** Document the fix process in `automated-fixes.md`

---

### VS Code Task 2: Fix Broken Link

**Scenario:** An issue reports: "Broken link in README.md line 45—links to old domain that doesn't exist"

**GitHub Copilot Chat Prompt:**

```text
@workspace Issue #25 reports a broken link.

Issue: "Link on line 45 of README.md points to http://old-docs.example.com which no longer exists. Should link to https://docs.example.com instead"

Please:
1. Find the broken link in README.md
2. Show me the current link
3. Provide the corrected link
4. Verify the new domain is used elsewhere in the docs (consistency check)

Generate the fix for me.
```

**What Copilot Does:**

- Finds the broken link
- Suggests correct replacement
- Checks for consistency across other files
- Provides ready-to-use fix

**Consistency Check:**

```text
@workspace Are there other references to old-docs.example.com in any other files that should also be updated?
```

**Deliverable:** Add "Broken Link Fix" to automated-fixes.md

---

### VS Code Task 3: Add Missing Import

**Scenario:** An issue reports: "Code example in tutorials/api-guide.md is missing import statement and won't run"

**GitHub Copilot Chat Prompt:**

```text
@workspace Issue #11: Code example missing import

Issue description: "The code example at line 45-52 in tutorials/api-guide.md uses `Client` but doesn't import it. The example fails when users try to run it."

Please:
1. Find the code example
2. Identify what import is needed
3. Show me the current code vs corrected code with import
4. Make sure the import is correct for our project

Provide a complete, working code example.
```

**What Copilot Does:**

- Locates the incomplete code
- Identifies missing import
- Provides corrected, complete example
- Ensures code actually works

**Test the Fix:**

```text
@workspace Is this code example now complete and syntactically correct? Would it actually work if a user copy-pasted it?
```

**Deliverable:** Add "Missing Import Fix" to automated-fixes.md

---

### VS Code Task 4: Update Outdated Version Reference

**Scenario:** An issue reports: "Documentation still references Python 2.7 which we dropped support for"

**GitHub Copilot Chat Prompt:**

```text
@workspace Issue #27: Update outdated Python version

Issue: "docs/installation.md line 8 says 'Requires Python 2.7+' but we dropped Python 2.7 support. Should be 'Requires Python 3.8+'"

Please:
1. Find all references to Python 2.7 in the documentation
2. Check what the minimum version should be (look at setup.py or pyproject.toml)
3. Update all occurrences to the correct minimum version
4. List all files that need updating

This might affect multiple files.
```

**What Copilot Does:**

- Searches all files for version references
- Identifies correct minimum version
- Finds all places needing updates
- Ensures consistency

**Comprehensive Fix:**

```text
@workspace Generate a complete list of all file changes needed to update Python version references across the docs.
```

**Deliverable:** Add "Version Update Fix" to automated-fixes.md

---

### VS Code Task 5: Add Missing Code Example

**Scenario:** An issue reports: "The authentication section mentions error handling but doesn't show an example"

**GitHub Copilot Chat Prompt:**

```text
@workspace Issue #14: Add missing code example

Issue: "In docs/api-reference.md, the Authentication section (around line 67) mentions handling authentication errors but doesn't provide a code example. Users don't know what error handling should look like."

Please:
1. Find the authentication section
2. Understand the context (what API, what language)
3. Generate a complete, realistic code example showing:
   - Successful authentication
   - Error handling for failed authentication
   - Best practices

4. Suggest where in the file to insert this example
5. Format it properly as a markdown code block with language specifier

Make it practical and copy-paste ready.
```

**What Copilot Does:**

- Reads the context around the section
- Generates realistic, working code example
- Includes proper error handling
- Formats correctly for documentation

**Refine the Example:**

```text
@workspace Make this code example more beginner-friendly by adding inline comments explaining each step.
```

**Deliverable:** Add "Added Code Example" to automated-fixes.md

---

### VS Code Task 6: Batch Process Multiple Typos

**Scenario:** You notice multiple small typos across different files

**GitHub Copilot Chat Prompt:**

```text
@workspace I want to fix multiple typos at once.

Typos to fix:
1. docs/quick-start.md line 23: "seperate" → "separate"
2. docs/api-reference.md line 105: "recieve" → "receive"
3. tutorials/advanced.md line 89: "occured" → "occurred"
4. README.md line 34: "compatability" → "compatibility"

For each:
1. Verify the typo exists
2. Provide the corrected text
3. Generate a single PR description that fixes all 4

Should these be one PR or separate PRs?
```

**What Copilot Does:**

- Analyzes whether to batch or separate
- Locates each typo
- Provides all fixes
- Suggests appropriate PR strategy

**PR Strategy:**

```text
@workspace Create a PR description for fixing all 4 typos in one PR titled "Fix multiple documentation typos"
```

**Deliverable:** Add "Batch Typo Fixes" to automated-fixes.md

---
