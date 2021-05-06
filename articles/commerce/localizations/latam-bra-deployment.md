---
# required metadata

title: Set up and deploy Dynamics 365 Commerce localization for Brazil
description: This topic covers how to set up and deploy Microsoft Dynamics 365 Commerce localization for Brazil.
author: v-ankvik
manager: annbe
ms.date: 05/06/2021
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
# Set up and deploy Dynamics 365 Commerce localization for Brazil

[!include[banner](../includes/banner.md)]

This topic covers how to set up and deploy Microsoft Dynamics 365 Commerce localization for Brazil.

Dynamics 365 Commerce localization for Brazil consists of several extensions of Commerce components. The extensions let you calculate Brazil-specific taxes, generate electronic fiscal documents for retail sales, print DANFE (Documento Auxiliar de Nota Fiscal Eletrônica) fiscal receipts containing custom fields, manage Brazil-specific customer information, and issue sales in offline contingency mode with postponed registration of electronic fiscal documents. For more information about Dynamics 365 Commerce localization for Brazil, see [Brazilian localization scope](../../finance/localizations/latam-bra-scope.md) and [Commerce localization for Brazil](latam-bra-commerce-localization.md).

The extensions described here were developed based on the fiscal integration framework. For details about the fiscal integration functionality, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md). Brazilian electronic fiscal documents formats are implemented using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md).

Commerce localization for Brazil includes extensions for the Commerce runtime (CRT), Retail Server, and point of sale (POS).

## Enable Brazil-specific Commerce functionality

This section describes how to configure Dynamics 365 Commerce headquarters settings that are specific to and recommended for Brazil. For more information, see the [Commerce home page](../index.md).

To enable and use the Brazil-specific functionality, you must specify the following settings in Commerce headquarters:

1. In the primary address of the legal entity, set the **Country/region** field to **BRA** (Brazil).
1. In the POS functionality profile of every store that is located in Brazil, set the **ISO code** field to **BR** (Brazil).
1. Go to **System administration \> Workspaces \> Feature management**, select the **All** tab, and enable the following feature keys:
    - **(Brazil) Commerce functionality that is specific to Brazil**
    - **Retail statements - Trickle feed**
    - **Support for internal and external connectors in the fiscal integration framework**
    - **Postponed registration of documents**
    - **User-defined certificate profiles for retail stores**

## Set up electronic reporting

You can download the electronic reporting configuration for the electronic fiscal documents from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the latest versions of the configurations listed below.

To set up electronic reporting in Commerce headquarters, follow these steps.

1. Go to **Organization Administration \> Workspaces \> Electronic Reporting**.
1. Select the ellipsis (...) on the **Microsoft** configuration provider tile, and then select **Set active**.
1. Select **Repositories** on the **Microsoft** configuration provider tile.
1. Select the **Global** configuration repository, and then select **Open** on the Action Pane.
1. In the **Connect to Regulatory Configuration Service** dialog box, select **Click here to connect to Regulatory Configuration Service**, return to the dialog box, and then select **OK**.
1. Import the last shared versions of the following data model, data model mapping, and format configurations:
    - **(Preview) Fiscal documents mapping**
    - **(Preview) NF-e cancel export format (BR)**
    - **(Preview) NF-e status request export format (BR)**
    - **(Preview) NF-e submit export format (BR)**
    - **(Preview) NFC-e submit export format (BR)**
    - **(Preview) NFC-e contingency export format (BR)**
    - **(Preview) NFC-e fiscal documents mapping**
    - **(Preview) NFC-e fiscal documents validation format (BR)**
1. Go to **Organization administration \> Workspaces \> Electronic reporting** and select **Reporting Configurations**.
1. Select **Fiscal documents mapping**, and then set **Default model mapping** to **No**.
1. Go to **NFC-e fiscal documents mapping**, and then set **Default model mapping** to **Yes**.
1. Go to **Organization Administration \> Setup \> Brazilian parameters**, select the **Retail** tab, and then select **NFC-e fiscal documents validation format (BR)** in the **Format mapping** field. 

## Set up fiscal establishment and NF-e federal parameters

To set up fiscal establishment and NF-e (Nota Fiscal Eletrônica) federal parameters in Commerce headquarters, follow these steps.

1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishment**.
1. For **tax registration numbers - CNPJ, IE & CCM**, enter the tax registration number(s), and for **address of the establishment** enter an address.
1. Set up CSC (Código de Segurança do Contribuinte) encryption by entering the CSC token and CSC alphanumeric code.
1. Select the appropriate digital certificate for tax authority service authentication and digital signing of fiscal documents.
    > [!NOTE]
    > The certificate configured in **Fiscal establishment** is used for NFC-e (Nota Fiscal de Consumidor Eletrônica) documents that were issued on POS in offline contingency mode that are then submitted for authorization through Commerce headquarters. In order to sign fiscal documents in offline contingency mode, a certificate must be installed in the offline certificate storage of the POS.
