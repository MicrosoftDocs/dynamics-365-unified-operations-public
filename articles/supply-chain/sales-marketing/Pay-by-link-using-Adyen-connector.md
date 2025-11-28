---
title: Accept payments for sales orders with payment links using Adyen connector
description: Learn how to accept payments for sales orders with payment links using the Adyen connector.
author: Shalabh Jain
ms.author: shajain
ms.topic: how-to
ms.date: 11/28/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Accept payments with payment links using Adyen connector

[!include [banner](../../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article explains how to set up and enable the pay by link payment method to capture payments for SCM orders using the Microsoft Dynamics 365 Payment Connector for Adyen. Pay by link functionality enables businesses to offer modern payment methods that give customers the flexibility to choose their preferred payment method. 

## Prerequisites

### Link your SCM environment to a Dataverse environment
The payment notification service uses Dataverse. Therefore, to receive payment notifications, you must link your SCM environment to a corresponding Dataverse environment. Learn more in [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv) and [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv).

### Minimum required versions
SCM version 10.0.46

> [!NOTE]
> Pay by link functionality is in private preview. Contact Microsoft support for enabling the capability in your environment.

### License requirements
To **setup** Pay by link using Adyen connector, Dynamics 365 Commerce license is required.

### Required role to complete the setup
Some of the steps require a SCM user who is either an **Administrator** or has the **Commerce Payment Administrator** role assigned to them in Microsoft Power platform.

## Setup

### Enable the features required for pay by link

To enable payment notifications for pay by link, you must enable the following features in the **Feature management** workspace:
- The unified payments experience in POS. Learn more in [Check out faster with optimized payment flows](/dynamics365/commerce/dev-itpro/faster-checkout-pos). This feature is applicable for Point of Sale only and will have no impact on the SCM orders, however, it must be enabled.
- The **Enable Payments Notification feature**. This feature enables the infrastructure to receive notifications.
- The **Enable Pay By Link Payment feature**. This feature is applicable for Point of Sale only and will have no impact on the SCM orders, however, it must be enabled.
- The  **Enable asynchronous payments for sales orders**. This feature enables the pay by link capability for SCM orders.

### Create a webhook to receive payment notifications from Adyen

The following information is required to create a webhook in the Adyen portal:

- The URL of the payment notification service
- OAuth credentials for authentication against the payment notification service

The payment notification service URL is where Adyen sends the payment notifications. You can get this URL from **Retail and Commerce** module. Go to **Commerce shared parameters** \> **Payment notifications**, and copy the value of the **Payment notifications end point URL** field. If the field is blank, the SCM environment isn't linked to a Dataverse environment. In this case, contact your SCM administrator or Microsoft Support for help.

To create the OAuth credentials, you must register a new application in the Azure portal. Payment notifications from Adyen use this application's credentials to communicate securely with the payment notification service.

#### Register a new application in the Azure portal

To register a new application in the Azure portal, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/) by using a work or school account.
1. If your account gives you access to more than one tenant, select your account in the upper-right corner. Then set your portal session to the Microsoft Entra tenant that you want.
1. In the left pane, select the **Microsoft Entra ID** service, and then select **App registrations** \> **New registration**.
1. On the **Register an application** page, enter your application's registration information:

    - **Name**: Enter a meaningful application name. This name is shown to users of the app.
    - **Supported account types**: Any of the available options should work.
    - **Redirect URI**: This field isn't needed.

1. Select **Register**.

After the new application is registered, on the **Overview** page, copy the values of the following properties:

- Application (client) ID
- Directory (tenant) ID

Next, you must create a client secret for the application. Go to the **Certificates & secrets** section, and then select **New client secret**. Provide a description and an expiration period for the secret. Ensure that you create a business process for rotating the secret, because payment notifications fail after the secret expires. Copy the secret value, and save it somewhere for later use.

To create a new webhook, follow these steps.

1. Go to the Adyen portal, and then go to the **Developers** section.
1. Create a standard webhook.
1. In the **Server configuration** section, in the **URL** field, paste the **Payment notifications endpoint URL** value that you copied earlier.
1. Keep the default values for the **Method** field (**JSON**) and the **Encryption protocol** fields (**TLS v1.3**).
1. In the **Security** section, select **OAuth**, and enter values for the following properties:

    - **Client ID**: Enter the **Application (client) ID** value that you copied earlier.
    - **Client secret**: Enter the **Secret value** value that you copied earlier.
    - **URL**: Enter `https://login.microsoftonline.com/{tenantid}/oauth2/v2.0/token`. Replace **\{tenantID\}** with the **Directory (tenant) ID** value that you copied earlier.
    - **Scope**: Enter **a013b12b-2624-40b4-b15b-b7751d733a22/.default**.

1. Generate a new Hash-based Message Authentication Code (HMAC) key, and copy it. You aren't able to view this key again, so keep it somewhere safe.
1. In the **Events** section, select **Authorization**.
1. Under **Additional settings**, in the **Card** section, select the **Include card bin** and **Include Subvariant** options.
1. Leave the remaining fields set to their default values, and save the configuration.

> [!NOTE]
> Don't test the configuration yet, because the setup isn't completed. The configuration is validated after the next step.

### Update Commerce module with the HMAC and application client ID details to authenticate the payment notifications sent by Adyen

To update the details to authenticate the payment notifications that Adyen sends, follow these steps.

1. Within the Commerce module, go to **Commerce shared parameters**.
1. In the **Payment notification** section, enter values for the following properties:

    - **Data verification HMAC key**: Enter the HMAC key that you copied earlier.
    - **Payment notifications client ID**: Enter the **Application (client) ID** value that you copied earlier.

1. Save the configuration.

    > [!NOTE]
    > Only those users who have either the **Administrator** or **Commerce Payment Administrator** role in Microsoft Power Platform can save the configuration.

#### Test the connection to the payment notification service

To test the connection, follow these steps.

1. Go to the Adyen portal.
1. Edit the webhook that you created earlier, and then select **Test configuration**. If the connection fails, review all the values that you entered when you created the webhook to validate that they're correct. If you make any changes (for example, if you change the keys), wait 20 minutes before you test the connection again. In this way, you ensure that caching doesn't affect the test. If the issue persists, contact Microsoft Support.


### Enable pay by link functionality for SCM orders 

In addition to the generic pay by link setup described earlier in this article, the following additional steps are required to enable the pay by link functionality for SCM orders.

1. Navigate to the "Methods of payment" form under **Accounts receivable  \> Payments setup**. The methods of payment with "Payment type" value as "Credit card" or "Electronic payment" show a new section named **PAY BY LINK. This section shows two configurations, namely **Allow pay by link** and **Allow pay later**. The "Allow pay by link" configuration is required for creating a payment link, however the configuration "Allow pay later" is optional. This configuration enables the capability to allow the customers to pay later for the order thus enabling scenarios where the customer needs some time to confirm the order but wants to reserve the inventory. Such pay later orders are created with a special hold code and remain on hold for a preconfigured duration. If the customer makes a payment within this duration, then the order is released for fulfillment, else the order is systematically cancelled.
1. To enable the Pay later capability, it is required to define the hold code to be applied to orders to be paid later via a payment link. To do so, go to the **Account receivable parameters** \> **General** \> **Sales setup** FastTab, and for the **Hold code for payment confirmation** configuration, select a hold code. Additionally, define the duration in minutes that is allowed for the customer to make a payment for the order. If the customer doesn't make a payment during this duration, then the system cancels the order. To define the payment duration, go to the **Account receivable parameters** \> **General** \> **Sales setup** FastTab and select a value for the **Order hold timeout for pending payments (minutes)** configuration.
1. Schedule the **Process asynchronous payments for sales orders** batch job to run at the desired interval (for example, every 15 minutes) to check for customer payments.

### Define the behavior for the payment link

This is an optional step and is only needed if you want to change the default behavior of the payment links. You can control some payment link experiences by configuring the following key-value pairs in the **Custom Settings** property in the Adyen connector. 

- **Payment expiration duration** - To control how long does the payment link is valid, add a value for the **PaymentLinkDuration_Orders** key.
- **Inclusion of the Adyen store information in the payment link** - To control this experience, add a value for the **Store** key.
- **Requirement for shoppers to enter their information before payment** - To control this experience, add a value for the **RequiredShopperFields** key.

You can skip adding any of the preceding key-value pairs in **Custom Settings**; if you don't add a value for the **PaymentLinkDuration** key, Adyen's default duration of 24 hours is used. If you don't add a value for the **Store** key, only payment methods that don't depend on the Adyen store are shown. If you don't add a value for the **RequiredShopperFields** key, the related fields aren't shown to customers before they use the payment link.

For example, you add the value `{"PaymentLinkDuration":"02:00", "Store":"Test_Store", "RequiredShopperFields":"email,name,phone,billingAddress,deliveryAddress"}` for the **Custom Settings** property. In this case, the Adyen payment connector sets the payment link expiration to two hours, the payment link is associated with the **Test_Store** store, and customers must enter their name, email address, phone number, delivery address, and billing address before they make the payment.

> [!NOTE]
> To define the payment link duration to be more than one day, see [System.TimeSpan.Parse method](/dotnet/fundamentals/runtime-libraries/system-timespan-parse) for instructions on how to specify the value for the **PaymentLinkDuration** property.


## End-to-end user experience for SCM orders

The following example describes a typical end-to-end user experience for a SCM order.

- A SCM user helps create an order for a customer over the phone.
- When the order is ready for payment, navigate to the order header and under the "Price and discount" fast tab, select the Payment and Method of payment for which the configuration "Allow pay by link" was enabled. Additionally, like credit cards, the property "Settlement type" under the "Setup " fast tab might need to set to "None".
Open the **Manage** tab for the sales order and expand the **Credit card** dropdown. A button named "Create payment link" is displayed. Refer the below image showcasing this button. 

- The SCM user selects the "Create payment link" button and a form is displayed. This form is used for creating the payment link and has the customer information prepopulated.
- After the SCM user updates the customer information as needed, the SCM user selects **Create link** to create the payment link. 

> [!NOTE]
> To send this payment link to the customer, the SCM user can use any communication mechanism available to them on the device where they are using SCM application.

- If the customer changes their mind or requests more time for making a payment, the SCM user can either cancel the payment link from the payment link dialog, or they can use the **Pay later** button on the payment link dialog, if the functionality is enabled. If the **Pay later** option is used, the order is placed on a hold and the customer can make a payment within the predefined duration to process the order. Otherwise, the system cancels the order.
- The customer opens the payment link from their phone or computer to complete the payment.
- The SCM user's screen is automatically refreshed every five seconds to check if the payment is tendered. Once the payment is received, then similar to the authorization via a credit card, the authorization is associated to the order.


### Manually check the payment status for the SCM order

To manually check the payment status of a SCM order, follow these steps.

1. In SCM, go to the **All sales orders** form and open the sales order waiting for payment.
1. On the **Sales order** tab, under the **Payments** submenu, select **Asynchronous payments**. This action opens a form with the payment links associated with the order. If the payment link status is shown as **Active**, the payments against this link are either not yet processed or the customer hasn't yet paid.
1. To check the latest status, select **Check status** to reload the current payment link status. This form also has a **Cancel** button to cancel the payment link. The payment link can only be canceled if the customer hasn't yet used the link for payment.

## Purge old payment authorization notifications

To ensure that old authorization notifications are deleted to save the storage and keep the notifications form manageable, old notifications can either be deleted manually from the **Payment authorization notifications** form, or deleted automatically by running the **Purge payment authorization notifications data** batch job. The batch job allows you to specify the number of days that pass before notifications are deleted.

## Enable critical payment notifications for Adyen connector 

Businesses can use the asynchronous payment notification framework to receive crucial and actionable notifications from Adyen, which are then displayed in Commerce headquarters. This functionality provides the operations team with the necessary visibility to take timely actions based on the notifications received. Learn more in [Enable Critical payment notifications](https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/payment-notifications)

