---
title: Enable Pay by Link in point of sale using Adyen connector 
description: Learn how to set up and enable Pay by Link payment method to capture payments in stores.
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

# Enable Pay by Link payment method to capture payments using point of sale

[!include [banner](../includes/banner.md)]

The document details how administrators can enable Pay by Link (PBL) for their stores. PBL allows merchants to offer modern payment methods, providing customers with the flexibility to choose their preferred payment method. This payment method also eliminates the need for a payment terminal, facilitating store associates to be mobile and accept various types of payments. Additionally, as explained later in this document, PBL can serve as an effective tool for reducing checkout lines by enabling customers to pay from their current location, thereby expediting the checkout process. PBL is a controlled release, so please contact your Adyen account manager to check availability for participation in the pilot release. 

## Prerequisites

### Enable OAuth authentical from Adyen
The payment notification for pay by link payment method leverages OAuth based authentication and hence before proceeding with setting up, it is required that OAuth authentication is enabled by both Dynamics 365 Commerce team and Adyen. To enable OAuth from D365 Commerce, a flight needs to be enabled. Contact Microsoft support to enable this in your Commerce environments. Similarly, contact your Adyen representative to enable OAuth authentication for webhooks for your Merchant account. Additionally, please request Adyen to set the “Time to Live” (TTL) for the OAuth token to be defined as 3599 seconds i.e., 1 second less than an hour, which is the default TTL value for OAuth token in Azure. 

> [!NOTE]
> If the OAuth TTL cannot be set to 3599 from Adyen, then contact Microsoft support for instructions to override the default TTL value in the Microsoft Azure portal.

### Link Commerce environment to Dataverse environment
Another requirement to receive payment notifications is to link your Commerce environment to a corresponding Dataverse environment. This is because the payment notification service leverages Dataverse and thus it is required to link the two environments. Refer to the following documents if the two environments are not already connected.
https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv 

https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv 

### Minimum required versions
The Pay by Link (PBL) feature is available starting 10.0.44 release and the minimum required versions for various components are mentioned below:
1.	**Store Commerce App/ Cloud Point of Sale**: 9.54.25148.1
2.	**Commerce Scale Unit**: 9.54.25137.4
3.	**Commerce HQ**: Any 10.0.44 version

### Required role to complete the setup
Some of the steps require a Commerce HQ user who should be either an administrator or have 'Commerce Payment Administrator' role assigned in Power platform.

## Setup
### Step 1: Enable the features required for Pay by Link. 

To enable the payment notifications for pay by link, enable the following features from the Feature management workspace:
1.	Enhanced wallet support and payment improvements (learn more: https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/wallets)
2.	Enable unified payments experience in POS (learn more: https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/faster-checkout-pos)
3.	Enable Payments Notification Feature (new feature flag)
4.	Enable Pay By Link Payment Feature (new feature flag)

### Step 2: Create a webhook to receive payment notification from Adyen
The following information is required to create a webhook in the Adyen portal:
a.	Payment notification service URL
b.	OAuth credentials to authenticate against the payment notification service
Payment notification service URL is the URL where the notifications will be sent by Adyen. It can be retrieved from Commerce HQ. To do so, navigate to the **Commerce Shared Parameters** -> **Payment notifications**. Copy the value shown in the field named **"Payment notifications end point URL"**. If this field does not show any value, then it means that the Commerce environment is not linked to Dataverse environment. Please contact your Commerce administrator or contact Microsoft support for help.
To create the OAuth credentials, you need to register a new application using Azure portal. Payment notifications from Adyen will use this application credentials to securely communicate with the Payment notification service. Here are the detailed steps to register a new application.

