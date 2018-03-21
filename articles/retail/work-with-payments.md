---
# required metadata

title: Payment methods in a call center
description: This topic covers the different payment methods you can use in a call center in Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: MCRSalesTableOrderHistory, MCRCCAuthManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 92163
ms.assetid: 8e738907-870b-466c-ab0c-07f4a4aa47f3
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment methods in a call center

[!include[banner](includes/banner.md)]

<!--I have deleted the entire document and re-written, it was referencing coupons and other weird things that were not even relevant, this document now actually covers payment method configuration for call center-->

In Dynamics 365 for Retail, users may enter payments against sales orders for customers when the **Enable order completion** setting on the call center channel configuration is enabled. This feature will ensure that all orders created by the call center channel users have a prepaid or pre-authorized payment within approved tolerances before the order can be released to order processing.  If the **Enable order completion** setting is turned off, call center users will not be able to use the payment processing features of call center, but can still apply prepayments to sales orders through standard Accounts Receivable functionality.

A company can define which payment methods are allowed for a call center channel as part of the channel configuration. The call center channel uses the same payment methods that are defined for the retail store channels.  

Payment methods for call centers are defined at **Retail>Channels>Call Centers>All Call Centers** Click **Payment methods** option in the **SET UP** menu to configure the allowed methods of payment for your channel.

When creating a payment method, there are 5 different payment method functions:

| Normal              | Use the Normal function on your payment method when defining methods of payment such as cash or vouchers.   When these types of payments are applied to a call center sales order, they will be posted immediately as pre-payments on the customer account.  The prepayment voucher is posted in the customer transaction history where it will later by systematically settled against the sales order invoice upon creation
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 92163
ms.assetid: 8e738907-870b-466c-ab0c-07f4a4aa47f3
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment methods in a call center

[!include[banner](includes/banner.md)]

<!--I have deleted the entire document and re-written, it was referencing coupons and other weird things that were not even relevant, this document now actually covers payment method configuration for call center-->

In Dynamics 365 for Retail, users may enter payments against sales orders for customers when the **Enable order completion** setting on the call center channel configuration is enabled. This feature will ensure that all orders created by the call center channel users have a prepaid or pre-authorized payment within approved tolerances before the order can be released to order processing.  If the **Enable order completion** setting is turned off, call center users will not be able to use the payment processing features of call center, but can still apply prepayments to sales orders through standard Accounts Receivable functionality.

A company can define which payment methods are allowed for a call center channel as part of the channel configuration. The call center channel uses the same payment methods that are defined for the retail store channels.  

Payment methods for call centers are defined at **Retail>Channels>Call Centers>All Call Centers** Click **Payment methods** option in the **SET UP** menu to configure the allowed methods of payment for your channel.

When creating a payment method, there are 5 different payment method functions:

| Normal              | Use the Normal function on your payment method when defining methods of payment such as cash or vouchers.   When these ty
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 92163
ms.assetid: 8e738907-870b-466c-ab0c-07f4a4aa47f3
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment methods in a call center

[!include[banner](includes/banner.md)]

<!--I have deleted the entire document and re-written, it was referencing coupons and other weird things that were not even relevant, this document now actually covers payment method configuration for call center-->

In Dynamics 365 for Retail, users may enter payments against sales orders for customers when the **Enable order completion** setting on the call center channel configuration is enabled. This feature will ensure that all orders created by the call center channel users have a prepaid or pre-authorized payment within approved tolerances before the order can be released to order processing.  If the **Enable order completion** setting is turned off, call center users will not be able to use the payment processing features of call center, but can still apply prepayments to sales orders through standard Accounts Receivable functionality.

A company can define which payment methods are allowed for a call center channel as part of the channel configuration. The call center channel uses the same payment methods that are defined for the retail store channels.  

Payment methods for call centers are defined at **Retail>Channels>Call Centers>All Call Centers** Click **Payment methods** option in the **SET UP** menu to configure the allowed methods of payment for your channel.

When creating a payment method, there are 5 different payment method functions:

| Normal              | Use the Normal function on your payment method when defining methods of payment such as cash or vouchers.   When these types of payments are applied to a call center sales order, they will be posted immediately as pre-payments on the customer account.  The prepayment voucher
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 92163
ms.assetid: 8e738907-870b-466c-ab0c-07f4a4aa47f3
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment methods in a call center

[!include[banner](includes/banner.md)]

<!--I have deleted the entire document and re-written, it was referencing coupons and other weird things that were not even relevant, this document now actually covers payment method configuration for call center-->

