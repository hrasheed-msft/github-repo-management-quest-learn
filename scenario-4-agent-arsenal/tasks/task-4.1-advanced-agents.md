# Task 4.1: Advanced Agent Configuration

**Duration:** 20 minutes  
**Difficulty:** Advanced  
**Prerequisites:** Module 0 (agent basics), familiarity with `.agent.md` file structure

## Objective

Master advanced agent configuration options: **tool permissions**, **model selection**, **target platforms**, and **structured outputs** that enable more powerful and reliable agent behavior.

## Background

In Module 0, you created basic agents with a name, description, and instructions. Now you'll learn the advanced YAML properties that control **what agents can do**, **how they think**, and **where they run**.

## Advanced YAML Properties

| Property | Purpose | Example Values |
|----------|---------|----------------|
| `tools` | What actions the agent can perform | `["read", "search", "edit", "run"]` |
| `model` | Which AI model to use (VS Code only) | `gpt-4o`, `claude-sonnet-4-20250514`, `o1` |
| `target` | Where the agent is available | `vscode`, `github-copilot` |

---

## Step 1: Configure Tool Permissions

Tools control what your agent can actually **do** in the workspace. Without tools, agents can only chat.

### Available Tools

| Tool | Capability | Use Case |
|------|------------|----------|
| `read` | Read files in workspace | Analysis, review, auditing |
| `search` | Search across files | Finding patterns, references |
| `edit` | Modify files | Automated fixes, refactoring |
| `run` | Execute terminal commands | Build, test, deploy tasks |
| `mcp` | Use MCP server tools | External integrations |

### Exercise: Create a Read-Only Auditor

Create `.github/agents/content-auditor.agent.md`:

```markdown
---
name: Content Auditor
description: Analyzes Learn modules for quality issues without making changes
tools: ["read", "search"]
---

You are a read-only content auditor. You can analyze and search files but CANNOT modify them.

Your audit checklist:
1. Check ms.date freshness (flag if > 12 months old)
2. Find broken internal links
3. Identify code blocks without language specifiers
4. Flag TODO/FIXME markers

Always output findings in this format:
- **File**: [path]
- **Issue**: [description]
- **Severity**: Critical | Major | Minor
- **Line**: [number if applicable]
```

### Exercise: Create an Auto-Fix Agent

Create `.github/agents/auto-fixer.agent.md`:

```markdown
---
name: Auto Fixer
description: Automatically fixes common documentation issues
tools: ["read", "search", "edit"]
---

You are an automated fixer with permission to edit files. Only fix issues that are:
- Clearly wrong (typos, broken syntax)
- Safe to change (formatting, not content meaning)
- Reversible (user can undo via git)

Before editing, always:
1. Explain what you'll change and why
2. Show the before/after diff
3. Wait for user confirmation unless they say "auto-fix all"

Never change:
- Technical content meaning
- Code logic
- API endpoints or parameters
```

### Test Tool Differences

Try both agents on the same content:

```text
@content-auditor Analyze learn-pr/wwl/get-started-lakehouses for quality issues
```

```text
@auto-fixer Fix any formatting issues in learn-pr/wwl/get-started-lakehouses/includes/1-introduction.md
```

**Notice:** The auditor reports issues; the fixer offers to change them.

---

## Step 2: Model Selection for Different Tasks

Different models excel at different tasks. Use `model:` to match the right model to the job.

### Model Capabilities

| Model | Best For | Trade-offs |
|-------|----------|------------|
| `gpt-4o` | Fast responses, code generation | Default, good all-around |
| `claude-sonnet-4-20250514` | Complex analysis, nuanced writing | Excellent reasoning |
| `o1` | Deep reasoning, complex problems | Slower, more expensive |
| `o1-mini` | Reasoning with faster response | Good balance |

### Exercise: Create a Deep Analysis Agent

Create `.github/agents/deep-analyzer.agent.md`:

```markdown
---
name: Deep Analyzer
description: Uses advanced reasoning for complex content architecture analysis
tools: ["read", "search"]
model: o1
---

You are a deep analysis specialist using advanced reasoning capabilities.

When analyzing content:
1. Think step-by-step through the problem
2. Consider multiple perspectives
3. Identify non-obvious relationships
4. Provide confidence levels for conclusions

Use your reasoning capabilities for:
- Complex dependency analysis
- Content gap identification across learning paths
- Strategic recommendations with trade-off analysis

Always explain your reasoning process.
```

### Exercise: Create a Fast Responder

Create `.github/agents/quick-check.agent.md`:

```markdown
---
name: Quick Check
description: Fast responses for simple validation tasks
tools: ["read"]
model: gpt-4o
---

You are optimized for speed. Provide quick, direct answers.

For validation tasks:
- Give yes/no answers with brief justification
- Use bullet points, not paragraphs
- Skip pleasantries and get to the point

If a question needs deeper analysis, say: "This needs @deep-analyzer for proper analysis."
```

### Test Model Differences

```text
@quick-check Does learn-pr/wwl/get-started-lakehouses/index.yml have all required fields?
```

```text
@deep-analyzer Analyze the learning path architecture for the Fabric modules. What content gaps exist and how should they be addressed?
```

---

