---
# required metadata

title: Sample for Retail POS integration with control units for Sweden
description: This topic is the building and installation guide for the sample for control unit integration for Sweden. 
author: EvgenyPopovMBS
manager: Annbe
ms.date: 02/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Sweden
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2018-2-28
ms.dyn365.ops.version: 7.3.2

---
# Sample for Retail POS integration with control units for Sweden

[!include [banner](../includes/banner.md)]

**SAMPLE CODE NOTICE**

**THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED, OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.  THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.**

**NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.**

This sample shows how to create Microsoft Dynamics 365 for Retail extensions to integrate Retail Modern POS or Cloud POS with a fiscal register. Specifically, this sample includes the code for integrating Microsoft Dynamics for Retail POS with control units for Sweden. As an example, this sample uses the application programming interface (API) of the CleanCash® Type A control unit by Retail Innovation HTT AB. Version 1.1.4 of the CleanCash® API is used. For the integration package that includes the API and documentation, contact the manufacturer of the device.

This sample is a part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Hardware station, commerce runtime (CRT), and point of sale (POS). To run this sample, you must modify and build the Hardware station, CRT, and POS projects. We recommend that use you an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE]
> Some steps in the procedures in this topic differ, depending on the version of Microsoft Dynamics 365 for Retail that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

