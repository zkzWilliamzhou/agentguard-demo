# AgentGuard Demo Repository

This is a demonstration repository for [AgentGuard](https://github.com/agentguard/agentguard) - the AI Agent Instruction File Health Check tool.

## What is this demo?

This repository demonstrates common issues with AI coding agent instruction files and shows how AgentGuard can help identify and fix them.

## Demo Scenarios

### Scenario 1: Proper AGENTS.md setup
✅ **HEALTHY** - `AGENTS.md` is recognized by all supported agents

### Scenario 2: Wrong file extension
❌ **CRITICAL ISSUE** - `.md` file named `instructions.txt` is not loaded

### Scenario 3: Large file truncation
⚠️ **WARNING** - File exceeds 32KiB truncate limit (Codex/GitHub Copilot)

### Scenario 4: Shadowed instruction file
⚠️ **WARNING** - New file shadowed by old one

## Running AgentGuard

```bash
# Install AgentGuard
pip install agentguard

# Scan this repository
agentguard scan .

# Generate HTML report
agentguard scan . --format html --output report.html
```

## Expected Output

```
AgentGuard - AI Agent Instruction File Health Report
Repository: /path/to/demo

SUMMARY
----------------------------------------
HEALTHY      1
WARNING      2
CRITICAL     1
UNKNOWN      0
TOTAL ISSUES 4

FILE ANALYSIS
----------------------------------------
✓ AGENTS.md
  Status: HEALTHY
  Healthy Agents: ["claude", "codex", "cursor", "gemini", "windsurf", "zed", "aider"]

⚠ large_instructions.md
  Status: WARNING
  Issues:
    [HIGH] File size exceeds 32KiB truncate limit
      → Fix: Split into multiple files

✗ instructions.txt
  Status: CRITICAL
  Issues:
    [CRITICAL] File is not loaded by any supported agent
      → Fix: Rename to AGENTS.md or CLAUDE.md
```

## CI/CD Integration

This demo repository shows how AgentGuard integrates with GitHub Actions:

```yaml
# .github/workflows/agentguard.yml
- name: AgentGuard scan
  run: agentguard scan . --fail-on-critical
```

The CI will fail if any instruction files are not properly loaded by their target agents.

## Learning Resources

- [AgentGuard Documentation](https://github.com/agentguard/agentguard#readme)
- [MCP Integration Guide](https://github.com/agentguard/agentguard#mcp-integration)
- [Supported Agents](https://github.com/agentguard/agentguard#supported-agents)