---
title: Fix common posting issues by editing the transactions using Edit and Audit capability
description: This article provides the steps required to fix the common statement posting issues that required editing the transactions.
author: Shajain
ms.date: 03/27/2023
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2022-01-30
ms.search.form: RetailStatementTable_SOCreateFailed, RetailStatementTable_InvoiceFailed, RetailStatementTable_PaymentPosted
---

# Statement posting errors due to unavailable inventory or update conflicts
Error code: SYS103633, SYS328431

[!include [banner](../../includes/banner.md)]

This article provides the steps required to fix the common statement posting issues that required editing the transactions.

## Description

Sometimes the statement posting fails because the data in one or more transactions needs to be  corrected before posting can proceed. Some of the scenarios where such data correction is needed are as following:
1. The fiscal period mapping to the current transaction has been closed and hence the transactions cannot be posted
2. The transactions are created without a required field e.g. warehouse, batch number etc.

The data correction is done by editing the necessary transactions and the steps required to edit the transactions vary based on the stage of statement posting where that issue occurs. This guide firstly lists down the generic steps required to edit a transaction depending on the various stage of statement posting, followed by the common errors that occur during that stage and specific steps required to fix the issue.

Note: The link [Edit cash and carry transactions](https://learn.microsoft.com/en-us/dynamics365/commerce/edit-cash-trans) provides the basic details on the structure of the excel file that gets downloaded while editing the transactions.

## Issues during statement calculation 
This is a prerequisite step of the statement posting process. The most common error during this stage is the transaction validation failure as the system shows a warning that some of the transactions could not be included in the statement because they failed validation.

### Transaction validation failed 
If the Trickle feed feature has been enabled, then is required that the transactions are validated before they can be included in a statement. This is usually done via running the "Validate store transactions" batch job. Some transactions might fail during validation. Follow the below steps to resolve the issue.

	1. Navigate to **Store financials** workspace and open the **Cash and carry validation failures" view. Refer the below image
	2. Select the transaction and click on **Validation errors** to identify the error. Refer the below image
	3. Click on office icon on top right and select **Edit selected transactions**. Refer the below image
	4. Download the file
	5. Once the file is downloaded, enable editing on the file and sign in
	6. Identify the correct entity and field that needs to be modified
		a. If the field you are looking for is missing, then please get it in excel as described here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel)

	7. Change the value of fields and hit **Publish** on the excel
	8. Run **Validate Store Transactions** again. This ensures that system tries to validate the edited transaction.
	9. If the transaction gets validated, then you can choose to continue posting the statement without the newly validated transaction as it will be included in the next statement posting or you can use the **Clear statement** button under the **Functions** group of the current statement to free the transactions that were marked with the current statement and create a new statement.
	
## Issues during order creation 
One of the steps of statement posting is to create the customer orders by grouping one or more transactions. So, if the statement posting fails before the customer orders are created, then follow the below steps to resolve the issue.

	1. Navigate to failed statement
	2. Click on office icon on top right and select **Edit cash and carry transactions**. Note, this will automatically pull in all the cash and carry transactions that are a part of the current statement. 
	3. Download the file
	4. Once the file is downloaded, enable editing on the file and sign in
	5. Change the **Validation status** of transaction you need to fix to **None** or **Error** in excel. This is a **required step** to make any changes to the transaction.
	6. Identify the correct entity and field that needs to be modified
		a. If the field you are looking for is missing, then please get it in excel  as described here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel)
	7. Change the value of fields and hit **Publish** on the excel
	8. In Statement forms, click on **Revalidate transactions** under Function group. Refer the below image.
	9. Press the **Aggregated transactions** button under the **Execution details" group and then click on **Re-generate aggregation data** to clear the aggregations that were generated using the old values of the transaction. This is a required step to ensure that the statement uses the edited transaction values to regenerate the aggregated values. Refer the below image.
	10. Post the statement

Some of the common issues that occur during order creation are as following:

Error 1:
While processing the state Customer order created, generic exception encountered in retail statement [XXXXX] in the controller : Inventory dimension Site is mandatory and must consequently be specified.
	
Mitigation:
This issue occurs because the Site and warehouse are setup to be required fields for the transactions and some of the transactions are missing values or incorrect values for these fields. This usually happens for the transactions imported from external systems as this validation might have missed, or it could happen if the value specified for these fields is not valid. To fix the issue, follow the steps mentioned above and on the step 7 and update the correct values for Site and Warehouse fields in the **Transactions** and **SalesTransactions** tabs of the excel, if these tabs are present.
**Note:** Site and Warehouse fields are not available by default in Excel and can be added as explained here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel).


