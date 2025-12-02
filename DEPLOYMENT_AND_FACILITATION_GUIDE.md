# Deployment and Facilitation Guide

## GitHub Repository Management Quest

This guide explains how to deploy this quest and facilitate it as a live demo or workshop.

---

## Table of Contents

1. [Deployment Options](#deployment-options)
2. [Self-Paced Deployment](#self-paced-deployment)
3. [Workshop/Live Demo Setup](#workshoplive-demo-setup)
4. [Facilitation Guide](#facilitation-guide)
5. [Automated Quest Setup (GitHub Actions)](#automated-quest-setup-github-actions)
6. [Technical Setup](#technical-setup)
7. [Troubleshooting](#troubleshooting)

---

## Deployment Options

### Option 1: Self-Paced Individual Learning
**Best for:** Individual learners, async training, onboarding
**Setup Time:** 5 minutes
**Requires:** GitHub account, AI tool access

### Option 2: Guided Workshop
**Best for:** Team training, bootcamps, courses
**Setup Time:** 30-60 minutes
**Requires:** Facilitator, meeting space/virtual room, participant setup

### Option 3: Live Demo/Presentation
**Best for:** Showcasing capabilities, conference talks, lunch & learns
**Setup Time:** 1-2 hours
**Requires:** Prepared demo environment, screen sharing

---

## Self-Paced Deployment

### For Individuals

**Step 1: Access the Quest**

Option A - GitHub Repository:
```bash
# Clone the repository
git clone https://github.com/your-org/github-repo-management-quest.git
cd github-repo-management-quest

# Open in your editor
code .
```

Option B - Download ZIP:
1. Download ZIP from GitHub
2. Extract to your local machine
3. Open in text editor or IDE

**Step 2: Prepare Your Environment**

1. **Install Required Tools:**
   - Git client
   - VS Code: https://code.visualstudio.com/
   - **GitHub Copilot** (Recommended - this quest is designed for Copilot):
     - Install "GitHub Copilot" extension in VS Code
     - Install "GitHub Copilot Chat" extension in VS Code
     - Sign in with your GitHub account
     - Requires: GitHub Copilot subscription (see below)

2. **GitHub Copilot Subscription (Required)**

   This quest is specifically designed for GitHub Copilot. You'll need one of:

   - **Individual Plan**: $10/month - https://github.com/features/copilot
   - **Free for Students/Teachers**: Verify at https://education.github.com/
   - **Business/Enterprise Plan**: If your organization provides it

   **Note:** Some features (like issue-to-PR automation) require Business or Enterprise plans.

3. **Verify GitHub Copilot Setup:**
   ```bash
   # Open VS Code
   # Press Ctrl+Shift+I (Cmd+Shift+I on Mac)
   # Type: @workspace
   # If it autocompletes, you're ready!
   ```

4. **Optional Tools:**
   ```bash
   # Install markdown tools for validation
   npm install -g markdownlint-cli markdown-link-check

   # Install GitHub CLI for automation examples
   brew install gh  # macOS
   # or download from https://cli.github.com/
   ```

**Important Notes**

In order to get the workflows working, you will need to do one of two things:

1. Create a Personal Access Token under Profile > Settings > Developer Settings > Personal Access Tokens > Fine Grained Tokens > Generate new token > "Repository Access" > "Only select repositories" > Add permissions (Actions, Workflows, Pull Requests). Then use `github-token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}`
1. Repository settings > Actions > General > "Workflow Permissions" > "Allow GitHub Actions to create and approve pull requests. Then use `github-token: ${{ secrets.GITHUB_TOKEN }}`

**Step 3: Start the Quest**

1. Read [README.md](README.md)
2. Start with [Scenario 1](scenario-1-inheritance/README.md)
3. Complete tasks in order
4. Reference [resources/](resources/) as needed

**Step 4: Track Progress**

Create a personal progress tracker:
```markdown
# My Quest Progress

## Scenario 1: The Inheritance
- [x] Task 1.1: Repository Exploration
- [x] Task 1.2: Content Audit
- [ ] Task 1.3: Audit Report
- [ ] Task 1.4: Documentation Standards

## Scenario 2: The Big Merge
- [ ] Task 2.1: Initial Review
...
```

### For Organizations

**Deploy to Your Team:**

1. **Fork or Clone** this repository to your organization's GitHub
2. **Customize** (optional):
   - Add your company logo
   - Include company-specific examples
   - Reference your internal documentation standards
3. **Assign** to team members:
   - As onboarding material
   - As professional development
   - As part of technical writing training

**Track Completion:**

Create a tracking sheet:
```
| Team Member | Scenario 1 | Scenario 2 | Scenario 3 | Completed |
|-------------|------------|------------|------------|-----------|
| Alice       | ✅         | ✅         | In Progress| No        |
| Bob         | ✅         | ✅         | ✅         | Yes       |
```

---

## Workshop/Live Demo Setup

### Pre-Workshop Preparation (1-2 Weeks Before)

#### 1. Participant Prerequisites Email

Send this email 1 week before:

```
Subject: Prepare for GitHub Repository Management Workshop

Hi team,

You're registered for the GitHub Repository Management Workshop on [DATE].

Please complete these setup steps BEFORE the workshop:

Required:
✅ Install VS Code: https://code.visualstudio.com/
✅ Install Git: https://git-scm.com/
✅ Create GitHub account (if you don't have one)
✅ Set up AI assistant (choose one):
   - GitHub Copilot: https://github.com/features/copilot
   - Claude: https://claude.ai
   - ChatGPT Plus: https://chatgpt.com

Optional but Recommended:
✅ Basic Git/GitHub knowledge (commit, push, pull, PR)
✅ Familiarity with Markdown syntax

Workshop Materials:
📁 We'll provide the quest materials on the day
📝 Bring a laptop with the above tools installed

Questions? Reply to this email or check our FAQ: [link]

See you at the workshop!
```

#### 2. Prepare Workshop Materials

**Create Workshop Repository:**
```bash
# Clone the quest
git clone https://github.com/your-org/github-repo-management-quest.git
cd github-repo-management-quest

# Create workshop branch (optional)
git checkout -b workshop-YYYY-MM-DD

# Customize for your organization (optional)
# - Add company logo
# - Customize examples
# - Add company-specific scenarios
```

**Prepare Facilitator Materials:**
- [ ] Solution guides for all scenarios
- [ ] Troubleshooting FAQ
- [ ] Timing guide/agenda
- [ ] Backup AI prompts (if tools fail)
- [ ] Example outputs to show

#### 3. Setup Checklist (Day Before)

**Technology:**
- [ ] Test screen sharing (Zoom/Teams/etc.)
- [ ] Test all links in materials
- [ ] Verify quest repository is accessible
- [ ] Prepare backup materials (USB drive, cloud storage)
- [ ] Test AI tools (Copilot, Claude, ChatGPT)
- [ ] Create Zoom breakout rooms (if using)

**Physical/Virtual Space:**
- [ ] Book room with projector/screens
- [ ] Test audio/video
- [ ] Prepare seating (if in-person)
- [ ] Create collaborative space (Miro board, shared doc)
- [ ] Send calendar invites with Zoom link

**Materials:**
- [ ] Print handouts (optional):
  - Quest overview
  - AI prompt cheat sheet
  - Troubleshooting guide
- [ ] Prepare intro slides (optional)
- [ ] Create sign-in sheet or registration form

---

## Facilitation Guide

### Workshop Format Options

#### Option A: Guided Workshop (3 hours)
**Format:** Instructor demonstrates, participants follow along
**Group Size:** 5-30 people
**Structure:**
- 15 min: Introduction & setup verification
- 60 min: Scenario 1 (guided walkthrough)
- 15 min: Break
- 60 min: Scenario 2 (semi-guided)
- 30 min: Scenario 3 overview + discussion
- 30 min: Q&A, wrap-up, next steps

#### Option B: Self-Paced Workshop (4 hours)
**Format:** Participants work at own pace, facilitator provides support
**Group Size:** 5-50 people
**Structure:**
- 15 min: Introduction & kickoff
- 180 min: Self-paced work (all 3 scenarios)
- 30 min: Group discussion & reflection
- 15 min: Wrap-up

#### Option C: Live Demo (60-90 minutes)
**Format:** Facilitator demonstrates, minimal participant interaction
**Group Size:** Any size
**Structure:**
- 10 min: Introduction & context
- 20 min: Scenario 1 demo (repository takeover)
- 20 min: Scenario 2 demo (PR review)
- 20 min: Scenario 3 demo (issue management)
- 10-20 min: Q&A
- 10 min: How to access quest, next steps

---

### Detailed Workshop Agenda

#### 3-Hour Guided Workshop

**0:00-0:15 - Introduction (15 min)**

**Facilitator Script:**
```
Welcome to the GitHub Repository Management Quest!

[Brief intro about yourself]

Today we'll learn AI-assisted techniques for:
- Taking over unfamiliar repositories
- Reviewing complex pull requests
- Managing issue backlogs

Show of hands:
- Who uses GitHub regularly?
- Who has used AI coding assistants?
- Who maintains documentation?

Great! Let's make sure everyone is set up...
```

**Setup Verification:**
- [ ] Everyone has quest files
- [ ] AI tools are working
- [ ] Can open markdown files
- [ ] Share screen to show repository structure

**Quick Setup Check:**
```bash
# Have everyone run these:
git --version
code --version

# Open quest in VS Code
cd github-repo-management-quest
code .
```

---

**0:15-1:15 - Scenario 1: The Inheritance (60 min)**

**Facilitator Approach:** Demonstrate first, then guide participants through

**0:15-0:25 - Task 1.1: Repository Exploration (10 min)**

**Facilitator Script:**
```
Let's start with Scenario 1. Imagine you've inherited a documentation
repository and need to understand it quickly.

Open: scenario-1-inheritance/README.md

[Read the story together - 2 min]

Now let's look at the challenge repository...
```

**Live Demo:**
1. Show the challenge-repo structure
2. Open task-1.1-explore.md
3. Demonstrate using AI prompt from the task
4. Share AI response showing repository analysis
5. Show how to create repository-map.md

**Participant Activity:**
```
Now you try! (5 minutes)

1. Open scenario-1-inheritance/challenge-repo/
2. Read task-1.1-explore.md
3. Use the AI prompt provided
4. Create your repository-map.md

I'll walk around [or check chat] if you need help.
```

**Checkpoint:**
- "Who found the Python utilities?"
- "What documentation gaps did your AI identify?"
- Share 1-2 participant findings

**0:25-0:40 - Task 1.2: Content Audit (15 min)**

**Facilitator Script:**
```
Great! Now that we understand the structure, let's audit
the content quality.

Common issues in documentation:
- Broken links
- Outdated information
- Formatting inconsistencies

Let's use AI to find these problems quickly...
```

**Live Demo:**
1. Show task-1.2-audit.md
2. Pick one audit task (e.g., broken links)
3. Demonstrate AI prompt
4. Show how AI finds issues
5. Create quality-audit.md with findings

**Participant Activity:**
```
Your turn! (10 minutes)

Pick 2-3 audit tasks from task-1.2-audit.md
Use AI to find issues
Document in quality-audit.md

Goal: Find at least 10 specific issues
```

**Group Share:**
- "What's the most critical issue you found?"
- "Anyone find interesting patterns?"
- Discuss common findings

**0:40-0:55 - Task 1.3: Audit Report (15 min)**

**Facilitator Script:**
```
Now let's turn our findings into a professional report
that management can act on.

Key elements:
- Executive summary (non-technical)
- Issues prioritized by impact
- Actionable recommendations
```

**Live Demo:**
1. Show report template in task
2. Use AI to generate executive summary from findings
3. Show prioritization framework
4. Create sample audit-report.md

**Participant Activity:**
```
Create your audit report (10 minutes)

Use AI to help:
1. Write executive summary
2. Prioritize your findings
3. Create action plan

Make it something you'd send to your manager!
```

**0:55-1:10 - Task 1.4: Documentation Standards (15 min)**

**Facilitator Script:**
```
Finally, let's prevent future problems by creating standards.

Think about the issues we found - how could standards have
prevented them?
```

**Quick Demo:**
1. Show standards template
2. Use AI to generate 2-3 standards based on audit findings
3. Emphasize making standards enforceable with automation

**Participant Activity:**
```
Create documentation standards (10 minutes)

Include sections for:
- Markdown formatting
- Link checking
- Review process

Think about your own projects - what standards would help?
```

**Scenario 1 Wrap-Up:**
```
Great work! In 1 hour, we've:
✅ Explored an unfamiliar repository
✅ Audited it for quality issues
✅ Created a professional report
✅ Established prevention standards

Questions before we break?
```

---

**1:10-1:25 - Break (15 min)**

**Facilitator Actions During Break:**
- Check in with struggling participants
- Review questions in chat
- Adjust pacing if needed
- Prepare Scenario 2 demo

---

**1:25-2:25 - Scenario 2: The Big Merge (60 min)**

**Facilitator Approach:** More independent work, facilitator as guide

**1:25-1:35 - Introduction & Task 2.1 Demo (10 min)**

**Facilitator Script:**
```
Welcome back! Scenario 2 is about reviewing a massive PR.

Show of hands - who dreads reviewing large PRs?

Today you'll learn to use AI to review them efficiently
WITHOUT missing important issues.
```

**Quick Demo:**
1. Show scenario-2-big-merge/README.md
2. Explain the scenario (Alex's big PR)
3. Demo task-2.1-initial-review.md approach
4. Show how to get PR overview with AI

**1:35-2:05 - Participant Work Time (30 min)**

**Facilitator Script:**
```
Now you have 30 minutes to work through Scenario 2.

Complete as much as you can:
- Task 2.1: High-level review (required)
- Task 2.2: Detailed review (if time)
- Tasks 2.3-2.4: (stretch goals)

Work at your own pace. I'll circulate to help.

[Set timer visible to everyone]
```

**Facilitator Actions:**
- Walk around (in-person) or monitor chat (virtual)
- Answer questions
- Share interesting findings with group
- At 15 min mark: "How's everyone doing? Questions?"
- At 25 min mark: "5 minutes left, wrap up your current task"

**2:05-2:25 - Group Discussion (20 min)**

**Facilitated Discussion:**
```
Let's share what we learned!

1. "What approach did you use for the high-level review?"
   [Get 2-3 volunteers to share]

2. "What issues did you find in the PR?"
   [Collect on shared screen/whiteboard]

3. "How would you provide feedback to Alex?"
   [Discuss constructive feedback principles]

Key Takeaways:
- Start with big picture before diving into details
- Use AI to find patterns across files
- Balance thoroughness with speed
- Always be constructive in feedback
```

---

**2:25-3:00 - Scenario 3: Overview & Wrap-Up (35 min)**

**Facilitator Script:**
```
Our last scenario is about issue management.
We won't have time to complete it, but let's explore it...
```

**2:25-2:40 - Scenario 3 Quick Demo (15 min)**

**Show Rather Than Do:**
1. Show the 27-issue backlog in issues/ALL_ISSUES.md
2. Demonstrate bulk categorization with AI (live)
3. Show example outputs from tasks
4. Highlight key templates created

**Key Points:**
```
With AI, you can:
- Categorize 25+ issues in minutes
- Find duplicates automatically
- Create professional issue templates
- Draft responses at scale

This transforms an overwhelming backlog into manageable work.
```

**2:40-2:55 - Quest Wrap-Up & Reflection (15 min)**

**Facilitated Reflection:**
```
What will you take back to your work?

[Go around room or use chat]
- One skill you learned
- One thing you'll try next week
- One question you still have
```

**Provide Resources:**
```
Quest materials: [Link to repo]
Resources folder has:
- AI prompts library
- Best practices guide
- Tools guide

Complete Scenario 3 on your own time!
```

**2:55-3:00 - Closing (5 min)**

**Facilitator Script:**
```
Thank you for participating!

Next Steps:
1. Complete remaining scenarios (optional)
2. Apply these techniques to your repositories
3. Share what you learned with your team

Feedback form: [link]
Questions: [your email]

Keep in touch - I'd love to hear how you use this!
```

---

## Live Demo Format (60-90 min)

**Best for:** Showcasing the quest, conference talks, lunch & learns

### Setup Requirements

**Before the Demo:**
1. **Prepare Demo Environment:**
   ```bash
   # Create clean demo directory
   git clone [quest-repo] demo-environment
   cd demo-environment

   # Pre-open key files in VS Code
   # Pre-write some AI prompts in text file for speed
   # Have example outputs ready to show
   ```

2. **Pre-Stage Demonstrations:**
   - Pre-run AI prompts so you can show results quickly
   - Take screenshots of key steps
   - Prepare "magic" moments (reveals, before/after comparisons)
   - Have backup recordings in case of technical issues

3. **Create Demo Flow Document:**
   ```markdown
   # Demo Script

   ## Slide 1: Problem
   [Show pain point of managing docs]

   ## Demo 1: Scenario 1
   [Show specific steps...]

   ## Slide 2: Impact
   [Show time saved, quality improved]
   ```

### 60-Minute Live Demo Agenda

**0:00-0:10 - Introduction**
- Problem: Documentation repo management is hard
- Solution: AI-assisted workflows
- What you'll see: 3 real-world scenarios

**0:10-0:25 - Scenario 1 Demo**
- Show: Inheriting unfamiliar repo
- Demonstrate: AI-assisted exploration
- Reveal: Complete audit in minutes
- Impact: "Usually takes hours, we did it in 10 minutes"

**0:25-0:40 - Scenario 2 Demo**
- Show: Massive PR to review
- Demonstrate: AI-assisted PR review
- Reveal: Found 10+ issues efficiently
- Impact: "Thorough review in 15 minutes"

**0:40-0:50 - Scenario 3 Demo**
- Show: 27-issue backlog chaos
- Demonstrate: AI-assisted triage
- Reveal: Categorized, prioritized, actionable plan
- Impact: "Transformed overwhelming backlog"

**0:50-0:60 - Wrap-Up**
- Key benefits: Speed + thoroughness
- How to access quest
- Q&A

### Demo Tips

**Do:**
✅ Practice the demo 3+ times
✅ Have backup screenshots/recordings
✅ Pre-write AI prompts for speed
✅ Use a clean, organized workspace
✅ Zoom in on text (make it readable)
✅ Narrate what you're doing
✅ Show real, unpolished examples
✅ Emphasize time saved

**Don't:**
❌ Type complex prompts live (too slow)
❌ Wait for AI responses (pre-run or have ready)
❌ Show every detail (highlight key points)
❌ Assume audience knows Git/GitHub
❌ Rush through (better to cover less well)
❌ Skip the "why" (explain value)

---

## Automated Quest Setup (GitHub Actions)

### Overview

The quest includes GitHub Actions workflows to automatically create sample issues and PRs for workshops and demos. This saves significant setup time and ensures consistent, high-quality sample data.

### Available Workflows

#### 1. Setup Quest Issues (`setup-quest-issues.yml`)

**What it does:**
- Creates 8 sample issues for Scenario 3 (Issue Management)
- Issues include bugs, documentation problems, feature requests, questions
- Some issues are intentionally duplicates or vague (for practice)
- All tagged with `quest-sample` label for easy cleanup

**When to use:**
- Before workshop: Day before or morning of
- For demos: When showing issue management capabilities
- For testing: Verify Copilot issue features work

**How to run:**

1. **Via GitHub Web Interface:**
   - Go to your repository on GitHub.com
   - Click "Actions" tab
   - Select "Setup Quest Issues" workflow
   - Click "Run workflow" button
   - Choose scenario: `scenario-3` or `all`
   - Click "Run workflow"

2. **Via GitHub CLI:**
   ```bash
   gh workflow run setup-quest-issues.yml
   ```

**Sample issues created:**
- Issue #1: API authentication bug (detailed)
- Issue #2: Documentation typo (good for auto-fix)
- Issue #3: Broken link (good for auto-fix)
- Issue #4: Feature request (dark mode)
- Issue #5: Duplicate of Issue #1 (for finding duplicates)
- Issue #6: Vague issue (needs more info)
- Issue #7: Missing code import (good for auto-fix)
- Issue #8: Question (categorization practice)

#### 2. Setup Quest PR (`setup-quest-pr.yml`)

**What it does:**
- Creates a sample pull request for Scenario 2 (PR Review)
- PR includes new documentation files and updates
- Intentionally includes issues for review practice
- Creates a feature branch automatically

**When to use:**
- Before workshop: Day before
- For demos: When demonstrating PR review
- For testing: Verify Copilot PR features work

**How to run:**

1. **Via GitHub Web Interface:**
   - Go to Actions → "Setup Quest PR"
   - Click "Run workflow"
   - Choose PR size: `small`, `medium`, or `large`
   - Click "Run workflow"

2. **Via GitHub CLI:**
   ```bash
   gh workflow run setup-quest-pr.yml
   ```

**What the PR includes:**
- New integration tutorial
- Quick reference guide
- Updated README
- **Intentional issues:**
  - Outdated Python version (Python 2.7)
  - Broken link to deleted file
  - Link to old domain
  - Typo: "experiance" → "experience"

**Perfect for practicing:**
- PR review with @workspace
- Finding cross-file issues
- Generating constructive feedback
- Using Copilot's PR summary feature

#### 3. Cleanup Quest Samples (`cleanup-quest-samples.yml`)

**What it does:**
- Closes all sample issues (labeled `quest-sample`)
- Closes all sample PRs (labeled `quest-sample`)
- Deletes sample feature branches
- Leaves comments explaining closure
- Cleans up your repository after workshop

**When to use:**
- After workshop completion
- After demo is done
- Before next workshop (to start fresh)
- When repository needs cleanup

**How to run:**

1. **Via GitHub Web Interface:**
   - Go to Actions → "Cleanup Quest Samples"
   - Click "Run workflow"
   - **Important:** Type `DELETE` to confirm
   - Click "Run workflow"

2. **Via GitHub CLI:**
   ```bash
   gh workflow run cleanup-quest-samples.yml -f confirm=DELETE
   ```

**Safety features:**
- Requires confirmation (must type "DELETE")
- Only affects items labeled `quest-sample`
- Leaves helpful comments on closed items
- Does not delete real issues/PRs

### Workshop Setup Checklist

**1-2 Days Before Workshop:**

- [ ] Run "Setup Quest Issues" workflow
  ```bash
  gh workflow run setup-quest-issues.yml
  ```
- [ ] Run "Setup Quest PR" workflow
  ```bash
  gh workflow run setup-quest-pr.yml
  ```
- [ ] Verify issues created (check Issues tab)
- [ ] Verify PR created (check Pull Requests tab)
- [ ] Test with GitHub Copilot
  - Open VS Code
  - Press `Ctrl+Shift+I`
  - Type: `@workspace Categorize all issues labeled quest-sample`
  - Verify Copilot can see and analyze them

**Day of Workshop:**

- [ ] Verify sample issues still open
- [ ] Verify sample PR still open
- [ ] Test Copilot @workspace can see them
- [ ] Have cleanup workflow ready for after

**After Workshop:**

- [ ] Run "Cleanup Quest Samples" workflow
  ```bash
  gh workflow run cleanup-quest-samples.yml -f confirm=DELETE
  ```
- [ ] Verify all samples cleaned up
- [ ] Repository ready for next workshop

### Troubleshooting Workflows

**Problem:** Workflow fails with permissions error

**Solution:**
```yaml
# Ensure repository settings have correct permissions:
# Settings → Actions → General → Workflow permissions
# Select: "Read and write permissions"
```

**Problem:** Issues/PRs not created

**Solution:**
- Check Actions tab for workflow run logs
- Verify you have issues/PR permissions
- Check if issue/PR limits reached

**Problem:** Can't find the workflow

**Solution:**
- Workflows are in `.github/workflows/` directory
- Must be on `main` or `master` branch
- Check Actions tab is enabled in repository settings

**Problem:** Cleanup doesn't remove everything

**Solution:**
- Manually verify `quest-sample` label exists
- Check if items were created with different labels
- Use GitHub CLI to force close:
  ```bash
  gh issue close 1 2 3 4 5 6 7 8 --comment "Cleanup after quest"
  ```

### Manual Setup (Without Workflows)

If GitHub Actions isn't available, you can manually create sample issues:

**Quick Manual Setup:**

```bash
# Create sample issues manually
gh issue create --title "[Quest Sample] API authentication failing" \
  --body "Authentication error with valid API key..." \
  --label "quest-sample,bug"

gh issue create --title "[Quest Sample] Typo in docs" \
  --body "Line 12 has 'experiance' should be 'experience'" \
  --label "quest-sample,docs,good-first-issue"

# Repeat for other issues...
```

**Or use the provided issue templates:**
- All sample issue content is in the workflow files
- Copy/paste from `.github/workflows/setup-quest-issues.yml`
- Create issues manually via GitHub web interface

### Benefits of Automated Setup

✅ **Saves Time:**
- Manual setup: 30-45 minutes
- Automated: 2 minutes + workflow run time (1-2 min)
- Total savings: ~30-40 minutes per workshop

✅ **Consistency:**
- Same issues every time
- Ensures all practice scenarios covered
- No forgotten issues

✅ **Quality:**
- Issues are well-written
- Include all necessary details
- Demonstrate best/worst practices

✅ **Easy Cleanup:**
- One command cleans everything
- No leftover test data
- Repository stays organized

### Advanced: Customizing Workflows

**To customize sample issues:**

1. Edit `.github/workflows/setup-quest-issues.yml`
2. Modify issue titles, bodies, or labels
3. Add more issues or remove some
4. Commit and push changes
5. Run updated workflow

**Example customization:**

```yaml
# Add company-specific issue
- name: Create Company-Specific Issue
  uses: actions/github-script@v7
  with:
    script: |
      await github.rest.issues.create({
        owner: context.repo.owner,
        repo: context.repo.repo,
        title: '[Quest Sample] Update company branding',
        body: 'Please update documentation with new company logo and colors.',
        labels: ['quest-sample', 'company-specific']
      });
```

**To customize the sample PR:**

1. Edit `.github/workflows/setup-quest-pr.yml`
2. Modify the files created in the PR
3. Change the intentional issues
4. Adjust PR description
5. Commit and run

---

## Technical Setup

### For Facilitators

**Computer Setup:**
```bash
# Install presentation tools
brew install --cask rectangle  # Window management (Mac)
# or
choco install microsoft-powertoys  # Windows

# Install screen recording
brew install --cask obs  # For backup recordings

# Configure VS Code for presentations
code --install-extension vscodevim.vim  # Optional
code --install-extension ritwickdey.LiveServer

# Increase font size for demos
# VS Code: Cmd/Ctrl + = (or Settings > Font Size: 16-18)
```

**VS Code Presentation Settings:**
```json
{
  "editor.fontSize": 18,
  "editor.lineHeight": 1.5,
  "editor.minimap.enabled": false,
  "workbench.activityBar.visible": true,
  "workbench.statusBar.visible": true,
  "editor.renderWhitespace": "none",
  "breadcrumbs.enabled": true
}
```

**AI Tool Setup:**
- **Copilot:** Pre-authenticate, verify working
- **Claude:** Open in browser tab, logged in
- **ChatGPT:** Open in browser tab, logged in
- Have backup text file with prompts

**Screen Sharing Settings:**
- Hide desktop clutter
- Close unrelated tabs/windows
- Disable notifications
- Use "Do Not Disturb" mode
- Test audio/video before start

### For Participants

**Provide Setup Guide:**

```markdown
# Workshop Setup Guide

## Required Software

1. **VS Code** (Free)
   - Download: https://code.visualstudio.com/
   - Install: Follow installer prompts
   - Verify: Run `code --version` in terminal

2. **Git** (Free)
   - Download: https://git-scm.com/
   - Install: Follow installer prompts
   - Verify: Run `git --version` in terminal

3. **AI Assistant** (Choose one):
   - GitHub Copilot ($10/mo, free for students)
   - Claude (Free tier available)
   - ChatGPT Plus ($20/mo)

## Recommended Extensions

Install in VS Code:
- Markdown All in One
- markdownlint

## Getting the Quest Materials

Option 1: Git Clone
```bash
git clone [quest-repo-url]
cd github-repo-management-quest
code .
```

Option 2: Download ZIP
1. Visit [repo-url]
2. Click "Code" > "Download ZIP"
3. Extract and open in VS Code

## Verify Setup

Run these commands:
```bash
git --version    # Should show version
code --version   # Should show version
```

Open VS Code and:
- Open Command Palette (Cmd/Ctrl+Shift+P)
- Type "Copilot" (or open Claude/ChatGPT)
- Verify AI tool is working

## Troubleshooting

**VS Code won't open:**
- On Mac: Install command line tools
- On Windows: Add to PATH

**AI tool not working:**
- Check internet connection
- Verify account is active
- Try restarting VS Code

**Can't clone repository:**
- Check Git is installed
- Verify repository URL
- Try download ZIP instead

Questions? Email [facilitator-email]
```

---

## Troubleshooting

### Common Issues

#### Issue: AI Tool Not Responding

**Causes:**
- Network issues
- Account not authenticated
- Rate limiting
- Service outage

**Solutions:**
1. Check internet connection
2. Re-authenticate
3. Switch to backup AI tool
4. Use pre-written prompts as manual guide

**Facilitator Backup Plan:**
```
"Looks like [AI tool] is having issues.
Let me show you the example output I prepared...

[Show pre-generated examples]

The process is the same - you'd use this prompt:
[Show prompt]

And get a response like:
[Show example]
```

#### Issue: Participants Falling Behind

**Causes:**
- Technical difficulties
- Varying skill levels
- Unclear instructions

**Solutions:**
1. **Pause and Sync:**
   ```
   "Let's all get to the same point.
   If you're on Task 1.2, that's perfect.
   If you're still on 1.1, no problem - we'll catch you up."
   ```

2. **Breakout Support:**
   - Send struggling participants to breakout room with assistant
   - Main room continues
   - Rejoin when ready

3. **Provide Completed Examples:**
   ```
   "If you're stuck, you can use this example output:
   [Link to solution]

   Focus on understanding the process, not perfecting the output."
   ```

#### Issue: Task Taking Longer Than Expected

**Solutions:**
1. **Adjust on the Fly:**
   ```
   "This is taking longer than planned. Let's...

   Option A: Finish this together (demo remaining steps)
   Option B: Skip to highlights (show key points)
   Option C: Make this homework (provide guidance)"
   ```

2. **Prioritize Learning Objectives:**
   - Focus on most valuable skills
   - Skip less critical tasks
   - Provide summary of skipped content

#### Issue: Mixed Experience Levels

**Solutions:**
1. **Pair Programming:**
   ```
   "Let's pair up:
   - Experienced with beginner
   - Work together on tasks
   - Teach each other"
   ```

2. **Differentiated Tasks:**
   - Beginners: Follow step-by-step
   - Intermediate: Less guidance
   - Advanced: Bonus challenges

3. **Multiple Tracks:**
   ```
   Track 1 (Beginners): Follow along with me
   Track 2 (Advanced): Try Scenario 3 independently

   We'll reconvene in 20 minutes.
   ```

---

## Post-Workshop Follow-Up

### Immediately After (Same Day)

**Send Thank You Email:**
```
Subject: Thanks for Joining the GitHub Repository Management Workshop!

Hi everyone,

Thanks for participating today! Here's what we covered:

✅ Scenario 1: Repository Exploration & Auditing
✅ Scenario 2: PR Review with AI
✅ Scenario 3: Issue Management (overview)

Resources:
📁 Quest Repository: [link]
📝 Workshop Recording: [link] (if recorded)
💬 Feedback Form: [link]
❓ Questions: Reply to this email

Next Steps:
1. Complete Scenario 3 on your own
2. Apply these techniques to your repos
3. Share learnings with your team

See you at the next workshop!

[Your name]
```

### Follow-Up (1 Week Later)

**Check-In Email:**
```
Subject: How's the Quest Going?

Hi team,

It's been a week since our workshop. How are you doing?

Quick check-in:
- Have you completed Scenario 3?
- Have you applied any techniques to your work?
- Any questions or challenges?

Optional: Join our office hours this Friday at 2pm to discuss!

[Link to calendar invite]
```

### Long-Term (1 Month Later)

**Impact Assessment:**
- Survey participants on skills applied
- Collect success stories
- Gather feedback for improvement
- Share aggregated results

---

## Measuring Success

### Workshop Success Metrics

**Immediate (During Workshop):**
- Participation rate (% completing exercises)
- Questions asked (engagement)
- Technical issues encountered (smoothness)

**Short-Term (1 Week After):**
- Quest completion rate
- Feedback survey scores
- Skills application (self-reported)

**Long-Term (1-3 Months After):**
- Improved documentation quality
- Faster PR reviews
- Reduced issue backlog
- Team adoption of techniques

### Survey Questions

**Post-Workshop Survey:**
```markdown
1. How satisfied were you with the workshop? (1-5)
2. How clearly were concepts explained? (1-5)
3. How useful is this content for your work? (1-5)
4. What was most valuable?
5. What should we improve?
6. Will you complete the remaining scenarios?
7. Will you apply these techniques to your work?
8. Would you recommend this workshop?
```

**Follow-Up Survey (1 Month):**
```markdown
1. Have you completed the quest?
2. Have you applied these techniques?
3. Which techniques have you used?
4. What impact have you seen? (time saved, quality improved, etc.)
5. Have you shared with your team?
6. What barriers prevented application?
7. What additional support would help?
```

---

## Quick Reference: Facilitation Cheat Sheet

### Opening Lines
```
"Welcome! Today we're going to learn AI-assisted repository management..."

"Show of hands - who maintains documentation?"

"By the end of today, you'll be able to..."
```

### Transition Lines
```
"Great work on that! Let's move to..."

"Now that we understand X, let's look at Y..."

"I'm seeing some great examples, let's share a few..."
```

### Time Management
```
"We have 15 minutes for this section..."

"5 minutes left, wrap up what you're doing..."

"If you're not done, that's fine - focus on the process..."
```

### Handling Questions
```
"Great question! [Answer] Does that help?"

"I don't know off the top of my head, let me follow up..."

"Who else has experience with this? [Leverage group knowledge]"
```

### Encouraging Participation
```
"Turn to your neighbor and share what you found..."

"In the chat, tell me one thing you learned..."

"Who wants to share their example?"
```

---

## Conclusion

This quest can be deployed in multiple ways:
- ✅ Self-paced individual learning
- ✅ Guided team workshop
- ✅ Live demonstration
- ✅ Hybrid approach

**Key Success Factors:**
1. Adequate preparation
2. Clear instructions
3. Working technology
4. Engaged facilitation
5. Follow-up support

**Remember:** The goal is learning, not perfection. Encourage experimentation and celebrate progress!

---

**Questions about deployment or facilitation?**
- Open an issue in this repository
- Contact [maintainer email]
- See the [README.md](README.md) for additional resources

**Good luck with your workshop!** 🚀
