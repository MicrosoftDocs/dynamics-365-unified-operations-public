---
# required metadata

title:  Fiscal registration service integration sample for Germany
description: This topic provides an overview of the fiscal integration sample for Germany.
author: josaw
manager: annbe
ms.date: 05/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Germany
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2020-5-29
ms.dyn365.ops.version: 10.0.12

---
# Fiscal registration service integration sample for Germany

[!include[banner](../includes/banner.md)]

## Introduction

To meet local fiscal requirements for cash registers in Germany, the Dynamics 365 Commerce functionality for Germany includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://www.efsta.eu/at/fiskalloesungen/oesterreich) solution from [EFSTA](https://www.efsta.eu/at/) and enables communication with the EFR service via the HTTPS protocol. The EFR service should be hosted on either the Retail Hardware station or a separate machine that can be connected to from the hardware station. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](https://www.efsta.eu/at/kontakt).


## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for Germany.

### Sales operations

- Registration of cash-and-carry sales and returns in the fiscal registration service:
    - The beginning of each transaction is registered in a **Technical security element (TSE)** connected to EFR.
    - As a result of the transaction start registration, a TSE assigns a **Transaction ID (TID)**.
    - When a transaction is concluded on POS, it is registered with the same TID that was assigned during registration of the transaction start. At that momen,t detailed transaction data is sent to the fiscal registration service. This data includes sales line information, and information about discounts, payments, and taxes.
    - It will capture a response from the fiscal registration service. The security data is received from TSE as a part of a response and saved in the transaction in the channel database. The security data consist of:
        - Transaction ID (TID)
        - Date and time of the transaction start
        - Date and time of the transaction end
        - Signature counter
        - Check value
        - Serial number of the Technical security element (TSE)

- Registration of customer orders in the fiscal registration service:
   - The registration process is the same as for cash-and-carry sales and returns.

- Registration of operations with gift cards and deposits:
   - The registration process is the same as for cash-and-carry sales and returns.

#### Notifying users about fiscal registration failures

There are two ways that the fiscal registration service can notify users about failures occurred during the fiscal registration:

- Print additional information from response in receipts in the **Info message** field.
- Display notifications from the fiscal service as a user message on POS.

> [!NOTE]
> The **Show fiscal registration notifications** parameter should be enabled on the **Connector technical profiles** page.

#### Printing receipts

Printing receipts is mandatory in Germany. All receipts must contain at least the following information:

- Name and address of the company
- Information about goods including their prices and quantities
- Information about payments received
- Information about taxes including total amounts per tax rate
- The security data:
    - Transaction ID (TID)
    - Date and time of the transaction start
    - Date and time of the transaction end
    - Signature counter
    - Check value
    - Serial number of the Technical security element (TSE)
- Info message

