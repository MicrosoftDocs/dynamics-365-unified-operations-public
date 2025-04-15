---
title: Electronic batch records (EBR) (preview)
description: Learn how to use electronic batch records to consolidate production-related data to meet 21 CFR Part 11 requirements.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSBatchProdRecord, QMSMasterMfgRecord
ms.topic: how-to
ms.date: 01/25/2025
ms.custom: 
  - bap-template
---

## Electronic batch records (EBR) (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Electronic batch records (EBRs) are required by the *21 CFR Part 11* regulations, which apply to the life science and pharmaceutical industries. EBRs have two major components:

- Master manufacturing record (MMR) – Documents all the ways an item might be produced and the various ways its characteristics might be measured.
- Batch production record (BPR) – Documents the specific way an item was produced and the actual value of the characteristic's measurements. It also details the characteristics and quantities of the ingredients used to produce the item.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM: Confirm feature requirements -->
    - *(Preview) Advanced quality management*
    - *(Preview) Electronic signature improvements*

## Turn electronic signature requirements for EBR on or off

<!-- KFM: I assumed this section. Please confirm. -->

To set up the electronic signature requirements for the types of records used for EBR, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the left pane, select the row for one of the features you want to turn electronic signatures on or off for. EBR typically expects signatures to be required for the following features (as listed in the **Name** column).
    - *Activate BOM version*
    - *Approve bill of materials*
    - *Activate route version*
    - *Approve BOM version*
    - *Approve route*
    - *Approve route version*
    - *Post dispensing ticket production journal*
    - *Post picking list production journal (non-dispensing)*
    - *Post report as finished production journal*
    - *Post route card production journal*
    - *Validate quality order*
1. In the right pane, set **Signature required** to *Yes* to require signatures from users who perform actions related to this feature. Set it to *No* to turn off the requirement.
1. Repeat from step 2 for each feature you want to turn electronic signatures on or off for.

<!-- KFM: Add section about setting up ES reason codes? these are mentioned in the bug bash video (27:13). -->

## Set up EBR

To enable EBR, follow these steps.\

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. Open the **Electronic batch record** tab.\
1. Make the following settings:
    - **Use electronic batch records** – To enable EBR for your system, set this option to *Yes*. When you change this setting to *Yes*, you'll see a message that says you must remove approvals on BOMs, formulas, or routes before editing those records. This allows the system to capture electronic signatures of the personnel performing these edits. While EBR is enabled, the *block editing* functions for routes and BOMs/formulas are automatically enabled and can't be disabled. The block editing feature for routes and BOMs/formulas prevents the editing of those records after they're approved. Approval must be removed before editing and after editing is completed, approval is required before the record can be used in production.
    - **Include batch expiration on BPR** – Choose whether the batch expiration date should be included in the BPR report.
    - **Suppress work instructions on EBR** – Choose whether to suppress the work instruction section in the PBR report when there aren't any work instructions.
    - **Allow BPR to print multiple reports at once** – Choose whether to allow multiple PBRs to be printed in a single report. If this is set to *No*, then only one BPR can be printed per report.

<!-- KFM: In the bug bash video, they go to **Print management** tab and do some setup that I don't see on my system. Should we add that here? Why don't I see it?  -->

### Set up a number sequence for the EBR

Because the EBR is maintained independently of the batch order or production order, a number sequence must be established.

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. Open the **Number sequences** tab.
1. Set up a new number sequence for the row with a **Reference** of *Batch production record*.

### Set up electronics signature requirements

You can configure electronic signature requirements to support EBR for the following production journal types:

- Picking list journal
- Route and job card journals
- Report as finished journal

Each of these journal types provides the following e-signature options: <!-- KFM: It isn't clear where these settings are. -->

- **Post route card production journal** – When this option is set to *Yes*, the system notifies users that route card journals are no longer posted automatically when starting a batch or production order.
- **Post picking list production journal (non-dispensing)** – When this option is set to *Yes*, the system notifies users that picking list journals are no longer posted automatically when starting a batch or production order. Also, the report as finished option of the batch or production order is disabled. To report a batch or production order as finish, you must use the report as finished production journal. This is because the system must capture the electronic signature of the individuals who are posting those activities.
- **Validate quality order** – When this option is set to *Yes*, the system requires a signature when validating an overall quality order, but not when validating individual tests of a quality order.

### Add work instructions to formula items

To add work instructions to a formula line, follow these steps.

