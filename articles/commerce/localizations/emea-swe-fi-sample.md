---
# required metadata

title: Control unit integration sample for Sweden
description: This topic provides an overview of the fiscal integration sample for Sweden in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 12/20/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2019-10-08

---
# Control unit integration sample for Sweden

[!include [banner](../includes/banner.md)]

This topic provides an overview of the fiscal integration sample for Sweden in Microsoft Dynamics 365 Commerce.

> [!NOTE]
> This sample fiscal integration functionality replaces the earlier [sample for POS integration with control units for Sweden](retail-sdk-control-unit-sample.md). The earlier sample doesn't take advantage of the [fiscal integration framework](./fiscal-integration-for-retail-channel.md) and will become obsolete in later updates. For information about how to migrate from the earlier sample to the sample that corresponds to Dynamics 365 Commerce version **10.0.22 and earlier**, see [Migrating from the earlier integration sample](emea-swe-fi-sample-sdk.md#migrating-from-the-earlier-integration-sample).

The Commerce functionality for Sweden includes a sample integration of the point of sale (POS) with Sweden-specific fiscal devices that are known as *control units*. This sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's assumed that a control unit is physically connected to a Hardware station that the POS is paired with. As an example, this sample uses the application programming interface (API) of the [CleanCash Type A](https://www.retailinnovation.se/produkter) control unit by Retail Innovation HTT AB. Version 1.1.4 of the CleanCash API is used.

