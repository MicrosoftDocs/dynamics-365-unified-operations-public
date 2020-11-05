---
# required metadata

title: Deployment guidelines for cash registers for India
description: This topic is a deployment guide for the Commerce localization for India.
author: AlexChern0v
manager: annbe
ms.date: 09/16/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

# ms.search.form:
audience: Developer
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: India
ms.search.industry: Retail
ms.author: jiaqia
ms.search.scope: Retail
ms.search.validFrom: 2018-1-31
ms.dyn365.ops.version: 7.3.1

---
# Deployment guidelines for cash registers for India

[!include [banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the requirements for Goods and Services Tax (GST) in the Dynamics 365 Commerce app's localization for India. For more information about the localization for India, see [Goods and Services Tax (GST) integration for cash registers for India](./apac-ind-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT). To run this sample, you must modify and build the CRT projects. We recommend that use you an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE]
> Some steps in the procedures in this topic differ, depending on the version of the app that you're using. For more information, see [What's new or changed in Dynamics 365 Retail](../get-started/whats-new.md).

## Prerequisites

Make sure that the Visual C++ Redistributable Packages are present on the machine that you're running Goods and Services Tax (GST) calculations on. For Cloud POS, and for Modern POS in online mode, this machine is Retail Server (Retail Server is known as Commerce Scale Unit in Commerce 10.0.8 and above). For Modern POS in offline mode, it's the Modern POS machine itself. To get the packages, see [Download the Visual C++ Redistributable Packages](https://www.microsoft.com/download/details.aspx?id=48145).

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**. You can find this solution under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

# [Retail 7.3.1](#tab/retail-7-3-1)

1. Find the **Runtime.Extensions.GenericTaxEngine** project, and build it.
2. Find the following files:

    - In the **Extensions.GenericTaxEngine\\bin\\Debug** folder:

        - Contoso.Commerce.Runtime.Extensions.GenericTaxEngine.dll

    - In the **Reference\\Newtonsoft.Json\\9.0.0.0** folder:

        - Newtonsoft.Json.dll

    - In the **Reference\\TaxEngine** folder:

        - Microsoft.Dynamics365.Tax.Core.dll
        - Microsoft.Dynamics365.Tax.DataAccessor.dll
        - Microsoft.Dynamics365.Tax.DataAccessFramework.dll
        - Microsoft.Dynamics365.Tax.DataModel.dll
        - Microsoft.Dynamics365.Tax.Metadata.dll
        - Microsoft.Dynamics365.LocalizationFramework.dll
        - Microsoft.Dynamics365.LocalizationFrameworkCore.dll
        - Microsoft.Dynamics365.ElectronicReportingMapping.dll
        - Microsoft.Dynamics365.XppSupportLayer.dll

    - Find the following folders in the **Reference\\Z3** folder:

        - x86
        - x64

3. Copy the 11 assembly files, and both x64 and x86 folders to the CRT extensions folder:

    - **Retail Server:** Copy the assemblies to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Copy the assemblies to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

1. Find the **Runtime.Extensions.GenericTaxEngine** project, and build it.
2. Find the following files:

    - In the **Extensions.GenericTaxEngine\\bin\\Debug** folder:

        - Contoso.Commerce.Runtime.GenericTaxEngine.dll

    - In the **References\\Newtonsoft.Json.9.0.1\\lib\\net45** folder:

        - Newtonsoft.Json.dll

    - In the **References\\Microsoft.Dynamics.AX.TaxEngine.7.3.42\\XppModule\\TaxEngine\\bin** folder:

        - Microsoft.Dynamics365.LocalizationFramework.dll
        - Microsoft.Dynamics365.Tax.Core.dll
        - Microsoft.Dynamics365.Tax.DataAccessFramework.dll
        - Microsoft.Dynamics365.Tax.DataAccessor.dll
        - Microsoft.Dynamics365.Tax.DataModel.dll
        - Microsoft.Dynamics365.Tax.Metadata.dll

    - In the **References\\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\\XppModule\\ElectronicReporting\\bin** folder:

        - Microsoft.Dynamics365.ElectronicReportingMapping.dll
        - Microsoft.Dynamics365.LocalizationFrameworkCore.dll
        - Microsoft.Dynamics365.XppSupportLayer.dll

    - Find the following folders in the **References\\Z3.4.5.0\\lib\\net40** folder:

        - x86
        - x64

3. Copy the 11 assembly files, and both x64 and x86 folders to the CRT extensions folder:

    - **Retail Server:** Copy the assemblies to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Copy the assemblies to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 8.1.3 and later](#tab/retail-8-1-3)

1. Find the **Runtime.Extensions.GenericTaxEngine** project, and build it.
2. Find the following files:

    - In the **Extensions.GenericTaxEngine\\bin\\Debug** folder:

        - Contoso.Commerce.Runtime.GenericTaxEngine.dll

    - In the **References\\Newtonsoft.Json.9.0.1\\lib\\net45** folder:

        - Newtonsoft.Json.dll

    - In the **References\\Microsoft.Dynamics.AX.TaxEngine.8.0.26\\XppModule\\TaxEngine\\bin** folder:

        - Microsoft.Dynamics365.LocalizationFramework.dll
        - Microsoft.Dynamics365.Tax.Core.dll
        - Microsoft.Dynamics365.Tax.DataAccessFramework.dll
        - Microsoft.Dynamics365.Tax.DataAccessor.dll
        - Microsoft.Dynamics365.Tax.DataModel.dll
        - Microsoft.Dynamics365.Tax.Metadata.dll

    - In the **References\\Microsoft.Dynamics.AX.ElectronicReporting.8.0.26\\XppModule\\ElectronicReporting\\bin** folder:

        - Microsoft.Dynamics365.ElectronicReportingMapping.dll
        - Microsoft.Dynamics365.LocalizationFrameworkCore.dll
        - Microsoft.Dynamics365.XppSupportLayer.dll

    - Find the following folders in the **References\\Z3.4.5.0\\lib\\net40** folder:

        - x86
        - x64

3. Copy the 11 assembly files, and both x64 and x86 folders to the CRT extensions folder:

    - **Retail Server:** Copy the assemblies to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Copy the assemblies to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 10.0 and later](#tab/retail-10-0)

The Generic Tax Engine component is a part of sealed extensions.

1. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extensions configuration file:

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do *not* edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 10.0.6 and later](#tab/retail-10-0-6)

1. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extensions configuration file:

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown above.

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

---

### The extension components

1. Open **web.config** in the root folder under the IIS Retail Server site location. Note that Retail Server is known as Commerce Scale Unit in Commerce 10.0.8 and above.
2. Register the extensions in the **extensionComposition** section of the configuration file.

# [Retail 7.3.1](#tab/retail-7-3-1)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 8.1.3 and later](#tab/retail-8-1-3)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0 and later](#tab/retail-10-0)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0.6 and later](#tab/retail-10-0-6)

``` xml
<add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
```

---
### The ClientBroker extension components

1. Open **RetailProxy.MPOSOffline.ext.config** under the local CRT client broker location.
2. Register the Proxy extensions in the **extensionComposition** section of the configuration file.

# [Retail 7.3.1](#tab/retail-7-3-1)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 8.1.3 and later](#tab/retail-8-1-3)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0 and later](#tab/retail-10-0)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0.6 and later](#tab/retail-10-0-6)

``` xml
<add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
```

---

### The Modern POS extension components

Enable the Tax Registration Id extension.

# [Retail 7.3.1](#tab/retail-7-3-1)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 8.1.3 and later](#tab/retail-8-1-3)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0 and later](#tab/retail-10-0)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0.6 and later](#tab/retail-10-0-6)

1. Open the solution at **RetailSdk\POS\ModernPOS.sln**, and make sure that it can be compiled without errors. Also make sure that Modern POS can be run from Microsoft Visual Studio using the Run command. (Modern POS must not be customized. You must enable User Account Control [UAC], and uninstall previously installed instances of Modern POS.)

2. Enable the extension in **POS.Extensions\extensions.json** by adding the following lines:

    ``` xml
    {
      "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

3. Build the solution.
4. Run Modern POS and test the functionality.

---

### The Cloud POS extension components

Enable the Tax Registration Id extension.

# [Retail 7.3.1](#tab/retail-7-3-1)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 8.1.3 and later](#tab/retail-8-1-3)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0 and later](#tab/retail-10-0)

> [!NOTE]
> This step doesn't apply to this version.

# [Retail 10.0.6 and later](#tab/retail-10-0-6)

1. Open the solution at **RetailSdk\POS\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extension in **POS.Extensions\extensions.json** by adding the following lines:

    ``` xml
    {
      "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

3. Build the solution.
4. Run Cloud POS and test the functionality.

---

### Set up required parameters in Headquarters

For more information, see [Goods and Services Tax (GST) integration for cash registers for India](./apac-ind-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain components, and to apply the packages in a production environment.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.GenericTaxEngine" />
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

    # [Retail 10.0 and later](#tab/retail-10-0)

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown above.

    ---

2. In the **RetailProxy.MPOSOffline.ext.config** configuration file under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0 and later](#tab/retail-10-0)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
    ```

    ---

3. Update the web configuration file. In the **RetailSDK\Packages\RetailServer\Code\web.config** file, add the following lines to the **extensionComposition** section.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0 and later](#tab/retail-10-0)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
    ```

    ---

4. In the **Customization.settings** package customization configuration file under the **RetailSdk\\BuildTools** folder, add the following lines to the **ItemGroup** section to include the CRT extensions in deployable packages.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.Extensions.GenericTaxEngine.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.Core.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.Metadata.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataAccessor.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataAccessFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataModel.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.LocalizationFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.LocalizationFrameworkCore.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.ElectronicReportingMapping.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.XppSupportLayer.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Newtonsoft.Json\9.0.0.0\Newtonsoft.Json.dll" />
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.GenericTaxEngine.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Core.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Metadata.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessor.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataModel.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.LocalizationFrameworkCore.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.ElectronicReportingMapping.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.XppSupportLayer.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Newtonsoft.Json.9.0.1\lib\net45\Newtonsoft.Json.dll" />
    ```

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.GenericTaxEngine.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Core.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Metadata.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessor.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataModel.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.8.0.26\XppModule\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.8.0.26\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.LocalizationFrameworkCore.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.8.0.26\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.ElectronicReportingMapping.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.8.0.26\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.XppSupportLayer.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Newtonsoft.Json.9.0.1\lib\net45\Newtonsoft.Json.dll" />
    ```

    # [Retail 10.0 and later](#tab/retail-10-0)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    > [!NOTE]
    > This step doesn't apply to this version.

    ---

5. Modify the following files to include the Z3 libraries in deployable packages:

    # [Retail 7.3.1](#tab/retail-7-3-1)

    - Packages\\ModernPOS.Sdk\\Sdk.ModernPOSSetup.csproj
    - Packages\\ModernPOSOffline.Sdk\\Sdk.ModernPOSSetupOffline.csproj
    - Packages\\RetailServer\\Sdk.RetailServerSetup.proj

    Add the following lines to the **ItemGroup** section.

    ```xml
    <_bin_ext_Z3_x86_File Include="..\..\References\Z3\x86\*.*" />
    <_bin_ext_Z3_x64_File Include="..\..\References\Z3\x64\*.*" />
    ```

    For **Sdk.ModernPOSSetup.csproj** and **Sdk.ModernPOSSetupOffline.csproj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.

    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x64" SkipUnchangedFiles="true" />
    ```

    For **Sdk.RetailServerSetup.proj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.
    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x64" SkipUnchangedFiles="true" />
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - Packages\\ModernPOS.Sdk\\Sdk.ModernPOSSetup.csproj
    - Packages\\ModernPOSOffline.Sdk\\Sdk.ModernPOSSetupOffline.csproj
    - Packages\\RetailServer\\Sdk.RetailServerSetup.proj

    Add the following lines to the **ItemGroup** section.

    ```xml
    <_bin_ext_Z3_x86_File Include="$(SdkReferencesPath)\Z3.4.5.0\lib\net40\x86\*.*" />
    <_bin_ext_Z3_x64_File Include="$(SdkReferencesPath)\Z3.4.5.0\lib\net40\x64\*.*" />
    ```

    For **Sdk.ModernPOSSetup.csproj** and **Sdk.ModernPOSSetupOffline.csproj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.

    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x64" SkipUnchangedFiles="true" />
    ```

    For **Sdk.RetailServerSetup.proj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.

    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x64" SkipUnchangedFiles="true" />
    ```

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    - Packages\\\_SharedPackagingProjectComponents\\Sdk.ModernPos.Shared.csproj
    - Packages\\RetailServer\\Sdk.RetailServerSetup.proj

    Add the following lines to the **ItemGroup** section.

     ```xml
    <_bin_ext_Z3_x86_File Include="$(SdkReferencesPath)\Z3.4.5.0\lib\net40\x86\*.*" />
    <_bin_ext_Z3_x64_File Include="$(SdkReferencesPath)\Z3.4.5.0\lib\net40\x64\*.*" />
     ```

    For **Sdk.ModernPos.Shared.csproj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.

    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x64" SkipUnchangedFiles="true" />
    ```

    For **Sdk.RetailServerSetup.proj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section.

    ```xml
    <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x86" SkipUnchangedFiles="true" />
    <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x64" SkipUnchangedFiles="true" />
    ```

    # [Retail 10.0 and later](#tab/retail-10-0)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    > [!NOTE]
    > This step doesn't apply to this version.

    ---

6. Enable the Tax Registration Id POS extension:

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.3 and later](#tab/retail-8-1-3)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0 and later](#tab/retail-10-0)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 10.0.6 and later](#tab/retail-10-0-6)

    Open **RetailSDK\POS\Extensions\extensions.json** and add the following lines:

    ``` xml
    {
      "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

7. Run **msbuild** for the whole Retail SDK to create deployable packages.
8. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create retail deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
