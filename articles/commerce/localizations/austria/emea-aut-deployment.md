---
title: Deployment guidelines for cash registers for Austria
description: This article is a deployment guide for the Commerce localization for Austria.
author: josaw1
ms.date: 08/09/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Austria
ms.author: anupamar
ms.search.validFrom: 10/20/2019
ms.custom: 
  - bap-template
---
# Deployment guidelines for cash registers for Austria

[!include[banner](../../../finance/includes/banner.md)]

This article is a deployment guide that shows how to enable the Dynamics 365 Commerce localization for Austria. The localization consists of several extensions of Commerce components. For example, the extensions let you print custom fields on receipts, register additional audit events, includes samples of the integration with the EFSTA System and
Electronical Fiscal Register Software. For more information about the localization for Austria, see [Fiscal registration service integration sample for Austria](../dev-itpro/emea-aut-fi-sample.md).

Integration samples were developed based on the fiscal integration framework. For details about the fiscal integration functionality, see [Overview of fiscal integration for Commerce channels](../dev-itpro/fiscal-integration-for-retail-channel.md), these samples are part of the Retail software development kit (SDK). For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md).

This localization consists of extensions for the Commerce runtime (CRT), Hardware station, and POS. To run this sample, you must modify and build the CRT, Hardware station, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this article. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### CRT extension components

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

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail and Commerce:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail and Commerce site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
    ```

#### Enable Microsoft components

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
    ```

### Hardware station extension components

The Hardware station extension components are included in the Hardware station samples. To complete the following procedures, open the solution, **HardwareStationSamples.sln.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

#### EFRSample component

1. Find the **HardwareStation.Extension.EFRSample** project, and build it.
2. In the **Extension.EFRSample\\bin\\Debug** folder, find following files:

    - The **Contoso.Commerce.HardwareStation.EFRSample.dll** assembly
    - The **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly

3. Copy the assembly file to the Hardware station extensions folder:

    - **Shared hardware station:** Copy the files to the **bin** folder under the Microsoft Internet Information Services (IIS) Hardware station site location.
    - **Dedicated hardware station on Modern POS:** Copy the files to the Modern POS client broker location.

4. Find the extension configuration file Hardware station's extensions **HardwareStation.Extension.config**:

    - **Shared hardware station:** The file is located under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** The file is located under the Modern POS client broker location.

5. Add the following section to the **composition** section of the config file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample.dll" />
    ```

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

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

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

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

### Set up required parameters in Headquarters

#### Set up the registration process

To enable the registration process, set up Headquarters using the steps below. For more details, see [Set up the fiscal integration for Commerce channels](../dev-itpro/setting-up-fiscal-integration-for-retail-channel.md).

1. Open **Commerce shared parameters** and enable **Fiscal integration** on the **General** tab.
2. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors** menu. Load connector configuration from RetailSdk. The file is located under SampleExtensions\HardwareStation\Extension.EFRSample\Configuration\ConnectorEFRSampleAustria.xml.
3. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers** menu. Load documment provider configurations from RetailSdk.

    Configuration files are located under **SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration**:

    - DocumentProviderEFRSampleAustria.xml
    - DocumentProviderNonFiscalEFRSampleAustria.xml

4. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create two new profiles per document provider from step above and select the loaded connector. Update data mapping settings if needed.
5. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new profile and select the loaded connector from the step above. Update connection settings if needed.
6. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector group**. Create two new group per connector's functional profile from the step above.
7. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Registration process**. Create a new process. Select both connector's functional groups from the step above.
8. Open **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select one that is linked to the store where the registration process should be activated. Expand the **Fiscal registration process** tab. Select the created registration process from the step above. For enabling registration of non-fiscal events on POS enable **Audit** property at **Functions** fasttab.
9. Open the **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select one that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** Tab. Select the connector technical profile.

For more information, see [Fiscal registration service integration sample for Austria](../dev-itpro/emea-aut-fi-sample.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the [Cloud POS extension components](#cloud-pos-extension-components) or [Modern POS extension components](#modern-pos-extension-components) section earlier in this article.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

        ```xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
        ```

    2. In the **HardwareStation.Extension.config** configuration file, add the following lines to the **composition** section.

        ```xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample" />
        ```

3. Make the following changes in the **BuildTools\Customization.settings** package customization configuration file:

    ```xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
    <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
    <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.EFRSample" />
    ```

4. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).
6. Complete the [Set up required parameters in Headquarters](#set-up-required-parameters-in-headquarters)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
