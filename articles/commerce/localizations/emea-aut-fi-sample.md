---

# required metadata

title: Fiscal registration service integration sample for Austria
description: This topic provides an overview of the fiscal integration sample for Austria.
author: josaw
manager: annbe
ms.date: 03/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria
ms.search.industry: Retail
ms.author: v-dmpere
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---
# Fiscal registration service integration sample for Austria

[!include[banner](../includes/banner.md)]

## Introduction

To meet local fiscal requirements for cash registers in Austria, the Dynamics 365 Commerce functionality for Austria includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://efsta.org/sicherheitsloesungen/) solution from [EFSTA](https://efsta.org/) and enables communication with the EFR service via the HTTPS protocol. The EFR service should be hosted on either the Commerce Hardware station or a separate machine that can be connected to from the Hardware station. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](https://efsta.org/kontakt/).

## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for Austria:

- Registration of cash transactions in the fiscal registration service:

    - Send detailed transaction data to the fiscal registration service. This data includes sales line information, and information about discounts, payments, and taxes.
    - Capture a response from the fiscal registration service. This response includes a digital signature and a link to the registered transaction.
    - Register taxes, and map them to the fiscal registration service's tax codes.
    - Print the QR code for a registered transaction on the receipt.

- Registration of gift card operations and customer deposits as non-cash transactions in the fiscal registration service:

    - Issue or add money to a gift card.
    - Register a customer account deposit.
    - Register a customer order deposit.

- Registration of non-sales transactions and events as non-cash transactions in the fiscal registration service:

    - Open shift and Close shift
    - Start amount, Float entry, and Tender removal
    - Price override
    - Tax override
    - Print copy of receipt
    - Open drawer
    - Print X report
    - Print Z report

- Printing end-of-day statements (X/Z reports) that have Austria-specific fields:

    - Total number of products or services that were delivered to customers
    - Breakdown of sales by tax rate
    - Breakdown of payments by cashier/cash register operator
    - Price discounts and returns that reduce daily sales
    - Zero sales (giveaways)

- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal registration service isn't available, isn't ready, or isn't responding.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal registration service before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- Value-added tax (VAT) rates mapping:

    *A: 20.00; B: 10.00; C: 13.00; D: 0.00; E: 19.00; F: 7.00*

### Gift cards

The fiscal registration service integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from a cash transaction. Instead of registering those lines as a part of a cash transaction, register them as a separate non-cash transaction in the fiscal registration service.
- Don't print a tax group breakdown and a QR code on a receipt if the receipt consists only of gift card lines.
- Print the total amount of gift cards that are issued or re-charged in a transaction separately from the cash transaction amount on the receipt.
- Save calculated adjustments of payment lines in the channel database with a reference to a corresponding fiscal transaction.
- Payment by gift card is considered a regular payment.

### Customer deposits and customer order deposits

The fiscal registration service integration sample implements the following rules that are related to customer deposits and customer order deposits:

- Register a non-cash transaction if a transaction is a customer deposit.
- Register a non-cash transaction if a transaction contains only a customer order deposit or a customer order deposit refund.
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
- Save calculated adjustments of payment lines in the channel database with a reference to a fiscal transaction for a hybrid customer order.

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.

## Set up Commerce for Austria

This section describes the Commerce settings that are specific to and recommended for Austria. For more information set up information, see [Commerce home page](../index.md).

To use the Austria-specific functionality, you must specify the following settings:

- In the primary address of the legal entity, set the **Country/region** field to **AUT** (Austria).
- In the POS functionality profile of every store that is located in Austria, set the **ISO code** field to **AT** (Austria).

You must also specify the following settings for Austria. Note that you must run appropriate distribution jobs after you complete the setup.

### Set up VAT per Austrian requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).


On sales receipts, you can print an abbreviated code for a sales tax code (for example, "A" or "B"). To make this functionality available, set the **Print code** field on the **Sales tax codes** page.

### Set up stores

On the **All stores** page, update the store details. Specifically, set the following parameters:

- In the **Sales tax group** field, specify the sales tax group that should be used for sales to the default customer.
- Set the **Prices include sales tax** option to **Yes**.
- Set the **Name** field to the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-form text.
- Set the **Tax identification number (TIN)** field to the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-form text.

### Set up functionality profiles

Set up POS functionality profiles:

- On the **Receipt numbering** FastTab, set up receipt numbering by creating or updating records for the **Sale**, **Sales order**, and **Return** receipt transaction types.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                      |
|-------------|---------|---------------------------|
| en-US       | 900001  | QR Code                   |
| en-US       | 900002  | Continuous Number         |
| en-US       | 900003  | Tax Retail Print Code     |
| en-US       | 900004  | Total (sales)             |
| en-US       | 900005  | Total Tax (sales)         |
| en-US       | 900006  | Total Include Tax (sales) |
| en-US       | 900007  | Tax Amount (sales)        |
| en-US       | 900008  | Tax Basis (sales)         |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                 | Type    | Caption text ID |
|----------------------|---------|-----------------|
| QRCODE               | Receipt | 900001          |
| CONTINUOUSNUMBER     | Receipt | 900002          |
| RETAILPRINTCODE      | Receipt | 900003          |
| SALESTOTAL           | Receipt | 900004          |
| SALESTOTALTAX        | Receipt | 900005          |
| SALESTOTALINCLUDETAX | Receipt | 900006          |
| SALESTAXAMOUNT       | Receipt | 900007          |
| SALESTAXBASIS        | Receipt | 900008          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

    - **Store name** and **Tax Identification Number** fields, which are used to print the company name and identity number on receipts. Alternatively, you can add the company name and identity number to the layout as free-form text.
    - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
    - **Continuous Number** fields, to identify the number of the cash transaction in the fiscal registration service.

