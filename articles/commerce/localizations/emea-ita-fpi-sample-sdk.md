---
# required metadata

title: Deployment guidelines for the fiscal printer integration sample for Italy (legacy)
description: This topic provides guidelines for deploying the fiscal printer integration sample for Italy from the Microsoft Dynamics 365 Commerce Retail software development kit (SDK).
author: EvgenyPopovMBS
ms.date: 03/04/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2019-3-1

---
# Deployment guidelines for the fiscal printer integration sample for Italy (legacy)

[!include[banner](../includes/banner.md)]

This topic provides guidelines for deploying the fiscal printer integration sample for Italy from the Microsoft Dynamics 365 Commerce Retail software development kit (SDK) on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information about this fiscal integration sample, see [Fiscal printer integration sample for Italy](emea-ita-fpi-sample.md). 

The fiscal integration sample for Italy is part of the Retail SDK. For information about how to install and use the SDK, see [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md). This sample consists of extensions for the Commerce runtime (CRT) and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system such as Azure DevOps where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### Commerce runtime extension components

The CRT extension components are included in the Retail SDK. To complete the following procedures, open the **CommerceRuntimeSamples.sln** solution under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample** project, and build it.
2. In the **Extensions.DocumentProvider.EpsonFP90IIISample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the file to the **\\bin\\ext** folder under the Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the file to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample" />
    ```

6. Restart the Commerce Scale Unit:

    - **Commerce Scale Unit:** Restart the Commerce Scale Unit site from IIS Manager.
    - **Client broker:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

### Hardware station extension components

The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the **HardwareStationSamples.sln** solution under **RetailSdk\\SampleExtensions\\HardwareStation**.

1. Find the **HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample** project, and build it.
2. In the **Extensions.EpsonFP90IIIFiscalDeviceSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll** assembly file.
3. Copy the assembly file to a deployed Hardware station machine:

    - **Remote Hardware station:** Copy the file to the **bin** folder under the IIS Hardware station site location.
    - **Local Hardware station:** Copy the file to the Modern POS client broker location.

4. Find the configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
    - **Local Hardware station:** The file is located under the Modern POS client broker location.

5. Add the following section to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample" />
    ```

6. Restart the Hardware station service:

    - **Remote Hardware station:** Restart the Hardware station site from IIS Manager.
    - **Local Hardware station:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

## Production environment

To create deployable packages that contain Commerce components, and apply those packages in a production environment, follow these steps.

1. Complete the steps that are described in the [Development environment](#development-environment) section earlier in this topic.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample" />
        ```

    1. In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample" />
        ```

3. Make the following changes in the **Customization.settings** package customization configuration file under the **BuildTools** folder:

    1. Add the following line to include the CRT extension in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll"/>
        ```

    1. Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll"/>
        ```

4. Make the following changes in the **Sdk.ModernPos.Shared.csproj** file under the **Packages\_SharedPackagingProjectComponents** folder to include the resource files for Italy in deployable packages:

    1. Add an **ItemGroup** section that contains nodes that point to the resource files for the desired translations. Ensure that you specify the correct namespaces and sample names. The following example adds resource nodes for the **it** and **it-CH** locales.

        ```xml
        <ItemGroup>
            <ResourcesIt Include="$(SdkReferencesPath)\it\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.resources.dll"/>
            <ResourcesItCh Include="$(SdkReferencesPath)\it-CH\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.resources.dll"/>
        </ItemGroup>
        ```

    1. In the **Target Name="CopyPackageFiles"** section, add one line for each locale, as shown in the following example.

        ```xml
        <Copy SourceFiles="@(ResourcesIt)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\it" SkipUnchangedFiles="true" />
        <Copy SourceFiles="@(ResourcesItCh)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\it-CH" SkipUnchangedFiles="true" />
        ```

5. Make the following changes in the **Sdk.RetailServerSetup.proj** file under the **Packages\_SharedPackagingProjectComponents** folder to include the resource files for Italy in deployable packages:

    1. Add an **ItemGroup** section that contains nodes that point to the resource files for the desired translations. Ensure that you specify the correct namespaces and sample names. The following example adds resource nodes for the **it** and **it-CH** locales.

        ```xml
        <ItemGroup>
            <ResourcesIt Include="$(SdkReferencesPath)\it\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.resources.dll"/>
            <ResourcesItCh Include="$(SdkReferencesPath)\it-CH\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.resources.dll"/>
        </ItemGroup>
        ```

    1. In the **Target Name="CopyPackageFiles"** section, add one line for each locale, as shown in the following example.

        ``` xml
        <Copy SourceFiles="@(ResourcesIt)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\it" SkipUnchangedFiles="true" />
        <Copy SourceFiles="@(ResourcesItCh)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\it-CH" SkipUnchangedFiles="true" />
        ```

6. Start the MSBuild Command Prompt for Visual Studio utility, and then run **msbuild** under the Retail SDK folder to create deployable packages.
7. Apply the packages via LCS or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer.

The CRT extension is **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample**.

For more information about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices and services](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services).

#### Request handler

The **DocumentProviderEpsonFP90III** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- VAT codes mapping
- VAT rates mapping
- Tender type mapping
- Barcode type for receipt number
- Deposit payment type

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal printer.

The Hardware station extension is **HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample**. This extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal printer. It also handles the responses that are received from the fiscal printer.

#### Request handler

The **EpsonFP90IIISample** request handler is the entry point for handling requests to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Endpoint address** – The URL of the printer.
- **Date and time synchronization** – A value that specifies whether the date and time of the printer must be synced with the connected Hardware station.
