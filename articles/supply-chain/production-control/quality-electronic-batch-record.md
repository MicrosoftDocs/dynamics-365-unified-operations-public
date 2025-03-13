---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Electronic Signature

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one.

Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, aerospace and defense. They are also necessary for compliance with regulations in 21 CFR Part 11 issued by the Food and Drug Administration (FDA) in the United States.

An electronic signature by itself is not the same as a digital signature. An electronic signature is simply a substitute for a handwritten signature, while a digital signature provides additional security measures. A digital signature can help identify whether another user or process has tampered with the data. A digital signature can also be verified, and this verification cannot be refuted by the owner of the certificate that was used to sign the data. As described below, electronic signatures in Supply Chain Management have built-in digital signature functionality.

In Supply Chain Management, you can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field. Electronic signatures in Supply Chain Management have built-in digital signature functionality. Each user who signs documents must obtain a valid cryptographic certificate. When a document is signed, the private key associated with that certificate is validated.

Electronic Signature functionality has been enhanced to increase the security of the digital signatures to meet the latest government requirements and regulations.

## Setting up Electronic signature parameters

Using the Organization module, you maintain the various parameters for defining the controls you want to place on the capture of electronic signature of the various individuals for authorization of the various processes within your organization.

| **Path: Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature parameters** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| Translations | <blockquote></br>Opens a form where you can enter notice text in additional languages.</br></blockquote> |  |
| **Fields** |  |  |
| Notice | The notice that signers will see on the **Sign document** form. You can enter any text. Typically, this text tells the user what it means to sign a document electronically, including legal implications. |  |
| Require comments | Select this option if all signers are required to enter a comment when signing. |  |
| Signature timeout | An amount of time in seconds. If a signature has not been provided in this time frame, the signing process fails. |  |
| Key expiry | Number of days a digital key will be valid from its creation. |  |
| Signature alert recipient | The user id who should receive an alert email if signature validation fails. Validation fails if the system determines that the certificate and private key provided by a user show signs of tampering. |  |
| Minimum length | Required minimum length of the passphrase. | Hint: recommend at least a minimum of 8 characters |
| Minimum alpha | Required number of alpha characters in the passphrase. |  |
| Minimum numerals | Required number of numeric characters in the passphrase. |  |
| Minimum special | Required number of special characters in the passphrase. | Hint: special characters include: !, @, #, $, %, ^, &amp;, *, (, ), ;, :, ?, &lt;, &gt;, -, +, =, ~ |

***\*Note: All the parameters for the Passphrase constraints work in conjunction with the Windows policy requirements. The constraints can be more complex than the Windows policy however, it cannot be less complex. For example, if Windows policy dictates minimum length of 8 characters with couple of numbers and couple of special characters and the Passphrase constraints only requires 6 characters, the password will be rejected when generating the certificate.***

Electronic Batch Records (EBR)

Electronic batch records are a requirement of the 21 CFR Part 11 requirement placed on Life Science industries, and pharmaceutical industries. Extensions are required to standard Supply Chain Management functionality to enable the consolidation of production related data to meet those requirements. EBR is composed of two major functions. One function is the Master Manufacturing Record (MMR) which documents all the way an item might be produced and the various ways the characteristics might be measured. The other function is the Batch Production Record (BPR) which documents the specific way an item was produced and the actual value of the characteristic's measurements. It also details the characteristics and quantities of the ingredients used to produce the item.

## Setting up Electronic Batch Record

In order to activate Electronic batch records you have to select the feature for the desired company. You must also determine which processes should be managed with the capture of electronic or digital signature.

### Utilizing Electronic Batch Records

First, select the desired company that will be utilizing electronic batch records. Select the parameters form for the Production Control module, select the Electronic Batch Record tab and select the 'Use electronic batch records' option.

When selected, a notification will be made to the user that you must remove the approval on BOMs, Formulas or Routes prior to editing those records. This allows for the capture of the electronic signature of the personnel performing these edits. By selecting to use EBR, the 'Block editing' functions, in Production Control for the Route and the 'Block editing' functions in Inventory and warehouse management for the BOM/Formulas, will be automatically selected and the option disabled. The Block Editing feature for Routes and BOM/Formulas prevents the editing of those records when the record is already approved. It requires that the approval is removed prior to editing and once editing is completed, the approval will need to be made before the record can be used in production.

