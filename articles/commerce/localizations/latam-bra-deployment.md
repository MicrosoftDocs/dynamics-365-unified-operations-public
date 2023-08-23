---
title: Set up and deploy the Dynamics 365 Commerce localization for Brazil
description: This article covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Brazil.
author: EvgenyPopovMBS
ms.date: 03/04/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.search.industry: Retail
---
# Set up and deploy the Dynamics 365 Commerce localization for Brazil

[!include [banner](../includes/banner.md)]

This article covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Brazil.

The Dynamics 365 Commerce localization for Brazil includes several extensions of the following Commerce components: the Commerce runtime (CRT), Retail Server, and point of sale (POS). These extensions let you calculate Brazil-specific taxes, generate electronic fiscal documents for retail sales, print DANFE (Documento Auxiliar de Nota Fiscal Eletrônica) and CF-e-SAT (Cupom Fiscal Eletrônico - Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal receipts that have custom fields, manage Brazil-specific customer information, and issue sales in offline contingency mode where registration of electronic fiscal documents is postponed. For more information about the Commerce localization for Brazil, see [Brazilian localization scope](../../finance/localizations/latam-bra-scope.md) and [Commerce localization for Brazil](latam-bra-commerce-localization.md).

The extensions that are described in this article were developed based on the fiscal integration framework. For information about the fiscal integration functionality, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md). [Electronic reporting (ER)](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) is used to implement formats for Brazilian electronic fiscal documents.

## Enable Brazil-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Brazil. For more information, see the [Commerce home page](../welcome.md).

To enable and use the Brazil-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **BRA** (Brazil).
1. In the POS functionality profile of every store that is located in Brazil, set the **ISO code** field to **BR** (Brazil).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - (Brazil) Commerce functionality that is specific to Brazil
    - (Brazil) NFC-e synchronous processing
    - Postponed registration of documents

## Set up electronic reporting

You can download the ER configurations for the electronic fiscal documents from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import Electronic reporting (ER) configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations). You must download the latest versions of the configurations that are listed in the following procedure.

To set up electronic reporting in Commerce headquarters, follow these steps.

1. Go to **Organization Administration \> Workspaces \> Electronic Reporting**.
1. On the tile for the **Microsoft** configuration provider, select the ellipsis (**...**), and then select **Set active**.
1. On the tile, select **Repositories**.
1. Select the **Global** configuration repository, and then, on the Action Pane, select **Open**.
1. In the **Connect to Regulatory Configuration Service** dialog box, select **Click here to connect to Regulatory Configuration Service**, return to the dialog box, and then select **OK**.
1. Import the latest shared versions of the following data model, data model mapping, and format configurations:

    - Fiscal documents mapping
    - NF-e submit export format (BR)
    - NF-e status request export format (BR)
    - NF-e cancel export format (BR)
    - NFC-e submit export format (BR)
    - NFC-e contingency export format (BR)
    - NFC-e fiscal documents mapping
    - NFC-e fiscal documents validation format (BR)
    - CF-e submit export format (BR)
    - CF-e cancel export format (BR)

1. Go to **Organization administration \> Workspaces \> Electronic reporting**, and select **Reporting configurations**.
1. Select **Fiscal documents mapping**, and then set the **Default model mapping** option to **No**.
1. Select **NFC-e fiscal documents mapping**, and then set the **Default model mapping** option to **Yes**.
1. Go to **Organization Administration \> Setup \> Brazilian parameters**.
1. On the **Retail** tab, in the **Format mapping** field, select **NFC-e fiscal documents validation format (BR)**.

## Set up a fiscal establishment and NF-e federal parameters

To set up a fiscal establishment and NF-e (Nota Fiscal Eletrônica) federal parameters in Commerce headquarters, follow these steps.

