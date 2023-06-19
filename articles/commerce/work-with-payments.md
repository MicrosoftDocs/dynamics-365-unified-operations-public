---
# required metadata

title: Payment methods in call centers
description: This article describes the various payment methods that you can use in a call center in Dynamics 365 Commerce.
author: josaw1
ms.date: 03/28/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MCRSalesTableOrderHistory, MCRCCAuthManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: 8e738907-870b-466c-ab0c-07f4a4aa47f3
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment methods in call centers

[!include [banner](includes/banner.md)]

In Dynamics 365 Commerce, the configuration of the call center channel includes a setting that is named **Enable order completion**. This setting helps guarantee that all orders that users of the channel create are released to order processing only if they have a prepaid or pre-authorized payment that is within approved tolerances. If the **Enable order completion** setting is turned on, call center users can enter payments against sales orders for customers by using the payment processing features of Call center. If the setting is turned off, call center users can't use the Call center payment processing features, but they can still apply prepayments to sales orders by using standard Accounts receivable functionality.

As part of the channel configuration, a company can define the methods of payment that are allowed for a call center channel. The call center channel uses the same payment methods that are defined for the store channels.

To configure the payment methods for a call center channel, go to **Retail and Commerce** \> **Channels** \> **Call centers** \> **All call centers**, and then, on the **Set up** menu, select the **Payment methods** option.

When you create a payment method, there are five payment method functions that you can assign.

| Function            | Description |
|---------------------|-------------|
| Normal              | Use the **Normal** function on your payment method when you define payment methods such as cash or vouchers. When these types of payments are applied to a sales order in the call center, the **Prepay** flag will default to **Yes**. This will immediately post a prepayment voucher to the customer account when this order is submitted. Users may change the **Prepay** flag to **No** if desired so that the payment voucher is not created until invoice posting. The prepayment voucher is posted in the customer transaction history, where it will be systematically settled against the invoice for the sales order. |
| Check               | Use the **Check** function when you define a bank check instrument as a form of payment. When this type of payment is applied to a sales order, the user must enter the customer's check number as part of the payment application processing. Check payments are always treated as prepayments when they are applied and payment vouchers are created immediately upon order submission. These prepayment vouchers will be systematically settled against the invoices that are created for the order. |
| Cards               | Card payment types represent any type of payment that requires entry of a card number that has been defined on the customer's payment card. Examples include credit cards and gift cards. When you configure these types of payments, you must use the **Card setup** menu to define the card IDs that are associated with this payment method. At the time of order entry, users can indicate whether the card payment will be prepaid, by using the **Prepay** option that appears on the payment entry page. Unless the business requires prepayments, the typical flow of a true credit card payment is a two-step process, where authorization is obtained at the time of order entry, and then payment is settled and collected from the customer's card at the time of invoicing. For gift card payments, prepayment is recommended, because the gift card balance should be reduced immediately so that the customer can't apply that same value somewhere else. |
| Customer            | The **Customer** function on a payment method implies that the payment will be applied to the customer's credit limit or put "on account." In Commerce, a customer can be assigned a credit limit that can be validated at the time of order entry. Payments that are made by using a payment method that is linked to the **Customer** function create a liability against the customer's account. Then, when the sales order is invoiced, a balance due is shown. In these situations, customers typically send a payment, according to terms that have been given. Alternatively, a previous open credit voucher on the customer's account can be applied to settle the balance that is due. Note that even if you define this payment method, it doesn't appear among the payment selection options in call center order entry unless the **Allow on account** flag is set on the customer record for the customer that you're working with. This flag is found on the **Payment Defaults** tab of the customer record. |
| Tender Remove/Float | The **Tender Remove/Float** function isn't used by the call center. It's applicable only when you define the methods of payment that the point of sale (POS) application uses in a store channel. |

As methods of payment are defined, they should be linked to a ledger or bank account. If you omit this step, users will receive errors when they try to save the payment type.

## Refund payment methods

For refund processing scenarios, Call center also uses some of the payment methods that are defined in Accounts receivable. To configure these payment methods, go to **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Call center refund methods**. You must complete this configuration to process refund checks to customers. For example, if a customer originally paid for an order by using cash or a check, the user might want to send the customer a refund check through Accounts receivable. In this case, the cash and check payment types in the call center must be mapped to the correct payment method in Accounts receivable to help guarantee that the refund is correctly processed.

Additionally, if a user is processing a return order as a call center user in Commerce, but the user can't link the return to an original sale, the **Return** payment method must be defined in the Call center parameters. Go to **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Call center parameters**, and then, on the **RMA/Return** tab, in the **Payment method** field, make sure that a payment method is defined. The payment method will be the payment method that is used for refunds. Typically, it will be defined as either a check method or a customer account method.


[!INCLUDE[footer-include](../includes/footer-banner.md)]