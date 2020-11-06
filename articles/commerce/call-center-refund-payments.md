---
# required metadata

title: Call Center refund payments
description: This topic is a reference guide regarding how payment refunds are generated through call center when returns are created or order/order lines are canceled
author: hhainesms
manager: annbe
ms.date: 11/6/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: hhaines
ms.search.validFrom:
ms.dyn365.ops.version: 
---

# Call Center Refunds  - Payments processing reference

When creating a return order as a call center user in Commerce HQ, the user will have the ability to set up the RMA which outlines which products the customer wishes to return or exchange.   If the call center channel has ‘enable order completion’ turned on, the return order will go through a Complete/Submit flow of processing which allows for a calculation of return order totals and allows for the configuration of the refund payments.

Call center  logic will determine the payment method for the refund systematically based on the original order’s payment.  If the RMA being created is not linked to an original order, a default payment method will be applied.

How call center determines which payment method to apply to the return order based on the original order payment method

If the original payment method was:

- Normal function (e.g. Cash), call center will reference configurations in the Call Center Refund Methods form.  Based on the currency code of the order, the refund can either be issued as a refund check, or a customer account credit.   Call center logic will create the customer payment journal using the AR payment method as defined in the Call Center Refund Methods form.  Once the payment journal is created, users must utilize standard Dynamics 356 Finance accounts receivable payment posting functions to complete the creation/posting of the refund payment voucher.

![Call Center refund method configurations for normal and check original payments](media/callcenterrefundmethods.png)

- Check function, see Normal function rules above.  The same rules will be used by call center when the original order being returned was paid for by check
- Credit Card, call center will refund back to the original credit card
- Loyalty Card, call center will refund back to the loyalty card
- Gift Card (Internal), call center will refund back to the original gift card
- Gift Card (External) ?? Ruben?

If for any reason the original order payment type is unknown or if the original order was paid for with multiple payment methods, call center logic will revert to applying a refund payment method to the return order based on the configuration of the Return Payment Method parameter found in Call Center Parameters form:

![Call Center refund default refund payment parameters](media/callcenterrefundparameters.png)

> [!NOTE]
> The above refund processing rules also apply to orders or order lines canceled in Commerce Headquarters by a call center user.  Any overpayments resulting from the cancelation of the order or specific order lines will be generate refund payment lines using the same business rules defined above.

Typically, a return order goes through a standard process of inventory receipt (or scrapping of inventory) and packing slip posting against the RMA, followed by an invoice posting process of the return sales order (which is linked and is systematically generated as part of the RMA creation process).   In typical scenarios, payment refunds are not issued to customers until the return sales order has it’s invoice posted.  At that time, any configured payments for the return sales order will get posted as payment vouchers.  

When posting the invoice on the return sales order:

- If the refund payment is a credit card, additional logic is invoked to call the payment processor.  

- If the refund payment is a check, a check payment voucher is created and must be manually posted/printed before the payment voucher is created against the customer account.  Users may process the refund check using the Customer Payment Journal form found in the Accounts Receivable Menu, or they may utilize the specialized Refund Check Processing form found in the Retail and Commerce menus.

- If the refund payment is against an internal gift card or loyalty card, invoicing the return order not only creates the payment voucher, but will also deposit the refund amount back to the customers gift card balance or loyalty points balance.   

- If the refund payment is an external gift card??? Ruben?

- If the return sales order has a Customer payment method linked (e.g. customer account) credit limit validations are ignored and no payment voucher is created (the credit note voucher created by the invoice posting process serves as the customer credit voucher to indicate a refund to the customer’s AR balance).  

## Using Advanced Credit
When processing return orders as a call center user, an exception to the previously outlined refund payment posting process occurs when the user creating the RMA selects, the Advanced Credit option on the RMA header.  When Advanced Credit is selected, the payment refund will occur immediately upon successful submission of the RMA using the Submit function on the return order recap form.   A prepayment payment voucher for the return value will be created and posted/processed immediately, even though the return sales order itself has not yet been invoiced.   This can be used in situations where the organization needs to issue refunds to customers in advance due to customer service issues and does not wish to require waiting for inventory receipt before refunding the customer.

