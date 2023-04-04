---
title: Fix common posting issues by editing transactions
description: This article provides troubleshooting guidance to fix common statement posting issues that require editing transactions in Microsoft Dynamics 365 Commerce.
author: Shajain
ms.date: 04/04/2023
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2022-01-30
ms.search.form: RetailStatementTable_SOCreateFailed, RetailStatementTable_InvoiceFailed, RetailStatementTable_PaymentPosted

---

# Fix common posting issues by editing transactions
Error code: SYS103633, SYS328431

[!include [banner](../../includes/banner.md)]

This article provides troubleshooting guidance to fix common statement posting issues that require editing transactions in Microsoft Dynamics 365 Commerce.

## Description

Sometimes statement posting fails because the data in one or more transactions must be corrected before posting can proceed. Some of the scenarios where such data correction is needed are:
- The fiscal period mapping to the current transaction has been closed, so the transactions can't be posted.
- The transactions are created without values for required fields (for example, warehouse or batch number field values).

The data is corrected by editing the necessary transactions, and the steps that are required to edit the transactions vary based on which stage of the statement posting that an issue occurs. This article first lists the generic steps that are required to edit a transaction depending on the stage of statement posting, and then lists common errors that occur during the stages with the specific steps that are required to fix each issue.

> [NOTE]
> For information on the structure of the Excel files that are downloaded when editing transactions, see [Edit cash and carry transactions](../edit-cash-trans.md).

## Resolutions

### Issues during statement calculation

Statement calculation is a prerequisite step of the statement posting process. The most common error that occurs during this stage is a transaction validation failure, where the system display a warning message that some of the transactions couldn't be included in the statement because they failed validation.

#### Transaction validation failed

If the trickle feed feature is enabled, transactions must be validated before they can be included in a statement. This validation is done by running the **Validate store transactions** batch job. If transaction validation fails, follow these steps in Commerce headquarters to resolve the issue.

1. Go to the **Store financials** workspace and open the **Cash and carry validation failures** view. 
    ![Transaction validation errors](../media/Transaction_validation_errors.png)
1. Select the transaction, and then select **Validation errors** to identify the error.
    ![View validation errors](../media/View_validation_errors.png)
1. At the top right, select the Microsoft Office symbol, and then under **OPEN IN EXCEL**, select **Edit selected transaction**. 
    ![Edit transaction](../media/Edit_transaction.png)
1. Once the Excel file is downloaded, enable editing on the file and sign in.
1. Identify the correct entity and field that needs to be modified. If the field you're looking for is missing, to add the field, follow the instructions in [Add more fields to excel](../add-fields-excel.md).
1. Update the field values as needed, and then select **Publish** on the Excel spreadsheet.
    ![Publish changes](../media/Publish.png)
1. Run the **Validate store transactions** job again to validate the edited transaction.
1. If the transaction gets validated, then you can continue posting the statement without the newly validated transaction since it will be included in the next statement posting, or under the **Functions** group of the current statement, you can select **Clear statement** to free the transactions that were marked with the current statement and create a new statement.
	
### Issues during order creation

One of the steps of statement posting is to create customer orders by grouping one or more transactions. If statement posting fails before the customer orders are created, follow these steps in headquarters to resolve the issue.

1. Go to the failed statement.
1. At the top right, select the Microsoft Office symbol, and then under **OPEN IN EXCEL**, select **Edit cash and carry transactions**. This action automatically pulls in all the cash and carry transactions that are a part of the current statement.
    ![Edit the selected transactions](../media/Edit_selected_transactions.png)
1. Once the Excel file is downloaded, enable editing on the file and sign in.
1. In the Excel file, change the **Validation status** of transaction you need to fix to **None** or **Error**. Performing this step is required before making any changes to the transaction. 
    ![Change the validation status](../media/Change_validation_status.png)
1. Identify the correct entity and field that you need to modify. If the field you're looking for is missing, to add the field, follow the instructions in [Add more fields to excel](../add-fields-excel.md).
1. Update the field values as needed, and then select **Publish** on the Excel spreadsheet.
1. On the **Statement** form, under **Function**, select **Revalidate transactions**. 
    ![Revalidate transactions](../media/Revalidate_transactions.png)
1. Under the **Execution details**, select **Aggregated transactions**, and then select **Re-generate aggregation data** to clear the aggregations that were generated using the old values of the transaction. This step is required to ensure that the statement uses the edited transaction values to regenerate the aggregated values. 
    ![Aggregated transactions](../media/Aggregated_transactions.png)
1. Post the statement.

#### Common issues that occur during order creation

**While processing the state Customer order created, generic exception encountered in retail statement [XXXXX] in the controller : Inventory dimension Site is mandatory and must consequently be specified.**
	
**Resolution:** This issue occurs because the **Site** and **Warehouse** fields are configured to be mandatory for the transactions, and some of the transactions are missing values or have incorrect values for these fields. This error is generated for transactions imported from external systems where validation might have missed the issue, or if the values specified for the fields aren't valid. To fix the issue, follow the steps in the procedure above, and for step 7 update the correct values for the **Site** and **Warehouse** fields in the **Transactions** and **SalesTransactions** tabs of the Excel file (if these tabs are present).

