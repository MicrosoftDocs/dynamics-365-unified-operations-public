---
title: Support for network peripherals
description: This article provides an overview of network peripherals supported by the Microsoft Dynamics 365 Commerce Store Commerce apps for Windows, Android, and iOS.
author: ritakimani1
ms.date: 02/18/2026
ms.topic: overview
ms.reviewer: v-griffinc
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
| Register | The entity used to configure an instance of a point of sale (POS) register. |
| Device | A representation of the physical instance of a POS register and the Store Commerce app that is assigned to it. |
| Dedicated hardware station | The hardware station business logic built into the Store Commerce apps for Windows, Android, and iOS. |
| Drawer kick (DK) port | A traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network-enabled payment terminals, receipt printers, and cash drawers. |
| ESC/P | Epson Standard Code for Printers (also known as "Escape/P") is printer a control language created by Epson that is commonly used to send commands to point of sale printers. |

## Supported POS clients and devices

The Store Commerce apps for Windows, Android, and iOS support functionality for network peripherals.

This functionality supports network-enabled *payment terminals* and *receipt printers*. You can provide *cash drawer* support by connecting the cash drawer to the network-enabled receipt printer via the DK port.

The [Microsoft Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3) provides out-of-box support for network-enabled payment terminals. Other payment connectors might be supported via customizations. For more information on extending payment integrations, see [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md).

The functionality provides out-of-box support for network-enabled receipt printers for network protocols for Epson and Star Micronics receipt printers. Cash drawers that are connected to those printers via the DK port are supported via Epson Standard Code for Printers (ESC/P) protocols.

## Set up network peripherals
 
### Adyen payment terminal

For information about how to set up an Adyen payment terminal, see the "POS payment terminal" section in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md#pos-payment-terminal).

### Epson or Star Micronics receipt printer and a cash drawer

For Commerce to support network peripherals, you must implement communication protocols that are unique for each manufacturer. If a printing protocol isn't listed here, it's not supported out of the box and requires customization. 