1. Select **Environment types "Testing" or "Production"** for NF-e / NFC-e web-services.
1. Specify the **versions of the NF-e and NFC-e features**.
1. Select **Authorities** from **NF-e federal parameters** for NF-e / NFC-e web-services.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Electronic fiscal documents \> NF-e federal parameters**.
1. Create new or use existing authorities for the needed states.
1. Insert QR code URLs into the **Internet address for NFC-e inquiry** fields of every state.
1. Specify the **Endpoints for all web services of the respected environments** for every state.

## Set up address books

To add the same address book for Brazilian customers, stores, and workers in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Customers \> All customers**. On the **General** tab, add retail address books for customers as needed in the **Address books** field.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**. On the **General** tab, add the address books for the stores in the **Customer address book** and **Employee address book** fields.
1. Go to **Retail and Commerce \> Employees \> Workers**. On the **Worker summary** tab, add the address books for workers in the **Address books** field. 

## Set up sales tax for POS

To set up sales tax for POS in Commerce headquarters, follow these steps. 

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**. Create necessary sales tax codes for different tax types and taxation codes, including sales tax codes for returns.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax group**. Create new sales tax groups for retail sales and returns, and add the tax codes created in the previous step.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**. In the **Sales tax group** and **Sales tax group for returns** fields, select the sales tax groups created in the previous step.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**, create a new group named **Item sales tax groups for retail**, and add the previously created sales tax codes.
1. Go to **Organization administration \> Setup \> Fiscal document source texts**, create a fiscal document source text for retail tax burden, and set **Restriction** to **External** and **Fiscal information** to **No**.
1. Go to **Organization administration \> Setup \> Brazilian parameters**. Select the **Retail** tab and specify the retail tax burden source text in the **Text ID** field.
1. Go to **Retail and Commerce \> Products and categories \> Released products by category**. Select the desired products, and fill in the following Brazil-specific fields:
    - Under the **Sell** tab:
        - **Item sales tax group**
    - Under the **Fiscal information** tab:
        - **Taxation origin**
        - **Product type**
        - **Fiscal classification code**
        - **Approximate federal tax percentage**
        - **Approximate state tax percentage**
        - **Approximate city tax percentage**
1. Go to **Tax \> Setup \> Sales tax \> CFOP codes** and set **Fiscal reference required** to **No** for CFOP codes used for retail returns.

## Set up a retail store

To set up a retail store in Commerce headquarters, follow these steps.

1. Go to **Inventory management \> Setup \> Inventory breakdown > Warehouses** and create warehouses for the stores, including addresses. 
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**, create the stores, and fill in the following Brazil-specific fields:
    - **Prices include sales tax**
    - **Sales tax group**
    - **Sales tax group for returns**
    - **Default customer** (should be included in the same address book as the store)
1. Set up **Payment methods** for the created stores.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler**. Add the newly created stores to the used channel database.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**. Create POS registers, and fill in the following Brazil-specific fields:
    - **NFC-e series**,
    - **NFC-e contingency series**,
    - **NF-e series**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Devices** and create and configure devices for the registers.
1. Go to **Organization administration \> Organizations \> Organization hierarchies**. Select **Retail Stores by Business Unit**, select **View**, select **Edit \> Insert retail channel**, and then add the newly created stores to the appropriate business units in the hierarchy. Publish the changes.
1. Assign the **Retail POS posting** purpose to the **Retail Stores by Business Unit*** organizational hierarchy.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes** and publish channel updates.
1. Go to **Retail and Commerce \> Channel setup \> POS profiles \> Receipt profiles**. Create receipt layouts for DANFE, and add the layouts to the receipt profiles.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language text setup should be created in both the user's default company and the legal entity of the store that the receipt setup is created for.

In the receipt format designer, add Brazilian custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

## Set up the fiscal registration process

To set up the fiscal registration process in Commerce headquarters, follow the steps below. For more information, see [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set **Enable fiscal integration** to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**. Load the connector configuration from the [Commerce Fiscal Integration Repo](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations). The following files are located under [**Configurations\\Connectors**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FConnectors):
    - SubmitConnector.xml,
    - ContingencyConnector.xml.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**. Load the document provider configurations from [Commerce Fiscal Integration Repo](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations). The following configuration files are located under [**Configurations\\DocumentProviders**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FDocumentProviders):
    - SubmitProvider.xml
    - ContingencyProvider.xml
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create three new profiles per document provider from the step above and select the loaded connectors. Update data mapping settings as needed.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create three new profiles and select the loaded connectors from the step above. Update connection settings as needed.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector group**. Create three new groups, one for each connector functional profile from the step above.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Registration process**. Create a new process. Select the three previously-created fiscal connector groups as registration steps.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select the profile that is linked to the store where the registration process should be activated, and then expand the **Fiscal registration process** FastTab. Select the registration process created above. To enable registration of non-fiscal events on POS, on the **Functions** FastTab set **Audit** to **No**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** FastTab and select the connector technical profile.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles** and set up profiles for printers.
1. Go to the **Stores** form, expand the **Hardware stations** FastTab, and add a setup for the hardware station. If needed, configure IP addresses for the network printer configured earlier.

## Customer information management

The **Add customer information** operation can be used to add Brazil-specific customer tax registration numbers such as the CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas) number and addresses to sales transactions. Customer information can be pulled from the customer record specified for the transaction, or entered manually. The customer information can then be printed on DANFE fiscal receipts, and can be used for invoicing purposes.

