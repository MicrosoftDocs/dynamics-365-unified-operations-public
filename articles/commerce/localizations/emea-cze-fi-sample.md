---
title: Fiscal registration service integration sample for the Czech Republic
description: This article provides an overview of the fiscal integration sample for the Czech Republic in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 10/04/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-04-01

---
# Fiscal registration service integration sample for the Czech Republic

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides an overview of the fiscal integration sample for the Czech Republic in Microsoft Dynamics 365 Commerce.

To meet local fiscal requirements for cash registers in the Czech Republic, the Dynamics 365 Commerce functionality for the Czech Republic includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://efsta.org/sicherheitsloesungen/) solution from [EFSTA](https://efsta.org/) and enables communication with the EFR service via the HTTPS protocol. The EFR service ensures Electronic Registration of Sales (Elektronická evidence tržeb \[EET\]). In other words, it ensures online transmission of the sales data to a fiscal web service of tax authorities. The EFR service should be hosted on either the Commerce Hardware station or a separate machine that can be connected to from the Hardware station. The sample is provided in the form of source code and is part of the Commerce software development kit (SDK).

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
    - Defer fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal registration service before a new sales transaction is opened or a sales transaction is finalized.

### Gift cards

The fiscal registration service integration sample implements the following rules that are related to gift cards.

- Sales lines that are related to the *Issue gift card* or *Add to gift card* operations in a sales transaction are marked with a special attribute when the transaction is registered in the fiscal registration service.
- A payment by gift card is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.

### Customer account deposits and customer order deposits

The fiscal registration service integration sample implements the following rules that are related to customer account deposits and customer order deposits.

- A transaction that is related to a customer account deposit or a customer order deposit is registered in the fiscal registration service as a single line transaction and is marked with a special attribute. The deposit VAT group is specified in this line.
- When a hybrid customer order is created, that is, a customer order that contains products that can be carried out of the store by the customer, as well as products that will be picked up or shipped later, the transaction registered in the fiscal registration service contains lines for the products that are carried out, as well as a line for the order deposit.
- A payment from a customer account is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.
- The customer order deposit amount that is applied to a customer order pickup operation is considered a regular payment and marked with a special attribute when the transaction is registered in the fiscal registration service.

### Offline registration

If the fiscal registration service fails to transmit transaction data to the fiscal web service of tax authorities (for example, due to the response timeout) and to receive a confirmation from the web-service (that is, the fiscal identification code of the transaction), it generates a local signature for the transaction and includes it and a special error code in the response. The fiscal registration service resends transactions in original order in background as soon as the network connection is restored.

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.

## Set up Commerce for the Czech Republic

This section describes the Commerce settings that are specific to and recommended for the Czech Republic. For more information, see [Commerce home page](../welcome.md).

To use the Czech-specific functionality, you must specify the following settings.

- In the primary address of the legal entity, set the **Country/region** field to **CZE** (Czech Republic).
- In the POS functionality profile of every store that is located in the Czech Republic, set the **ISO code** field to **CZ** (Czech Republic).

You must also specify the following settings for the Czech Republic. Note that you must run appropriate distribution jobs after you complete the setup.

### Set up VAT per Czech Republic requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview.md).

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
4. On the opened **Manage addresses** page you must specify the following settings:

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
| en-US       | 900003  | PKP                    |
| en-US       | 900004  | FIK                    |
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

> [!NOTE]
> It's important that you specify correct custom field names, as listed in the preceding table. An incorrect custom field name will cause missing data in receipts.

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

## Set up fiscal integration for the Czech Republic

