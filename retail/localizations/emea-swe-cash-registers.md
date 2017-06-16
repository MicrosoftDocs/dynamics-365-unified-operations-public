---
# required metadata

title: Cash registers for Sweden
description: This topic provides an overview of the cash register functionality that is available for Sweden. 
author: epopov
manager: annbe
ms.date: 07/1/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  RetailPosPermissionGroup, RetailFunctionalityProfile, RetailFormLayout, RetailHardwareProfile, RetailFiscalPrinterConfigTable
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Retail, Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Sweden
ms.search.industry: retail
ms.author: epopov
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---
# Cash registers for Sweden

This topic provides an overview of the cash register functionality that is available for Sweden in Microsoft Dynamics 365 for Retail. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:

- Common point-of sale (POS) features that are made available to customers in all countries or regions, such as an option to prevent sales and returns from being combined on one retail receipt
- Sweden-specific features, such as additional counters in daily POS reports
- A sample for integration of Dynamics 365 for Retail POS with Sweden-specific fiscal devices that are known as control units.

## Overview of cash register functionality for Sweden 

### Common POS features

To learn about common POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

Additionally, the following POS features that were implemented for Sweden have been made available to customers in all countries or regions:

- **Prohibit sales and returns from being combined on one retail receipt.** When you set the **Prohibit mixing sales and returns in one receipt** parameter in the POS functionality profile to **Yes**, Cloud POS and Modern POS won't let users create a transaction that contains both positive and negative lines.
- **Print text fields on the receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in a receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a receipt copy in large characters.
- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable the printing of receipt copies and other POS audit events to be registered. The audit events are registered in the channel database and in Retail headquarters. You can view the audit events on the **Audit events** page.
- **Prevent a copy of a receipt from being printed more than one time.** When the parameter **Audit** in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether receipt copies can be printed. There is also an option to prevent a copy of a receipt from being printed more than one time. 

### Sweden-specific POS features

The following Sweden-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **SE**:

- Additional counters on daily POS reports, such as X-reports and Z-reports:

    - Receipt copy count and total amount
    - Value added tax amounts per tax rate
    - Total quantities of items and services sold
    - Total sales excluding and including VAT
    - Grand total sales, returns, and net

- An **Electronic journal (Sweden)** channel report that lists continuous use events in the POS, such as sales, returns, receipt copies, drawer openings, and price overrides.

    > [!NOTE]
    > Currently, the **Electronic journal (Sweden)** report can't be exported or printed. However, functionality for exporting and printing the report will be added later.

### Integration of Retail POS with control units

Retail includes a sample for integration of POS with Sweden-specific fiscal devices that are known as control units. It's assumed that a control unit is physically connected to a Hardware station that POS is paired with. The sample is implemented as source code of POS, Hardware station, and Commerce runtime extensions, and is available in the Retail software development kit (SDK). The sample includes the following capabilities:

- Sales, returns, and receipt copies are automatically registered in a control unit that is connected to the Hardware station that is paired with the POS.
- The control code and the manufacturing number of the control unit for a registered transaction are captured from the control unit and saved in the transaction. (This data is also referred to as _fiscal data_.) The fiscal data can be viewed on the **Retail store transactions** page in Retail.
- Custom fields for the control code and the manufacturing number of the control unit can be added to a receipt format, so that you can print the fiscal data for the transaction on a receipt.
- The fiscal data for a transaction is printed on the **Electronic journal (Sweden)** channel report.
- If a failure occurs during the registration of a transaction in the control unit, the fiscal data for the transaction remains blank. In this case, a new transaction can't be started, and the current shift can't be closed. The operator will be asked to try to register the unregistered transaction again in the control unit. If the second attempt fails, the operator can skip the registration, provided that he or she has a special permission. If the operator skips the registration of a transaction in the control unit, information about this event is saved in the transaction instead of the fiscal data.

> [!NOTE]
> Currently, the control unit integration sample doesn't support customer orders. However, a sample that supports customer orders will be available later.

For more information about the control unit integration sample, see the [sample deployment guide](../dev-itpro/retail-sdk/retail-sdk-control-unit-sample.md).

## Setting up Retail for Sweden

This section describes the Retail settings that are specific to and recommended for Sweden. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the Sweden-specific functionality for Retail, you must complete these tasks:

- Set the **Country/region** field to **SWE** (Sweden) in the primary address of the legal entity.
- Set the **ISO code** field to **SE** (Sweden) in the POS functionality profile of every store that is located in Sweden.

Sweden-specific settings can be divided into two groups:

- General settings
- Control unit–specific settings

### General settings

You must specify the following general settings for Sweden.

1. Set up the following parameters for value-added tax (VAT) per Swedish requirements:

    - Sales tax codes
    - Sales tax groups
    - Item sales tax groups
    - Sales tax settings in items (item sales tax groups for sales)

    For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and in Retail, see [Sales tax overview](../../operations/financials/general-ledger/indirect-taxes-overview).