To configure the **Add customer information** operation in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Button Grids**. 
1. Select the button grid where the operation should appear, and then open **Button grid designer**. 
1. Add a new button, and then select **Add customer information** in the **Action** field. 

For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

## Set up parameters for statements

1. Go to **Organization administration \> Number sequences**. Create and set up number sequences for retail statements for each store (operating unit).
1. On the **References** FastTab, add two references for the **Retail store** area: one with the **Reference** value set to **Statement number**, and one with the **Reference** value set to **Voucher**.
1. Go to **Retail and Commerce \> Catalog and assortments**. Create a new assortment with appropriate products, add the previously-created stores under the **Commerce channels** tab, and then select **Publish**.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes** and publish channel updates.
1. Go to **Sales and marketing \> Setup > Returns \> Disposition codes** and add a disposition code.
1. Go to **Retail and commerce \> Products and categories \> Released products by category**. Select a product for the gift card, and then select the **Blocked at register** check box.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**, select the **Customer orders** tab, and then enter the **Disposition code** from step 4 above.
1. Select the **Posting** tab on the same form and set up the parameters for the gift card, including **Gift card company** and **Gift card product**.

## Configure a production environment

This section provides deployment guidance for enabling Commerce components of Dynamics 365 Commerce localization for Brazil.

> [!NOTE]
> Some steps in these procedures vary, depending on the product version you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

### Use certificates for tax authority service authentication and digital signing of fiscal documents

A digital certificate for Application Object Server (AOS) must be stored in Azure Key Vault. 

Digital certificates for Retail Server must be installed locally or stored in Azure Key Vault. Both location types for Retail Server can be configured simultaneously and used according to their priorities. 

For more information about how to work with Azure Key Vault storage, see [Get started with Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started) and [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

You can also use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Azure Key Vault or Commerce headquarters are not available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

> [!NOTE]
> In order to sign NFC-e documents in offline contingency mode, a certificate must be installed in the offline certificate storage of the POS.

#### Configure certificates to be used in Retail Server

The Brazilian tax service extension of Retail Server uses a certificate for tax authority service authentication, and for digital signing of fiscal documents. Retail Server certificates settings are controlled by certificate profiles.

To configure certificates to be used in Retail Server, follow these steps.

1. Go to **System administration \> Setup \> Certificate profiles**. 
1. Create a certificate profile for the appropriate legal entities. 
1. Select **Settings** for each legal entity.
    - For the local certificate, create a record where the **Location type** value is **Local certificate**, and then enter the **Thumbprint** value.
    - For the Azure Key Vault certificate, create a record where the **Location type** value is **Key Vault**, and then select **Key Vault certificate**.

Certificates can either be installed in the local certificate storage of the machine where Retail Server is deployed, stored in Azure Key Vault, or stored in both location types and configured simultaneously to be used according to their priorities.

#### Configure a certificate in AOS

A certificate for tax authority service authentication is stored in Azure Key Vault. This certificate is used in AOS for submission through Commerce headquarters NFC-e documents that were issued on POS in offline contingency mode. The certificate is also needed for digital signing of "discard" and "cancellation by substitution" requests. Parameters of the certificate must be specified in the fiscal establishment settings.

To configure a certificate in AOS, follow these steps.

1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Select the appropriate digital certificate for tax authority service authentication and digital signing of fiscal documents.

> [!NOTE]
> The appropriate distribution jobs must be run in headquarters once the setup is completed.

### Configure CRT extension components

To configure CRT extension components, follow these steps.

1. Find the extensions configuration file for CRT.

    - **Commerce Scale Unit:** the file is named **Commerceruntime.ext.config**, and is located in the **bin\\ext** folder under the Microsoft IIS Commerce Scale Unit site location.
    - Register the CRT change in the extensions configuration file.

       ``` xml
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalServiceBrazil" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdBrazil" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxServiceBrazil" />
       ```

1. Find the extensions configuration file for Local CRT on Modern POS: 
     
     - **Local CRT on Modern POS:** the file is named **CommerceRuntime.MPOSOffline.Ext.config**, and is located in the local CRT client broker location.

       ``` xml
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil.Offline" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ElectronicFiscalDocumentBrazil" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdBrazil" />
       <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxServiceBrazil" />
       ```

> [!WARNING]
> Do not edit the **Commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

### Enable Modern POS extension components

To enable Modern POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and ensure that it can be compiled without errors. Also make sure to confirm that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and must uninstall previously installed instances of Modern POS as required.

1. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

    ``` json
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
    > For more information and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file of the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Enable cloud POS extension components

To enable the cloud POS extension components to be loaded in **extensions.json**, add the following lines in the appropriate location of the JSON file.

``` json
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

[Get started with Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)

[Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md)

[User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md)

[Manage secrets for retail channels](../dev-itpro/manage-secrets.md)
