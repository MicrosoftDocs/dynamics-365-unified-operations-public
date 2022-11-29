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

Asynchronous orders created from Dynamics 365 Commerce e-commerce or point of sale (POS) aren't reflected in Commerce headquarters.

## Troubleshooting

There can be various reasons for order creation failure in headquarters, depending on which stage the order creation process fails. The following troubleshooting steps walk through the corresponding possible root causes of an order creation failure.

### Validate if the transaction related to the asynchronous order has reached headquarters

For e-commerce orders, in headquarters go to **Retail and Commerce \> Inquiries and reports \> Online store transactions**. If you have a confirmation number for the order, filter transactions by entering the confirmation number to **Channel reference ID**. If the confirmation number isn't available, filter the transactions by entering the customer account number. 

For POS orders, go to the **Store transactions** form and filter the records with the receipt number or the customer account number. If the transaction isn't found, run the **P-0001** channel transactions job, which syncs transactions from the channels to headquarters. If the **P-0001** job fails, open a support ticket for the job failure. If the **P-0001** job succeeds but the transactions still don't appear in headquarters, then open a support ticket with the relevant information.
 
### Check the synchronization status if the transaction is present in headquarters but isn't linked with a sales order

If the transaction is present in headquarters but the sales order hasn't been created, on the **Online store transactions** form, expand the **Synchronization status** FastTab. If the **Synchronize orders** job tried to synchronize this transaction, the **Pending order status** property should display a **Succeeded** or **Failed** status. If the status is **Succeeded**, then the sales order field must be present on this transaction. If the status is **Failed**, you can view the error details in the **Order error details** property on the **Synchronization status** FastTab. If neither of these statuses is shown, it means that no attempt has been made to process the transaction, in which case you can select **Synchronize order** at the top of the form to run the synchronization job. 

Ensure that the **Synchronize orders** job is scheduled to run periodically so that asynchronous transactions can be created as orders in headquarters.

The following sections provide information about some common errors and their proposed fixes.

#### The "Order error details" field displays the "Number sequence has been exceeded" error message

Number sequences are used to create sales orders in headquarters. If all the numbers allowed from a number sequence are exhausted, then the system generates this error message. The number sequence used to create sales orders can be found on the **Account receivables parameters \> Number sequences \> Sales order** form. To resolve the error, fix the existing number sequence or replace it with a new number sequence.

#### The "Order error details" field displays the "There must be a default payment service to process credit card transactions" error message

To resolve this error, confirm that there's a default payment defined in headquarters. If not, a default payment must be set. Go to **Accounts receivable \> Payment setup \> Payment services** and ensure that the **Default processor for new credit cards** option is set to **Yes** for one payment service.
	
#### The "Order error details" field displays an account structure error message

Account structure error message text may vary as shown in the following examples, but the errors share a common root cause related to the account structure configuration. 

- **Posting results for journal batch number 0009656328 Voucher ARP-000959899 1.00 for voucher ARP-000959899 in company usrt will be posted as an overpayment or underpayment**
- **Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Account structure Account structure, for the combination 618160, is not valid for ledger Corporate Main Account Shared**
- **Posting results for journal batch number 0009656328 Voucher ARP-000959899 Voucher ARP-000959901 Reported from company accounts usrt**
- **Posting results for journal batch number 0009656328 Voucher ARP-000959899 Posting has been canceled**
	
To resolve these errors, review the account structures for accuracy. For more information, see [Configure account structures](/dynamics365/finance/general-ledger/configure-account-structures).
	
Once the error is fixed, select the failed transaction and then select **Synchronize order** at the top of the form to run the synchronization job.
	
#### Other types of errors that may need the transaction data to be fixed

To resolve other types of errors that may need the transaction data to be fixed, you can use the "edit and audit transactions" capability. For more information, see [Edit and audit transactions](../edit-order-trans.md).