> [!NOTE]
> - For network-enabled printers, Store Commerce only supports using the "en-us" locale identifier. Other locale identifiers, including identifiers that specify right-to-left text direction, aren't supported.
> - To use a locale identifier other than "en-us," set up the POS printer as a "Windows driver device" (only supported with Interprocess Communications [IPC] hardware stations) or as an "OPOS device." For configuration details, see [OPOS device setup and configuration](../retail-peripherals-overview.md#opos-device-setup-and-configuration) and [IPC (built-in) hardware station configuration](../retail-peripherals-overview.md#modern-pos-for-windows-with-an-ipc-built-in-hardware-station-1).

#### Epson prerequisite

If your printer supports Epson ePOS-Print, see your Epson product manual for information on how to access the Epson printers configuration website. On the configuration website, enable ePOS-Print and ensure that the printer is set up to transmit data to port 80. When you configure ePOS-Print, after a power cycle the printer prints a chit that shows the printer's IP address.

> [!NOTE]
> - If the printer is producing an ePOS payload (or garbage), this condition might indicate that ePOS printing isn't enabled on the network printer, or that the incorrect port might be configured.
> - For Epson network printers, port 9100 is designated for RAW printing and shouldn't be used for printing with Store Commerce. Ensure that the printer is set up to transmit data to port 80. When configuring the IP address of the networking printer in Dynamics 365 Commerce, leave the port number field empty to default to port 80.
> - If printing to the default port results in an HTTP 404 error, this condition might indicate that either ePOS printing isn't enabled on the printer, or it isn't supported by the printer.

#### Star Micronics prerequisite

Network-enabled Star Micronics printers that support Ethernet can be configured to use network protocols through the Star Micronics Printer Utility. For information about how to set up Star Micronics devices to support network printing, see the documentation that is provided by Star Micronics. When a device is correctly configured, the IP address of the printer can be obtained through the user interface (UI) of the printer utility.

#### Set up a hardware profile

1. In Dynamics 365 Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Select **New**.
1. Assign a hardware profile number, and then enter a description.
1. On the FastTabs for different device types, set up the following device types.

    | Device | Type | Device name | Additional details |
    |---|---|---|---|
    | Printer | Network | **Epson** or **Star** | The device name is case-sensitive. Assign a **Receipt profile ID**. |
    | Cash drawer | Network | **Epson** or **Star** | The device name is case-sensitive. Set the **Use shared shift** option to **Yes** if the cash drawer is shared by multiple POS devices. |

1. Select **Save**.
   
#### Enable a dedicated or shared hardware station

To enable a *dedicated* hardware station, follow these steps in Commerce headquarters for each store for which you want to configure network-enabled receipt printers and cash drawers.

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores** and select the store for which you're configuring a network-enabled receipt printer or cash drawer.
1. On the **Hardware Station** FastTab, select **Add**.
1. For **Hardware Station type**, select **Dedicated**.
1. Enter a description, but don't specify a hardware profile or set any other values for this hardware station.
1. Select **Save** to save changes to the store.
1. Search for **Distribution schedules**.
1. Select distribution schedule **1070 (Channels job)**, and then select **Run now**.

To enable a *shared* hardware station, follow these steps in Commerce headquarters for each store for which you want to configure network-enabled receipt printers and cash drawers. 

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores** and select the store for which you're configuring a network-enabled receipt printer or cash drawer.
1. Select the store by selecting its **Retail Channel Id** value, and then select **Edit**.
1. On the **Hardware stations** FastTab, select **Add**.
1. Set the **Hardware station type** field to **Shared**.
1. Enter a description. This hardware station can be shared by multiple POS clients, including POS clients that have built-in hardware station logic.
1. Enter a host name for the hardware station.
1. In the **Hardware profile** field, use the drop-down arrow to assign the hardware profile for the network-enabled peripherals you created to this hardware station.
1. Select **Save** to save changes to the store.
1. Search for **Distribution schedules**.
1. Select distribution schedule **1070 (Channels job)**, and then select **Run now**.

For detailed information about how to set up shared hardware stations, see [Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md). 

 > [!NOTE]
 > - Store Commerce for web doesn't support dedicated (built-in) hardware station logic. If you're configuring peripherals for Store Commerce for web, set up a shared hardware station and configure each peripheral's IP address at the store level.
 > - Network-enabled receipt printers and cash drawers can be shared by multiple POS devices. To share them, use a shared hardware station to broker the connection to the devices. Alternatively, if you're using Store Commerce for Windows, Android, or iOS, you can configure the same devices directly in the register properties.
 > - Payment terminals can only be shared if a shared hardware station is deployed to broker the connection to the payment terminal. You can't share a payment terminal by setting the same payment terminal IP address directly at the register level. If you try to use this approach, you encounter problems when individual POS clients try to lock and claim the payment terminal.

#### Set up a Dynamics 365 Commerce register

For a setup that uses *dedicated* (in-built) hardware station, follow these steps:

1. In headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**.
1. Select the register you want to configure by selecting the register number, and then select **Edit**.
1. Assign the hardware profile for the network-enabled peripherals that you created to the register.
1. Select **Save**.
1. On the Action Pane, on the **Registers** tab, select **Configure IP addresses**.
1. On the **Printer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
1. On the **Cash drawer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
1. Select **Save**.
1. Search for **Distribution schedules**.
1. Select distribution schedule **1090**, and then select **Run now**.
1. Select distribution schedule **1070**, and then select **Run now**.

For a setup that uses *shared* hardware station, follow these steps: 

> [!NOTE]
> - Configure peripheral IP addresses at the store level.
> - If you're using Store Commerce for Web, configure peripheral IP addresses at the store level. 

1. In headquarters, go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Select the store by selecting its **Retail Channel Id** value, and then select **Edit**.
1. On the **Hardware stations** FastTab, select the shared hardware station that you configured.
1. While the hardware station for the receipt printer and cash drawer is selected, select **Configure IP addresses**.
1. On the **Printer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
1. On the **Cash drawer** FastTab, enter the IP address of the printer. Leave the field for the port number blank.
1. Select **Save**.
1. Search for **Distribution schedules**.
1. Select distribution schedule **1090**, and then select **Run now**.
1. Select distribution schedule **1070**, and then select **Run now**.

## Additional resources

[Set up POS hybrid app on Android and iOS](./hybridapp.md)

[Dynamics 365 Payment Connector for Adyen](./adyen-connector.md?tabs=8-1-3)

[Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md)

[Dedicated payment terminals and prompts for a printer and cash drawer](../pos-multi-hws.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
