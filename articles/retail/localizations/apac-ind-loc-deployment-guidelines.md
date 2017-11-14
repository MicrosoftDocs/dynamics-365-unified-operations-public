---
# required metadata

title: Deployment guidelines for cash registers for India
description: This topic is a deployment guide for the Retail localization for India.
author: 
manager: ralin
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.industry: Retail
ms.author: jiaqia
ms.search.scope: Retail
ms.search.validFrom: 2018-01-15
ms.dyn365.ops.version: App update 7.3.1

---
# Deployment guidelines for cash registers for India

This topic is a deployment guide that shows how to enable the requirements for Goods and Services Tax (GST) in the Microsoft Dynamics 365 for Retail localization for India.

This sample is a part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](./retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT). To run this sample, you must modify and build the CRT projects. We recommend that use you an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**. You can find this solution under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### Generic Tax Engine component

1. Find the **Runtime.Extensions.GenericTaxEngine** project, and build it.
2. Find the following files:

    - In the **Extensions.GenericTaxEngine\\bin\\Debug** folder:

        - Contoso.Commerce.Runtime.GenericTaxEngine.dll

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

    - In the **Reference\\Newtonsoft.Json\\9.0.0.0** folder:

        - Newtonsoft.Json.dll

    - In the **Reference\\Z3\\x86** folder:

        - Microsoft.Z3.dll
        - libz3.dll

        > [!NOTE]
        > If you target a 64-bit computer, modify the Z3 package so that it's an x64 version.

3. Copy the 13 assembly files to the CRT extensions folder:

    - **Retail Server:** Copy the assemblies to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Copy the assemblies to the **\\ext folder** under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

## Production environment

Follow these steps to create deployable packages that contain Retail components, and to apply the packages in a production environment.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.GenericTaxEngine" />
    ```

2. In the **Customization.settings** package customization configuration file, add the following lines to the **ItemGroup** section to include the CRT extensions in deployable packages.

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
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Z3\x86\Microsoft.Z3.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Z3\x86\libz3.dll" />
    ```

    > [!NOTE]
    > If you target a 64-bit computer, modify the Z3 package so that it's an x64 version.

3. Run **msbuild** for the whole Retail SDK to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).
