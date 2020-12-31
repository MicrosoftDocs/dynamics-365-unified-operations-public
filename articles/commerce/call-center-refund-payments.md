---
# required metadata

title: Refund payment processing in call centers
description: This topic covers how payment refunds are generated through call centers when returns are created or when orders or order lines are cancelled.
author: hhainesms
manager: annbe
ms.date: 12/17/2020
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

# Refund payment processing in call centers

This topic covers how payment refunds are generated through call centers when returns are created or when orders or order lines are cancelled.

When creating a return order for a customer as a call center user in Dynamics 365 Commerce headquarters, the user will use the **Return order** form to create the initial Return Materials Authorization (RMA). The RMA defines which products the customer wishes to return or exchange and creates a linked return sales order with an order type of **Returned order**.  This linked returned order is used to track the postings of the returned inventory and any credit notes or payment refunds posted. 

If the call center channel has the **Enable order completion** setting turned on, the call center user creating the RMA will be required to execute the order completion processing flow by selecting the **Complete** function from the **Return order** form.  Selecting **Complete** provides the user with a calculated return summary that outlines the refund amount due and will also (if configured correctly) systematically create a refund payment line against the returned order.

Call center logic will determine the payment method for the refund payment line based on the original order's payment method. If the return order being created is not linked to an original order, a default payment method pulled from a system parameter will be applied.

## How a call center determines which payment method to apply to the return order

If the original payment method function was:

- **Normal** (cash) or **Check** - When creating a return order that references an original order that was paid by the normal or check payment types, the call center application will reference configurations in the **Call center refund methods** form. This form allows organizations to define, by order currency, how the customer will be refunded for orders originally paid by normal or check payment types. The **Call center refund methods** form also allows organizations to choose whether to send a system-generated refund check to the customer, or to create a customer account credit against the internal customer account balance. In these scenarios, call center logic will reference the currency of the return order and then create a refund payment line on the return sales order using the configured **Retail payment method** for that currency. Subsequently, an accounts receivable (AR) customer payment journal using the mapped AR payment method is tied to the currency.

The following image shows a configuration where a customer returning products from a sales order tied to the USD currency that was originally paid by normal or check payment types will be refunded by a system-generated refund check. The accounts receivable payment method of **REF-CHK** has been configured as a refund check payment type.

![Call Center refund method configurations for normal and check original payments](media/callcenterrefundmethods.png)

- **Credit card** - When creating a return order that references an original order that was paid by credit card, call center refund payments logic will apply that same original credit card to the return order. 
- **Loyalty card** - When creating a return order that references an original order that was paid by a customer loyalty card, call center refund payments logic will refund back to the same loyalty card.
- **Gift card** (Internal) - When creating a return order that references an original order that was paid for by a gift card issued from Dynamics 365 Commerce (internal gift card functionality), call center refund payments logic will refund back to that same original gift card number.
- **Gift card** (External) - When creating a return order that references an original order that was paid for by an external third-party gift card, call center refund payments logic will apply the default return payment method as defined on the **RMA/Return** header of the **Call center parameters** form.

If for any reason the original order payment type is unknown or if the original order was paid for with multiple payment methods, call center logic will revert to applying the default return **payment method** as defined on the **RMA/Return** header of the **Call center parameters** form.

The following image highlights the **Payment method** on the **RMA/Return** header of the **Call center parameters** form.

![Call center parameters RMA/Return header with the payment method drop-down menu highlighted](media/callcenterrefundparameters.png)

> [!NOTE]
> The refund processing rules above also apply to orders or order lines canceled in Commerce headquarters by a call center user. Any overpayments resulting from the cancellation of an order or specific order lines will generate refund payment lines using the same business rules defined above.

Typically a return order goes through a standard process of inventory receipt (or scrapping of inventory) and packing slip posting against the return order, followed by an invoice posting process of the return sales order. The return sales order is linked and systematically-generated as part of the return order creation process. In typical scenarios, payment refunds are not issued to customers until the return sales order has its invoice posted.   

### What happens when an invoice is posted on a return sales order

When posting the invoice on the return sales order:

The following scenarios explain what happens when an invoice is posted on a return sales order.

- If the refund payment on the return order is a credit card, additional logic is invoked at the time of invoice posting to call the payment processor to refund payment to the customer's credit card. A refund customer payment voucher is also created and posted systematically against the customer's account. This payment journal will be settled against the return order credit note voucher.

- If the refund payment to be issued is for the check payment type, a customer payment voucher with the AR payment method is created and must then be manually posted or printed before the payment voucher can be posted against the customer account. Users can process the refund check using the **Customer payment journal** form found on the **Accounts receivable** menu, or by using the specialized **Refund check processing** form found on the **Retail and commerce** menu.

- If the refund payment is issued for the internal gift card or loyalty card payment types, invoicing the return order creates and posts the refund payment voucher against the customer account. This invoicing step will also deposit the refund amount back to the customer's internally tracked gift card balance or loyalty points balance.   

