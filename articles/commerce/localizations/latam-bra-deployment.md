---
# required metadata

title: Setting up and deploying Commerce localization for Brazil
description: This topic is a deployment guide for the Commerce localization for Brazil.
author: v-ankvik
manager: epopov
ms.date: 
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
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Setting up and deploying Commerce localization for Brazil

[!include[banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable and set up the Dynamics 365 Commerce localization for Brazil. The localization consists of several extensions of Commerce components. For example, the extensions let you calculate Brazil-specific taxes, generate electronic fiscal documents for retail sales, print DANFE fiscal receipts containig custom fields, manage Brazil-specific customer information, issue sales in offline contingency mode with postponed registration of electronic fiscal documents. For more information about the localization for Brazil, see the [Brazilian localization scope](../../finance/localizations/latam-bra-scope.md) and [Commerce localization for Brazil](latam-bra-commerce-localization.md) pages.

The extensions described here were developed based on the fiscal integration framework. For details about the fiscal integration functionality, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md). Brazilian electronic fiscal documents formats are implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md).

This localization includes extensions for the Commerce runtime (CRT), Retail Server, and POS.

## Enable Commerce functionality that is specific to Brazil

This section describes the Commerce settings that are specific to and recommended for Brazil. For more information, see [Commerce home page](../index.md).

To use the Brazil-specific functionality, you must specify the following settings:

- In the primary address of the legal entity, set the **Country/region** field to **BRA** (Brazil).
- In the POS functionality profile of every store that is located in Brazil, set the **ISO code** field to **BR** (Brazil).
- Open **System administration > Workspaces > Feature management** menu. Go to the **All** tab, and filter the **feature keys** listed below.
- Enable the **(Brazil) Commerce functionality that is specific to Brazil** feature key.
- Enable the **Retail statements - Trickle feed** feature key.
- Enable the **Support for internal and external connectors in the fiscal integration framework** feature key.
- Enable the **Postponed registration of documents** feature key.
- Enable the **User-defined certificate profiles for retail stores** feature key.

## Set up Electronic reporting

You can download the ER configuration for the electronic fiscal documents from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You have to download the later versions of the configurations listed below.

1. Open **Organization Administration > Workspaces > Electronic Reporting** menu.
1. Click on the **menu "…"** on **Microsoft configuration provider** tile and click **Set active** button.
1. Click on **Repositories** on Microsoft configuration provider.
1. Select **Global** configuration repository and click **Open** button.
1. Click on the link **Click here to connect to Regulatory Configuration Service** for authorization, navigate back, click OK.
1. Import the last shared versions of the following **data model, data model mapping and format configurations**:

    - (Preview) **Fiscal documents mapping**,
    - (Preview) **NF-e cancel export format (BR)**,
    - (Preview) **NF-e status request export format (BR)**,
    - (Preview) **NF-e submit export format (BR)**,
    - (Preview) **NFC-e submit export format (BR)**,
    - (Preview) **NFC-e contingency export format (BR)**,
    - (Preview) **NFC-e fiscal documents mapping**,
    - (Preview) **NFC-e fiscal documents validation format (BR)**.
    
1. Open **Organization administration > Workspaces > Electronic reporting** menu, click **Reporting Configurations**.
1. Choose **Fiscal documents mapping**, and set **Default model mapping = No**.
1. Go to **NFC-e fiscal documents mapping**, and enable **Default model mapping**.
1. Open **Organization Administration > Setup > Brazilian parameters** form. Go to **Retail tab**, and specify the value **NFC-e fiscal documents validation format (BR)** in the **Format mapping** field. 

## Set up Fiscal establishment and NF-e federal parameters

1. Open **Organization administration > Organizations > Fiscal establishments > Fiscal establishments**.
1. Fill in **tax registration numbers - CNPJ, IE & CCM**, and add an **address of the establishment**.
1. Setup the **SCS**.
1. Choose the appropriate digital **certificate** for authentication in tax authority service and digital signing of fiscal documents.
    > [!NOTE]
    > The certificate configured in Fiscal establishment is used for the NFC-es that were issued on POS in offline contingency mode and can then be submitted for authorization through Commerce Headquarters. In order to sign fiscal documents in offline contingency mode a sertificate must be installed in offline certificate storage of POS (point of sale).
1. Choose **Environment types "Testing" or "Production"** for NF-e / NFC-e web-services.
1. Specify the **versions of the NF-e and NFC-e features**.
1. Select the **Authorities** from **NF-e federal parameters** for NF-e / NFC-e web-services.
1. Open **Organization administration > Organizations > Fiscal establishments > Electronic fiscal documents > NF-e federal parameters**.
1. Create new or use existing authorities for the needed states.
1. Insert the **QR-code URL**s into **Internet address for NFC-e inquiry** fields of every state.
1. Specify **Endpoints for all web services of the respected environments** of every state.

