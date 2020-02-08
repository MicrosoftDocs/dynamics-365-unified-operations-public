---
# required metadata

title: Cash register functionality for Sweden
description: This topic provides an overview of the cash register functionality that is available for Sweden. 
author: EvgenyPopovMBS
manager: annbe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form:  RetailPosPermissionGroup, RetailFunctionalityProfile, RetailFormLayout, RetailHardwareProfile, RetailFiscalPrinterConfigTable
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Sweden
ms.search.industry: retail
ms.author: epopov
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---
# Cash register functionality for Sweden

[!include [banner](../includes/banner.md)]

This topic provides an overview of the cash register functionality that is available for Sweden in Dynamics 365 Commerce. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:

- Common point-of sale (POS) features that are made available to customers in all countries or regions, such as an option to prevent sales and returns from being combined on one receipt
- Sweden-specific features, such as additional counters in daily POS reports
- A sample for integration of POS with Sweden-specific fiscal devices that are known as control units.

## Overview of cash register functionality for Sweden

### Common POS features

To learn about common POS features that are available to customers in all countries or regions, see [Help resources for Dynamics 365 Retail](../index.md).

Additionally, the following POS features that were implemented for Sweden have been made available to customers in all countries or regions:

- **Prohibit sales and returns from being combined on one receipt.** When you set the **Prohibit mixing sales and returns in one receipt** parameter in the POS functionality profile to **Yes**, Cloud POS and Modern POS won't let users create a transaction that contains both positive and negative lines.
- **Print text fields on the receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in a receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a receipt copy in large characters.
- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable the printing of receipt copies and other POS audit events to be registered. The audit events are registered in the channel database and in Headquarters. You can view the audit events on the **Audit events** page.
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


   # [Retail 10.0.6 and earlier](#tab/retail-10-0-6)

  For more information about the integration with control units that is available in Retail versions up to and including Retail 10.0.6, see [Sample for POS integration with control units for Sweden (legacy)](./retail-sdk-control-unit-sample.md#overview-of-integration-with-control-units). 


   # [Retail 10.0.7 and later](#tab/retail-10-0-7)

  For more information about the control unit integration sample, see [Control unit integration sample for Sweden](./emea-swe-fi-sample.md).

---


## Setting up Commerce for Sweden

This section describes the settings that are specific to and recommended for Sweden. For more information, see [Help resources for Dynamics 365 Retail](../index.md).

To use the Sweden-specific functionality, you must complete these tasks:

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

    For more information about how to set up and use sales tax, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).


2. On the **All stores** page, update store details. Specifically, set the following parameters:

    - In the **Sales tax group** field, set the sales tax group that should be used for sales to the default customer.
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

   # [Retail 10.0.6 and earlier](#tab/retail-10-0-6)

  For more information about setting up and configuring the integration with control units that is available in Retail versions up to and including Retail 10.0.6, see [Sample for POS integration with control units for Sweden (legacy)](./retail-sdk-control-unit-sample.md#setting-up-integration-with-control-units). 

   # [Retail 10.0.7 and later](#tab/retail-10-0-7)

  For more information about setting up and configuring the control unit integration sample, see [Control unit integration sample for Sweden](./emea-swe-fi-sample.md#setting-up-the-integration-with-control-units).

---

    

