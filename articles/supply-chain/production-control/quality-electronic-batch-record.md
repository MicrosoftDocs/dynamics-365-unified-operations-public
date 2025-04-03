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

<!-- KFM: This topic needs to go into the TOC. But where? -->

Electronic batch records are a requirement of the 21 CFR Part 11 requirement placed on Life Science industries, and pharmaceutical industries. Extensions are required to standard Supply Chain Management functionality to enable the consolidation of production related data to meet those requirements.

EBR is composed of two major functions. One function is the master manufacturing record (MMR) which documents all the way an item might be produced and the various ways the characteristics might be measured. The other function is the batch production record (BPR) which documents the specific way an item was produced and the actual value of the characteristic's measurements. It also details the characteristics and quantities of the ingredients used to produce the item.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM: Confirm feature requirements -->
    - *(Preview) Advanced quality management*
    - *(Preview) Electronic signature improvements*

## Set up EBR

To enable the feature go to **Production control** \> **Setup** \> **Production control parameters**. Under the **Electronic batch record** tab, make the following selections:

**Use electronic batch records** – Select this option to enable EBR. When selected, a notification will be made to the user that you must remove the approval on BOMs, formulas or routes prior to editing those records. This allows for the capture of the electronic signature of the personnel performing these edits. By selecting to use EBR, the *block editing* functions, in production control for the route and the *block editing* functions in Inventory and warehouse management for the BOM/formulas, will be automatically selected and the option disabled. The block editing feature for routes and BOM/formulas prevents the editing of those records when the record is already approved. It requires that the approval is removed prior to editing and once editing is completed, the approval will need to be made before the record can be used in production.

**Include batch expiration on BPR** – Determines if the batch expiration date should be included in the BPR report.
**Suppress work instructions on EBR** – Select to suppress the work instruction section in the PBR report, if there are no work instructions.

**Allow BPR to print multiple reports at once** – Allow to print multiple PBR's in one single report. If not selected, only one BPR can be printed per report.

### Set up number sequence for the electronic batch record

Since the electronic batch record is maintained independently of the batch order or production order, a number sequence needs to be established. Go to **Production control** \> **Setup** \> **Production control parameters**. Under the **Number sequences** FastTab, set up a new number sequence for **Batch production record**

### Set up electronics signature requirements

You can configure electronic signature requirements to the following production journal types to support EBR

- Picking list journal
- Route and job card journals
- Report as finished journal.

When the **Post route card production journal** E-signature requirement is selected, a notification will be made to the user that the posting of route card journals can no longer be performed automatically by Starting the batch or production order. Likewise, selecting **Post picking list production journal (non-dispensing)** e-signature requirement is selected, a notification that the posting of Picking list journals can no longer be performed automatically by Starting the batch or production order. Also, the report as finished option of the batch or production order will be disabled. To Report as finish a batch or production order, the user will have to use the Report as finished production journal. This is due to the need to capture the electronic signature of the individuals who are posting those activities.

When the **Validate quality order** E-signature requirement is selected, a signature will be required upon the validation of quality orders. The signature will be required at the validation of the overall quality order, not the validation of the individual test of the quality order.

### Configuring work instructions for BOM and formula items

To establish work instructions for an ingredient line, you will need to edit the formula line. When EBR is in use, the editing of formula lines will be blocked when the formula is approved. In order to edit the formula, you'll need to remove that approval. Access the formula page, or the bill of material page from the **Common** section of the **Inventory Management** module. In the page you will see the BOM/formula version in the lower portion of the page and the BOM/formula lines in the upper portion of the page. Select **Approve** and select to **Remove approval**. Then select **Lines** to display the multiple ingredient lines for that BOM/formula. Select the desired ingredient and select the **Work instructions** tab. Select **Add** to add a new work instruction for that ingredient. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of adding that ingredient in the production process.

### Configuring work instructions for routes

To establish work instructions for an operation line, you will need to edit the route. When EBR is in use, the editing of routes will be blocked when the route is approved. To edit the route, you'll need to remove that approval. Access the route form from the **Common** section of the **Production Control** module. Another method to edit the route is to access the route from the **Released Products** form from the Common section of the Product Information Management module. After you select the desired Item, select the **Engineer** tab, and select **Route** in the **View** action group. Select the desired operation and select the **Work instructions** tab. Select **Add** to add a new work instruction for that operation. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of executing that operation in the production process.

