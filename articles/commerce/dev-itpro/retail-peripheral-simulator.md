---
title: Peripheral simulator for Commerce
description: This article describes the peripheral simulator tool that is provided with Dynamics 365 Commerce.
author: BrianShook
ms.date: 08/22/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: global
ms.author: brshoo
ms.search.validFrom: 2016-06-30
ms.custom: 266544
ms.assetid: 16f31e70-15fc-441e-9727-e6a31c3a48f5
ms.search.industry: Retail
ms.search.form: RetailHardwareProfile, RetailTerminalTable, EcoResProductDetailsExtended, RetailCDXSchedule, RetailStoreTable

---

# Peripheral simulator for Commerce

[!include [banner](../includes/banner.md)]

The peripheral simulator is a utility that Microsoft provides as part of Microsoft Dynamics 365 Commerce and as a standalone utility. The utility has two primary components, a *virtual peripheral simulator* and a *point of sale (POS) simulator*.

- **Virtual peripheral simulator** - The virtual peripheral simulator primarily supports the testing of scenarios that usually require physical POS peripheral devices, and is also useful for diagnosing peripheral problems. If a peripheral isn't functioning correctly when physically connected but does function correctly when configured as a virtual peripheral, the issue is probably caused by the physical device or the manufacturer-provided device driver. In these cases, Microsoft recommends that you contact the manufacturer to resolve the issue. 
- **POS simulator** - The POS simulator tests the compatibility of physical peripheral devices without having to deploy the POS client.

## Install the peripheral simulator

1. Go to **Retail and Commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2. Click **Download**, and then click **PeripheralSimulator**.

    > [!NOTE]
    > You must turn off pop-up blockers before you can download the peripheral simulator.

3. After the download is completed, open the **Downloads** folder, and double-click **VirtualPeripherals.msi** to start the installer.
4. Install the peripheral simulator by using the default settings.

Besides the peripheral simulator, you must install the common control objects from Monroe Consulting Services. Otherwise, the peripheral simulator won't work correctly. To download the common control objects, go to <http://monroecs.com/oposccos_current.htm>.

## Virtual peripheral simulator

The virtual peripheral simulator helps you set up, test, and troubleshoot peripheral devices. It can be used to streamline the testing of peripherals, and to isolate issues that are caused by incorrect setup or malfunctioning device drivers. The peripheral simulator includes a desktop program that features virtual versions of devices that Commerce supports. A section for each virtual device shows the interaction between the device and the POS. You can also use it to provide input that is valid for various POS scenarios. The peripheral simulator supports interaction between the POS and the following virtual devices:

- **Printer** – The virtual peripheral simulator can show receipts that are configured for a POS printer.
- **Line display** – You can configure a virtual line display to show activity on a physical line display.
- **Magnetic stripe reader (MSR)** – You can send simulated magnetic stripe events to the POS from the virtual peripheral simulator.
- **Drawer** – You can simulate a physical cash drawer.
- **Drawer 2** – By setting up a second cash drawer in the peripheral simulator, you can simulate scenarios that involve a single POS register that has two active shifts.
- **Scanner** – The virtual bar code scanner that the virtual peripheral simulator supports can issue bar code scan events.
- **Scale** – A virtual scale lets you simulate the interaction of weighed items with the POS.
- **Personal identification number (PIN) pad** – You can simulate PIN pad operations.

    > [!NOTE]
    > You must implement support for a physical PIN pad through the payment connector.

- **Signature capture** – The virtual peripheral simulator includes a virtual signature capture device that you can set up to prompt for signatures that are required for some tenders, such as customer account payments.
- **Payment terminal** – A virtual payment terminal can be used in conjunction with a custom payment connector to test application programming interface (API) calls from the POS to a virtual payment device. To use the virtual payment terminal, you must implement a payment connector. For more information, see <Implementing a payment connector and payment device (white paper)>.