## Replacement Orders
When issuing an RMA, it is possible to use the Replacement Order function to generate a new sales order for the customer.  This can be used in exchange scenarios.  Replacement order will create another sales order for the new items to be sent, but there will be a cross-reference link (which can be found in the RMA header) linking the replacement order to the return.

When creating a replacement order, from a payment processing perspective, organizations have two choices:

- They can choose to refund the customer for the return order and collect a separate payment for the replacement order (no additional configuration is required for this option)
- They can choose to apply a Customer Account payment method to both the return and replacement order.   This avoids any payment processing on the transaction and it is assumed that the credit note generated by the return order invoice will be manually settled to pay for the replacement order sales invoice.   

If the organization wishes to apply customer credits to the replacement order and not issue refund payments or collect new payments for replacement orders, the user can enable the Apply Credits setting on the RMA header.   Enabling this setting is only applicable when the RMA will be linked to a replacement order.  When this setting is enabled, the system will apply a Customer payment method to both the return and replacement orders.    Currently the application references the Payment methods parameters in configured in the RMA/Return tab of the Call Center Parameters form to determine which Customer payment method to apply.   

![Call Center refund default refund payment parameters](media/callcenterrefundparameters.png)

> [!NOTE]
> Even though the application currently allows organizations to define any payment method in the Payment Methods field of Call Center RMA/Return parameters, if  the organization wishes to use the Apply Credits functionality – they must configure this parameter with a Customer function payment type.   Configuring any other payment type in this parameter will result in out of balance financial postings.

> [!NOTE]
> Enabling the Apply Credit toggle on an RMA that has no linked replacement order will have no effect on the return order payment logic as this setting should only be used for replacement orders.

> [!IMPORTANT NOTE]
> When creating replacement orders with an intent to use Apply Credits, users should not click the Complete operation on the RMA prior to enabling the Apply Credits setting.  If this is done, the refund payment will be already have been calculated using the Apply Credits as disabled logic, later attempts to enable the Apply Credit setting once this refund payment has already been calculated will not trigger a recalculation of the refund payment and therefore the customer payment type will not be applied. If it is required to use apply credits in this context, the user must delete the replacement order and the RMA and start over and create a new RMA, making sure to enable Apply Credits, before clicking the Complete operation.

## Payment Overrides for Call Center returns
While call center logic will systematically determine the refund payment method based on logic outlined earlier in this document, there may be times where a user would like to override these payments.   Users may choose to edit or remove existing refund payment lines and apply new payment lines.   Changing the system calculated refund payment is only allowed by users with the proper override permissions.    These user permissions can be configured on the Override Permissions form.   For a user to be able to perform a refund payment override, ensure the user is linked to a security role where the Allow alternate payment configuration has been enabled in the Override permissions form.

![Call Center user override permissions](media/overridepermissions.png)

As an alternative option, the organization can turn on the Allow payment override configuration in Call Center parameters.  When this configuration is enabled, a Security override code must be defined. This is an alphanumeric code that must be managed externally as once it is set users can not view the defined code through the application.   This is a code that is meant to be known by only a few key trusted people within the organization.   When this setting is enabled, if the user is attempting to change the method of payment on a return order but does not have the proper role permissions, the user will alternatively be offered an option to enter the security override code.  If the user doesn’t know this code, or if they are not able to have a manager or supervisor enter this code into the form for them, the user will not be able to override the return payment method.
 
![Call Center refund payment override parameters](media/overridepaymentparameter.png)

> [!NOTE]
> If the code is lost or forgotten, an organization can simply define a new security override code to reset the code.

> [!NOTE]
> Before attempting to use this capability, ensure you verify that your credit card processor allows for unlinked returns.  Many processors require refunds to be posted back to the original card and an attempt to issue a refund to a card that has no previous captures may result in posting failures with the processor.
