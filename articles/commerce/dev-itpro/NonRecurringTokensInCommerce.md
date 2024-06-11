---
title: Nonrecurring payment tokens in Commerce
description: This article describes how to configure and operate payment processing with nonrecurring payment tokens in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 06/11/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2024-04-10
ms.custom: 
  - bap-template
---

# Nonrecurring payment token usage in Commerce

[!include [banner](../includes/banner.md)]

This article describes how to configure and operate payment processing with nonrecurring payment tokens in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce payment processing actions have historically saved payment card tokens to use for downstream sales order changes, resubmission of authorizations coming up to expiration, and for 'card on file' uses for future customer orders. With direct configurations, these card payment tokens carry a 'recurring detail' reference to use in an unscheduled merchant-initiated transaction. In version 10.0.40, payment processing is updated to provide the ability to operate payments without a recurring card token saved against the customer. This ability applies to online stores, Call Center orders, and Point-of-Sale (POS) customer orders requiring future shipment. This article will detail configuration and operation of payment processing with non-recurring payment tokens.

## Key terms

| Term | Description |
|---|---|
| Token | A referenced XML blob in the Dynamics 365 system that stores payment references for transactional purposes. |
| Recurring | Reference to a card payment token type, recurring if intended to re-use at a future time, either in a set cadence or in an unscheduled fashion. Non-recurring refers to a non-reusable token or the absence of storing a recurring token. |
| Card on file | A saved card reference token that is agreed upon for future use in the Dynamics 365 system or the payment gateway, and that is specific to a customer's account. |

## Prerequisites

To set up an environment for non-recurring payment token usage, the following elements are required:
- Enable  **Enable use of non-recurring tokens in Commerce** in **System administration>Workspaces>Feature management**. 
  - This feature also requires the **Extensibility to support incremental credit card capture** and **Restrict Payment Token usage to Order context** features to be enabled for the environment.

- For online channels to support non-recurring tokens, in Site Builder, the **Site settings \> Extensions \> Card and checkout** section must have the **Enable single payment authorization checkout** setting enabled.

- For customers using the **Dynamics 365 Payment Connector for Adyen**, in the Adyen Portal, under the **Settings>Checkout settings** section, the **Tokenization** field's **Recurring** setting must be **disabled** when using non-recurring tokens in Commerce. Note that this setting is at the merchant account level and affects all transactions under the merchant account. If enabled, it forces a recurring detail reference for all transactions against the merchant account. If disabled, the Commerce Adyen connector will set recurring details as needed for transactional situations described below. Note that the Adyen **Recurring** setting is required to be **enabled** to operate with the Commerce **Dynamics 365 Payment Connector for Adyen** if the **Enable use of non-recurring tokens in Commerce** feature management flag is **disabled** for the Commerce environment.

## Authorization patterns with non-recurring payment tokens