You can also use the virtual peripheral simulator to simulate keyboard wedge events that originate from a bar code scanner and MSR. The virtual peripheral simulator specifically supports Object Linking and Embedding for Retail POS (OPOS) devices.

### Key scenarios – Virtual peripheral simulator

#### Troubleshooting

You can use the peripheral simulator to troubleshoot device setup. If you don't have the peripheral simulator or a second device of the same class, it can be difficult to determine where issues originate. However, when you have the peripheral simulator, you can set up virtual devices, and run the same code paths and business logic that are used for physical devices. From the perspective of the peripheral simulator, the main difference between virtual devices and physical devices is the service object, or device driver. For physical devices, the service object is provided by the device manufacturer. By contrast, for virtual devices, the service objects are provided as part of the peripheral simulator. When the peripheral simulator is working correctly, if a device doesn't work correctly after the device name in the hardware profile is changed to the name of a real device, you can assume that there's an issue with the service object that the manufacturer provided.

#### Training

You can use the peripheral simulator to add a realistic layer to cashier training when a physical hardware setup isn't available. When the peripheral simulator is included in training scenarios, the cashier can more effectively interact with the POS by providing input such as product bar code scans and gift card swipes, and by observing which receipts are printed for a specific transaction.

#### Testing

You can use the peripheral simulator to test product bar codes, receipt formats, and so on, without having to deploy physical hardware in a virtual environment. Because physical hardware isn't required, and you don't have to deploy a POS client on a hardware station or a physical computer, you can more quickly test changes that are made in the back office.

### Set up the virtual peripheral simulator

#### Set up a hardware profile

1. To set up the peripheral simulator, go to **Retail and Commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2. Click **New** to create a profile.
3. Enter values in the **Profile number** and **Description** fields.
4. Use the following table to set up the virtual devices that must be tested. Here is an explanation of the columns in the table:

   - **Device** – This column gives the name of the FastTab where you set up the device.
   - **Device type** – This column gives the value that you select in the field that is labeled with the name of the device.
   - **Device name** – This column gives the exact value that you enter for the device name.

     > [!IMPORTANT]
     > The device names that are given here are required, because the hardware station uses these specific names to address the devices. If you don't use the following specific names, the device won't be usable.

     No specific setup in the hardware profile is required in order to simulate keyboard wedge events from the bar code scanner and MSR.

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

#### Assign the hardware profile to a register

1. After the hardware profile is created, go to **Retail and Commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**.
2. In the **POS registers** list, click the link in the **Register number** field for the register that should use the peripheral simulator.
3. Click **Edit**.
4. In the **Profiles** section, in the **Hardware profile** field, select the hardware profile that you created for virtual peripherals.
5. Click **Save**.

#### Synchronize changes to the channel database

1. Go to **Retail and Commerce** &gt; **Retail and Commerce IT** &gt; **Distribution schedule**.
2. Select the **1090** distribution schedule.
3. Click **Run now** to synchronize changes to the POS.

After the data is synchronized, the new hardware profile and changes on the register are available in the channel database.

## Using the virtual peripheral simulator

To start the virtual peripheral simulator, click **Start** on your computer, type **Peripheral simulator**, and then select the app when it appears in the search results. After you start the peripheral simulator, click **Use virtual peripherals**. The supported devices will be listed as tabs on the left side of the window. To view a specific device, click the tab for that device.

### Line display capabilities

When the virtual line display is configured, it shows line items as they are scanned in the POS transaction. In addition to line items, the display shows the total that is due when a tender is selected at the POS. It also shows the balance that is due if a tender is entered but a balance is still due for the transaction. When the POS isn't being used, a message can be shown to indicate that the till is closed. You must configure the message on the **Line display** FastTab in the hardware profile.

### Cash drawer capabilities

