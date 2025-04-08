---
# required metadata

title: Dynamics 365 Payment Connector for PayPal
description: This article provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal.
author: BrianShook
ms.date: 02/28/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2020-10-31
ms.custom: 
  - bap-template
---

# Dynamics 365 Payment Connector for PayPal

[!include [banner](../../finance/includes/banner.md)]

This article provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal (PayPal payment connector). It includes a list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

> [!WARNING]
> The Dynamics 365 Commerce pattern for PayPal and Google Pay Express payment behavior isn't currently recommended for regions enforcing Revised Payment Services Directive (PSD2) requirements. The Commerce payment module express payment patterns calculate the final order price on the Commerce checkout page when it has obtained the delivery address for a user's order. PSD2 recommends that users see the full order total price within the authentication window of the digital wallet. Commerce will track future work to update PayPal and Google Pay module behavior to support express flows by updating order details within the wallet payment window when a delivery address is selected.

## Key terms

| Term | Description |
|---|---|
| PayPal Wallet | Also known as the PayPal "button," PayPal Wallet describes the customer experience and integration supported by the PayPal payment connector. |
| Wallet | A payment type that doesn't include traditional payment characteristics, such as the BIN range and expiration date, which are used to differentiate among credit and debit card types. |

Microsoft Dynamics 365 Commerce offers an out-of-box integration for PayPal Wallet. When the PayPal payment connector is configured, the PayPal button is a selectable payment method as part of online order checkout. When users select **PayPal**, they're directed to complete their payment directly with PayPal and then are returned to the online storefront for order completion.  

The PayPal payment connector is implemented using the same payments SDK that is used for credit card payments. To better support PayPal payments, support for noncredit card payments was enhanced with the addition of support for "wallet" payment types. Specifically, PayPal payments don't return a BIN range. To support PayPal and other wallet payments, a new mapping for payments was introduced that doesn't include BIN range. This new mapping can also be used to augment existing BIN range mapping for credit card payment methods. For more information, see [Wallet payment support](wallets.md). 

The PayPal payment connector isn't available in China. For other locales where Dynamics 365 Commerce is available, there are currently no restrictions. 

## Functional overview

### PayPal Wallet in storefront 

The PayPal payment connector supports the use of the PayPal Wallet, or PayPal button, for e-commerce payments. When the PayPal payment connector is configured for the online storefront, customers are presented with the option to pay using the PayPal button at the time of payment. When customers select the PayPal button, they're redirected to a PayPal Wallet mini-browser window where they're authenticated by PayPal and can select their method of payment. Upon successful authentication and selection of a payment method, customers are redirected back to the storefront with the PayPal payment loaded into the checkout form. When the order is placed, the PayPal payment is included as a payment line on the order, and is synchronized to Commerce headquarters.

For more information on PayPal Wallet, visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) hosted by PayPal. 

### Fulfillment

Orders with PayPal payment lines are fulfilled in the same manner as orders that are paid using a credit card. When an order is created, the PayPal payment is added in an authorized state. Upon fulfillment, whether the order is shipped to the customer from a distribution center or picked up in a store, the payment authorization that is associated with the order is then captured using the same payments SDK requests used to capture credit card payments. 

Fulfillment for PayPal orders supports incremental capture. This means that if an order is partially fulfilled and invoiced, the same original authorization is referenced when the remainder of the order is fulfilled instead of requiring a new authorization. 

### Authorization expiration

Orders made using the PayPal payment connector should be fulfilled within 30 days. If an order can't be fulfilled or invoiced within 30 days, the original authorization expires. The PayPal payment connector doesn't currently support billing agreements. Recurring billing agreements, similar to recurring card references/tokens, are required to automatically generate new authorizations after original authorization expiration. This means that if an authorization expires, the order falls into a "don't process" state and the customer must be contacted to arrange for an alternate form of payment. 

### Order Intent

Beginning in Commerce version 10.0.30, the PayPal payment connector configuration in headquarters includes the **OrderIntent** field, which allows the configuration of the PayPal payment connector to operate with a saved order with the PayPal service for the online channel. After a payer approves an order, the PayPal payment connector sends a command to save the PayPal order, which allows for future references against the order within PayPal. For Commerce, this action means that a specific PayPal order reference can be reauthorized if a void was previously called. Merchants can also work with PayPal to configure the order expiry duration, and to customize functionality to reauthorize against a PayPal order if the original authorization isn't expired.

When you configure the PayPal payment connector in Commerce headquarters, the **OrderIntent** field can have two values:

