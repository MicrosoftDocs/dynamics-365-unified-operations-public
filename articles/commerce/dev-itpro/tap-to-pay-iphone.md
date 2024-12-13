---
title: Enable Tap to Pay on iPhone to run the Store Commerce app
description: This article describes how to set up and enable Tap to Pay on iPhone to run the Microsoft Dynamics 365 Commerce Store Commerce app.
author: shajain
ms.date: 12/13/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2024-11-30
---

# Enable Tap to Pay on iPhone to run the Store Commerce app

[!include [banner](../includes/banner.md)]

This article describes how to set up and enable Tap to Pay on iPhone to run the Microsoft Dynamics 365 Commerce Store Commerce app.

Merchants who use the Store Commerce app with the Adyen payment connector on iPhones can allow their store associates to accept various types of in-person payments on the iPhones by enabling and using the Tap to Pay on iPhone capability. This capability prevents the need to use external payment terminals and reduces the cost and maintenance of the hardware peripherals.

## Prerequisites

Enabling the Tap to Pay on iPhone feature requires onboarding from both Adyen and Microsoft. Contact your Adyen representative to complete the onboarding with Adyen, and then contact Microsoft support to enable this feature in your environment. 

This feature is available starting with Commerce version 10.0.40. The minimum versions for the various components are as follows:

- Dynamics 365 Commerce headquarters: 10.0.1935.73
- Commerce Scale Unit (CSU): 9.50.24201.4+
- Store Commerce app on iPhone from App Store: 9.51.24320

This feature requires a dedicated Hardware station that is deployed on the iPhone with the Store Commerce app. 

