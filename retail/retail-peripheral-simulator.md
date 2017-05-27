---
# required metadata

title: Peripheral simulator for Retail
description: This topic describes the peripheral simulator tool that is provided with Microsoft Dynamics 365 for Operations - Retail.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 266544
ms.assetid: 16f31e70-15fc-441e-9727-e6a31c3a48f5
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Peripheral simulator for Retail

[!include[banner](includes/banner.md)]


This topic describes the point of sale and peripheral simulator tool that is provided with Microsoft Dynamics 365 for Operations - Retail.

Overview
--------

The Peripheral Simulator for Retail is a utility provided by Microsoft as part of Microsoft Dynamics 365 for Retail and as a standalone utility. The utility has two primary components, a virtual peripheral simulator and a point-of sale(POS) simulator. 

The virtual peripheral simulator is primarily provided to support testing of scenarios that would normally require physical point of sale peripheral devices, whereas the POS simulator is used to test physical peripheral devices for compatibility with Microsoft Dynamics 365 for Retail without the need to deploy the point of sale client. 

## Install the Peripheral simulator for Retail
1.  Go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2.  Click **Download**, and then click **PeripheralSimulator**. **Note:** You must turn off pop-up blockers before you can download the peripheral simulator.
3.  After the download is completed, open the **Downloads** folder, and double-click **VirtualPeripherals.msi** to start the installer.
4.  Install the peripheral simulator by using the default settings.

In addition to the peripheral simulator, you must install the common control objects from Monroe Consulting Services. Otherwise, the peripheral simulator won't work correctly. To download the common control objects, go to <http://monroecs.com/oposccos_current.htm>.

Virtual peripheral simulator overview
--------
The virtual peripheral simulator is a tool included in the Peripheral simulator for Retail assists in the set up, test, and troubleshooting of peripheral devices that are used in retail environments. It can be used to streamline the testing of retail peripherals, and to isolate issues that are caused by incorrect setup or malfunctioning device drivers. The peripheral simulator includes a desktop program that features virtual versions of devices that Dynamics 365 for Retail supports. A section for each virtual device shows the interaction between the device and the retail point of sale (POS). You can also use it to provide input that is valid for various POS scenarios. The peripheral simulator supports interaction between the POS and the following virtual devices:

-   **Printer** – The virtual peripheral simulator can show receipts that are configured for a POS printer.
-   **Line display** – You can configure a virtual line display to show activity on a physical line display.
-   **Magnetic stripe reader (MSR)** – You can send simulated magnetic stripe events to the POS from the virtual peripheral simulator.
-   **Drawer** – You can simulate a physical cash drawer.
-   **Drawer 2** – By setting up a second cash drawer in the peripheral simulator, you can simulate scenarios that involve a single POS register that has two active shifts.
-   **Scanner** – The virtual bar code scanner that the virtual peripheral simulator supports can issue bar code scan events.
-   **Scale** – A virtual scale lets you simulate the interaction of weighed items with the POS.
-   **Personal identification number (PIN) pad** – You can simulate PIN pad operations. **Note:** You must implement support for a physical PIN pad through the payment connector.
-   **Signature capture** – The virtual peripheral simulator includes a virtual signature capture device that you can set up to prompt for signatures that are required for some tenders, such as customer account payments.
-   **Payment terminal**- A virtual payment terminal can be used in conjunction with a custom payment connector to test API calls from the point of sale to a virtual payment device. Use of the virtual payment terminal requires the implementation of a payment connector. For more information see < Implementing a payment connector and payment device (white paper)>

You can also use the virtual peripheral simulator to simulate keyboard wedge events that originate from a bar code scanner and MSR. The virtual peripheral simulator specifically supports Object Linking and Embedding for Retail POS (OPOS) devices.

## Key scenarios- Virtual peripheral simulator
### Troubleshooting

