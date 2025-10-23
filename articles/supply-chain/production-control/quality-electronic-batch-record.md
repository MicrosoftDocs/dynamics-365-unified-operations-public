---
title: Electronic batch records (EBRs)
description: Learn how to use electronic batch records (EBRs) to consolidate production-related data to meet 21 CFR Part 11 requirements.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSBatchProdRecord, QMSMasterMfgRecord
ms.topic: how-to
ms.date: 01/25/2025
ms.custom: 
  - bap-template
---

# Electronic batch records (EBRs)

[!include [banner](../../includes/banner.md)]

Electronic batch records (EBRs) are required by part 11 of Title 21 of the Code of Federal Regulations (21 CFR Part 11), which applies to life science and pharmaceutical industries. EBRs consist of two major components:

- **Master manufacturing record (MMR)** – This component documents all the methods that might be used to produce an item and the various ways that the item's characteristics might be measured.
- **Batch production record (BPR)** – This component documents the actual method that was used to produce the item and the actual value of the measurement for each of the item's characteristics. It also details the characteristics and quantities of the ingredients that were used to produce the item.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

    - *Advanced quality management*
    - *Electronic signature improvements*

## Turn electronic signature requirements for EBRs on or off

To set up the electronic signature requirements for the types of records that are used for EBRs, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the left pane, select the row for a feature that you want to turn electronic signature requirements on or off for. For EBRs, the usual expectation is that signatures are required for the following features (as listed in the **Name** column):

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

1. In the right pane, set the **Signature required** option to *Yes* to require signatures from users who perform actions that are related to the feature. Set the option to *No* to turn off the requirement.
1. Repeat steps 2 and 3 for every other feature that you want to turn electronic signature requirements on or off for.

## Set up EBRs

To enable EBRs, follow these steps.

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. On the **Electronic batch record** tab, set the following fields:

    - **Use electronic batch records** – Set this option to *Yes* to enable EBRs in your system. When you change the setting to *Yes*, a message notifies you that you must remove approvals on bills of materials (BOMs), formulas, or routes before you edit those records. In this way, the system can capture electronic signatures of the users who perform the edits. While EBRs are enabled, the *block editing* functions for routes and BOMs/formulas are automatically enabled and can't be disabled. The block editing feature for routes and BOMs/formulas prevents those records from being edited after they are approved. Approval must be removed before the records are edited. Then, after editing is completed, approval is required before the records can be used in production.
    - **Include batch expiration on BPR** – Select whether the batch expiration date should be included on the BPR report.
    - **Suppress work instructions on EBR** – Select whether the work instruction section of the BPR report should be omitted if there aren't any work instructions.
    - **Allow BPR to print multiple reports at once** – Select whether multiple BPRs can be printed on a single report. If this option is set to *No*, only one BPR can be printed per report.

### Set up a number sequence for EBRs

Because EBRs are maintained independently of the batch order or production order, a number sequence must be established.

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. On the **Number sequences** tab, set up a new number sequence for the row where the **Reference** field is set to *Batch production record*.

### Set up electronics signature requirements

You can configure electronic signature requirements to support EBRs for the following types of production journals:

- Picking list journal
- Route and job card journals
- Report as finished journal

Each of these journal types provides the following electronic signature options:

- **Post route card production journal** – When this option is set to *Yes*, the system notifies users that route card journals are no longer automatically posted when a batch or production order is started.
- **Post picking list production journal (non-dispensing)** – When this option is set to *Yes*, the system notifies users that picking list journals are no longer automatically posted when a batch or production order is started. In addition, the option for reporting the batch or production order as finished is disabled. Because the system must capture the electronic signature of the users who post those activities, the report as finished production journal must be used to report a batch or production order as finished.
- **Validate quality order** – When this option is set to *Yes*, the system requires a signature when an overall quality order is validated. However, no signature is required when individual tests of a quality order are validated.

### Add work instructions to formula items

To add work instructions to a formula line, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Open or select the item that uses the formula that you want to add instructions to.
1. On the Action Pane, on the **Engineer** tab, select **Formula versions**.
1. In the list pane, select the formula version that you want to edit.
1. On the Action Pane, on the **Formulas** tab, select **Formula**.
1. If the **Approved** option for the formula is set to *Yes* on the **Formula header** FastTab, you must follow these steps to remove the approval before you can edit the formula:

    1. On the Action Pane, on the **Formula** tab, select **Approve formula**.
    1. In the dialog, set the **Remove approval** option to *Yes*.
    1. Select **OK**.