When the hardware profile is configured to use virtual cash drawers, the POS opens the cash drawer for the active shift in response to drawer operations such as tender declarations. The POS also opens the cash drawer so that the cashier can make change or deposit cash during standard cash-and-carry transactions. The virtual cash drawers have the labels **Main drawer** and **Secondary drawer**. These labels represent Drawer and Drawer 2 in the hardware profile, respectively. When a drawer is closed, an image of a closed cash drawer is shown, and the button on the closed cash drawer is labeled **Open drawer**. If you click this button, the image is replaced with an image of an open cash drawer to indicate that the drawer is now open. The button on the open cash drawer is labeled **Close drawer**.

Several operations at the POS can cause the cash drawer to open. Most operations can't proceed while the cash drawer is open. The exceptions are some end-of-day procedures. If the POS user receives an error message that states that an operation can't be performed while the cash drawer is open, the user must close the virtual or physical cash drawer to proceed. If a cash drawer is marked as **Shared** in the hardware profile, the system doesn't verify that the drawer is closed before an operation. The operation proceeds as usual, even if the cash drawer is open. This behavior supports scenarios where cash drawers are shared among sales associates, and where one associate uses a cash drawer while another associate performs unrelated tasks on their own POS device. Changes that are made to the cash drawer aren't evident until the current shift is closed and a new shift is opened.

### MSR capabilities

The peripheral simulator provides robust support for virtual MSR operations by working in either OPOS mode or keyboard wedge mode. OPOS mode requires that the MSR be configured in the hardware profile to work as an OPOS device. Keyboard wedge mode just sends keyboard wedge data events to Microsoft Windows. Besides differences in setup, OPOS and keyboard wedge modes differ in the following ways:

- The POS client enables OPOS MSR devices for specific scenarios, such as scenarios that allow for magnetic stripe data for loyalty or gift card entry.
- In keyboard wedge mode, the peripheral simulator sends keyboard wedge data to the field that is active when the data is sent. This behavior resembles the behavior that occurs if the data is entered by using a keyboard. To use the MSR as a keyboard wedge, the user must switch to the Store Commerce app to make sure that data is received in the correct field. Therefore, you can configure a delay, so that the user has time to make sure that the data will be sent to the correct field.

#### Testing gift and payment card swipes

The virtual MSR that the peripheral simulator provides also lets you configure specific MSR data to test scenarios for gift and payment card swipes. To create a card, click the plus sign (**+**) button, and select the type of card. Then specify the card number or track data that should be sent to the POS, together with the expiration month and year for the card that you're defining. The value that you select in the **Type of card** field is just a label that can be mapped to a card. This label makes it easier to identify cards when they are swiped through the peripheral simulator. You can select cards that have been configured in the peripheral simulator by using the left arrow (**&lt;**) and right arrow (**&gt;**) buttons above the image of the card. You can edit and delete cards by using the **Edit** and **Delete** buttons next to the plus sign (**+**) button.

### PIN pad

You can configure the PIN pad simulator to simulate an OPOS PIN pad. When an electronic funds transfer (EFT) transaction is performed at the POS and requires that a PIN be entered, the hardware station calls the PIN device to prompt for PIN entry. To work, the PIN pad in the peripheral simulator must support an EFT payment connector.

### Printer

The virtual peripheral printer just shows receipts as they are printed from the POS. If a print operation produces multiple receipts, you can scroll through the receipts.

#### Configure receipt printing

1. Go to **Retail and Commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2. Select the hardware profile that you created for virtual peripherals.
3. On the **Printer** FastTab, click **Edit**.
4. In the **Receipt profile ID** field, select a receipt profile.
5. Click **Save**.

#### Scale

When a scale product is added to the POS transaction, and a scale is configured, the POS retrieves the weight from the scale. For both the virtual and physical scale, the product or weight should be specified before the product is added to the transaction. Before you add the scale product to the transaction, go to the scale in the peripheral simulator, and use the plus sign (**+**) and minus sign (**–**) buttons to adjust the weight that the scale should report. You can also enter the desired weight directly in the **Current value** field. You can adjust the units of weight for the scale by using the plus sign (**+**), **Edit**, and **Delete** buttons. In this way, units can be specified based on the products that are weighed or the locale where the scale is used.

