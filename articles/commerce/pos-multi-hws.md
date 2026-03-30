---
title: Dedicated payment terminals and prompts for a printer and cash drawer
description: Learn about the capability to have a dedicated payment terminal and prompt the user to select a cash drawer and a receipt printer in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-03-31
ms.custom: 
  - bap-template
---

# Dedicated payment terminals and prompts for a printer and cash drawer

[!include [banner](includes/banner.md)]

This article provides information about the capability to have a dedicated payment terminal and prompt the user to select a cash drawer and a receipt printer in Microsoft Dynamics 365 Commerce.

Modern retailers are searching for ways to streamline the in-store checkout experience. Recent trends toward paperless checkout through electronic payments not only help to make the purchasing experience smoother but also reduce the need to have a full complement of peripheral devices available for every store associate.

Microsoft Dynamics 365 Commerce supports these trends by enabling a scenario where a point of sale (POS) device has a dedicated payment terminal assigned to it, but it doesn't have its own receipt printer or cash drawer. When associates must print a receipt or take a cash payment, they're prompted to select a hardware station where those devices are configured.

## Key terms

| Term | Description |
|---|---|
| Register | The entity that you use to configure an instance of a POS register. |
| Device | A representation of the physical instance of a POS register and the Store Commerce app that is assigned to it. |
| Dedicated hardware station | The hardware station business logic that is built into the Store Commerce app for Windows, Android, and iOS. |
| Drawer kick (d/k) port | A traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network-enabled payment terminals, receipt printers, and cash drawers. |

## Supported POS clients and devices

The Store Commerce app for Windows, Android, and iOS clients supports the functionality described in this article.

This functionality supports network-enabled payment terminals and receipt printers. You can provide cash drawer support by connecting the cash drawer to the network-enabled receipt printer via the d/k port.

The [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3) provides out-of-box support for this functionality. However, other payment connectors might be supported via the Commerce software development kit (SDK) for payments. Supported receipt printers include network-enabled receipt printers from Star Micronics and Epson.

To set up Star Micronics receipt printers, use the Star Micronics Printer Utility to configure the device so that it can be used over the network. This utility also provides the IP address of the device.

To set up Epson receipt printers, use the Epson ePOS-Print utility to set up the device to use network protocols.

For more information about how to set up network peripherals, see [Network peripheral support overview](./dev-itpro/network-peripherals.md).

## Set up a dedicated payment terminal and a prompt for a printer and cash drawer

### Set up hardware profiles

You need two types of hardware profiles. Assign the first profile to the register. Assign the second profile to a hardware station at the store level. Use the second profile to logically group network receipt printers and cash drawers.

#### Set up a hardware profile for the register

Follow these steps to set up the hardware profile for the register:

1. In Dynamics 365 Commerce, search for **Hardware profile**.
1. Select **New**.
1. Assign a hardware profile number, and then enter a description. For example, this hardware profile is assigned to the register, so a description such as **Dedicated with fallback** works well.
1. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Device name | Additional details |
    |---|---|---|---|
    | Printer | Network | *Any* | The device name is case-sensitive. The **Receipt profile ID** should match the **Receipt profile ID** that maps to the network printer in the hardware profile assigned to the hardware station at the channel level. |
    | Cash drawer | Network | *Any* | The device name is case-sensitive. Set the **Use shared shift** option to **Yes**. |
    | EFT service | Adyen | Not applicable | For information about how to set up the out-of-box Adyen connector, see [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3). Other payment connectors can be supported via the [Commerce software development kit (SDK) for payments](./dev-itpro/end-to-end-payment-extension.md). |
    | PIN pad | Network | **MicrosoftAdyenDeviceV001** | None. |

