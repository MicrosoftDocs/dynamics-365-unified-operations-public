---
title: Deployment guidelines for the fiscal printer integration sample for Poland (legacy)
description: This article provides guidelines for deploying the fiscal printer integration sample for Poland from the Microsoft Dynamics 365 Commerce Retail software development kit (SDK).
author: EvgenyPopovMBS
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-03-01
ms.custom: 
  - bap-template
---
# Deployment guidelines for the fiscal printer integration sample for Poland (legacy)

[!include [banner](../../../finance/includes/banner.md)]

> [!IMPORTANT]
> Follow the guidelines in this article only if you're using Microsoft Dynamics 365 Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, the fiscal printer integration sample for Poland is available in the Commerce software development kit (SDK). For more information, see [Configure channel components](emea-pol-fpi-sample.md#configure-channel-components).

This article provides guidelines for deploying the fiscal printer integration sample for Poland from the Dynamics 365 Commerce Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information about this fiscal integration sample, see [Fiscal printer integration sample for Poland](emea-pol-fpi-sample.md). 

The fiscal integration sample for Poland is part of the Retail SDK. For information about how to install and use the SDK, see [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md). This sample consists of extensions for the Commerce runtime (CRT) and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. Use an unmodified Retail SDK to make the changes that are described in this article. Also, use a source control system such as Azure DevOps where no files are changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### Commerce runtime extension components

The Retail SDK includes the CRT extension components. To complete the following procedures, open the **CommerceRuntimeSamples.sln** solution under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.PosnetSample** project, and build it.
1. In the **Extensions.DocumentProvider.PosnetSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample.dll** assembly file.
1. Copy the assembly file to the CRT extension folder:

    - **Commerce Scale Unit:** Copy the file to the **\\bin\\ext** folder under the Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the file to the **\\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**. It's under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample" />
    ```

1. Restart the Commerce service:

    - **Commerce Scale Unit:** Restart the Commerce service site from IIS Manager.
    - **Client broker:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

### Hardware station extension components

The Retail SDK includes the Hardware station extension components. To complete the following procedures, open the **HardwareStationSamples.sln** solution under **RetailSdk\\SampleExtensions\\HardwareStation**.

1. Find the **HardwareStation.Extension.PosnetThermalFVFiscalPrinterSample** project, and build it.
1. In the **Extension.Posnet.ThermalFVFiscalPrinterSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.dll** assembly file.
1. Copy the assembly file to a deployed Hardware station machine:

    - **Remote Hardware station:** Copy the file to the **bin** folder under the IIS Hardware station site location. Also, copy the printer driver libraries (**libposcmbth.dll**, **libcmbth\_serial.dll**, and **cmbth\_pl.lng**).

1. Find the configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.

1. Add the following line to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample" />
    ```

1. Restart the Hardware station service:

	- **Remote Hardware station:** Restart the Hardware station site from IIS Manager.

## Production environment

In the previous procedure, you enabled the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample" />
        ```

1. Make the following changes in the **Customization.settings** package customization configuration file under the **BuildTools** folder:

    - Add the following line to include the CRT extension in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample.dll"/>
        ```

    - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.dll"/>
        ```

1. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
1. Apply the packages via LCS or manually. For more information, see [Create deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of extensions

The fiscal printer integration sample for Poland is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). For more information about the design of the fiscal integration solution, see the [overview of a fiscal integration sample design](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services).

### Commerce runtime extension design

The fiscal document provider extension generates printer-specific documents and handles responses from the fiscal printer.

The CRT extension is **Runtime.Extensions.DocumentProvider.PosnetSample**. This extension generates a set of printer-specific commands in JavaScript Object Notation (JSON) format that the POSNET specification 19-3678 defines.

For more information about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices and services](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services).

#### Request handler

The **DocumentProviderPosnetProtocol** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler inherits from the **INamedRequestHandler** interface. The **HandlerName** method returns the name of the handler. The handler name should match the connector document provider name that you specify in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document to generate. It returns a printer-specific document that the fiscal printer registers.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

You can find the configuration file in the **Configuration** folder of the extension project. The file enables you to configure settings for the document provider from Commerce headquarters. The file format aligns with the requirements for fiscal integration configuration. Add the following settings:

- VAT rates mapping
- Tender type mapping
- Deposit payment type

### Hardware station extension design

The fiscal connector extension communicates with the fiscal printer.

The Hardware station extension is **HardwareStation.Extension.PosnetThermalFVFiscalPrinterSample**. This extension calls the functions of the POSNET driver to submit commands that the CRT extension generates to the fiscal printer. It also handles device errors.

#### Request handler

The **FiscalPrinterHandler** request handler is the entry point for handling the request to the fiscal peripheral device.

The handler inherits from the **INamedRequestHandler** interface. The **HandlerName** method returns the name of the handler. The handler name matches the fiscal connector name that you specify in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration. Add the following settings:

- **Connection string** – A string that describes the details of the connection to the device in a format that the driver supports. For more information, see the POSNET driver documentation.
- **Date and time synchronization** – A value that specifies whether the date and time of the printer must sync with the connected Hardware station.
- **Device timeout** – The amount of time, in milliseconds, that the driver waits for a response from the device. For more information, see the POSNET driver documentation.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]