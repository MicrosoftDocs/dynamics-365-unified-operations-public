---
title: Enable Tap to Pay on iPhone to run the Store Commerce app
description: Learn how to set up and enable Tap to Pay on iPhone to run the Microsoft Dynamics 365 Commerce Store Commerce app.
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

Merchants that use the Store Commerce app with the Adyen payment connector on iPhones can enable the Tap to Pay on iPhone capability. Store associates can then accept various types of in-person payments on the iPhones. Tap to Pay on iPhone eliminates the need to use external payment terminals. It also reduces the cost and maintenance of hardware peripherals.

## Prerequisites

Before the Tap to Pay on iPhone feature can be enabled, onboarding from both Adyen and Microsoft is required. Contact your Adyen representative to complete the onboarding with Adyen. Then contact Microsoft Support, and ask to have the feature enabled in your environment.

This feature is available as of Commerce version 10.0.40. The minimum versions for the various components are as follows:

- **Dynamics 365 Commerce headquarters:** 10.0.1935.73
- **Commerce Scale Unit (CSU):** 9.50.24201.4
- **Store Commerce app on iPhone from App Store:** 9.51.24320

This feature requires that a dedicated Hardware station is deployed on the iPhones where the Store Commerce app is installed.

To test the Tap to Pay on iPhone capability on an iPhone, you must sign in to the iPhone by using a Sandbox Apple Account. Learn more about Sandbox Apple Accounts in [Create a Sandbox Apple Account](https://developer.apple.com/help/app-store-connect/test-in-app-purchases/create-a-sandbox-apple-account/).

> [!NOTE]
> Tap to Pay on iPhone isn't available in all regions. You can find the list of available regions in [Countries and regions](https://developer.apple.com/tap-to-pay/regions/).

## Enable and test Tap to Pay on iPhone

After both Adyen and Microsoft complete the onboarding process, follow these steps to enable and test the Tap to Pay on iPhone capability.

### Install the Store Commerce app on iPhone

The Tap to Pay on iPhone feature works on iPhones that run the Store Commerce app. You must install the app first. Learn how to download and enable the Store Commerce app on iPhones in [Install the app](store-commerce-mobile.md#install-the-app).

### Enable Tap to Pay in the hardware profile

To enable Tap to Pay in the hardware profile, follow these steps.

1. In Commerce headquarters, go to **Retail and commerce** \> **Channel setup** \> **POS setup**.
1. On the **Registers** page, open the register that is used to run the Store Commerce app on iPhone. 
1. Open the associated hardware profile.
1. Ensure that the Adyen connector is configured to accept the credit cards that you want to accept via Tap to Pay on iPhone, such as Visa, MasterCard, and American Express. If the Adyen connector isn't set up yet, you must do that setup first. Learn how to configure the Adyen connector in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md).

> [!NOTE]
> Only the cloud architecture for Adyen connector is supported for Tap To Pay on iPhone. Therefore, be sure to set the **Terminal architecture** property of the Adyen connector to **Cloud** instead of **Local**.

Next, you must configure the PIN pad properties in headquarters.

To configure the PIN pad properties, follow these steps.

1. In the hardware profile, on the **PIN pad** FastTab, for the **PIN pad** property, select **Network**.
1. For the **Device name** property, enter **MicrosoftAdyenDeviceV001**.
1. The Tap to Pay on iPhone feature adds an option that is named **Accept NFC Payments**. Set this option to **Yes**. If this option doesn't appear on the **PIN pad** FastTab, contact Microsoft Support, and ask to have the Tap to Pay on iPhone feature enabled in your environment.

The following example image shows the configuration of PIN pad properties for a hardware profile. Because the Tap to Pay on iPhone feature is enabled, those properties include the **Accept NFC Payments** option.

![Screenshot that shows the configuration of PIN pad properties, including the Accept NFC Payments option, for a hardware profile.](../media/Accept_NFC_Payments.png)

### Associate a payment method with the store

Tap to Pay on iPhone doesn't require that a new payment method is added to the store. Instead, it relies on the existing payment method that is mapped to the **Pay card** operation. In headquarters, go to **Retail and commerce** \> **Channels** \> **Stores**. On the **All stores** page, confirm that a payment method is associated with the **Pay card** operation. If no such payment method is defined for the store, create a new payment method to capture credit or debit cards.

### Enable a Hardware station for the store

Learn how to enable a dedicated Hardware station for a store in [Store Commerce app with connected peripheral devices](../define-maintain-channel-clients-registers-hw-stations.md#store-commerce-app-with-connected-peripheral-devices).

> [!NOTE]
> The Tap to Pay on iPhone feature requires a dedicated Hardware station. It doesn't support shared hardware stations.

### (Optional) Enable a PIN pad terminal with Tap To Pay on iPhone

This optional step is used to test the Tap to Pay on iPhone capability. In some scenarios, the Near Field Communication (NFC)-based tap capability isn't sufficient. For example, the customer might not have an NFC-enabled card, or the customer might want to use a gift card or a wallet.

To support these additional use cases, it's useful to pair the iPhone that runs the Store Commerce app with a PIN pad device. In headquarters, go to the register that is used with the iPhone. On the Action Pane, on the **Register** tab, in the **Hardware** group, select **Configure IP address**. Then set the details on the **PIN pad** FastTab. Learn about PIN pad onboarding in [Onboard and configure an Adyen payment terminal](adyen-connector-setup.md#onboard-and-configure-an-adyen-payment-terminal).

### Test with test and live environments

For test environments, you must set the **Gateway environment** property of the Adyen connector in the hardware profile to **Test**. For live environments, the value of the **Gateway environment** property depends on whether you want to pair the iPhone with an external PIN pad terminal.

- If you don't want to pair an external PIN pad terminal with an iPhone, set the **Gateway environment** property of the Adyen connector to **Custom**. You must also set the **Optional Domain** property of the Adyen connector in the hardware profile to the prefix value that you can find in the Adyen customer portal.

    1. Sign in to the live environment of the Adyen customer portal.
    1. In the left pane, under **Developers**, select **API URLs**.
    1. For **Select a data center**, select the appropriate data center, based on your region.
    1. Copy the **Prefix** value that is shown. The following example image shows the **Prefix** property on the **API URLs** page. (The property value is masked in the image.)

        ![Screenshot that shows the Prefix property and masked value on the API URLs page in the Adyen customer portal.](../media/Prefix.png)

    1. Paste the value into the field for the **Optional Domain** property of the Adyen connector.

- If you want to pair an external PIN pad terminal with an iPhone, set the **Gateway environment** property of the Adyen connector to **Live**. You must also set the **Custom Settings** property of the Adyen connector in the hardware profile to **iOSCustomGatewayTTP:\<*Prefix*\>**, where **\<*Prefix*\>** is the prefix value in double quotation marks. For example, if the prefix value is **"ecc3f8b08d323232-MS"**, the value of the **Custom Settings** property is **iOSCustomGatewayTTP:"ecc3f8b08d323232-MS"**.

    > [!NOTE]
    > The prefix value should be passed in double quotation marks.

The following example image shows the configuration of a hardware profile where the **Gateway environment** property is set to **Live**.

![Screenshot of a hardware profile that has sample data for a Live setup.](../media/sampleHWP.png)

After you set the **Gateway environment** property, in headquarters, go to **Retail and Commerce IT** \> **Distribution schedule**, and run the **9999** schedule job to update the channel components with your changes.

## The Tap to Pay on iPhone user experience

- When the store associate is ready to take a payment for a transaction, they select the subtotal amount of the transaction. A list of supported payment methods is then opened.
- If the Tap to Pay on iPhone feature is enabled, a **Tap to Pay on iPhone** button is shown as the first payment method.
- If the user selects **Tap to Pay on iPhone**, a page appears where the store associate can specify the amount that should be captured via Tap to Pay on iPhone. This page includes a **Tender payment** button on the bottom toolbar.
- If no optional external PIN pad is configured with the Store Commerce app, the Tap to Pay on iPhone experience can also be triggered by selecting **Pay card**. However, if an external PIN pad is configured, selecting **Pay card** activates the PIN pad instead of triggering the Tap to Pay on iPhone experience.
- Selecting **Tender payment** activates the Tap to Pay screen on the iPhone. This screen shows the selected amount.
- The store associate can then ask the customer to tap their physical card, or their mobile device that has a digital wallet, on the iPhone.
- After the payment is successful, the user receives an approval message, and a payment line is added to the transaction.
- The **Change due** dialog box appears, unless it's configured to be hidden if no balance is due. This step concludes the transaction.

The following example image shows screenshots of the user experience in the Store Commerce app when Tap to Pay on iPhone is enabled.

![Screenshots that show the user's experience of paying by using the Store Commerce app with Tap to Pay on iPhone.](../media/TTP_ux.png)

## Limitations of the Tap to Pay on iPhone feature

Tap to Pay on iPhone can't be used to authorize the remaining balance of a customer order. In this scenario, the merchant has several options:

- Capture the full order amount as a deposit via Tap to Pay on iPhone.
- Use the **Pay the balance later** option for the customer order.
- Pair the iPhone with a physical PIN pad device, and use that device for balance authorizations.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