> [!NOTE]
> The **Site** and **Warehouse** fields aren't available by default in Excel. To add them, follow the instructions in [Add more fields to excel](../add-fields-excel.md).

**While processing the state Customer order created, generic exception encountered in retail statement [XXXXX] in the controller : Batch number [XXXXX] isn't created for item number [XXXXX].**
	
**Resolution:** This issue occurs because the batch number is configured to be mandatory for an item but it isn't provided. To fix the issue, follow the steps in the procedure above, and for step 7, on the **Lines** or **Sales transaction** tabs of the Excel file, update the **Batch number** value for the item. 

> [!NOTE]
> The **Batch number** field isn't available by default in Excel. To add it, follow the instructions in [Add more fields to excel](../add-fields-excel.md).

### Issues during customer order invoicing

After customer orders are created, the next statement posting step is to attempt invoicing the customer orders. If the statement posting fails while invoicing the customer orders, follow these steps in headquarters to resolve the issue.

1. Go to the failed statement.
1. Under the **Execution details**, select **Aggregated transactions**.
1. Identify and select the aggregations failing to be invoiced, and then select **Delete customer order**.  Performing this step is required because it automatically deletes the aggregation data and ensures that the edit transactions information is used to generate new customer orders.
1. At the top right, select the Microsoft Office symbol, and then under **OPEN IN EXCEL**, select **Edit cash and carry transactions**. This action automatically pulls in all the cash and carry transactions that are a part of the current statement.
1. Once the Excel file is downloaded, enable editing on the file and sign in.
1. In the Excel file, change the **Validation status** of transaction you need to fix to **None** or **Error**. Performing this step is required before making any changes to the transaction. 
1. Identify the correct entity and field that you need to modify. If the field you're looking for is missing, to add the field, follow the instructions in [Add more fields to excel](../add-fields-excel.md).
1. Update the field values as needed, and then select **Publish** on the Excel spreadsheet.
1. On the **Statement** form, under **Function**, select **Revalidate transactions**. 
1. Post the statement.

#### Common issues that occur during order invoicing

**While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] Voucher [XXXXX] Period for [XXXXX] does not exist. Posting Posting Sales order: XXXX Voucher [XXXXX] Fiscal year for 1/1/2000 does not exist.**

**Resolution:** This issue occurs because the transaction date belongs to a fiscal period that is no longer open. This error is generated when transactions haven't been posted for a long time. To fix the issue, follow the steps in the procedure above and on step 7, go to the **Statement aggregations** tab of the Excel file and update the **Business date** field to a value that corresponds to an open fiscal period.

**While processing the state Payments posted, generic exception encountered in retail statement [XXXXX] in the controller : Posting results for journal batch number [XXXXX] Voucher [XXXXX] Voucher [XXXXX] Period for 1/1/2000 does not exist. Posting results for journal batch number [XXXXX] Voucher [XXXXX] Voucher [XXXXX] Fiscal year for 1/1/2000 does not exist.**
	
**Resolution:** This issue is similar to the previous error above. To fix the issue, follow the steps in the procedure above and on step 7, on the **Transactions**, **Sales Transactions**, and **Payment Transactions** tabs, fix the **Business date** value that corresponds to an open fiscal period.

**While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] Item: [XXXXX] Inventory dimension Location must be specified.**
	
**Resolution:** This issue occurs because the **Site** and **Warehouse** fields are configured to be mandatory for the transactions, and some of the transactions are missing values or have incorrect values for these fields. This error is generated for transactions imported from external systems where validation might have missed the issue, or if the values specified for the fields aren't valid. To fix the issue, follow the steps in the procedure above, and for step 7 update the correct values for the **Site** and **Warehouse** fields in the **Transactions** and **SalesTransactions** tabs of the Excel file (if these tabs are present).

> [!NOTE]
> The **Site** and **Warehouse** fields aren't available by default in Excel. To add them, follow the instructions in [Add more fields to excel](../add-fields-excel.md).

**While processing the state Customer order invoiced, generic exception encountered in retail statement [XXXXX] in the controller : Posting Posting Sales order: [XXXXX] You must select a value in the [Field name] field in combination with the following dimensions values that are valid.**
	
**Resolution:** This issue occurs because a required field for statement posting is missing a value. To fix the issue, follow the steps in the procedure above, and for step 7, update the correct values for fields mentioned in the error message.

**While processing aggregation state Sales order is invoiced for this aggregation. Transaction state Customer order invoiced, the invoice couldn't be found for the manually invoiced sales order for this aggregation [XXXXX].**
	
**Resolution:** To fix the issue, follow the steps in the procedure above, and for step 7, on the **Statement aggregations** tab of the Excel file, check if **Business date** value for the aggregation matches the invoice date of the manually invoiced sales order for this aggregation. If the values don't match, update the **Business date** value to the invoice date of the order.
