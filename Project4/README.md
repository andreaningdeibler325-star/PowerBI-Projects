**SLA Compliance Rate**

```dax
SLA Compliance Rate =
DIVIDE(
    [SLA Met Tickets],
    [SLA Met Tickets] + [SLA Breached Tickets]
)
```

**Average Customer Satisfaction**

```dax
Average Satisfaction =
AVERAGE('Support Tickets'[Customer Satisfaction])
```

## Key Analytical Findings

### Ticket Distribution

| Issue Category | Tickets | Percentage |
|---|---:|---:|
| Technical | 303 | 30.3% |
| Billing | 270 | 27.0% |
| Product | 146 | 14.6% |
| Account | 145 | 14.5% |
| Shipping | 136 | 13.6% |
| **Total** | **1,000** | **100.0%** |

- Technical and Billing issues account for 57.3% of all support tickets.
- Medium-priority tickets represent the largest priority group at 39.6%.
- High and Critical priority tickets collectively represent 37.9% of all tickets.
- Email is the most frequently used communication channel, accounting for 34.0% of ticket submissions.

### Service & SLA Performance

| Issue Category | SLA Compliance Rate |
|---|---:|
| Account | 81.38% |
| Technical | 78.55% |
| Shipping | 77.21% |
| Billing | 77.04% |
| Product | 74.66% |
| **Overall** | **77.80%** |

- All 1,000 support tickets were resolved.
- 778 tickets met SLA requirements.
- 222 tickets breached SLA requirements.
- Account issues achieved the highest SLA compliance rate.
- Product issues achieved the lowest SLA compliance rate.
- Higher-priority tickets were resolved faster on average.

### Agent Performance

The report enables comparative analysis of 15 support agents across four operational dimensions:

- Ticket workload
- Average resolution time
- SLA compliance
- Customer satisfaction

Agent performance comparisons should consider differences in ticket priority, complexity, and workload.

## Technical Challenge and Resolution

During report development, a DAX data type conversion error occurred when calculating monthly SLA compliance rates.

The root cause was the use of FORMAT() in the Total Tickets measure, which converted numeric results into text. Empty strings encountered under certain filter contexts caused subsequent numeric calculations to fail.

The solution involved:

- Removing unnecessary FORMAT() calls from numeric measures.
- Maintaining numeric data types throughout dependent calculations.
- Using Power BI Measure tools for presentation formatting.
- Using COALESCE() to replace blank values with zero where appropriate.
- Using DIVIDE() to safely handle zero denominators.

This experience reinforced an important Business Intelligence development principle:

**Separate calculation logic from presentation formatting.**

## Data Validation

- Issue category counts reconcile to 1,000 tickets.
- Priority counts reconcile to 1,000 tickets.
- Communication channel counts reconcile to 1,000 tickets.
- Resolved and unresolved tickets reconcile to the total ticket count.
- SLA Met and SLA Breached counts reconcile to 1,000 evaluated tickets.
- Monthly reporting follows chronological year and month-number sorting.

## Tools and Technical Skills

- Microsoft Power BI Desktop
- Microsoft Excel
- Power Query and M language
- Data extraction, transformation, and loading (ETL)
- Data type management
- Relational data modeling
- Calendar dimension development
- Active and inactive relationships
- DAX measures and filter context
- DAX measure dependencies
- DAX debugging
- KPI development
- IT Service Management analytics
- SLA compliance analysis
- Interactive dashboard development
- Data validation and analytical storytelling

## Analytical Limitations

- Specific SLA thresholds have not been independently verified.
- Agent comparisons are not adjusted for ticket complexity or priority.
- Ticket creation volumes do not necessarily represent ticket resolution volumes within the same reporting period.
- Associations between operational metrics do not establish causation.
- The original Excel workbook may be required to refresh the report.

## Future Enhancements

- Develop a corresponding Tableau dashboard using the same dataset.
- Integrate support ticket data with SQL Server.
- Implement automated cloud-based data refresh.
- Develop additional resolution-date and backlog analyses.
- Explore predictive analytics for identifying potential SLA breaches using Python and machine learning.
- Explore AI-powered customer support analytics and intelligent ticket classification.

## Project Status

**Power BI report development completed — November 27, 2026.**

Project 4 of my professional Power BI analytics portfolio.

**Practice makes perfect. Continuous learning leads to professional excellence.**

*Übung macht den Meister!*
