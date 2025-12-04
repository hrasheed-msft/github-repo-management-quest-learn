Copilot for Microsoft Fabric data agents supports several advanced scenarios that extend beyond basic data retrieval. These capabilities enable more sophisticated interactions with your organizational data.

## Multi-turn conversations

Data agents maintain context across multiple conversation turns, allowing users to refine their queries progressively:

1. User asks: "Show me sales data for Q4"
2. Agent returns Q4 sales summary
3. User follows up: "Now compare that to Q3"
4. Agent understands "that" refers to Q4 sales and provides comparison

This contextual awareness reduces the need for users to repeat information in each query.

## Cross-source data correlation

When configured with access to multiple data sources, agents can correlate information across:

- OneLake lakehouses
- Data warehouses
- Semantic models
- External data connections

```python
# Example: Agent correlating customer data across sources
from fabric.dataagent import DataAgent

agent = DataAgent(workspace="sales-analytics")
response = agent.query(
    "Compare customer satisfaction scores with purchase frequency"
)
```

## Automated insight generation

Data agents can proactively identify trends and anomalies in your data without explicit prompting. Configure this behavior in the agent settings:

| Setting | Description | Default |
|---------|-------------|---------|
| auto_insights | Enable automatic insight generation | False |
| insight_frequency | How often to scan for insights | Daily |
| anomaly_threshold | Sensitivity for anomaly detection | Medium |

## Integration with Power BI

Data agents integrate seamlessly with Power BI reports and dashboards. Users can:

- Ask questions about visualized data
- Request drill-down analysis
- Generate natural language summaries of report pages

> [!NOTE]
> Power BI integration requires the workspace to have both Fabric capacity and Power BI Pro licensing.