You can use the peripheral simulator to troubleshoot device setup. If you don't have the peripheral simulator or a second device of the same class, it can be difficult to determine where issues originate. However, when you have the peripheral simulator, you can set up virtual devices, and run the same code paths and business logic that are used for physical devices. From the perspective of the peripheral simulator, the main difference between virtual devices and physical devices is the service object, or device driver. For physical devices, the service object is provided by the device manufacturer. By contrast, for the peripheral simulator, the service objects are provided as part of the peripheral simulator. When the peripheral simulator is working correctly, if a device doesn't work correctly after the device name in the hardware profile is changed to the name of a real device, you can assume that there's an issue with the service object that the manufacturer provided.

### Training

You can use the peripheral simulator to add a realistic layer to cashier training when a physical hardware setup isn't available. When the peripheral simulator is included in training scenarios, the cashier can more effectively interact with the POS by providing input such as product bar code scans and gift card swipes, and by observing which receipts are printed for a specific transaction.

### Testing

You can use the peripheral simulator to test product bar codes, receipt formats, and so on, without having to deploy physical hardware in a virtual environment. Because physical hardware isn't required, and you don't have to deploy a POS client on a hardware station or a physical computer, you can more quickly test changes that are made in the back office.

## Set up the virtual peripheral simulator
### Set up a hardware profile

1.  To set up the peripheral simulator, go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2.  To create a new profile, click **New**.
3.  Enter values in the **Profile number** and **Description** fields.
4.  Use the following table to set up the virtual devices that must be tested. Here is an explanation of the columns in the table:
    -   **Device** – This column gives the name of the FastTab that you expand to set up the device.
    -   **Device type** – This column gives the value that you select in the field that is labeled with the name of the device.
    -   **Device name** – This column gives the exact value that you enter for the device name. **Important:** The device names that are given here are required, because the hardware station uses these specific names to address the devices. If you don't use these specific names, the device won't be usable.

    | Device            | Device type | Device name              |
    |-------------------|-------------|--------------------------|
    | Printer           | OPOS        | MockOPOSPrinter          |
    | Line display      | OPOS        | MockOPOSLineDisplay      |
    | MSR               | OPOS        | MockOPOSMSR              |
    | Drawer            | OPOS        | MockOPOSDrawer1          |
    | Drawer2           | OPOS        | MockOPOSDrawers          |
    | Scanner           | OPOS        | MockOPOSScanner          |
    | Scale             | OPOS        | MockOPOSScale            |
    | PIN Pad           | OPOS        | MockOPOSPinPad           |
    | Signature capture | OPOS        | MockOPOSSignatureCapture |

**Note:** No specific setup in the hardware profile is required to simulate keyboard wedge events from the bar code scanner and MSR.

### Assign the hardware profile to a register

1.  After the hardware profile is created, go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**.
2.  In the **POS registers** list, click the link in the **Register number** field for the register that should use the peripheral simulator.
3.  Click **Edit**.
4.  In the **Profiles** section, in the **Hardware profile** field, select the hardware profile that you created for virtual peripherals.
5.  Click **Save**.

### Synchronize changes to the channel database

1.  Go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
2.  Select the **1090** distribution schedule.
3.  Click **Run now** to synchronize changes to the POS.

After the data is synchronized, the new hardware profile and changes on the register are available in the channel database.

## Using the virtual peripheral simulator
To start the virtual peripheral simulator, click **Start** on your computer, type **Peripheral simulator for Retail**, and then select the app when it appears in the search results. After you start the peripheral simulator, click Use virtual peripherals. The supported devices will be listed as tabs on the left side of the window. To view a specific device, click the tab for that device.

### Line display capabilities

The line display is the first device that is listed in the peripheral simulator. When the virtual line display is configured, it shows line items as they are scanned in the POS transaction. In addition to line items, the display shows the total that is due when a tender is selected at the POS. It also shows the balance that is due if a tender is entered but a balance is still due for the transaction. When the POS isn't being used, a message can be shown to indicate that the till is closed. You must configure the message on the **Line display** FastTab in the hardware profile.

### Cash drawer capabilities