##### Configure a scale product

1. Go to **Retail and Commerce** &gt; **Products and categories** &gt; **Released products by category**.
2. Open the product record.
3. Select the product to weigh.
4. On the **Retail and Commerce** FastTab, set the **Scale product** option from **No** to **Yes**.

##### Synchronize changes to the channel database

1. Go to **Retail and Commerce** &gt; **Retail and Commerce IT** &gt; **Distribution schedule**.
2. Select the **1040** distribution schedule.
3. Click **Run now** to synchronize changes to the POS.

After the data is synchronized, when a scale product is added to the POS transaction, the POS checks the scale for the weight.

#### Signature capture

The virtual signature capture device prompts the user to provide a signature on the virtual signature capture pad when the tender that is used requires a signature. The user can accept the signature to show it at the POS. The cashier can then accept the signature. The signature is then saved together with the tender and is synchronized to the back office together with other transaction data.

##### Set up a tender to require a signature

1. Go to **Retail and Commerce** &gt; **Channels** &gt; **Stores** &gt; **All stores**.
2. Select the store.
3. Click **Edit**.
4. Click **Set up**, and then, in the **Set up** section, click **Payment methods**.
5. Click **Edit**.
6. Select the payment method that requires a signature.
7. In the **General** section, under **Signature Capture**, set the **Use signature capture device** option to **Yes**.
8. In the **Signature capture minimum amount** field, enter the minimum amount that should trigger signature capture.

##### Synchronize changes to the channel database

1. Go to **Retail and Commerce** &gt; **Retail and Commerce IT** &gt; **Distribution schedule**.
2. Select the **1070** distribution schedule.
3. Click **Run now** to synchronize changes to the POS.

After the data is synchronized, when a tender is used that requires a signature, and the amount meets the signature threshold, the POS prompts for a signature on the virtual signature capture device.

#### Additional configuration

You can edit the peripheral simulator's configuration file to more appropriately address the scenarios that you're testing. You can find the configuration file at C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\VirtualPeripherals\\Microsoft.Dynamics.Commerce.VirtualPeripherals.Client.exe.config. The configuration file defines the units that are available for testing on the scale, the card types that are available for testing, and bar code types. For example, by modifying the text values in the configuration file, you can add a new card type or a new unit of measure that can be selected at runtime. The new values will appear after the app is restarted.

#### Troubleshooting

Activities for the peripheral simulator are logged in the peripheral simulator. You can find the log at C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\VirtualPeripherals\\Microsoft.Dynamics.Commerce.VirtualPeripherals.Client.exe.config. The peripheral simulator also reports issues to the Windows event log, which you can access at **Application and Services Logs** &gt; **Microsoft** &gt; **DynamicsAX**.

If changes that you made to the hardware profile or other areas aren't evident when you use the Store Commerce app or the peripheral simulator, check the distribution scheduler jobs that you used to synchronize the data to the channel database. If the changes were synchronized but still aren't evident at the POS, restart the POS client.

Changes to configured cash drawers aren't effective until a new shift is created. Therefore, if you make changes to cash drawers, make sure that you always close the existing shift to test the new cash drawer setup.

Sometimes, if a manufacturer's driver is installed after the common control objects from Monroe Consulting Services, the driver can cause the common control objects to stop working correctly. In this case, you should reinstall the common control objects.

At install time, it's possible that certain assemblies related to the virtual peripheral simulator were registered incorrectly. This issue is often associated with an 'OPOS_E_CLOSED' error when attempting to use a virtual device. This can be corrected by running the Windows Assembly Registration tool. To register the assembly (called Microsoft.Dynamics.Commerce.VirtualPeripherals.ServiceObjects.dll), open a command prompt as administrator and run 'regasm /codebase "C:\Program Files (x86)\Microsoft Dynamics 365\70\Peripheral simulator for Retail\Microsoft.Dynamics.Commerce.VirtualPeripherals.ServiceObjects.dll"'.

