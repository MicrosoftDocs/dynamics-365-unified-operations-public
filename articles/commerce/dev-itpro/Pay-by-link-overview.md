---
title: Enable pay by link in POS using Adyen connector 
description: Learn how to set up and enable pay by link payment method to capture payments in stores in Microsoft Dynamics 365 Commerce.
author: shajain
ms.date: 06/19/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2025-06-15
---

# Enable pay by link payment method to capture payments using point of sale (POS)

[!include [banner](../includes/banner.md)]

This article explains how to set up and enable pay by link payment method to capture payments in stores in Microsoft Dynamics 365 Commerce.

Pay by link functionality allows merchants to offer modern payment methods that provide customers with the flexibility to choose their preferred payment method. Pay by link also eliminates the need for a payment terminal, allowing store associates to be mobile and accept various types of payments. Pay by link can also serve as an effective tool for reducing checkout lines by enabling customers to pay from their current location, expediting the checkout process. 

Pay by link functionality is a controlled release, so contact your Adyen account manager to check participation availability for the pilot release. 

## Prerequisites

### Enable OAuth authentication from Adyen

The payment notification for pay by link payment method uses OAuth-based authentication. Before setting it up, OAuth authentication must be enabled by both the Dynamics 365 Commerce team and Adyen. To enable OAuth from Commerce, you must contact Microsoft support to enable a flight in your Commerce environments. You must also contact your Adyen representative to enable OAuth authentication for webhooks for your account. You must also ask Adyen to set the "Time to Live" (TTL) value for the OAuth token 3599 seconds, which is one second less than an hour (the default TTL value for OAuth token in Microsoft Azure). 

> [!NOTE]
> If the OAuth TTL can't be set to 3599 seconds by Adyen, then contact Microsoft support for instructions on how to override the default TTL value in the Azure portal.

### Link your Commerce environment to a Dataverse environment

Another requirement to receive payment notifications is to link your Commerce environment to a corresponding Dataverse environment, because the payment notification service uses Dataverse. Learn more in [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv) and [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv).

### Minimum required versions

The pay by link feature is available starting with the Commerce 10.0.44 release. The minimum required versions for the various components are listed below.
- **Store Commerce App/ Cloud Point of Sale**: 9.54.25148.1
- **Commerce Scale Unit**: 9.54.25137.4
- **Commerce headquarters**: 10.0.44

### Required role to complete the setup

Some of the steps require a Commerce headquarters user who is either an administrator or has the Commerce Payment Administrator role assigned in the Power platform.

## Setup

### Enable the features required for pay by link 

To enable the payment notifications for pay by link, enable the following features from the **Feature management** workspace:
- Enhanced wallet support and payment improvements. Learn more in [Wallet payment support](/dynamics365/commerce/dev-itpro/wallets).
- Unified payments experience in POS. Learn more in [Check out faster with optimized payment flows](/dynamics365/commerce/dev-itpro/faster-checkout-pos).
- **Payments Notification** feature.
- **Pay By Link Payment** feature.

### Create a webhook to receive payment notification from Adyen

The following information is required to create a webhook in the Adyen portal:
- Payment notification service URL.
- OAuth credentials to authenticate against the payment notification service.

The payment notification service URL is where Adyen sends the notifications. It can be retrieved from Commerce headquarters by going to **Commerce Shared Parameters** \> **Payment notifications**. Copy the **Payment notifications end point URL** field value. If this field has no value, then it means that the Commerce environment isn't linked to Dataverse environment. For assistance, contact your Commerce administrator or Microsoft support.

To create the OAuth credentials, you must register a new application using the Azure portal. Payment notifications from Adyen use the new application's credentials to securely communicate with the payment notification service.

#### Register a new application by using the Azure portal

To register a new application by using the Azure portal, follow these steps.