The cash drawer is the second device that is listed in the peripheral simulator. When the hardware profile is configured to use virtual cash drawers, the POS opens the cash drawer for the active shift in response to drawer operations such as tender declarations, and so that the cashier can make change or deposit cash during standard cash-and-carry transactions. The virtual cash drawers have the labels **Main drawer** and **Secondary drawer**. These labels represent Drawer and Drawer 2 in the hardware profile, respectively. When a drawer is closed, an image of a closed cash drawer is shown, and the button on the closed cash drawer is labeled **Open drawer**. If you click this button, the image is replaced with an image of an open cash drawer to indicate that the drawer is now open. The button on the open cash drawer is labeled **Close drawer**. Several operations at the POS can cause the cash drawer to open. Most operations can't proceed while the cash drawer is open. The exceptions are some end-of-day procedures. If the POS user receives an error message that states that an operation can't be performed while the cash drawer is open, the user must close the virtual or physical cash drawer to proceed. If a cash drawer is marked as **Shared** in the hardware profile, the system doesn't verify that the drawer is closed before an operation. The operation proceeds as usual, even if the cash drawer is open. This behavior supports scenarios where cash drawers are shared among sales associates, and where one associate uses a cash drawer while another associate performs unrelated tasks on his or her own POS device. Changes that are made to the cash drawer aren't evident until the current shift is closed and a new shift is opened.

### MSR capabilities

The peripheral simulator provides robust support for virtual MSR operations by working in either OPOS mode or keyboard wedge mode. OPOS mode requires that the MSR be configured in the hardware profile to work as an OPOS device. Keyboard wedge mode just sends keyboard wedge data events to Microsoft Windows. Besides differences in setup, OPOS and keyboard wedge modes differ in the following ways:

-   The POS client enables OPOS MSR devices for specific scenarios, such as scenarios that allow magnetic stripe data for loyalty or gift card entry.
-   In keyboard wedge mode, the peripheral simulator sends keyboard wedge data to the field that is active when the data is sent. This behavior resembles the behavior that occurs if the data is entered by using a keyboard. To use the MSR as a keyboard wedge, the user must switch to Retail Modern POS (MPOS) to make sure that data is received in the correct field. Therefore, you can configure a delay, so that the user has time to make sure that the data will be sent to the correct field.

#### Testing gift and payment card swipes

The virtual MSR that the peripheral simulator provides also lets you configure specific MSR data to test scenarios for gift and payment card swipes. To create a card, click the plus sign (**+**) button, and select the type of card. Then specify the card number or track data that should be sent to the POS, together with the expiration month and year for the card that you're defining. The value that you select in the **Type of card** field is just a label that can be mapped to a card. This label makes it easier to identify cards when they are swiped through the peripheral simulator. You can select cards that have been configured in the peripheral simulator by using the left arrow (**&lt;**) and right arrow (**&gt;**) buttons above the image of the card. You can edit and delete cards by using the **Edit** and **Delete** buttons next to the plus sign (**+**) button.

### PIN pad

You can configure the PIN pad simulator to simulate an OPOS PIN pad. When an electronic funds transfer (EFT) transaction is performed at the POS and requires PIN entry, the hardware station calls the PIN device to prompt for PIN entry. To work, the PIN pad in the peripheral simulator requires EFT payment connector support.

### Printer

The virtual peripheral printer just shows receipts as they are printed from the POS. If a print operation produces multiple receipts, you can scroll through the receipts.

#### Configure receipt printing

1.  Go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2.  Select the hardware profile that you created for virtual peripherals.
3.  On the **Printer** FastTab, click **Edit**.
4.  In the **Receipt profile ID** field, select a receipt profile.
5.  Click **Save**.

### Scale

When a scale product is added to the POS transaction, and a scale is configured, the POS retrieves the weight from the scale. For both the virtual and physical scale, the product or weight should be specified before the product is added to the transaction. Before you add the scale product to the transaction, go to the scale in the peripheral simulator, and use the plus sign (**+**) and minus sign (**–**) buttons to adjust the weight that the scale should report. You can also enter the desired weight directly in the **Current value** field. You can adjust the units of weight for the scale by using the plus sign (**+**), **Edit**, and **Delete** buttons. In this way, units can be specified based on the products that are weighed or the locale where the scale is used.