The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Retail Innovation HTT AB. For information about how to get the control unit and operate it, contact [Retail Innovation HTT AB](https://www.retailinnovation.se/).

## Scenarios

The control unit integration sample for Sweden includes the following capabilities:

- Sales, returns, and receipt copies are automatically registered in a control unit that is connected to the Hardware station that is paired with the POS.
- The control code and the manufacturing number of the control unit for a registered transaction are captured from the control unit and saved in the transaction. This data is also referred to as a *fiscal response*. The fiscal response can be viewed on the **Store transactions** page.
- Custom fields for the control code and the manufacturing number of the control unit can be added to a receipt layout. In that way, you can print the fiscal response for a transaction on a receipt.
- The fiscal response for a transaction is shown on the **Electronic journal (Sweden)** channel report.
- Several error handling options are available. Here are some examples:

    - Retry fiscal registration, if a retry is possible. You can retry fiscal registration if, for example, the control unit isn't connected, isn't ready, or isn't responding.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Verify the availability of the control unit before a new sales transaction is opened or a sales transaction is finalized.

### Limitations of the sample

The control unit integration sample for Sweden doesn't currently support customer order scenarios.

## Setting up the integration with control units

For more information about the setup that is required for Sweden, see [Setting up Commerce for Sweden](./emea-swe-cash-registers.md#setting-up-commerce-for-sweden).

### Configuring Sweden–specific receipts

#### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or greater than 900001.

Add the following POS labels in the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                  |
|-------------|---------|-----------------------|
| en-US       | 900001  | Register control code |
| en-US       | 900002  | Register device       |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                         | Type    | Caption text ID |
|------------------------------|---------|-----------------|
| SE_FISCALREGISTERCONTROLCODE | Receipt | 900001          |
| SE_FISCALREGISTERID          | Receipt | 900002          |

> [!NOTE]
> It's important that you specify correct custom field names, as listed in the above table. An incorrect custom field name will cause missing data in receipts.

#### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the **Footer** section. Note that field names correspond to the language texts that you defined in the previous section of this topic.

- **Register control code** – This field prints the control code.
- **Register device** – This field prints the manufacturing number of the control unit.

For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Set up fiscal integration for Sweden

The control unit integration sample for Sweden is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\CleanCash** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/CleanCash)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of the Commerce runtime (CRT), and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for the control unit integration sample for Sweden (legacy)](emea-swe-fi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Also, make a note of the settings for the fiscal registration process that are [specific to this control unit integration sample](#set-up-the-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce headquarters. For more information, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Select a correct release branch version according to your SDK/application version (for example, **[release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33)**).
    1. Open **src \> FiscalIntegration \> CleanCash**.
    1. Download the fiscal document provider configuration file at **CommerceRuntime \> DocumentProvider.CleanCashSample \> Configuration \> DocumentProviderFiscalCleanCashSample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/CleanCash/CommerceRuntime/DocumentProvider.CleanCashSample/Configuration/DocumentProviderFiscalCleanCashSample.xml)).
    1. Download the fiscal connector configuration file at **HardwareStation \> Connector.CleanCashSample \> Configuration \> ConnectorCleanCashSample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/CleanCash/HardwareStation/Connector.CleanCashSample/Configuration/ConnectorCleanCashSample.xml)).

    > [!WARNING]
    > Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. The configuration files for this fiscal integration sample are located in the following folders of the Retail SDK on a developer VM in LCS:
    >
    > - **Fiscal document provider configuration file:** RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.CleanCashSample\\Configuration\\DocumentProviderFiscalCleanCashSample.xml
    > - **Fiscal connector configuration file:** RetailSdk\\SampleExtensions\\HardwareStation\\Extension.CleanCashSample\\Configuration\\ConnectorCleanCashSample.xml
    > 
    > Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the [data mapping settings](#default-data-mapping) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the fiscal connector that you loaded earlier. Update the [connector settings](#fiscal-connector-settings) as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process and a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- **Value-added tax (VAT) code mapping** – This mapping sets device-specific value-added tax (VAT) codes to corresponding sales tax codes. The VAT code mapping should have the following format:

    ```
    1 : code1 ; 2 : code2
    ```

    Here is an explanation of this format:

    - *1* and *2* are device-specific VAT codes.
    - A semicolon (;) is used as a separator.
    - *code1* and *code2* are sales tax codes that are configured in Commerce headquarters. You must modify the sample mapping according to the tax codes that are configured in your application.

    Control units support up to four different VAT codes. Therefore, the VAT code mapping might be set up in the following way:

    ```
    1 : code1 ; 2 : code2 ; 3 : code3 ; 4 : code4
    ```

    > [!NOTE]
    > Multiple sales tax codes can be mapped to the same device-specific VAT code.

#### Fiscal connector settings

The following settings are included in the fiscal connector configuration that is provided as part of the fiscal integration sample:

- **Connections string** – The control unit connection settings.
- **Timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the control unit.

### Configure channel components

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the control unit integration sample for Sweden (legacy)](emea-swe-fi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

#### Set up the development environment

To set up a development environment to test and extend the sample, follow these steps.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
1. Open the control unit integration solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\CleanCash\\CleanCash.sln**, and build it.
1. Install CRT extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **CleanCash\\ScaleUnit\\ScaleUnit.CleanCash.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.CleanCash.Installer** installer.
        - **Local CRT on Modern POS:** In the **CleanCash\\ModernPOS\\ModernPOS.CleanCash.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.CleanCash.Installer** installer.

    2. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.CleanCash.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.CleanCash.Installer.exe install --verbosity 0
            ```

1. Install Hardware station extensions:

    1. In the **CleanCash\\HardwareStation\\HardwareStation.CleanCash.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.CleanCash.Installer** installer.
    1. Start the extension installer from the command line:

        ```Console
        HardwareStation.CleanCash.Installer.exe install --verbosity 0
        ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **CleanCash build-pipeline.yml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

## Design of the extensions

The control unit integration sample for Sweden is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\CleanCash** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/CleanCash)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of CRT, and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the control unit integration sample for Sweden (legacy)](emea-swe-fi-sample-sdk.md). Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

### CRT extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the control unit.

#### Request handler

There is a single **DocumentProviderCleanCash** request handler for the document provider. This handler is used to generate fiscal documents for the control unit.

This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the control unit.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, sales events and audit events are supported.

#### Configuration

The configuration file for the fiscal document provider is located at **src\\FiscalIntegration\\CleanCash\\CommerceRuntime\\DocumentProvider.CleanCashSample\\Configuration\\DocumentProviderFiscalCleanCashSample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of this file is to enable settings for the document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the control unit. It uses the HTTP protocol to submit documents that the CRT extension generates to the control unit. It also handles the responses that are received from the control unit.

#### Request handler

The **CleanCashHandler** request handler is the entry point for handling requests to the control unit.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the control unit and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the control unit.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the control unit.

#### Configuration

The configuration file for the fiscal connector is located at **src\\FiscalIntegration\\CleanCash\\HardwareStation\\Connector.CleanCashSample\\Configuration\\ConnectorCleanCashSample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings for the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
