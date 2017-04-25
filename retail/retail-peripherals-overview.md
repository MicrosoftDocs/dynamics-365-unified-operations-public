---
# required metadata

title: Retail peripherals overview
description: This topic explains the concepts that are related to retail peripherals. It describes the various ways that peripherals can be connected to the point of sale (POS) and the components that are responsible for managing the connection with the POS.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 268444
ms.assetid: 2ea93e43-8019-49a0-a7f8-325565ebc52d
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Retail peripherals overview

[!include[banner](includes/banner.md)]


This topic explains the concepts that are related to retail peripherals. It describes the various ways that peripherals can be connected to the point of sale (POS) and the components that are responsible for managing the connection with the POS.

Concepts
--------

### POS registers

Navigation: Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**. The point of sale (POS) register is an entity that is used to define the characteristics of a specific instance of the POS. These characteristics include the hardware profile or setup for retail peripherals that will be used at the register, the store that the register is mapped to, and the visual experience for the user who signs in to that register.

### Devices

Navigation: Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**. A device is an entity that represents a physical instance of a device that is mapped to a POS register. When a device is created, it’s mapped to a POS register. The device entity tracks information about when a POS register is activated, the type of client that is being used, and the application package that has been deployed to a specific device. Devices can be mapped to the following application types: Retail Modern POS, Retail Cloud POS, Retail Modern POS – Windows Phone, Retail Modern POS – Android, and Retail Modern POS – iOS.

### Retail Modern POS

Modern POS is the POS program for Microsoft Windows. It can be deployed on Windows 10 operating systems (OSs).

### Cloud POS

Cloud POS is a browser-based version of the Modern POS program that can be accessed in a web browser.

### Modern POS for iOS

Modern POS for iOS is an iOS-based version of the Modern POS program that can be deployed on iOS devices.

### Modern POS for Android

Modern POS for Android is an Android-based version of the Modern POS program that can be deployed on Android devices.

### POS peripherals

POS peripherals are devices that are explicitly supported for POS functions. These peripherals are typically divided into specific classes. For more information about these classes, see the “Device classes” section of this topic.

### Hardware station

Navigation: Click **Retail and commerce** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**. Select a store, and then click the **Hardware stations** FastTab. The **Hardware station** setting is a channel-level setting that is used to define instances where the retail peripheral logic will be deployed. This setting at the channel level is used to determine characteristics of the hardware station. It's also used to list hardware stations that are available for a Modern POS instance in a given store. The hardware station is built into the Modern POS program for Windows. The hardware station can also be deployed independently as a stand-alone Microsoft Internet Information Services (IIS) program. In this case, it can be accessed via a network.

### Hardware profile

Navigation: Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**. The hardware profile is a list of devices that are configured for a POS register or a hardware station. The hardware profile can be mapped directly to a POS register or a hardware station.

## Devices classes
POS peripherals are typically divided into classes. This section describes and gives an overview of the devices that Modern POS supports.

### Printer

Printers include traditional POS receipt printers and full-page printers. Printer are supported through Object Linking and Embedding for Retail POS (OPOS) and Microsoft Windows driver interfaces. Up to two printers can be used at the same time. This capability supports scenarios where cash-and-carry customer receipts are printed on receipt printers, whereas customer orders, which carry more information, are printed on a full-page printer. Receipt printers can be connected directly to a computer via USB, connected to a network via Ethernet, or connected via Bluetooth.

### Scanner

Up to two bar code scanners can be used at the same time. This capability supports scenarios where a scanner that is more mobile is required in order to scan large or heavy items, whereas a fixed embedded scanner is used for most standard-sized items, to speed up checkout times. Scanners can be supported through OPOS, Universal Windows Platform (UWP), or keyboard wedge interfaces. USB or Bluetooth can be used to connect a scanner to a computer.

### MSR

One USB magnetic stripe reader (MSR) can be set up by using OPOS drivers. If you want to use a stand-alone MSR for electronic funds transfer (EFT) payment transactions, the MSR must be managed by a payment connector. Stand-alone MSRs can be used for customer loyalty entry, employee sign-in, and gift card entry, independently of the payment connector.

### Cash drawer

Two cash drawers can be supported per hardware profile. This capability enables two active shifts per register to be available at the same time. In the case of a shared shift, or a cash drawer that is used by multiple mobile POS devices at the same time, only one cash drawer is allowed per hardware profile. Cash drawers can be connected directly to a computer via USB, connected to a network, or connected to a receipt printer via an RJ12 interface. In some cases, cash drawers can also be connected via Bluetooth.

### Line display

Line displays are used to show products, transaction balances, and other useful information to the customer during a transaction. One line display can be connected to the computer via USB by using OPOS drivers.

### Signature capture

Signature capture devices can be connected directly to a computer via USB by using OPOS drivers. When signature capture is configured, the customer is prompted to sign on the device. After the signature is provided, it's shown to the cashier for acceptance.

### Scale

Scales can be connected to the computer via USP by using OPOS drivers. When a product that is marked as a “Weighed” product is added to a transaction, the POS reads the weight from the scale, adds the product to the transaction, and uses the quantity that the scale provided.

### PIN pad

Personal identification number (PIN) pads are supported through OPOS, but they must be managed via a payment connector.

### Secondary display