#### Configure a scale product

1.  Go to **Retail and** **commerce** &gt; **Products and categories** &gt; **Released products by category**.
2.  Open the product record.
3.  Select the product to weigh.
4.  On the **Retail** FastTab, set the **Scale product** option from **No** to **Yes**.

#### Synchronize changes to the channel database

1.  Go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
2.  Select the **1040** distribution schedule.
3.  Click **Run now** to synchronize changes to the POS.

After the data is synchronized, when a scale product is added to the POS transaction, the POS checks the scale for the weight.

### Signature capture

The virtual signature capture device prompts the user to provide a signature on the virtual signature capture pad when the tender that is used requires a signature. The user can accept the signature to show it at the POS. The cashier can then accept the signature. The signature is then saved together with the tender and is synchronized to the back office together with other transaction data.

#### Set up a tender to require a signature

1.  Go to **Retail and commerce** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
2.  Select the retail store.
3.  Click **Edit**.
4.  Click **Set up**, and then, in the **Set up** section, click **Payment methods**.
5.  Click **Edit**.
6.  Select the payment method that requires a signature.
7.  In the **General** section, under **Signature Capture**, set the **Use signature capture device** option to **Yes**.
8.  In the **Signature capture minimum amount** field, enter the minimum amount that should trigger signature capture.

#### Synchronize changes to the channel database

1.  Go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
2.  Select the **1070** distribution schedule.
3.  Click **Run now** to synchronize changes to the POS.

After the data is synchronized, when a tender is used that requires a signature, and the amount meets the signature threshold, the POS prompts for a signature on the virtual signature capture device.

## Additional configuration
You can edit the peripheral simulator's configuration file to more appropriately address the scenarios that you're testing. You can find the configuration file at C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\VirtualPeripherals\\Microsoft.Dynamics.Commerce.VirtualPeripherals.Client.exe.config. The configuration file defines the units that are available for testing on the scale, the card types that are available for testing, and bar code types. For example, by modifying the text values in the configuration file, you can add a new card type or unit of measure that can be selected at run time. The new values will appear after the app is restarted.

## Troubleshooting
Activities for the peripheral simulator are logged within the peripheral simulator. You can find the log at C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\VirtualPeripherals\\Microsoft.Dynamics.Commerce.VirtualPeripherals.Client.exe.config. The peripheral simulator also reports issues to the Windows event log, which you can access at **Application and Services Logs** &gt; **Microsoft** &gt; **DynamicsAX**. If changes that you made to the hardware profile or other areas aren't evident when you use MPOS or the peripheral simulator, check the distribution scheduler jobs that you used to synchronize the data to the channel database. If the changes were synchronized but still aren't evident at the POS, restart the POS client. Changes to configured cash drawers aren't effective until a new shift is created. Therefore, if you make changes to cash drawers, make sure that you always close the existing shift to test the new cash drawer setup. Sometimes, if a manufacturer's driver is installed after the common control objects from Monroe Consulting Services, the driver can cause the common control objects to stop working correctly. In this case, you should reinstall the common control objects.

POS simulator overview
--------

The POS simulator provides the ability for device manufacturers, ISVs and retailers to test peripheral devices without the need to deploy the point of sale. By using the same retail peripheral business logic as the MPOS and standalone hardware station, the POS simulator can determine device driver compatibility with the point of sale as a standalone utility. This enables device selection to occur independent of the point of sale setup and deployment.

 The POS simulator is also provided as a standalone utility, independent of Microsoft Dynamics 365 for Retail. As a standalone utility, the simulator is primarily used for peripheral device compatibility testing. Only devices tested with the POS simulator are acceptable for new deployments of the point of sale. Testing is intended to be driven by the device manufacturers themselves. Portions of the POS simulator overview are intended to explain how the POS simulator is used for compatibility testing. Manufacturers interested in testing their devices for compatibility with the point of sale or standalone hardware station should send an email to drpc@microsoft.com to request information about the program. 
 
 ## Using the POS simulator
 To start the POS simulator, click Start on your computer, type Peripheral simulator for Retail, and then select the app when it appears in the search results. After you start the peripheral simulator, click Use virtual peripherals. The supported devices will be listed as tabs on the left side of the window. To view a specific device, click the tab for that device.
 