Commerce payment authorizations are used to ensure a shopper's credit is available for the amount of a transaction before the funds are 'captured', or finalized as a charge on the shopper's card or digital wallet. For customer orders where items from the order are still being picked, packed, and invoiced against- the 'capture' is triggered on the invoicing action during the order management process. In the time between order placement (the credit amount is authorized as available by the card or wallet issuer) and capture (the shopper's credit is charged), the transaction within Commerce is maintained as an authorization state. Authorizations against the card or wallet issuer can expire if held open for a specific amount of time. The expiry timeframe depends on the issuer and is unknown to Commerce or the payment gateway. Typically the expiration is determined when a request to capture is sent and the payment gateway passes back the issuer's 'decline'. To avoid attempting to capture against an expired authorization, the Commerce system tracks a set of parameters to consider an authorization expired. When a recurring card payment token is used against an order, there are some scenarios within the system which a new merchant initiated transaction will be performed against the order using the recurring token to get a new authorization. With the enablement of the **Enable use of non-recurring tokens in Commerce** feature management setting, any customer order which does not have a recurring token associated will require a new payment authorization be collected from the shopper to enable progression of the order. These details and scenarios are expanded on further in the sections below.

When using non-recurring tokens in Commerce, the following scenarios will still require a recurring detail payment token in order to obtain an authorization:

- Future Orders
- Installments
- Unlinked refunds

In these scenarios, a message will be displayed to the inputting user to inform that a recurring token payment will be required. Please align training for these processes with your company's compliance policy for saving payment tokens.

### Authorization Expiration Settings in Commerce

Dynamics 365 Commerce tracks an internal setting to consider credit card and digital wallet authorizations expired. This is a protective setting to avoid an attempted funds capture against an authorization that the issuer may consider expired and invalid. 

An environment default setting is set at the **Accounts receivable \> Setup \> Accounts receivable parameters \> Credit Card** section, in the **Number of days before expired** attribute. Note that **Credit card authorization** is also set to "Yes" in normal Commerce payments setup. 

In addition to this environmental setting, the **Electronic payment types** per store can also have their own expiration in days setting applied. In headquarters, navigate to the store to configure and under the **Set up** fast tab, select the **Payment methods** item. With **Cards** (or the desired payment method) selected, click the **Electronic payment setup** button in the menu. Within the **General** tab, set the **Pre-authorization duration in days** for each of the selected electronic payment types. This setting will also show in the record of the **Retail and Commerce \> Channels \> Call centers \> Call center credit cards \> Authorization management** screen for reference against a specific pending authorization.

The **Pre-authorization duration in days** setting is used as the primary attribute to measure an authorization's expiration for the transaction based on the payment method used by the shopper. If this value is not set, the system will default to the **Number of days before expired** setting in the Accounts receivable parameters section.

### Monitoring expired authorizations

Credit card authorizations that have expired in the system will return the payment tracking back to 'Pending Authorization', with the order being placed on hold with the **Do Not Process** header attribute being set to "True" in the Sales Order header.  In Commerce headquarters, users can monitor these expired authorizations in the **Retail and Commerce \> Channels \> Call centers \> Call center credit cards \> Authorization management** page. Set the page's **Status** filter to 'Pending Authorization' to see a list of pending authorizations. The record's **Status** will note "Open order" and the authorization response section's **Expired** field will show 'Yes'.

When a record is selected, details for the Customer account, Sales order, and payment status are shown. The user can also view the Credit card details and authorization response details for additional context on the declined authorization. To collect a new payment, select the Sales Order number link to be directed to the sales order and process a new payment line against the order's **Balance**. If previously authorized against, the balance will reflect the amount of any authorized but expired (or any open, unapplied) payment lines.

## Payment flow updates using non-recurring payment tokens

Once enabled, the use of non-recurring tokens will have specific payment flow patterns depending on the operating channel. This section will review each channel's patterns specifically.

### Saved card on file

A payment card token can continue to be saved against a customer record for scenarios that require a card on file and with proper agreement with the customer to save the card for future usage. 

In headquarters, customer records, as selected within the **Accounts receivable \> Customers** page, have a **Credit cards** page link under the **Set up** fast tab within the **Customer** menu. Here, the **Customer credit cards** page offers the ability to view, add, or delete credit cards stored against the customer.

To add a new card, ensure a default payment connector is configured in the **Accounts receivable \> Payments setup \> Payments services** page. For the Adyen connector, you can refer to [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md). In **Customer credit cards**, select **New**. The **New customer credit card** form will be presented. 

In the credit card input form, enter the customer's card details and Billing address information. Click **OK** to save the card information. The card will now be available in the customer's credit cards list. 

>[!WARNING]
>Cards must only be saved with the customer's agreement per your company's compliance practices and customer terms and agreements.

A saved card on file can be used for future Sales Order references in Call Center. This process is reviewed further in the  [Call Center payments](#call-center-payments) section below.

To delete a card on file, in the same **Customer credit cards** form, select the card to be deleted and select the **Delete** button. The credit card reference will now be unavailable to be selected in a future sales order payment form in Call Center.

### Call Center payments

Call center is used to create or edit existing sales orders in Commerce. When submitting a payment in call center, a payment form is presented to accept payment details. Within the **Enter customer payment information** form, for credit card payment methods, the call center associate must fill out the form with the Payment method information. Here, the call center associate has two options to enter the card number information. First is the **Number** drop down can be used to select from a list of saved cards on file for the customer account of the sales order. This is a list of recurring payment card tokens previously saved against the customer record (referencing from the card holder info and the last 4 digits of the saved card's information). The other option is to select the plus sign button, launching the **New customer credit card** form. This form renders the configured payment service provider's payment acceptance page within an iFrame. The entered credit card information is entered directly with the payment service provider. The lower **Billing Address** section is Commerce system-specific, and can be entered both to include with the payment request to the payment gateway as well as to save the billing address information against the customer's record as an **address** entry. On the lower end of the form, when the **Restrict Payment Token usage to Order context** feature is enabled in feature management, a **Save payment information** checkbox is made available to the configured call center associate to allow saving this entered payment information as a recurring token for future reference in the **Number** drop down, and viewable as a listed reference in the **Customer \> Customer credit cards** page. The **Save payment information** checkbox should only be selected with agreement from the shopper, as defined by your business compliance processes. The **View disclaimer** button can be selected to see a dialogue with this similar suggestion. 

System admins can use the **Allow customer card on file** option in the **Call center parameter** page in Commerce headquarters to allow ("Yes") or hid ("No") the **Save payment information** checkbox option in the payment form. Refer to the [Limit payment token usage](limit-token-usage.md) article for additional details.

#### Future orders

Commerce authorizations support processing future orders when a shipment is set for a date in the future that may extend beyond the typical authorization validity period. Having the system request an authorization at a future time requires a saved card on file (recurring payment token) to be saved against the customer or the sales order. 

In **Retail and Commerce \> Channel setup \> Call center setup \> Call center parameters**, go to the **Payment** section and under the **Credit Card Authorizations** header, the **Future orders** option must be set to **Yes**. The **Delay authorization** setting can also be set to **Yes** to wait until the ship date reaches within the following configured **Future order days** setting to authorize. For example, with **Future order days** set to '7', the order will be authorized as the date reaches 7 days ahead of the ship date. 

When set, sales orders built in Call center with the **Requested ship date** are compared against the **Future order days** date, and authorization is requested by the Authorization Resubmit job when falling into the date range of these setting's difference. 

#### Editing orders in Call center

In Call center or in POS, an order can be recalled and edited. Changes to the order caused by an active change, like a product line addition or removal, while the order's payment is in an active authorized state will result in the payment connector attempting to adjust the authorization. The authorization adjustment requests the new authorization total against the pre-existing original authorization. If approved, the authorization will be adjusted in the Commerce system. If declined, the original authorization will be considered declined and a new payment will be required to complete the transaction.

>[!WARNING]
>Currently, the system will not attempt a pure authorization extension to extend the authorization period. This operation may result in a higher rate of declines from issuers. This functionality will be reviewed for future iterations when webhook support can handle asynchronous operations.

### Online storefront payments

For online storefront payments using credit cards or digital wallets, the payments module processes an online shopper's entered payment information. When the **Enable use of non-recurring tokens in Commerce** feature management flag is enabled, all online transactions will process within the Commerce system without the payment card token being saved. The payment module presents an iFrame of the configured payment processor's payment acceptance page. For the **Dynamics 365 Payment Connector for Adyen** when configured for the online store, if the **Allow saving payment information in e-commerce** parameter is set to **True**, the Adyen iFrame will present an authenticated (signed-in) online shopper the ability to "Save for my next payment" checkbox within the payment iFrame. Note that this mechanism allows the card to be saved with Adyen and can be presented within the Adyen iFrame at the time of the authenticated user's next checkout. However, this will not save the card on file within the Commerce system as described above in the [Saved card on file](#saved-card-on-file) section above. The online storefront's generated sales order will process the payment without a saved payment card token. If the online storefront's authorization expires before the order is fulfilled, meaning the payment was not captured against before the authorization is considered expired, the payment will be set to declined in the Commerce system. This event will set the 'Do not process' flag on the sales order header, and a new payment will need to be retrieved against the order. Orders in the declined state can be managed in the **Retail and Commerce \> Channels \> Call centers \> Call center credit cards \> Authorization management** screen in headquarters. 

### Point of sale payments

#### Cash and carry transactions

Transactional payments in POS cover a few flows depending on the actions taken. For shoppers paying for goods they are leaving the store with, this is typically referred to as a 'cash and carry' transaction, in which the payment resolves with a captured payment at the end of a transaction, without the need for the system to utilize or save a card payment token. No changes will occur to this existing cash and carry payment pattern when the **Enable use of non-recurring tokens in Commerce** feature is enabled or disabled.

#### Customer orders

A **Customer order** can be placed from the POS which will set up a sales order which is fulfilled by a shipment to the shopper. When the **Enable use of non-recurring tokens in Commerce** feature is enabled, a payment card token will be required for any set shipment date that exceeds a system set variable for shipment duration to require the payment card token. This card payment token will be required to place the authorization closer to the day the shipment will occur, reducing the chance that the authorization will expire before the items are invoiced and payment captured against that authorization. 

With a customer order, if the shipment date is under the threshold, no card payment token will be saved to place the order. An authorization will be requested and subsequent sales order created with the authorization reference. If items in the sales order are later adjusted prior to order completion, changing the sales order amount due will trigger the system to call an authorization adjustment against the originating authorization.

If the customer order shipment date is over the threshold, the POS associate will receive a warning that a payment card token is required to proceed with the order. This warning notes the shopper must agree to the saved card on file procedure, and the POS associate should follow the business procedures in place to meet your compliance standards for saving payment card information. Once the order is placed, the system will monitor and place the authorization using the saved card information as the shipment date falls within the set threshold. The card payment token will be scoped to the sales order specifically, and will not be available for future, new orders in the system. With the scoped card payment token, authorization resubmit will also utilize the saved card to retrieve a new authorization if an original authorization is considered expired.

## Additional resource

[Limit payment token usage](limit-token-usage.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]



