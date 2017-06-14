---
# required metadata

title: Cash registers for Sweden
description: This topic provides an overview of the cash register functionality available for Sweden. 
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

This topic provides an overview of the cash register functionality available for Sweden in Microsoft Dynamics 365 for Retail, and guidelines on setting up the functionality. The functionality includes the following parts:

1. Common POS features that are made available to customers in all countries/regions, such as an option to prohibit mixing sales and returns in one retail receipt;

2. Sweden-specific features, such as additional counters in daily POS reports;

3. A sample for integration of Dynamics 365 Retail POS with Sweden-specific fiscal devices named control units.

## Overview of cash register functionality for Sweden 

### Common POS features

Please refer to [Microsoft Dynamics 365 for Retail documentation](../index.md) to learn common POS features available to customers in all countries/regions.

A few additional common POS features implemented for Sweden but made available to customers in all countries/regions include:

1. An option to prohibit mixing sales and returns in one retail receipt

    In order to prohibit mixing sales and returns in one retail receipt, set the POS functionality profile parameter **Prohibit mixing sales and returns in one receipt** to **Yes**. When the parameter is enabled, Cloud POS/Modern POS will not allow creating a transaction containing both positive and negative lines.

2. An option to print text fields in receipt with large-sized font

    You can use the Receipt format designer parameter **Font size** to specify that the large (~double) font size should be used for a field in a receipt format. This option may be used to print the copy indication in a receipt copy with large characters.

3. An option to register printing of receipt copies in the POS audit event log

    You can enable the registration of printing of receipt copies, as well as other POS audit events, via the **Audit** parameter in the POS functionality profile. The audit events are registered in the Channel DB and in the Dynamics 365 for Retail Headquarters and can be viewed on the **Audit events** page.

4. A POS permission to restrict printing of a receipt copy more than once

    When the POS functionality profile parameter **Audit** is enabled, the POS permission **Allow printing receipt copies** controls the possibility to print receipt copies, including the option to prohibit printing a copy of a receipt more than once. 

### Sweden-specific POS features

Sweden-specific POS features are enabled in POS when the POS functionality profile parameter **ISO code** is set to **SE**. The features include:

1. Additional counters in daily POS reports, such as X- and Z-reports. These counters include:

    - Receipt copy count and total amount;
    
    - Value added tax amounts per tax rate;

    - Total quantities of items and services sold;

    - Total sales excluding and including VAT;

    - Grand total sales, returns, and net.

2. The channel report Electronic journal (Sweden) that lists continuous use events in the POS, including sales, returns, receipt copies, drawer openings, price overrides, etc. 
    > [!NOTE] the report cannot be exported and/or printed. The functionality to export and/or print the Electronic journal (Sweden)    report will be made available later.

### Integration of Dynamics 365 Retail POS with control units

Microsoft Dynamics 365 for Retail includes a sample for integration of POS with Sweden-specific fiscal devices named control units. It is assumed that a control unit is physically connected to a Hardware station which POS is paired to. The example is implemented as a source code of POS, HW station and Commerce Run-Time extensions, and is available in Retail SDK. The sample includes the following capabilities:

  - Sales, returns, receipt copies are automatically registered in a control unit connected to the HW station paired with the POS;
  
  - The control code and the manufacturing number of the control unit for a registered transaction (further referred to as "fiscal data") are captured from the control unit and saved in the transaction. The fiscal data can be viewed in Dynamics 365 for Retail on the **Retail store transactions** page;
  
  - Custom fields for the control code and the manufacturing number of the control unit may be added to a receipt format to print the fiscal data for the transaction in a receipt;

  - The fiscal data for a transaction is printed in the channel report **Electronic journal (Sweden)**;

  - If a failure happens during the registration of a transaction in the control unit, the fiscal data for the transaction remains blank. In this case, it will not be allowed to start a new transaction or to close the current shift. The operator will be requested to re-try registering the un-registered transaction in the control unit. If the repeated attempt fails, the operator will be offered to skip the registration. Skipping the registration requires a special permission to be enabled. If the registration of a transaction in the control unit is skipped, the information about this event is saved in the transaction instead of the fiscal data.

> [!NOTE] customer orders are not supported by the sample for the integration. A sample for the control unit integration for customer orders will be available later.

You can find more information about the control unit integration sample in the [sample deployment guide](../dev-itpro/retail-sdk/retail-sdk-control-unit-sample.md).

## Setting up Dynamics 365 for Retail for Sweden

This section describes the Microsoft Dynamics 365 for Retail settings that are specific to and recommended for Sweden. Please refer to [Microsoft Dynamics 365 for Retail documentation](../index.md) for more details on setting up Dynamics 365 for Retail.

In order to use the Sweden-specific functionality of Dynamics 365 for Retail, you need to:

  - Set **Country/region** as **SWE** (Sweden) in the primary address of the legal entity;

  - Set **ISO code** as **SE** (Sweden) in the POS functionality profile(s) of store(s) located in Sweden.

Sweden-specific settings can be divided into two groups:

1. General settings

2. Control unit-specific settings

### General settings

The following settings need to be made for Sweden:

1. Set up VAT parameters according to Swedish requirements:

    - Sales tax codes;

    - Sales tax groups;

    - Item sales tax groups;

    - Sales tax settings in items (item sales tax groups for sales)

    Please refer to the [Sales tax overview](../../operations/financials/general-ledger/indirect-taxes-overview) page for more information on setting up and using sales tax in Dynamics 365 for Finance and Operations and Dynamics 365 for Retail. 