1. Go to **Product information management \> **Products** \> **Released products**.
1. Open or select the item that uses the formula that you want to add instructions to.
1. On the Action Pane, open the **Engineer** tab and select **Formula versions**.
1. From the list pane, select the formula version that you want to edit.
1. On the Action Pane, open the **Formulas** tab and select **Formula**.
1. If your formula has **Approved** set to *Yes* on the **Formula header** FastTab, you must remove the approval before you can edit it. Follow these steps:
    1. On the Action Pane, open the **Formula** tab and select **Approve formula**.
    1. In the dialog, set **Remove approval** to *Yes*.
    1. Select *OK*.
1. On the **Formula lines** FastTab, select the line you want to add instructions to.
1. On the **Line details** FastTab, open the **Work instructions** tab.
1. Select **Add** on the **Work instructions** tab toolbar to add a new work instruction for the selected line.
1. Set **Type** to *Note* and enter a short **Description**.
1. In the lower text box, enter the required work instructions or other comments.
1. On the Action Pane, select **Save**.

### Add work instructions to BOM items

To add work instructions to a BOM line, follow these steps.

1. Go to **Product information management \> **Products** \> **Released products**.
1. Open or select the item that uses the BOM that you want to add instructions to.
1. On the Action Pane, open the **Engineer** tab and select **BOM versions**.
1. From the list pane, select the BOM version that you want to edit.
1. On the Action Pane, open the **Bill of materials** tab and select **Bills of materials**.
1. If your BOM has **Approved** set to *Yes* on the **Bill of materials header** FastTab, you must remove the approval before you can edit it. Follow these steps:
    1. On the Action Pane, open the **Bill of materials** tab and select **Approval**.
    1. In the dialog, set **Remove approval** to *Yes*.
    1. Select *OK*.
1. On the **Bill of materials lines** FastTab, select the line you want to add instructions to.
1. On the **Line details** FastTab, open the **Work instructions** tab.
1. Select **Add** on the **Work instructions** tab toolbar to add a new work instruction for the selected line.
1. Set **Type** to *Note* and enter a short **Description**.
1. In the lower text box, enter the required work instructions or other comments.
1. On the Action Pane, select **Save**.

### Add work instructions for routes

To establish work instructions for an operation line, you must edit the route. When EBR is in use, the editing of formula lines is blocked for approved routes. To add work instructions to a route, follow these steps.

1. Go to **Product information management \> **Products** \> **Released products**.
1. Open or select the item that uses the route you want to edit.
1. On the Action Pane, open the **Engineer** tab and, from the **View** group, select **Route**.
1. In the top section, select the route version you want to edit.
1. If your selected route version shows a check mark in the **Approved** column, you must remove the approval before you can edit the route. Follow these steps:
    1. On the Action Pane, open the **Route version** tab and select **Approve**.
    1. In the dialog, set **Remove approval** to *Yes*.
    1. Select *OK*.
1. In the bottom section, open the **Overview** tab and select the operation you want to edit.
1. In the bottom section, open the **Work instructions** tab.
1. Select **New** on the **Work instructions** tab toolbar to add a new work instruction for the selected operation.
1. Set **Type** to *Note* and enter a short **Description**.
1. In the lower text box, enter the required work instructions or other comments.

### Configure test plan instructions for test groups

When test plan instructions are associated with a line in a test group, quality orders that reference that test group displays those instructions as read-only text. To add test plan instruction to a test group, follow these steps.

1. Go to **Inventory Management** \> **Setup** \> **Quality control** \> **Test groups**.
1. In the top section, open the **Overview** tab and select the test group you want to add instructions to.
1. In the bottom section, open the **Overview** tab and select the test that you want to add instructions to.
1. In the bottom section, open the **Test plan notes** tab.
1. Select **Add** on the **Test plan notes** tab toolbar to add a new work instruction for the selected test line.
1. Set **Type** to *Note* and enter a short **Description**.
1. In the lower text box, enter the required work instructions or other comments.

## Work with EBRs

When all the required production data is set up for a BOM or formula item, you can search for that information, which is the primary purpose of EBR.

EBR is composed of the following two major functions.

- **Master manufacturing record (MMR)** – Documents all the methods that might be used to produce an item and the various ways its characteristics might be measured. This query contains all the BOM/formula versions that are approved to use in the manufacturing of that item. It also includes the various approved route versions. This information also includes quality associations referenced by the production process of the item. These quality associations result in quality orders being generated automatically for the item. If the item is an ingredient, there might be quality associations referenced for that ingredient that might generate quality orders during an inspection. Other characteristics might be referenced for the ingredients or produced items that indicate the type of characteristic that is being measured, which might be related to a particular inventory batch dimension or information related to the vendor that supplied the ingredient.

- **Batch production record (BPR)** – Documents the specific way the item was produced and the value of each characteristic. It also details the characteristics and quantities of the ingredients used to produce the item. This query contains the BOM/formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information also contains the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredients that were substituted during the production process.

