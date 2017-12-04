---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition 7.3
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3. This version was released in December 2017.
author: tonyafehr
manager: AnnBe
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tfehr
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: 7.3 update 
---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition 7.3

[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3. This version was released in December 2017.

To learn more about the new features and changes in all of the latest product releases, see [What’s new or changed](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed) and [What's new or changed in Dynamics 365 for Retail](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new).

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. 

Demand forecast entries data entity enabled for Data management framework
-------------------------------------------------------------------------

Data management framework (DMF) is now enabled for the **Demand forecast
entries** data entity (ForecastDemandForecastEntryEntity), which makes it
possible to integrate with third-party systems.

In addition, each demand forecast entry is uniquely identified by a sequence
number (entity field ForecastEntryNumber). For all integrations consider this
unique identifier, even if it doesn’t exist in the source or third-party system.

## Demo data in data packages 
Demo data has been delivered in prior releases as a database with a large number of companies. In addition to that database, we also create data packages using the demo data companies so that you can load your demo data on an empty environment using the data management framework. These data packages will be delivered, for a specific release, as assets in the global shared assets library in Lifecycle Services (LCS). Instructions for loading the data packages will also be provided. 

The data packages are similar but not identical to existing demo companies and may change over time. The packages are very small and provide a quick way to download the demo data and modify it before you import it into an environment. We will continue to add additional demo data for more companies and module functionality in the future.

Enhanced integration of Prospect to cash between Dynamics 365 for Sales and Dynamics 365 for Finance and Operations
-------------------------------------------------------------------------------------------------------------------

Enhancements to Prospect to cash integration between Dynamics 365 for Sales and
Dynamics 365 for Finance and Operations, Enterprise edition enable direct
synchronization in the following processes:

-   Maintain accounts in Sales and sync them to Finance and Operations as
    customers.

-   Maintain contacts in Sales and sync them to Finance and Operations as either
    customers or contacts for a customer.

-   Maintain products in Finance and Operations and sync them to Sales.

-   Create quotes in Sales and sync them to Finance and Operations.

-   Generate sales orders in Sales for existing products and sync them to
    Finance and Operations.

-   Generate, modify, and fulfill sales orders in Finance and Operations and
    sync changes to Sales.

-   Generate invoices in Finance and Operations and sync them to Sales.

Highlights of these integration enhancements include:

-   Support data entity overwrite of numbers for quotes, sales orders, and
    invoices (no need to set number sequence to manual).

-   Conversion of quote, sales, or invoice line discount from per unit to per
    line.

-   Support for sync of tax related charges from Finance and Operations to
    Sales, such as freight tax.

-   Additional functionality to support sales order sync from Sales to Finance
    and Operations.

-   Additional functionality to support sales order sync from Finance and
    Operations to Sales.

-   Sync support for country/region ISO codes on invoice address, exposed on
    data entities.

## Expense management mobile workspace enhancements
This feature provides support for functionality that is available in expense management that was not available in the mobile solution for expense management. This list includes (but is not limited to):

-  Support for mileage expenses.
-  Support for intercompany expenses.
-  Support for per diem expenses.

For more information, see [Expense management mobile workspace](https://docs.microsoft.com/en-us/dynamics365/operations/financials/expense-management/expense-management-mobile-workspace). 

## Financial reporting using Power BI
A set of default reports built using a new visualization using Power BI is available for financial reporting. The new financial reporting experience will be embedded within Finance and Operations, giving you a seamless experience of report generation and allowing you to drill into supporting documents. Limited subledger data will be available to provide better ledger to subledger analysis. Default reports, such as a trial balance, balance sheet, and profit and loss, will be shipped out of the box, however, initially no edits will be allowed using Finance and Operations. Edits need to be made using the Power BI desktop. The existing financial reporting using Report Designer is still available and fully supported.

To view additional information about Financial reporting using Power BI, watch the following video: [Reporting for Dynamics 365 for Finance and Operations](https://youtu.be/9m5ys9UmaVg).

## Fixed asset roll forward report
The new **Fixed assets roll** forward report provides you with the detailed fixed asset data needed for period closing, financial statements, and tax reporting in an easy-to-read Excel format. The report, which utilizes the GER framework, shows fixed asset financial details for a specific period. Comprehensive data includes individual asset starting and ending balances along with valuation movements for the period, in addition to any new asset acquisitions and disposals that occurred in the specified timeframe. Totals are provided for the fixed asset group and legal entity.  

Inventory transactions logging (InventSumLogTTS) optimization  
---------------------------------------------------------------

Inventory transactions logging (InventSumLogTTS) is now turned on for all items
and the old records in the log are automatically removed.

These changes prevent records from being inserted into the **Inventory
transactions log** table (InventSumLogTTS) in certain conditions. This prevents
the table from getting too large and causing performance issues.

When planning processes are enabled in a company, which means that **Master
planning** \> **Setup** \> **Master planning parameters** \> **Disable all
planning processes** is set to **No**, inventory transactions logging
(InventSumLogTTS) is not turned on in the following cases:

-   The warehouse on the transaction has the **Manual replenishment** setup.

-   The coverage code for the item and its product dimensions is **Manual**.

-   The transaction is related to **Blocking inventory statuses**.

The item is disabled for planning via the **Product lifecycle state** parameter
on the item master.

When planning processes are disabled in a company, which means that **Master
planning** \> **Setup** \> **Master planning parameters** \> **Disable all
planning processes** is set to **Yes**, inventory transactions logging is never
turned on.

The **Inventory transactions log** table will be periodically cleaned up to
remove all records that are older than 90 days. The cleanup is triggered
automatically by regenerating the master plan.

Master and reference data entities for warehouse and transportation management  
--------------------------------------------------------------------------------

Data entity support is now enabled for setup data in the supply chain management
area. For the warehouse and transportation areas, enhancements have been made to
the default configuration templates. The default configuration templates provide
the entities and sequencing that are required to copy configuration data from
one instance to another instance in a single step.

## Notifications in Point of Sale
In today's modern retail environment, the store associates are assigned various tasks such as helping customers, running transactions, performing stock counts, or receiving orders in the store. Point of Sale (POS) client empowers the associates to do these and much more, all in one application. With various tasks to be performed in a day, there is a need to notify the associates when a task requires their attention. To address this requirement, we have created a notification framework that utilizes the notification capability in POS. For this release, the notifications can be enabled for POS operations only, and out of the box, the notifications can only be enabled for the order fulfillment operation. However, the notification framework is extensible and enables developers to easily plug in custom code for any operation. We have also provided the ability to configure role-based notifications that empower the retailers to easily define who should receive what notifications.

Optimization advisor   
-----------------------

The Optimization advisor workspace helps business users follow best practices to
optimize the business processes that they own. It analyzes business processes,
finds optimization opportunities, leverages application data to quantify the
opportunities, and then recommends solutions that can help improve both the
effectiveness towards the business goal and the performance of the application.

With Optimization advisor, business users can:

-   Find proactive, quantified, actionable, and personalized optimization
    opportunities in one place.

-   Take recommended actions.

-   Analyze the impact of taking the recommended actions.

With the current release, the advisor presents opportunities to optimize:

-   The performance of inventory closing. 

-   The performance of wave processing and work creation within warehouse
    management.

-   The overall performance of the application by updating system configuration
    settings to reflect the actual business processes. 

-   Master data quality across BOMs, routes, and inventory management.

Partial release of materials and release materials per production operation 
----------------------------------------------------------------------------

Previously, when a production order was released, all the material for the order
was released to the warehouse. In some production scenarios, this was not the
optimal process. For example, consider the following scenarios:

-   Production orders where material is consumed on different operation.

-   Long running production orders where materials for the total quantity of the
    production order cannot be released at once; either because all the material
    is not available or there is not space enough on the shop floor.

To better support these scenarios, the release process has been enhanced with
the following capabilities:

-   Ability to limit the release of materials to an operation or selected
    operations.

-   Ability to release materials for a partial quantity of finished goods. In
    process industries, this can for example be useful for batch orders where
    not all the materials that are scheduled for the order can be consumed at
    once. For example, if you plan to produce 1000 pieces of the finished goods
    per day or shift, then you can easily limit the release of materials to
    match the requirement for this quantity.

Product lifecycle state   
--------------------------

The product lifecycle state is now available for released products and product
variants. You can define any number of product lifecycle states by assigning a
state name and description. You can select one lifecycle state as the default
state for new released products. Released product variants inherit the product
lifecycle state from their released product masters. When changing the lifecycle
state on a released product master, you can choose to update all existing
variants that have the same original state.  

To control and understand the situation of a specific product or product variant
in its lifecycle, it is a best practice in Product lifecycle management
solutions (PLM) to associate a lifecycle state with a variable state model to
products. This capability has been added to the released product model. The main
purpose of this extension is to provide a scalable solution that can exclude
obsolete products and product variants, including configurations, from master
planning and BOM-level calculation.

**Impact on master planning** - The product lifecycle state has only one control
flag: **Is active for planning**. By default, this is set to **Yes** for all
product lifecycle states. When the field is set to **No**, the associated
released products or product variants are: 

-   Excluded from Master planning 

-   Excluded from BOM level calculation 

For performance reasons, it is highly recommended that you associate all
obsolete released products or product variants to a product lifecycle state that
is deactivated for master planning, especially when you work with non-reusable
product configuration variants.  

**Find obsolete released products and products variants** - You can run an
analysis to find and update obsolete released products or product variants.

If you run the analysis in a simulation mode, the released products and product
variants that are identified as obsolete will be displayed on a specific page
for you to view. The analysis searches for transactions and specific master data
to find the released products or product variants that have no demand within a
specific period. New released products that are created within the specific
period can be excluded from the analysis.  

When the analysis simulation returns the expected result, you can run the
analysis by assigning a new product lifecycle state to all the products that are
identified as obsolete.  

**Default value during migration, import, and export**

-   When migrating from previous releases, the lifecycle state for all released
    products and product variants will be blank.  

-   When importing released products through a data entity, the default
    lifecycle state will be applied.  

-   When importing released product variants through a data entity, the product
    lifecycle state of the released product master will be applied. 

Note, the ability to set individual product lifecycle states using the data
entities for released products or product variants is not supported.

Product configuration enhancements  
------------------------------------

**Arrange attributes in one or multiple columns** - To optimize configuration
experience, you can arrange attributes in one or more columns. The maximum
number of columns is 10, and the default number is 1. This makes it easier to
model configuration experiences with many attributes in one configuration
step. You must first group attributes before you set up the field. If some
attributes are not added to groups, they will be shown in the leftmost column.
If all attributes are assigned to attribute groups, the groups will be shown in
the columns.

**Enable Z3 Solver strategy for product configuration** - The Z3 Solver strategy
is available for product configuration. In many benchmark tests, the solver has
shown a significant performance improvement compared to the Microsoft solver
foundation (MSF) solver. The new Z3 Solver strategy will be assigned per
configuration model. Note that the other three solver strategies are all
strategies of MSF: **Default**, **Top-down**, and **Minimal domains first**.

**Import, export, and migrate the product configuration model** - You can export
and import the product configuration model and model versions using standard
data entities. The configuration model is exported as an XML structure and saved
in a single entity, which makes it simple to export and import again.  

Safety stock replenishment enhancements   
------------------------------------------

The constraint that, at any given time, the available inventory for an item must
be above the safety stock quantity can introduce delays in shipping sales
orders, production orders, and any other real, independent, or dependent demand.
For example, for an item with 5 days lead time, if the item has 10 pieces in
inventory, and a safety stock level is set to 10, a sales line will be delayed
by 5 days, waiting for the delivery of the planned order for the item.

The constraint that the available inventory must always be above the safety
stock quantity is deprioritized if the system determines that this causes delays
in the fulfilment of real demand: sales lines, BOM lines, transfer requirements,
demand forecast lines, and so on. Otherwise, making sure that the available
inventory is above the safety stock quantity has the same priority as any other
demand types. This ensures no delays for real transactions and helps to prevent
over-replenishment and early-replenishment of safety stock.

During the coverage phase of master planning, safety stock replenishment is no
longer deprioritized. Now on-hand inventory can be used before any other demand
types. During the delay calculation, new logic will be added to go over the
delayed sales lines, BOM line requirements, and all the other demand types, to
determine whether they could be delivered on time, provided safety stock is
used. If the system identifies that it can minimize delays by using safety
stock, then the sales lines or BOM lines will replace their initial coverage
with the safety stock, and the system will trigger the replenishment for the
safety stock instead.

If the plan or the item is not set up for delayed calculation, then the safety
stock constraint will have the same priority as any other demand types. This
means there be a reserve of on-hand and other available inventory before any
other demand types.

Coverage calculation for the items that expire also has new logic. At any point
in time, the inventory receipt with the latest expiry date will be used for
safety stock to allow real demand, such as sale lines or BOM lines, to be
fulfilled in the FEFO (First Expired, First Out) order.

## Tax Engine (GTE) – India GST only
The Tax Engine (GTE) is an essential part of the configurable business application experience in Finance and Operations. It's highly customizable and lets a business user, functional consultant, or power user configure tax rules that determine tax applicability, calculation, posting, and settlement, based on legal and business requirements. Tax configuration is more flexible with GTE. It provides an easier extension experience; almost no code change is required for the data provider in the AOT to support extension scenarios.

Vendor collaboration 
---------------------
Vendor collaboration has been extended to enable vendors to view and selectively maintain their own company information, such as contact information, business identification data, procurement categories, and certifications. 

- The vendor can view and respond to RFQs, which includes the ability to receive and upload attachments. The collaborative interface allows the vendor to receive information about the awarded or lost bids.
- In public sector configurations, RFQs can now be published and exported as entities via data management. This enables the data to be consumed and exposed in a customer-hosted public website.
- A new workflow-supported process, Vendor onboarding, can facilitate the addition of new vendors to Dynamics 365 for Financial and Operations. The vendor is invited to register based on a signup request imported via entities or based on a request entered directly in Financial and Operations.
- The registration process provisions the person representing the vendor with a user account that has restrictive security roles and then invites the user to register by completing a wizard-guided process. The guided registration process prompts for data ,such as contact information, business identification data, procurement categories, and questionnaire answers. The information entered by the vendor contact person is populated in a vendor request and after the information has been approved via a workflow process, a new vendor account is created.

## Warehouse - Fulfillment policy added to full or partial batch release of transfer orders

The release to warehouse batch job is enriched by a fulfilment policy that is equivalent to the functionality for sales order, but now also includes transfer orders. You can batch release transfer orders according to a fulfilment rate policy. The policy can also be applied for the **Manual release to warehouse** form, as well as from the load release. It is also possible to override the default policy at a line level when releasing manually.

Warehouse - Tare weight used in containerization is included in the load’s gross weight
---------------------------------------------------------------------------------------

This enhancement ensures that the tare weight of a container used in the
containerization is included in the gross weight of the load. Some usability
enhancements of the load header have also been added to better relate to the
applied load template.

The volume of the container is now represented with greater detail, including
gross volume, remaining volume, and the ability to capture actual volume.

These updated values are consumed by the rate route engines, as well as by the
transportation tender.