## Step 3: Platform Targeting

Use `target:` to control where agents appear.

### Target Options

| Target | Where It Runs | Use Case |
|--------|---------------|----------|
| `vscode` | VS Code only | Uses VS Code-specific features |
| `github-copilot` | GitHub.com only | PR reviews, issue triage |
| *(omit)* | Available everywhere | General-purpose agents |

### Exercise: Create a PR Review Agent (GitHub-only)

Create `.github/agents/pr-reviewer.agent.md`:

```markdown
---
name: PR Reviewer
description: Specialized for GitHub pull request reviews
target: github-copilot
---

You are a PR review specialist optimized for GitHub.com workflows.

When reviewing PRs:
1. Focus on the diff, not the entire file
2. Leave specific, actionable inline comments
3. Categorize feedback: Blocker | Suggestion | Nitpick
4. Summarize with clear Approve/Request Changes recommendation

Use GitHub-native features:
- Reference line numbers for inline comments
- Use GitHub markdown (task lists, mentions)
- Suggest specific code changes when possible
```

### Exercise: Create a VS Code Debug Agent

Create `.github/agents/debug-helper.agent.md`:

```markdown
---
name: Debug Helper
description: Uses VS Code debugging features for troubleshooting
target: vscode
tools: ["read", "search", "run"]
---

You are a debugging specialist with access to VS Code terminal.

Your debugging workflow:
1. Analyze error messages and stack traces
2. Search codebase for related code
3. Suggest and run diagnostic commands
4. Propose fixes with explanations

VS Code-specific capabilities:
- Access to integrated terminal
- Can read any file in workspace
- Can search across all files
```

---

## Step 4: Structured Output for Reliability

Train agents to output consistent, parseable formats for reliable workflows.

### Exercise: Create a JSON Output Agent

Create `.github/agents/structured-auditor.agent.md`:

```markdown
---
name: Structured Auditor
description: Outputs audit results in parseable JSON format
tools: ["read", "search"]
---

You are an auditor that ALWAYS outputs results in valid JSON format.

**Output Schema:**
```json
{
  "audit_date": "YYYY-MM-DD",
  "files_analyzed": 0,
  "summary": {
    "critical": 0,
    "major": 0,
    "minor": 0
  },
  "issues": [
    {
      "file": "path/to/file.md",
      "line": 42,
      "severity": "critical|major|minor",
      "category": "freshness|links|formatting|accuracy",
      "description": "What's wrong",
      "fix": "How to fix it"
    }
  ],
  "recommendations": ["List of improvement suggestions"]
}
```

Rules:
- Always return valid JSON (no markdown code fences in the JSON itself)
- Include ALL fields even if empty arrays
- Use lowercase for severity and category values
- Be specific in descriptions and fixes
```

### Test Structured Output

```text
@structured-auditor Audit learn-pr/wwl/get-started-lakehouses/includes/ and return JSON results
```

You can use this JSON output in:
- Automated workflows
- Issue creation scripts
- Dashboard reporting
- Quality tracking over time

---

## Step 5: Combine Advanced Features

Create an agent that uses multiple advanced features together.

### Exercise: Full-Featured Review Agent

Create `.github/agents/enterprise-reviewer.agent.md`:

```markdown
---
name: Enterprise Reviewer
description: Full-featured content review agent with all capabilities
tools: ["read", "search", "edit"]
model: claude-sonnet-4-20250514
---

You are an enterprise-grade content reviewer with full capabilities.

**Capabilities:**
- ✅ Read and search all files
- ✅ Edit files with user confirmation
- ✅ Advanced reasoning for complex analysis

**Review Workflow:**

1. **Discovery Phase** (read + search)
   - Scan all files in scope
   - Build dependency map
   - Identify patterns

2. **Analysis Phase** (reasoning)
   - Evaluate against quality criteria
   - Prioritize issues by impact
   - Generate recommendations

3. **Action Phase** (edit with confirmation)
   - Offer to fix simple issues
   - Show diffs before changes
   - Create summary report

**Output Format:**
Start with JSON summary, then provide detailed analysis:

```json
{
  "status": "pass|needs_work|critical",
  "score": 85,
  "blockers": 0,
  "warnings": 3,
  "suggestions": 5
}
```

Then provide detailed findings with specific file references.
```

---

## Success Criteria

- [ ] Created agents with different tool permissions (read-only vs edit)
- [ ] Experimented with model selection for different tasks
- [ ] Created platform-targeted agents (VS Code vs GitHub)
- [ ] Built an agent with structured JSON output
- [ ] Combined multiple advanced features in one agent

---

## Key Takeaways

| Feature | When to Use |
|---------|-------------|
| `tools: ["read"]` | Analysis-only, safe exploration |
| `tools: ["edit"]` | Automated fixes, refactoring |
| `model: o1` | Complex reasoning, architecture decisions |
| `model: gpt-4o` | Fast responses, simple tasks |
| `target: vscode` | Terminal access, debugging |
| `target: github-copilot` | PR reviews, issue management |
| Structured output | Automation, reporting, pipelines |

---

**Ready to orchestrate multiple agents?** Continue to [Task 4.2: Workflow Orchestration](task-4.2-workflow-orchestration.md).