1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishment**.
1. In the **Tax registration numbers - CNPJ, IE & CCM** field, enter the tax registration numbers. (CNPJ stands for *Cadastro Nacional da Pessoa Jurídica*, IE stands for *Inscrição Estadual*, and CCM stands for *Cadastro de Contribuinte Mobiliário*.)
1. In the **Address of the establishment** field, enter an address.
1. Set up CSC (Código de Segurança do Contribuinte) encryption by entering the CSC token and CSC alphanumeric code.
1. Select the appropriate digital certificate for authentication with the tax authority service and digital signing of fiscal documents.

    > [!NOTE]
    > The certificate that is configured on the **Fiscal establishment** page is used for NFC-e (Nota Fiscal de Consumidor Eletrônica) documents that are issued in POS in offline contingency mode and then submitted for authorization through Commerce headquarters. To enable fiscal documents to be signed in offline contingency mode, you must install a certificate in the offline certificate storage of the POS. For more information, see [Make a cash-and-carry sale of goods in offline contingency mode](latam-bra-nfce.md#scenario-3-make-a-cash-and-carry-sale-of-goods-in-offline-contingency-mode) and [Postponed registration of NFC-e issued in contingency mode](latam-bra-nfce-contingency-mode.md).

1. Under **NF-E WEB SERVICE**, in the **Environment** field, select **Testing** or **Production.**
1. Under **NFC-E WEB SERVICE**, in the **Environment** field, select **Testing** or **Production.**
1. Specify the versions of the NF-e and NFC-e features.
1. Under **NF-E WEB SERVICE**, in the **Authority** field, enter the value used at **NF-e federal parameters \> Web services \> Authority**.
1. Under **NFC-E WEB SERVICE**, in the **Authority** field, enter the value used at **NF-e federal parameters \> Web services \> Authority**.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Electronic fiscal documents \> NF-e federal parameters**.
1. Create new authorities for the required states, or use existing authorities.
1. For each state, turn on the **NFC-e synchronous processing** flag.
1. For each state, in the **Internet address for NFC-e inquiry** field, enter QR code URLs.
1. For each state, specify the endpoints for all web services of the appropriate environments.

## Set up address books

To add the same address book for Brazilian customers, stores, and workers in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Customers \> All customers**.
1. On the **General** tab, in the **Address books** field, add retail address books for customers as required.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. On the **General** tab, in the **Customer address book** and **Employee address book** fields, add the address books for the stores.
1. Go to **Retail and Commerce \> Employees \> Workers**.
1. On the **Worker summary** tab, in the **Address books** field, add the address books for workers.

## Set up sales tax for POS

To set up sales tax for POS in Commerce headquarters, follow these steps.

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Create the required sales tax codes for different tax types and taxation codes. Include sales tax codes for returns.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax group**.
1. Create sales tax groups for retail sales and returns, and add the sales tax codes that you just created.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. In the **Sales tax group** and **Sales tax group for returns** fields, select the sales tax groups that you just created.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. Create item sales tax groups for retail, and add the sales tax codes that you created earlier.
1. Go to **Organization administration \> Setup \> Fiscal document source texts**.
1. Create a fiscal document source text for retail tax burden. Set the **Restriction** field to **External** and the **Fiscal information** option to **No**.
1. Go to **Organization administration \> Setup \> Brazilian parameters**.
1. On the **Retail** tab, in the **Text ID** field, specify the source text for retail tax burden.
1. Go to **Retail and Commerce \> Products and categories \> Released products by category**.
1. Select the desired products, and set the following fields:

    - On the **Sell** tab:

        - Item sales tax group

    - On the **Fiscal information** tab:

        - Taxation origin
        - Product type
        - Fiscal classification code
        - Approximate federal tax percentage
        - Approximate state tax percentage
        - Approximate city tax percentage

1. Go to **Tax \> Setup \> Sales tax \> CFOP codes**.
1. Set the **Fiscal reference required** option to **No** for CFOP (Código Fiscal de Operações e de Prestações) codes that are used for retail returns.

## Set up a retail store

To set up a retail store in Commerce headquarters, follow these steps.

1. Go to **Inventory management \> Setup \> Inventory breakdown \> Warehouses**.
1. Create warehouses for the stores, and specify addresses.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Create the stores, and set the following fields:

    - Prices include sales tax
    - Sales tax group
    - Sales tax group for returns
    - Default customer

        > [!NOTE]
        > The default customer should be included in the same address book as the store.

1. Set up payment methods for the stores that you created in the previous step.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler**.
1. Add the stores that you created earlier to the channel database that is used.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**.
1. Create POS registers, and set the following Brazil-specific fields, depending on the fiscal operation mode:

    - **Fiscal operation mode** – Select **NFC-e** or **CF-e**.
	- **NFC-e series** – If you selected **NFC-e** in the **Fiscal operation mode** field, enter the NFC-e series. 
    - **NFC-e contingency series** – If you selected **NFC-e** in the **Fiscal operation mode** field, enter the NFC-e series for offline contingency mode.
    - **NF-e series** – Enter the NF-e series to use when NF-e documents are issued for returns. 
    - **Register number for CF-e** – Enter the number of the POS register that is connected to SAT. This register number exists to comply with the **numeroCaixa** tag in the CF-e XML. Two or more POS registers can't have the same register number for CF-e.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Devices**.
1. Create and configure devices for the POS registers that you just created.
1. Go to **Organization administration \> Organizations \> Organization hierarchies**.
1. Select **Retail Stores by Business Unit** organization hierarchy, select **View**, select **Edit \> Insert retail channel**, and add the stores that you created earlier to the appropriate business units in the hierarchy. Then publish the changes.
1. Assign the **Retail POS posting** purpose to the **Retail Stores by Business Unit** organization hierarchy.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Publish the channel updates.
1. Go to **Retail and Commerce \> Channel setup \> POS profiles \> Receipt profiles**.
1. Create receipt layouts for DANFE, and add the layouts to the receipt profiles.
1. Create receipt layouts for CF-e-SAT and CF-e-SAT cancellation, and add the layouts to the receipt profiles.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language text setup should be created in both the user's default company and the legal entity of the store that the receipt setup is created for.

In the receipt format designer, add Brazilian custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

## Set up the fiscal registration process

To set up the fiscal registration process in Commerce headquarters, follow these steps. For more information, see [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md).

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Open the last available release branch (for example, [release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.31)).
    1. Open **src \> FiscalIntegration \> ElectronicFiscalDocumentsBrazil**.
    1. Download the fiscal connector configuration files at **Configurations \> Connectors** (for example, [the files for release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.31/src/FiscalIntegration/ElectronicFiscalDocumentsBrazil/Configurations/Connectors)):

        - SubmitConnector.xml
        - SatConnector.xml
        - ContingencyConnector.xml

    1. Download the fiscal document provider configuration files at **Configurations \> DocumentProviders** (for example, [the files for release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.31/src/FiscalIntegration/ElectronicFiscalDocumentsBrazil/Configurations/DocumentProviders)):

        - SubmitProvider.xml
        - SatProvider.xml
        - ContingencyProvider.xml

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration files that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration files that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**.
1. For each document provider that you just loaded the configuration for, create connector functional profiles, and select the fiscal connectors that you loaded the configuration for earlier. Update data mapping settings as required. If settings for SAT are needed, set the **Key Vault activation code secret name** and **POS Signature for SAT** fields.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
1. Create connector technical profiles, and select the fiscal connectors that you loaded the configuration for earlier. Update connection settings as required (for NFC-e, set the **Connector type** field to **Internal**). If settings for SAT are needed, set the **Connector name** field for the SAT device (**Connector type** = **Local**), and specify the **SAT library path** string. Include the name of the dynamic-link library (DLL) file.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector group**.
1. Create fiscal connector groups, one for each connector functional profile that you created earlier (including SAT).
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Registration process**.
1. Create a registration process. As registration steps, select the fiscal connector groups that you just created.
1. Create a separate registration process for the SAT device.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select the functionality profile that is linked to the store where the registration process should be activated, and then, on the **Fiscal registration process** FastTab, select the registration process number that you just created.
1. Create a separate functionality profile for the SAT device.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Select a hardware profile that is linked to the hardware station that the fiscal printer will be connected to.
1. Create a separate hardware profile for SAT device.
1. On the **Fiscal peripherals** FastTab, select the connector technical profile for each hardware profile.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Set up hardware profiles for printers.
1. On the **Stores** page, on the **Hardware stations** FastTab, add a setup for the hardware station. As required, configure IP addresses for the network printer that you configured earlier.

## Customer information management

The **Add customer information** operation can be used to add Brazil-specific CNPJ or CPF (Cadastro de Pessoas Físicas) customer tax registration numbers and addresses to sales transactions. Customer information can be pulled from the customer record that is specified for the transaction, or it can be manually entered. The customer information can then be printed on DANFE and CF-e-SAT fiscal receipts and used for invoicing purposes.

To configure the **Add customer information** operation in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Button grids**.
1. Select the button grid where the operation should appear, and then open **Button grid designer**.
1. Add a button, and then, in the **Action** field, select **Add customer information**.

For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

## Enable customer searches based on tax registration numbers in POS

To enable customers to be searched for by CNPJ/CPF and CCM tax registration numbers in POS, follow these steps.

1. In Commerce headquarters, on the **Commerce parameters** page, on the **POS search criteria** tab, on the **Customer search criteria** FastTab, add a record. 
1. In the new record, in the **Customer search criteria** field, select **Tax registration number**.
1. Select the **Display as shortcut** checkbox, but leave the **Can be refined** checkbox cleared.
1. On the **Distribution schedules** page, run the 1110 job.

## Set up parameters for statements

1. Go to **Organization administration \> Number sequences**.
1. Create and set up number sequences for retail statements for each store (operating unit).
1. On the **References** FastTab, add two references for the **Retail store** area: one where the **Reference** value is set to **Statement number** and one where it's set to **Voucher**.
1. Go to **Retail and Commerce \> Catalog and assortments**.
1. Create an assortment that includes appropriate products.
1. On the **Commerce channels** tab, add the stores that you created earlier. Then select **Publish**.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**, and publish channel updates.
1. Go to **Sales and marketing \> Setup > Returns \> Disposition codes**, and add a disposition code.
1. Go to **Retail and commerce \> Products and categories \> Released products by category**.
1. Select a product for the gift card, and then select the **Blocked at register** check box.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer orders** tab, enter the disposition code that you added earlier.
1. On the **Posting** tab, set up the parameters for the gift card. These parameters include the **Gift card company** and **Gift card product** fields.

## Configure a production environment

This section provides deployment guidance that will help you enable Commerce components of the Commerce localization for Brazil.

> [!NOTE]
> Some steps in these procedures vary, depending on the product version that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new-home-page.md).

