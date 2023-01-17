---
title: Preview of Dynamics 365 Supply Chain Management 10.0.32 (March 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.32. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.32 (March 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.32. This version has a build number of 10.0.1406 <!-- KFM: Get new build number -->and is available on the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** March 2023
- **General availability of release (auto-update):** April 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Product information management | Share product information across legal entity boundaries <!-- KFM: List this now, or wait until real public preview? --> | <!-- KFM: Add link to new topic --> | Feature management:<br>*(Preview) Cross-company data sharing for products* |
| Warehouse management | Pack shipments with speed and resilience | <!-- KFM: Add links to new and updated topics --> |  |
| Warehouse management | Run the Warehouse Management mobile app on iOS devices | <!-- KFM: Any info available? --> | <!-- KFM: Any FM needed? --> |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Procurement and sourcing | Request for quotation amendment and cancellation email framework options | This feature gives you the option to send a RFQ amendment and RFQ cancellation emails using either SSRS report or email distributor framework. This feature adds new settings to both the "Amendment" and "Cancelation" group of fields of the "Request for quotation" tab in the Procurement and sourcing parameters. When this feature is enabled, the new "Send email using" options become available and can be used for determining the preferred way of sending emails. SSRS report is the default value. Selecting the SSRS report option means that an email is sent as part of generating the report using the SSRS report. This option should be used if only a few email recipients should receive the email or if the report should be delivered as an attachment to the email. Selecting the Email distributor option means that an email is sent using the email distributor framework. With the email distributor option, the email can be monitored in the Batch email sending status. This option should be used when emails are sent to many recipients. When using the email distributor option, the report cannot be sent as an attachment. Without this feature, the system always sends email using the rendering of the SSRS report. |
| Procurement and sourcing | Purchase order workflow submission and approval performance enhancement | <!-- KFM: in FM, this feature is both on by default and showing a preview banner (Missing "(Preview)"?). What is going on? Is this even new? Ask Smitha --> This feature improves the performance of the purchase order workflow submission dialog and approval dialog which is most noticeable on purchase orders with larger number of lines. When this feature is enabled, purchase order totals and accounting distributions are calculated and validated by a workflow execution. Validation errors surface in the workflow history. Please note that this feature is not supported with budget control enabled. |
| Master planning | Forecast demand plan import service. <!-- KFM: Missing "(Preview)". Period in feature name. --> | Allows multiple threads for importing forecast demand plan lines. |
| Production control | Production batch balancing enhanced onhand grid capability |  Provides an enhanced on-hand grid capability for the batch balancing process. <!-- KFM: More detail would be nice. Doc needed? On-hand what, inventory? --> |
| Sales and marketing | (Preview) Integrate Sales Quotation lifecycle with Dynamics 365 Sales | This feature changes the manner in which sales quotations in the Dynamics 365 Sales application integrate with sales quotations in Supply Chain management over dual write. Once enabled, state and status transition throughout the lifecycle of a sales quotation is mapped between the two applications while applying a policy of ownership to control the available actions for a sales quotation when in either Dynamics 365 Sales or in Supply Chain Management. <!-- KFM: documentation needed? --> |
| Sales and marketing | (Preview) Process Dynamics 365 Sales integration related events | Enables Dynamics 365 Sales integration related events to be processed asynchronously using the message processor framework. This can improve performance of sales order and sales quotation integration in various scenarios, such as status transition of a sales quotation when a quotation journal or quotation confirmation journal needs to be created. This feature is applicable only when the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled. <!-- KFM: documentation needed? --> |
| Sales and marketing | Prevent updates to intercompany sales order line requested dates in header to lines update scenario when derived. | This feature prevents updating intercompany sales order line requested dates in a header to lines scenario when the intercompany sales order line is created from the purchase order and therefore is derived. Previously, when updating either confirmed or requested dates on the intercompany sales order header, both requested and confirmed sales order line dates would be updated when Transfer settings from the header to the lines ship and receipt dates, update ship and receipt dates, is *Yes*. When this feature is enabled, only the sales order line confirmed dates are updated in such a header to lines update scenario. |
| Sales and marketing | (Preview) Pricing management | <!-- KFM: Description is missing in FM. Is this really being made available as public preview in 10.0.32? --> |
| Sales and marketing | Operational reporting of Sales invoice and packing slip | Operational reporting of Sales Invoice and packing slip <!-- KFM: Description is missing in FM. "(Preview)" is missing in feature name.  Documentation needed? Part of Pricing management? --> |
| Sales and marketing | (Preview) Sequence and compound for customer charges | Enables the new charge concepts of sequence, compound, and specific unit of measure for customer charges. The feature supports setting up and working with these concepts on auto charges. They provide the capability of defining the order in which header level charges are calculated and which invoice amounts are taken into account when calculating the value upon which a header level charge is calculated. <!-- KFM: documentation needed? Part of Pricing management? --> |
| Sales and marketing | (Preview) Unit of measure for line level charges | This feature gives you the option of specifying a unit of measure (UoM) for which a line-level auto charge applies. You can set up an auto charge for customer and vendor so that it only applies to lines that use the exact UoM configured for the charge, or you could choose to allow the charge to apply proportionally based on an applicable UoM conversion factor (if one exists). This feature supports customer and vendor line-level charges and applies for sales quotation and sales order lines, request for quotation, purchase requisition, and purchase order lines. <!-- KFM: documentation needed? Part of Pricing management? --> |
| Transportation management | (Preview) Performance improvements for post receipt function in Landed Cost | Improves performance of the Landed cost module by reducing the amount of information queried and updated when posting a product receipt for a large purchase order in Landed cost. |
| Transportation management | (Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages | Allocate costs on a more granular basis by breaking down costs from each voyage according to the cost type code. As a result, the invoice journal can include lines where each line represents a specific cost type code. <!-- KFM: FM description has many errors. Consider replacing with this one. Really coming in 10.0.31? Documentation needed? -->  |
| Transportation management | (Preview) Enable shipping container creation and update in batch mode | Use batch processing to perform container operations on large numbers of purchase order lines included within a voyage. Batch processing allows you to apply many operations at once without experiencing long delays or timeouts on the front end. Users can add purchase order lines to new or existing shipping containers and then choose to apply the changes in batch mode, which allows the system to process the updates in the background. However, background processing won't activate when the transfer quantity is less than the total quantity of the related purchase order line. <!-- KFM: Really coming in 10.0.31? Documentation needed? --> |
| Transportation management | (Preview)Assign shipments to related route segments | Enables the system to apportion shipment freight costs more accurately, including for loads with multiple shipments delivered to various segment destinations along a single route. It assigns each shipment to the most suitable route segment based on the destination addresses of the shipment and segment. The feature then calculates each shipment's freight cost as a proportion of the load's total freight cost, based on the shipment's relative weight, volume, quantity and distance traveled. This feature only applies to shipments managed using the Transportation management (TMS) module. <!-- KFM: Really coming in 10.0.31? Documentation needed? -- |
| Warehouse management | Reverse match feature | <!-- KFM: Description is missing in FM. --> |
| Warehouse management | Warehouse-specific inventory transactions | Helps optimize the performance of warehouse management processes, especially when processing a large number of SKUs. It also prepares the Supply Chain Management database to support future improvements. The feature adds a new database table that stores inventory transactions specifically for warehouse management processes, which then use this table to drive on-hand inventory changes rather than using the common inventory transaction table (InventTrans). As a result, this feature significantly reduces the load on the InventTrans table, thereby also improving the performance of many other system processes. <!-- KFM: "(Preview)" is missing in feature name. -->

## Feature state changes in this release

The following table lists features that became mandatory or on by default in version 10.0.32. All these features will automatically be turned on for your system as soon as you update to version 10.0.32. Mandatory features can't be turned off, but features that are on by default can still be turned off by using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Features that are now listed as enabled by default are targeted to become mandatory with 2023 release wave 2.

The table also lists features that were previously in public preview but have changed to become generally available in version 10.0.32. This change indicates that the features are now recommended for use in production environments. These features are turned off by default unless otherwise noted. Therefore, you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them. Features that are now listed as generally available are targeted to become enabled by default with 2023 release wave 2 and then to become mandatory with 2024 release wave 1.

| Module | Feature name | New feature state |
| --- | --- | --- |
| Asset management | [Apply rules for grouping work orders while running a maintenance plan](../asset-management/preventive-and-reactive-maintenance/creating-work-orders.md) | On by default <!-- KFM: UI says mandatory --> |
| Asset management | [Counter-based maintenance enhancements](../asset-management/preventive-and-reactive-maintenance/maintenance-plans.md) | On by default |
| Asset management | [Offset accounts for expenses in work order journals](whats-new-scm-10-0-23.md) | On by default |
| Asset management | [Work order billing](../asset-management/integration-to-project-management-and-accounting/customer-billing.md) | On by default <!-- KFM: UI says mandatory --> |
| Cost management | [Inventory aging report storage](../cost-management/inventory-aging-report-storage.md) | On by default |
| Cost management | [Post on-hand adjustments using configurable reason codes connected to offset accounts](../warehousing/reason-codes-for-counting-journals.md) | On by default |
| Cost management | Enable error execution log for cost accounting overhead calculation | Generally available <!-- KFM: zero documentation --> |
| Inventory management | [Inventory on-hand report data clean up](whats-new-scm-10-0-28.md) | On by default |
| Production control | [Enable to enter batch and serial numbers while reporting as finished from the Job Card Device](../production-control/report-finished-job-device.md) | Mandatory |
| Production control | Improved production catch weight quantity picking | Mandatory <!-- KFM: zero documentation --> |
| Production control | [Manufacturing execution system integration](../production-control/mes-integration.md) | Mandatory |
| Production control | ["My day" view for the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [On-demand material availability check for production orders](whats-new-scm-10-0-24.md) | Mandatory |
| Production control | [Report on co- and by-products from the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [Report on planning items in the production floor execution interface](whats-new-scm-10-0-27.md) | Mandatory |
| Production control | [Validate expiration of raw materials against planned consumption date](whats-new-scm-10-0-23.md) | Mandatory |
| Production control | [Auto-picking of warehouse enabled materials for auto-posted picking lists](whats-new-scm-10-0-23.md)  | On by default |
| Production control | [Copy generic routes](whats-new-scm-10-0-20.md) | On by default |
| Production control | [My jobs tab on the production floor execution interface](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [Production teams in the production floor execution interface](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [Register material consumption on the production floor execution interface (non-WMS)](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [Update related resource requirements when a route operation is changed](whats-new-scm-10-0-20.md) | On by default |
| Master planning | Batchable firming and consolidation for planned bulk and pack batch orders | Mandatory |
| Master planning | Include items with on-hand when pre-processing filters are enabled | Mandatory |
| Master planning | Planned orders simplified | Mandatory |
| Master planning | Azure Machine Learning Service for demand forecasting | On by default |
| Master planning | Make-to-order supply automation | On by default |
| Master planning | Priority driven MRP support for Planning Optimization | On by default |
| Master planning | Group transactions in Planning Optimization | On by default |
| Master planning | CTP for Planning Optimization | Generally available |
| Master planning | Source products and materials from multiple vendors using Planning Optimization | Generally available |
| Master planning | Consider inventory lead time when creating a planned transfer order | Generally available |
| Procurement and sourcing | Add lines to PO invoices associated with a purchase agreement | Mandatory |
| Procurement and sourcing | Allow vendors to apply for procurement categories through vendor collaboration | Mandatory |
| Procurement and sourcing | Bid submission success message | Mandatory |
| Procurement and sourcing | Clean up purchase-order update history | Mandatory |
| Procurement and sourcing | Disable Purchase Requisition Distribution Reset Button | Mandatory |
| Procurement and sourcing | Purchasing cXML enhancements | Mandatory |
| Procurement and sourcing | RFQ questions and answers | Mandatory |
| Procurement and sourcing | RFQ reference link added to PO | Mandatory |
| Procurement and sourcing | Check unit precision for not-stocked items | On by default |
| Procurement and sourcing | Default broker contract tax information on vendor invoice lines | On by default |
| Procurement and sourcing | Enable vendor collaboration certification management | On by default |
| Procurement and sourcing | Maintain vendor bank information using vendor collaboration workspace | On by default |
| Procurement and sourcing | Post registered quantities of stocked products and remainders of not-stocked products for receipts and vendor invoices | On by default |
| Procurement and sourcing | Purchase agreement matching policy | On by default |
| Procurement and sourcing | Purchase order delivery date | On by default |
| Procurement and sourcing | Purchasing card processing | On by default |
| Procurement and sourcing | Put vendor on hold for purchase orders | On by default |
| Procurement and sourcing | Sealed bidding for RFQs | On by default |
| Procurement and sourcing | Synchronize tracking dimensions on intercompany sales and purchase order lines: | On by default |
| Procurement and sourcing | Limit the number of purchase order lines per batch task | Generally available |
| Procurement and sourcing | Request for quotation amendment and cancellation email framework options | Generally available |
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
| Rebate management | Rebate Management | On by default |
| Rebate management | Cancel posted rebate provision with a posting date | Generally available |
| Rebate management | Credit note calculation enhancement in Rebate management | Generally available |
| Rebate management | Enable auto negative tier in Rebate management | Generally available |
| Rebate management | Write-off before rebate claim | Generally available |
| Sales and marketing | Limit the number of sales order lines per batch task | Mandatory |
| Sales and marketing | Update Requested receipt date with Confirmed date for intercompany orders | Mandatory |
| Sales and marketing | Calculate sales totals using multiple threads | On by default |
| Sales and marketing | Update prices and discounts entered manually for intercompany | On by default |
| Transportation management | Goods in Transit Receiving and Put away | Mandatory |
| Warehouse management | Cross-docking templates with location directives | Mandatory |
| Warehouse management | Deferred put - container | Mandatory |
| Warehouse management | Disable expected receipts from quality orders that sample blocked inventory | Mandatory |
| Warehouse management | License plate receiving history | Mandatory |
| Warehouse management | Manual shipment consolidation | Mandatory |
| Warehouse management | Maximum execution time for the warehouse management on-hand entries cleanup job | Mandatory |
| Warehouse management | Validate templates selected for replenishment jobs | Mandatory |
| Warehouse management | Use faster API for containers closing/reopening on packing station | Mandatory |
| Warehouse management | Allow editing of physical dimension for a released product and its handling unit | On by default |
| Warehouse management | Auto update shipment | On by default |
| Warehouse management | Change the error to a warning when releasing a load where sufficient quantity isn't available | On by default |
| Warehouse management | Enhanced parser for GS1 barcodes | On by default |
| Warehouse management | Evaluate work header breaks before work header maximums during work creation | On by default |
| Warehouse management | Include Confirmed ship and Confirmed receipt dates into date filters on Load planning workbench | On by default |
| Warehouse management | Item consolidation location utilization | On by default |
| Warehouse management | License plate receiving enhancements | On by default |
| Warehouse management | License plate validation on source document lines | On by default |
| Warehouse management | Line reservation enhancements for the batch number reserv | On by default |ation form feature | On by default |
| Warehouse management | Location directive inventory picking aging
| Warehouse management | Manual transfer line picking service for admin or similar trusted users | On by default |
| Warehouse management | New load planning workbench pages: Enables two new load planning workbench pages | On by default |
| Warehouse management | Organization wide wave step code | On by default |
| Warehouse management | Organization-wide "Schedule work creation" wave method | On by default |
| Warehouse management | Organization-wide system directed work sequencing | On by default |
| Warehouse management | Outbound sorting | On by default |
| Warehouse management | Over receipt of load quantities | On by default |
| Warehouse management | Packaging product dimensions | On by default |
| Warehouse management | Packing work for packing stations | On by default |
| Warehouse management | Parent license plates cannot be target license plates | On by default |
| Warehouse management | Pick line grouping | On by default |
| Warehouse management | Purchase order quantity left to load calculation using registered quantities | On by default |
| Warehouse management | Quality Management For Warehouse Processes. | On by default |
| Warehouse management | Replenishment over location capacity | On by default |
| Warehouse management | Sales order packing slip corrections/cancellation transaction status change | On by default |
| Warehouse management | Scale unit support for warehouse app work lists | On by default |
| Warehouse management | Scan GS1 barcodes | On by default |
| Warehouse management | Schedule work creation | On by default |
| Warehouse management | System directed cluster picking | On by default |
| Warehouse management | System directed work sequencing | On by default |
| Warehouse management | Warehouse management app data inquiry flow | On by default |
| Warehouse management | Warehouse management application - blank GTD | On by default |
| Warehouse management | Warehouse release rule | On by default |
| Warehouse management | Wave Load building feature | On by default |
| Warehouse management | Wave step code | On by default |
| Warehouse management | Work policy enhancements for inbound work | On by default |
| Warehouse management | Work split | On by default |
| Warehouse management | Options for updating the mode of delivery for sales order lines when creating loads | Generally available |
| Warehouse management | Options for validating ingredient batch expiration dates | Generally available |
| Warehouse management | Reverse match feature | Generally available |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of Finance and Operations apps (March 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-32.md) <!-- KFM: Confirm link -->.

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.32, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525) <!-- KFM: Get new KB link -->.

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/) <!-- KFM: Update to 2023w1 -->. We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]