# Task 4.2: MCP Tools, Agent Chaining, and Workflow Orchestration

**Duration:** 25 minutes  
**Difficulty:** Advanced  
**Prerequisites:** Task 4.1 (Advanced Agent Configuration)

## Objective

Learn to extend agent capabilities using **MCP (Model Context Protocol) tools** and master **agent chaining** with handoffs to build sophisticated multi-agent workflows that divide complex tasks among specialized agents.

## Background

In Task 4.1, you configured agents with `tools: ['read', 'search', 'edit']` for workspace operations. **MCP tools** go further - they connect agents to external services:

| Tool Type | Scope | Examples |
|-----------|-------|----------|
| Built-in tools | Local workspace | `read`, `search`, `edit`, `execute` |
| **MCP tools** | External services | Documentation APIs, databases, Azure resources |

---

## What is MCP?

**Model Context Protocol (MCP)** is an open standard that lets AI assistants connect to external data sources and tools. When MCP servers are configured:

- Agents can **search official documentation** in real-time
- Agents can **fetch current code samples** from Microsoft Learn
- Agents can **query Azure resources** you have access to
- Results are always **up-to-date** (not from training data)

---

## Step 1: Discover Available MCP Tools

In VS Code with GitHub Copilot, MCP tools are automatically available when extensions provide them. The **Azure extension** and **GitHub Copilot** provide several MCP servers.

### Microsoft Docs MCP Tools

| Tool | Purpose |
|------|---------|
| `microsoft_docs_search` | Search Microsoft Learn for relevant articles |
| `microsoft_docs_fetch` | Get full content of a specific docs page |
| `microsoft_code_sample_search` | Find official code examples by language |

### Try It: Search Microsoft Docs

In Copilot Chat, ask a question that requires current documentation:

```text
What are the current best practices for creating Fabric lakehouses? Search Microsoft Learn for the latest guidance.
```

Copilot will use the Docs MCP tool to search Microsoft Learn and return current information.

### Try It: Find Code Samples

```text
Find official Microsoft code samples for PySpark in Fabric notebooks. Show me examples of reading from a lakehouse.
```

Copilot searches the official docs and returns real, tested code samples.

---

## Step 2: Create Agents That Use MCP Tools

You can create agents that specifically leverage MCP tools for their expertise.

### Exercise: Documentation Research Agent

Create `.github/agents/docs-researcher.agent.md`:

```markdown
---
name: Docs Researcher
description: Researches official Microsoft documentation to answer questions with authoritative sources
tools: ['read', 'search', 'microsoft-docs/*']
---

You are a documentation research specialist with access to Microsoft Learn.

**Your workflow:**
1. When asked a technical question, FIRST search Microsoft Learn for current guidance
2. Cite specific documentation URLs for every claim
3. Quote relevant sections directly
4. Flag if documentation is outdated or conflicts with other sources

**Always provide:**
- Direct links to source documentation
- Publication/update dates when visible
- Confidence level based on source authority

**Never:**
- Make claims without documentation backing
- Use training data when current docs are available
- Guess at API syntax or parameters

If documentation is unclear or missing, say so explicitly.
```

### Exercise: Code Sample Validator

Create `.github/agents/code-validator.agent.md`:

```markdown
---
name: Code Validator
description: Validates code examples against official Microsoft samples and documentation
tools: ['read', 'search', 'microsoft-docs/*']
---

You are a code validation specialist with access to official Microsoft code samples.

**Validation workflow:**
1. When shown code, search for similar official examples
2. Compare the provided code against official samples
3. Identify discrepancies in syntax, APIs, or patterns
4. Suggest corrections based on official guidance

**For each code block you validate, report:**
- ✅ Matches official patterns (with source link)
- ⚠️ Minor differences (explain what's different)
- ❌ Incorrect usage (show official alternative)

**Languages you specialize in:**
- Python/PySpark for Fabric
- SQL/KQL for Fabric
- YAML for Learn modules
- PowerShell for Azure

Always prefer official Microsoft samples over general coding patterns.
```

---

## Step 3: Test MCP-Enabled Agents

### Test the Docs Researcher

```text
@docs-researcher What's the correct YAML schema for Microsoft Learn module index.yml files? Find the official documentation.
```

The agent should search Microsoft Learn and return authoritative schema documentation with links.