2. Update retail store details on the **All retail stores** page. In particular, set the following parameters:
    
    - Set the **Sales tax group** to be used for sales to the default retail customer;

    - Select the **Prices include sales tax** check-box;

    - Set the **Store name** to include the company name. This is needed to ensure the company name is present in a sales receipt. Alternatively, you can add the company name to the sales receipt layout as a free-format text.

    - Set the **Tax identification number (TIN)** to include the company identity number. This is needed to ensure the company identity number is present in a sales receipt. Alternatively, you can add the company identity number to the sales receipt layout as a free-format text.

3. Set up POS functionality profiles:

    - Select the **Audit** and **Prohibit mixing sales and returns in one receipt** check-boxes on the **Functions** fast-tab;

    -  Set up receipt numbering on the **Receipt numbering** fast-tab: create or update records for Receipt transaction types **Sale** and **Return**. Set the formats to include numeric characters only. Clear the **Independent sequence** check-box in both records.

4. Update POS permissions groups and individual permission settings for store workers:

    -  Set the **Allow printing receipt copy** permission to an appropriate value:

        - **Allow always** - If this permission is enabled, the operator will be allowed to print copies of a receipt multiple times;

        - **Allow only once** - If this permission is enabled, the operator will be allowed to print a copy of a receipt only once;

        - **Allow only once, and only if HQ DB is available** - If this permission is enabled, the operator will be allowed to print a copy of a receipt only once, and only if the Headquarters DB is available through the Real-Time service, and thus it is possible to verify that no copies of the receipt have been printed previously in any store;

        - **Never** - If this permission is enabled, the operator will not be allowed to print a copy of a receipt.

5. Make necessary changes to receipt formats for sales receipts:

    - Change **Print behavior** to **Always print** for the receipt format;
    
    - In the Receipt format designer:
    
        - Add at least the following fields to the **Header** section of the receipt layout:
        
            - **Store name** and **Tax Identification Number** fields, to print the company name and identity number in receipts. Alternatively, you can add the company name and identity number to the layout as free-format text;

            - **Store address**, **Date**, **Time 24H**, **Receipt Number**, **Register number**;
                    
            - **Reprint Message** field, to print the **Copy** indication in receipt copies. Set **Font size** for it to **Large**;
    
        - Add at least the following fields to the **Lines** section of the receipt layout:

            - **Item name**, **Qty**, **Total price with tax**;

        - Add at least the following fields to the **Footer** section of the receipt layout:

            - Add tax fields to print the receipt tax amounts per tax rate. For example, add the fields **Tax Id**, **Tax percentage**, and **Tax amounts** to one line of the layout;

            - Add payment fields to print the amounts of payments per payment method used. For example, add the fields **Tender name** and **Tender amount** to one line of the layout.

6. Set up the **Electronic journal (Sweden)** report on the **Channel reports configuration** page. In the  **Permission groups** field, select the POS permission groups that should be allowed to run the report.

### Control unit-specific settings

The following settings need to be made to enable the [sample for integration](../dev-itpro/retail-sdk/retail-sdk-control-unit-sample.md) of Dynamics 365 Retail POS with control units for Sweden:

1. Create fiscal register configurations and assign them to hardware profiles:

    - Create a new fiscal register configuration record on the **Fiscal register configurations** page; set the name and the description of the configuration.

    - Fill in the configuration content. For this sample, a configuration is an XML file that establishes the mapping between sales tax codes and control unit's VAT groups. You can map up to four sales tax codes. An example configuration can be found below; "VAT10" and "VAT20" stand for sales tax codes that need to be mapped. It is also possible to export a sample configuration by selecting **Export sample configuration** in the action pane.

        ``` xml
        <UnitConfiguration>
            <TaxMapping>
                <Tax taxCode="VAT10" controlUnitTaxId="1"/>
                <Tax taxCode="VAT20" controlUnitTaxId="2"/>
            </TaxMapping>
        </UnitConfiguration>
        ```
    
    - On the **Hardware profiles** page, select the hardware profile of the HW station, which the POS is paired to and the control unit is connected to, and set the following fields on the **Fiscal register** fast-tab:

        - Select **Third-party driver** in the **Fiscal register** field;

        - Select the name of the newly created fiscal register configuration in the **Configuration** field.

2. Set up custom fields of receipt layouts to print the control code and the manufacturing number of the control unit in receipts:

    - On the **Language text** page, add two records for the captions of the custom receipt layout fields. Specify the **Language ID** for the captions (e.g. "sv-se"), the **Text ID** (e.g. 900001 and 900002), and the caption **Text** (e.g. "Control code" and "Control unit ID");

    - On the **Custom fields** page, add two records for the custom receipt layout fields. Select **Receipt** in the **Type** field. Specify names and captions of the custom receipt layout fields:

        - Control code:

            - **Name** = **FiscalRegisterControlCode**;

            - **Caption text ID** = the Text ID specified for the control code field (900001 in the above example);
            
        - Manufacturing number of the control unit:

            - **Name** = **FiscalRegisterId**;

            - **Caption text ID** = the Text ID specified for the control unit ID field (900002 in the above example);
            
    - For sales receipt formats, add the fields with the specified captions to the **Footer** section of the receipt layout in the Receipt format designer ("Control code" and "Control unit ID" in the above example).

3. Update POS permissions groups and individual permission settings for store workers:

    -  Select the **Allow skip fiscal registration** check-box to allow workers who are assigned to the permission group to skip the fiscal registration. 
