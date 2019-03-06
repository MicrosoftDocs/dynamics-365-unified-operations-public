---

# required metadata

title: Fiscal registration service integration sample for Austria
description: This topic provides an overview of the fiscal integration sample for Austria.
author: josaw
manager: annbe
ms.date: 03/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria
ms.search.industry: Retail
ms.author: v-dmpere
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---
# Fiscal registration service integration sample for Austria

[!include[banner](../includes/banner.md)]

## Introduction

The Microsoft Dynamics 365 for Retail functionality for Austria includes a sample of integration of POS with an external fiscal registration service to cover local fiscal requirements to cash registers in Austria. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It is based on the [EFR (Electronic Fiscal Register)](http://efsta.org/sicherheitsloesungen/) solution from [EFSTA](http://efsta.org/) and enables the communication with the EFR service via the HTTPS protocol. The EFR service should be hosted on the Retail Hardware station or a separate machine that can be connected from the Hardware station. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](http://efsta.org/kontakt/).

## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for Austria:
   - Registration of cash transactions in the fiscal register service:
      - Send detailed transaction data, including sales line information, discounts, payments, and taxes, to the fiscal register service.
      - Capture a response from the fiscal register service including a digital signature and a link to the registered transaction.
      - Print the tax decomposition and the QR-code for a registered transaction in the receipt.
  - Registration of gift card operations and customer deposits in the fiscal register service as non-cash transactions:
      - Issue / Add to a Gift card.
      - Register a customer account deposit.
      - Register a customer order deposit.
  - Registration of non-sales transactions and events in the fiscal register service as non-cash transactions:
      - Open / Close shift;
      - Start amount / Float entry / Tender removal;
      - Price override;
      - Tax override;
      - Print copy of receipt;
      - Open drawer;
      - Print X report;
      - Print Z report.
  - Printing of end of day statements (X/Z reports) with Austria-specific fields:  
      - Total number of products or services delivered to customers;
      - Breakdown of sales by tax rate;
      - Breakdown of payments by cashier/cash register operator;
      - Price discounts and returns that reduce daily sales;
      - Zero sales (giveaways).
  - Error handling, such as the following options:
      - Retry fiscal registration if a retry is possible, such as if the fiscal register service isn't available, isn't ready or isn't responding.
      - Postpone fiscal registration.
      - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
      - Check availability of the fiscal register service before opening a new sales transaction or finalizing a sales transaction.    - 

### Gift cards handling

The fiscal registration service integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from a cash transaction to be registered in the fiscal register service and register them as a separate non-cash transaction.
- Don't print a tax group breakdown and a QR-code in a receipt if it consists only of gift card lines.
- Print the total amount of gift cards that are issued or re-charged in a transaction separately from the cash transaction amount in the receipt.
- Save calculated adjustments of payment lines in the channel database with a reference to a corresponding fiscal transaction.
- Payment by gift card is considered a regular payment.

### Customer deposits and customer order deposits

The fiscal registration service integration sample implements the following rules that are related to customer deposits and customer order deposits:

- Register a non-cash transaction if a transaction is a customer deposit.
- Register a non-cash transaction if a transaction contains only a customer order deposit or a customer order deposit refund.
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
- Save calculated adjustments of payment lines in the channel database with a reference to a fiscal transaction for a hybrid customer order.

## Set up Retail for Austria

This section describes the Retail settings that are specific to and recommended for Austria. To use the Austria-specific functionality for Retail, you must complete these tasks:
- Set the **Country/region** field to AUT (Austria) in the primary address of the legal entity;
- Set the **ISO code** field to AT (Austria) in the POS functionality profile of every store that is located in Austria.

Austria-specific settings can be divided into two groups:
- General settings
- EFR–specific settings

### General settings

You must specify the following general settings for Austria:
1. Set up the following parameters for value-added tax (VAT) per Austria requirements:
    - Sales tax codes;
    - Sales tax groups;
    - Item sales tax groups;
    - Sales tax settings in items (item sales tax groups for sales).

For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations and in Retail see [Sales tax overview](https://docs.microsoft.com/dynamics365/unified-operations/financials/general-ledger/indirect-taxes-overview).

2. On the **All retail stores** page, update retail store details. Specifically, set the following parameters:
    - In the **Sales tax group** field, set the sales tax group that should be used for sales to the default retail customer.
    - Select the **Prices include sales tax** check box.
    - Set the **Store name** field so that it includes the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-format text.
    - Set the **Tax identification number (TIN)** field so that it includes the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-format text.

3. Set up POS functionality profiles:
    - On the **Receipt numbering** FastTab, set up receipt numbering. 
    - Create or update records for the **Sale**, **Sales order** and **Return** receipt transaction types.

4. Make the required changes to **Receipt formats**:
    - Change the value of the **Print behavior** field to **Always print** for the receipt format.
    - In the Receipt format designer, make these changes:
        - Add at least the following fields to the **Header** section of the receipt layout:
            - **Store name** and **Tax Identification Number** fields, so that the company name and identity number are printed receipts. Alternatively, you can add the company name and identity number to the layout as free-format text.
            - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
    - Add at least the following field to the **Lines** section of the receipt layout: **Item name**, **Qty**, **Total price with tax**.
    - Add at least the following fields to the **Footer** section of the receipt layout:
        - Tax fields, so that the receipt tax amounts for each tax rate are printed. For example, add the **Tax Id**, **Tax percentage**, and **Tax amounts** fields to one line of the layout.
        - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.

### EFR–specific settings

Before starting to define EFR-specific settings please be aware that all steps from the document **Deployment guidelines for cash registers for Austria** were done.

1. Cofigure VAT rates mapping:
The **VAT rates mapping** is included in the **Fiscal connector functional profile** provided as part of the fiscal integration sample:

    A: 20.00; B: 10.00; C: 13.00; D: 0.00; E: 19.00; F: 7.00

Check default mapping rates values and correct it if is is nessesary.

2. Set up tax group code for printing in receipt:
For printing tax group code in receipt (for example, “A”, “B”) field **Print code** must be filled for sales taxes in **Sales tax codes** form.

3. Set up custom fields and receipt formats as described below.

#### Set up custom fields for receipt format

Configure custom fields so that they can be used in receipt formats for sales receipts:
You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the Language ID, Text ID, and Text values that are shown in the table are just examples. You can change them to meet to your requirements. However, the Text ID values that you use must be unique, and they must be equal to or higher than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text Id | Text                      |
|-------------|---------|---------------------------|
| en-US       | 103174  | QR Code                   |
| en-US       | 103175  | Continuous Number         |
| en-US       | 103176  | Tax Retail Print Code     |
| en-US       | 103177  | Total (sales)             |
| en-US       | 103178  | Total Tax (sales)         |
| en-US       | 103179  | Total Include Tax (sales) |
| en-US       | 103180  | Tax Amount (sales)        |
| en-US       | 103181  | Tax Basis (sales)         |

Note: data records of **Language text** should be added to current company and DAT company.

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                 | Type    | Caption text Id |
|----------------------|---------|-----------------|
| QRCODE               | Receipt | 103174          |
| CONTINUOUSNUMBER     | Receipt | 103175          |
| RETAILPRINTCODE      | Receipt | 103176          |
| SALESTOTAL           | Receipt | 103177          |
| SALESTOTALTAX        | Receipt | 103178          |
| SALESTOTALINCLUDETAX | Receipt | 103179          |
| SALESTAXAMOUNT       | Receipt | 103180          |
| SALESTAXBASIS        | Receipt | 103181          |

#### Receipt format configurations

In the **Receipt format designer**, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

   **Header**: 
      Continuous Number. This field identifies the number of cash transaction in the fiscal registrator;
      
   **Lines**:
      Tax Retail Print Code. This field dysplays the code corresponding to the tax group;
      
   **Footer**: 
      Fileds group **Sales total**: 
      	Total (sales) - total transaction amount without tax sum;
	Total Include Tax (sales) - total transaction amount with tax sum;
        Total Tax (sales) - transaction tax sum.	
      **Tax break down** (should be separate line):
	Tax Basis (sales) - total cash transaction amount (without taxes) excluding deposits, prepayments and gift cards;
	Tax Amount (sales) - total tax amount for cash transactions excluding deposits, prepayments and gift cards;
	Total Include Tax (sales) - total cash transaction amount (with taxes) excluding deposits, prepayments and gift cards;
	Tax Retail Print Code - the code corresponding to tax group.		
      **QR Code**: 
         QR Code - reference to registered cash transaction in the form of QR-code.
      
5. Update POS permissions groups and individual permission settings for store workers. To allow workers who are assigned to the permission group to skip the fiscal registration, select the **Allow skip fiscal registration** check box (not recommended). 

## Deployment guideline for cash registers for Austria

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 for Retail localization for Austria. The localization consists of several extensions of Retail components. For example, the extensions let you print custom fields on receipts, register additional audit events, includes samples of the integration with the EFSTA System and
Electronical Fiscal Register Software. 

Integration samples were developed based on the fiscal integration framework. For details about the fiscal integration functionality, see [Fiscal integration for Retail channel](fiscal-integration-for-retail-channel.md), these samples are part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This localization consists of extensions for the Commerce runtime (CRT), Hardware station, and POS. To run this sample, you must modify and build the CRT, Hardware station, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### Enable Commerce runtime extensions

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### DocumentProvider.EFRSample component

1. Find the **Runtime.Extensions.DocumentProvider.EFRSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.EFRSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
    ```

#### DocumentProvider.DataModelEFR component

1. Find the **Runtime.Extensions.DocumentProvider.DataModelEFR** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.DataModelEFR\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
    ```
#### Update extension configuration file

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
    ```

### Enable Hardware station extensions

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

#### Modern POS extension components

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

#### Cloud POS extension components

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

### Set up the registration process

To enable the registration process, set up Retail Headquarters using the steps below. For more details, see [How to set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md).

1. Open **Retail shared parameters** and enable **Fiscal integration** on the **General** tab.

2. Open **Retail > Channel setup > Fiscal integration > Fiscal connectors** menu. Load connector configuration from RetailSdk. The file is located under SampleExtensions\HardwareStation\Extension.EFRSample\Configuration\ConnectorEFRSampleAustria.xml.

3. Open **Retail > Channel setup > Fiscal integration > Fiscal document providers** menu. Load documment provider configurations from RetailSdk.

Configuration files are located under SampleExtensions\CommerceRuntime\Extensions.DocumentProvider.EFRSample\Configuration
    - DocumentProviderEFRSampleAustria.xml
    - DocumentProviderNonFiscalEFRSampleAustria.xml

4. Open **Retail > Channel setup > Fiscal integration > Connector functional profiles**. Create two new profiles per document provider from step above and select the loaded connector. Update data mapping settings if needed.

5. Open **Retail > Channel setup > Fiscal integration > Connector technical profiles**. Create a new profile and select the loaded connector from the step above. Update connection settings if needed.

6. Open **Retail > Channel setup > Fiscal integration > Fiscal connector group**. Create two new group per connector's functional profile from the step above.

7. Open **Retail > Channel setup > Fiscal integration > Registration process**. Create a new process. Select both connector's functional groups from the step above.

7. Open **Retail > Channel setup > POS setup > POS profiles > Functionality profiles**. Select one that is linked to the store where the registration process should be activated. Expand the **Fiscal registration process** tab. Select the created registration process from the step above. For enabling registration of non-fiscal events on POS enable **Audit** prorerty at **Functions** fasttab.

8. Open the **Retail > Channel setup > POS setup > POS profiles > Hardware profiles**. Select one that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** Tab. Select the connector technical profile.

### Setting up a production environment

Follow these steps to create deployable packages that contain Retail components, and to apply those packages in a production environment.

1. Complete the steps in the [Cloud POS extension components](#cloud-pos-extension-components) or [Modern POS extension components](#modern-pos-extension-components) section earlier in this topic.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EFRSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventAustria" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsAustria" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following lines to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.EFRSample" />
        ```

3. Make the following changes in the **BuildTools\Customization.settings** package customization configuration file:

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.EFRSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.DataModelEFR.dll" />
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.EFRSample" />
        ```

4. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.

5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create retail deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

6. Complete all necessary settings from the [Set up Retail for Austria](#set-up-retail-for-austria).

## Limitations of the sample

  - The fiscal printer supports only scenarios where sales tax is included in the price. Therefore, the Price include sales tax option must be set to Yes for both retail stores and customers.