## POS simulator

The POS simulator lets device manufacturers, independent software vendors (ISVs), and retailers test peripheral devices without having to deploy the POS. By using the same business logic for peripherals as the Store Commerce app and the standalone hardware station, the POS simulator can determine device driver compatibility with the POS as a standalone utility. Therefore, device selection can occur independently of POS setup and deployment.

The POS simulator is also provided as a standalone utility that is independent of Commerce. As a standalone utility, the POS simulator is primarily used to test peripheral device compatibility. Only devices that are tested by using the POS simulator are acceptable for new deployments of the POS. Testing should be driven by the device manufacturers themselves. Parts of the POS simulator overview are intended to explain how the POS simulator is used for compatibility testing. Manufacturers that are interested in testing their devices for compatibility with the POS or standalone hardware station should send an email to drpc@microsoft.com to request information about the program.

### Using the POS simulator

1. Click **Start** on your computer, type **Peripheral simulator**, and then select the app when it appears in the search results.
2. Click **Use virtual peripherals**. The supported devices will be listed as tabs on the left side of the window. To view a specific device, click the tab for that device.

The POS simulator supports the following devices:

- Line display
- Cash drawer
- MSR
- PIN pad
- Printer
- Scale
- Signature capture pad
- Bar code scanner
- Payment terminal

    > [!NOTE]
    > A payment terminal requires that a payment connector be present. For more information, see [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md).

Below the list of supported devices, there is a **Settings** tab. You can use the **Settings** tab to specify how the POS simulator should communicate with the devices that are being tested. If **Runtime** is selected, the method that the POS simulator uses to communicate with the device resembles the method that the Store Commerce app with a built-in hardware station communicates. If **Win32** is selected, the POS simulator communicates directly with the device. This communication method resembles the method that a standalone hardware station communicates.

On the **Settings** tab, you can also provide details about the user who is performing the tests. These details are important for manufacturers that perform compatibility testing.

### Configuring the POS simulator

For each supported device class, the POS simulator lets you set up multiple devices. For example, several printers can be configured in the POS simulator. Then, on the **Printer** tab, the user can cycle through the configured devices and test them as required.

The setup parameters that are available for a device depend on the type of device. To set up a new device, select the class of device to test, and then click the plus sign (**+**) button. A menu of the available device parameters appears.

To edit a device that has already been created, use the left arrow (**&lt;**) and right arrow (**&gt;**) buttons to find the appropriate device, and then click **Edit**.

#### Configure an OPOS device

1. Select **OPOS** as the device type.
2. Select the name of the device driver. This value is required. This list includes all the OPOS service objects that are installed on the local machine where devices are being tested. You can also manually enter the device driver name.

    > [!IMPORTANT]
    > Before you can test OPOS devices by using the POS simulator, OPOS common control objects must be installed. These objects are separate are separate from the service objects that the manufacturer provides.

3. Enter data in the rest of the required fields.

    > [!NOTE]
    > When you configure devices for testing, all fields are required, so that the POS simulator can confirm compatibility with the POS.

4. When the device is configured to the level that is required for either casual testing or compatibility testing, click **Save device**.

#### Configure a network device

The POS simulator can be used to test network devices. The following network devices are supported out of the box:

- **Cash drawer:** APG Atwood
- **Receipt printer:** Star TSP650II
- **Payment terminal:** Although a payment terminal can be configured as network devices, any testing of a payment terminal requires a custom payment connector.

    > [!NOTE]
    > No payment terminals are supported out of the box.

1. Select **Network** as the device type.
2. Enter data for the rest of the fields.

    > [!NOTE]
    > The fields for the device driver name, model, and version can help identify the version of the device-specific implementation that is being tested. Because devices tend to have their own communication protocol over IP, custom implementations should be labeled with specific attributes.