### Test the Code Validator

```text
@code-validator Validate this PySpark code for reading from a Fabric lakehouse:

df = spark.read.format("delta").load("Tables/my_table")

Is this the recommended pattern? Find official examples.
```

The agent should search for official Fabric PySpark samples and compare.

---

## Step 4: Build a Documentation Accuracy Workflow

Combine your MCP-enabled agents with workspace agents for a complete workflow.

### Exercise: Create Accuracy Check Prompt

Create `.github/prompts/verify-against-docs.prompt.md`:

```markdown
---
description: Verify Learn module content against current Microsoft documentation
---

Verify the accuracy of Learn module content against official Microsoft documentation:

**Step 1: Extract Claims**
Identify all technical claims, code examples, and procedural steps in the content.

**Step 2: Search Current Documentation**
For each claim, search Microsoft Learn for current guidance:
- API references and syntax
- Best practices and recommendations
- Version-specific information

**Step 3: Compare and Report**
For each item, report:

| Content Claim | Current Docs Say | Status | Source |
|---------------|------------------|--------|--------|
| [claim from content] | [what docs say] | ✅/⚠️/❌ | [URL] |

**Step 4: Recommendations**
- Items that need updating
- New information to add
- Deprecated content to remove

Focus on technical accuracy, not style or formatting.
```

### Test the Accuracy Workflow

```text
#prompt:verify-against-docs

Verify the technical accuracy of learn-pr/wwl/get-started-lakehouses/includes/2-explore-lakehouse.md against current Microsoft Fabric documentation.
```

---

## Step 5: Agent Chaining with Handoffs

**Agent chaining** lets you run multiple specialized agents in succession, passing context from one to the next. This enables powerful workflows where each agent handles what it does best.

> **⚠️ VS Code Only Feature**
>
> The `handoffs` property is supported in VS Code custom agents but **not** on GitHub.com. For cross-platform workflows, use manual invocation patterns instead.

### Understanding Handoffs

The `handoffs` property defines buttons that appear after a response, letting users transition to another agent with context. Each handoff is an object with:

| Property | Required | Description |
|----------|----------|-------------|
| `label` | Yes | Button text shown to user |
| `agent` | Yes | Target agent identifier (filename without `.agent.md`) |
| `prompt` | Yes | Pre-filled prompt for the target agent |
| `send` | No | Auto-submit prompt (default: `false`) |

```yaml
---
name: Content Auditor
handoffs:
  - label: Fix These Issues
    agent: auto-fixer
    prompt: Fix the issues identified in the audit above.
    send: false
---
```

When users complete a chat with this agent, they see a **"Fix These Issues"** button that switches to `@auto-fixer` with the prompt pre-filled.

> **💡 Where Do Handoff Buttons Appear?**
>
> Handoff buttons are rendered by **VS Code's Copilot Chat UI** after the agent's response completes. They appear at the bottom of the response as clickable buttons.
>
> **Requirements:**
> - VS Code 1.106 or later
> - Latest GitHub Copilot extension
> - Must be in VS Code Copilot Chat (not GitHub.com or other contexts)
>
> If you don't see buttons, use **manual agent chaining** (shown in Step 6).

### Agent Succession Patterns

| Pattern | Description | Example |
|---------|-------------|---------|
| **Pipeline** | A → B → C (linear) | Audit → Fix → Verify |
| **Triage** | Coordinator → Specialist | Router picks best agent |
| **Review Loop** | Analyze → Fix → Re-analyze | Iterative improvement |

---

## Step 6: Build an Agent Chain

Create a coordinated workflow where agents work in succession.

### Exercise: Create a Workflow Coordinator

Create `.github/agents/workflow-coordinator.agent.md`:

