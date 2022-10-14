---
# required metadata

title: Limit payment token usage
description: This article describes the feature that limits how payment tokens are used in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 10/17/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2022-09-20

---

# Limit payment token usage

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes the feature that limits how payment tokens are used in Microsoft Dynamics 365 Commerce. Token usage is restricted to the scope of a sales order, or stored as a card on file with customer consent.

## Key terms

| Term | Description |
|---|---|
| Token | Referenced XML blob in the Dynamics system that stores payment references for transactional purposes. |
| Card on file | A saved card reference token agreed upon for future use in the Dynamics system or payment gateway that is specific to a customer's account. |

Limiting payment token usage applies to any environment that uses a payment gateway service in which recurring tokens are employed. The out-of-the-box [Dynamics 365 Payment Connector for Adyen](adyen-connector.md) uses recurring payment tokens to perform subsequent order actions such as authorization adjustments and reauthorizations. 

To help control the behavior of how these recurring payment tokens are used throughout the system, the **Restrict Payment Token usage to Order context** feature restricts usage of a recurring token to the scope of a sales order within the system. When enabled, the feature modifies the Commerce headquarters user interface to update payment input forms and limit selection of past customer payment references for use in new transaction instances. 

This feature helps meet usage rules for some payment issuers such as Visa, who include in their [Visa Core Rules and Visa Product and Service Rules](https://usa.visa.com/content/dam/VCOM/download/about-visa/visa-rules-public.pdf) that use of payment tokens should be restricted to the scope of a transaction, unless agreed upon by the cardholder.

The **Restrict Payment Token usage to Order context** feature is only relevant if you're employing a payment gateway service that uses recurring payment token references. 

## Enable the feature

To enable the **Restrict Payment Token usage to Order context** feature, in Commerce headquarters for your environment, go to **Workspaces \> Feature management**, find and select the  **Restrict Payment Token usage to Order context** feature from the list, and then select **Enable Now**.

## Limit payment token usage

When enabled, the Commerce headquarters forms used for payment method capture will update how the payment form references customer payment methods on file for the customer. Primarily this will affect two areas of operation: 

- How a customer card on file is entered on behalf of a customer.
- How payment information against a customer is stored for future sales order payment entries.

When a customer transacts against Commerce channels, payment details are stored with a sales order context. The sales order context limits the payment token so it won't be used as a payment reference against the customer record in headquarters payment forms for new or edited sales order payments. 

### Payment form changes

When a call center or headquarters user takes a payment for a customer against a sales order, the payment form presents payment method selection details. With the **Restrict Payment Token usage to Order context** feature enabled, when a user selects the plus symbol (**+**) on the payment form, only saved "card on file" records are displayed. Changes require the call center or headquarters user to enter the full payment details provided by the customer when filling out the **Enter customer payment information** form for the new sales order transaction. 

The **Number** drop-down list only displays card references associated with the customer with the card on file. The **Number** drop-down list filters out any past payment references that aren't scoped to a sales order. 

The plus symbol under the **Number** field remains available to enter the payment information provided by the customer for the transaction associated with the sales order being processed. 

### How cards on file work

When the **Restrict Payment Token usage to Order context** feature is enabled, a card on file is a recurring payment token saved against a customer record that isn't limited to the scope of a sales order. A card on file allows quick reference for headquarters users when filling out the payment form for a new sales order payment. This token reference is only applicable to the Dynamics environment. For online channels using a payment gateway service that allows users to save a payment method for future use within the payment iFrame module, these references are stored securely by the payment gateway as a separate reference to the Dynamics card on file. 

For example, if using the Dynamics 365 Commerce Payment Connector for Adyen in an online channel, customers that enter their credit card information in the payment iFrame module only see the gateway service saved card references for their next online purchase when they are authenticated. They don't see the Dynamics environment stored card on file as an option in the payment iFrame module. Similarly, shoppers placing an order via the call center don't have their online saved card references presented as options to the call center user. The call center user only sees prior card on file references from the Dynamics system (as agreed to by the customer) to save for future orders.

Headquarters users can save customer a card on file by going to **Retail and Commerce \> Customers** and selecting a customer account record. Under the **Customer \> Set Up** section, users with permissions to process the payment forms can use the **Credit cards** entry form to enter a payment card to be stored on file for future transactions. This operation saves time when processing future sales order payments for the customer. Call center and headquarters users should only enter the card on file card details if the customer agrees to use the card reference for future transactions.

A **Save for future use** checkbox is displayed at the end of headquarters payment forms to save the card on file for future use. This checkbox should only be used if the customer agrees to the use of the card on file for future transactions. The **Save for future use** option can be displayed or restricted by using the **Call center parameters \> Payment \> Allow customer card on file** parameter in headquarters. When this parameter is set to **Yes**, headquarters users with permissions to process payment forms are able to save a card on file using the **Save for future use** checkbox. When the parameter is set to **No**, the checkbox option isn't available to headquarters users with permissions to process payment forms. The **Allow customer card on file** parameter can be used if your company wants to restrict the usage of recurring tokens in headquarters, but doesn't yet want to allow saving a card on file without a procedure to ensure customer consent is granted.

### Headquarters forms where the recurring token restrictions are enforced

Token restriction scoping affects the following areas in headquarters when the feature is enabled:

- **Sales Order \> Payments \> Enter customer payment** information
- Continuity orders
- Installment payments
- Accounts receivable credit card payments

### Manage payment tokens (archiving or removal)

Payment tokens created prior to the **Restrict Payment Token usage to Order context** feature flag being enabled (or created while the feature is disabled) will remain "unscoped" in the system and be referenceable in the headquarters payment form selection lists. These tokens can be removed on a regular basis in headquarters two ways:

- Use the **Archive credit card transaction data** page to set a job to regularly purge or archive the payment tokens. Setting the **Delete data without archiving** option to **Yes** will delete the tokens that meet the **Minimum transaction age (in days)** setting. For more information, see [Archive credit card transaction data](archive-cc-data.md).
- Use the new **Account receivable \> Inquiries and reports \> Clean up \> Purge credit card tokens** form, which allows you to run or set a batch job to delete payment tokens. Set the following parameters:
  - The **Minimum token age in days** value must be 90 days or more.
  - **Run in the background** settings can be used to set **Recurrence** or **Alerts** settings.
  - A **Batch group** can be assigned to run this task with a specific group as created.
  - Setting the **Private** option to **Yes** will allow only the user who creates the job to run it.
  - Setting the **Critical Job** option to **Yes** ensures that the system actively tracks its status. 
 
Deleted tokens aren't retrievable. Set the **Minimum token age in days** setting to a range that suits the longest-running transactional lifespan (from authorization to capture or refund) for your environment.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