1. Extend the Hardware station component:

    1. Open the Hardware station solution under **RetailSDK\\SampleExtensions\\HardwareStation**.
    2. Find the **HardwareStation.Extension.FiscalRegisterSample.csproj** extension project, and compile it.
    3. Find extension assemblies and configurations.

        # [Retail 7.3 and earlier](#tab/retail-7-3)

        Find the following files in **Extension.FiscalRegisterSample\\bin\\Debug**:

        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll** assembly
        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll.config** configuration
        - The **Interop.CleanCash\_1\_1.dll** assembly

        # [Retail 7.3.1 and later](#tab/retail-7-3-1)

        Find the following files in **Extension.FiscalRegisterSample\\bin\\Debug**:

        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll** assembly
        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll.config** configuration
        - The **Interop.CleanCash\_1\_1.dll** assembly

        # [Retail 10.0 and later](#tab/retail-10-0)

        Find the following files in **Extension.FiscalRegisterSample\\bin\\Debug**:

        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll** assembly
        - The **Contoso.Commerce.HardwareStation.FiscalRegisterSample.dll.config** configuration

        Find the following file in **RetailSDK\\References\\Microsoft.Dynamics.Commerce.CleanCashInterop.1.0.1\\lib\\net451**:

        - The **Interop.CleanCash\_1\_1.dll** assembly

        ---

    4. Copy the files to a deployed Hardware station machine:

        - **Remote Hardware station:** Copy the files to the **bin** folder under the Microsoft Internet Information Services (IIS) Hardware station site location.
        - **Local Hardware station:** Copy the files to the Modern POS client broker location.

    5. Find the configuration file for Hardware station's extensions.

        # [Retail 7.3 and earlier](#tab/retail-7-3)

        - **Remote Hardware station:** The file is named **hardwarestation.shared.config**, and it's under the IIS Hardware station site location.
        - **Local Hardware station:** The file is named **HardwareStation.Dedicated.config**, and it's under the Modern POS client broker location.

        # [Retail 7.3.1 and later](#tab/retail-7-3-1)

        The file is named **HardwareStation.Extension.config**:

        - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
        - **Local Hardware station:** The file is located under the Modern POS client broker location.

        # [Retail 10.0 and later](#tab/retail-10-0)

        The file is named **HardwareStation.Extension.config**:

        - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
        - **Local Hardware station:** The file is located under the Modern POS client broker location.

        ---

    6. Add the following section to the **composition** section of the config file.

        # [Retail 7.3 and earlier](#tab/retail-7-3)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```

        # [Retail 7.3.1 and later](#tab/retail-7-3-1)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```

        # [Retail 10.0 and later](#tab/retail-10-0)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.FiscalRegisterSample" />
        ```

        ---

    7. Restart the Hardware station service:

        - **Remote Hardware station:** Restart the Hardware station site from IIS Manager.
        - **Local Hardware station:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

2. Extend the CRT component:

    1. Open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.
    2. Find the **Runtime.Extensions.FiscalRegisterReceiptSample** project, and build it.
    3. Find the ext.config file for CRT:

        - **Retail Server:** The file is named **commerceRuntime.ext.config**, and it's under the **bin\\ext** folder under the IIS Retail server site location.
        - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the **bin\\ext** folder under the local CRT client broker location.

    4. Register the CRT change in the configuration file.

        ``` xml
        <add source="type" value="Contoso.Commerce.Runtime.FiscalRegisterReceipt, Contoso.Commerce.Runtime.FiscalRegisterReceipt" />
        ```

        > [!NOTE]
        > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

    5. Find the **Contoso.Commerce.Runtime.FiscalRegisterReceiptSample.dll** assembly file in **Extensions.FiscalRegisterReceiptSample\\bin\\Debug**.
    6. Copy the assembly to the CRT extensions folder:

        - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail server site location.
        - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

        > [!NOTE]
        > All the code changes for CRT and Retail Server are all part of RetailSdk\\SampleExtensions. Therefore, the preceding steps show how to build, deploy, and test these code changes.

3. Extend the Modern POS component:

    1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Also make sure that Modern POS can be run from Microsoft Visual Studio using the **Run** command. (Modern POS must not be customized. You must enable User Account Control \[UAC\], and you must uninstall previously installed instances of Modern POS as required.)
    2. Include **FiscalRegisterSample** in the **Pos.Extensions** project.
    3. Enable the extension to be compiled in **tsconfig.json** by removing the **FiscalRegisterSample** folder from the exclude list.
    4. Enable the extension in **Extensions\\extensions.json** by adding the following lines in the appropriate place.

        ``` json
        {
            "debugBuildsOnly": false,
            "baseUrl": "FiscalRegisterSample"
        }
        ```

    5. Rebuild the solutions.
    6. Run Modern POS in the debugger, and test the functionality.

4. Extend the Cloud POS component:

    1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
    2. Include **FiscalRegisterSample** in the **Pos.Extensions** project.
    3. Enable the extension to be compiled in **tsconfig.json** by removing the **FiscalRegisterSample** folder from the exclude list.
    4. Enable the extension in **Extensions\\extensions.json** by adding the following lines in the appropriate place.

        ``` json
        {
            "debugBuildsOnly": false,
            "baseUrl": "FiscalRegisterSample"
        }
        ```

    5. Rebuild the solutions.
    6. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.
    7. Test the functionality.

5. Set up the fiscal register configuration and other required parameters in Retail headquarters. For more information, see [Cash registers for Sweden](emea-swe-cash-registers.md).

## Production environment

Follow these steps to create and apply deployable packages that contain Retail components in a production environment.

1. Extend the POS component

    1. Enable the extension to be compiled in **tsconfig.json** by removing the **FiscalRegisterSample** folder from the exclude list.
    2. Enable the extension in **Extensions\\extensions.json** by adding the following lines in the appropriate place.

        ``` json
        {
            "baseUrl": "FiscalRegisterSample"
        }
        ```

2. Make the following changes in the package config files under the **RetailSdk\\Assets** folder:

    1. Add the following section to the **composition** section of the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** config files.

        ``` xml
        <add source="type" value="Contoso.Commerce.Runtime.FiscalRegisterReceipt, Contoso.Commerce.Runtime.FiscalRegisterReceipt" />
        ```

    2. Add the following section to the **composition** section of the Hardware station configuration file.

        # [Retail 7.3 and earlier](#tab/retail-7-3)

        Modify the **HardwareStation.Shared.config** and **HardwareStation.Dedicated.config** configuration files.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```

        # [Retail 7.3.1 and later](#tab/retail-7-3-1)

        Modify the **HardwareStation.Extension.config** configuration file:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```
        
        # [Retail 10.0 and later](#tab/retail-10-0)

        Modify the **HardwareStation.Extension.config** configuration file:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.FiscalRegisterSample" />
        ```

        ---

3. Run **msbuild** for the whole Retail SDK to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