#### Register a new application by using the Azure portal
- Sign in to the Microsoft Azure portal (https://portal.azure.com/) with a work or school account.
- If your account gives you access to more than one tenant, select your account in the upper-right corner, and set your portal session to the Microsoft Entra tenant that you want.
- In the left pane, select the Microsoft Entra ID service, and then select **App registrations** > **New registration**.
- When the Register an application page appears, enter your application's registration information:
  - **Name**: Enter a meaningful application name that will be shown to users of the app.
  - **Supported account types**: Any of the available options should work
  - **Redirect URI** is not needed
  - Select **Register**

Once the app is registered, then from the Overview page, copy the following two properties:
- **Application (client) ID**
- **Directory (tenant) ID**
Refer the below image for the copying these fields.

![Screenshot that shows the Client ID and Tenant ID properties on Azure portal](./media/App%20registration_1.png)

Next, you need to create a client secret for this application. To do so, select the **“Certificates & secrets"** section and select the **"New client secret"** button. Provide a description to the secret along with a desired expiration period for this secret. Please ensure to create a business process on rotating this secret as the payment notifications will fail once this secret expires. **Copy** the secret value and save it somewhere for later use. Refer the below image for copying the secret value.

![Screenshot that shows the Client sercret location in Azure portal](./media/App%20registration_2.png)

Navigate to Adyen portal and create a new webhook by navigating to the Developers section. Create a **"Standard webhook"**. Under the "Server configuration" section, paste the value copied for **"Payment notifications end point URL"** in the URL field.
Keep the default values for Method as **JSON** and Encryption protocol as **TLS v1.3**
Under the **Security** section, select "OAuth" option and fill in the properties described below:

- **Client ID**: Enter the value for "Application (client) ID copied earlier.
- **Client Secret**: Enter the value for "Secret value" copied earlier.
- **URL**: Enter https://login.microsoftonline.com/{tenantid}/oauth2/v2.0/token after replacing the {tenantID} with the "Directory (tenant) ID" value copied earlier.
- **Scope**: Enter a013b12b-2624-40b4-b15b-b7751d733a22/.default 

![Screenshot that shows the OAuth settings in Adyen](./media/Adyen_OAuth.png)

Next, generate a new HMAC key and copy it. You will not be able to view this key again, hence save it somewhere safe. 
In the Events section select **"Authorisation"**.
Under Additional settings, in the **Card** section select **"Include card bin"** and **"Include Subvariant"** options.
Leave the rest of the fields as is and save the configuration. 

> [!NOTE]
> Do not test the configuration yet as the setup is not yet complete. The configuration will be validated after the next step.

### Step 3: Update Commerce HQ with the HMAC and Application client ID details to authenticate the payment notifications sent by Adyen
Navigate to **Commerce shared parameters** in Commerce HQ and open the **"Payment notification"** section and fill in the properties as described below:
**Data verification HMAC key**: Enter the HMAC key copied earlier.
**Payment notifications client id**: Enter the value for "Application (client) ID” copied earlier.
Save the configuration. 

> [!NOTE]
> Only those Commerce HQ users will be able to save the configuration who have either “Administrator” or “Commerce Payment Administrator” role in Power Platform

**This completes the connection between payment notification service and Adyen. **

#### Test the connection to payment notification service
To test the connection, navigate back to Adyen portal and edit the webhook that was created earlier and select **"Test configuration"** to test the connection. If the connection fails, then validate all the steps above to ensure the values are correct. If any changes are made such as keys are changed, then please wait 20 mins for the test again as it ensures no caching is impacting the test. If the issue persists, contact Microsoft support.


### Step 4: Setup Pay by Link payment method for the store.
Pay by Link (PBL) payment method can be either created as a new payment method so that it can be displayed in the list of payment methods or a dedicated button be created for it. Or, it can be added to the existing payment method created for credit/debit cards so that when a cashier selects the existing payment method, then the point of sale can show PBL as one of the input types for payment capture. In either case, for PBL option to be displayed, the admin needs to select "Pay By Link" as one of the "Payment input type" for a payment method. If you want to create a dedicated payment method for PBL then only select the Pay By Link option, but if you want to add PBL as one of the options to capture payments, then select "Payment on terminal" and "Manual entry" (optional) along with "Pay By Link" option

> [!NOTE]
> The Payment input type option will only be available for payment methods for which the **‘Function’** is set as "Card" or "Wallet”, and **‘Operation name’** is "Pay card".  

![Screenshot that shows the payment input type options in Commerce HQ](./media/payment_input_type.png)

If the “Manual entry” is added as a Payment input type, then on POS, when the cashier chooses this payment method, the shopper will be prompted to manually input the credit card number on the payment terminal. Additionally, enabling Manual entry will set the property **“Allow manual card numbers”** under **“Electronic payment setup”** to True and it will be disabled. If later the manual entry is removed, then the property “Allow manual card numbers” will remain disabled but it can now be edited by the user.

To support payment options such as QR code-based wallets, setting up bin ranges does not suffice. Thus, new card types would have to be created and mapped to corresponding payment variants as described here (Wallet payment support - Commerce | Dynamics 365 | Microsoft Learn). These card types need to be added to the payment method where the PBL is enabled. 

> [!NOTE]
> If you are creating a new payment method for Pay by Link, you do not need to add the "Electronic payment types" that are already added to another payment method available for this store. For example, if Visa, Mastercard, American Express are already added to the Cards payment method, then you do not need to add them again to the PBL payment method. The system looks through all the payment methods associated to the store to find a matching ‘Electronic payment type’ used for payment.

PBL does not require Hardware station to be enabled for Cloud point of sale or the Store Commerce App. Thus, if you want to use PBL with a register which will NOT be paired to a hardware station then the register to be configured to use Commerce Scale Unit (aka Retail server) for Card not present processing. To do so, navigate to the Register form in HQ and in the General section, set the value for **"Card not present processing"** to **"Use retail server"**.

![Screenshot that shows the payment input type options in Commerce HQ](./media/Register_CNP.png)

> [!IMPORTANT]
> If you do not intend to pair the hardware station with the Point of sale, then please contact Microsoft support to enable the flight named “Payments.PayByLinkVisibleWhenHWSOrTerminalInactive” in your environment. This flight will be automatically enabled starting 10.0.45.

### Step 5: Define the behavior for payment link
You can control some payment link experiences by configuring the "Custom Settings" in the Adyen connector section of the Hardware profile used by the register. Here are the experiences that you can control: 
- **Payment expiration duration**- This is controlled by adding the HH:MM value against the property "PaymentLinkDuration"
- **Include the Adyen store information in the payment link** - This is controlled by adding value against the property "Store"
- **Require shoppers to enter their information before payment** - This is controlled by adding value against the property "RequiredShopperFields"

You can skip any of these properties from the Custom Settings. So, if the payment link expiration is not mentioned, then Adyen’s default value of 24 hours will be used. If the Store property is not mentioned, then only the payment methods which are not dependent on the Adyen store will be displayed. If any of the required shopper fields are not mentioned, then those fields will not be shown to the shopper prior to using the payment link. 

For example, the value below added to the "Custom Settings" property of the Adyen payment connector will set the payment link expiration to **2 hours**, the payment link will be associated to the **"Test_Store"** and the shopper will have to enter their **name, email, phone, delivery address and billing address** before making the payment. 

**{"PaymentLinkDuration":"02:00", "Store":"Test_Store", "RequiredShopperFields":"email,name,phone,billingAddress,deliveryAddress"}**

For **Test** environments, you must set the **“Gateway environment”** property of the Adyen connector in the hardware profile to **Test**. 
For **Production** environments, set the value of the Gateway environment property to **Live** and set the **Optional Domain** property of the Adyen connector in the hardware profile to the prefix value that you can find in the Adyen customer portal.
- Sign in to the live environment of the Adyen customer portal.
- In the left pane, under Developers, select API URLs.
- For Select a data center, select the appropriate data center, based on your region.
- **Copy the Prefix value** that is shown. Refer the below image showing the Prefix property on the API URLs page whose value needs to be copied.
- Paste the value into the field for the **Optional Domain** property of the Adyen connector.
- Run **9999** distribution schedule job.

**This completes the setup for Pay by Link.**

## Payment experience for Pay by Link: 
On selecting the PBL payment method, the POS displays a dialog which shows the basic customer information such as Name, Email and Primary delivery address. None of these are required to generate the payment link, however, these are recorded against the shopper details for the payment link. However, it is possible that some payment methods require some of this payment information, and if this information is missing, then those payment methods will not work. These values are defaulted from the customer who is added to the transaction, but the cashier can change the values before creating the payment link. If no customer is added to the transaction, then the name and email fields are blank, but the store's address is added as the default delivery address. 
Once the payment link is created, the system shows the payment link and a corresponding Quick Response (QR) code. The cashier can copy the payment link and send it to the customer via any communication methods available on their device, or alternatively, the customer can scan the QR code from their phone.
The payment link is an Adyen hosted web page which can be branded as per the merchant's needs. Contact Adyen to learn more about the branding options. Some payment methods, especially Buy Now Pay Later payment methods require the billing address to be provided for the customer. However, the payment link created by default does not include the billing address information, thus, as mentioned in the Step 5 above, if the key value pair **"RequiredShopperFields":"billingAddress"** has been added in the "Custom Settings" property of the hardware profile, then on opening the payment link, first the shopper would have to enter the billing address and then they will be able to see the payment options. While the customer is making the payment, the system will automatically check for the payment status after every 5 seconds or the cashier can manually check for the payment status by clicking the "Check status" button.  

![Screenshot that shows the Pay by Link user experience in Point of Sale](./media/PBL_main.png)

If for some reason, the cashier needs to cancel the payment link, for example, the customer wants to add or remove some items then the cashier can press **"Exit Pay By Link"** button and then press **"Cancel payment link"**. Once the payment link is cancelled, the payment link will be considered expired and cannot be used for accepting payments. However, if the customer needs some additional time and, in the meantime, the cashier wants to help other customers, then the cashier can press **"Cancel payment link"** and then press **"Suspend payment link"**. Assuming the cashier has the required permissions, then this action will suspend the transaction, and the cashier can help the next customer line. This can also be helpful for the "Line Busting" scenarios where a store associate can scan the items of the customers, generate a payment link and suspend the transaction. The customers can make the payment before reaching the counter and once they do, the cashier can resume the suspended transaction and check for the payment. If the payment has been received, then a payment line will be added on resuming the transaction. If the payment has not been received, the cashier can view the incomplete payment line in the **"Payments"** section of the transaction and check the payment status. 

### Suspended transactions:
The suspended transaction screen has been updated to include a new column **"Has payment link”**. A value of Yes indicates that this transaction was suspended with an active payment link. The cashier can multi-select the suspended transactions and attempt to void the transactions. For the transactions with payment link, the system will first automatically expire any unused payment links, however, the used payment links will remain unchanged. So, it is recommended to check for the payment status of the suspended transactions prior to voiding the transactions.
Additionally, when the shift is being closed, if the configuration **"Void when closing shift"** is enabled in the functionality profile for the store, then the system will follow the same logic as explained above and attempt to expire the payment link status of the unused payment links, before voiding the suspended transactions.

With 10.0.44, the PBL payment method supports the scenarios where the payment needs to be **"captured”**, and the customer is in the store and wants to make a payment. Thus, apart from the above-mentioned scenario, the PBL can also be used for capturing **customer order deposit**, **payment for invoices** and **customer account deposit** in POS.  In future releases, the ability to create orders with pending payments will be released which will enable scenarios such that the store associate would be able to create the customer order with customer's shipping details and generate a payment link for the customer. The customer would be able to make the payment from the comfort of their home, whenever they are ready. If the payment is not received within the predefined duration, then the order will be cancelled.

## Known limitations
Here are the known limitations of the PBL payment method with the 10.0.44 release. Some of these will be fixed in future releases. 
1.	PBL does not support unreferenced returns and hence a payment link cannot be generated for negative amounts. However, the original payment will be automatically refunded in case of referenced returns.
2.	PBL only supports payments Capture. Thus, PBL link cannot be used for authorizing the remaining balance on the customer orders.
3.	PBL does not support partial payments i.e., using the payment link, the customer cannot pay partially by gift card and partially by some other payment method. Instead, the cashier can create a payment link for the partial amount and send it to the customer. Once the payment is received, then the cashier can create the second link for the balance. This limitation will be mitigated on 10.0.45.
4.	Payment link cannot be created when the POS is in offline mode. Additionally, if the payment link was created while the POS was online, but then the POS goes offline, then the system will not be able to check the payment status. Moreover, the cashier will not be able to cancel the payment link, however, as explained in the "What if" section below, the cashier will be able to proceed without cancelling the payment link. 
5.	Some payment methods such as Klarna which require the country code to be provided, are not supported in 10.0.44. However, this limitation will be mitigated in the 10.0.45 release.

## What-if scenarios
We have thoroughly tested various scenarios, but we know there are edge cases which are hard to predict. We have provided some tips which can help the cashier get unblocked in case they run into issues: 

**Scenario 1: The cashier wants to cancel the payment, but the payment link cancellation fails.**
The payment link dialog is modal, and the cashier cannot close it unless the payment link is cancelled, or the transaction is suspended. Thus, if the payment link cancellation fails either due to connectivity issues or because the POS is offline, then the cashier can suspend the transaction and later recall or void it when the POS comes online. 
However, if a partial payment exists for the transaction, then such transactions cannot be suspended. Thus, whenever the payment link cannot be cancelled, the system shows an error message but also provides an option to continue without cancelling the payment link. On selecting yes, the payment link dialog will be closed. Now the cashier can void the existing payment and suspend the transaction. 
Note: If a transaction which has a payment link is voided, then the system tries to expire the active payment link, but this is not guaranteed. If there are no connection issues and the payment has not been made by the payment link, then it would be cancelled. However, if there are connection issues or the payment has been made, then the payment link will not be cancelled although the transaction will be voided. 

**Scenario 2: The customer has made a payment or claims to have completed the payment, but the POS is unable to receive the payment**
Although the payment process is very fast, i.e., payments are recognized usually within 5 seconds of the customer completing the payment, but some payment methods might take a few extra seconds. Assuming, even waiting for a minute the POS does not receive the payment then, the cashier can try to cancel the payment link. If the customer has truly made the payment, then the payment link cancellation will fail but if the payment link is cancelled, then it means that the customer payment was not successful, and customer's balance would not be affected. Assuming the payment cancellation fails as the customer has made the payment, then the cashier can suspend the transaction and note down the transaction details for later. This payment would need to be refunded from the Adyen portal by an HQ user. The cashier can assure the customer that their previous payment would be refunded and create a new transaction for the customer. 
 

