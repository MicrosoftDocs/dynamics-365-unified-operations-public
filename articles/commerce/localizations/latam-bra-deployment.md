---
# required metadata

title: Set up and deploy the Dynamics 365 Commerce localization for Brazil
description: This topic covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Brazil.
author: v-ankvik
ms.date: 06/03/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Set up and deploy the Dynamics 365 Commerce localization for Brazil

[!include[banner](../includes/banner.md)]

This topic covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Brazil.

The Dynamics 365 Commerce localization for Brazil includes several extensions of the following Commerce components: the Commerce runtime (CRT), Retail Server, and point of sale (POS). These extensions let you calculate Brazil-specific taxes, generate electronic fiscal documents for retail sales, print DANFE (Documento Auxiliar de Nota Fiscal Eletrônica) fiscal receipts that have custom fields, manage Brazil-specific customer information, and issue sales in offline contingency mode, where registration of electronic fiscal documents is postponed. For more information about the Commerce localization for Brazil, see [Brazilian localization scope](../../finance/localizations/latam-bra-scope.md) and [Commerce localization for Brazil](latam-bra-commerce-localization.md).

The extensions that are described in this topic were developed based on the fiscal integration framework. For information about the fiscal integration functionality, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md). [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md) is used to implement formats for Brazilian electronic fiscal documents.

## Enable Brazil-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Brazil. For more information, see the [Commerce home page](../index.md).

To enable and use the Brazil-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **BRA** (Brazil).
1. In the POS functionality profile of every store that is located in Brazil, set the **ISO code** field to **BR** (Brazil).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - (Brazil) Commerce functionality that is specific to Brazil
    - Retail statements - Trickle feed
    - Support for internal and external connectors in the fiscal integration framework
    - Postponed registration of documents
    - User-defined certificate profiles for retail stores

## Set up electronic reporting

You can download the ER configurations for the electronic fiscal documents from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import Electronic reporting (ER) configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the latest versions of the configurations that are listed in the following procedure.

To set up electronic reporting in Commerce headquarters, follow these steps.

1. Go to **Organization Administration \> Workspaces \> Electronic Reporting**.
1. On the tile for the **Microsoft** configuration provider, select the ellipsis (**...**), and then select **Set active**.
1. On the tile, select **Repositories**.
1. Select the **Global** configuration repository, and then, on the Action Pane, select **Open**.
1. In the **Connect to Regulatory Configuration Service** dialog box, select **Click here to connect to Regulatory Configuration Service**, return to the dialog box, and then select **OK**.
1. Import the latest shared versions of the following data model, data model mapping, and format configurations:

    - (Preview) Fiscal documents mapping
    - (Preview) NF-e cancel export format (BR)
    - (Preview) NF-e status request export format (BR)
    - (Preview) NF-e submit export format (BR)
    - (Preview) NFC-e submit export format (BR)
    - (Preview) NFC-e contingency export format (BR)
    - (Preview) NFC-e fiscal documents mapping
    - (Preview) NFC-e fiscal documents validation format (BR)

1. Go to **Organization administration \> Workspaces \> Electronic reporting**, and select **Reporting configurations**.
1. Select **Fiscal documents mapping**, and then set the **Default model mapping** option to **No**.
1. Select **NFC-e fiscal documents mapping**, and then set the **Default model mapping** option to **Yes**.
1. Go to **Organization Administration \> Setup \> Brazilian parameters**.
1. On the **Retail** tab, in the **Format mapping** field, select **NFC-e fiscal documents validation format (BR)**.

## Set up a fiscal establishment and NF-e federal parameters

To set up a fiscal establishment and NF-e (Nota Fiscal Eletrônica) federal parameters in Commerce headquarters, follow these steps.

1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishment**.
1. In the **Tax registration numbers - CNPJ, IE & CCM** field, enter the tax registration numbers.
1. In the **Address of the establishment** field, enter an address.
1. Set up CSC (Código de Segurança do Contribuinte) encryption by entering the CSC token and CSC alphanumeric code.
1. Select the appropriate digital certificate for authentication with the tax authority service and digital signing of fiscal documents.

    > [!NOTE]
    > The certificate that is configured on the **Fiscal establishment** page is used for NFC-e (Nota Fiscal de Consumidor Eletrônica) documents that are issued in POS in offline contingency mode and then submitted for authorization through Commerce headquarters. To enable fiscal documents to be signed in offline contingency mode, you must install a certificate in the offline certificate storage of the POS.