To test Tap to Pay on iPhone functionality on an iPhone, you must sign in to the iPhone using a Sandbox Apple Account. For more information on Sandbox Apple Accounts, see [Learn about Sandbox Apple Account](https://developer.apple.com/help/app-store-connect/test-in-app-purchases/create-a-sandbox-apple-account/).

> [!NOTE]
> Tap to Pay on iPhone isn't available in all regions. For a list of available regions, see [Tap to Pay on iPhone regions](https://developer.apple.com/tap-to-pay/regions/). 

## Steps to enable and test Tap to Pay on iPhone

Once both Adyen and Microsoft complete the onboarding process, implement the following steps to enable and test the Tap to Pay on iPhone capability.

### Install the Store Commerce app on iPhone

The Tap to Pay on iPhone feature works on iPhones that run the Store Commerce app, which you must install first. For information on how to download and enable the Store Commerce app on iPhones, see [Store Commerce app for mobile platforms](store-commerce-mobile.md#install-the-app).

### Enable Tap to Pay on the hardware profile

To enable Tap to Pay on the hardware profile, follow these steps.

1. In Commerce headquarters, go to the **Registers** form (**Retail and commerce \> Channel setup \> POS setup**) and open the register that's used to run the Store Commerce app on iPhone. 
1. Open the associated hardware profile and ensure that the Adyen connector is configured to accept the credit cards you choose to accept via Tap to Pay on iPhone, such as Visa, MasterCard, and American Express. If the Adyen connector isn't set up yet, you must configure that first. For information on configuring the Adyen connector, see [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md).

> [!NOTE]
> Only the cloud architecture for Adyen connector is supported for Tap To Pay on iPhone, so make sure to set the **Terminal architecture** property of the Adyen connector to **Cloud** instead of **Local**.

Next, you must configure the PIN pad properties in headquarters.

To configure the PIN pad properties, follow these steps.

1. Expand the **PIN pad** FastTab.
1. Add the following properties:
    1. For **PIN pad**, select **Network**.
    2. For **Device name**, enter "MicrosoftAdyenDeviceV001."
    3. Set the **Accept NFC Payments** option added by the Tap to Pay on iPhone feature to **On**. If you don't see this option, contact Microsoft to enable the Tap to Pay on iPhone feature in your environment.

The following example image shows the **Accept NFC Payments** property on the hardware profile when the Tap to Pay on iPhone option is enabled.
![Accept NFC payments](../media/Accept_NFC_Payments.png)

### Associate a payment method with the store

Tap to Pay on iPhone doesn't need a new payment method to be added to the store. It relies on the existing payment method that is mapped to the **Pay card** operation. In headquarters, go to the **All stores** form (**Retail and commerce \> Channels \> Stores**) and verify that there's a payment method associated to the **Pay card** operation. If such a payment method isn't defined for the store, then create a new payment method to capture credit or debit cards.

### Enable a Hardware station for the store

For information on enabling a dedicated Hardware station for the store, see [Connect peripherals to the point of sale (POS)](../define-maintain-channel-clients-registers-hw-stations.md#store-commerce-app-with-connected-peripheral-devices).

> [!NOTE]
> The Tap to Pay on iPhone feature requires a dedicated Hardware station. Shared hardware stations aren't supported by the Tap to Pay on iPhone feature.

### (Optional) Enable a PIN pad terminal with Tap To Pay

This optional step is for testing the Tap to Pay on iPhone feature capability. There are scenarios where the Near Field Communication (NFC)-based tap capability isn't sufficient. For example, the customer doesn't have an NFC-enabled card, or the customer wants to use a gift card or a wallet. To support these additional use cases, it's useful to pair the iPhone that runs the Store Commerce app with a PIN pad device. To do so, in headquarters navigate to the register used with the iPhone. Under the **Hardware** section on the top toolbar, select **Configure IP address** and then set the details under the PIN pad FastTab. For information about PIN pad onboarding, see [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md#onboard-and-configure-an-adyen-payment-terminal).

### Test with test and live environments

For test environments, you must set the **Gateway environment** property of the Adyen connector in the hardware profile to **Test**.

For live environments, the **Gateway environment** property value of the Adyen connector depends on whether you want to pair the iPhone with an external PIN pad terminal or not. 
- If you don't want to pair an external PIN pad terminal with an iPhone, set the **Gateway environment** property of the Adyen connector to **Custom**. You must also set the **Optional Domain** property value of the Adyen connector in the hardware profile to the prefix value located in the Adyen customer portal. To find the prefix value, sign in to the live environment of Adyen customer portal and on the left pane under **Developers**, select **API URLs**. For **Select a data center**, select the appropriate data center based on your region. Next, copy the **Prefix** value shown and paste it into the **Optional Domain** property field of the Adyen connector. The following example image shows the **API URLs** page with the **Prefix** property value masked.

![Prefix value from Adyen customer portal](../media/Prefix.png)

- If you want to pair an external PIN pad terminal with an iPhone, set the **Gateway environment** property of the Adyen connector to **Live**. You must also set the **Custom Settings** property value of the Adyen connector in the hardware profile to `iOSCustomGatewayTTP:<"paste prefix here">`. For example, if the prefix value is "ecc3f8b08d323232-MS" the **Custom Settings** property value is `iOSCustomGatewayTTP:"ecc3f8b08d323232-MS"`.

    > [!NOTE]
    > The prefix value should be passed within double quotes.

The following example image shows a screenshot of the hardware profile with sample data for when the gateway environment property is set to **Live**. 

![Hardware profile sample with Live setup](../media/sampleHWP.png)

After you set the **Gateway environment** property, in headquarters go to **Retail and Commerce IT \> Distribution schedule** and run the **9999** schedule job to update the channel components with your changes.

## The Tap to Pay on iPhone user experience

- When a store associate is ready to take a payment for a transaction, they select the subtotal amount of the transaction which then opens a list of supported payment methods.
- If the Tap to Pay on iPhone feature is enabled, a **Tap to Pay on iPhone** button is displayed as the first payment method.
- Selecting **Tap to Pay on iPhone** displays a screen for the store associate to choose the amount that should be captured via Tap to Pay on iPhone. This screen displays a **Tender payment** button on the bottom toolbar.
- If the optional PIN pad isn't configured with the Store Commerce app, selecting **Pay card** also triggers the Tap to Pay on iPhone experience. However, if an external PIN pad is configured, when you select **Pay card** the PIN pad is activated instead of the Tap to Pay on iPhone experience.
- Selecting **Tender payment** activates the Tap to Pay screen on the iPhone that displays the selected amount.
- The store associate can then request that the customer tap their physical card or mobile phone with a digital wallet on the iPhone.
- Once the payment is successful, the user sees an approved message and a payment line is added to the transaction.
- Optionally, the **Change due** dialog displays unless it's configured to be hidden when there's no balance due. This step concludes the transaction.

The following example image shows screenshots of the user experience of Store Commerce app with Tap to Pay on iPhone enabled.

![Store Commerce App with Tap to Pay on iPhone](../media/TTP_ux.png)

## Limitations of the Tap to Pay on iPhone feature

The Tap to Pay on iPhone feature has a limitation related to customer orders where Tap to Pay on iPhone can't be used to authorize the remaining balance of a customer order. For this scenario, the merchant can either capture the full order amount as a deposit via Tap to Pay on iPhone, or use the **Pay the balance later** option for the customer order. Alternatively, the merchant can pair the iPhone with a physical PIN pad device and use that device for balance authorizations. 



[!INCLUDE [footer-include](../../includes/footer-banner.md)]