Where the MMR maintains the types of characteristics that would be measured for the item, the BPR maintains the actual values of those measured characteristics. The BPR contains the actual detail of the quality orders that were referenced by the quality associations in the MMR.

### Run an MMR query

When you run an MMR query, you start by selecting the target item number. You can also select a site to limit the BOM/formula and route versions to that site. You can also select a date and/or quantity.

All applicable route versions are displayed in the query results. The BOM/formula versions and the route version number are hyperlinks, so you can select the number to open the detailed page for the selected version. Quality associations that are referenced as production or co-product production are displayed and summarized. Select **Details** for a quality association to see the detailed form for that quality association. Inventory batch attributes defined for the produced item are displayed with the applicable range and target value for each characteristic.

To run an MMR query, follow these steps.

1. Go to **Production control** \> **Inquiries** \> **Electronic batch records** \> **Master manufacturing record**.
1. At the top of the page, set up your query by specifying one or more of the following criteria.
    - **Item number** – Select the item for which to list the manufacturing information. The dropdown list only includes items with a **Production type** of *BOM*, *Formula* or *Planning item*.
    - **Site** – Select a specific site for the selected item.
    - **Date** – Enter a from date to filter the formula/BOM version for the selected item.
    - **Quantity** – Enter a from quantity to filter the formula/BOM version for the selected item.
1. Results and information are displayed in the following FastTabs.
    - **General** – Shows some general information for the selected item.
    - **BOM/formula versions** – Lists the formula/BOM versions of the selected item based on the specified criteria.
    - **Route versions** – Lists the route versions of the selected item based on the specified criteria.
    - **Quality associations** – Lists all quality association relations for the selected item. Use the **Details** button to open the quality association form for the selected record.
    - **Inventory batch attributes** – List of all inventory batch attributes specified for the selected item.

### Run a BPR query

When you run a BPR query, you start by selecting either the desired item number or the batch production record associated with a specific batch or production order.

The query contains the BOM/formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information also includes the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that might have been substituted during the production process. The batch production record lets you view the inventory batch attributes and any quality orders for the produced items plus the inventory batch attributes, vendor batch details, and quality orders for the raw material items used in the production process.

To run a BPR query, follow these steps.

1. Go to **Production control** \> **Inquiries** \> **Electronic batch records** \> **Batch production record**.
1. At the top of the page, set up your query by specifying one or more of the following criteria.
    - **Item number** – Select the item for which to list the manufacturing information. The drop-down list only includes items with a **Production type** of *BOM*, *Formula*, or *Planning item*.
    - **Batch production record** – Select the batch production record ID for a corresponding batch or production order. If you select this before the item number, the **Item number** field defaults to the item number of the batch or production order related to the batch production record ID.
1. Results and information are displayed in the following FastTabs.
    - **Production order** – Shows the batch or production order related to the specified batch production record ID
    - **Report as finished** – Shows the produced items (including co/by products for formula items) for the batch or production order related to the specified batch production record ID. The FastTab is populated when the RAF production journal has been created. Use the **Inventory batch attributes** button in the toolbar to view attribute information for the selected record. The **Inventory batch attributes** button is only active if there's batch number for the selected record. Use the **Quality orders** button to view the quality orders for the selected record.
    - **BOM/formula** – Lists the raw material items used in the production of the selected item.
    - **Picking list** – Shows the information from the picking list production journal of the batch or production order. The FastTab is populated when the picking list production journal has been created. Use the **Inventory batch attributes** button to view attribute information for the selected record. The **Inventory batch attributes** button is only active if there's batch number for the selected record. Use the **Vendor batch details** button to view the vendor batch information for the selected record. The **Vendor batch details** button is only active if there's batch number for the selected record. Use the **Quality orders** button to view the quality orders for the selected record.
    - **Route** – Lists the route version used on the batch or production order
    - **Route card** – Shows the information from the route card production journal of the batch or production order. The FastTab is populated when the route card production journal has been created.
    - **Job card** – Shows information from the job card production journal of the batch or production order. The FastTab is populated when the job card production journal has been created.

### Generate a batch production record report

The batch production record report lets you view and/or print a report for a batch production record ID. A simplified version of the report contains the same information reflected on a batch production record query.

To generate a batch production record report, follow these steps.

1. Run a BPR query to find the relevant batch production record, as described in the previous section.
1. On the Action Pane, select **Batch production report (BPR)**.
1. In the dialog, expand the **Parameters** FastTab and choose which details you want to include in the report.
1. On the **Destination** FastTab, choose whether to view the report on screen, print it, save it as a file, or email it.
1. Select **OK** to generate the report.

<!-- KFM: Add a section that describes how to find the batch production record from a production order or batch order? Other places? -->