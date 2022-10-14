---
# required metadata

title: Limit payment token usage
description: This topic reviews the capability to limit how payment tokens are used within the system. Token usage is restricted to the scope of a Sales Order, or stored as a card-on-file for the shopper per their consent.
author: BrianShook
ms.date: 10/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom:

---

# Limit payment token usage

This topic provides an overview of the Microsoft Dynamics 365 Commerce usage of payment tokens within the product. 

## Key terms

| Term | Description |
|---|---|
| Token | Referenced XML blob in the Dynamics system which stores payment references for transactional purposes. |
| Card on file | A saved card reference in the Dynamics system or payment gateway specific to a customer's account and agreed upon for future use |

The limiting of payment token usage applies to any environment which is using a payment gateway service in which recurring tokens are used. The Dynamics 365 Commerce out-of-box Adyen payment connector uses recurring payment tokens to perform subsequent order actions such as authorization adjustments or re-authorizations. However, to assist in controlled behavior of how these recurring payment tokens are used throughout the system, this feature restricts the usage of the recurring token to the scope of a Sales Order within the system. The feature when enabled will alter the user interface within Dynamics 365 Commerce headquarters to address payment input forms and limit selection of past customer payment references for use in new transaction instances. 

This update assists in meeting usage rules for some payment issuers such as Visa, who note in their [Visa Core Rules and Visa Product and Service Rules](https://usa.visa.com/content/dam/VCOM/download/about-visa/visa-rules-public.pdf) that use of a payment token should be restricted to the scope of a transaction unless agreed upon by the cardholder.

## Prerequisites

This feature is relevant to using a payment gateway service which uses recurring payment token references. 

### Enable the Feature

In headquarters for your Dynamics environment, go to **Workspaces \> Feature management** and set the feature **Restrict Payment Token usage to Order context** to "Enabled" using the **Enable Now** button.

## Limiting Payment Token Usage
When enabled, the Dynamics 365 Commerce headquarters forms used for payment method capture will update how the payment form references customer payment methods on file for the customer. Primarily this will affect two areas of operation: 

- How a customer 'card on file' is entered on behalf of a customer
- How payment information against the customer is stored for future Sales Order payment entries

When a customer transacts against Commerce channels, payment details are stored with a Sales Order context. The Sales Order context will limit the payment token so it won't surface as a payment reference against the customer record in headquarters payment forms for new or future edited Sales Order payments. 

### Payment form changes

When a call center or headquarters user is taking a payment for a customer against a Sales Order, the payment form will present payment method selection details. With this feature enabled, when the user selects the 'plus' sign on the payment form, only saved 'card on file' records will be presented for easy selection. Changes will require the customer service employees to enter the full payment details provided by the customer when filling out the **Enter customer payment information** form for the new Sales Order transaction. 

The **Number** field drop-down will only display card references for the customer that are associated to the customer as a 'card on file' (or specifically, will filter out any past payment references not scoped to a Sales Order). 

The 'plus' sign under the **Number** field will remain available to enter the payment information provided by the customer for the transaction associated to the Sales Order being processed. 

### Cards on file

A 'card on file' is a recurring payment token saved against a customer record that isn't limited to a Sales Order scope (when the **Restrict Payment Token usage to Order context** feature is enabled). A 'card on file' will allow quick reference for headquarters users when filling out the payment form for a new Sales Order payment. Note that this token reference is specific only to the Dynamics environment. For online channels using a payment gateway service that allows users to save a payment method for future use within the payment iFrame module, these references are stored securely by the Payment Gateway as a separate reference to the Dynamic's 'card on file'. For example, if using the Dynamics 365 Commerce Payment Connector for Adyen in an online channel, customers filling out their credit card information in the payment iFrame module will see only those gateway service saved card references for their next online purchase when authenticated. They won't see the Dynamics environment stored 'cards on file' as options in the payment iFrame module. Similarly, shoppers placing an order through Call Center won't have their online saved card references presented as options to the Call Center employee.  The Call Center employee will only see past 'card on file' references from the Dynamics system as agreed upon by the customer to save for future orders.

Headquarters users can save a 'card on file' for a customer using the **Retail and Commerce \> Customers** page by selecting a customer account record. Under the **Customer \> Set Up** section, users with permissions to process the payment forms can use the **Credit cards** entry form to enter a payment card to be stored on file for future transactions. This saves time when processing future Sales Order payments for the customer. Call Center and Headquarters users should only enter the 'card on file' card details if agreed upon from the customer to use for future transactions.

Additionally, a **Save for future use** checkbox will be presented at the end of headquarters payment forms to save for future use as a 'card on file'. This checkbox should only be used if agreed upon by the customer to use for future transactions. The **Save for future use** option can be displayed or restricted by using the **Call center parameters \> Payment \> Allow customer card on file** parameter in headquarters. When this parameter is set to **Yes**, headquarters users with permissions to process payment forms will be able to save a 'card on file' using the **Save for future use** checkbox.  When the parameter is set to **No**, the option won't be available to headquarters users with permissions to process payment forms. This parameter can be used if your company wants to restrict the usage of recurring tokens in headquarters, but doesn't yet want to allow saving a 'card on file' without a procedure to ensure customer consent is granted.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