The fiscal registration service integration sample for the Czech Republic is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Commerce SDK. The sample is located in the **src\\FiscalIntegration\\Efr** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The [sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) consists of a fiscal document provider, which is an extension of the Commerce runtime (CRT), and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Commerce SDK, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!NOTE]
> The fiscal registration service integration sample for the Czech Republic is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for the fiscal integration sample for the Czech Republic (legacy)](emea-cze-fi-sample-sdk.md).

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Also, make a note of the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of deferred fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-deferred-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce headquarters. For more information, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Select a correct release branch version according to your SDK/application version.
    1. Open **src \> FiscalIntegration \> Efr**.
    1. Download the fiscal document provider configuration file at **Configurations \> DocumentProviders \> DocumentProviderFiscalEFRSampleCzech.xml**.
    1. Download the fiscal connector configuration file at **Configurations \> Connectors \> ConnectorEFRSample.xml**.

    > [!NOTE]
    > In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. The configuration files for this fiscal integration sample are located in the following folders of the Retail SDK on a developer VM in LCS:
    >
    > - **Fiscal document provider configuration file:** RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration\\DocumentProviderFiscalEFRSampleCzech.xml
    > - **Fiscal connector configuration file:** RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the [data mapping settings](#default-data-mapping) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the fiscal connector that you loaded earlier. Update the [connector settings](#fiscal-connector-settings) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process and a fiscal registration process step, and select the fiscal connector group that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal registration service will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
1. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- **Value-added tax (VAT) rates mapping** – The mapping of tax percentage values that are set up for the sales tax codes to values of the **TaxG** (tax group) attribute in requests that are sent to the fiscal service. Here is the default mapping:

    ```
    A: 21.00; B: 15.00; C: 10.00; Z: 0.00
    ```

    The first component in each pair represents a VAT tax group that is supported by the EFR fiscal registration service. The second component represents the corresponding VAT rate. For more information about VAT tax groups that EFR supports for the Czech Republic, see the [EFR reference](https://public.efsta.net/efr/).

- **Default VAT group mapping** – Any VAT amounts that can't be mapped to one of the predetermined VAT groups will be attributed to the default (basic) VAT group. Here is the default mapping:

    ```
    A
    ```

- **Deposit VAT group mapping** – Customer deposit amounts and customer order deposit amounts will be attributed to the deposit VAT group. Here is the default mapping:

    ```
    Z
    ```

#### Fiscal connector settings

The following settings are included in the fiscal connector configuration that is provided as part of the fiscal integration sample:

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the fiscal connector will wait for a response from the fiscal registration service.

### Configure channel components

> [!NOTE]
> - The fiscal registration service integration sample for the Czech Republic is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal integration sample for the Czech Republic (legacy)](emea-cze-fi-sample-sdk.md).
> - Commerce samples that are deployed in your environment aren't automatically updated when you apply service or quality updates to Commerce components. You must manually update the required samples.

#### Set up the development environment

To set up a development environment to test and extend the sample, follow these steps.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
1. Open the EFR solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\EFR.sln**, and build it.
1. Install CRT extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **Efr\\ScaleUnit\\ScaleUnit.EFR.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.EFR.Installer** installer.
        - **Local CRT on Modern POS:** In the **Efr\\ModernPOS\\ModernPOS.EFR.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.EFR.Installer** installer.

    1. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.EFR.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.EFR.Installer.exe install --verbosity 0
            ```

1. Install fiscal connector extensions:

    You can install fiscal connector extensions on the [Hardware station](fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-via-a-device-connected-to-the-hardware-station) or the [POS register](fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-via-a-device-or-service-in-the-local-network).

    1. Install Hardware station extensions:

        1. In the **Efr\\HardwareStation\\HardwareStation.EFR.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.EFR.Installer** installer.
        1. Start the extension installer from the command line by running the following command.

            ```Console
            HardwareStation.EFR.Installer.exe install --verbosity 0
            ```

    1. Install POS extensions:

        1. Open the POS fiscal connector sample solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\PosFiscalConnectorSample\\Contoso.PosFiscalConnectorSample.sln**, and build it.
        1. In the **PosFiscalConnectorSample\\StoreCommerce.Installer\\bin\\Debug\\net461** folder, find the **Contoso.PosFiscalConnectorSample.StoreCommerce.Installer** installer.
        1. Start the extension installer from the command line by running the following command.

            ```Console
            Contoso.PosFiscalConnectorSample.StoreCommerce.Installer.exe install --verbosity 0
            ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **EFR build-pipeline.yml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

## Design of extensions

The fiscal registration service integration sample for the Czech Republic is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Commerce SDK. The sample is located in the **src\\FiscalIntegration\\Efr** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The [sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) consists of a fiscal document provider, which is an extension of CRT, and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Commerce SDK, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!NOTE]
> The fiscal registration service integration sample for the Czech Republic is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal integration sample for the Czech Republic (legacy)](emea-cze-fi-sample-sdk.md).

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

#### Request handler

There is a single **DocumentProviderEFRFiscalCZE** request handler for document provider, which is used to generate fiscal documents for the fiscal registration service.

This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests.

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, customer account deposits and customer order deposits.
- **GetFiscalRegisterResponseToSaveDocumentProviderRequest** – This request returns the response from the fiscal registration service. This response is serialized to form a string so that it's ready to be saved.

#### Configuration

The configuration file for the fiscal document provider is located at **src\\FiscalIntegration\\Efr\\Configurations\\DocumentProviders\\DocumentProviderFiscalEFRSampleCzech.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service. The Hardware station extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **EFRHandler** request handler is the entry point for handling requests to the fiscal registration service.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests.

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file for the fiscal connector is located at **src\\FiscalIntegration\\Efr\\Configurations\\Connectors\\ConnectorEFRSample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### POS fiscal connector extension design

The purpose of the POS fiscal connector extension is to communicate with the fiscal registration service from POS. It uses the HTTPS protocol for communication.

#### Fiscal connector factory

The fiscal connector factory maps the connector name to the fiscal connector implementation and is located in the **Pos.Extension\\Connectors\\FiscalConnectorFactory.ts** file. The connector name should match the fiscal connector name that is specified in Commerce headquarters.

#### EFR fiscal connector

The EFR fiscal connector is located in the **Pos.Extension\\Connectors\\Efr\\EfrFiscalConnector.ts** file. It implements the **IFiscalConnector** interface that supports the following requests:

- **FiscalRegisterSubmitDocumentClientRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **FiscalRegisterIsReadyClientRequest** – This request is used for a health check of the fiscal registration service.
- **FiscalRegisterInitializeClientRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is located in the **src\\FiscalIntegration\\Efr\\Configurations\\Connectors** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings for the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the connector will wait for a response from the fiscal registration service.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