- **Authorize**: This configuration value is the default value. If the field is left blank, **Authorize** becomes the default value. Configuring the **OrderIntent** field with the **Authorize** value correlates to the PayPal processing instruction value of **NO_INSTRUCTION**. The order is authorized with PayPal and the authorization can't be modified when this value is used.
- **Save**: Configuring the **OrderIntent** field with the **Save** value correlates to the PayPal processing instruction value of **ORDER_SAVED_EXPLICITLY**. When this value is used, order references are saved in the PayPal service.

## Test the PayPal payment connector

### Create a PayPal developer account

To test the PayPal payment connector, you must first create PayPal developer credentials and a PayPal sandbox environment. 

1. Go to the [Test and go live](https://developer.paypal.com/docs/business/test-and-go-live/) page provided as part of PayPal's development resources. 
2. Select [Get Started](https://developer.paypal.com/docs/platforms/get-started/) on the **Test and go live** page. 
3. On that page, select **Log in to the Developer Dashboard**.
4. If prompted to sign in, select **Sign up**.
5. Select **Business Account**, then select **Next**.
6. Provide the email address you want to associate with your PayPal account and create a password for your PayPal account. 
7. On the next page, enter contact information details, then read the PayPal user agreement and Privacy statement. If you agree to the terms, select **Agree and Create Account**.  

    > [!NOTE]
    > The terms agreed to for the creation of a PayPal developer account are between the organization or individual creating the account and PayPal. Microsoft is in no way liable and makes no warranty as to the terms specified the agreement. These instructions are for informational purposes only. 

8. After you agree to the terms, specify your business type, and select **Continue**.
9. Next, go to the [PayPal Developer page](https://developer.paypal.com/developer/applications) and select **Log in to Dashboard**.
10. Sign in using the credentials used when creating your PayPal account.
11. In the developer dashboard, select the **Default Application** in the list of RestAPI apps.
12. Note the **Client ID** and **Secret** for your sandbox account. These values are used to set up the PayPal payment connector in Dynamics 365 Commerce.

    > [!NOTE]
    > To collect **Client ID** and **Secret** for a live environment, select the **Live** tab for the selected RestAPI app.

## Set up the PayPal payment connector in Dynamics 365 Commerce

### Map the PayPal wallet payment method to a processor payment method

> [!NOTE]
> Some of these steps leverage a new capability for supporting wallet payment methods. For more information on this feature, see [Wallet payment support](wallets.md).

1. Go to **Retail and Commerce \> Channel Setup \> Payment methods \> Payment methods**.
2. Select **New**.
3. Specify a **Payment method ID** and **Payment method name**, such as **Wallet**. Set the **Default function** to **Wallet**, and then select **Save**.
4. Go to **Retail and Commerce \> Channel Setup \> Payment methods \> Card types**.
5. Select **New**.
6. Specify an **ID**, such as **PayPal**. Set an **Electronic payment name**, such as **PayPal**. Set **Type** to **Wallet**, and then specify a name for the **Issuer**, such as **PayPal**. Select **Save**.
7. Select the entry previously created and select **Processor mapping**.
8. On the **Processor payment method mapping** page, select the previously created **PayPal** card type. In the middle column, select the **Dynamics 365 Payment Connector for PayPal** and select **Add**. 

> [!NOTE]
> The **Processor payment method mapping** capability adds a new table that must be synchronized to the channel database. To add this data to the Commerce scheduler, you need to initialize the Commerce scheduler. For details, please refer to documentation related to [updating commerce scheduler configurations](cdx-best-practices.md#update-configurations). 

### Set up the PayPal payment connector in payment services

Follow these steps to configure the PayPal payment connector in **Payment Services**.

1. In Commerce headquarters, go to **Accounts receivable \> Payments setup \> Payment services**.
2. On the Action Pane, select **New**, and then on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | PayPal |
    | Payment connector | Select the PayPal payment connector. | Dynamics 365 Payment Connector for PayPal |
    | Test mode | For the PayPal payment connector, in production and test environments you should set this field to **False**. | False |
    | Default processor for credit cards | This option should be set to **No** because the call center uses the default processor. | No |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a zero amount. | Yes |

3. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Autopopulated name of the assembly for the PayPal payment connector. | Yes | Yes | *Binary name* |
    | Service account ID | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes should use (such as invoicing). | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**.  | Yes | Yes | *String* |
    | Merchant API key | Enter the sandbox **Secret** collected from the PayPal developer dashboard under **Default application**. | Yes | Yes | *String* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal payment connector. The default is **USD**. | Yes | Yes, but can be edited. | USD; CAD |
    | Supported tender types | Other payment connectors may support multiple tender types. For PayPal, the only payment method is **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connectors may return multiple payment method variants. For PayPal, the only variant is **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to sandbox or live environments. | Yes | Yes | *Sandbox* or *Live* |
    | OrderIntent | This field is used to specify whether the order reference is saved in the PayPal service. | No | No | *Authorize* (default behavior if left blank) or *Save* |
    | Enhanced totaling audit | When this field is set to **True**, Commerce revalidates online order total calculations with the PayPal service before authorization. Introduced in Commerce version 10.0.35.  | No | No | True/False (If the field is blank, the default value is **False**. ) |
    
> [!NOTE]
> When testing payments in a sandbox environment, the **Environment** field should never be set to live and live environment. **Merchant client ID** and **Merchant API keys** must never be used. Sandbox environments are for sandbox testing only.

### Set up the PayPal payment connector for the online store

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
2. Select the online store to add the PayPal payment connector.
3. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
4. In **Connectors**, select **Dynamics 365 Payment Connector for PayPal**.
5. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Autopopulated name of the assembly for the PayPal payment connector. | Yes | Yes | *Binary name* |
    | Service account ID | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes should use (such as invoicing). | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**.  | Yes | Yes | *String* |
    | Merchant API key | Enter the sandbox **Secret** collected from the PayPal developer dashboard under **Default application**. | Yes | Yes | *String* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal payment connector. The default is **USD**. | Yes | Yes, but can be edited. | USD; CAD |
    | Supported tender types | Other payment connectors may support multiple tender types. For PayPal, the only payment method is **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connectors may return multiple payment method variants. For PayPal, the only variant is **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to sandbox or Live environments. | Yes | Yes | *Sandbox* or *Live* |
    | OrderIntent | This field is used to specify whether the order reference is saved in the PayPal service. | No | No | *Authorize* (default behavior if left blank) or *Save* |
    | Enhanced totaling audit | When this field is set to **True**, Commerce revalidates online order total calculations with the PayPal service before authorization. Introduced in Commerce version 10.0.35.  | No | No | True/False (If the field is blank, the default value is **False**. ) |

### Set up the PayPal payment method for the online store

To set up the PayPal payment method for the online store, follow these steps.

1. In the online store where the PayPal payment connector is configured, on the **Setup** tab, select **Payment methods**.
1. Select **New** to add a payment method.
1. In the **Payment method** field, select the PayPal payment method that you created earlier. 
1. In the **Operation name** field, select **Pay card**.
1. In the **Connector name** field, select **Dynamics 365 Payment Connector for PayPal**.
1. On the **Posting** FastTab, specify the posting details.
1. Select **Electronic payment setup**, select **New**, and then, in the **ID** field, select the card type that you previously created for PayPal. 
1. Select **Save**, and then close the **Electronic payment types** and **Online stores** pages. 

> [!NOTE]
> When testing payments in a sandbox environment, the **Environment** field should never be set to live and live environment. **Merchant client ID** and **Merchant API key**s must never be used. Sandbox environments are for sandbox testing only.

After the above changes are made in Commerce headquarters, synchronize the changes using the **1070** distribution schedule.

### Configure PayPal for the storefront checkout module

For information on configuring the storefront checkout module to use PayPal in the checkout module, see [Payment module](../payment-module.md).

#### Use the payment express section on the cart and checkout pages with PayPal using the payment module

> [!WARNING]
> The Dynamics 365 Commerce pattern for PayPal Express isn't currently recommended for regions enforcing PSD2 requirements. The payment module used for PayPal support calculates the final order price upon return to the Commerce checkout page when it has acquired the delivery address information for a user's order. PSD2 recommends that users see the full order total price within the authentication window of the digital wallet. Commerce will track future work to update the PayPal express patterns to support express flows by updating order details within the PayPal payment window when a delivery address is selected.

The Commerce payment module payment express patterns provide site users with the option to check out faster by using their payment service account information during the checkout process. The payment module payment express actions reference the linked payment connector via the **Supported tender types** attribute string of the payment connector. Express payment actions within the payment module then return the user-selected order details (address, contact information, and payment method) to prefill the checkout form.

When the payment module is used with express patterns for PayPal, if customers select the PayPal button in the **Payment Express** section, the PayPal payment window opens. Users can then sign in to their PayPal account to use their account shipping address, billing address, email address, and PayPal payment method of choice to pay for the transaction.

When users complete the action in the PayPal window, they're directed to the Commerce site checkout page, where the checkout form is prefilled with their PayPal account details. After users return to the checkout page from the PayPal window, they see the following details:

- In the payment express flow, the first delivery option that is available for the shipping address that was returned is preselected for the customer.
- The shipping address and contact information, such as the customer's email address, are prepopulated in the checkout form. If they're using express checkout, the email address from the express account is used.
- The payment method is selected from the customer's digital PayPal wallet.

Customers can review orders and change checkout order details before they select **Place order** to finalize the order.

#### Configure the checkout fragment for express payments using PayPal with the payment module

To set up the checkout fragment for express payments using PayPal in site builder, follow these steps.

1. Go to **Fragments**.
1. Select the **Checkout** fragment, and then select **Edit**.
1. In the **Checkout express payment container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Payment express**, and then select **OK**.
1. In the payment express module's properties pane, update the module properties as needed: 
    1. To rename the module for easier identification in the **Outline** view, select the pencil symbol next to the module name, enter a new name, and then select the checkmark symbol.
    1. For the **Height of the iFrame** property, set a height in pixels that meets your page design needs (for example, enter "65" to set a height of 65 pixels).
    1. Set the **Supported tender types** value to **PayPal**. This value must match the **Supported Tender Types** string in the connector set up for the channel.
    1. The **Payment style override** property is used to apply CSS code styling to the module. Site builder CSS overrides and styles don't apply to the payment express module via this property. This styling doesn't affect the inner-window styles within the payment iframe rendered by the payment service.
    1. You can reference a **Custom CSS class name** to apply to the payment module, which can be a class name defined in the theme pack. This styling doesn't affect the inner window styles within the payment iframe element rendered by the payment service.
    1. Enabling the **Render when module scrolls into view** setting is recommended for modules that are hidden below the site user's view when interacting within the page. When **Render when module scrolls into view** is selected, the payment module renders on the site user's client device once the viewport is reached on the page. This setting can help improve overall initial page load time.
1. Optionally, in the **Checkout express payment container** module, you can add a text block module that includes instructions or disclosure information for the express payment section of your site. After you add the module, in the properties pane, enter the desired text under **Rich text**. You can position the text above or below the payment express modules by selecting the ellipsis (**...**) in the **Text block** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

#### Configure the cart page for express using PayPal with the Payment module

To set up the cart page for express payment using PayPal in site builder, follow these steps.

1. Go to **Pages**.
1. Select your site's cart page, and then select **Edit**.
1. Under the **Main slot**, find the container that contains the **Cart** module.
1. Under the **Cart** module, select the **Payment express** section.
1. In the **Payment express** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Payment express**, and then select **OK**.
1. In the payment express module's properties pane, update the module properties as needed: 
    1. To rename the module for easier identification in the **Outline** view, select the pencil symbol next to the module name, enter a new name, and then select the checkmark symbol.
    1. For the **Height of the iFrame** property, set a height in pixels that meets your page design needs (for example, enter "50" to set a height of 50 pixels).
    1. Set the **Supported tender types** value to **PayPal**. This value must match the **Supported Tender Types** string in the connector set up for the channel.
    1. The **Payment style override** property is used to apply CSS code styling to the module. Site builder CSS overrides and styles don't apply to the payment express module via this property. This styling doesn't affect the inner-window styles within the payment iframe rendered by the payment service.
    1. You can reference a **Custom CSS class name** to apply to the payment module, which can be a class name defined in the theme pack. This styling doesn't affect the inner window styles within the payment iframe element rendered by the payment service.
    1. Enabling the **Render when module scrolls into view** setting is recommended for modules that are hidden below the site user's view when interacting within the page. When **Render when module scrolls into view** is selected, the payment module renders on the site user's client device once the viewport is reached on the page. This setting can help improve overall initial page load time.
1. Optionally, in the **Checkout express payment container** module, you can add a text block module that includes instructions or disclosure information for the express payment section of your site. After you add the module, in the properties pane, enter the desired text under **Rich text**. You can position the text above or below the payment express modules by selecting the ellipsis (**...**) in the **Text block** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the page.

You can include up to three supported payment express modules (in other words, three available supported payment options) in the cart page's **Payment Express** slot.

#### Modes of delivery

For the payment express module that uses PayPal, the first delivery option returned against the selected shipping address from the PayPal account is preselected. Site users have an opportunity to adjust the shipping address to a different option if they want.

The order in which the delivery methods are displayed in the payment express module is configured on the channel's **Modes of delivery** page in Commerce headquarters. In headquarters, go to **Retail and Commerce \> Channels \> Online stores**, and then select the **Retail channel ID** value for your store. On the **Setup** tab of the action pane,  select **Modes of delivery**. The modes of delivery that are listed are displayed in the same order as in the payment express module. Select **Manage modes of delivery** on the action pane to add or remove modes of delivery for a retail channel or product. For more information about how to set up modes of delivery, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The checkout module also uses the delivery options module when modes of delivery are rendered during checkout. For more information, see [Delivery options module](../delivery-options-module.md).

Modes of delivery are displayed as they're added to the **Modes of delivery** list in the online store.

## Enter a merchant relationship with PayPal

To create a **Live** merchant account with PayPal, visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) for self-service or [connect with a sales representative](https://www.paypal.com/business/contact-sales) to discuss custom rates. 
 
## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
