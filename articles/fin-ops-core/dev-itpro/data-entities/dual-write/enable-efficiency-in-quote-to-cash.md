---
title: Enable extra efficiency in quote-to-cash with Dynamics 365 Sales
description: This article describes how to enable extra efficiency in quote-to-cash with Dynamics 365 Sales
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable extra efficiency in quote-to-cash with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.34 GA -->
<!-- KFM: Change "prospect to cash" to "quote to cash" everywhere in Docs? -->

The new features introduced in Dynamics 365 Supply Chain Management with *Add efficiency in Quote to Cash with Dynamics 365 Sales* will only take effect with dual write supply chain  solution  XX.XX.XX. When updating to the new Dual-write Supply chain solution, the update can be disruptive if not done in the proper sequence.  

Below is the recommended and supported sequence of update steps to support that the update and uptake is as least disruptive as possible.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version XX.XX.XX.<!--KFM: Version needed -->
- The features listed as required in the following table must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). You can choose whether or not to turn on the optional features based on your business needs.

    | Feature | Required or optional | Description |
    |---|---|---|
    | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <!--KFM: Status needed --> | This feature changes the way sales quotations in the Dynamics 365 Sales application integrate with sales quotations in Supply Chain management over dual-write. Once enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two applications while applying a policy of ownership to control the available actions for a sales quotation when in either Dynamics 365 Sales or in Supply Chain Management. |
    | *Set default ownership for sales quotations when integrated with Dynamics 365 Sales* | <!--KFM: Status needed --> | This feature is available when the *Integrate sales quotation lifecycle with Dynamics 365 Sales* feature is enabled. This feature adds a setting to the 'Accounts receivables parameters' page, where the default ownership can be set. Default ownership can be set to 'Based on origin', 'Dynamics 365 Sales', or 'Supply Chain Management'. When this feature is disabled, ownership is always based on origin. |
    | *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* | <!--KFM: Status needed --> | When enabled, calculations for extended amounts, summary amounts, subtotals, and totals for sales quotations and sales orders will not be performed in Dynamics 365 Sales. When quotations or sales orders are created in Sales, and a pricelist exists in Sales, then that price will be used, but no other calculations will be made. All calculated monetary fields are calculated in and synchronized from Supply Chain Management. When enabled, this feature sets 'Use system price calculation' to 'No' and 'Discount calculation method' to 'Per unit' in Sales. When enabled, the following changes are made in the Sales user interface for sales quotation and sales order lines: the 'Volume discount' field is hidden, the 'Discount' field is expressed as per-unit discount amount, and the 'Manual discount' field is made read-only and relabeled. Manual discounts can henceforth be entered in the 'Line discount amount' field. |
    | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | <!--KFM: Status needed --> | When integrated to Dynamics 365 Sales, this feature enables to calculate and push line prices, discounts, charges, taxes and totals for a single sales order and sales quotation to Dynamics 365 Sales. A new menu item is introduced on the sales order and sales quotation list and details pages, that when pressed, will enable the calculation and push to Dynamics 365 Sales. The feature also makes available two new forms to complement the existing periodic Calculate sales totals form: Calculate sales order totals for Sales and Calculate sales quotation totals for Sales. Each form will add the ability to specify a range of sales orders or sales quotations to be considered in the calculation. |
    | *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* | <!--KFM: Status needed --> | This feature ensures data consistency between sales orders and related sales quotations in Supply Chain Management when sales orders are created from sales quotations in Dynamics 365 Sales and synchronized over dual-write. As a result, sales orders in the Supply Chain Management will contain the information from the sales quotation in Supply Chain Management. This feature is applicable only when the "Integrate sales quotation lifecycle with Dynamics 365 Sales" feature is enabled. This feature adds a setting on the “Dynamics 365 Sales integration” tab of the “Accounts receivable parameters” page, which lets admins choose whether to copy quotation information on order creation or through the message processor. |
    | *Process Dynamics 365 Sales integration related events* | <!--KFM: Status needed --> | This feature enables Dynamics 365 Sales integration related events to be processed asynchronously using the message processor framework. This can improve performance of sales order and sales quotation integration in various scenarios, such as status transition of a sales quotation when a quotation journal or quotation confirmation journal needs to be created. This feature is applicable only when "Integrate Sales Quotation lifecycle with Dynamics 365 Sales" feature is enabled. |

## Steps <!--KFM: Steps to do what? -->

Once the new dual write supply chain solution has been installed <!--KFM: Add a step for this? --> and associated with a supply chain management instance version 10.0.32 or later <!--KFM: Describe how to do this? -->, then perform the following steps in sequence.

> [!WARNING]
> Dual-write Supply Chain solution version XX.XX.XX <!--KFM: Version needed --> isn't compatible with Supply Chain Management version 10.0.31 or older. Don't upgrade the solution unless you are running Supply Chain Management version 10.0.32 or later.

### Step 1: Apply the entity maps solution

In the dual-write mapping page click Apply solution to import new entity maps. Mapping solution which contains new maps is called "Dynamics 365 Supply Chain Management extended entity maps". When the mapping solution is imported, the page will notify a user that the solution has been applied successfully.

### Step 2: Enable new entity map for feature status

<!--KFM: This section doesn't make any sense to me. Please rewrite as a procedure with specific steps. Add an intro describing what we are doing here. -->

