When working with Fabric data agents, you may encounter various issues. This guide helps you diagnose and resolve common problems.

## Agent not responding

If your data agent isn't responding to queries:

1. Verify Fabric capacity is running and not paused
2. Check that the agent is enabled in workspace setings
3. Confirm user has appropriate permissions
4. Review the agent activity log for errors

## Incorrect or incomplete responses

When agent responses don't match expectations:

### Check data freshness

Data agents query the most recent data avialable. If data seems outdated:

- Verify lakehouse data refresh completed
- Check semantic model refresh schedule
- Confirm data pipeline ran successfully

### Improve query specificity

Vague queries produce vague responses. Instead of:
- "Show me the data" ❌

Try:
- "Show me monthly sales totals for the North region in 2024" ✓

## Performance issues

Slow response times often indicate:

| Symptom | Likely Cause | Solution |
|---------|--------------|----------|
| > 30s response | Large dataset scan | Add aggregation layer |
| Timeout errors | Complex joins | Simplify data model |
| Intermitent slowness | Capacity throttling | Review capacity metrics |

## Error messages

Common error codes and their meanings:

```
AGENT_001: Agent not initialized
Solution: Wait 2-3 minutes after agent creation

AGENT_002: Insufficient permissions  
Solution: Grant user 'Viewer' role or higher on workspace

AGENT_003: Data source unavailable
Solution: Check lakehouse/warehouse connectivity
```

## Getting help

If issues persist, gather diagnostic information:

1. Agent ID and workspace ID
2. Exact error message or unexpected behavior
3. Sample query that reproduces the issue
4. Timestamp of when the issue occured

Contact support at [Fabric Support](http://old-support.fabric.com/help).

> [!TIP]
> Enable verbose logging temporarily to capture detailed diagnostics for complex issues.
