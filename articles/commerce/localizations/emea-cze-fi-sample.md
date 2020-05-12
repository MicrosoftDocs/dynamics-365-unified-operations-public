---

# required metadata

title: Fiscal registration service integration sample for Czech Republic
description: This topic provides an overview of the fiscal integration sample for Czech Republic.
author: josaw
manager: annbe
ms.date: 05/16/2019
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
ms.search.region: Czech Republic
ms.search.industry: Retail
ms.author: v-dmpere
ms.search.validFrom: 2019-4-1
ms.dyn365.ops.version: 10.0.2

---
# Fiscal registration service integration sample for Czech Republic


[!include[banner](../includes/banner.md)]

## Introduction

To meet local fiscal requirements for cash registers in the Czech Republic, the Dynamics 365 Commerce functionality for the Czech Republic includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://efsta.org/sicherheitsloesungen/) solution from [EFSTA](https://efsta.org/) and enables communication with the EFR service via the HTTPS protocol. The EFR service ensures Electronic Registration of Sales (EET - Elektronická evidence tržeb), that is, the online transmission of the sales data to a fiscal web service of tax authorities.

The EFR service should be hosted on either the Commerce Hardware station or a separate machine that can be connected to from the Hardware station. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](https://efsta.org/kontakt/).

## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for the Czech Republic.

- Registration of cash transactions in the fiscal registration service.

    - Send detailed transaction data to the fiscal registration service. This data includes sales line information, and information about discounts, payments, and taxes. The fiscal registration service further sends the data to the web-service of tax authorities and receives a confirmation from it that includes the fiscal identification code of the transaction.
    - Capture a response from the fiscal registration service. This response includes fiscal data such as the fiscal identification code and the security code of the transaction, etc.
    - Print the fiscal data for a registered transaction on the receipt.

- Registration of gift card operations and customer deposits in the fiscal registration service.

    - Issue or add money to a gift card.
    - Register a customer account deposit.
    - Create a customer order and register a deposit for the order.
    - Edit a customer order and override the deposit for the order.
    - Cancel a customer order and refund the deposit for the order.

- Error handling, such as the following options.

    - Retry fiscal registration if a retry is possible, such as if the fiscal registration service isn't available, isn't ready, or isn't responding.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal registration service before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample.

- Value-added tax (VAT) rates mapping:

    *A: 21.00; B: 15.00; C: 10.00; Z: 0.00*

- Default VAT group mapping. Any VAT amounts that cannot be mapped to one of the predetermined VAT groups will be attributed to the default (basic) VAT group:

    *A*

- Deposit VAT group mapping. Customer deposit amounts and customer order deposit amounts will be attributed to the deposit VAT group:

    *Z*

### Gift cards

The fiscal registration service integration sample implements the following rules that are related to gift cards.

- Sales lines that are related to the *Issue gift card* or *Add to gift card* operations in a sales transaction are marked with a special attribute when the transaction is registered in the fiscal registration service.
- A payment by gift card is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.

### Customer account deposits and customer order deposits

The fiscal registration service integration sample implements the following rules that are related to customer account deposits and customer order deposits.

- A transaction that is related to a customer account deposit or a customer order deposit is registered in the fiscal registration service as a single line transaction and is marked with a special attribute. The deposit VAT group is specified in this line.
- When a hybrid customer order is created, that is, a customer order that contains products that can be carried out of the store by the customer, as well as products that will be picked up or shipped later, the transaction registered in the fiscal registration service contains lines for the products that are carried out, as well as a line for the order deposit.
- A payment from a customer account is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.
- The customer order deposit amount that is applied to a customer order *Pick up* operation is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.

### Offline registration

If the fiscal registration service fails to transmit transaction data to the fiscal web service of tax authorities (e.g. due to the response timeout) and to receive a confirmation from the web-service (that is, the fiscal identification code of the transaction), it generates a local signature for the transaction and includes it and a special error code in the response. The fiscal registration service resends transactions in original order in background as soon as the network connection is restored.

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.

## Set up Commerce for Czech Republic

This section describes the Commerce settings that are specific to and recommended for the Czech Republic. For more information, see [Commerce home page](../index.md).

To use the Czech-specific functionality, you must specify the following settings.

- In the primary address of the legal entity, set the **Country/region** field to **CZE** (Czech Republic).
- In the POS functionality profile of every store that is located in the Czech Republic, set the **ISO code** field to **CZ** (Czech Republic).

You must also specify the following settings for the Czech Republic. Note that you must run appropriate distribution jobs after you complete the setup.

### Set up VAT per Czech Republic


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).