1. On the **Formula lines** FastTab, select the line that you want to add instructions to.
1. On the **Line details** FastTab, on the **Work instructions** tab, select **Add** on the toolbar to add work instructions for the selected line.
1. In the **Type** field, select *Note*. Then, in the **Description** field, enter a short description.
1. In the lower text box, enter the required work instructions or other comments.
1. On the Action Pane, select **Save**.

### Add work instructions to BOM items

To add work instructions to a BOM line, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Open or select the item that uses the BOM that you want to add instructions to.
1. On the Action Pane, on the **Engineer** tab, select **BOM versions**.
1. In the list pane, select the BOM version that you want to edit.
1. On the Action Pane, on the **Bill of materials** tab, select **Bills of materials**.
1. If the **Approved** option for the BOM is set to *Yes* on the **Bill of materials header** FastTab, you must follow these steps to remove the approval before you can edit the BOM:

    1. On the Action Pane, on the **Bill of materials** tab, select **Approval**.
    1. In the dialog, set the **Remove approval** option to *Yes*.
    1. Select **OK**.

1. On the **Bill of materials lines** FastTab, select the line that you want to add instructions to.
1. On the **Line details** FastTab, on the **Work instructions** tab, select **Add** on the toolbar to add work instructions for the selected line.
1. In the **Type** field, select *Note*. Then, in the **Description** field, enter a short description.
1. In the lower text box, enter the required work instructions or other comments.
1. On the Action Pane, select **Save**.

### Add work instructions for routes

To add work instructions for an operation line, you must edit the route. When EBRs are used, formula lines for approved routes can't be edited. To add work instructions to a route, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Open or select the item that uses the route that you want to edit.
1. On the Action Pane, on the **Engineer** tab, in the **View** group, select **Route**.
1. In the top section, select the route version that you want to edit.
1. If a check mark appears in the **Approved** column for the selected route version, you must follow these steps to remove the approval before you can edit the route:

    1. On the Action Pane, on the **Route version** tab, select **Approve**.
    1. In the dialog, set the **Remove approval** option to *Yes*.
    1. Select **OK**.

1. In the bottom section, on the **Overview** tab, select the operation that you want to edit.
1. On the **Work instructions** tab, select **New** on the toolbar to add work instructions for the selected operation.
1. In the **Type** field, select *Note*. Then, in the **Description** field, enter a short description.
1. In the lower text box, enter the required work instructions or other comments.

### Configure test plan instructions for test groups

When test plan instructions are associated with a line in a test group, quality orders that reference the test group show the instructions as read-only text. To add test plan instruction to a test group, follow these steps.

1. Go to **Inventory Management** \> **Setup** \> **Quality control** \> **Test groups**.
1. In the top section, on the **Overview** tab, select the test group that you want to add instructions to.
1. In the bottom section, on the **Overview** tab, select the test that you want to add instructions to.
1. On the **Test plan notes** tab, select **Add** on the toolbar to add work instructions for the selected test line.
1. In the **Type** field, select *Note*. Then, in the **Description** field, enter a short description.
1. In the lower text box, enter the required work instructions or other comments.

## Work with EBRs

After all the required production data is set up for a BOM or formula item, you can search for that information. This capability is the primary purpose of EBRs.

As was mentioned earlier, EBRs consist of two major components:

- **Master manufacturing record (MMR)** – This component documents all the methods that might be used to produce an item and the various ways that the item's characteristics might be measured. The MMR query contains all the BOM/formula versions that are approved for use in the manufacture of the item. It also includes the various approved route versions. In addition, the information includes quality associations that are referenced by the production process for the item. As a result of these quality associations, quality orders are automatically generated for the item. If the item is an ingredient, quality associations for that ingredient might be referenced and cause quality orders to be generated during an inspection. Other characteristics might be referenced for the ingredients or produced items to indicate the type of characteristic that is being measured. The measured characteristic might be related to a specific inventory batch dimension or to the vendor that supplied the ingredient.
- **Batch production record (BPR)** – This component documents the actual method that was used to produce the item and the actual value of the measurement for each of the item's characteristics. It also details the characteristics and quantities of the ingredients that were used to produce the item. The BPR query contains the BOM/formula version that was used in the production process, together with the proposed ingredient quantities that were estimated for completion of the production. In addition, the information includes the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredients that were substituted during the production process.

Whereas the MMR maintains the types of characteristics that might be measured for the item, the BPR maintains the actual values of those measured characteristics. The BPR contains the actual details of the quality orders that were referenced by the quality associations in the MMR.

### Run an MMR query