In Dynamics 365 for Retail, users may enter payments against sales orders for customers when the **Enable order completion** setting on the call center channel configuration is enabled. This feature will ensure that all orders created by the call center channel users have a prepaid or pre-authorized payment within approved tolerances before the order can be released to order processing.  If the **Enable order completion** setting is turned off, call center users will not be able to use the payment processing features of call center, but can still apply prepayments to sales orders through standard Accounts Receivable functionality.

A company can define which payment methods are allowed for a call center channel as part of the channel configuration. The call center channel uses the same payment methods that are defined for the retail store channels.  

Payment methods for call centers are defined at **Retail>Channels>Call Centers>All Call Centers** Click **Payment methods** option in the **SET UP** menu to configure the allowed methods of payment for your channel.

When creating a payment method, there are 5 different payment method functions:

| Normal              | Use the Normal function on your payment method when defining methods of payment such as cash or vouchers.   When these types of payments are applied to a call center sales order, they will be posted immediately as pre-payments on the customer account.  The prepayment voucher is posted in the customer transaction history where it will later by systematically settled against the sales order invoice upon creation of the invoice(s).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
| Check               | Use the Check function when defining a bank check instrument form of payment.  When using this type of method of payment on a sales order, the user will be required to enter the customers check number as part of the payment application processing.  Check payments will always be treated as prepayments when applied and just like the Normal payment function, these prepayment vouchers will be systematically settled against the future invoice(s) created for the order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Cards               | Card payment types can represent credit cards or gift cards – essentially any type of payment that requires entering in a card number that has been defined on the customer’s payment card.  When configuring this payment type, you must use the Card setup menu to define the card ID’s associated to this payment method.  At the time of order entry, users are able to determine if the card payment will be prepaid or not using the Prepay slider that will appear on the payment entry form.  Unless the business requires prepayments, the typical flow of a true credit card payment would be a two-step process with only an authorization obtained at the time of order entry, and then the settlement/collection of payment from the customer’s card at the time of invoicing.   For gift card payments, prepayment is advised as you will want the gift card balance to be reduced immediately to ensure the customer can not apply that same value elsewhere.                                      |
| Customer            | The Customer function on a method of payment implies that the payment will be applied to the customer’s credit limit or “on account”.  In Dynamics 365 for Retail, a customer can be assigned a credit limit which can be validated at the time of order entry.  Paying with a payment method linked to the customer function will create a liability against the customers account and indicate a balance due when the sales order invoices.   In these situations, customer’s will typically send in a payment in compliance with terms that have been given or a previous open credit voucher on the customer’s account may be applied to settle the amount due.   *Please note that even if you define this method of payment, it will not appear in your payment selection options in call center order entry unless you are working with a customer who has the **Allow on account** flag enabled on their customer record. This flag can be found on the **Payment Defaults** tab of the Customer record*. |
| Tender Remove/Float | The Tender Remove/Float payment function is not used by the call center and is only applicable when defining methods of payment used in a store channel by the POS application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | is posted in the customer transaction history where it will later by systematically settled against the sales order invoice upon creation of the invoice(s).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
| Check               | Use the Check function when defining a bank check instrument form of payment.  When using this type of method of payment on a sales order, the user will be required to enter the customers check number as part of the payment application processing.  Check payments will always be treated as prepayments when applied and just like the Normal payment function, these prepayment vouchers will be systematically settled against the future invoice(s) created for the order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Cards               | Card payment types can represent credit cards or gift cards – essentially any type of payment that requires entering in a card number that has been defined on the customer’s payment card.  When configuring this payment type, you must use the Card setup menu to define the card ID’s associated to this payment method.  At the time of order entry, users are able to determine if the card payment will be prepaid or not using the Prepay slider that will appear on the payment entry form.  Unless the business requires prepayments, the typical flow of a true credit card payment would be a two-step process with only an authorization obtained at the time of order entry, and then the settlement/collection of payment from the customer’s card at the time of invoicing.   For gift card payments, prepayment is advised as you will want the gift card balance to be reduced immediately to ensure the customer can not apply that same value elsewhere.                                      |
| Customer            | The Customer function on a method of payment implies that the payment will be applied to the customer’s credit limit or “on account”.  In Dynamics 365 for Retail, a customer can be assigned a credit limit which can be validated at the time of order entry.  Paying with a payment method linked to the customer function will create a liability against the customers account and indicate a balance due when the sales order invoices.   In these situations, customer’s will typically send in a payment in compliance with terms that have been given or a previous open credit voucher on the customer’s account may be applied to settle the amount due.   *Please note that even if you define this method of payment, it will not appear in your payment selection options in call center order entry unless you are working with a customer who has the **Allow on account** flag enabled on their customer record. This flag can be found on the **Payment Defaults** tab of the Customer record*. |
| Tender Remove/Float | The Tender Remove/Float payment function is not used by the call center and is only applicable when defining methods of payment used in a store channel by the POS application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |pes of payments are applied to a call center sales order, they will be posted immediately as pre-payments on the customer account.  The prepayment voucher is posted in the customer transaction history where it will later by systematically settled against the sales order invoice upon creation of the invoice(s).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
| Check               | Use the Check function when defining a bank check instrument form of payment.  When using this type of method of payment on a sales order, the user will be required to enter the customers check number as part of the payment application processing.  Check payments will always be treated as prepayments when applied and just like the Normal payment function, these prepayment vouchers will be systematically settled against the future invoice(s) created for the order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Cards               | Card payment types can represent credit cards or gift cards – essentially any type of payment that requires entering in a card number that has been defined on the customer’s payment card.  When configuring this payment type, you must use the Card setup menu to define the card ID’s associated to this payment method.  At the time of order entry, users are able to determine if the card payment will be prepaid or not using the Prepay slider that will appear on the payment entry form.  Unless the business requires prepayments, the typical flow of a true credit card payment would be a two-step process with only an authorization obtained at the time of order entry, and then the settlement/collection of payment from the customer’s card at the time of invoicing.   For gift card payments, prepayment is advised as you will want the gift card balance to be reduced immediately to ensure the customer can not apply that same value elsewhere.                                      |
| Customer            | The Customer function on a method of payment implies that the payment will be applied to the customer’s credit limit or “on account”.  In Dynamics 365 for Retail, a customer can be assigned a credit limit which can be validated at the time of order entry.  Paying with a payment method linked to the customer function will create a liability against the customers account and indicate a balance due when the sales order invoices.   In these situations, customer’s will typically send in a payment in compliance with terms that have been given or a previous open credit voucher on the customer’s account may be applied to settle the amount due.   *Please note that even if you define this method of payment, it will not appear in your payment selection options in call center order entry unless you are working with a customer who has the **Allow on account** flag enabled on their customer record. This flag can be found on the **Payment Defaults** tab of the Customer record*. |
| Tender Remove/Float | The Tender Remove/Float payment function is not used by the call center and is only applicable when defining methods of payment used in a store channel by the POS application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | of the invoice(s).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
| Check               | Use the Check function when defining a bank check instrument form of payment.  When using this type of method of payment on a sales order, the user will be required to enter the customers check number as part of the payment application processing.  Check payments will always be treated as prepayments when applied and just like the Normal payment function, these prepayment vouchers will be systematically settled against the future invoice(s) created for the order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Cards               | Card payment types can represent credit cards or gift cards – essentially any type of payment that requires entering in a card number that has been defined on the customer’s payment card.  When configuring this payment type, you must use the Card setup menu to define the card ID’s associated to this payment method.  At the time of order entry, users are able to determine if the card payment will be prepaid or not using the Prepay slider that will appear on the payment entry form.  Unless the business requires prepayments, the typical flow of a true credit card payment would be a two-step process with only an authorization obtained at the time of order entry, and then the settlement/collection of payment from the customer’s card at the time of invoicing.   For gift card payments, prepayment is advised as you will want the gift card balance to be reduced immediately to ensure the customer can not apply that same value elsewhere.                                      |
| Customer            | The Customer function on a method of payment implies that the payment will be applied to the customer’s credit limit or “on account”.  In Dynamics 365 for Retail, a customer can be assigned a credit limit which can be validated at the time of order entry.  Paying with a payment method linked to the customer function will create a liability against the customers account and indicate a balance due when the sales order invoices.   In these situations, customer’s will typically send in a payment in compliance with terms that have been given or a previous open credit voucher on the customer’s account may be applied to settle the amount due.   *Please note that even if you define this method of payment, it will not appear in your payment selection options in call center order entry unless you are working with a customer who has the **Allow on account** flag enabled on their customer record. This flag can be found on the **Payment Defaults** tab of the Customer record*. |
| Tender Remove/Float | The Tender Remove/Float payment function is not used by the call center and is only applicable when defining methods of payment used in a store channel by the POS application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
