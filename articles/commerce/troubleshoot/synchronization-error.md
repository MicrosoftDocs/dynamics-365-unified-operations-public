---
title: Asynchronous order synchronization issues 
description: This article describes common reasons for asynchronous order creation failure in Microsoft Dynamics 365 Commerce, and provides troubleshooting steps to help system users and partners understand what might have gone wrong during order creation.
author: Shajain
ms.date: 11/29/2022
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2021-01-31

---

# Asynchronous order synchronization issues

[!include [banner](../../includes/banner.md)]

This article describes common reasons for asynchronous order creation failure in Microsoft Dynamics 365 Commerce, and provides troubleshooting steps to help system users and partners understand what might have gone wrong during order creation.

## Symptom

Asynchronous orders created from Dynamics 365 Commerce e-commerce or point of sale (POS) are not reflected in Commerce headquarters.

## Troubleshooting

There can be various reasons for order creation failure in headquarters, depending on which stage the order creation process fails. The following troubleshooting steps walk through the corresponding possible root causes of an order creation failure.

### Validate if the transaction related to the asynchronous order has reached headquarters

For e-commerce orders, in headquarters go to **Retail and Commerce \> Inquiries and reports \> Online store transactions**. If you have a confirmation number for the order, filter transactions by entering the confirmation number to **Channel reference ID**. If the confirmation number isn't available, filter the transactions by entering the customer account number. For POS orders, go to the **Store transactions** form and filter the records with the receipt number or the customer account number. If the transaction isn't found, run the **P-0001** channel transactions job, which syncs transactions from the channels to headquarters. If the **P-0001** fails, open a support ticket for the job failure. If the **P-0001** job succeeds but the transactions stil don't appear in headquarters, then open a support ticket with the relevant information.
 
### Check the synchronization status of the transaction if it's found in headquarters, but isn't linked with a sales order

If the transaction is present but the sales order is not created, then select the transaction and expand the "Synchronization status" of the transaction. Check the "Pending order status" property for this transaction. If the "Synchronize orders" job tried to synchronize this transaction, then you should see a "Succeeded" or "Failed" status. Else, it means that this transaction has not been attempted to be processed. If the status is "Succeeded", then the sales order field must be present on this transaction. If the status is "Failed", then you can view the error details in the "Order error details" property of the "Synchronization status" section. You can find more troubleshooting steps based on the common errors later in this guide. If the transaction has not been attempted to be synchronized, then you can click on the "Synchronize order" button at the top of this form to run the synchronization job now. Also, please validate if the Synchronize order job is scheduled to be run periodically so that these transactions can be created as orders in headquarters.

The following section provides information about some of the common errors and the proposed fix.

#### The "Order error details" fields shows "Number sequence has been exceeded"

Number sequence is used to create sales orders in headquarters. If all the numbers allowed from the number sequence are exhausted then the system throws this error. The number sequence used to create sales order can be found in the **Account receivables parameters \> Number sequences \> Sales order** form. To fix it, either fix the existing number sequence or replace it by a new number sequence.

#### The "Order error details" fields show "There must be a default payment service to process credit card transactions"

To fix this, confirm if there is a default payment defined in the Commerce headquarters. If not, it needs to be set. To do so, navigate to the **Accounts receivable* \> Payment setup \> Payment services** and make sure that the **Default processor for new credit cards** option is set to **Yes** for one payment service.
	
#### The "Order error details" fields show "Account structure for the combination, is not valid for ledger Corporate Main Account Shared"

The error text might vary but they share a common root cause related to the account structure configuration. For example, the errors should show up in the following formats:
- Posting results for journal batch number 0009656328 Voucher ARP-000959899 1.00 for voucher ARP-000959899 in company usrt will be posted as an overpayment or underpayment
- Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Account structure Account structure, for the combination 618160, is not valid for ledger Corporate Main Account Shared.
- Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Reported from company accounts usrt
- Posting results for journal batch number 0009656328 Voucher ARP-000959899 Posting has been canceled.
	
To fix these issues, review the account structures for accuracy. For more information, see [Configure account structures](/dynamics365/finance/general-ledger/configure-account-structures).
	
Once the problem is fixed, select the failed transaction and click the 'Synchronize order' button at the top for this transaction.
	
#### For any other type of errors which might need the transaction data to be fixed, the user can leverage the "Edit and audit" capability. 

Here is the link for related documentation: [Edit and audit transactions](https://learn.microsoft.com/en-us/dynamics365/commerce/edit-order-trans)