- **Lines:** Add the following fields:

    - **Item name**.
    - **Qty**.
    - **Total price with tax**.
    - **Tax Retail Print Code**, which is used to print the abbreviated code that corresponds to the sales tax code that applies to the item.

- **Footer:** Add the following fields:

    - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.
    - **Sales total** field group:

        - **Total (sales)** field, which is used to print the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
        - **Total Include Tax (sales)** field, which is used to print the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
        - **Total Tax (sales)** field, which is used to print the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded.

    - **Tax break down** field group. The fields in this field group must be printed on a separate line.

        - **Tax Id** field, which is a standard field that enables a sales tax summary to be printed for each sales tax code. The field must be added to a new line.
        - **Tax Percentage** field, which is a standard field that is used to print the effective tax rate for the sales tax code.
        - **Tax Basis (sales)** field, which is used to print the receipt's total cash sale amount for the sales tax code. Prepayments and gift card operations are excluded.
        - **Tax Amount (sales)** field, which is used to print the receipt's tax amount for cash sales for the sales tax code.
        - **Tax Retail Print Code** field, which is used to print the abbreviated code that corresponds to the sales tax code.

    - **QR Code** field, which is used to print the reference to the registered cash transaction in the form of QR code.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Configure fiscal integration

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

## Deployment guidelines for cash registers for Austria

The fiscal registration service integration sample for Austria is part of the Retail SDK. For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the CRT, Hardware station, and POS. To run this sample, you must modify and build the CRT, Hardware station, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

Follow these steps to set up a development environment so that you can test and extend the sample.

### Enable Commerce runtime extensions

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### DocumentProvider.EFRSample component

1. Find the **Runtime.Extensions.DocumentProvider.EFRSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.EFRSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
    ```

#### DocumentProvider.DataModelEFR component

1. Find the **Runtime.Extensions.DocumentProvider.DataModelEFR** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.DataModelEFR\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
    ```

#### Update extension configuration file

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
    ```

### Enable Hardware station extensions

The Hardware station extension components are included in the Hardware station samples. To complete the following procedures, open the solution, **HardwareStationSamples.sln.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

#### EFRSample component

1. Find the **HardwareStation.Extension.EFRSample** project, and build it.
2. In the **Extension.EFRSample\\bin\\Debug** folder, find following files:

    - The **Contoso.Commerce.HardwareStation.EFRSample.dll** assembly
    - The **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly

3. Copy the assembly files to the Hardware station extensions folder:

    - **Shared hardware station:** Copy the files to the **bin** folder under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** Copy the files to the Modern POS client broker location.

4. Find the extension configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**.

    - **Shared hardware station:** The file is located under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** The file is located under the Modern POS client broker location.

5. Add the following line to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample.dll" />
    ```

### Enable Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions to be loaded by adding the following lines in **extensions.json**.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.AT"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extensions to be loaded by adding the following lines in **extensions.json**.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.AT"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.

### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configurations. The configuration files are located under **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration**:

    - DocumentProviderEFRSampleAustria.xml
    - DocumentProviderNonFiscalEFRSampleAustria.xml

4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create two new connector functional profiles, one for each document provider that you loaded earlier, and select the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create two new fiscal connector groups, one for each connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, two fiscal registration process steps, and select the fiscal connector groups that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. To enable registration of non-fiscal events on the POS, on the **Functions** FastTab, under **POS**, set the **Audit** option to **Yes**.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample" />
        ```

2. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file:

    - Add the following lines to include the CRT extensions in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
        ```

    - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.EFRSample" />
        ```

3. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
5. Complete all the required setup tasks that are described in the [Set up Commerce for Austria](#set-up-commerce-for-austria) section.

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

The CRT extension is **Runtime.Extensions.DocumentProvider.EFRSample**.

For more details about the design of the fiscal integration solution, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler
	
There are two request handlers for document providers:

- **DocumentProviderEFRFiscalAUT** – This handler is used to generate fiscal documents for the fiscal registration service.
- **DocumentProviderEFRNonFiscalAUT** – This handler is used to generate non-fiscal documents for the fiscal registration service.

These handlers are inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetNonFiscalDocumentDocumentProviderRequest** – This request contains information about what non-fiscal document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, printing Z report, customer account deposits, customer order deposits, audit events, and non-sales transactions.
- **GetFiscalRegisterResponseToSaveDocumentProviderRequest** – This request returns the response from the fiscal registration service. This response is serialized to form a string so that it's ready to be saved.

#### Configuration

The configuration files are located in the **Configuration** folder of the extension project:

- **DocumentProviderFiscalEFRSampleAustria** – For fiscal documents.
- **DocumentProviderNonFiscalEFRSampleAustria** – For non-fiscal documents.

The purpose of these files is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following setting is added:

- VAT rates mapping

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.EFRSample**. The Hardware station extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **EFRHandler** request handler is the entry point for handling requests to the fiscal registration service.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the fiscal connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the fiscal registration service.