> [!NOTE]
> Printing a QR-code in receipts is optional but highly recommended. For more information how to get QR-code as a part of response from the fiscal registration service, see the **EFR Guide [DE]** document published on the [EFSTA documentation](https://public.efsta.net/efr/) web-site.
> **Info message** field in receipts displays a notification from the fiscal registration service, for example, if the signature device is broken.

#### Void, suspend, and recall transactions

- Voided transaction is registered as a request to terminate transaction in the fiscal registration service.
- Suspended transaction is registered as a request to terminate transaction in the fiscal registration service.
- Recall of suspended transaction is registered as beginning of a new transaction in the fiscal registration service.

### Non-sales transactions and shift closing

The following non-sales transactions are registered as non-fiscal operations in the fiscal registration service with the **NFS** tag:
- Declare start amount
- Float entry
- Tender removal
- Safe drop
- Bank drop
- Income accounts
- Expense accounts

The **Close shift** operation is also registered as a non-fiscal operation in the fiscal registration service with the **NFS** tag.

### Data export and audit

All transactions must be signed by a **Technical security element (TSE)** to ensure their integrity, authenticity and completeness and prevent manipulations with recorded data. 

> [!WARNING]
> Only certified TSE can be used. Please see the **EFR Guide [DE]** document published on the [EFSTA documentation](https://public.efsta.net/efr/) website to find what types and models of TSE are supported in the EFR solution. 
> For information about how to choose and obtain a TSE, contact [EFSTA](https://www.efsta.eu/at/kontakt).

Support of the DSFinV-K export is required due to regulations in Germany. The DSFinV-K export can be triggered in the EFR solution. 

> [!NOTE]
> For more information about the DSFinV-K export, see the **EFR Guide [DE]** document published on the [EFSTA documentation](https://public.efsta.net/efr/) web-site.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample.

- Tender type mapping:

    *1: 0; 2: 1; 3: 3; 4: 8; 5: 2; 6: 0; 7: 7; 8: 6; 9: 0; 10: 8; 11: 1*
    
> [!NOTE]
> In each pair of values separated by ';' the first number refers to a payment method set up for the store, and the second value means a respective payment group in the EFR service represented by the 'PayG' attribute.

- Value-added tax (VAT) rates mapping:

    *A: 19.00; B: 7.00; C: 10.70; D: 5.50; E: 0.00*
    
> [!NOTE]
> In each pair of values separated by ';' the letter refers to a tax group in the EFR service represented by the 'TaxG' attribute, and the second value refers to the tax percentage.

- Tax group for gift cards and deposits: *G*
- Tax group for VAT exempt: *F*

> [!WARNING]
> Tax settings in the default data mapping are responsible for matching between tax settings in the system and tax groups in the EFR service. Printing tax groups in receipts also requires the **Code for printing** field being specified on the **Sales tax codes** page. 

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in prices. Therefore, the **Prices include sales tax** option must be set to **Yes** for both stores and customers.

A situation when more than one sales tax code is applied to the same transaction line is not supported in the fiscal service.

Sales quotations are not supported in the fiscal integration framework and as a result, these operations are not registered in the fiscal service.

## Set up Commerce for Germany

This section describes the Commerce settings that are specific to and recommended for Germany. For more information set up information, see [Commerce home page](../index.md).

To use the Germany-specific functionality, you must specify the following settings.

- In the primary address of the legal entity, set the **Country/region** field to **DEU** (Germany).
- In the POS functionality profile of every store that is located in Austria, set the **ISO code** field to **DE** (Germany).

You must also specify the following settings for Germany. Be sure to run appropriate distribution jobs after you complete the setup.

### Set up VAT per German requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).


On sales receipts, you can print an abbreviated code for a sales tax code (for example, "A" or "B"). To make this functionality available, set the **Code for printing** field on the **Sales tax codes** page.

### Set up stores

On the **All stores** page, update the store details. Specifically, set the following parameters:

- In the **Sales tax group** field, specify the sales tax group that should be used for sales to the default customer.
- Set the **Prices include sales tax** option to **Yes**.
- Set the **Name** field to the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-form text.
- Set the **Tax identification number (TIN)** field to the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-form text.

### Set up functionality profiles

Set up POS functionality profiles.

- On the **Receipt numbering** FastTab, set up receipt numbering by creating or updating records for the **Sale**, **Sales order**, and **Return** receipt transaction types.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                                   |
|-------------|---------|----------------------------------------|
| en-US       | 900001  | QR code                                |
| en-US       | 900002  | Transaction ID                         |
| en-US       | 900003  | Tax Retail Print Code                  |
| en-US       | 900004  | Tax Amount (sales)                     |
| en-US       | 900005  | Tax Basis (sales)                      |
| en-US       | 900006  | Transaction start date time            |
| en-US       | 900007  | Transaction end date time              |
| en-US       | 900008  | Serial number of the security element  |
| en-US       | 900009  | Signature counter                      |
| en-US       | 900010  | Check value                            |
| en-US       | 900011  | Info message                           |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                           | Type    | Caption text ID |
|--------------------------------|---------|-----------------|
| QRCODE_DE                      | Receipt | 900001          |
| TRANSACTIONID_DE               | Receipt | 900002          |
| RETAILPRINTCODE_DE             | Receipt | 900003          |
| SALESTAXAMOUNT_DE              | Receipt | 900004          |
| SALESTAXBASIS_DE               | Receipt | 900005          |
| TRANSACTIONSTARTDATETIME_DE    | Receipt | 900006          |
| TRANSACTIONENDDATETIME_DE      | Receipt | 900007          |
| SECURITYELEMENTSERIALNUMBER_DE | Receipt | 900008          |
| SIGNCOUNTER_DE                 | Receipt | 900009          |
| SIGN_DE                        | Receipt | 900010          |
| INFOMESSAGE_DE                 | Receipt | 900011          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

    - **Store name** and **Tax Identification Number** fields, which are used to print the company name and identity number on receipts. Alternatively, you can add the company name and identity number to the layout as free-form text.
    - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
    
- **Lines:** Add the following fields:

    - **Item name**.
    - **Qty**.
    - **Total price with tax**.
    - **Tax Retail Print Code**, which is used to print the abbreviated code that corresponds to the sales tax code that applies to the item.

- **Footer:** Add the following fields:

    - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.

    - **Tax break down** field group. The fields in this field group must be printed on a separate line.

        - **Tax Id** field, which is a standard field that enables a sales tax summary to be printed for each sales tax code. The field must be added to a new line.
        - **Tax Percentage** field, which is a standard field that is used to print the effective tax rate for the sales tax code.
        - **Tax Basis (sales)** field, which is used to print the receipt's total cash sale amount for the sales tax code. Prepayments and gift card operations are excluded.
        - **Tax Amount (sales)** field, which is used to print the receipt's tax amount for cash sales for the sales tax code.
        - **Tax Retail Print Code** field, which is used to print the abbreviated code that corresponds to the sales tax code.

    - Fields with secured transaction data returned by the fiscal registration service:
        - **Transaction ID** field to identify the number of the cash transaction in the fiscal registration service. 
        - **Transaction start date time**.
        - **Transaction end date time**.
        - **Serial number of the security element**.
        - **Signature counter**.
        - **Check value**.
        - **QR Code** field, which is used to print the reference to the registered cash transaction in the form of QR code.

    - **Info message** field to display notification messages from the fiscal registration service in receipts. For example, if a signature device is broken, then a special text is printed in a receipt. 

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Configure fiscal integration

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).

> [!WARNING]
> The error handling capabilities of the fiscal integration framework may be not fully aligned with the local fiscal regulations.
>    - It is not recommended to enable the **Continue on error** option on the **Fiscal registration process** page, as all transactions must be properly registered even if the first attempt of the fiscal registration was not successful.
>    - Before enabling **Skip** or **Mark as registered** option on the **Fiscal registration process** page, you should verify these changes of the fiscal registration process with your tax consultant or with the local tax office. 

- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

## Deployment guidelines for cash registers for Germany

The fiscal registration service integration sample for Germany is a part of the Retail SDK. For more information about how to install and use the Retail SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the CRT and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

Follow these steps to set up a development environment so that you can test and extend the sample.

### Enable Commerce runtime extensions

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### DocumentProvider.EFRSample component

1. Find the **Runtime.Extensions.DocumentProvider.EFRSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.EFRSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit**: Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS**: Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit**: The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS**: The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
    ```

#### DocumentProvider.DataModelEFR component

1. Find the **Runtime.Extensions.DocumentProvider.DataModelEFR** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.DataModelEFR\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit**: Copy the assembly to the **\\bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS**: Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit**: The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS**: The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
    ```

#### Update extension configuration file

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit**: The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS**: The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsGermany" />
    ```

### Enable Hardware station extensions

The Hardware station extension components are included in the Hardware station samples. To complete the following procedures, open the solution **HardwareStationSamples.sln.sln** under **RetailSdk\\SampleExtensions\\HardwareStation**.

#### EFRSample component

1. Find the **HardwareStation.Extension.EFRSample** project, and build it.
2. In the **Extension.EFRSample\bin\Debug** folder, find following files:

    - The **Contoso.Commerce.HardwareStation.EFRSample.dll** assembly.
    - The **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly.

3. Copy the assembly files to the Hardware station extensions folder:

    - **Shared hardware station**: Copy the files to the **bin** folder under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS**: Copy the files to the Modern POS client broker location.

4. Find the extension configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**.

    - **Shared hardware station**: The file is located under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS**: The file is located under the Modern POS client broker location.

5. Add the following line to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample.dll" />
    ```

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce Headquarters. For more details, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configurations. The configuration file is **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration\\DocumentProviderFiscalEFRSampleGermany.xml**.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.

> [!NOTE]
> By default, the **Include customer data** parameter is enabled. You can toggle it to **No** to avoid sending information about customers such as their names and addresses to the fiscal registration service.

5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.

> [!WARNING]
> By default, the **Show fiscal registration notifications** parameter is enabled. It is recommended to leave it enabled as the fiscal registration service is sending notifications about some specific errors occurred during the fiscal registration, for example, if a transaction was not signed at the moment of registration.

6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group, for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder.

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsGermany" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample" />
        ```

2. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file.

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

3. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
5. Complete all the required setup tasks that are described in the [Set up Commerce for Germany](#set-up-commerce-for-germany) section.

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

The CRT extension is **Runtime.Extensions.DocumentProvider.EFRSample**. For more details about the design of the fiscal integration solution, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler
	
There is a single **DocumentProviderEFRFiscalDEU** request handler for document provider, which is used to generate fiscal documents for the fiscal registration service. This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetFiscalTransactionExtendedDataDocumentProviderRequest** - This request returns the response with extended data. 

#### Configuration

The **DocumentProviderFiscalEFRSampleGermany** configuration file is located in the **Configuration** folder of the extension project. The purpose of this file is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. 

The following settings are added:

- **VAT rates mapping** - mapping of tax percentage values that are set up for the sales tax codes, to values of the **TaxG** attribute (Tax group) in requests sent to the fiscal service.
- **Tax group for gift cards and deposits** - value of the **TaxG** attribute in requests sent to the fiscal service based on operations with gift cards or deposits.
- **Tender type mapping** - mapping of payment methods to values of the **PayG** attribute (payment group) in requests sent to the fiscal service.
- **Tax group for VAT exempt** - value of the **TaxG** attribute in requests sent to the fiscal service based on operations that are exempt from tax obligations.
- **Include customer data** - if this parameter is enabled, then requests to the fiscal service will contain information about customers such as their names and addresses, where a customer is added to a transaction.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.EFRSample**. The Hardware station extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **EFRHandler** request handler is the entry point for handling requests to the fiscal registration service. The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the fiscal connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added. 

The following settings are added:

- **Endpoint address** – the URL of the fiscal registration service.
- **Timeout** – the amount of time, in milliseconds, that the driver will wait for a response from the fiscal registration service.
- **Show fiscal registration notifications** - if this parameter is enabled, POS will display notifications from the fiscal service as a user message on POS.