Since the electronic batch record is maintained independently of the batch order or production order, a number sequence needs to be established. From the Production Control parameters form within the desired company select the Number Sequences tab and navigate to the Batch production record reference. Select or create a new number sequence and designate it accordingly.

### Setting up Electronic Signature Parameters

Before setting up the requirements for electronic signature, you need to establish the parameters. These parameters are detailed in the previous chapter.

### Setting up Electronics Signature Requirements

With the addition of EBR, new electronic signature requirements have been added. EBR requirements would normally be the posting of Picking lists, Route cards, Jobs cards, and Report as finished production journals. Other **eSignature** requirements may be desired to capture digital signatures for approving and activating BOM/Formula and Routes and the release of batch/production orders to the production floor. When EBR is in use, you should not use the Report as Finished action in the Process update action group. When EBR is in use, only production journals should be used for batch/production orders.

When the 'Post route card production journal' requirement is selected, a notification will be made to the user that the posting of Route card journals can no longer be performed automatically by Starting the Batch or Production order. Likewise, selecting 'Post picking list production journal (non-dispensing)' will make a notification that the posting of Picking list journals can no longer be performed automatically by Starting the Batch or Production order. Also, the Report as finished option of the Batch or Production order will be disabled. To Report as finish a batch or production order, the user will have to use the Report as finished production journal. This is due to the need to capture the electronic signature of the individuals who are posting those activities.

When the 'Validate quality order' requirement is selected, a signature will be required upon the validation of quality orders. The signature will be required at the validation of the overall quality order, not the validation of the individual Test of the Test group of the quality order.

### Configuring Work Instructions for BOM and Formula items

To establish work instructions for an ingredient line, you will need to edit the Formula line. When EBR is in use, the editing of formula lines will be blocked when the formula is approved. In order to edit the Formula, you'll need to remove that approval. Access the Formula form, or the Bill of material form from the Common section of the Inventory Management module. In the form you will see the BOM/Formula version in the lower portion of the form and the BOM/Formula lines in the upper portion of the form. Click **Approve** and select to **Remove approval**. Then click **Lines** to display the multiple ingredient lines for that BOM/Formula. Select the desired ingredient and click the **Work instructions** tab. Click **Add** to add a new work instruction for that ingredient. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of adding that ingredient in the production process.

### Configuring Work Instructions for Routes

To establish work instructions for an operation line, you will need to edit the Route. When EBR is in use, the editing of Routes will be blocked when the route is approved. To edit the Route, you'll need to remove that approval. Access the Route form from the Common section of the Production Control module. Another method to edit the Route is to access the route from the **Released Products** form from the Common section of the Product Information Management module. After you select the desired Item, select the **Engineer** tab, and click **Route** in the **View** action group. Select the desired operation and click the **Work instructions** tab. Click **Add** to add a new work instruction for that operation. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of executing that operation in the production process.

### Configuring Test Plan instructions for Test Groups

To establish test plan instruction for a test group, you will edit the actual test sequence within the test group. The test plan instruction will be visible within a quality order but cannot be edited. Select the Test Group menu option from the Setup section in the Inventory Management module. Select the desired **Test Group** and then select the applicable **Sequence Number**. The sequence number will be related to a particular test, such as testing for the percentage of fatty acid in the product. Click the **Test** tab and the **Test Plan** will be displayed in the right side of the lower pane. Click **Add** to add a new test plan instruction for that test sequence. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable test plan text that is needed to convey the proper instructions or comments about conducting that test. This might include not only the method, but the environmental parameters that should be present such as temperature, or what equipment to use to conduct the test.

Once the Test Plan instructions have been associated with the Test Group, the Quality Order that references that Test Group will display the Test Plan instructions for that test sequence in a read-only mode.

## Using Electronic Batch Records