### Configuring test plan instructions for test groups

To establish test plan instruction for a test group, you will edit the actual test sequence within the test group. The test plan instruction will be visible within a quality order but cannot be edited.

Go to **Inventory Management** \> **Setup** \> **Quality control** \> **Test groups**. Select the desired **Test group** and then select the applicable **Sequence number**. The sequence number will be related to a particular test, such as testing for the percentage of fatty acid in the product. Select the **Test** Tab and the **Test plan** will be displayed in the right side of the lower pane. Select **Add** to add a new test plan instruction for that test sequence. Select the **Type** of *Note* and enter a short **Description**. In the lower text box, enter the applicable test plan text that is needed to convey the proper instructions prestnt such as temperature or wat equipment to use to conduct the test.

Once the **Test Plan instructions** have been associated with the **Test Group**, the quality order that references that **Test group** will display the **Test Plan instructions** for that test sequence in a read-only mode.

## Using electronic batch records

Once all the production data has been maintained for the BOM item or formula item, then you will be able to execute inquires that are the primary functions of EBR. EBR is composed of two major functions. One function is the Master Manufacturing Record (MMR) which documents all the methods an item might be produced and the various ways the characteristics might be measured. Specifically, this inquiry will contain all the BOM/formula versions that are approved to use in the manufacturing of that item. It includes the various route versions that have been approved as well. This information will also contain **Quality associations** referenced to the production process of the item. These **Quality associations** result in quality orders being generated automatically for the item. If the item is an ingredient, there may be quality associations referenced for that ingredient that may generate quality orders during an inspection. Other characteristics may be referenced for the ingredients or produced items that indicate the type of characteristic that is being measured which may be related to a particular inventory batch dimension or information related to the vendor that supplied the ingredient.

The other function is the batch production Record (BPR) which documents the specific way the item was produced and the actual value of the characteristic's measurements. It also details the characteristics and quantities of the ingredients used to produce the item. Specifically, this inquiry will contain the BOM/formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. Where the Master Manufacturing Record maintained the types of characteristics that would be measured for the item, the batch production Record maintains the actual values of those measured characteristics. It will contain the actual detail of the quality Orders that were referenced by the quality Associations in the Master Manufacturing Record (MMR).

### Using master manufacturing record inquiry

When using the Master manufacturing record inquiry from the **Production control** module, you will select the desired **Item number**. You may select a site which will limit the BOM/formula and route versions to that site. You may select a date or a quantity that will perform a query like the process utilized by Master Scheduling that will filter the BOM/formula and route versions to those that meet the selection criteria for the selected date and/or quantity. For example, there may be multiple formula versions for the item, one for quantities from 0 to 500 and one version for quantities greater than 500. By leaving the quantity blank or 0, all formula versions will be shown. If the quantity was entered as 600 then only the formula version for quantities greater than 500 will be displayed. If the site is left blank, then formula versions that are non-site-specific will be displayed along with those formula versions that are site-specific.

All applicable route versions will be displayed in the inquiry. The BOM/formula versions and the route version number are hyperlinks so that you can select the number and the actual detailed form for the version will be displayed. quality associations that are referenced as production or Co-Product production will be displayed with some brief information. By selecting the **Details** menu option for the selected quality association, the detailed form for that quality association will be displayed. The Inventory batch attributes that have been defined for the produced item will be displayed with the applicable range and target value for each characteristic.

- **Path: Production control** \> **Inquiries** \> **Electronic batch records** \> **Master manufacturing record**
- **Label Name** – **Description** – **Examples/Hints**
- **Criteria**
    - **Item number** – Select the item for which to list the manufacturing information – Field drop down will only list items with a **Production type** of *BOM*, *Formula* or *Planning item*.
    - **Site** – Select a specific site for the selected item
    - **Date** – Enter a from date to filter the formula/BOM version for the selected item
    - **Quantity** – Enter a from quantity to filter the formula/BOM version for the selected item