1. Sign in to the Microsoft Azure portal (https://portal.azure.com/) with a work or school account.
1. If your account gives you access to more than one tenant, select your account in the upper-right corner, and set your portal session to the Microsoft Entra tenant that you want.
1. In the left pane, select the Microsoft Entra ID service, and then select **App registrations** > **New registration**.
1. When the Register an application page appears, enter your application's registration information:
    - **Name**: Enter a meaningful application name that is shown to users of the app.
    - **Supported account types**: Any of the available options should work.
    - **Redirect URI** isn't needed.
1. Select **Register**

Once the new application is registered, then from the Overview page, copy the values of the following two properties:
- **Application (client) ID**
- **Directory (tenant) ID**

<!--![Screenshot that shows the Client ID and Tenant ID properties on Azure portal](./media/App%20registration_1.png)-->

Next, you must create a client secret for the application. To do so, select the **Certificates & secrets** section, and then select **New client secret**. Provide a description of the secret and an expiration period for the secret. Ensure that you create a business process for rotating this secret because payment notifications fail when the secret expires. Copy the secret value and save it somewhere for later use. 

<!--![Screenshot that shows the Client sercret location in Azure portal](./media/App%20registration_2.png)-->

To create a new webhook, follow these steps.

1. navigate to the Adyen portal and go to the **Developers** section.
1. Create a **Standard webhook**.
1. Under the **Server configuration** section, paste the value copied for the **Payment notifications endpoint URL** in the URL field.
1. Keep the default values for **Method** (**JSON**) and **Encryption protocol** (**TLS v1.3**).
1. Under the **Security** section, select **OAuth** and enter values for following the properties:
    - **Client ID**: Enter the value for **Application (client) ID** you copied earlier.
    - **Client Secret**: Enter the value for **Secret value** you copied earlier.
    - **URL**: Enter `https://login.microsoftonline.com/{tenantid}/oauth2/v2.0/token` after replacing {tenantID} with the **Directory (tenant) ID** value you copied earlier.
    - **Scope**: Enter "a013b12b-2624-40b4-b15b-b7751d733a22/.default". 

    <!--![Screenshot that shows the OAuth settings in Adyen](./media/Adyen_OAuth.png)-->

1. Generate a new Hash-based Message Authentication Code (HMAC) key and copy it. You won't be able to view this key again, so keep it somewhere safe. 
1. In the **Events** section, select **Authorisation**.
1. Under **Additional settings**, in the **Card** section, select the **Include card bin** and **Include Subvariant** options.
1. Leave the rest of the fields as is and save the configuration. 

> [!NOTE]
> Don't test the configuration yet because the setup isn't yet complete. The configuration is validated after the next step.

### Update Commerce headquarters with the HMAC and application client ID details to authenticate the payment notifications sent by Adyen

1. In headquarters, go to **Commerce shared parameters**.
1. Open the **Payment notification** section and enter values for the following properties:
    - **Data verification HMAC key**: Enter the HMAC key you copied earlier.
    - **Payment notifications client ID**: Enter the value for **Application (client) ID** you copied earlier.
1. Save the configuration. 

> [!NOTE]
> Only Commerce headquarters users who have either the "Administrator" or "Commerce Payment Administrator" roles in Power Platform are able to save the configuration. 

#### Test the connection to payment notification service

To test the connection, follow these steps.

1. Navigate to the Adyen portal.
1. Edit the webhook you created earlier, and then select **Test configuration**. If the connection fails, then validate all the steps above to ensure the values are correct. If any changes are made (for example, if keys are changed), then wait 20 minutes to test again to ensures that caching isn't impacting the test. If the issue persists, contact Microsoft support.

### Set up pay by link payment method for the store

You can either create the pay by link payment method as a new payment method that can be displayed in the list of payment methods, or as a dedicated button. You can also add it to the existing payment method created for credit/debit cards so that when a cashier selects the existing payment method, the POS shows pay by link as one of the input types for payment capture. 

In either case, for the pay by link option to be displayed, the administrator must select **Pay By Link** as one of the payment input types for a payment method. If you want to create a dedicated payment method for pay by link, then only select the **Pay By Link** option. If you want to add pay by link as one of the options to capture payments, then select **Payment on terminal** and **Manual entry** (optional) along with the **Pay By Link** option.

> [!NOTE]
> The payment input type option is only available for payment methods that have **Function** set to **Card** or **Wallet**, and **Operation name** set to **Pay card**.  

<!--![Screenshot showing the payment input type options in Commerce headquarters](./media/payment_input_type.png)-->

If **Manual entry** is added as a payment input type, then when a cashier on POS selects this payment method, the customer is prompted to manually enter their credit card number on the payment terminal. Also, enabling manual entry sets the **Electronic payment setup** \> **Allow manual card numbers** property to **True**, and it is disabled. If the manual entry option is removed, then the **Allow manual card numbers** property remains disabled but can be edited by the user.

To support payment options such as quick response (QR) code-based wallets, setting up bin ranges isn't. New card types must be created and mapped to corresponding payment variants. These card types must be added to the payment method where the pay by link is enabled. Learn more in [Wallet payment support](/dynamics365/commerce/dev-itpro/wallets).

> [!NOTE]
> If you're creating a new payment method for pay by link, you don't need to add the electronic payment types already added other payment methods that are available for the store. For example, if Visa, Mastercard, American Exselect payment types are already added to the **Cards** payment method, then you don't need to add them again to the pay by link payment method. The system looks through all the payment methods associated with the store to find a matching electronic payment type used for payment.

Pay by link doesn't require Hardware station to be enabled for Cloud POS or the Store Commerce app. If you want to use pay by link with a register that isn't paired with a hardware station, then the register must be configured to use Commerce Scale Unit (AKA Retail Server) for **Card not present processing**. In headquarters, go to the **Register** form and in the **General** section, set the value for **Card not present processing** to **Use retail server**.

![Screenshot showing the payment input type options in Commerce headquarters](./media/Register_CNP.png)

> [!IMPORTANT]
> If you don't intend to pair the hardware station with POS, then contact Microsoft support to enable the flight named "Payments.PayByLinkVisibleWhenHWSOrTerminalInactive" in your environment. This flight is automatically enabled starting with Commerce version 10.0.45.

### Define the behavior for payment link

You can control some payment link experiences by configuring **Custom Settings** in the **Adyen connector** section of the Hardware profile used by the register. You can control the following experiences: 
- **Payment expiration duration**- This is controlled by adding a value to the **PaymentLinkDuration** property.
- **Include the Adyen store information in the payment link** - This is controlled by adding a value to the **Store** property.
- **Require shoppers to enter their information before payment** - This is controlled by adding a value to the **RequiredShopperFields** property.

You can skip any of these properties from **Custom Settings**. So, if the payment link expiration isn't mentioned, then Adyen’s default value of 24 hours is used. If the **Store** property isn't mentioned, then only the payment methods that aren't dependent on the Adyen store are displayed. If any of the required customer fields aren't mentioned, then those fields aren't shown to the customer prior to using the payment link. 

For example, if the value `{"PaymentLinkDuration":"02:00", "Store":"Test_Store", "RequiredShopperFields":"email,name,phone,billingAddress,deliveryAddress"}` is added to the **Custom Settings** property, the Adyen payment connector sets the payment link expiration to two hours, the payment link is associated to the **Test_Store**, and the customer must to enter their name, email, phone, delivery address and billing address before making the payment. 

For test environments, you must set the **Gateway environment** property of the Adyen connector in the hardware profile to **Test**. 

For production environments, set the value of the **Gateway environment** property to **Live** and set the **Optional Domain** property of the Adyen connector in the hardware profile to the prefix value located in the Adyen customer portal.

1. Sign in to the live environment of the Adyen customer portal.
1. In the left pane under **Developers**, select **API URLs**.
1. For **Select a data center**, select the appropriate data center based on your region.
1. Copy the prefix value that's shown and paste it into the **Optional Domain** property field of the Adyen connector.
1. Run the **9999** distribution schedule job.

## Payment experience for pay by link

On selecting the pay by link payment method, the POS displays a dialog which shows the basic customer information such as name, email and primary delivery address. None of this information is required to generate the payment link, but the information is recorded against the customer details for the payment link. It's possible that some payment methods require some of this payment information, and if this information is missing, then those payment methods don't work. These values are defaulted from the customer who's added to the transaction, but the cashier can change the values before creating the payment link. If no customer is added to the transaction, then the name and email fields are blank, but the store's address is added as the default delivery address. 

Once the payment link is created, the system shows the payment link and a corresponding Quick Response (QR) code. The cashier can copy the payment link and send it to the customer via any communication methods available on their device, or the customer can scan the QR code from their phone.

The payment link is an Adyen-hosted webpage that can be branded according to you needs. Contact Adyen to learn more about the branding options. Some payment methods such as "Buy Now, Pay Later" require the billing address to be provided for the customer. The payment link created by default doesn't include the billing address information. If the "RequiredShopperFields:billingAddress" key value pair is added in the **Custom Settings** property of the hardware profile, then when the payment link is opened, the customer must enter the billing address before being able to see the payment options. While the customer is making the payment, the system automatically checks for the payment status every five seconds, or the cashier can manually check for the payment status by selecting the **Check status**.  

<!--![Screenshot that shows the pay by link user experience in Point of Sale](./media/PBL_main.png)-->

If the cashier needs to cancel the payment link for some reason (for example, the customer wants to add or remove some items), then the cashier can select **Exit Pay By Link** and then select **Cancel payment link**. Once the payment link is cancelled, the payment link is considered expired and can't be used for accepting payments. However, if the customer needs some additional time and the cashier wants to help other customers, then the cashier can select **Cancel payment link**, and then select **Suspend payment link**. Assuming that the cashier has the required permissions, this action suspends the transaction and the cashier can help the next customer in line. This action can also be helpful for "line busting" scenarios where a store associate scans customer items, generates a payment link, and suspends the transaction. Customers can make the payment before reaching the counter, and once they do so the cashier can resume the suspended transaction and check for the payment. If the payment has been received, then a payment line is added on resuming the transaction. If the payment hasn't been received, the cashier can view the incomplete payment line in the **Payments** section of the transaction to check the payment status. 

### Suspended transactions

The suspended transaction screen is updated to include a new **Has payment link** column. A value of **Yes** indicates that a transaction was suspended with an active payment link. The cashier can select the suspended transactions and attempt to void them. For the transactions with payment links, the system first automatically expires any unused payment links. However, the used payment links remain unchanged. It's recommended that the cashier checks for the payment status of the suspended transactions before voiding the transactions.

When the shift is being closed, if the **Void when closing shift** configuration is enabled in the functionality profile for the store, the system follows the same logic explained above and attempts to expire the payment link status of the unused payment links before voiding the suspended transactions.

With Commerce version 10.0.44, the pay by link payment method supports scenarios where the payment needs to be captured and the customer is in the store and wants to make a payment. The pay by link can also be used for capturing customer order deposits, payment for invoices, and customer account deposits in POS. In future releases, the ability to create orders with pending payments will enable scenarios such as the store associate being able to create the customer order with the customer's shipping details and generate a payment link for the customer. The customer will be able to make the payment whenever they are ready. If the payment isn't received within the predefined duration, then the order is cancelled.

## Known limitations

The following are the known limitations of the pay by link payment method with the 10.0.44 release. Some of these will be fixed in future releases. 

- Pay by link doesn't support unreferenced returns, so a payment link can't be generated for negative amounts. However, the original payment is automatically refunded in case of referenced returns.
- Pay by link only supports payments capture. Pay by link links can't be used for authorizing the remaining balance on the customer orders.
- Pay by link doesn't support partial payments using the payment link, and customers can't partially pay by gift card and partially by some other payment method. Instead, the cashier can create a payment link for the partial amount and send it to the customer. Once the payment is received, then the cashier can create the second link for the balance. This limitation is mitigated in Commerce version 10.0.45 release.
- A payment link can't be created when the POS is in offline mode. If the payment link is created while the POS is online but the POS then goes offline, then the system isn't able to check the payment status. The cashier isn't able to cancel the payment link, but the cashier is able to proceed without cancelling the payment link. 
- Some payment methods such as Klarna that require the country code to be provided aren't supported in Commerce version 10.0.44. This limitation is mitigated in the Commerce version 10.0.45 release.

## What-if scenarios

Microsoft has thoroughly tested various scenarios, but there are edge cases which are hard to predict. The following tips can help cashiers resolve issues they may encounter. 

### Scenario 1: The cashier wants to cancel the payment, but the payment link cancellation fails

The payment link dialog is modal, and the cashier can't close it unless the payment link is cancelled or the transaction is suspended. If the payment link cancellation fails either due to connectivity issues or because the POS is offline, then the cashier can suspend the transaction and later recall or void it when the POS comes online. 

However, if a partial payment exists for the transaction, then such transactions can't be suspended. Whenever the payment link can't be cancelled, the system shows an error message but also provides an option to continue without cancelling the payment link. On selecting **Yes**, the payment link dialog is closed. The cashier can then void the existing payment and suspend the transaction. 

If a transaction that has a payment link is voided, then the system tries to expire the active payment link. But cancellation isn't guaranteed. If there are no connection issues and the payment hasn't been made by the payment link, then it is cancelled. However, if there are connection issues or the payment has been made, then the payment link isn't cancelled even though the transaction is voided. 

### Scenario 2: The customer has made a payment or claims to have completed the payment, but the POS is unable to receive the payment

Although the payment process is very fast, some payment methods might take a few extra seconds. If after waiting for a minute the POS doesn't receive the payment, then the cashier can try to cancel the payment link. If the customer has actually made the payment, then the payment link cancellation fails, but if the payment link is cancelled, then it means that the customer payment wasn't successful, and customer's balance isn't affected. Assuming that the payment cancellation fails as the customer has made the payment, then the cashier can suspend the transaction and note down the transaction details for later. This payment would need to be refunded from the Adyen portal by a headquarters user. The cashier can assure the customer that their previous payment would be refunded and create a new transaction for the customer. 
 