- If the return sales order has a customer function payment method linked (for example, a customer account), credit limit validations are ignored when processing the payment and no payment voucher is created or posted in this context. When using a customer payment type on a return order, the credit note voucher created by the invoice posting process serves as the customer credit voucher to indicate a refund to the customer's AR balance.  

## Advance credit

When processing return orders as a call center user in a call center where the **Enable order completion** setting is turned on, an exception to the previously-outlined refund payment posting process can occur when the call center user creating the return order enables the **Advance credit** setting on the **RMA/Return** header. When the **Advance credit** setting is enabled, the payment refund occurs immediately upon successful submission of the return order using the **Submit** function on the **Return summary** form. When the **Advance credit** setting is enabled, the system will create a prepayment customer payment voucher for the return value immediately, even though the return sales order itself has not yet been invoiced. This can be used in situations where the organization needs to issue refunds to customers in advance due to customer service issues and does not want to require waiting for returned inventory to be received before refunding the customer.

## Replacement orders

When issuing a return order, it is possible to use the **Replacement order** function to generate a new sales order for the customer. This can be used in exchange scenarios.  Using the **Replacement order** function will create another sales order for the new items to be sent, but there will be a cross-reference link (located on the **RMA/Return** header) that links the replacement order, the RMA, and the returned sales order.

When processing payments on a replacement order, organizations have two choices:

- Refund the customer for the return order based on the original payment method and then collect a separate payment for the replacement order. No additional configuration is required to use this option.
- Enable the **Apply credit** setting on the **RMA/Return** header, which will systematically apply a customer payment method to both the return and replacement order. This option can be used to prevent the issuance of any external refund payment. This option also avoids any payment processing on the transaction and can be useful in situations where an even exchange is being processed and the organization would prefer to use the credit voucher generated when invoicing the return order to pay for the invoice generated by the replacement order. When using the **Apply credit** function, the organization must manually settle the credit note against the replacement order's invoice once both of these financial documents have been generated.

Enabling **Apply credit** is only applicable when the return order will be linked to a replacement order. When **Apply credit** is enabled, the customer payment method that will be used to systematically pay for the return and the exchange order is defined in the **Payment method** parameter on the **RMA/Return** header of the **Call center parameters** form. The only type of payment that can be configured in this parameter is the **Customer** function payment type.

> [!NOTE]
> Enabling the **Apply credit** setting for a return order that has no linked replacement order will have no effect on the return order payment logic, since this setting only applies to replacement orders.

![Call center parameters RMA/Return header highlighting the apply credits payment method](media/callcenterrefundparameters1.png)

> [!IMPORTANT]
> When creating replacement orders with an intent to use the **Apply credit** function, users should not execute the **Complete** operation on the return order prior to enabling the **Apply credit** setting. Once the **Complete** operation is executed, the refund payment is calculated and applied to the return sales order. Subsequent attempts to enable the **Apply credit** setting once a refund payment has already been calculated and applied will not trigger a recalculation of the refund payment, and the **Apply credits payment method** will not be applied. If it is required to use the **Apply credit** function in this context, the user must delete the replacement order and the RMA and start over and create a new RMA, ensuring to enable the **Apply credit** setting before executing the **Complete** operation.

## Payment overrides for call center returns

While call center logic will systematically determine the refund payment method based on logic outlined above, there may be times where a user wants to override these payments. For example, a user may choose to edit or remove existing refund payment lines and apply new payment lines. Changing the system-calculated refund payment is only allowed for users with the proper override permissions. These user permissions can be configured on the **Override permissions** form found in the **Call center setup** menu. For a user to be able to perform a refund payment override, ensure that the user is linked to a security role where the **Allow alternate payment** configuration has been enabled on the **Override permissions** form.

![Call center user override permissions](media/overridepermissions.png)

As an alternative option, an organization can enable the **Allow payment override** setting on the **RMA/Return** header. When this configuration is enabled, a **Security override code** must be defined. The security code is an alphanumeric code that must be managed externally since once it is set users cannot view the defined code in Commerce headquarters. The security code is meant to be known by only a few key trusted people within an organization. When the **Allow payment override** setting is enabled, if the user attempting to change the method of payment on a return order does not have the proper role permissions, the user will alternatively be offered an option to enter the **Security override code**. If the user doesn't know this code, or if they are not able to have a manager or supervisor enter this code into the form for them, the user will not be able to override the return payment method.

> [!NOTE]
> If the override code is lost or forgotten, an organization will need to reset it by defining a new security override code in the **Security override code** field on the **Call center parameters** form.
 
![Call center refund payment override parameters](media/overridepaymentparameter.png)

> [!IMPORTANT]
> Before attempting to override refund payments with credit card payment types, an organization should verify that their credit card processor allows for unlinked returns. Many processors require refunds to be posted back to the original card and an attempt to issue a refund to a card that has no previous captures may result in posting failures with the processor.

## Additional resources

[Payment methods in call centers](work-with-payments.md)
