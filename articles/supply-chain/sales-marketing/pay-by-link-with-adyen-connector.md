---
title: Pay-by-link payment with the Dynamics 365 Payment Connector for Adyen (preview)
description: Learn how to accept payments for sales orders with payment links using the Adyen connector.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
ms.topic: how-to
ms.date: 02/11/2026
ms.custom:
  - bap-template
---

# Pay-by-link payment with the Dynamics 365 Payment Connector for Adyen (preview)

[!include [banner](../../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to set up and enable the pay-by-link payment method to capture payments for sales orders by using the Microsoft Dynamics 365 Payment Connector for Adyen. By using pay-by-link functionality, businesses can offer modern payment methods that give their customers the flexibility to choose their preferred way to pay.

By using the pay-by-link payment method, salespeople can generate payment links for their customers, which eliminates the need for customers to share sensitive card details verbally over the phone. This method enhances security and trust. By using these payment links, customers can employ modern payment methods like digital wallets that aren't feasible in traditional phone transactions. Moreover, if customers are undecided about their order, salespeople can create the orders on a payment hold. If customers make the payment within a preconfigured duration, the system releases the order for fulfillment. Otherwise, the order gets canceled.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

### Set up and configure the Adyen portal and connector

Before you can set up and use the pay-by-link payment method for Supply Chain Management, the Dynamics 365 Payment Connector for Adyen must already be set up and configured for your system. Learn more in the following articles:

- [Dynamics 365 Payment Connector for Adyen overview](../../commerce/dev-itpro/adyen-connector.md)
- [Set up Dynamics 365 Payment Connector for Adyen](../../commerce/dev-itpro/adyen-connector-setup.md)

### Link your Supply Chain Management environment to a Dataverse environment

The payment notification service uses Dataverse. Therefore, to receive payment notifications, you must link your Supply Chain Management environment to a corresponding Dataverse environment. Learn more in [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv) and [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv).

### Version requirements

Pay-by-link payment requires Supply Chain Management version 10.0.47 or later.

### License required to set up the connector

To set up pay-by-link payment for Supply Chain Management, you must have a Dynamics 365 Commerce license.

### Security roles required to set up the connector

Some of the steps for setting up pay-by-link payment require you to sign in to Supply Chain Management by using a user account that has either the *Administrator* or *Commerce Payment Administrator* security role in Microsoft Power Platform.

## Set up pay-by-link payment

### Enable the features required for pay by link

To enable pay-by-link payment, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *Enable unified payments experience in POS* – Must be enabled to use pay-by-link payment, but only applies to POS and doesn't affect sales orders in Supply Chain Management. Learn more in [Check out faster with optimized payment flows](../../commerce/dev-itpro/faster-checkout-pos.md).
- *Enable Payments Notification feature* – Enables the infrastructure to receive notifications.
- *Enable Pay By Link Payment feature* – Must be enabled to use pay-by-link payment, but only applies to POS and doesn't affect sales orders in Supply Chain Management.
- *Enable asynchronous payments for sales orders* – Enables the pay-by-link capability for sales orders in Supply Chain Management.

### Find your payment notification service URL

The payment notification service URL is where Adyen sends the payment notifications. You'll need this value later when you create a webhook to receive payment notifications from Adyen.

To find your payment notification service URL, follow these steps:

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce shared parameters**.
1. Open the **Payment notifications** tab.
1. Copy the value shown in the **Payment notifications end point URL** field.

    > [!NOTE]
    > If the **Payment notifications end point URL** field is blank, then you need to connect your Supply Chain Management environment to a Dataverse environment. Learn more [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv) and [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv)

### Create a Microsoft Entra ID application registration

A Microsoft Entra ID application registration lets you establish OAuth credentials for the payment notification service. Payment notifications from Adyen use these credentials to communicate securely with the payment notification service. You'll need these credentials later when you create a webhook to receive payment notifications from Adyen.

Create a new Microsoft Entra ID application registration in your Azure portal by following these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/) by using a work or school account.
1. If your account gives you access to more than one tenant, select your account in the upper-right corner. Then set your portal session to the Microsoft Entra tenant that you want.
1. In the left pane, select the **Microsoft Entra ID** service, and then select **App registrations** \> **New registration**.
1. On the **Register an application** page, enter your application's registration information:

    - **Name** – Enter a meaningful application name. This name is shown to users of the app.
    - **Supported account types** – Any of the available options should work.
    - **Redirect URI** – You don't need this field.

1. Select **Register**.
1. After the new application is registered, on the **Overview** page, copy the values of the following properties:

    - **Application (client) ID**
    - **Directory (tenant) ID**

1. Now you must create a client secret for the application. Go to the **Certificates & secrets** section, and then select **New client secret**. Provide a description and an expiration period for the secret. Ensure that you create a business process for rotating the secret, because payment notifications fail after the secret expires. Copy the secret value, and save it for later use.

### Create a webhook to receive payment notifications from Adyen

To create a new webhook to receive payment notifications from Adyen, follow these steps.

1. Go to the [Adyen portal](https://ca-test.adyen.com/), and then go to the **Developers** section.
1. Create a standard webhook.
1. In the **Server configuration** section, in the **URL** field, paste the **Payment notifications endpoint URL** value that you copied earlier.
1. Keep the default values for the **Method** field (*JSON*) and the **Encryption protocol** field (*TLS v1.3*).
1. In the **Security** section, select **OAuth**, and enter values for the following properties:

    - **Client ID** – Enter the **Application (client) ID** value that you copied earlier from the Microsoft Entra ID application registration.
    - **Client secret** – Enter the **Secret value** value that you copied earlier from the Microsoft Entra ID application registration.
    - **URL** – Enter `https://login.microsoftonline.com/{tenantid}/oauth2/v2.0/token`. Replace *\{tenantid\}* with the **Directory (tenant) ID** value that you copied earlier from the Microsoft Entra ID application registration.
    - **Scope** – Enter *a013b12b-2624-40b4-b15b-b7751d733a22/.default*.

1. Generate a new hash-based message authentication code (HMAC) key and copy it. You aren't able to view this key again, so keep it somewhere safe.
1. In the **Events** section, select **Authorization**.
1. Under **Additional settings**, in the **Card** section, select the **Include card bin** and **Include Subvariant** options.
1. Leave the remaining fields set to their default values, and save the configuration.

> [!NOTE]
> Don't test the configuration yet because you aren't finished setting up the system. You'll validate the configuration after the next step.

### Enter the HMAC and application client ID details

Supply Chain Management uses the HMAC and application client ID details to authenticate the payment notifications sent by Adyen. To enter these details, follow these steps:

> [!IMPORTANT]
> To complete this procedure and save the configuration, sign in to Supply Chain Management by using a user account that has either the *Administrator* or *Commerce Payment Administrator* security role in Microsoft Power Platform.

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce shared parameters**.
1. Open the **Payment notifications** tab.
1. Enter the following values:

    - **Data verification HMAC key** – Enter the HMAC key that you copied earlier when setting up the webhook in the Adyen portal.
    - **Payment notifications client ID** – Enter the **Application (client) ID** value that you copied earlier from the Microsoft Entra ID application registration.

1. On the Action Pane, select **Save**.

#### Test the connection to the payment notification service

To test the connection, follow these steps.

1. Go to the Adyen portal.
1. Edit the webhook that you created earlier, and then select **Test configuration**. If the connection fails, review all the values that you entered when you created the webhook to validate that they're correct. If you make any changes (for example, if you change the keys), wait 20 minutes before you test the connection again. This wait time ensures that caching doesn't affect the test. If the issue persists, contact Microsoft Support.

### Enable pay by link functionality for sales orders

In addition to the generic pay-by-link setup described earlier in this article, complete the following steps to enable the pay by link functionality for sales orders.

1. Go to **Accounts receivable  \> Payments setup** \> **Methods of payment**.
1. Methods of payment with a **Payment type** of *Credit card* or *Electronic payment* now include a section named **Pay by link** on the **General** FastTab. For each method of payment where you want to enable pay by link, make the following settings:
    - **Allow pay by link** – Set to *Yes* to allow salespeople to create payment links for sales orders that use this method of payment. This setting is required to enable the pay by link functionality for the payment method.
    - **Allow pay later** – Set to *Yes* to allow customers to pay later, enabling scenarios where the customer needs some time to confirm the order but wants to reserve the inventory. Pay-later orders are created with a special hold code and remain on hold for a preconfigured duration (as described in the next step). If the customer makes a payment within this duration, then the order is released for fulfillment; otherwise, the order is systematically canceled. Set to *No* to disable pay-later for a payment method.

1. If you chose to enable the pay-later capability for one or more payment methods, go to **Accounts receivable** \> **Setup** \> **Account receivable parameters**, open the **General** tab, and make the following settings on the **Sales setup** FastTab:
    - **Hold code for payment confirmation** – Select the hold code you want to apply to pay-later orders that aren't paid yet. This hold code is automatically applied to orders that are placed on hold when the salesperson selects the **Pay later** option while creating the payment link.
    - **Order hold timeout for pending payments (minutes)** – Enter the number of minutes system should wait for payment. If the customer doesn't pay before this limit expires, then the system cancels the order.

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Payments** \> **Process asynchronous payments for sales orders**. In the dialog, expand the **Run in the background** FastTab and select **Recurrence**. Use the settings here to choose how often the system should check for customer payments (for example, every 15 minutes). Then select **OK** twice to close the dialog and save your setting. These settings schedule the *Process asynchronous payments for sales orders* batch job, which checks for customer payments and updates the status of sales orders accordingly.

### Customize the behavior of payment links

This step is optional. Complete it only if you want to change the default behavior of the payment links.

1. Go to **Account receivables** \> **Payments setup** \> **Payment services**.
1. Open payment service for your Adyen connector.
1. On the **Payment service account** FastTab, in the **Custom settings** property, add key-value pairs for any or all of the following keys (an example is shown later in this step):
    - `PaymentLinkDuration_Orders` – Set the duration for which the payment link is valid. The default value is 24 hours.
    - `Store` – Specify which Adyen store information to include in the payment link. By default, only payment methods that don't depend on the Adyen store are shown.
    - `RequiredShopperFields` – Specify which fields the customers must enter values for before making a payment. By default, the related fields aren't shown to customers before they use the payment link.

    The system uses the default value for any keys that you don't include in the key-value pairs.

    For example, you enter the value `{"PaymentLinkDuration_Orders":"02:00", "Store":"Test_Store", "RequiredShopperFields":"email,name,phone,billingAddress,deliveryAddress"}` for the **Custom settings** property. In this case, the Adyen payment connector sets the payment link expiration to *two hours*, the payment link is associated with the *Test_Store* store, and customers must enter their *name*, *email address*, *phone number*, *delivery address*, and *billing address* before they make the payment.

    > [!TIP]
    > To define the payment link duration to be more than one day, specify the value for the `PaymentLinkDuration` property as described in [System.TimeSpan.Parse method](/dotnet/fundamentals/runtime-libraries/system-timespan-parse).

## The pay-by-link user experience

The following example describes a typical end-to-end user experience for using pay by link with sales orders in Supply Chain Management.

1. A salesperson takes an order by phone and creates a sales order in Supply Chain Management.
1. When the order is ready for payment, the salesperson goes to the **Header** tab of the sales order and, on the **Price and discount** FastTab, selects a **Method of payment** for which **Allow pay by link** is set to *Yes* (as described earlier in this article). Additionally, as with credit cards, the **Settlement type** field on the **Setup** FastTab might need to be set to *None*.
1. On the Action Pane, the salesperson opens the **Manage** tab, opens the  **Credit card** drop-down list, and selects **Create payment link**.

    :::image type="content" source="media/create-payment-link.png" alt-text="The create payment link button for sales orders in Supply Chain Management." lightbox="media/create-payment-link.png":::

1. A page opens that the salesperson uses to create the payment link. Customer information is prepopulated.
1. After the salesperson updates the customer information as needed, they select **Create link** to create the payment link.
1. The salesperson copies the payment link and can use any available communication channel to send it to the customer.
    - If the customer requests more time to make the payment, the salesperson selects the **Pay later** button on the payment link dialog (if this functionality is enabled).
    - If the customer changes their mind about the purchase, the salesperson can cancel the payment link from here.
1. The customer opens the payment link from their phone or computer to complete the payment.
1. The salesperson's screen automatically refreshes every five seconds to check for the payment. As with a credit card authorization, once the payment is received, the system associates the authorization to the order.

## Manually check the payment status of a sales order

To manually check the payment status of a sales order, follow these steps.

1. In Supply Chain Management, go to the **All sales orders** page and open the sales order waiting for payment.
1. On Action Pane, open the **Sales order** tab, from the **Payments** group, select **Asynchronous payments**.
1. A page opens showing the payment links associated with the order. If a payment link status is shown as *Active*, then payments against this link are either not yet processed or the customer hasn't yet paid.
    - To refresh the current payment link status display, select **Check status** on the Action Pane.
    - To cancel a selected payment link, select **Cancel** on the Action Pane. You can only cancel a payment link if the customer hasn't yet used the link for payment.

## Purge old payment authorization notifications

To save storage and keep the notifications page manageable, delete old notifications manually from the **Payment authorization notifications** page or automatically by running the **Purge payment authorization notifications data** batch job. The batch job allows you to specify the number of days that pass before notifications are deleted.

## Enable critical payment notifications for Dynamics 365 Payment Connector for Adyen

You can use the asynchronous payment notification framework to receive crucial and actionable notifications from Adyen, which are then displayed in Commerce headquarters. This functionality provides the operations team with the necessary visibility to take timely actions based on the notifications received. Learn more in [Enable critical payment notifications using the Dynamics 365 Payment Connector for Adyen](../../commerce/dev-itpro/payment-notifications.md).
