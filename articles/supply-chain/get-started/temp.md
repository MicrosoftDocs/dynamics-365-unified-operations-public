| Asset management | Apply rules for grouping work orders while running a maintenance plan | On by default |
| Asset management | Counter-based maintenance enhancements | On by default |
| Asset management | Offset accounts for expenses in work order journals | On by default |
| Asset management | Work order billing | On by default |
| Manufacturing | Enable to enter batch and serial numbers while reporting as finished from the Job Card Device | Mandatory |
| Manufacturing | Improved production catch weight quantity picking | Mandatory |
| Manufacturing | Manufacturing execution system integration | Mandatory |
| Manufacturing | "My day" view for the production floor execution interface | Mandatory |
| Manufacturing | On-demand material availability check for production orders | Mandatory |
| Manufacturing | Report on co- and by-products from the production floor execution interface | Mandatory |
| Manufacturing | Report on planning items in the production floor execution interface | Mandatory |
| Manufacturing | Validate expiration of raw materials against planned consumption date | Mandatory |
| Manufacturing | Auto-picking of warehouse enabled materials for auto-posted picking lists | On by default |
| Manufacturing | Copy generic routes | On by default |
| Manufacturing | My jobs tab on the production floor execution interface | On by default |
| Manufacturing | Production teams in the production floor execution interface | On by default |
| Manufacturing | Register material consumption on the production floor execution interface (non-WMS) | On by default |
| Manufacturing | Update related resource requirements when a route operation is changed | On by default |
| Master planning | Batchable firming and consolidation for planned bulk and pack batch orders | Mandatory |
| Master planning | Include items with on-hand when pre-processing filters are enabled | Mandatory |
| Master planning | Planned orders simplified | Mandatory |
| Master planning | Azure Machine Learning Service for demand forecasting | On by default |
| Master planning | Make-to-order supply automation | On by default |
| Master planning | Priority driven MRP support for Planning Optimization | On by default |
| Master planning | Consider inventory lead time when creating a planned transfer order | Generally available |
| Product information management | Country of origin management feature | Mandatory |
| Product information management | Enable change management on existing products | Mandatory |
| Product information management | Engineering notifications for production | Mandatory |
| Product information management | Improved attribute inheritance for Engineering Change Management | Mandatory |
| Product information management | Product readiness checks | Mandatory |
| Product information management | Variant generation for engineering products | Mandatory |
| Product information management | Clean up product attribute values | On by default |
| Product information management | Engineering Change Management | On by default |
| Product information management | Manage changes to formulas and their ingredients | On by default |
| Product information management | Populate product attribute values | On by default |







Inventory and logistics feature state updates for 10.0.32
Enabled for	Public preview	General availability
End users by admins, makers, or analysts	Jan 2023	Apr 2023
Business value
Turning on features by default helps ensure that your system stays current with the latest inventory and logistics capabilities of Dynamics 365 Supply Chain Management.
Feature details
Features becoming mandatory with the 10.0.32 release
These features are now mandatory and can no longer be disabled.

Sales and marketing

Limit the number of sales order lines per batch task: Helps you optimize system performance when posting confirmations, picking lists, packing slips, and invoices by limiting the number of order lines processed by each batch task.
Update Requested receipt date with Confirmed date for intercompany orders: Lets you control what will happen to sales and purchase date field values within intercompany direct delivery scenarios.
Transportation management

Goods in Transit Receiving and Put away: Allows the goods-in-transit item receiving and putaway processes to receive goods using the legacy codes instead of the process guide framework.
Features becoming enabled by default with the 10.0.32 release
These features are now turned on by default but can still be disabled manually. These are all targeted to become mandatory with 2023 release wave 1.

Cost Management

Inventory aging report storage
Post on-hand adjustments using configurable reason codes connected to offset accounts
Inventory Management

Inventory on-hand report data clean up: Provides a way to clean up the data that is used to create inventory on-hand report storage reports.
Rebate Management

Rebate management
Sales and marketing

Calculate sales totals using multiple threads: Helps improve system performance by using parallel processing when calculating sales totals in batch.
Update prices and discounts entered manually for intercompany: Enables manual change policy functionality for intercompany commerce. It includes the ability to transfer manual change policies between intercompany sales and purchase orders. Previously, this functionality was only available for non-intercompany orders. Now, the Update price and discounts dialog option will be displayed after making changes to an intercompany order. This dialog option lets users choose whether to update or keep prices and discounts details on each intercompany order.
Features becoming generally available with the 10.0.32 release
These features are now generally available. They are not turned on by default and must be enabled manually. Some features can be disabled again after being turned on, and these are targeted to become enabled by default with 2023 release wave 2. All of these features are targeted to become mandatory with 2024 release wave 1.

Cost Management

Enable error execution log for cost accounting overhead calculation: Enables the logging of error messages when journal creation fails while the system is calculating overhead.
Rebate Management

Cancel posted rebate provision with a posting date: Cancel a posted rebate provision with a specified posting date and reverse the original transactions and documents. Rebate provision transactions already posted before this feature was enabled can only be reversed by generating opposite provision transactions with a specific date and the current deal setup. Once this feature is enabled, newly posted rebate provision transactions can be fully reversed with a specific date regardless of current deal setup.
Credit note calculation enhancement in Rebate management: Enables you to Include credit note in the rebate management deal line. The rebate management line will check both the sales order and credit note to consider the rebate value/quantity condition and calculate accordingly during the batch job process or process at posting of provision (based on the configuration). If the credit note is matched with a sales order line, the price details will include the original sales transaction.
Enable auto negative tier in Rebate management: Enables the negative tier to be set up automatically for each deal line. The system will then calculate rebates automatically as needed.
Write-off before rebate claim: In some cases, you can expect part of the provision amount will never be claimed back. This feature enables you to process rebate write-offs before you process the rebate management. The system will calculate the balance between the posted provision and the posted write-off during the period and then propose the rebate management amount for you to process.