## Set up Address books

Add the same address book for Brazilian customers, and stores, and workers as follows:
1. Open **Retail and Commerce > Customers > All customers**. Add Retail address books for the customers as needed in the field **Address books** under the **General** tab.
1. Open **Retail and Commerce > Channels > Stores > All stores**, and add the address books for the stores in the fields **Customer address book** and **Employee address book** under the **General** tab.
1. Open **Retail and Commerce > Employees > Workers**, and add the address books for the workers in the field **Address books** under **Worker summary** tab. 

## Set up sales tax in Retail POS

1. Open **Tax > Indirect taxes > Sales tax codes** menu. Create necessary **sales tax codes for different tax types, and taxation codes**, etc., **including** sales tax codes for **returns**.
1. Open **Tax > Indirect taxes > Sales tax group**. Create new **sales tax groups for retail sales and returns**, and add the tax codes created in the previous step.
1. Open **Retail and Commerce > Channels > Stores > All stores**, and select the sales tax groups created in the previous step into the fields **Sales tax group** and **Sales tax group for returns**.
1. Open **Tax > Indirect taxes > Item sales tax groups**, and create **Item sales tax groups for retail**, and add the previously created Sales tax codes.
1. Open **Organization administration > Setup > Fiscal document source texts**, and create a fiscal document source text for **retail tax burden**, and set up **Restriction = External** and **Fiscal information = No**.
1. Open **Organization administration > Setup > Brazilian parameters**, go to **Retail** tab, and specify the retail **tax burden source text** in the field **Text ID**.
1. Open **Retail and commerce > Products and categories > Released products by category**. Choose the needed products, and fill in the following specific to Brazil fields.
    
    Under the **Sell tab**:
    - **Item sales tax group**.
     
    Under the **Fiscal information tab**:
    - **Taxation origin**,
    - **Product type**,
    - **Fiscal classification code**,
    - **Approximate federal tax percentage**,
    - **Approximate state tax percentage**,
    - **Approximate city tax percentage**.
    
1. Open **Tax > Setup > Sales tax > CFOP codes** and set **Fiscal reference required = No** for CFOP codes used for **retail returns**.

## Set up a retail store

1. Open **Inventory management > Setup > Inventory breakdown > Warehouses** menu. Create warehouses for the stores, including addresses. 
1. Open **Retail and Commerce > Channels > Stores > All stores** menu. 

    **Create the stores**, and fill in the following specific to Brazil fields:
    - **Prices include sales tax**,
    - **Sales tax group**,
    - **Sales tax group for returns**,
    - **Default customer** (should be included in the same address book as the store)

1. Set up **Payment methods** for the created stores.
1. Open **Retail and Commerce > Headquarters setup > Commerce scheduler** menu. Add the new created stores to the used channel database.
1. Open **Retail and Commerce > Channel setup > POS setup > Registers** menu. 

    Create POS registers, and fill in the following specific to Brazil fields:
    
    - **NFC-e series**,
    - **NFC-e contingency series**,
    - **NF-e series**.
    
1. Open **Retail and Commerce > Channel setup > POS setup > Devices** menu. Create and configure devices for the registers.
1. Open **Organization administration > Organizations > Organization hierarchies** menu. Select **Retail Stores by Business Unit** and click View, and click Edit > Insert retail Channel, and add the created stores to the needed business units in the hierarhy. Publish the changes.
1. **Assign purpose *Retail POS posting* to the *Retail Stores by Business Unit*** organization hierarhy.
1. Open **Retail and Commerce > Channel setup > Channel categories and product attributes** menu. Publish channel updates.
1. Open **Retail and Commerce > Channel setup > POS profiles > Receipt profiles** menu. Create receipt **layouts for DANFE**, and add the layouts to the profiles.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

In the Receipt format designer, add Brazilian custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

## Set up fiscal registration process

To enable the registration process, set up Headquarters using the steps below. For more details, see [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md).

1. Open **Commerce shared parameters** and enable **Fiscal integration** on the **General** tab.
1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors** menu. Load connector configuration from the [Commerce Fiscal Integration Repo](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations). 

    The files are located under [**Configurations\\Connectors**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FConnectors):
    
    - SubmitConnector.xml,
    - ContingencyConnector.xml.

1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers** menu. Load documment provider configurations from [Commerce Fiscal Integration Repo](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations).

    Configuration files are located under [**Configurations\\DocumentProviders**](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-EndToEndSolutions?path=%2Fsrc%2FFiscalIntegration%2FElectronicFiscalDocumentsBrazil%2FConfigurations%2FDocumentProviders):

    - SubmitProvider.xml,
    - ContingencyProvider.xml.