3. When the device is configured to the level that is required for either casual testing or compatibility testing, click **Save device**.

#### Windows devices

The POS simulator can also be used to test Windows printers. The setup parameters are the same as the parameters for OPOS devices.

1. Select **Printer** as the device type.
2. Enter data in the rest of the required fields.

    > [!NOTE]
    > When you configure devices for testing, all fields are required, so that the POS simulator can confirm compatibility with the POS.

3. When the device is configured to the level that is required for either casual testing or compatibility testing, click **Save device**.

### Testing devices

Each device class has unique testing capabilities. In addition to device-specific tests, each device has a **Self-test** function.

When you're testing a device for compatibility, set up the device, and then click the green arrow to begin the self-test. For each device, a different set of tests is performed to determine the device's compatibility with the POS (in **Runtime** mode) or the standalone hardware station (in **Win32** mode). For some devices, the test requires user interaction. For example, the self-test for a bar code scanner requires that a bar code be scanned. Therefore, the self-test will instruct the user to scan a bar code.

Results from each self-test and each manual operation are shown in the **Log** section of the device test page. You can clear the **Log** section, or you can export the results and save them to a file. For information about how the exported log results can be used for official compatibility testing, see the "Instructions for device manufacturers" section later in this article.

To stop a self-test, click the red square. For example, you might have to stop a self-test if the device becomes non-responsive. The red square can be used only when a self-test is in progress.

### Device-specific settings to be aware of

This section lists settings that you might require some help to complete.

#### Line display &gt; Settings tab

To view the values that are entered in a free text field, click **Lock and claim** to claim the device.

1. Click **Display text**, and view the text that was sent to the device.
2. Click **Clear text** to clear the text from the line display.
3. Click **Release** to release the line display, so that it can be used for other processes.

#### Line display &gt; Advanced tab settings

- **Binary conversion** – Some line displays require that text be converted into binary format. To determine whether this conversion is required, see the device’s documentation.
- **Character set** – The code page for the characters that are sent to the device. For the identifiers of specific code pages, see <https://msdn.microsoft.com/library/windows/desktop/dd317756(v=vs.85).aspx>.

#### MSR

- **Open and claim MSR** – Prepare the POS simulator to receive data from the MSR.
- **Release and close MSR** – Close the MSR device when testing is completed.
- **Card info** – Data from the card that was scanned on the MSR device.

    > [!IMPORTANT]
    > Actual credit cards should never be used for device testing. Even expired credit cards should not be used for testing.

#### PIN pad

**Settings that appear on both tabs**

- **Lock** – Lock the PIN pad device so that it can be used only with the POS simulator.
- **Get entry** – Enable the POS simulator to receive PIN data.
- **Cancel operation** – Cancel the request that was sent to the PIN pad.
- **Release** – Release the PIN pad device.

**Settings tab**

- **Amount** – The amount to send to the PIN pad device for customer acceptance.
- **Account number** – Specify the account number, if it's required.
- **Encrypted PIN** – The encrypted PIN that is received from the device.
- **Additional security data** – Specify the cryptography that is used for the encrypted PIN.

**Advanced tab**

- **Timeout** – Specify the number of seconds to wait for a response from the device.
- **Exclusive** – Require that the PIN pad device be claimed before it can be enabled.
- **Override** – Override previous commands that were sent to device when the device isn't responding.

#### Scale

- **Timeout** – The time-out interval. Product should be put on the scale before the weight is read. If the scale doesn't respond within the specified interval, the request is canceled.

#### Signature capture

**Settings tab**

- **Form name** – Some signature capture devices require a form name when the signature request is sent.
- **Signature (in HEX)** – The hex value for the signature data that is received from the device.
- **Rendered signature** – The image of the signature that is received from the device.

**Advanced tab**

