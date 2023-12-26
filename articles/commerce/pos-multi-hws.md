---
# required metadata

title: Dedicated payment terminals and prompts for a printer and cash drawer
description: This article provides information about the capability to have a dedicated payment terminal and prompt the user to select a cash drawer and a receipt printer.
author: BrianShook
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2019-03-31
ms.dyn365.ops.version: AX 7.0.1

---

# Dedicated payment terminals and prompts for a printer and cash drawer

[!include [banner](includes/banner.md)]

This article provides information about the capability to have a dedicated payment terminal and prompt the user to select a cash drawer and a receipt printer.

## Overview

Modern retailers are searching for ways to streamline the in-store checkout experience. Recent trends toward paperless checkout through electronic payments not only help to make the purchasing experience smoother but also reduce the need to have a full complement of peripheral devices available for every store associate.

Microsoft Dynamics 365 Commerce supports these trends by enabling a scenario where a point of sale (POS) device has a dedicated payment terminal assigned to it all the time, but it doesn't have its own receipt printer or cash drawer. When associates must print a receipt or take a cash payment, they are prompted to select a hardware station where those devices are configured.

## Key terms

| Term | Description |
|---|---|
| Register | The entity that is used to configure an instance of a POS register. |
| Device | A representation of the physical instance of a POS register and the Store Commerce app that is assigned to it. |
| Dedicated hardware station | The hardware station business logic that is built into the Store Commerce app for Windows, Android, and iOS. |
| Drawer kick (d/k) port | A traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network-enabled payment terminals, receipt printers, and cash drawers. |

## Supported POS clients and devices

The functionality that is described in this article is supported by the Store Commerce app for Windows, Android, and iOS clients.

This functionality supports network-enabled payment terminals and receipt printers. You can provide cash drawer support by connecting the cash drawer to the network-enabled receipt printer via the d/k port.

Out-of-box support for this functionality is provided by the [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3). However, other payment connectors might be supported via the Commerce software development kit (SDK) for payments. Supported receipt printers include network-enabled receipt printers from Star Micronics and Epson.

To set up Star Micronics receipt printers, use the Star Micronics Printer Utility to configure the device so that it can be used over the network. This utility will also provide the IP address of the device.

To set up Epson receipt printers, use the Epson ePOS-Print utility to set up the device to use network protocols.

For more information about how to set up network peripherals, see [Network peripheral support overview](./dev-itpro/network-peripherals.md).

## Set up a dedicated payment terminal and a prompt for a printer and cash drawer

### Set up hardware profiles

You must have two types of hardware profile. The first is assigned to the register. The second is assigned to a hardware station at the store level, and is used to logically group network receipt printers and cash drawers.

#### Set up a hardware profile for the register

To set up the hardware profile that is assigned to the register, follow these steps.

1. In Dynamics 365 Commerce, search for **Hardware profile**.
2. Select **New**.
3. Assign a hardware profile number, and then enter a description. This hardware profile will be assigned to the register itself. Therefore, a description such as **Dedicated with fallback** will suffice.
4. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Device name | Additional details |
    |---|---|---|---|
    | Printer | Network | *Any* | The device name is case-sensitive. The **Receipt profile ID** should be the same as the **Receipt profile ID** that is mapped to the network printer that is set up in the hardware profile that is assigned to the hardware station at the channel level. |
    | Cash drawer | Network | *Any* | The device name is case-sensitive. Set the **Use shared shift** option to **Yes**. |
    | EFT service | Adyen | Not applicable | For information about how to set up the out-of-box Adyen connector, see [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3). Other payment connectors can be supported via the [Commerce software development kit (SDK) for payments](./dev-itpro/end-to-end-payment-extension.md). |
    | PIN pad | Network | **MicrosoftAdyenDeviceV001** | None. |