When a secondary display is configured, the number 2 Windows display is used to show basic information. The purpose of the secondary display is to support independent software vendor (ISV) extension, because out of the box, the secondary display isn't configurable and shows limited content.

### Payment device

Payment device support is implemented through the payment connector. Payment devices can perform one or many of the functions that other device classes provide. For example, a payment device can function as an MSR/card reader, line display, signature capture device, or PIN pad. Support for payment devices is implemented independently of the stand-alone device support that is provided for other devices that are included in the hardware profile.

## Supported interfaces
### OPOS

To help guarantee that the largest range of devices can be used with Microsoft Dynamics 365 for Operations - Retail, the OLE for POS industry standard is the primary retail peripheral device platform that is supported in Microsoft Dynamics 365 for Operations - Retail. The OLE for POS standard was produced by the National Retail Federation (NRF), which establishes industry-standard communication protocols for retail peripheral devices. OPOS is a widely adopted implementation of the OLE for POS standard. It was developed in the mid-1990s and has been updated several times since then. OPOS provides a device driver architecture that enables easy integration of POS hardware with Windows–based POS systems. OPOS controls handle communication between compatible hardware and the POS software. An OPOS control consists of two parts:

-   **Control object** – The control object for a device class (such as line displays) provides the interface for the software program. Monroe Consulting Services ([www.monroecs.com](http://www.monroecs.com/)) provides a standardized set of OPOS control objects that are known as the common control objects (CCOs). The CCOs are used to test the POS component of Microsoft Dynamics 365 for Operations - Retail. Therefore, the testing helps guarantee that, if Microsoft Dynamics 365 for Operations - Retail supports a device class through OPOS, many device types can be supported, provided that the manufacturer provides a service object that is built for OPOS. You don't have to explicitly test each device type.
-   **Service object** – The service object provides communication between the control object (CCO) and the device. Typically, the service object for a device is provided by the device manufacturer. However, in some cases, you might have to download the service object from the manufacturer’s website. For example, a more recent service object might be available. To find the address of the manufacturer's website, see your hardware documentation.

[![Control object and service object](./media/retail_peripherals_overview01.png)](./media/retail_peripherals_overview01.png) Support for the OPOS implementation of OLE for POS helps guarantee that, if the device manufacturers and POS publishers implement the standard correctly, POS systems and supported devices can work together, even if they weren't previously tested together. **Note:** OPOS support doesn't guarantee support for all devices that have OPOS drivers. Microsoft Dynamics 365 for Operations - Retail must first support that device type, or class, through OPOS. In addition, service objects might not always be up to date with the latest version of the CCOs. You should also be aware that, in general, the quality of service objects varies.

### Windows

Receipt printing at the POS is optimized for OPOS. OPOS tends to be much faster than printing through Windows. Therefore, it's a good idea to use OPOS, especially in retail environments where 40-column receipts are printed and transaction times must be fast. For most devices, you will use OPOS controls. However, some OPOS receipt printers also support Windows drivers. By using a Windows driver, you can access the latest fonts and network one printer for multiple registers. However, there are drawbacks to using Windows drivers. Here are some examples of these drawbacks:

-   When Windows drivers are used, images are rendered before printing occurs. Therefore, printing tends to be slower than it is on printers that use OPOS controls.
-   Devices that are connected through the printer (“daisy-chained”) might not work correctly when Windows drivers are used. For example, the cash drawer might not open, or the slip printer might not word as you expect.
-   OPOS also supports a more extensive set of variables that are specific to retail receipt printers, such as paper cutting or slip printing.

If OPOS controls are available for the Windows printer that you're using, the printer should still work correctly with Microsoft Dynamics 365 for Operations - Retail.

### Universal Windows Platform

UWP, in the case of retail peripherals, is related to Windows support for Plug and Play devices. When a Plug and Play device is connected to a Windows OS version that supports that type of device, no driver is required for the device to be used as intended. For example, if Windows detects a Bluetooth speaker device, the OS knows that the device has the **Speaker** class type. Therefore, and it treats that device as a speaker. No additional setup is required. In the case of POS devices, many USB devices can be plugged in, and Windows will recognize them as Human Interface Devices (HIDs). However, it might not be able to determine the capabilities that the device provides, because the device doesn't specify the class, or type, of device. In Windows 10, device classes for bar code scanners and MSRs have been added. Therefore, if a device declares itself to Windows 10 as a device of one of these classes, Windows will listen for events from the device at the appropriate times. Modern POS supports UWP MSRs and scanners. Therefore, when it's ready for input from one of these devices, and a device that belongs to one of these classes is connected, the device can be used. For example, if a UWP bar code scanner is plugged into a Windows 10 computer, and bar code sign-in is configured for Modern POS, the bar code scanner will become active on the sign-in screen. No additional setup is required. Additional classes of point of service UWP devices are being added to Windows. These classes include classes for cash drawers and receipt printers. Support for these new device classes in Modern POS is pending.

### Keyboard wedge

Keyboard wedge devices send data to the computer as if that data were typed on a keyboard. Therefore, by default, the field that is active at the POS will receive the data that is scanned or swiped. In some cases, this behavior can cause the wrong type of data to be scanned into the wrong field. For example, a bar code might be scanned into a field that is intended for input of credit card data. In many cases, there is logic at the POS that determines whether the data that is scanned or swiped is a bar code or card swipe. Therefore, the data is handled correctly. However, when devices are set up as OPOS instead of keyboard wedge devices, there is more control over how the data from those devices can be consumed, because more is “known” about the device that the data originates from. For example, data from a bar code scanner is automatically recognized as a bar code, and the associated record in the database is found more easily and faster than if a generic string search were used, as in the case of keyboard wedge devices.

### Native printer

Native (or "Device" as the type is named in the hardware profile) printers can be configured to prompt the user to select a printer that is configured for the computer. When a printer of the **Device** type is configured, if Modern POS encounters a print command, the user is prompted to select a printer in a list. This behavior differs from the behavior for Windows drivers, because the **Windows** printer type in the hardware profile doesn't show a list of printers. Instead, it requires that a named printer be provided in the **Device name** field.

### Windows

The **Windows** device type is used for printers only. When a Windows printer is configured in the hardware profile, the specific printer name must be provided. When Modern POS encounters print events, if a Windows printer is configured, the event will be passed to the specified Windows printer. The user won't be prompted to select a printer.

### Network

Network-addressable cash drawers, receipt printers, and payment terminals can be used over a network, either directly through the Interprocess Communications (IPC) hardware station that is built into the Modern POS for Windows application or through the IIS hardware station for other Modern POS clients.

## Hardware station deployment options
### IPC (built-in)

The Interprocess Communications (IPC) hardware station is built into the Modern POS for Windows application. To use the IPC hardware station, assign a hardware profile to a register that will use the Modern POS for Windows application. Then create a hardware station of the **Dedicated** type for the store where the register will be used. When you start Modern POS, the IPC hardware station will be active, and the POS peripherals that have been configured will be ready to use. If you temporarily don't require the local hardware for some reason, use the **Manage hardware stations** operation to turn off the hardware station capabilities. Modern POS can also use the IPC hardware station to communicate directly with network peripherals.

### IIS

You can use the IIS or stand-alone version of the hardware station in two ways. The descriptor “IIS” implies that the POS application connects to the hardware station via Microsoft Internet Information Services. The POS application connects to the IIS hardware station via web services that run on a computer where the devices are connected. When IIS is used, the retail peripherals that are connected to a hardware station can be used by any POS register that is on the same network as the IIS hardware station. Because only Modern POS for Windows includes built-in support for retail peripherals, all other Modern POS applications must use the IIS hardware station to communicate with POS peripherals that are configured in the hardware profile. Therefore, each instance of the IIS hardware station requires a computer that runs the web service and application that communicates with the devices. The IIS hardware station is required for all non-Windows Modern POS applications.

#### Dedicated

Modern POS uses hardware stations of the **Dedicated** type to detect that peripherals are directly connected to the computer where the app is being used. However, the **Dedicated** type can also be used for IIS hardware stations. In a traditional, fixed POS scenario that uses Cloud POS as the POS application, the **Dedicated** hardware station type is used for IIS hardware stations that are deployed on the same computer that is running Cloud POS. From a retail peripherals perspective, the dedicated IIS hardware station has better retail peripheral support for traditional, fixed POS scenarios. Dedicated hardware stations support all peripherals that are supported in the hardware profile.

#### Shared

Shared hardware stations are intended to be used by multiple POS devices through the course of the day. Shared hardware stations are optimized to support only cash drawers, receipt printers, and payment terminals. You can't directly connect stand-alone bar code scanners, MSRs, line displays, scales, or other devices. Otherwise, conflicts will occur when multiple POS devices try to claim those peripherals at the same time. Here is how conflicts are managed for supported devices:

-   **Cash drawer** – The cash drawer is opened via an event that is sent to the device. The only issue that can occur when a cash drawer is called occurs if the cash drawer is already open. In the case of shared hardware stations, the cash drawer should be set to **Shared** in the hardware profile. This setting prevents the POS from checking whether the cash drawer is already open when it sends open commands.
-   **Receipt printer** – If two receipt printing commands are sent to the hardware station at the same time, one of the commands can be lost, depending on the device. Some devices have internal memory or pooling that can prevent this issue. If a print command isn't successful, the cashier receives an error message and can retry the print command from the POS.
-   **Payment terminal** – If a cashier tries to tender a transaction on a payment terminal that is already being used, a message notifies the cashier that the terminal is being used and asks the cashier to try again later. Usually, cashiers can see that a terminal is already being used and will wait until the other transaction is completed before they try to tender again.

Validation is planned for a future release, to detect whether unsupported devices are set up for a hardware profile that is mapped to a shared hardware station. If any unsupported devices are detected, the user will receive a message that states that the devices aren't supported for shared hardware stations. In the case of shared hardware stations, the **Select upon tendering** option is set to **Yes** at the register level. The POS user is then prompted to select a hardware station when a tender is selected for a transaction at the POS. When the hardware station is selected only at the time of tender, the hardware station selection is added directly to the POS workflow for mobile scenarios. As an additional benefit, the line display on the payment terminal isn't used for shared scenarios. If the payment terminal is used as a line display, other users might be blocked from using that terminal until the transaction is completed. In mobile scenarios, lines might be added to a transaction over a longer period. Therefore, the **Select upon tendering** option is required in order to ensure optimum device availability.

### Network peripherals

The network designation for devices in the hardware profile enables cash drawers, receipt printers, and payment terminals to be connected via a network connection.

#### Modern POS for Windows

You can specify IP addresses for network peripherals in two places. If the Modern POS Windows client is using a single set of network peripherals, you should set the IP addresses for those devices by using the **IP configuration** option on the Action Pane for the register itself. In the case of network devices that will be shared among POS registers, a hardware profile that has network devices assigned to it can be mapped directly to a shared hardware station. To assign IP addresses, select that hardware station on the **Retail stores** page, and then use the **IP configuration** option in the **Hardware stations** section to specify the network devices that are assigned to that hardware station. For hardware stations that have only network devices, you don't have to deploy the hardware station itself. In this case, the hardware station is required only in order to conceptually group network-addressable devices according to their location in the retail store.

#### Cloud POS, Modern POS for iOS, and Modern POS for Android

The logic that drives physically connected and network-addressable peripherals is contained in the hardware station. Therefore, for all POS clients except Modern POS for Windows, an IIS hardware station must be deployed and active to enable the POS to communicate with peripherals, regardless of whether those peripherals are physically connected to a hardware station or addressed over the network.

## Setup and configuration
### Hardware station installation

For information, see [Retail hardware station configuration and installation](retail-hardware-station-configuration-installation.md).

### Modern POS for Windows setup and configuration

For information, see [Retail Modern POS configuration and installation](retail-modern-pos-device-activation.md).

### OPOS device setup and configuration

For more information about OPOS components, see the "Supported interfaces" section of this document. Typically, OPOS drivers are provided by the device manufacturer. When an OPOS device driver is installed, it adds a key to the Windows registry in one of the following locations:

-   **32-bit system:** HKEY\_LOCAL\_MACHINESOFTWAREOLEforRetailServiceOPOS
-   **64-bit system:** HKEY\_LOCAL\_MACHINESOFTWAREWOW6432NodeOLEforRetailServiceOPOS

Within the ServiceOPOS registry location, configured devices are organized according to the OPOS device class. Multiple device drivers are saved.

## Supported scenarios by hardware station type
### Client support – IPC hardware station vs. IIS hardware station

The following table shows the topologies and deployment scenarios that are supported.

| Client      | IPC hardware station | IIS hardware station |
|-------------|----------------------|----------------------|
| Windows app | Yes                  | Yes                  |
| Cloud POS   | No                   | Yes                  |
| Android     | No                   | Yes                  |
| iOS         | No                   | Yes                  |

### Network peripherals

Network peripherals can be supported directly through the hardware station that is built into the Modern POS for Windows application. For all other clients, you must deploy an IIS hardware station.

| Client      | IPC hardware station | IIS hardware station |
|-------------|----------------------|----------------------|
| Windows app | Yes                  | Yes                  |
| Cloud POS   | No                   | Yes                  |
| Android     | No                   | Yes                  |
| iOS         | No                   | Yes                  |

## Supported device types by hardware station type
### Modern POS for Windows with an IPC (built-in) hardware station

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Supported device class</th>
<th>Supported interfaces</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Printer</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver</li>
<li>Device</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="even">
<td>Printer 2</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver</li>
<li>Device</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="odd">
<td>Line display</td>
<td>OPOS</td>
</tr>
<tr class="even">
<td>Dual display</td>
<td>Windows driver</td>
</tr>
<tr class="odd">
<td>MSR</td>
<td><ul>
<li>OPOS</li>
<li>UWP (No setup is required.)</li>
<li>Keyboard wedge (No setup is required.)</li>
</ul></td>
</tr>
<tr class="even">
<td>Drawer</td>
<td><ul>
<li>OPOS</li>
<li>Network <strong>Note:</strong> Only one drawer can be set up if <strong>Use shared shift</strong> is configured on the drawer.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Drawer 2</td>
<td><ul>
<li>OPOS</li>
<li>Network <strong>Note:</strong> Only one drawer can be set up if <strong>Use shared shift</strong> is configured on the drawer.</li>
</ul></td>
</tr>
<tr class="even">
<td>Scanner</td>
<td><ul>
<li>OPOS</li>
<li>UWP (No setup is required.)</li>
<li>Keyboard wedge (No setup is required.)</li>
</ul></td>
</tr>
<tr class="odd">
<td>Scanner 2</td>
<td><ul>
<li>OPOS</li>
<li>UWP (No setup is required.)</li>
<li>Keyboard wedge (No setup is required.)</li>
</ul></td>
</tr>
<tr class="even">
<td>Scale</td>
<td>OPOS</td>
</tr>
<tr class="odd">
<td>PIN pad</td>
<td>OPOS (Support is provided through customization of the payment connector.)</td>
</tr>
<tr class="even">
<td>Signature capture</td>
<td>OPOS</td>
</tr>
<tr class="odd">
<td>Payment terminal</td>
<td><ul>
<li>Custom device support</li>
<li>Network (For more information, see the payment connector documentation.)</li>
</ul></td>
</tr>
</tbody>
</table>

### All Modern POS clients that have a dedicated IIS hardware station

**Note:** When the IIS hardware station is “dedicated,” there is a one-to-one relationship between the POS client and the hardware station.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Supported device class</th>
<th>Supported interfaces</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Printer</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver <strong>Note:</strong> For Windows printers on a network, the user of the hardware station must have permission to access the printer.</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="even">
<td>Printer 2</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="odd">
<td>Line display</td>
<td>OPOS</td>
</tr>
<tr class="even">
<td>MSR</td>
<td>OPOS</td>
</tr>
<tr class="odd">
<td>Drawer</td>
<td><ul>
<li>OPOS</li>
<li>Network <strong>Note:</strong> Only one drawer per hardware profile can be set up if <strong>Use shared shift</strong> is configured on the drawer.</li>
</ul></td>
</tr>
<tr class="even">
<td>Drawer 2</td>
<td><ul>
<li>OPOS</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="odd">
<td>Scanner</td>
<td>OPOS</td>
</tr>
<tr class="even">
<td>Scanner 2</td>
<td>OPOS</td>
</tr>
<tr class="odd">
<td>Scale</td>
<td>OPOS</td>
</tr>
<tr class="even">
<td>PIN pad</td>
<td>OPOS (Support is provided through customization of the payment connector.)</td>
</tr>
<tr class="odd">
<td>Sig. capture</td>
<td>OPOS</td>
</tr>
<tr class="even">
<td>Payment terminal</td>
<td><ul>
<li>Custom device support</li>
<li>Network (For more information, see the payment connector documentation.)</li>
</ul></td>
</tr>
</tbody>
</table>

### All Modern POS clients that have a shared IIS hardware station

**Note:** When the IIS hardware station is “shared,” multiple devices can use the hardware station at the same time. For this scenario, you should use only the devices that are listed in the following table. If you try to share devices that aren't listed here, such as bar code scanners and MSRs, errors will occur when multiple devices try to claim the same peripheral. In the future, such a configuration will be explicitly prevented.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Supported device class</th>
<th>Supported interfaces</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Printer</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver <strong>Note:</strong> For Windows printers on a network, the user of the hardware station must have permission to access the printer.</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="even">
<td>Printer 2</td>
<td><ul>
<li>OPOS</li>
<li>Windows driver</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="odd">
<td>Drawer</td>
<td><ul>
<li>OPOS</li>
<li>Network <strong>Note:</strong> Only one drawer per hardware profile can be set up if <strong>Use shared shift</strong> is configured on the drawer.</li>
</ul></td>
</tr>
<tr class="even">
<td>Drawer 2</td>
<td><ul>
<li>OPOS</li>
<li>Network</li>
</ul></td>
</tr>
<tr class="odd">
<td>Payment terminal</td>
<td><ul>
<li>Custom device support</li>
<li>Network (For more information, see the payment connector documentation.)</li>
</ul></td>
</tr>
</tbody>
</table>

## Configuration for supported scenarios
For more information about how to create hardware profiles, see [Define and maintain channel clients, including registers and hardware stations](define-maintain-channel-clients-registers-hw-stations.md). **Note:** For Microsoft Dynamics 365 for Operations version 1611, the hardware station profile is no longer used. Attributes that you previously set up in the hardware station profile are now part of the hardware station itself.

### Modern POS for Windows with an IPC (built-in) hardware station

This configuration is the most typical configuration for traditional, fixed POS registers. For this scenario, the hardware profile information is mapped directly to the register itself. The EFT terminal number should also be set on the register itself. To set up this configuration, follow these steps.

1.  Create a hardware profile where all the required peripherals are configured.
2.  Map the hardware profile to the POS register.
3.  Create a hardware station of the **Dedicated** type for the retail store where the POS register will be used. A description is optional. **Note:** You don't have to set any other properties on the hardware station. All other required information, such as the hardware profile, will come from the register itself.
4.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
5.  Select the **1090** distribution schedule to sync the new hardware profile to the store. Click **Run now** to sync changes to the POS.
6.  Select the **1040** distribution schedule to sync the new hardware station to the store. Click **Run now** to sync changes to the POS.
7.  Install and activate Modern POS for Windows.
8.  Start Modern POS for Windows, and begin to use the connected peripheral devices.

### All Modern POS clients that have a dedicated IIS hardware station

This configuration can be used for all Modern POS clients that have a hardware station that is used exclusively by one POS register. To set up this configuration, follow these steps.

1.  Create a hardware profile where all the required peripherals are configured.
2.  Create a hardware station of the **Dedicated** type for the retail store where the POS register will be used.
3.  On the dedicated hardware station, set the following properties:
    -   **Host name** – The name of the host computer where the hardware station will run. **Note:** Cloud POS can resolve **localhost** to determine the local computer where Cloud POS is running. However, the certificate that is required in order to pair Cloud POS with the hardware station must also have "Localhost" as the computer name. To avoid issues, we recommend that you list an instance of each dedicated hardware station for the store, as required. For each hardware station, the host name should be the specific computer name where the hardware station will be deployed.
    -   **Port** – The port to use for the hardware station to communicate with the Modern POS client.
    -   **Hardware profile** – If the hardware profile isn't provided on the hardware station itself, the hardware profile that is assigned to the register will be used.
    -   **EFT POS number** – The EFT terminal ID to use when EFT authorizations are sent. This ID is provided by the credit card processor.
    -   **Package name** – The hardware station package to use when the hardware station is deployed.

4.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
5.  Select the **1090** distribution schedule to sync the new hardware profile to the store. Click **Run now** to sync changes to the POS.
6.  Select the **1040** distribution schedule to sync the new hardware station to the store. Click **Run now** to sync changes to the POS.
7.  Install the hardware station. For more information about how to install the hardware station, see [Retail hardware station configuration and installation](retail-hardware-station-configuration-installation.md).
8.  Install and activate Modern POS. For more information about how to install Modern POS, see [Retail Modern POS configuration and installation](retail-modern-pos-device-activation.md).
9.  Sign in to Modern POS, and select **Perform non-drawer operations**.
10. Start the **Manage hardware stations** operation.
11. Click **Manage**.
12. On the hardware station management page, set the option to turn on the hardware station.
13. Select the hardware station to use, and then click **Pair**.
14. After the hardware station is paired, click **Close**.
15. On the hardware station selection page, click the recently selected hardware station to make it active.

### All Modern POS clients that have a shared IIS hardware station

This configuration can be used for all Modern POS clients that share hardware stations with other devices. To set up this configuration, follow these steps.

1.  Create a hardware profile where the required peripherals are configured.
2.  Create a hardware station of the **Shared** type for the retail store where the POS register will be used.
3.  On the shared hardware station, set the following properties:
    -   **Host name** – The name of the host computer where the hardware station will run.
    -   **Description** – Text that will help identify the hardware station, such as **Returns** or **Front of store**.
    -   **Port** – The port to use for the hardware station to communicate with the Modern POS client.
    -   **Hardware profile** – For shared hardware stations, each hardware station should have a hardware profile. Hardware profiles can be shared among hardware stations, but they must be mapped to each hardware station. In addition, we recommend that you use shared shifts when multiple devices use the same shared hardware station. To set up a shared shift, click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**. For each shared hardware profile, select the cash drawer, and set the **Shared shift drawer** option to **Yes**.
    -   **EFT POS number** – The EFT terminal ID to use when EFT authorizations are sent. This ID is provided by the credit card processor.
    -   **Package name** – The hardware station package to use when the hardware station is deployed.

4.  Repeat steps 2 and 3 for each additional hardware station that is required in the store.
5.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
6.  Select the **1090** distribution schedule to sync the new hardware profile to the store. Click **Run now** to sync changes to the POS.
7.  Select the **1040** distribution schedule to sync the new hardware station to the store. Click **Run now** to sync changes to the POS.
8.  Install the hardware station on each host computer that you set up in steps 2 and 3. For more information about how to install the hardware station, see [Retail hardware station configuration and installation](retail-hardware-station-configuration-installation.md).
9.  Install and activate Modern POS. For more information about how to install Modern POS, see [Retail Modern POS configuration and installation](retail-modern-pos-device-activation.md).
10. Sign in to Modern POS, and select **Perform non-drawer operations**.
11. Start the **Manage hardware stations** operation.

12. Click **Manage**.
13. On the hardware station management page, set the option to turn on the hardware station.
14. Select the hardware station to use, and then click **Pair**.
15. Repeat step 14 for each hardware station that Modern POS will use.
16. After all the required hardware stations are paired, click **Close**.
17. On the hardware station selection page, click the recently selected hardware station to make it active. **Note:** If devices often use different hardware stations, we recommend that you configure Modern POS to prompt cashiers to select a hardware station when they begin the tender process. Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**. Select the register, and then set the **Select upon tender** option to **Yes**. Use the **1090** distribution schedule to sync changes to the channel database.

## Extensibility
For information about extensibility scenarios for the hardware station, see [Hardware Station extensibility](dev-itpro/hardware-station-extensibility.md).

## Security
According to current security standards, the following settings should be used in a production environment: **Note:** The hardware station installer will automatically make these registry edits as part of the installation through self-service.

-   Secure Sockets Layer (SSL) should be disabled.
-   Only Transport Layer Security (TLS) version 1.2 (or the current highest version) should be enabled and used. **Note:** By default, SSL and all version of TLS except TLS 1.2 are disabled. To edit or enable these values, follow these steps:
    1.  Press the Windows logo key+R to open a **Run** window.
    2.  In the **Open** field, type **Regedit**, and then click **OK**.
    3.  If a **User Account Control** message box appears, click **Yes**.
    4.  In the **Registry Editor** window, navigate to **HKEY\_LOCAL\_MACHINESystemCurrentControlSetSecurityProvidersSCHANNELProtocols**. The following keys have been automatically entered to allow for TLS 1.2 only:
        -   TLS 1.2Server:Enabled=1
        -   TLS 1.2Server:DisabledByDefault=0
        -   TLS 1.2Client:Enabled=1
        -   TLS 1.2Client:DisabledByDefault=0
        -   TLS 1.1Server:Enabled=0
        -   TLS 1.1Client:Enabled=0
        -   TLS 1.0Server:Enabled=0
        -   TLS 1.0Client:Enabled=0
        -   SSL 3.0Server:Enabled=0
        -   SSL 3.0Client:Enabled=0
        -   SSL 2.0Server:Enabled=0
        -   SSL 2.0Client:Enabled=0
-   No additional network ports should be open, unless they are required for known, specified reasons.
-   Cross-origin resource sharing must be disabled and must specify the allowed origins that are accepted.
-   Only trusted certificate authorities should be used to obtain certificates that will be used on computers that run the hardware station.

**Note:** It’s very important that you review security guidelines for IIS and the Payment Card Industry (PCI) requirements.

## Peripheral simulator
For information, see [Retail peripheral simulator](retail-peripheral-simulator.md).

## Microsofttested peripheral devices
### IPC (built-in) hardware station

The following peripherals were tested by using the IPC hardware station that is built into Modern POS for Windows.

#### Printer

| Manufacturer | Model    | Interface | Comments                |
|--------------|----------|-----------|-------------------------|
| Epson        | Tm-T88IV | OPOS      |                         |
| Epson        | TM-T88V  | OPOS      |                         |
| Star         | TSP650II | OPOS      |                         |
| Star         | TSP650II | Custom    | Connected via network   |
| Star         | mPOP     | OPOS      | Connected via Bluetooth |
| HP           | F7M67AA  | OPOS      | Powered USB             |

#### Bar code scanner

| Manufacturer  | Model         | Interface | Comments |
|---------------|---------------|-----------|----------|
| Motorola      | DS9208        | OPOS      |          |
| Honeywell     | 1900          | UWP       |          |
| Symbol        | LS2208        | OPOS      |          |
| HP Integrated | E1L07AA       | OPOS      |          |
| Datalogic     | Magellan 8400 | OPOS      |          |

#### PIN pad

| Manufacturer | Model  | Interface | Comments                                        |
|--------------|--------|-----------|-------------------------------------------------|
| VeriFone     | 1000SE | OPOS      | Requires customization of the payment connector |

#### Payment terminal

| Manufacturer | Model | Interface | Comments                                                                       |
|--------------|-------|-----------|--------------------------------------------------------------------------------|
| Equinox      | L5300 | Custom    | Requires customization of the payment connector                                |
| VeriFone     | MX925 | Custom    | Requires customization of the payment connector; connected via network and USB |
| VeriFone     | MX915 | Custom    | Requires customization of the payment connector; connected via network and USB |

#### Cash drawer

| Manufacturer | Model     | Interface | Comments                |
|--------------|-----------|-----------|-------------------------|
| Star         | mPOP      | OPOS      | Connected via Bluetooth |
| APG          | Atwood    | Custom    | Connected via network   |
| Star         | SMD2-1317 | OPOS      |                         |
| HP           | QT457AA   | OPOS      |                         |

#### Line display

| Manufacturer  | Model   | Interface | Comments |
|---------------|---------|-----------|----------|
| HP integrated | G6U79AA | OPOS      |          |
| Epson         | M58DC   | OPOS      |          |

#### Signature capture

| Manufacturer | Model  | Interface | Comments |
|--------------|--------|-----------|----------|
| Scriptel     | ST1550 | OPOS      |          |

#### Scale

| Manufacturer | Model         | Interface | Comments |
|--------------|---------------|-----------|----------|
| Datalogic    | Magellan 8400 | OPOS      |          |

#### MSR

| Manufacturer | Model       | Interface | Comments |
|--------------|-------------|-----------|----------|
| Magtek       | 21073075    | UWP       |          |
| Magtek       | 21073062    | OPOS      |          |
| HP           | IDRA-334133 | OPOS      |          |

### Dedicated IIS hardware station

The following peripherals were tested by using a dedicated (not shared) IIS hardware station together with Modern POS for Windows and Cloud POS.

#### Printer

| Manufacturer | Model    | Interface | Comments                  |
|--------------|----------|-----------|---------------------------|
| Epson        | Tm-T88IV | OPOS      |                           |
| Epson        | TM-T88V  | OPOS      |                           |
| Star         | TSP650II | OPOS      |                           |
| Star         | TSP650II | Custom    | Connected via network     |
| Star         | TSP100   | OPOS      | Requires TSP650II drivers |
| HP           | F7M67AA  | OPOS      | Powered USB               |

#### Bar code scanner

| Manufacturer  | Model   | Interface | Comments |
|---------------|---------|-----------|----------|
| Motorola      | DS9208  | OPOS      |          |
| Symbol        | LS2208  | OPOS      |          |
| HP Integrated | E1L07AA | OPOS      |          |

#### PIN pad

| Manufacturer | Model  | Interface | Comments                                        |
|--------------|--------|-----------|-------------------------------------------------|
| VeriFone     | 1000SE | OPOS      | Requires customization of the payment connector |

#### Payment terminal

| Manufacturer | Model | Interface | Comments                                                                       |
|--------------|-------|-----------|--------------------------------------------------------------------------------|
| Equinox      | L5300 | Custom    | Requires customization of the payment connector                                |
| VeriFone     | MX925 | Custom    | Requires customization of the payment connector; connected via network and USB |
| VeriFone     | MX915 | Custom    | Requires customization of the payment connector; connected via network and USB |

#### Cash drawer

| Manufacturer | Model     | Interface | Comments              |
|--------------|-----------|-----------|-----------------------|
| APG          | Atwood    | Custom    | Connected via network |
| Star         | SMD2-1317 | OPOS      |                       |
| HP           | QT457AA   | OPOS      |                       |

#### Line display

| Manufacturer  | Model   | Interface | Comments |
|---------------|---------|-----------|----------|
| HP integrated | G6U79AA | OPOS      |          |
| Epson         | M58DC   | OPOS      |          |

#### Signature capture

| Manufacturer | Model  | Interface | Comments |
|--------------|--------|-----------|----------|
| Scriptel     | ST1550 | OPOS      |          |

#### Scale

| Manufacturer | Model         | Interface | Comments |
|--------------|---------------|-----------|----------|
| Datalogic    | Magellan 8400 | OPOS      |          |

#### MSR

| Manufacturer | Model       | Interface | Comments |
|--------------|-------------|-----------|----------|
| Magtek       | 21073075    | UWP       |          |
| Magtek       | 21073062    | OPOS      |          |
| HP           | IDRA-334133 | OPOS      |          |

### Shared IIS hardware station

The following peripherals were tested by using a shared IIS hardware station together with Modern POS for Windows and Cloud POS. **Note:** Only a printer, payment terminal, and cash drawer are supported.

#### Printer

| Manufacturer | Model    | Interface | Comments                  |
|--------------|----------|-----------|---------------------------|
| Epson        | Tm-T88IV | OPOS      |                           |
| Epson        | TM-T88V  | OPOS      |                           |
| Star         | TSP650II | OPOS      |                           |
| Star         | TSP650II | Custom    | Connected via network     |
| Star         | TSP100   | OPOS      | Requires TSP650II drivers |
| HP           | F7M67AA  | OPOS      | Powered USB               |

#### Payment terminal

| Manufacturer | Model | Interface | Comments                                                                       |
|--------------|-------|-----------|--------------------------------------------------------------------------------|
| VeriFone     | MX925 | Custom    | Requires customization of the payment connector; connected via network and USB |
| VeriFone     | MX915 | Custom    | Requires customization of the payment connector; connected via network and USB |

#### Cash drawer

| Manufacturer | Model     | Interface | Comments              |
|--------------|-----------|-----------|-----------------------|
| APG          | Atwood    | Custom    | Connected via network |
| Star         | SMD2-1317 | OPOS      |                       |
| HP           | QT457AA   | OPOS      |                       |

## Troubleshooting
### Modern POS can detect the hardware station in its list for selection, but it can’t complete the pairing

**Solution:** Verify the following list of potential failure points:

-   The computer that is running Modern POS trusts the certificate that is used on the computer that runs the hardware station.
    -   To verify this setup, in a web browser, go to the following URL: https://&lt;Computer Name&gt;:&lt;Port Number&gt;/HardwareStation/ping.
    -   This URL uses a ping to verify that the computer can be accessed, and the browser indicates whether the certificate is trusted. (For example, in Internet Explorer, a lock icon appears in the address bar. When you click this icon, Internet Explorer verifies whether the certificate is currently trusted. You can install the certificate on the local computer by viewing the details of the certificate that is shown.)
-   On the computer that runs the hardware station, the port that will be used by the hardware station is opened in the firewall.
-   The hardware station has correctly installed merchant account information through the Install merchant information tool that runs at the end of the hardware station installer.

### Modern POS can’t detect the hardware station in its list for selection

**Solution:** Either of the following factors can cause this issue:

-   The hardware station hasn’t been set up correctly in headquarters. Use the steps earlier in this topic to verify that the hardware station profile and the hardware station are correctly entered.
-   The jobs haven’t been run to update the channel configuration. In this case, run the 1070 job for channel configuration.

### Modern POS doesn't reflect new cash drawer settings

**Solution:** Close the current batch. Changes to the cash drawer aren't updated to Modern POS until the current batch is closed.

### Modern POS is reporting an issue with a retail peripheral

**Solution:** Here are some typical causes of this issue:

-   Make sure that other device driver configuration utilities are closed. If these utilities are open, they might prevent Modern POS or the hardware station from claiming the device.
-   If the retail peripheral is shared with multiple POS devices, make sure that it belongs to one of the following categories:
    -   Cash drawer
    -   Receipt printer
    -   Payment terminal

    If the peripheral doesn't belong to one of these categories, the hardware station isn't designed to enable the peripheral to be shared among multiple POS devices.
-   Sometimes, device drivers can cause the common control objects (CCOs) to stop working correctly. If a device has recently been installed, but it isn't working properly or you notice other issues, you can often resolve the issue by reinstalling the CCOs. To download the CCOs, visit <http://monroecs.com/oposccos_current.htm>.
-   If you make frequent peripheral changes during testing or troubleshooting, you might have to reset IIS instead of waiting for the cache to refresh itself. To reset IIS, follow these steps:
    1.  From the **Start** menu, type **CMD**.
    2.  In the search results, right-click **Command prompt**, and then click **Run as administrator**.
    3.  In the **Command prompt** window, type **iisreset /Restart** and then press Enter.
    4.  After IIS has restarted, restart Modern POS.
-   While you're making frequent changes to peripheral devices, if you also frequently start and exit the POS client, the dllhost process from a previous POS session can interfere with the current session. In this case, a device might not be usable until you close the dynamic-link library (DLL) host that is managing the previous session. To close the DLL host, follow these steps:
    1.  From the **Start** menu, type **Task manager**.
    2.  In the search results, click **Task manager**.
    3.  In Task manager, on the **Details** tab, click the column header that is labeled **Name** to sort the table alphabetically by name.
    4.  Scroll down until you find dllhost.exe.
    5.  Select each DLL host, and then click **End task**.
    6.  After the DLL hosts have been closed, restart Modern POS.


See also
--------

[Retail peripheral simulator](retail-peripheral-simulator.md)



