---

# required metadata

title: Deployment guidelines for the fiscal printer integration sample for Poland (legacy)
description: This topic provides guidelines on how to deploy the fiscal printer integration sample for Poland from the Retail SDK
author: EvgenyPopovMBS
ms.date: 11/17/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Poland
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---
# Deployment guidelines for the fiscal printer integration sample for Poland (legacy)

This topic provides guidelines on how to deploy the fiscal printer integration sample for Poland from the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information about this fiscal integration sample, see [Fiscal printer integration sample for Poland](emea-pol-fpi-sample.md). The fiscal integration sample for Poland is part of the Retail SDK. For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md). This sample consists of extensions for the CRT and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### Enable extensions

#### Commerce runtime extension components

The Commerce runtime (CRT) extension components are included in the Retail SDK. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.PosnetSample** project, and build it.
2. In the **Extensions.DocumentProvider.PosnetSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample.dll** assembly file.
3. Copy the assembly file to the CRT extension folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the bin\\ext folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension's configuration file. Add **source="assembly" value="Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample"**.
6. Restart the Commerce service.

    - **Commerce Scale Unit:** Restart the Commerce service site from IIS Manager.
    - **Client broker:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

#### Hardware station extension components

The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the Hardware Station solution, **HardwareStationSamples.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

1. Find the **HardwareStation.Extension.PosnetThermalFVFiscalPrinterSample** project, and build it.
2. In the **Extension.Posnet.ThermalFVFiscalPrinterSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.dll** assembly file.
3. Copy the files to a deployed Hardware station machine:

    - **Remote Hardware station:** Copy the files to the **bin** folder under the IIS Hardware station site location. Copy the printer driver libraries (**libposcmbth.dll**, **libcmbth\_serial.dll**, and **cmbth\_pl.lng**).

4. Find the configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.

5. Add the following section to the **composition** section of the config file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample" />
    ```

6. Restart the Hardware station service:

	- **Remote Hardware station:** Restart the Hardware station site from IIS Manager.

### Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps that are described in the [Enable extensions](#enable-extensions) section earlier in this topic.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample" />
        ```

3. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file:

    - Add the following line to include the CRT extension in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample.dll"/>
        ```

    - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.dll"/>
        ```

4. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer.

The Commerce runtime extension is **Runtime.Extensions.DocumentProvider.PosnetSample**. This extension generates a set of printer-specific commands in JavaScript Object Notation (JSON) format that are defined by POSNET specification 19-3678.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler

The **DocumentProviderPosnetProtocol** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

The configuration file is found in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- VAT rates mapping
- Tender type mapping
- Deposit payment type

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal printer.

The Hardware station extension is **HardwareStation.Extension.PosnetThermalFVFiscalPrinterSample**. This extension calls the functions of the POSNET driver to submit commands that the Commerce runtime extension generates to the fiscal printer. It also handles device errors.

#### Request handler

The **FiscalPrinterHandler** request handler is the entry point for handling the request to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Connection string** – This string describes the details of the connection to the device in a format that is supported by the driver. For details, see the POSNET driver documentation.
- **Date and time synchronization** – This setting specifies whether the date and time of the printer must be synced with the connected Hardware station.
- **Device timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the device. For details, see the POSNET driver documentation.