5. In Dynamics 365 Commerce, search for **Registers**.
6. Select a register by selecting the register number, and then select **Edit**.
7. Assign the hardware profile that you just created to the register that should use a dedicated payment terminal. The device that is mapped to this register must use either the Store Commerce app for Windows, the Store Commerce app for Android, or the Store Commerce app for iOS.
8. Select **Save**.
9. On the Action Pane, on the **Registers** tab, select **Configure IP addresses**.
10. On the **PIN pad** FastTab, enter the IP address of the payment terminal. For information about how to get the IP address of the payment terminal by using the Adyen connector, see [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3).
11. Select **Save**.

#### Set up a hardware profile for the receipt printer and cash drawer

To set up the hardware profile that is used to group the network receipt printer and cash drawer, follow these steps.

1. In Dynamics 365 Commerce, search for **Hardware profile**.
2. Select **New**.
3. Assign a hardware profile number, and then enter a description. This hardware profile will be used to group the receipt printer and cash drawer. Therefore, a description such as **Network printer and cash drawer** will suffice.
4. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Description | Additional details |
    |---|---|---|---|
    | Printer | Network | **Epson** or **Star** | The device name is case-sensitive. The **Receipt profile ID** should be the same as the **Receipt profile ID** that is mapped to the printer that is set up in the hardware profile that is assigned to the register. |
    | Cash drawer | Fallback | **Epson** or **Star** | The device name is case-sensitive. set the **Use shared shift** option to **Yes**. |

5. Select **Save**.

### Set up hardware stations

You must have two hardware stations. The first will be mapped to the register. The second will be selected as it's required, whenever a receipt must be printed or a cash drawer must be opened.

#### Register a hardware station

1. In Dynamics 365 Commerce, search for **All stores**.
2. Select a store by selecting its **Retail Channel Id** values, and then select **Edit**.
3. On the **Hardware stations** FastTab, select **Add**.
4. Set the **Hardware station type** field to **Dedicated**.
5. Enter a description, but don't set any other values for this hardware station. This hardware station will be used for the register at all times. 

#### Set up a hardware station for the receipt printer and cash drawer

1. In Dynamics 365 Commerce, search for **All stores**.
2. Select a store by selecting its **Retail Channel Id** values, and then select **Edit**.
3. On the **Hardware stations** FastTab, select **Add**.
4. Set the **Hardware station type** field to **Dedicated**.
5. Enter a description. This hardware station will be used for the receipt printer and cash drawer.
6. In the **Hardware profile** field, select the hardware profile that you previously created for the receipt printer and cash drawer.
7. Select **Save**.
8. While the hardware station for the receipt printer and cash drawer is still selected, select **Configure IP addresses**.
9. Obtain the IP address for the printer, and enter it as the IP address for both the receipt printer and the cash drawer.
10. Select **Save**
11. Search for **Distribution schedules**.
12. Select distribution schedule **1090**, and then select **Run now**.
13. Select distribution schedule **1070**, and then select **Run now**.

### Set up the system to prompt for receipt printer and cash drawer selection as it's required

1. In a supported POS client, close the current shift, if a shift is open.
2. Sign in, and then select **Non-drawer drawer operations**.
3. Use the **Manage hardware stations** operation to turn on a hardware station.
4. Select the hardware station that you created for the register to make it active.
5. Sign out of the POS, sign back in, and open a shift.

The payment terminal that is assigned to the hardware profile will now always be active, and you will be prompted if a receipt printer or cash drawer is required.

Many merchants who requested this feature are interested in reducing waste by providing email receipts and encouraging electronic payments. Depending on the configuration of the POS, store associates are prompted to select a receipt printer or cash drawer only when a customer wants a physical receipt or wants to pay with cash.

Store associates are prompted to select a hardware station only one time per transaction, unless a receipt must be printed and cash is used for payment, but the hardware profile that was originally selected doesn't include both devices. In that case, the store associate will be prompted again to select a hardware station that can be used to complete the transaction.

## Related articles

- [Set up POS hybrid app on Android and iOS](./dev-itpro/hybridapp.md)
- [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md?tabs=8-1-3)
- [Network peripheral support overview](./dev-itpro/network-peripherals.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