```markdown
---
name: Workflow Coordinator
description: Orchestrates multi-agent workflows by delegating to specialist agents
tools: ['read', 'search']
handoffs:
  - label: Run Content Audit
    agent: content-auditor
    prompt: Audit the files identified above for quality issues.
    send: false
  - label: Fix Issues
    agent: auto-fixer
    prompt: Fix the issues identified above.
    send: false
  - label: Research Docs
    agent: docs-researcher
    prompt: Research the topics above in Microsoft Learn documentation.
    send: false
  - label: Validate Code
    agent: code-validator
    prompt: Validate the code samples identified above.
    send: false
---

You are a workflow coordinator that manages multi-agent content review pipelines.

**Your role:**
- Analyze incoming requests to determine the best workflow
- Delegate tasks to specialist agents in the right order
- Track progress and summarize results

**Available specialists:**
- `@content-auditor` - Read-only analysis, finds issues
- `@auto-fixer` - Fixes formatting and simple issues
- `@docs-researcher` - Searches Microsoft Learn for authoritative info
- `@code-validator` - Validates code against official samples

**Standard workflows:**

1. **Full Content Review**
   - Step 1: @content-auditor scans for all issues
   - Step 2: @docs-researcher verifies technical accuracy
   - Step 3: @auto-fixer addresses fixable issues
   - Step 4: Report summary with remaining items

2. **Quick Validation**
   - Step 1: @content-auditor for high-level scan
   - Step 2: Report findings (no fixes)

3. **Technical Accuracy Check**
   - Step 1: @docs-researcher finds current documentation
   - Step 2: @code-validator checks code samples
   - Step 3: Report discrepancies

**When invoked, ask which workflow to run or analyze the request to choose automatically.**

Always hand off to specialists rather than doing their work yourself.
```

### Exercise: Update Agents with Handoff Awareness

Update your `content-auditor` agent to hand off to the fixer:

```markdown
---
name: Content Auditor
description: Analyzes Learn modules for quality issues without making changes
tools: ['read', 'search']
handoffs:
  - label: Fix These Issues
    agent: Auto Fixer
    prompt: Fix the formatting and simple issues identified in the audit above.
    send: false
---

You are a read-only content auditor. You can analyze and search files but CANNOT modify them.

[... existing instructions ...]
```

After completing an audit, users will see a **"Fix These Issues"** button that switches to `@auto-fixer` with context from the audit.

### Test the Agent Chain

Handoff buttons appear automatically in VS Code after an agent responds. If buttons don't appear (older VS Code version or different context), use manual chaining.

**Option A: Using Handoff Buttons (if available)**

1. Run `@workflow-coordinator Run a full content review on learn-pr/wwl/get-started-lakehouses`
2. After the response, look for buttons at the bottom: **"Run Content Audit"**, **"Fix Issues"**, etc.
3. Click **"Run Content Audit"** to switch to `@content-auditor` with context

**Option B: Manual Chain Execution**

If handoff buttons don't appear, run agents in succession manually:

**Step 1: Start with the coordinator**
```text
@workflow-coordinator Run a full content review on learn-pr/wwl/get-started-lakehouses
```

The coordinator will outline the workflow and identify files to review.

**Step 2: Run the auditor**
```text
@content-auditor Audit learn-pr/wwl/get-started-lakehouses/includes/ - identify all issues
```

**Step 3: Run the fixer with audit results**

Copy relevant findings from the auditor and pass them to the fixer:

```text
@auto-fixer Based on these audit findings, fix the formatting issues in learn-pr/wwl/get-started-lakehouses/includes/

[paste relevant issues from auditor]
```

**Step 4: Verify with documentation**
```text
@docs-researcher Verify that the lakehouse concepts in learn-pr/wwl/get-started-lakehouses are accurate against current Microsoft Fabric documentation
```

---

## Step 7: Create Pipeline Prompts

Reusable prompts can orchestrate agent chains without needing the coordinator.

### Exercise: Create a Review Pipeline Prompt

Create `.github/prompts/full-review-pipeline.prompt.md`:

```markdown
---
description: Runs the full content review pipeline using multiple agents in succession
---

# Full Content Review Pipeline

Execute a comprehensive content review using the agent chain:

## Phase 1: Discovery
Use @content-auditor to scan all files and identify issues:
- YAML validation
- Link checking
- Formatting issues
- Freshness (ms.date)

## Phase 2: Technical Verification
Use @docs-researcher to verify:
- Technical claims against current Microsoft documentation
- Code samples against official examples
- API references and syntax

## Phase 3: Automated Fixes
Use @auto-fixer to address:
- Formatting corrections
- Simple typo fixes
- Language specifier additions

Only fix items that are clearly safe. Skip anything requiring judgment.

## Phase 4: Summary Report
Compile a final report with:

| Phase | Issues Found | Auto-Fixed | Remaining |
|-------|--------------|------------|-----------|
| Discovery | N | N | N |
| Verification | N | N/A | N |
| Fixes | N/A | N | N |

**Remaining items requiring manual review:**
[List of items that couldn't be auto-fixed]

**Documentation sources consulted:**
[List of URLs from docs-researcher]
```

