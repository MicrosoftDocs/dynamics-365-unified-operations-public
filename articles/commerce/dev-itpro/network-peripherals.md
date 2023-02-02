---
# required metadata

title: Support for network peripherals
description: This article provides an overview of network peripherals that are supported in the store.
author: BrianShook
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
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

# Support for network peripherals

[!include [banner](../includes/banner.md)]

This article describes the support for and setup of network peripherals in the store.

## Key terms

| Term | Description |
|---|---|
| Register | The entity that is used to configure an instance of a point of sale (POS) register. |
| Device | A representation of the physical instance of a POS register and the Store Commerce app that is assigned to it. |
| Dedicated hardware station | The hardware station business logic that is built into the Store Commerce apps for Windows, Android, and iOS. |
| Drawer kick (d/k) port | A traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network-enabled payment terminals, receipt printers, and cash drawers. |
| ESC/P | Epson Standard Code for Printers, aslo know as "Escape/P, is printer a control language created by Epson that is commonly used to send commands to point of sale printers. |

## Supported POS clients and devices

Functionality for network peripherals is supported by the Store Commerce apps for Windows, Android, and iOS.

This functionality supports network-enabled payment terminals and receipt printers. You can provide cash drawer support by connecting the cash drawer to the network-enabled receipt printer via the d/k port.

Out-of-box support for this functionality is provided by the [Microsoft Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3). However, other payment connectors might be supported via the Commerce software development kit (SDK). Supported receipt printers include network-enabled receipt printers from Star Micronics and Epson.

Out-of-box support is provided for network protocols for Epson and Star Micronics receipt printers. Cash drawers that are connected to those printers via the d/k port are supported via ESC/P protocols.

## Set up network peripherals

### Adyen payment terminal

For information about how to set up an Adyen payment terminal, see the "POS payment terminal" section in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md#pos-payment-terminal).

### Epson or Star Micronics receipt printer and a cash drawer

For Commerce to support network peripherals, you must implement communication protocols that are unique for each manufacturer. If a printing protocol isn't listed here, it isn't supported out of box and will require customization. 

#### Epson prerequisite

If your printer supports Epson ePOS-Print, see Epson's product manuals for information about how to access the Epson Printers Configuration Website and enable ePOS-Print. When ePOS-Print is configured, the printer will print a chit that shows its IP address after a power cycle.

#### Star Micronics prerequisite

Network-enabled Star Micronics printers that support Ethernet can be configured to use network protocols through the Star Micronics Printer Utility. For information about how to set up Star Micronics devices to support network printing, see the documentation that is provided by Star Micronics. When a device is correctly configured, the IP address of the printer can be obtained through the user interface (UI) of the printer utility.

#### Set up a hardware profile

1. In Dynamics 365 Commerce, search for **Hardware profiles**.
2. Select **New**.
3. Assign a hardware profile number, and then enter a description.
4. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Device name | Additional details |
    |---|---|---|---|
    | Printer | Network | **Epson** or **Star** | The device name is case-sensitive. Assign a **Receipt profile ID**. |
    | Cash drawer | Network | **Epson** or **Star** | The device name is case-sensitive. Set the **Use shared shift** option to **Yes** if the cash drawer will be shared by multiple POS devices. |

5. Select **Save**.

#### Set up the Store Commerce app for Windows, Android, or iOS

To set up the Store Commerce app for Windows, Android, or iOS, follow these steps.

1. In Dynamics 365 Commerce, search for **Registers**.
2. Select a register by selecting the register number, and then select **Edit**.
3. Assign the hardware profile that you just created to the register that should use a dedicated payment terminal. The device that is mapped to this register must use either the Store Commerce application, the "Retail Modern POS - Android" application type, or the "Retail Modern POS - iOS" application type.
4. Select **Save**.
5. On the Action Pane, on the **Registers** tab, select **Configure IP addresses**.
6. On the **Printer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
7. On the **Cash drawer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
8. Select **Save**.
9. Search for **All stores**.
10. Select a store by selecting its **Retail Channel Id** value, and then select **Edit**.
11. On the **Hardware stations** FastTab, select **Add**.
12. Set the **Hardware station type** field to **Dedicated**.
13. Enter a description, but don't specify a hardware profile or set any other values for this hardware station.
14. Select **Save**.
15. Search for **Distribution schedules**.
16. Select distribution schedule **1090**, and then select **Run now**.
17. Select distribution schedule **1070**, and then select **Run now**.

Store Commerce for web doesn't have built-in hardware station logic. If you're using Store Commerce for web, follow these steps.

1. In Dynamics 365 Commerce, search for **All stores**.
2. Select a store by selecting its **Retail Channel Id** value, and then select **Edit**.
3. On the **Hardware stations** FastTab, select **Add**.
4. Set the **Hardware station type** field to **Shared**.
5. Enter a description. This hardware station can be shared by multiple POS clients, including POS clients that have built-in hardware station logic.
6. In the **Hardware profile** field, use the drop-down arrow to assign the hardware profile for network peripherals to this hardware station.
7. Select **Save**.
8. While the hardware station for the receipt printer and cash drawer is still selected, select **Configure IP addresses**.
9. On the printer FastTab, enter the IP address of the printer. Leave the field for the port number blank.
10. On the cash drawer FastTab, enter the IP address of the printer. Leave the field for the port number blank.

    > [!NOTE]
    > For detailed information about how to set up shared hardware stations, see [Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md).

11. Select **Save**
12. Search for **Distribution schedules**.
13. Select distribution schedule **1090**, and then select **Run now**.
14. Select distribution schedule **1070**, and then select **Run now**.

### Sharing network peripherals

Network receipt printers and cash drawers can be shared by multiple POS devices. To share them, you can use a shared hardware station to broker the connection to the devices. Alternatively, if you're using Store Commerce for Windows, Android, or iOS, you can configure the same devices directly in the register properties.

Payment terminals can be shared only if a shared hardware station is deployed to broker the connection to the payment terminal. You can't share a payment terminal by setting the same payment terminal IP address directly at the register level. If you try to use this approach, issues will occur when individual POS clients try to lock and claim the device.

## Related articles

- [Set up POS hybrid app on Android and iOS](./hybridapp.md)
- [Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3)
- [Dedicated payment terminals and prompts for a printer and cash drawer](../pos-multi-hws.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