Devices supported by the POS simulator are as follows:
**Line display
Cash drawer
MSR
PIN pad
Printer
Scale
Signature capture pad
Bar code scanner
Payment terminal**- Requires presence of a payment connector. For more information see < Implementing a payment connector and payment device (white paper)>

Below the list of supported devices, there is a **Settings** tab. The settings tab can be used to specify how the POS simulator should communicate with the devices being tested. If **Runtime** is selected, the POS simulator will communicate with the device in a method similar to how the MPOS with built-in hardware station would communicate. Using **Win32**, however, makes the POS simulator communicate with the device directly, similar to the way a standalone hardware station would communicate.  Also on the settings page, details can be provided around who is performing the tests. Those details are important for manufacturers performing compatibility testing, which is explained in a section later in this page.

## Configuring the POS simulator 
For each supported device class, the POS simulator supports setting up multiple devices. For example, several printers can be configured in the POS simulator and within the printer tab, the user can cycle through configured devices testing as needed. 

The setup parameters for different devices depend on the type selected. To set up a new device, select the class of device to be tested and then click the ‘+’ symbol. This will display the device parameters slide out menu. To later edit a device that has already been created, use the < and > selectors to find the appropriate device, then click Edit

**OPOS devices**
When setting up devices as **OPOS**, the following values are available:

**Device driver name (Required)**- This list will be populated with OPOS service objects installed on the local machine where devices are being tested. Device names can also be manually entered here. 

Remember: OPOS common control objects must be installed to test OPOS devices using the POS simulator. This is in addition to the service objects provided by the manufacturer.

**Device model (Required)**- Free text that allows the device model to be specified. 

**Connection type**- Specify how the device is connected.
**Firmware version**- The firmware version for the device currently being configured. 
**Driver version**- The driver version for the device currently being configured. 
**Driver download link**- The link where the driver for the device can be downloaded. 

Note: All fields are required when configuring devices for testing to confirm compatibility with the point of sale.

When the device is configured to the level required for either casual testing or compatibility testing, click **Save device**.

**Network devices**
The POS simulator can be used to test network devices. The following network devices are supported out of the box:
**Cash drawer**: APG Atwood
**Receipt printer**: Star TSP650II
**Payment terminal**: May also be configured as network devices, but any payment terminal testing requires a custom payment connector. No payment terminals are supported out of the box. 

Upon selecting **Network** for device type, the following parameters are available:
**Device driver name** (Required): Selects the device driver to be selected.  
**IP address** (Required): IP address of the device being tested.
**Port** (Required): Port number be specified when communicating with the device.
**Device model** (Required): Used to identify the device model number. 
**Firmware version**: Version of firmward installed on the device being tested.
**Driver version**: Version of device driver that is being tested. 

Note: In the case of device driver name, model and version, these fields are useful for identification of the version of device specific implementation that is being tested. Devices tend to have their own communication protocol over IP, so custom implementations should be labeled with specific attributes. 

When the device is configured to the level required for either casual testing or compatibility testing, click **Save device**. 

**Windows devices**
Windows printers can also be tested using the POS simulator. Setup parameters are the same as for OPOS devices.

**Device driver name** (Required)- This list will be populated with Windows printers installed on the local machine where devices are being tested. Device names can also be manually entered here. 
**Device model** (Required)- Free text that allows the device model to be specified. 
**Connection type**- Specify how the device is connected.Firmware version- The firmware version for the device currently being configured. 
**Driver version**- The driver version for the device currently being configured. 
**Driver download link**- The link where the driver for the device can be downloaded. 

Note: All fields are required when configuring devices for testing to confirm compatibility with the point of sale. 

When the device is configured to the level required for either casual testing or compatibility testing, click **Save device**.