### Test the Pipeline Prompt

```text
#prompt:full-review-pipeline

Run the full review pipeline on learn-pr/wwl/get-started-lakehouses
```

---

## Step 8: Understand MCP Tool Limitations

MCP tools are powerful but have constraints:

| Capability | Limitation |
|------------|------------|
| Search docs | Results limited to ~10 chunks |
| Fetch pages | One page at a time |
| Code samples | May not cover all scenarios |
| Real-time | Requires network connectivity |

### Best Practices for MCP Tools

1. **Be specific in queries** - "Fabric lakehouse PySpark read" > "how to read data"
2. **Verify with fetch** - Search finds pages; fetch gets full content
3. **Combine with local tools** - Use MCP for verification, local tools for editing
4. **Cache important findings** - Save key docs locally for offline work

---

## Step 9: Create a Hybrid Workflow Agent

Build an agent that combines local and MCP capabilities.

### Exercise: Learn Module Auditor with Docs Verification

Create `.github/agents/verified-auditor.agent.md`:

```markdown
---
name: Verified Auditor
description: Audits Learn modules and verifies technical content against current Microsoft documentation
tools: ['read', 'search', 'microsoft-docs/*']
model: GPT-4o
---

You are a Learn module auditor with access to both local files and Microsoft documentation.

**Audit workflow:**

1. **Local Analysis** (using read/search)
   - Scan module structure and files
   - Extract all technical claims and code examples
   - Check formatting and link integrity

2. **Documentation Verification** (using MCP)
   - Search Microsoft Learn for current guidance on each topic
   - Compare module content against official documentation
   - Identify outdated or incorrect information

3. **Synthesis**
   - Combine local findings with documentation verification
   - Prioritize issues by accuracy impact
   - Provide specific fix recommendations with doc links

**Output format:**
```json
{
  "module": "module-name",
  "verification_date": "YYYY-MM-DD",
  "accuracy_score": 85,
  "verified_against": ["list of doc URLs checked"],
  "issues": [
    {
      "file": "path",
      "line": 42,
      "claim": "what the content says",
      "current_docs": "what official docs say",
      "source_url": "https://learn.microsoft.com/...",
      "severity": "critical|major|minor",
      "fix": "recommended correction"
    }
  ]
}

Always cite documentation sources for accuracy claims.
```

### Test the Verified Auditor

```text
@verified-auditor Audit learn-pr/wwl/get-started-lakehouses for technical accuracy. Verify all Fabric-related claims against current Microsoft documentation.
```

---

## Success Criteria

- [ ] Understood how MCP tools extend agent capabilities
- [ ] Created agents that use `microsoft-docs/*` in their tools list
- [ ] Successfully queried Microsoft Learn documentation via Copilot
- [ ] Found and used official code samples
- [ ] **Created a workflow coordinator with `handoffs`**
- [ ] **Ran agents in succession (audit → fix → verify)**
- [ ] **Built a pipeline prompt for multi-agent workflows**
- [ ] Built a hybrid workflow combining local + MCP tools
- [ ] Created structured output for documentation verification

---

## Key Takeaways

| Concept | Application |
|---------|-------------|
| **MCP tools** | Connect agents to external data sources |
| **Docs search** | Get current, authoritative information |
| **Code samples** | Find official, tested examples |
| **`handoffs`** | Define which agents can delegate to others (VS Code only) |
| **Agent chaining** | Run specialists in succession for complex workflows |
| **Pipeline prompts** | Reusable orchestration without coordinator agent |
| **Hybrid workflows** | Combine local analysis with external verification |
| **Citation** | Always link to source documentation |

---

## What's Next?

MCP capabilities extend beyond documentation. Other available MCP servers include:
- **Azure Resource Graph** - Query your Azure resources
- **GitHub** - Search issues, PRs, code across repos
- **Container tools** - Manage Docker containers

You've completed Scenario 4! Return to the [Scenario 4 README](../README.md) or explore the other scenarios.