Once all the production data has been maintained for the BOM item or Formula item, then you will be able to execute inquires that are the primary functions of EBR. EBR is composed of two major functions. One function is the Master Manufacturing Record (MMR) which documents all the methods an item might be produced and the various ways the characteristics might be measured. Specifically, this inquiry will contain all the BOM/Formula versions that are approved to use in the manufacturing of that item. It includes the various Route versions that have been approved as well. This information will also contain Quality Associations referenced to the production process of the item. These quality associations result in quality orders being generated for the item. If the item is an ingredient, there may be quality associations referenced for that ingredient that may generate quality orders during an inspection. Other characteristics may be referenced for the ingredients or produced items that indicate the type of characteristic that is being measured which may be related to a particular inventory batch dimension or information related to the vendor that supplied the ingredient.

The other function is the Batch Production Record (BPR) which documents the specific way the item was produced and the actual value of the characteristic's measurements. It also details the characteristics and quantities of the ingredients used to produce the item. Specifically, this inquiry will contain the BOM/Formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. Where the Master Manufacturing Record maintained the types of characteristics that would be measured for the item, the Batch Production Record maintains the actual values of those measured characteristics. It will contain the actual detail of the Quality Orders that were referenced by the Quality Associations in the Master Manufacturing Record (MMR).

### Using Master Manufacturing Record inquiry

When using the Master manufacturing record inquiry from the Production control module, you will select the desired Item number. You may select a site which will limit the BOM/Formula and Route versions to that site. You may select a date or a quantity that will perform a query like the process utilized by Master Scheduling that will filter the BOM/Formula and Route versions to those that meet the selection criteria for the selected date and/or quantity. For example, there may be multiple formula versions for the item, one for quantities from 0 to 500 and one version for quantities greater than 500. By leaving the quantity blank or 0, all formula versions will be shown. If the quantity was entered as 600 then only the formula version for quantities greater than 500 will be displayed. If the site is left blank, then formula versions that are non-site-specific will be displayed along with those formula versions that are site-specific.

All applicable Route versions will be displayed in the inquiry. The BOM/Formula versions and the Route version number are hyperlinks so that you may click on the number and the actual detailed form for the version will be displayed. Quality associations that are referenced as Production or Co-Product Production will be displayed with some brief information. By clicking the Details menu option for the selected Quality association, the detailed form for that quality association will be displayed. The Inventory batch attributes that have been defined for the produced item will be displayed with the applicable range and target value for each characteristic.

| **Path: Production control** \> **Inquiries** \> **Electronic batch records** \> **Master manufacturing record** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Criteria** |  |  |
| Item number | <blockquote></br>Select the item for which to list the manufacturing information</br></blockquote> | Field drop down will only list items with a 'Production type' of BOM, Formula or Planning item. |
| Site | <blockquote></br>Select a specific site for the selected item</br></blockquote> |  |
| Date | <blockquote></br>Enter a from date to filter the Formula/BOM version for the selected item</br></blockquote> |  |
| Quantity | <blockquote></br>Enter a from quantity to filter the Formula/BOM version for the selected item</br></blockquote> |  |
| **FastTabs** |  |  |
| General | <blockquote></br>Shows some general information for the selected item</br></blockquote> |  |
| BOM/Formula versions | <blockquote></br>List of the Formula/BOM versions of the selected item based on the specified criteria</br></blockquote> |  |
| Route versions | <blockquote></br>List of the Route versions of the selected item based on the specified criteria</br></blockquote> |  |
| Quality associations | <blockquote></br>List of all Quality association relations for the selected item</br></blockquote> | Use the Details button to open the Quality association form for the selected record. |
| Inventory batch attributes | <blockquote></br>List of all Inventory batch attributes specified for the selected item</br></blockquote> |  |

### Using Batch Production Record inquiry

When using the Batch production record inquiry from the Production control module, you will select either the desired Item number or the Batch production record associated with a specific Batch or Production order. If the item number is selected prior to the Batch production record, then the pull down of the Batch production record field will list only records associated to the specified item. If the Batch production record is selected prior to the Item number, the Item number field will default to the item number related to the Batch or Production order associated with the Batch production record ID.

The inquiry will contain the BOM/Formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. The Batch Production Record will give the user the ability to view the Inventory batch attributes and any Quality orders for the produced items as well as the Inventory batch attributes, Vendor batch details and Quality orders for the raw material items used in the production process.

