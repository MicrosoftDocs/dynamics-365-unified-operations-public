---
title: Support for network peripherals
description: This article provides an overview of network peripherals supported by the Microsoft Dynamics 365 Commerce Store Commerce apps for Windows, Android, and iOS.
author: ritakimani1
ms.date: 08/02/2024
ms.topic: overview
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2019-03-31
ms.custom: 
  - bap-template
---

# Support for network peripherals

[!include [banner](../includes/banner.md)]

This article provides an overview of network peripherals supported by the Microsoft Dynamics 365 Commerce Store Commerce apps for Windows, Android, and iOS.

## Key terms

| Term | Description |
|---|---|
| Register | The entity that is used to configure an instance of a point of sale (POS) register. |
| Device | A representation of the physical instance of a POS register and the Store Commerce app that is assigned to it. |
| Dedicated hardware station | The hardware station business logic that is built into the Store Commerce apps for Windows, Android, and iOS. |
| Drawer kick (DK) port | A traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network-enabled payment terminals, receipt printers, and cash drawers. |
| ESC/P | Epson Standard Code for Printers (also known as "Escape/P") is printer a control language created by Epson that is commonly used to send commands to point of sale printers. |

## Supported POS clients and devices

Functionality for network peripherals is supported by the Store Commerce apps for Windows, Android, and iOS.

This functionality supports network-enabled payment terminals and receipt printers. You can provide cash drawer support by connecting the cash drawer to the network-enabled receipt printer via the DK port.

Out-of-box support for this functionality is provided by the [Microsoft Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3). However, other payment connectors might be supported via the Commerce software development kit (SDK). Supported receipt printers include network-enabled receipt printers from Star Micronics and Epson.

Out-of-box support is provided for network protocols for Epson and Star Micronics receipt printers. Cash drawers that are connected to those printers via the d/k port are supported via ESC/P protocols.

## Set up network peripherals

### Adyen payment terminal

For information about how to set up an Adyen payment terminal, see the "POS payment terminal" section in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md#pos-payment-terminal).

### Epson or Star Micronics receipt printer and a cash drawer

For Commerce to support network peripherals, you must implement communication protocols that are unique for each manufacturer. If a printing protocol isn't listed here, it isn't supported out-of-box and requires customization. 

> [!NOTE]
> - For network printers, Store Commerce only supports using the "en-us" locale identifier. Other locale identifiers, including those that specify right-to-left text direction, aren't supported.
> - To use a locale identifier other than "en-us", set up the POS printer as a "Windows driver device" (only supported with Interprocess Communications [IPC] hardware stations) or as an "OPOS device". For configuration details, see [OPOS device setup and configuration](../retail-peripherals-overview.md#opos-device-setup-and-configuration) and [IPC (built-in) hardware station configuration](../retail-peripherals-overview.md#modern-pos-for-windows-with-an-ipc-built-in-hardware-station-1).

#### Epson prerequisite

If your printer supports Epson ePOS-Print, see your Epson product manual for information on how to access the Epson printers configuration website. On the configuration website, enable ePOS-Print and ensure that the printer is set up to transmit data to port 80. When ePOS-Print is configured, after a power cycle the printer prints a chit that shows the printer's IP address.

> [!NOTE]
> - If the printer is producing an ePOS payload (or garbage), this could indicate that ePOS printing isn't enabled on the network printer, or that the incorrect port might be configured.
> - For Epson network printers, port 9100 is designated for RAW printing and shouldn't be used for printing with Store Commerce. Ensure that the printer is set up to transmit data to port 80. When configuring the IP address of the networking printer in Dynamics 365 Commerce, leave the port number field empty to default to port 80.
> - If printing to the default port results in an HTTP 404 error, this could indicate that either ePOS printing isn't enabled on the printer, or it isn't supported by the printer.

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
    | Cash drawer | Network | **Epson** or **Star** | The device name is case-sensitive. Set the **Use shared shift** option to **Yes** if the cash drawer is shared by multiple POS devices. |

5. Select **Save**.

#### Set up the Store Commerce app for Windows, Android, or iOS

To set up the Store Commerce app for Windows, Android, or iOS, follow these steps.

1. In Dynamics 365 Commerce, search for **Registers**.
2. Select a register by selecting the register number, and then select **Edit**.
3. Assign the hardware profile that you created to the register that should use a dedicated payment terminal. The device mapped to this register must use either the Store Commerce application, the "Retail Modern POS - Android" application type, or the "Retail Modern POS - iOS" application type.
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

Payment terminals can only be shared if a shared hardware station is deployed to broker the connection to the payment terminal. You can't share a payment terminal by setting the same payment terminal IP address directly at the register level. If you try to use this approach, you will encounter issues when individual POS clients try to lock and claim the device.

## Related articles

- [Set up POS hybrid app on Android and iOS](./hybridapp.md)
- [Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3)
- [Dedicated payment terminals and prompts for a printer and cash drawer](../pos-multi-hws.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