**Testing devices**
Each device class has specific testing capabilities unique to that class of device. 

In addition to device specific tests,  each device has a **Self-test function**. When testing a device for compatibility, set up the device and then click the **Green arrow** to begin the self-test. Each device has a different set of tests that are performed to determine the devices compatibility with the point of sale (in **Runtime** mode) and standalone hardware station(in **Win32** mode). Some devices require user interaction for the test to be completed. For example, the self-test for bar code scanner will instruct the user to scan a bar code to complete the self-test.

Results from each self-test and manual operation are displayed in the **Log** section of the device test page. The **Log** can be cleared or the results listed in the log can be exported and saved to file. Details on log export as used for official compatibility tested are provided later in this page. 

To abort the self-test, such as in cases where the device becomes non-responsive, click the **Red square**. The red square can only be used when a self-test is in progress. 

**Line display**
**Settings tab**:
The settings tab for the line display includes the following free text fields:
**Display text**: The description of the product.
**Quantity**: The quantity of the product.
**Price**: The price of the product.
To view the values entered in the free text field, use the Lock and claim button to claim the device. Next click Display text and observe the text that was sent to the device. Click Clear text to clear the text from the line display and then click Release to release the line display, making it usable for other processes. 

**Advanced tab**:
**Binary conversion**: Some line displays require that text is converted into binary format. See the device’s documentation to determine if this is necessary. 

Character set: Identifies the code page for the characters being sent to the device. For specific code page identifiers, see: https://msdn.microsoft.com/en-us/library/windows/desktop/dd317756(v=vs.85).aspx

**Cash drawer**

**Open cash drawer**: Opens the cash drawer.
Check drawer status:Checks the drawer to determine if it is open or closed. 
Drawer status: Displays the status of the drawer. 

**MSR**
**Open and claim MSR**: Used to prepare the POS simulator to receive data from the MSR.
Release and close MSR: Closes the MSR device when testing is completed.
Card info: Displays data from the card that was scanned on the MSR device.

Note: Actual credit cards should never be used for device testing. Even testing with expired credit cards is
discourage. 

PIN pad
Appears on both tabs:
Lock: Locks the PIN pad device for use with the POS simulator.
Get entry: Enables the POS simulator to receive PIN data.
Cancel operation: Cancels the request sent to the PIN pad.
Release: Releases the PIN pad device. 
Settings tab:
Amount: The amount to send to the PIN pad device for customer acceptance.
Account number: Specify account number if required. 
Encrypted PIN: Displays the encrypted PIN received from the device.
Additional security data: Used to specify cryptography in use for encrypted PIN. 
Advanced tab: 
Timeout: Specify the timeout in seconds when waiting for a response from the device.
Exclusive: Used to require that the PIN pad device is claimed before being enabled. 
Override: Overrides previous commands sent to device when device is not responding.

Scale
Timeout: Specifies the timeout interval. Product should be put on the scale before reading the weight. If the scale does not respond within the specified timeout, the request will cancel. 
Weight: Displays the weight value read from the scale.
Read: Requests the current weight from the scale.

Signature capture
Settings tab:
Form name: Some signature captures require a form name when sending the signature request. 
Signature (in HEX): The hex value for the signature data received from the device.
Rendered signature: The image of the signature received from the device. 

Advanced tab: 
Timeout: Specifies the timeout interval. If the signature capture device does not respond within the specified timeout, the request will cancel. 
Exclusive: Used to require that the PIN pad device is claimed before being enabled. 
Override: Overrides previous commands sent to device when device is not responding.
Lock: Locks the device and claims for use by the POS simulator.
Get entry: Requests the signature from the device.
Cancel operation: Cancels the signature request.
Release: Releases the device for use by other processes. 

Bar code scanner
Open and claim scanner: Opens and claims the scanner. The POS simulator can receive scan events after this is completed successfully. 
Release and close the scanner: Makes the scanner available for other processes.
Scanned information: Displays the data received from the bar code scanner. 






See also
--------

[Retail peripherals overview](retail-peripherals-overview.md)



