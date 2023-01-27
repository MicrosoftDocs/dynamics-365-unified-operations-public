---
# required metadata

title: Limit payment token usage
description: This article describes the feature that limits how payment tokens are used in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 10/20/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2022-09-20

---

# Limit payment token usage

[!include [banner](../includes/banner.md)]

This article describes the feature that limits how payment tokens are used in Microsoft Dynamics 365 Commerce. Token usage is restricted to the scope of a sales order or, if customer consent is granted, is stored as a card on file.

## Key terms

| Term | Description |
|---|---|
| Token | A referenced XML blob in the Dynamics 365 system that stores payment references for transactional purposes. |
| Card on file | A saved card reference token that is agreed upon for future use in the Dynamics 365 system or the payment gateway, and that is specific to a customer's account. |

The limits on payment token usage apply to any environment that uses a payment gateway service where recurring tokens are employed. The out-of-box [Dynamics 365 Payment Connector for Adyen](adyen-connector.md) uses recurring payment tokens to perform subsequent order actions, such as authorization adjustments and reauthorizations.

To help control how these recurring payment tokens are used throughout the system, the **Restrict Payment Token usage to Order context** feature restricts usage of a recurring token to the scope of a sales order in the system. When it's enabled, the feature modifies the Commerce headquarters user interface (UI) by updating payment input pages and limiting the ability to select past customer payment references for use in new transaction instances.

This feature helps meet usage rules for some payment issuers such as Visa. In its [Visa Core Rules and Visa Product and Service Rules](https://usa.visa.com/content/dam/VCOM/download/about-visa/visa-rules-public.pdf), Visa specifies that usage of payment tokens should be restricted to the scope of a transaction unless the cardholder agrees otherwise.

The **Restrict Payment Token usage to Order context** feature is relevant only if you're using a payment gateway service that employs recurring payment token references.

## Enable the feature

To enable the **Restrict Payment Token usage to Order context** feature, in Commerce headquarters for your environment, go to **Workspaces \> Feature management**, find and select **Restrict Payment Token usage to Order context** in the list, and then select **Enable Now**.

## Limit payment token usage

When the feature is enabled, the Commerce headquarters pages that are used for payment method capture will update how they reference customer payment methods that are on file for the customer. This update will primarily affect two areas of operation:

- How a customer card on file is entered on behalf of a customer
- How payment information against a customer is stored for future sales order payment entries

When a customer transacts against Commerce channels, payment details are stored with a sales order context. The sales order context limits the payment token so that it won't be used as a payment reference against the customer record on payment pages for new or edited sales order payments in Commerce headquarters.

### Payment form changes

When a call center or Commerce headquarters user takes a payment for a customer against a sales order, the payment page presents payment method selection details. When the **Restrict Payment Token usage to Order context** feature is enabled, if a user selects the plus sign (**+**) on the payment page, only saved "card on file" records are shown. Changes require that the call center or Commerce headquarters user enter the full payment details that the customer provided when they filled in the **Enter customer payment information** page for the new sales order transaction.

The list of values for the **Number** field includes only card references that are associated with the customer who has the card on file. It filters out any past payment references that aren't scoped to a sales order.

The plus sign (**+**) under the **Number** field remains available and can be used to enter the payment information that the customer provided for the transaction that is associated with the sales order that is being processed.

### How cards on file work

When the **Restrict Payment Token usage to Order context** feature is enabled, a card on file is a recurring payment token that is saved against a customer record and isn't limited to the scope of a sales order. A card on file enables quick reference for Commerce headquarters users when they fill in the payment page for a new sales order payment. This token reference is applicable only to the Dynamics 365 environment. For online channels that use a payment gateway service that lets users save a payment method for future use in the payment iFrame module, the payment gateway securely stores these references as a separate reference to the Dynamics 365 card on file.

For example, if the Dynamics 365 Commerce Payment Connector for Adyen is used in an online channel, customers who enter their credit card information in the payment iFrame module see only the gateway service saved card references for their next online purchase when they are authenticated. They don't see the Dynamics 365 environment stored card on file as an option in the payment iFrame module. In a similar way, when shoppers place an order via the call center, their online saved card references aren't presented as options to the call center user. The call center user sees only previous card on file references from the Dynamics 365 system (as agreed to by the customer) to save for future orders.

Commerce headquarters users can save a card on file for a customer by going to **Retail and Commerce \> Customers** and selecting the customer account record. In the **Customer \> Set Up** section, users who have permissions to process the payment pages can use the **Credit cards** entry page to enter a payment card that will be stored on file for future transactions. This operation helps save time when future sales order payments are processed for the customer. Call center and Commerce headquarters users should enter the card on file card details only if the customer agrees to use the card reference for future transactions.

A **Save for future use** checkbox at the bottom of Commerce headquarters payment pages lets users save the card on file for future use. This checkbox should be used only if the customer agrees to use the card on file for future transactions. You can show or restrict the **Save for future use** checkbox by using the **Allow customer card on file** option on the **Payment** tab of the **Call center parameters** page in Commerce headquarters. When this option is set to **Yes**, Commerce headquarters users who have permissions to process payment pages can save a card on file by using the **Save for future use** checkbox. When the option is set to **No**, the checkbox isn't available to Commerce headquarters users who have permissions to process payment pages. The **Allow customer card on file** option can be used if your company wants to restrict the usage of recurring tokens in Commerce headquarters, but it doesn't yet want to allow a card on file to be saved without a procedure to ensure that customer consent is granted.

### Commerce headquarters pages where the recurring token restrictions are enforced

Token restriction scoping affects the following areas in Commerce headquarters when the feature is enabled:

- Customer payment information at **Sales Order \> Payments \> Enter customer payment**
- Continuity orders
- Installment payments
- Accounts receivable credit card payments

### Manage payment tokens (archiving or removal)

Payment tokens that were created before the **Restrict Payment Token usage to Order context** feature flag was enabled (or while the feature was disabled) will remain "unscoped" in the system and can be referenced in selection lists on the Commerce headquarters payment page. These tokens can be removed on a regular basis in two ways in Commerce headquarters:

- Use the **Archive credit card transaction data** page to set up a job that regularly purges or archives the payment tokens. If you set the **Delete data without archiving** option to **Yes**, the tokens that meet the **Minimum transaction age (in days)** setting will be deleted. For more information, see [Archive credit card transaction data](archive-cc-data.md).
- Use the new **Purge credit card tokens** page (**Accounts receivable \> Inquiries and reports \> Clean up \> Purge credit card tokens**), which lets you run or set up a batch job that deletes payment tokens. Set the following parameters:

    - The **Minimum token age in days** value must be 90 days or more.
    - The **Run in the background** settings can be used to define **Recurrence** or **Alerts** settings.
    - A batch group can be assigned to run the task for a specific group.
    - If the **Private** option is set to **Yes**, only the user who creates the job can run it.
    - A setting of **Yes** for the **Critical Job** option ensures that the system actively tracks the job's status.

Deleted tokens can't be retrieved. Set the **Minimum token age in days** field to a range that suits the longest-running transactional lifespan for your environment (from authorization to capture or refund).

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