### Use certificates for authentication with the tax authority service and digital signing of fiscal documents

A digital certificate for Application Object Server (AOS) must be stored in Azure Key Vault.

Digital certificates for Retail Server must be installed locally or stored in Key Vault. Both location types for Retail Server can also be configured simultaneously and used according to their priorities.

For more information about how to work with Key Vault storage, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) and [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

You can also use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Commerce headquarters isn't available. This feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

> [!NOTE]
> To enable NFC-e documents to be signed in offline contingency mode, you must install a certificate in the offline certificate storage of the POS. For more information, see [Make a cash-and-carry sale of goods in offline contingency mode](latam-bra-nfce.md#scenario-3-make-a-cash-and-carry-sale-of-goods-in-offline-contingency-mode) and [Postponed registration of NFC-e issued in contingency mode](latam-bra-nfce-contingency-mode.md).

#### Configure certificates so that they can be used in Retail Server

The Brazilian tax service extension of Retail Server uses a certificate for authentication with the tax authority service and digital signing of fiscal documents. The settings for Retail Server certificates are controlled by certificate profiles.

To configure certificates so that they can be used in Retail Server, follow these steps.

1. Go to **System administration \> Setup \> Certificate profiles**.
1. Create a certificate profile for the appropriate legal entities.
1. For each legal entity, select **Settings**, and then follow these steps:

    - For the local certificate, create a record where the **Location type** field is set to **Local certificate**. Then, in the **Thumbprint** field, enter a value.
    - For the Key Vault certificate, create a record where the **Location type** field is set to **Key Vault**, and then select **Key Vault certificate**.

Certificates can be installed in the local certificate storage of the machine where Retail Server is deployed or in Key Vault. Alternatively, they can be installed in both location types and configured simultaneously so that they are used according to their priorities.

#### Configure a certificate in AOS

A certificate for authentication with the tax authority service is stored in Key Vault. This certificate is used in AOS to submit, through Commerce headquarters, NFC-e documents that were issued in POS in offline contingency mode. The certificate is also required for digital signing of "discard" and "cancellation by substitution" requests. Parameters of the certificate must be specified in the fiscal establishment settings.

To configure a certificate in AOS, follow these steps.

1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Select the appropriate digital certificate for authentication with the tax authority service and digital signing of fiscal documents.

> [!NOTE]
> After the setup is completed, the appropriate distribution jobs must be run in Commerce headquarters.

### Set up the SAT activation code

The SAT activation code enables communication between the POS register and the SAT device. The SAT hardware attribute contains the activation code for the SAT serial number that was entered during SAT device activation. That SAT hardware attribute must be associated with the POS register. 

To create the SAT hardware attribute, follow these steps.

1. Go to **System administration \> Setup \> Key Vault parameters**.
1. Create a record for the SAT activation code.
1. Add a secret that is named **ActivationCode**.
1. In the **Secret** field, enter value.
1. In the **Secret type** field, select **Manual**.

### Configure CRT extension components

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used with this localization functionality. You must use the previous version of the Retail software development kit (SDK) on a developer virtual machine (VM) in LCS. (Microsoft plans to add support for localization functionality to the new independent packaging and extension model in later versions.)

To configure CRT extension components, follow these steps.

1. Find the extension configuration file for CRT.

    - **Commerce Scale Unit:** The file is named **Commerceruntime.ext.config**, and it's located in the **bin\\ext** folder under the Internet Information Services (IIS) Commerce Scale Unit site location.

2. Register the CRT change in the extension configuration file.

    ```xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalServiceBrazil" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdBrazil" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxServiceBrazil" />
    ```
 
3. Find the Web.config file for CRT.

    - **Commerce Scale Unit:** The file is named **Web.config**, and it's located in the **\RetailServer\webroot** folder.

4. Update this Web.config file by adding the new extension library name in the extensionComposition section.
 
    ```xml
    <extensionComposition>
        <add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.ElectronicFiscalDocumentBrazil" />
    </extensionComposition>
    ```

5. Find the extension configuration file for Local CRT on Modern POS:

    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located in the local CRT client broker location.

6. Register the Local CRT on Modern POS change in the extension configuration file.

    ```xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil.Offline" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdBrazil" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxServiceBrazil" />
    ```

    > [!WARNING]
    > Don't edit the **Commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

7. Find the extension configuration file for Retail proxy on Modern POS:

    - **Retail proxy on Modern POS:** The file is named **RetailProxy.MPOSOffline.Ext.config**, and it's located in the local CRT client broker location.

8. Register the Retail proxy on Modern POS change in the extension configuration file.

    ```xml
    <retailProxyExtensions>
        <composition>
            <add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.ElectronicFiscalDocumentBrazil" />
        </composition>
    </retailProxyExtensions>
    ```

### Enable Hardware station extension components

> [!NOTE]
> For more information, see [Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md).

#### SatBrazil component

To help ensure that the Hardware station loads the SAT extension component, you must set the corresponding assembly reference in the **HardwareStation.Extension.config** file that is located in the **Assets** folder in the Retail SDK.

```xml
<hardwareStationExtension>
    <composition>
        <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.FiscalPeripherals.SatBrazil" />
    </composition>
</hardwareStationExtension>
```

#### Payments.Connector.Adyen.Device.Brazil component

To help ensure that the Hardware station loads the extension component for the Payment Connector for Adyen in POS for Brazil, you must set the corresponding assembly reference in the **HardwareStation.Extension.config** file that is located in the **Assets** folder in the Retail SDK.

```xml
<hardwareStationExtension>
    <composition>
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Device.Brazil" />
    </composition>
</hardwareStationExtension>
```

### Enable Modern POS extension components

To enable Modern POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, confirm that you can run Modern POS from Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

1. Enable the extensions to be loaded by adding the following lines in the **extensions.json** file.

    ```json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/ElectronicFiscalDocument.BR"
            },
            {
                "baseUrl": "Microsoft/TaxRegistrationId.BR"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file of the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

To enable the Cloud POS extension components to be loaded in the **extensions.json** file, add the following lines in the appropriate part of the file.

```json
{
    "extensionPackages": [
        {
            "baseUrl": "Microsoft/ElectronicFiscalDocument.BR"
        },
        {
            "baseUrl": "Microsoft/TaxRegistrationId.BR"
        }
    ]
}
```

## Additional resources

[Commerce localization for Brazil](latam-bra-commerce-localization.md) 

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

[CF-e fiscal documents and integration with SAT functionality in Commerce POS for Brazil](latam-bra-cf-e-sat.md)

[Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md)

[Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil](latam-bra-adyen.md)