- **Timeout** – The time-out interval. If the signature capture device doesn't respond within the specified interval, the request is canceled.
- **Exclusive** – Require that the PIN pad device be claimed before it can be enabled.
- **Override** – Override previous commands that were sent to device when the device isn't responding.
- **Lock** – Lock the device and claim it for use by the POS simulator.
- **Get entry** – Request the signature from the device.
- **Cancel operation** – Cancel the signature request.
- **Release** – Release the device so that it can be used by other processes.

#### Bar code scanner

- **Open and claim scanner** – Open and claim the scanner. The POS simulator can receive scan events after this operation is completed successfully.
- **Release and close the scanner** – Make the scanner available for other processes.
- **Scanned information** – The data that was received from the bar code scanner.

#### Payment terminal

**Settings that appear on every tab**

- **Select an operation** – Select a specific operation to perform on the device. Options include **All**, **Pay by card**, **Refund by card**, and **Void payment**.
- **Lock and claim** – Prepare the device so that it can be used by the POS simulator.
- **Update line items** – Send specified line item details to the device.
- **Authorize payment** – Instruct the payment connector to request payment authorization.
- **Capture payment** – Instruct the payment connector to capture the previous authorization.
- **Release** – Release the device.

**Settings tab**

The **Settings** tab contains properties that are sent to the device when a payment authorization is requested.

- **Invoice number** – Specify the invoice number that is generated at the POS.
- **Test mode** – A value that indicates that a test transaction is being performed.
- **Payment connector** – The name of the payment connector to use.
- **Debit cashback limit** – The maximum amount of cash back that can be requested on the device when a debit transaction is performed.
- **Locale** – The locale that is used. Locales are defined in the configuration file for the POS simulator.
- **Maximum amount allowed** – The maximum amount that can be processed for a given transaction.
- **Minimum amount allowed** – The minimum amount that can be processed for a given transaction.
- **Signature capture minimum amount** – The lowest amount that the customer is prompted to provide a signature for.
- **Terminal ID** – The terminal ID that is included in the transaction properties that the processor provided.

**Lines tab**

The **Lines** tab contains data that can be sent to the device when it's used as a line display.

- **Description** – The product description for the transaction line to show on the device.
- **Discount** – The discount amount that is applied to the transaction line.
- **Extended line with tax** – The product line amount. This amount includes tax.
- **Line item ID** – The product ID for the transaction line.
- **Quantity** – The quantity for the transaction line.
- **Stock keeping unit** – The unit of measure to show on the device.
- **Unit price** – The selling price for the transaction line.
- **Universal product code** – The bar code that was scanned for the transaction line.
- **Is voided** – A value that indicates that the transaction line has been voided from the transaction.

**Advanced tab**

The **Advanced** tab contains subtotal information that can be shown on the device.

- **Discount amount** – The total amount for discounts on the transaction.
- **Subtotal amount** – The subtotal for the transaction. This amount doesn't include tax.
- **Tax amount** – The tax amount for the transaction.
- **Total amount** – The total amount that is due. This amount includes tax and discounts.
- **Currency** – The currency that is used for the transaction.

**Payment info tab**

The **Payment info** tab contains data that is received from the payment connector after an authorization has been processed.

- **Is approved** – A value that indicates whether the authorization request is approved.
- **Card number masked** – The masked card number that is provided by the device. Typically, only the last four digits of the card number are shown.
- **Card type** – The issue for the card that is used in the transaction.
- **Approved amount** – The amount that is authorized for the card payment.
- **Payment SDK data** – Additional data that the payment software development kit (SDK) can provide, such as the authorization code and other data that the payment processor provides.
- **Signature data** – Hexadecimal signature data that is provided by the device.
- **Payment errors** – Any errors that occurred during the authorization request.

## Instructions for device manufacturers

To submit a device so that it can be listed for compatibility with Commerce,  follow these steps.