Error 2:
While processing the state Customer order created, generic exception encountered in retail statement [XXXXX] in the controller : Batch number [XXXXX] is not created for item number [XXXXX].
	
Mitigation:
This issue occurs because the batch number is setup as required for an item and it is not provided. To fix the issue, follow the steps mentioned above and on the step 7 and update the batch number for this item. 
**Note:** Batch number field is not available by default in Excel and can be added as described here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel).

## Issues during customer order invoicing 
After the customer orders are created, the statement posting next step is to attempt invoicing the customer orders. If the statement posting fails during invoicing the customer orders, then follow the below steps to resolve the issue.

	1. Navigate to failed statement and press the **Aggregated transactions** button under the **Execution details" group.
	2. Identify and select the aggregations failing to be invoiced, and click on **Delete customer order**.  This is a **required step** to ensure that the edit transactions information is used to generate new customer orders.
	3. Click on office icon on top right and select **Edit cash and carry transactions**. Note, this will automatically pull in all the cash and carry transactions that are a part of the current statement. 
	4. Download the file
	5. Once the file is downloaded, enable editing on the file and sign in
	6. Change the **Validation status** of transaction you need to fix to **None** or **Error** in excel. This is a **required step** to make any changes to the transaction.
	7. Identify the correct entity and field that needs to be modified
		a. If the field you are looking for is missing, then please get it in excel as described here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel)
	8. Change the value of fields and hit **Publish** on the excel
	9. In Statement forms, click on **Revalidate transactions** under Function group. Refer the below image.
	10. Post the statement

Some of the common issues that occur during order creation are as following:

Error 1: 
While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] Voucher []XXXXX Period for [XXXXX] does not exist. Posting Posting Sales order: XXXX Voucher [XXXXX] Fiscal year for 1/1/2000 does not exist.

Mitigation:
This issue occurs because the transaction date belongs to a fiscal period which is not open anymore. This usually happens when transactions have not been posted for a long time. To fix the issue, follow the steps mentioned above and on the step 7, navigate to the **Statement aggregations** tab of the excel and update the **Business date** field to a value that corresponds to an open fiscal period

Error 2: 
While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] Item: [XXXXX]Inventory dimension Location must be specified.
	
Mitigation:
This issue occurs because the Site and warehouse are setup to be required fields for the transactions and some of the transactions are missing values or incorrect values for these fields. To fix the issue, follow the steps mentioned above and on the step 7, update the correct values for Site and Warehouse fields in the **Transactions** and **SalesTransactions** tabs of the excel, if these tabs are present.
**Note:** Site and Warehouse fields are not available by default in Excel and can be added as described here [Add more fields to excel](https://learn.microsoft.com/en-us/dynamics365/commerce/add-fields-excel).

Error 3: 
While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] -> You must select a value in the [Field name] field in combination with the following dimensions values that are valid.
	
Mitigation:
This issue occurs because a required field for statement posting is missing a value. To fix the issue, follow the steps mentioned above and on the step 7, update the correct values for fields mentioned in the error message

Error 4: 
While processing aggregation state Sales order is invoiced for this aggregation. Transaction state Customer order invoiced, the invoice could not be found for the manually invoiced sales order for this aggregation [XXXXX].
	
Mitigation:
To fix this issue, follow the steps mentioned above and on the step 7, navigate to the **Statement aggregations** tab of the excel. Now check if **Business date** for the aggregation is not the same as the invoice date of manually invoiced sales order for this aggregation, then update the **Business date** to the invoice date of the order.

Error 5: 
While processing the state Payments posted, generic exception encountered in retail statement [XXXXX] in the controller : Posting results for journal batch number [XXXXX] Voucher [XXXXX] Voucher [XXXXX] Period for 1/1/2000 does not exist. Posting results for journal batch number [XXXXX] Voucher [XXXXX] Voucher [XXXXX] Fiscal year for 1/1/2000 does not exist.
	
Mitigation:
This issue is similar to the error 1 mentioned above. To fix the issue, follow the steps mentioned above and on the step 7, navigate to the **Transactions**, **Sales Transactions** and **Payment Transactions** tab and fix the **Business date** that corresponds to an open fiscal period.