1. Under **NF-E WEB SERVICE**, in the **Environment** field, select **Testing** or **Production.**
1. Under **NFC-E WEB SERVICE**, in the **Environment** field, select **Testing** or **Production.**
1. Specify the versions of the NF-e and NFC-e features.
1. Under **NF-E WEB SERVICE**, in the **Authority** field, enter the value used at **NF-e federal parameters \> Web services \> Authority**.
1. Under **NFC-E WEB SERVICE**, in the **Authority** field, enter the value used at **NF-e federal parameters \> Web services \> Authority**.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Electronic fiscal documents \> NF-e federal parameters**.
1. Create new authorities for the required states, or use existing authorities.
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
1. Create an item sales tax group that is named **Item sales tax groups for retail**, and add the sales tax codes that you created earlier.
1. Go to **Organization administration \> Setup \> Fiscal document source texts**.
1. Create a fiscal document source text for retail tax burden. Set the **Restriction** field to **External** and the **Fiscal information** option to **No**.
1. Go to **Organization administration \> Setup \> Brazilian parameters**.
1. On the **Retail** tab, in the **Text ID** field, specify the source text for retail tax burden.
1. Go to **Retail and Commerce \> Products and categories \> Released products by category**.
1. Select the desired products, and set the following Brazil-specific fields:

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
1. Create the stores, and set the following Brazil-specific fields:

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
1. Create POS registers, and set the following Brazil-specific fields:

    - NFC-e series
    - NFC-e contingency series
    - NF-e series

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Devices**.
1. Create and configure devices for the POS registers that you just created.
1. Go to **Organization administration \> Organizations \> Organization hierarchies**.
1. Select **Retail Stores by Business Unit** organization hierarchy, select **View**, select **Edit \> Insert retail channel**, and add the stores that you created earlier to the appropriate business units in the hierarchy. Then publish the changes.
1. Assign the **Retail POS posting** purpose to the **Retail Stores by Business Unit** organization hierarchy.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Publish the channel updates.
1. Go to **Retail and Commerce \> Channel setup \> POS profiles \> Receipt profiles**.
1. Create receipt layouts for DANFE, and add the layouts to the receipt profiles.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language text setup should be created in both the user's default company and the legal entity of the store that the receipt setup is created for.

In the receipt format designer, add Brazilian custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

## Set up the fiscal registration process

To set up the fiscal registration process in Commerce headquarters, follow these steps. For more information, see [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**.
1. Load the connector configuration from the [Commerce Fiscal Integration repository (repo)](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations). The following files are located under [**Configurations\\Connectors**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FConnectors):

    - SubmitConnector.xml
    - ContingencyConnector.xml

1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**.
1. Load the document provider configurations from the [Commerce Fiscal Integration repo](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations). The following configuration files are located under [**Configurations\\DocumentProviders**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FDocumentProviders):

    - SubmitProvider.xml
    - ContingencyProvider.xml

1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**.
1. For each document provider that you just loaded the configuration for, create three connector functional profiles, and select the fiscal connectors that you loaded the configuration for earlier. Update data mapping settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
1. Create three connector technical profiles, and select the fiscal connectors that you loaded the configuration for earlier. Update connection settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector group**.
1. Create three fiscal connector groups, one for each connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Registration process**.
1. Create a registration process. As registration steps, select the three fiscal connector groups that you just created.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select the functionality profile that is linked to the store where the registration process should be activated, and then, on the **Fiscal registration process** FastTab, select the registration process that you just created. To enable registration of non-fiscal events in POS, on the **Functions** FastTab, set the **Audit** option to **No**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Select a hardware profile that is linked to the hardware station that the fiscal printer will be connected to.
1. On the **Fiscal peripherals** FastTab, select the connector technical profile.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Set up hardware profiles for printers.
1. On the **Stores** page, on the **Hardware stations** FastTab, add a setup for the hardware station. As required, configure IP addresses for the network printer that you configured earlier.

## Customer information management

The **Add customer information** operation can be used to add Brazil-specific customer tax registration numbers, such as CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas) numbers, and addresses to sales transactions. Customer information can be pulled from the customer record that is specified for the transaction, or it can be manually entered. The customer information can then be printed on DANFE fiscal receipts and used for invoicing purposes.

To configure the **Add customer information** operation in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Button grids**.
1. Select the button grid where the operation should appear, and then open **Button grid designer**.
1. Add a button, and then, in the **Action** field, select **Add customer information**.

For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

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
> Some steps in these procedures vary, depending on the product version that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

### Use certificates for authentication with the tax authority service and digital signing of fiscal documents

A digital certificate for Application Object Server (AOS) must be stored in Azure Key Vault.

Digital certificates for Retail Server must be installed locally or stored in Key Vault. Both location types for Retail Server can also be configured simultaneously and used according to their priorities.

For more information about how to work with Key Vault storage, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) and [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

You can also use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Commerce headquarters isn't available. This feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

> [!NOTE]
> To enable NFC-e documents to be signed in offline contingency mode, you must install a certificate in the offline certificate storage of the POS.

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

### Configure CRT extension components

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

3. Find the extension configuration file for Local CRT on Modern POS:

    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located in the local CRT client broker location.

4. Register the local CRT on Modern POS change in the extension configuration file.

 ```xml
 <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
 <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil.Offline" />
 <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil" />
 <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdBrazil" />
 <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxServiceBrazil" />
 ```

> [!WARNING]
> Don't edit the **Commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

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

[Brazilian localization scope](../../finance/localizations/latam-bra-scope.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md)

[Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md)

[Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md)

[Receipt templates and printing](../receipt-templates-printing.md)

[Screen layouts for the point of sale (POS)](../pos-screen-layouts.md)

[Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started)

[Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md)

[User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md)

[Manage secrets for retail channels](../dev-itpro/manage-secrets.md)