| **Path: Production control** \> **Inquiries** \> **Electronic batch records** \> **Batch production record** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Criteria** |  |  |
| Item number | <blockquote></br>Select the item for which to list the manufacturing information</br></blockquote> | Field drop down will only list items with a 'Production type' of BOM, Formula or Planning item. |
| Batch production record | <blockquote></br>Select the Batch production record ID for a corresponding Batch or Production order</br></blockquote> | Required field. If selected before the item number, the Item number field will default to the item number of the Batch or Production order related to the Batch production record ID. |
| **FastTabs** |  |  |
| Production order | <blockquote></br>Shows the Batch or Production order related to the specified Batch production record ID</br></blockquote> |  |
| Report as finished | <blockquote></br>Shows the produced items (including co/by products for formula items) for the Batch or Production order related to the specified Batch production record ID</br></blockquote> | Tab will be populated when the RAF production journal has been created.</br>Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record.</br>Inventory batch attributes button will only be active if there is Batch number for the selected record.</br>Use the Quality orders button to view the Quality orders for the selected record. |
| BOM/Formula | <blockquote></br>List the raw material items used in the production of the selected item</br></blockquote> |  |
| Picking list | <blockquote></br>Shows the information from the Picking list production journal of the Batch or Production order</br></blockquote> | Tab will be populated when the Picking list production journal has been created.</br>Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record.</br>Inventory batch attributes button will only be active if there is Batch number for the selected record.</br>Use the Vendor batch details button to open the Batches form to view the vendor batch information for the selected record.</br>Vendor batch details button will only be active if there is Batch number for the selected record.</br>Use the Quality orders button to view the Quality orders for the selected record. |
| Route | <blockquote></br>List the Route version used on the Batch or Production order</br></blockquote> |  |
| Route card | <blockquote></br>Shows the information from the Route card production journal of the Batch or Production order</br></blockquote> | Tab will be populated when the Route card production journal has been created. |
| Job card | <blockquote></br>Shows the information from the Job card production journal of the Batch or Production order</br></blockquote> | Tab will be populated when the Job card production journal has been created. |
| **Tabs** |  |  |
| Overview (Report as finished) | <blockquote></br>List the lines for each produced item based on the Report as finished production journal</br></blockquote> | If there were multiple (partial) RAFs, then the overview tab will list each line. |
| Transactions (Report as finished) | <blockquote></br>List the individual transaction lines for the produced items from the Inventory Registration</br></blockquote> |  |
| Overview (Picking list) | <blockquote></br>List the lines for each raw material item based on the Picking list production journal</br></blockquote> | If there were multiple (partial) Picking or if there is an Automatic reservation (ex. at Estimation), then the overview tab will list each line. |
| Transactions (Picking list) | <blockquote></br>List the individual transaction lines for each raw material item from the Inventory Reservation</br></blockquote> |  |

### Using Batch Production Record reports

The Batch production record report gives the user the ability to view/print a report using the Batch production record ID. The simplified version of the report will contain the same information reflected on the Batch production record Inquiry. On the General tab of the report, the user will have the ability to include more information for both the produced items and/or the raw material item. For the produced items, the user can choose to include the Quality order information as well as the Batch attribute value information on the report. For the raw material items, the user can choose to include the Quality order information, the Batch attribute value information as well as the Vendor batch details information on the report.

| **Path: Production control** \> **Reports** \> **Electronic batch records** \> **Batch production record** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Field** |  |  |
| Batch production record | <blockquote></br>Select the Batch production record ID for a corresponding Batch or Production order</br></blockquote> |  |
| Quality orders (Produced items) | <blockquote></br>Select to include the Quality orders for the produced items</br></blockquote> |  |
| Batch attribute values (Produced items) | <blockquote></br>Select to include the Batch attribute values for the batches of the produced items</br></blockquote> |  |
| Quality orders (Ingredients) | <blockquote></br>Select to include the Quality orders for the raw material items</br></blockquote> |  |
| Batch attribute values (Ingredients) | <blockquote></br>Select to include the Batch attribute values for the batches of the raw material items</br></blockquote> |  |
| Vendor batch details (Ingredients) | <blockquote></br>Select to include the Vendor batch details for the batches of the raw material items</br></blockquote> |  |
