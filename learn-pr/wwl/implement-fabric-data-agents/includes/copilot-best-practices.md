Follow these best practices when implementing Copilot data agents in your Microsoft Fabric environment to ensure optimal performance and user experience.

## Data preparation

Proper data preparation is essential for effective data agent responses:

- **Use descriptive column names**: Agents work better with columns named "CustomerPurchaseDate" than "CPD"
- **Add data descriptions**: Document tables and columns in your semantic model
- **Maintain data quality**: Clean, consistent data produces more accurate responses

## Security configuration

Configure appropriate security boundaries for your data agents:

1. Enable row-level security (RLS) on sensitive data
2. Use workspace roles to control agent access
3. Review audit logs regularly for unusual query patterns

## Performance optimization

Optimize agent performance with these techniques:

```kusto
// Use materialized views for frequently queried aggregations
.create materialized-view SalesSummary on SalesTable
{
    SalesTable
    | summarize TotalSales = sum(Amount) by Region, ProductCategory
}
```

## Common mistakes to avoid

- Don't expose raw transactional tables directly to agents
- Avoid overly complex schemas with many joins
- Don't forget to test agent responses with sample queries

## Monitoring and maintenance

Establish a regular maintenance schedule:

| Task | Frequency | Priority |
|------|-----------|----------|
| Review query logs | Weekly | High |
| Update data descriptions | Monthly | Medium |
| Test edge case queries | Quarterly | Medium |
| Refresh training data | As needed | High |