1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create three new profiles per document provider from the step above and select the loaded connectors. Update data mapping settings if needed.
1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create three new profiles and select the loaded connectors from the step above. Update connection settings if needed.
1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector group**. Create three new group per connector's functional profile from the step above.
1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Registration process**. Create a new process. Select three previously created fiscal connector groups as registration steps.
1. Open **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select the profile that is linked to the store where the registration process should be activated. Expand the **Fiscal registration process** tab. Select the created registration process from the step above. For enabling registration of non-fiscal events on POS enable **Audit** property at **Functions** fasttab.
1. Open the **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select one that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** Tab. Select the connector technical profile.
1. Open **Retail and Commerce > Channel setup > POS setup > POS profiles > Hardware profiles** menu. Set up profiles for printers.
1. Open **Stores** form, expand the **Hardware stations** tab, and add a setup for the hardware station. If needed, configure IP addresses for the network printer from the step above.

## Customer information management

The **Add customer information** operation can be used to add Brazil-specific customer tax registration numbers, such as the CNPJ / CPF number, and address to a sales transaction. This information can be used from the customer that is specified for the transaction, or it can be manually entered. The customer information can then be printed on DANFE fiscal receipts, and it can be used for invoicing purposes.

Open **Retail and Commerce > Channel setup > POS setup > POS > Button Grids** menu. Select the button grid where the operation should appear, and open the **Button grid designer**. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

## Set up parameters for statements
1. Open **Organization administration > Number sequences** menu. Create and set up number sequences for retail statements **per each store *(Scope = Operating unit)***. Add references to Statement number and Voucher for Retail store area.
1. Open **Retail and Commerce > Catalog and assortments** menu. Create new assortment(s) with needed products, and add the previously created stores under the **Commerce channels** tab, then press the publish button.
1. Open **Retail and Commerce > Channel setup > Channel categories and product attributes** menu. Publish channel updates.
1. Open **Sales and marketing > Setup > Returns > Disposition codes** menu. Add a disposition code.
1. Open **Retail and commerce > Products and categories > Released products by category** menu. Choose a product for gift card, and set on the **Blocked at register** checkbox.
1. Open **Commerce parameters** form, go to the **Customer orders** tab, and specify the **Disposition code** from the step above.
1. Swith to the **Posting** tab on the same form and set up the parameters for gift card, including **Gift card company** and **Gift card product**.


## Configuring a production environment
This section provides deployment guidance for enabling Commerce components of the localization of Dynamics 365 Commerce for Brazil.

> [!NOTE]
> Some steps in these procedures vary, depending on the product version you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

### Using certificates for authentication in tax authority service and digital signing of fiscal documents

A digital sertificate for Application Object Server (AOS) must be stored in Azure Key Vault. 

Digital sertificates for Retail Server must be installed locally and / or it can be stored in Azure Key Vault. Both location types for Retail Server can be configured simultaneously and used according to their priorities. 

For more information about how to work with Azure Key Vault storage, see [Get started with Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started) and [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

Also you can use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Headquarters are not available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

> [!NOTE]
> In order to sign NFC-es in offline contingency mode a sertificate must be installed in offline certificate storage of POS (point of sale).

#### Configure certificates to be used in Retail Server

Brazilian **tax service extension** of **Retail server** uses a certificate for authentication in tax authority service, and for digital signing of fiscal documents. 

**Retail server** certificates settings are controlled by **Certificate profiles** in the following way:
- Open **System administration > Setup > Certificate profiles** menu. 
- Create a certificate profile for the appropriate Legal entities. 
- Click on the 'Settings' button per each legal entity.

These certificates can be either installed in the local certificate storage of the machine where Retail Server is deployed, or stored in Azure Key Vault, or both location types for Retail Server can be configured simultaneously and used according to their priorities. The settings opened in the previous step must be specified as follows:
- for the local certificate create a record having **Location type = Local certificate**, and fill in the **Thumbprint** value;
- for Key Vault certificate create a record having **Location type = Key Vault**, and choose **Key Vault certificate**.

#### Configure a certificate in AOS

**Application Object Server** uses a certificate that is stored in Azure Key Vault for authentication in tax authority service for submittion through Commerce Headquarters NFC-es that were issued on POS in offline contingency mode. Also it is needed for digital signing of Discard and Cancellation by substitution requests. Parameters of the certificate must be specified in the following **Fiscal establishment settings**:

1. Open **Organization administration > Organizations > Fiscal establishments > Fiscal establishments**.
1. Choose the appropriate digital **certificate** for authentication in tax authority service and digital signing of fiscal documents.

    > [!NOTE]
    > Appropriate distribution jobs must be run once the setup is completed.

### CRT extension components

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
    > **Do not edit** the **Commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

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
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Cloud POS extension components

1. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate location.

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