1. On the **Settings** tab, specify all contact information that is requested. All fields are required. The personal contact information is for Microsoft internal use. It will be used only if there are issues with devices that have been submitted as compatible.
2. For each device, on the **Devices** tab, set up the device, and provide values for all fields. For each permutation, a new device must be specified. For example, if a given device mode is tested for USB and serial, two compatibility reports must be submitted. Any variance from one device to the next should be indicated. Then, when devices are listed for compatibility, very specific information can be provided to people who implement the devices. The more information that can be provided about device compatibility, the higher the success rate for implementations and the fewer support issues will be raised.
3. After you've entered the required information for devices and settings, test the device.

    1. Clear the log for the device that you're testing.
    2. Click **Self-test**.
    3. When a test has been completed successfully, export the test results, and save them. Give the file a name that will make the test easy to identify. We suggest that you use an abbreviated form of the manufacturer's name and the device model as the file name.

The following example shows the data that is included in the exported file.

```xml
<?xml version="1.0" encoding="utf-8"?>  
<Report xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/Microsoft.Dynamics.Commerce.VirtualPeripherals.Modules">  
   <CreationDateTime>05/27/2017 19:34:50</CreationDateTime>  
   <ManufacturerInfo>  
    <ManufacturerName>Contoso </ManufacturerName>  
    <ManufacturerWebsite>http://www.contoso.com</ManufacturerWebsite>  
    <SupportEmail>support@contoso.com</SupportEmail>  
    <SupportTelephoneNumber>555-555-5555</SupportTelephoneNumber>  
    <SupportWebsite>http://www.contoso.com</SupportWebsite>  
    <TechnicalContactEmail>karen@contoso.com</TechnicalContactEmail>  
    <TechnicalContactName>Karen Berg</TechnicalContactName>  
    <TechnicalContactPhone>555-555-5555</TechnicalContactPhone>  
  </ManufacturerInfo>  
  <DeviceInfo i:type="OposDevice">  
   <DeviceDriverName>MockOPOSDrawer1</DeviceDriverName>  
   <DeviceModel>Model1</DeviceModel>  
   <DriverVersion>V2</DriverVersion>  
   <FirmwareVersion>V1</FirmwareVersion>  
  <HardwareType>OPOS</HardwareType>  
  <ConnectionType>USB</ConnectionType>  
  <DriverDownloadLink>htttp://model1.drivers.contoso.com</DriverDownloadLink>  
 <DeviceInfo i:type="OposDevice">
 <LogItems>  
  <LogMessage>  
     <LogType>Info</LogType>  
     <Message>The cash drawer is opened successfully.</Message>  
     <Timestamp>05/27/2017 19:48:14</Timestamp>  
  </LogMessage>  
  <LogMessage>  
     <LogType>Info</LogType>  
     <Message>The cash drawer open operation elapsed time: 00:00:00.053</Message>  
     <Timestamp>05/27/2017 19:48:14</Timestamp>  
  </LogMessage>  
  <LogMessage>  
      <LogType>Info</LogType>  
      <Message>The cash drawer status check operation is completed successfully.</Message>  
      <Timestamp>05/27/2017 19:48:14</Timestamp>  
   </LogMessage>  
   <LogMessage>  
      <LogType>Info</LogType>  
      <Message>The cash drawer status check operation elapsed time: 00:00:00.045</Message>  
      <Timestamp>05/27/2017 19:48:14</Timestamp>  
   </LogMessage>  
      <LogMessage>  
      <LogType>Info</LogType>  
      <Message>Test finished successfully.</Message>  
      <Timestamp>05/27/2017 19:48:14</Timestamp>  
    </LogMessage>  
  </LogItems>  
</Report>
```

Eventually, the data that is included in the report (except personal contact information) will be listed on a device compatibility website. It will also be listed in design and deployment tools that are used to manage customer environments.

Successful logs should be sent to drpc@microsoft.com. Include the manufacturer’s name and the device model in the subject line.

For support if you're performing compatibility tests, and for other inquiries, send an email to drpc@microsoft.com.

## Additional resources

[Peripherals](../retail-peripherals-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