### Set up stores

On the **All stores** page, update the store details. Specifically, set the following parameters.

- In the **Sales tax group** field, specify the sales tax group that should be used for sales to the default customer.
- Set the **Prices include sales tax** option to **Yes**.
- Set the **Name** field to the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-form text.
- Set the **Tax identification number (TIN)** field to the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-form text.

### Set up functionality profiles

Set up POS functionality profiles.

- On the **Receipt numbering** FastTab, set up receipt numbering by creating or updating records for the **Sale**, **Sales order**, and **Return** receipt transaction types.

### Set up registration numbers

1. Go to **Organization administration \> Global address book \> Registration types \> Registration types**. Create a new registration type. Specify the **Country/region** field to **CZE** (Czech Republic) and make it restricted to Organization.
2. Go to **Organization administration \> Global address book \> Registration types \> Registration categories**. Create a new registration category. Select the registration type from the previous step and set the **Registration category** to **Business Premise ID**.
3. Go to **Organization administration \> Organizations \> Operating units**. For each store located in the Czech Republic, select the unit related to the store. On the **Address** FastTab expand the **More options** drop-down list and select **Advanced**. 
4. On the opened **Manage addresses** page you must specify following setting.

    - On the **Address** FastTab set the **Country/region** field to **CZE**.
    - On the **Registration ID** FastTab create a new record. Select the registration type created earlier and set the registration number.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                   |
|-------------|---------|------------------------|
| en-US       | 900001  | ID provozovny/pokladny |
| en-US       | 900002  | BKP                    |
| en-US       | 900003  | FIK                    |
| en-US       | 900004  | PKP                    |
| en-US       | 900005  | Info                   |
| en-US       | 900006  | Sequence number        |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                 | Type    | Caption text ID |
|----------------------|---------|-----------------|
| TLT                  | Receipt | 900001          |
| SEC                  | Receipt | 900002          |
| SIGN                 | Receipt | 900003          |
| FISCAL               | Receipt | 900004          |
| INFO                 | Receipt | 900005          |
| CONTINUOUSNUMBER     | Receipt | 900006          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields.

    - **Store name** and **Tax Identification Number**: these fields are used to print the company name and identity number on receipts. Alternatively, you can add the company name and identity number to the layout as free-form text.
    - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number**.
    - **Sequence number**: this field identifies the number of the cash transaction in the fiscal registration service.

- **Lines:** Add the following fields.

    - **Item name**
    - **Qty**
    - **Total price with tax**

- **Footer:** Add the following fields.

    - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.
    - **ID provozovny/pokladny**: this field prints the identifiers of the business premises and the cash register.
    - **BKP**: this field prints the taxpayer's security code that is assigned by the fiscal registration service.
    - **FIK**: this field prints the fiscal identification code of the transaction that is assigned by the web-service of tax authorities in case of successful online registration.
    - **PKP**: this field prints the taxpayer's signature code that is generated by the fiscal registration service in case of offline registration.
    - **Info**: this field prints the additional information from the fiscal registration service.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Configure fiscal integration

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

## Deployment guidelines for cash registers for Czech Republic

The fiscal registration service integration sample for the Czech Republic is part of the Retail SDK. For information about how to install and use the Retail SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the CRT and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

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
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsCzechia" />
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

### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The configuration file is  **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration\\DocumentProviderFiscalEFRSampleCzech.xml**.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group, for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder.

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsCzechia" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample" />
        ```

2. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file.

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
5. Complete all the required setup tasks that are described in the [Set up Commerce for Czech Republic](#set-up-commerce-for-czech-republic) section.

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

The CRT extension is **Runtime.Extensions.DocumentProvider.EFRSample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler
	
There is a single **DocumentProviderEFRFiscalCZE** request handler for document provider, which is used to generate fiscal documents for the fiscal registration service.

This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests.

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, customer account deposits and customer order deposits.
- **GetFiscalRegisterResponseToSaveDocumentProviderRequest** – This request returns the response from the fiscal registration service. This response is serialized to form a string so that it's ready to be saved.

#### Configuration

The **DocumentProviderFiscalEFRSampleCzech** configuration file is located in the **Configuration** folder of the extension project.
The purpose of this file is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added.

- VAT rates mapping
- Default VAT group
- Deposit VAT group

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.EFRSample**. The Hardware station extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **EFRHandler** request handler is the entry point for handling requests to the fiscal registration service.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Headquarters.

The connector supports the following requests.

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the fiscal connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added.

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the fiscal registration service.