- **FastTabs**
    - **General** – Shows some general information for the selected item
    - **BOM/formula versions** – List of the formula/BOM versions of the selected item based on the specified criteria
    - **Route versions** – List of the route versions of the selected item based on the specified criteria
    - **Quality associations** – List of all quality association relations for the selected item – Use the Details button to open the quality association form for the selected record.
    - **Inventory batch attributes** – List of all Inventory batch attributes specified for the selected item

### Using batch production record inquiry

When using the batch production record inquiry from the production control module, you will select either the desired Item number or the batch production record associated with a specific batch or production order. If the item number is selected prior to the batch production record, then the pull down of the batch production record field will list only records associated to the specified item. If the batch production record is selected prior to the Item number, the Item number field will default to the item number related to the batch or production order associated with the batch production record ID.

The inquiry will contain the BOM/formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. The batch production Record will give the user the ability to view the Inventory batch attributes and any quality orders for the produced items as well as the Inventory batch attributes, Vendor batch details and quality orders for the raw material items used in the production process.

- **Path: Production control** \> **Inquiries** \> **Electronic batch records** \> **Batch production record**
- **Label Name** – **Description** – **Examples/Hints**
- **Criteria**
    - **Item number** – Select the item for which to list the manufacturing information – Field drop down will only list items with a **Production type** of *BOM*, *Formula* or *Planning item*.
    - **Batch production record** – Select the batch production record ID for a corresponding batch or production order – Required field. If selected before the item number, the Item number field will default to the item number of the batch or production order related to the batch production record ID.
    - **FastTabs**
    - **Production order** – Shows the batch or production order related to the specified batch production record ID
    - **Report as finished** – Shows the produced items (including co/by products for formula items) for the batch or production order related to the specified batch production record ID – Tab will be populated when the RAF production journal has been created. Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record. Inventory batch attributes button will only be active if there is batch number for the selected record. Use the quality orders button to view the quality orders for the selected record.
    - **BOM/formula** – List the raw material items used in the production of the selected item
    - **Picking list** – Shows the information from the Picking list production journal of the batch or production order – Tab will be populated when the Picking list production journal has been created. Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record. Inventory batch attributes button will only be active if there is batch number for the selected record. Use the Vendor batch details button to open the batches form to view the vendor batch information for the selected record. Vendor batch details button will only be active if there is batch number for the selected record. Use the quality orders button to view the quality orders for the selected record.
    - **Route** – List the route version used on the batch or production order
    - **Route card** – Shows the information from the route card production journal of the batch or production order – Tab will be populated when the route card production journal has been created.
    - **Job card** – Shows the information from the Job card production journal of the batch or production order – Tab will be populated when the Job card production journal has been created.
- **Tabs**
    - **Overview (Report as finished)** – List the lines for each produced item based on the Report as finished production journal – If there were multiple (partial) RAFs, then the overview tab will list each line.
    - **Transactions (Report as finished)** – List the individual transaction lines for the produced items from the Inventory Registration
    - **Overview (Picking list)** – List the lines for each raw material item based on the Picking list production journal – If there were multiple (partial) Picking or if there is an Automatic reservation (ex. at Estimation), then the overview tab will list each line.
    - **Transactions (Picking list)** – List the individual transaction lines for each raw material item from the Inventory Reservation

### Using batch production record reports

The batch production record report gives the user the ability to view/print a report using the batch production record ID. The simplified version of the report will contain the same information reflected on the batch production record Inquiry. On the General tab of the report, the user will have the ability to include more information for both the produced items and/or the raw material item. For the produced items, the user can choose to include the quality order information as well as the batch attribute value information on the report. For the raw material items, the user can choose to include the quality order information, the batch attribute value information as well as the Vendor batch details information on the report.

- **Batch production record** – Select the batch production record ID for a corresponding batch or production order
- **Quality orders (Produced items)** – Select to include the quality orders for the produced items
- **Batch attribute values (Produced items)** – Select to include the batch attribute values for the batches of the produced items
- **Quality orders (Ingredients)** – Select to include the quality orders for the raw material items
- **Batch attribute values (Ingredients)** – Select to include the batch attribute values for the batches of the raw material items
- **Vendor batch details (Ingredients)** – Select to include the Vendor batch details for the batches of the raw material items
