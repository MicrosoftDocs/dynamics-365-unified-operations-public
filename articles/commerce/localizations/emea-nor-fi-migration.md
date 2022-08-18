---
# required metadata

title: Migrate from legacy Commerce functionality for Norway
description: This article explains how to migrate from the legacy digital signing solution in the Microsoft Dynamics 365 Commerce localization for Norway to the solution that is based on the Commerce fiscal integration framework.
author: EvgenyPopovMBS
ms.date: 08/18/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Norway
ms.author: epopov
ms.search.validFrom: 2022-8-1

---

# Migrate from legacy Commerce functionality for Norway

[!include [banner](../includes/banner.md)]

This article explains how to migrate from the [legacy digital signing solution](./emea-nor-loc-deployment-guidelines.md) in the Microsoft Dynamics 365 Commerce localization for Norway to the solution that is based on the [Commerce fiscal integration framework](./emea-nor-fi-deployment.md).

If you're using the [legacy digital signing solution for Norway](./emea-nor-loc-deployment-guidelines.md) in Commerce version 10.0.28 or earlier, you must migrate to the [current Commerce fiscal integration solution](./emea-nor-fi-deployment.md) in version 10.0.29 or later to uptake the changes and receive timely updates for Norway-specific features in the future. No major changes are required in the extension logic that you created. However, because this update is a major update, some of your customizations will stop working unless changes are made on your side. Therefore, you should plan, prepare for, and complete the uptake for your environment.

## Migration process

The migration process from the legacy digital signing solution to the current fiscal integration solution is based on the concept of a gradual update. In other words, all Commerce headquarters and Commerce Scale Unit components should already be updated before you start to update the point of sale (POS).

To help prevent scenarios where an event or transaction is signed twice (by both the legacy extension and the current extension), or where an event or transaction can't be signed because of incorrect or incomplete configuration, we recommend that you turn off all POS devices that use the legacy solution and then update all of them simultaneously. For example, you can do this simultaneous update on a store-by-store basis, by updating each store's functionality profile.

To complete the migration process, follow these steps.

1. Update the Commerce headquarters components.
1. Update the Commerce Scale Unit components, and disable the extensions of the legacy solution.
1. Update the POS components, and disable the extensions of the legacy solution.
1. In Commerce headquarters, [enable Norway-specific features](./emea-nor-cash-registers.md#enable-features-for-norway) and configure the fiscal integration functionality for Norway.
1. Make sure that all offline transactions are uploaded from offline-enabled Modern POS devices to the channel database.
1. Close shifts, and sign out of all POS devices.
1. Adjust receipt formats so that they use updated custom fields.
1. Enable the fiscal integration functionality.
1. Restart the POS.

> [!NOTE]
> Depending on the type of environment, you can find more technical details about the migration process in either the [Migration in a development environment](#migration-in-a-development-environment) section of this article or the [Migration in a production environment](#migration-in-a-production-environment) section.

## Configure fiscal integration

To configure the fiscal integration functionality for Norway, follow the steps in [Set up fiscal registration](./emea-nor-fi-deployment.md#set-up-fiscal-registration-for-norway)) and [Configure the digital signature parameters](./emea-nor-fi-deployment.md#configure-the-digital-signature-parameters).

> [!IMPORTANT]
> Don't enable fiscal integration on the **Commerce shared parameters** page at this point.

## Adjust receipt formats

You must adjust your receipt formats so that they use updated custom fields. For up-to-date information about custom fields for Norway, see [Configure custom fields so that they can be used in receipt formats for sales receipts](./emea-nor-cash-registers.md#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts).

## Enable fiscal integration

When you're ready to enable the fiscal integration functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile that is linked to the store where the registration process should be activated.
1. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
1. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

> [!WARNING]
> After you complete the preceding steps, your previous customizations of the digital signing functionality will stop working.

## Migration in a development environment

### Update the Commerce runtime (development)

To update the Commerce runtime (CRT), follow these steps.

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config** and can be found in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

1. In the extension configuration file, find and remove the legacy CRT extensions, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

### Remove obsolete customizations from the development environment after future updates

After a future update, you can remove the obsolete Retail Server and POS customizations from your development environment. The following procedures describe how to remove extensions that can safely be removed.

#### Remove the earlier CRT extensions (development)

To remove the earlier CRT extensions, follow these steps.

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

1. In the extension configuration file, find and remove the earlier CRT extensions, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

#### Remove the earlier Retail Server extension (development)

To remove the earlier Retail Server extension, follow these steps.

1. Find the configuration file for Retail Server. The file is named **web.config** and can be found in the root folder under the IIS Retail Server site location.
1. In the configuration file, find the earlier Retail Server extension in the **extensionComposition** section, and remove it, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Disable the earlier Modern POS extension (development)

To disable the earlier Modern POS extension, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In the **extensions.json** file, remove the following lines to disable the earlier POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

#### Disable the earlier Cloud POS extension (development)

To disable the earlier Cloud POS extension, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. In the **extensions.json** file, remove the following lines to disable the earlier POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

## Migration in a production environment

### Update CRT (production)

To update CRT, follow these steps.

1. In the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, remove the earlier CRT extension, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

### Create deployable packages (production)

To create deployable packages, follow these steps.

1. Run **msbuild** for the whole Retail software development kit (SDK) to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually.

For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Remove obsolete customizations from the production environment after future updates

After a future update, you can remove the obsolete Retail Server and POS customizations from your production environment. The following procedures describe how to remove extensions that can safely be removed.

#### Remove the earlier CRT extension (production)

1. In the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, remove the earlier CRT extension.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

2. In the **Customization.settings** package customization configuration file under the **BuildTools** folder, remove the following lines to exclude the earlier sample CRT extension from the deployable packages.

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
    ```

3. In the **ItemGroup** section, remove the following lines to exclude the Retail Server extension from the deployable packages.

    ``` xml
    <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
    ```

4. Update the Retail Server configuration file. In the **web.config** file under the **RetailSDK\\Packages\\RetailServer\\Code** folder, remove the following lines from the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Disable the earlier Modern POS extension (production)

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the following folders to the exclude list:

        - SalesTransactionSignatureSample
        - SalesTransactionSignatureNorway
        - SequentialSignature

    - In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, remove the following lines.

        ``` json
        {
            "baseUrl": "Microsoft/AuditEvent.NO"
        },
        {
            "baseUrl": "SalesTransactionSignatureSample"
        },
        {
            "baseUrl": "SalesTransactionSignatureNorway"
        },
        {
            "baseUrl": "SequentialSignature"
        }
        ```

#### Disable the earlier Cloud POS extension (production)

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the following folders to the exclude list:

        - SalesTransactionSignatureSample
        - SalesTransactionSignatureNorway
        - SequentialSignature

    - In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, remove the following lines.

        ``` json
        {
            "baseUrl": "Microsoft/AuditEvent.NO"
        },
        {
            "baseUrl": "SalesTransactionSignatureSample"
        },
        {
            "baseUrl": "SalesTransactionSignatureNorway"
        },
        {
            "baseUrl": "SequentialSignature"
        }
        ```

#### Create deployable packages (production)

1. Run **msbuild** for the whole Retail SDK to create deployable packages.
1. Apply the packages via LCS or manually.

For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