When you run an MMR query, you first select the target item number. You can also select a site to limit the BOM/formula and route versions to that site. In addition, you can select a date and/or quantity.

The query results show all applicable route versions. The BOM/formula versions and the route version number are hyperlinks. You can use them to open the details page for the selected version. The results also show and summarize quality associations that are referenced as production or coproduct production. Select **Details** for a quality association to open the details page for it. Finally, the results show inventory batch attributes that are defined for the produced item, together with the applicable range and target value for each characteristic.

To run an MMR query, follow these steps.

1. Go to **Production control** \> **Inquiries** \> **Electronic batch records** \> **Master manufacturing record**.
1. At the top of the page, set up the query by specifying one or more of the following criteria:

    - **Item number** – Select the item to list the manufacturing information for. The dropdown list includes only items where the **Production type** field is set to *BOM*, *Formula*, or *Planning item*.
    - **Site** – Select a specific site for the selected item.
    - **Date** – Enter a "from" date to filter the formula/BOM version for the selected item.
    - **Quantity** – Enter a "from" quantity to filter the formula/BOM version for the selected item.

Results and information are shown on the following FastTabs:

- **General** – This FastTab shows general information about the selected item.
- **BOM/formula versions** – This FastTab lists the formula/BOM versions of the selected item, based on the specified criteria.
- **Route versions** – This FastTab lists the route versions of the selected item, based on the specified criteria.
- **Quality associations** – This FastTab lists all quality association relations for the selected item. Use the **Details** button to open the quality association page for the selected record.
- **Inventory batch attributes** – This FastTab lists all inventory batch attributes that are specified for the selected item.

### Run a BPR query

When you run a BPR query, you first select either the target item number or the BPR that is associated with a specific batch or production order.

The query contains the BOM/formula version that was used in the production process, together with the proposed ingredient quantities that were estimated for completion of the production. The information also includes the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredients that were substituted during the production process. In the BPR, you can view the inventory batch attributes and any quality orders for the produced items. You can also view the inventory batch attributes, vendor batch details, and quality orders for the raw material items that were used in the production process.

To run a BPR query, follow these steps.

1. Go to **Production control** \> **Inquiries** \> **Electronic batch records** \> **Batch production record**.
1. At the top of the page, set up the query by specifying one or more of the following criteria:

    - **Item number** – Select the item to list the manufacturing information for. The dropdown list includes only items where the **Production type** field is set to *BOM*, *Formula*, or *Planning item*.
    - **Batch production record** – Select the BPR ID for a corresponding batch or production order. If you select this criterion before the item number, the **Item number** field is automatically set to the item number of the batch or production order that is related to the selected BPR ID.

Results and information are shown on the following FastTabs:

- **Production order** – This FastTab shows the batch or production order that is related to the specified BPR ID.
- **Report as finished** – This FastTab shows the items that were produced for the batch or production order that is related to the specified BPR ID. (For formula items, the produced items include coproducts and by-products.) This FastTab is populated when the report as finished production journal is created. Use the **Inventory batch attributes** button on the toolbar to view attribute information for the selected record. (The **Inventory batch attributes** button is available only if there is batch number for the selected record.) Use the **Quality orders** button to view the quality orders for the selected record.
- **BOM/formula** – This FastTab lists the raw material items that were used to produce the selected item.
- **Picking list** – This FastTab shows information from the picking list production journal of the batch or production order. It's populated when the picking list production journal is created. Use the **Inventory batch attributes** button to view attribute information for the selected record. (The **Inventory batch attributes** button is available only if there is a batch number for the selected record.) Use the **Vendor batch details** button to view the vendor batch information for the selected record. (The **Vendor batch details** button is available only if there is a batch number for the selected record.) Use the **Quality orders** button to view the quality orders for the selected record.
- **Route** – This FastTab lists the route version that is used on the batch or production order.
- **Route card** – This FastTab shows the information from the route card production journal of the batch or production order. It's populated when the route card production journal is created.
- **Job card** – This FastTab shows information from the job card production journal of the batch or production order. It's populated when the job card production journal is created.

### Generate a BPR report

You can view and/or print a report for a specific BPR ID. A simplified version of the report contains the same information that is reflected in a BPR query.

To generate a BPR report, follow these steps.

1. Run a BPR query to find the relevant BPR, as described in the previous section.
1. On the Action Pane, select **Batch production report (BPR)**.
1. In the dialog, on the **Parameters** FastTab, select the details that you want to include on the report.
1. On the **Destination** FastTab, select whether you want to view the report on screen, print it, save it as a file, or email it.
1. Select **OK** to generate the report.