2. On the **All retail stores** page, update retail store details. Specifically, set the following parameters:
    
    - In the **Sales tax group** field, set the sales tax group that should be used for sales to the default retail customer.
    - Select the **Prices include sales tax** check box.
    - Set the **Store name** field so that it includes the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-format text.
    - Set the **Tax identification number (TIN)** field so that it includes the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-format text.

3. Set up POS functionality profiles:

    - On the **Functions** FastTab, select the **Audit** and **Prohibit mixing sales and returns in one receipt** check boxes.
    - On the **Receipt numbering** FastTab, set up receipt numbering. Create or update records for the **Sale** and **Return** receipt transaction types. Set the formats so that they include only numeric characters. Clear the **Independent sequence** check box in both records.

4. Update POS permissions groups and individual permission settings for store workers. Set the **Allow printing receipt copy** permission to an appropriate value:

    - **Allow always** – The operator can print a copy of a receipt multiple times.
    - **Allow only once** – The operator can print a copy of a receipt only one time.
    - **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the headquarters database is available through Real-Time service, so that the system can verify that no copies of the receipt have previously been printed in any store.
    - **Never** – The operator can't print a copy of a receipt.

5. Make the required changes to receipt formats for sales receipts:

    - Change the value of the **Print behavior** field to **Always print** for the receipt format.
    - In the Receipt format designer, make these changes:
    
        - Add at least the following fields to the **Header** section of the receipt layout:
        
            - **Store name** and **Tax Identification Number** fields, so that the company name and identity number are printed receipts. Alternatively, you can add the company name and identity number to the layout as free-format text.
            - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
            - **Reprint Message** field, so that the "Copy" indicator is printed on receipt copies. Set the **Font size** field for the **Reprint Message** field to **Large**.
    
        - Add at least the following field to the **Lines** section of the receipt layout: **Item name**, **Qty**, and **Total price with tax**.

        - Add at least the following fields to the **Footer** section of the receipt layout:

            - Tax fields, so that the receipt tax amounts for each tax rate are printed. For example, add the **Tax Id**, **Tax percentage**, and **Tax amounts** fields to one line of the layout.
            - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.

6. On the **Channel reports configuration** page, set up the **Electronic journal (Sweden)** report. In the  **Permission groups** field, select the POS permission groups that should be allowed to run the report.

### Control unit–specific settings

You must specify the following settings to enable the [integration sample](../dev-itpro/retail-sdk/retail-sdk-control-unit-sample.md), so that Retail POS is integrated with control units for Sweden.

1. Create fiscal register configurations, and assign them to hardware profiles:

    1. On the **Fiscal register configurations** page, create a new fiscal register configuration record. Set the name and the description of the configuration.
    2. Fill in the configuration content. For this sample, a configuration is an XML file that establishes the mapping between sales tax codes and a control unit's VAT groups. You can map up to four sales tax codes. In the following example of a configuration, **VAT10** and **VAT20** represent sales tax codes that must be mapped.

        ``` xml
        <UnitConfiguration>
            <TaxMapping>
                <Tax taxCode="VAT10" controlUnitTaxId="1"/>
                <Tax taxCode="VAT20" controlUnitTaxId="2"/>
            </TaxMapping>
        </UnitConfiguration>
        ```
        
        You can also export a sample configuration by clicking **Export sample configuration** on the Action Pane.

    3. On the **Hardware profiles** page, select the hardware profile of the Hardware station that the POS is paired with and the control unit is connected to. On the **Fiscal register** FastTab, set the following fields:

        - In the **Fiscal register** field, select **Third-party driver**.
        - In the **Configuration** field, select the name of the fiscal register configuration that you just created.

2. Set up custom fields for receipt layouts, so that the control code and the manufacturing number of the control unit are printed on receipts:

    1. On the **Language text** page, add two records for the captions of the custom receipt layout fields. In the appropriate fields, specify the language ID for the captions (for example, **sv-se**), the text ID (for example, **900001** and **900002**), and the caption text (for example, **Control code** and **Control unit ID**).
    2. On the **Custom fields** page, add two records for the custom receipt layout fields. In the **Type** field, select **Receipt**. Specify names and captions for the custom receipt layout fields:

        - Control code:

            - **Name:** **FiscalRegisterControlCode**
            - **Caption text ID:** The text ID that you specified for the control code field (**900001** in the preceding example)
            
        - Manufacturing number of the control unit:

            - **Name:** **FiscalRegisterId**
            - **Caption text ID:** The text ID that you specified for the control unit ID field (**900002** in the preceding example)
            
    3. For sales receipt formats, in the Receipt format designer, in the **Footer** section of the receipt layout, add the fields for the specified captions  (**Control code** and **Control unit ID** in the preceding example).

3. Update POS permissions groups and individual permission settings for store workers. To allow workers who are assigned to the permission group to skip the fiscal registration, select the **Allow skip fiscal registration** check box.
