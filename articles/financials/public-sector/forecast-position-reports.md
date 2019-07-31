# Forecast position reports for the public sector

You can use the **Forecast position summary** and **Forecast position detail** reports to generate forecast position information for during a budget plan and scenario that you specify.  

The **Forecast position summary** report shows forecast position costs by account distributions. The forecast position costs are shown, grouped by their assigned account distributions. The cost amounts are factored by the percentage assigned to the account distribution. 

The **Forecast position details** report contains most of the information displayed on the forecast position form. The account distributions assigned to the forecast position via financial dimensions and financial dimension templates are shown, along with the costs associated with each distribution combination for the forecast position. 

To view more information about a Forecast position, select the Position number to open the Forecast position page.

## Filter the data on this report

When you generate the report, the following default parameters are shown.  You can use these parameters to filter the data that appears on the report.  

| Field | Description |
| --------- | ------- |
| Financial dimension set | Select the dimension group for the ledger accounts that should be listed on the report.<p>A financial dimension set is a named group of accounts or dimensions that contains either account values for the account or dimension values for a single dimension. For example, a set can include main accounts, departments, and cost centers. Alternatively, it can contain combinations, such as a cost center and a main account, or a department and a cost center. For more information, see [Create a financial dimension set](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/create-a-financial-dimension-set).</p> |
| Budget planning process | Select the budget planning process that should be listed on the report.<p> Budget planning processes determine how budget plans can be updated, routed, reviewed, and approved in the budgeting organization hierarchy. A budget planning process is linked to a budget cycle and an organization via a legal entity.</p> |
| Budget plan scenario | Select the budget plan scenario that should be listed on the report. <p> Budget plan scenarios define categories of data for the budget plans. You define budget plan scenarios to support monetary and other unit of measure classes, such as quantity. Examples of monetary budget plan scenarios include Department previous year and Department requests. Examples of budget plan scenarios that use quantities include Previous year support calls and Full-time equivalent (FTE) count. </p> |
| Unfilled only | Set this option to "Yes" to exclude positions that are currently filled. |
| Suppress total | Set this option to "Yes" to exclude totals from appearing on the report. |
| Range of Dimensions | Select the financial dimension you would like to filter on the report.  This will include the dimensions selected in the Financial dimension set field. |

## Review the report:

The Forecast position summary report includes the following information:

Header:
- Budget plan scenario
- Budget planning process
- Position count
- Grand total

Body:
- Financial dimension set
- Position
- Description
- Job
- Assigned worker
- FTE
- Compensation group
- Level
- Step
- Rate/Hourly
- Allocation
- Earnings
- Benefits
- Taxes
- Others
- Total


The Forecast position detail report includes the following information:

- Position
- Description
- Job
- Division
- Title
- Position type
- Forecast state
- Assigned worker
- Legal entity
- Budget planning process
- Budget plan scenario
- FTE
- Activation
- Retirement
- Compensation group
- Compensation level
- Compensation step
- Rate
- Hourly rate
- Anniversary date
- Scheduled increase date
- Accounting Distributions
- Percentage 
- Financial dimensions
- Costs
- Earnings
- Benefits
- Tax 
- Other
- Total
- Budget cost elements
- Cost type
- Main account
- Start date
- End date
- Percent
- Annual amount
- Budget amount