1. In Dynamics 365 Commerce, search for **Registers**.
1. Select a register by selecting the register number, and then select **Edit**.
1. Assign the hardware profile that you created to the register that uses a dedicated payment terminal. The device that you map to this register must use either the Store Commerce app for Windows, the Store Commerce app for Android, or the Store Commerce app for iOS.
1. Select **Save**.
1. On the Action Pane, on the **Registers** tab, select **Configure IP addresses**.
1. On the **PIN pad** FastTab, enter the IP address of the payment terminal. For information about how to get the IP address of the payment terminal by using the Adyen connector, see [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3).
1. Select **Save**.

#### Set up a hardware profile for the receipt printer and cash drawer

Follow these steps to set up the hardware profile that groups the network receipt printer and cash drawer:

1. In Dynamics 365 Commerce, search for **Hardware profile**.
1. Select **New**.
1. Assign a hardware profile number, then enter a description. Use this hardware profile to group the receipt printer and cash drawer. Therefore, a description such as **Network printer and cash drawer** works well.
1. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Description | Additional details |
    |---|---|---|---|
    | Printer | Network | **Epson** or **Star** | The device name is case-sensitive. The **Receipt profile ID** should match the **Receipt profile ID** that maps to the printer in the hardware profile assigned to the register. |
    | Cash drawer | Fallback | **Epson** or **Star** | The device name is case-sensitive. Set the **Use shared shift** option to **Yes**. |

1. Select **Save**.

### Set up hardware stations

You need two hardware stations. Map the first hardware station to the register. Select the second hardware station as it's required whenever a receipt must be printed or a cash drawer must be opened.

#### Register a hardware station

1. In Dynamics 365 Commerce, search for **All stores**.
1. Select a store by selecting its **Retail Channel Id** values, and then select **Edit**.
1. On the **Hardware stations** FastTab, select **Add**.
1. Set the **Hardware station type** field to **Dedicated**.
1. Enter a description, but don't set any other values for this hardware station. Always use this hardware station for the register.

#### Set up a hardware station for the receipt printer and cash drawer

1. In Dynamics 365 Commerce, search for **All stores**.
1. Select a store by selecting its **Retail Channel Id** values, and then select **Edit**.
1. On the **Hardware stations** FastTab, select **Add**.
1. Set the **Hardware station type** field to **Dedicated**.
1. Enter a description. Use this hardware station for the receipt printer and cash drawer.
1. In the **Hardware profile** field, select the hardware profile that you previously created for the receipt printer and cash drawer.
1. Select **Save**.
1. While the hardware station for the receipt printer and cash drawer is still selected, select **Configure IP addresses**.
1. Obtain the IP address for the printer, and enter it as the IP address for both the receipt printer and the cash drawer.
1. Select **Save**.
1. Search for **Distribution schedules**.
1. Select distribution schedule **1090**, and then select **Run now**.
1. Select distribution schedule **1070**, and then select **Run now**.

### Set up the system to prompt for receipt printer and cash drawer selection as required

1. In a supported POS client, close the current shift if a shift is open.
1. Sign in, and then select **Non-drawer drawer operations**.
1. Use the **Manage hardware stations** operation to turn on a hardware station.
1. Select the hardware station that you created for the register to make it active.
1. Sign out of the POS, sign back in, and open a shift.

The payment terminal that you assign to the hardware profile is always active, and the system prompts you if a receipt printer or cash drawer is required.

Many merchants who request this feature are interested in reducing waste by providing email receipts and encouraging electronic payments. Depending on the configuration of the POS, store associates are prompted to select a receipt printer or cash drawer only when a customer wants a physical receipt or wants to pay with cash.

Store associates are prompted to select a hardware station only one time per transaction, unless a receipt must be printed and cash is used for payment, but the hardware profile that you originally selected doesn't include both devices. In that case, the store associate is prompted again to select a hardware station that can be used to complete the transaction.

## Additional resources

[Set up POS hybrid app on Android and iOS](./dev-itpro/hybridapp.md)

[Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3)

[Network peripheral support overview](./dev-itpro/network-peripherals.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
