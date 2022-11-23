---
title: Asynchronous order synchronization issues 
description: This article provides the common reasons for asynchronous order creation failure and troubleshooting steps which can help the system users and partners to understand what might have went wrong during order creation.
author: Shajain
ms.date: 03/11/2021
ms.topic: Troubleshooting
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18
ms.custom: 
ms.assetid: 
ms.search.industry: Retail
---

# Asynchronous order synchronization issues

[!include [banner](../../includes/banner.md)]

This article provides the common reasons for asynchronous order creation failure and troubleshooting steps which can help the system users and partners to understand what might have went wrong during order creation.

## Symptom

The asynchronous orders created from Ecommerce or Point of Sale (POS) do get created in Commerce headquarters (HQ) application

## Troubleshooting

There could be various reasons for the order creation failure in HQ depending at what stage the order creation process fails. Let us look at the troubleshooting steps and the corresponding possible root causes of the failure.

- Validate if the transaction related to the asynchronous order has reached HQ
For Ecommerce orders, navigate to the Online store transactions form and if the customer has provided the Confirmation number of their order, then add a filter for "Channel reference ID" property and enter the "Confirmation number" provided by the customer. If the confirmation number is not available, then the user can filter the transactions by the "Customer account" number to find any transactions. Similarly, for POS orders, navigate to the Store transactions form and filter the records with the "Receipt number" or the "Customer account" number. If the transaction is not found then please try running the P-0001 "Channel transactions" job again which syncs the transactions from the channels to the HQ. If the P-0001 failed then log a support ticket for the job failure. If the job succeeds but still the transactions do not show up in HQ, then log a support ticket with this information.

- Assuming the transaction is found in HQ, but it is not linked with a sales order
If the transaction is present but the sales order is not created, then select the transaction and expand the "Synchronization status" of the transaction. Check the "Pending order status" property for this transaction. If the "Synchronize orders" job tried to synchronize this transaction, then you should see a "Succeeded" or "Failed" status. Else, it means that this transaction has not been attempted to be processed. If the status is "Succeeded", then the sales order field must be present on this transaction. If the status is "Failed", then you can view the error details in the "Order error details" property of the "Synchronization status" section. You can find more troubleshooting steps based on the common errors later in this guide. If the transaction has not been attempted to be synchronized, then you can click on the "Synchronize order" button at the top of this form to run the synchronization job now. Also, please validate if the Synchronize order job is scheduled to be run periodically so that these transactions can be created as orders in HQ.

The following section provides information about some of the common errors and the proposed fix.
1. The "Order error details" fields shows **'Number sequence has been exceeded'**
	Number sequence is used to create sales orders in HQ. If all the numbers allowed from the number sequence are exhausted then the system throws this error. The number sequence used to create sales order can be found in the **"Account receivables parameters"** -> **"Number sequences"** -> **Sales order** form. To fix it, either fix the existing number sequence or replace it by a new number sequence.
	
2. The "Order error details" fields shows **'There must be a default payment service to process credit card transactions.'**
	To fix this, confirm if there is a default payment defined in the Commerce headquarters. If not, it needs to be set. To do so, navigate to the **Accounts receivable** > **Payment setup** > **Payment services** and make sure that the **Default processor for new credit cards** option is set to **Yes** for one payment service.
	
3. The "Order error details" fields shows **'Account structure for the combination, is not valid for ledger Corporate Main Account Shared.'**
	The error text might vary but they share a common root cause related to the account structure configuration. For example, the errors should show up in the following formats:
    - Posting results for journal batch number 0009656328 Voucher ARP-000959899 1.00 for voucher ARP-000959899 in company usrt will be posted as an overpayment or underpayment
    - Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Account structure Account structure, for the combination 618160, is not valid for ledger Corporate Main Account Shared.
    - Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Reported from company accounts usrt
    - Posting results for journal batch number 0009656328 Voucher ARP-000959899 Posting has been canceled.
	
	To fix these issues, review the account structures for accuracy. Please follow the below link for the official documentation about it: [Configure account structures]( https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/configure-account-structures)
	
	Once the problem is fixed, select the failed transaction and click the 'Synchronize order' button at the top for this transaction.
	
4. For any other type of errors which might need the transaction data to be fixed, the user can leverage the "Edit and audit" capability. Here is the link for related documentation: [Edit and audit transactions](https://learn.microsoft.com/en-us/dynamics365/commerce/edit-order-trans)