Run new entity map with initial sync enabled where Finance and Operations apps is selected as Master for initial sync:

- Dynamics 365 Sales feature management states

Impact of step #2:

- Status of features in Supply Chain Management is exposed to Dataverse and will be consumed by business logic executed in Dynamics 365 Sales. If the feature *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* is enabled, user interaction for a sales quotation in both Dynamics 365 Sales and Supply Chain Management will be impacted. The nature of the impact  will depend on ownership of the sales quotation. Exposing feature statuses to Dataverse ensures feature status consistency between the two applications.
- Sales order status mapping changes will be in effect (learn more link). <!-- KFM: Link needed. -->

> [!NOTE]
> This step is mandatory. Initial sync is mandatory and this map must always be running to correctly provide the Supply Chain Management feature state to Dynamics 365 Sales. <!-- KFM: Aren't all the steps mandatory? -->

### Step 3: Enable new entity maps for sales orders

Stop entity maps:

- CDS Sales order headers (salesorders)
- CDS Sales order lines (salesorderdetails)

Run new entity maps:

- Dynamics 365 Sales order headers (salesorders)
- Dynamics 365 Sales order lines (salesorderdetails)

Impact of step #2 <!-- KFM: Do you mean step 3? -->: Sales Order status mapping changes will be effective (learn more link). <!-- KFM: Link needed. -->

> [!NOTE]
> When deploying the new dual-write solution for Supply Chain Management, we recommend that you complete both step #2 and step #3, irrespective of up taking the sales quotation lifecycle integration capabilities. 

At this time, you have neither enabled feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales in Supply Chain Management nor are the new table maps for Dynamics 365 Sales quotation header and lines running. CDS Sales quotation header and lines table maps are still running. The behavior of the sales quotation flow between Dynamics 365 Sales and Supply Chain Management is at this point in time unaffected.

When you decide to enable the feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales in Supply Chain management, enable the feature in the following sequence: <!-- KFM: Please provide the sequence. -->

> [!NOTE]
> We recommend that you complete (win or cancel) any existing sales quotations in progress, and then recreate them if needed, after the feature has been enabled for a clean feature cutover. <!-- KFM: What do we mean by "cutover"? If we need to do this first, then we should describe it first. -->

### Step 4: Enable new entity maps for sales quotations

Stop entity maps:

- CDS Sales quotation header (quotes)
- CDS Sales quotation lines (quotedetails)

Run new entity maps:

- Dynamics 365 Sales quotation header (quotes)
- Dynamics 365 Sales quotation lines (quotedetails)

### Step 5: Enable feature

Enable feature *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* in Supply Chain Management Feature Management

You have now enabled the feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales. New sales quotations will fully align with the behaviour described in Learn more.

> [!NOTE]
> All sales quotations created prior to the feature being enabled, will have Dynamics 365 Sales as default origin in Dataverse while the same sales quotations have Supply Chain Management as default origin In Supply Chain Management. This immediate misalignment of origin and resulting ownership, will align upon the first sales quotation header synchronization. Once the first synchronization of a sales quotation header update is done, then the origin value will be aligned. If the first post-uptake synchronization is invoked from an update in Supply Chain Management, then Supply Chain Management will be synched as origin; If the first post-uptake synchronization is invoked from an update in Dynamics 365 Sales, then Dynamics 365 Sales will be synced as origin.

## Configurations not supported for feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales

The following are examples of not supported configurations. The list is not exhaustive, but presents the main not supported configurations:

- Initial sync has not been run for table map Dynamics 365 Sales feature management states
- Feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales is enabled and CDS Sales quotation header and CDS Sales quotation lines maps are running
- Dynamics 365 Sales quotation headers and Dynamics 365 Sales quotation lines maps are running and Feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales is disabled

## Impact on running with unsupported configuration

If you run with an unsupported configuration, you risk of not being able to create and process any sales quotations from Dynamics 365 Sales or Supply Chain Management. To enable the creation and processing of sales quotations, you must correct the configuration.

Following is a high level flowchart illustration illustration of various uptake permutations and the outcomes. Please note that the flowchart illustration is high level  and as such not exhaustive. It should be used as an overview only.  

![How-to-visio-flow](../dual-write/media/add_effciency_18.png)

## Troubleshooting

If the sales quotation lifecycle flow does not yield the expected results for newly created sales quotation and the feature Integrate Sales Quotation lifecycle with Dynamics 365 Sales is enabled, do the following:

Do Initial Sync (from FnO) for table map:

- Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)

Check that following maps are running:

- Dynamics 365 Sales order headers (salesorders) Replaces CDS Sales order headers (salesorders)
- Dynamics 365 Sales order lines (salesorderdetails) Replaces CDS Sales order lines (salesorderdetails)
- Dynamics 365 Sales quotation header (quotes) Replaces CDS Sales quotation header (quotes)
- Dynamics 365 Sales quotation lines (quotedetails) Replaces CDS Sales quotation lines (quotedetails)

Check that these table maps have been stopped:

- CDS Sales order headers (salesorders)
- CDS Sales order lines (salesorderdetails)
- CDS Sales quotation header (quotes)
- CDS Sales quotation lines (quotedetails)
