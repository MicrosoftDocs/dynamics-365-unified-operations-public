---
# required metadata

title: Control unit integration sample for Sweden
description: This topic provides an overview of the fiscal integration sample for Sweden.
author:
manager: annbe
ms.date: 10/08/2019
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
ms.search.region: Sweden
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: 10.0.7

---
# Control unit integration sample for Sweden

[!include [banner](../includes/banner.md)]

## Introduction


This topic provides an overview of the cash register functionality that is available for Sweden in Dynamics 365 Retail. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:
  - Common point-of sale (POS) features that are made available to customers in all countries or regions, such as an option to prevent sales and returns from being combined on one retail receipt.
  - A Sweden-specific channel report.
  - A sample of integration with Sweden-specific fiscal devices called control units. 


## Scenarios

### Common POS features

To learn about common POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

Additionally, the following POS features that were implemented for Sweden have been made available to customers in all countries or regions:

- **Prohibit sales and returns from being combined on one retail receipt.** When you set the **Prohibit mixing sales and returns in one receipt** parameter in the POS functionality profile to **Yes**, Cloud POS and Modern POS won't let users create a transaction that contains both positive and negative lines.
- **Print text fields on the receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in a receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a receipt copy in large characters.
- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable the printing of receipt copies and other POS audit events to be registered. The audit events are registered in the channel database and in Retail headquarters. You can view the audit events on the **Audit events** page.
- **Prevent a copy of a receipt from being printed more than one time.** When the parameter **Audit** in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether receipt copies can be printed. There is also an option to prevent a copy of a receipt from being printed more than one time.


### Electronic journal (Sweden) report

An **Electronic journal (Sweden)** channel report that lists continuous use events in the POS, such as sales, returns, receipt copies, drawer openings, and price overrides. 

This report is a country-specific, so it's avaialbale only when the **ISO code** parameter in the POS functionality profile is set to **SE**.


### Integration with control units

Control unit is a Sweden-specific fiscal device. It's assumed that a control unit is physically connected to a Hardware station that POS is paired with. A sample of integration with 
The Control unit integration sample for Sweden extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and includes the following capabilities:

  - Support of Sweden-specific requirements for transactions registered on POS:
    - Sales, returns, and receipt copies are automatically registered in a control unit that is connected to the Hardware station that is paired with the POS.
    - The control code and the manufacturing number of the control unit for a registered transaction are captured from the control unit and saved in the transaction. (This data is also referred to as _fiscal data_.) The fiscal data can be viewed on the **Retail store transactions** page.
    - Custom fields for the control code and the manufacturing number of the control unit can be added to a receipt format, so that you can print the fiscal data for the transaction on a receipt.
    - The fiscal data for a transaction is displayed in the **Electronic journal (Sweden)** channel report. 

  - Support of Sweden-specific additional counters in daily reports (X and Z):
    - Receipt copy count and total amount,
    - Value added tax amounts per tax rate,
    - Total quantities of items and services sold,
    - Total sales excluding and including VAT,
    - Grand total sales, returns, and net grand total.


#### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is distributed as a part of the fiscal integration sample.

- **Value-added tax (VAT) code mapping** sets rescpective device-specific VAT codes to sales tax codes. VAT code mapping should have the following format:

1 : code1 ; 2 : code2

Where 
1, 2, etc. - device-specific VAT codes,
";" - separator,
code1, code2 - sales tax codes, that were set up in the system.

Control units support up to 4 different VAT code, so VAT code mapping may be set up as shown below:

1 : code1 ; 2 : code2 ; 2 code3 ; 3 : code4 ; 4 : code5   


#### Limitations of the sample

  - Customer order scenarios are not supported in the Control unit integration sample for Sweden for now. 
  - Export and printing of **Electronic journal (Sweden)** channel report is not supported in the current design.  


## Set up Retail for Sweden

This section describes the settings that are specific to and recommended for Sweden. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the Sweden-specific functionality, you must complete these tasks:

- Set the **Country/region** field to **SWE** (Sweden) in the primary address of the legal entity.
- Set the **ISO code** field to **SE** (Sweden) in the POS functionality profile of every store that is located in Sweden.


### Set up VAT 

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md)..


### Set up retail stores

On the **All retail stores** page, update retail store details. Specifically, set the following parameters:

  - In the **Sales tax group** field, set the sales tax group that should be used for sales to the default retail customer.
  - Select the **Prices include sales tax** check box.
  - Set the **Store name** field so that it includes the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-format text.
  - Set the **Tax identification number (TIN)** field so that it includes the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-format text.


### Set up functionality profiles

Set up POS functionality profiles:

  - On the **Functions** FastTab, select the **Audit** and **Prohibit mixing sales and returns in one receipt** check boxes.
  - On the **Receipt numbering** FastTab, set up receipt numbering. Create or update records for the **Sale** and **Return** receipt transaction types. Set the formats so that they include only numeric characters. Clear the **Independent sequence** check box in both records.


### Set up POS permissions

Update POS permissions groups and individual permission settings for store workers. Set the **Allow printing receipt copy** permission to an appropriate value:

  - **Allow always** – The operator can print a copy of a receipt multiple times.
  - **Allow only once** – The operator can print a copy of a receipt only one time.
  - **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the headquarters database is available through Real-Time service, so that the system can verify that no copies of the receipt have previously been printed in any store.
  - **Never** – The operator can't print a copy of a receipt.


### Set up the Electronic journal (Sweden) report

On the **Channel reports configuration** page, set up the **Electronic journal (Sweden)** report. In the  **Permission groups** field, select the POS permission groups that should be allowed to run the report.

### Set up receipts

Make the required changes to receipt formats for sales receipts:

  - Change the value of the **Print behavior** field to **Always print** for the receipt format.
  - In the Receipt format designer, make these changes:

    - Add at least the following fields to the **Header** section of the receipt layout:

      - **Store name** and **Tax Identification Number** fields, so that the company name and identity number are printed receipts. Alternatively, you can add the company name and identity number to the layout as free-format text.
      - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
      - **Reprint Message** field, so that the "Copy" indicator is printed on receipt copies. Set the **Font size** field for the **Reprint Message** field to **Large**.


#### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                   |
|-------------|---------|------------------------|
| en-US       | 900001  | Register control code  |
| en-US       | 900002  | Register device        |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                           | Type    | Caption text ID |
|--------------------------------|---------|-----------------|
| SE_FISCALREGISTERCONTROLCODE   | Receipt | 900001          |
| SE_FISCALREGISTERID            | Receipt | 900002          |


#### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Footer:** Add the following fields.

    - **Register control code**: this field prints the control code.
    - **Register device**: this field prints the manufacturing number of the control unit.

For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).


### Configure fiscal integration

#### Set up the registration process

To enable the registration process, follow these steps to set up Retail Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail \> Headquarters setup \> Parameters \> Retail shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.CleanCashSample\\Configuration\\ConnectorCleanCashSample.xml**.
3. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The configuration file is  **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.CleanCashSample\\Configuration\\DocumentProviderFiscalCleanCashSample.xml**.
4. Go to **Retail \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
6. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group, for the connector functional profile that you created earlier.
7. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail \> Retail IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.


#### Error handling settings

Complete setup steps, that define system behavior and available options in case of an error occured during the fiscal registration, following the insrtuctions:
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
