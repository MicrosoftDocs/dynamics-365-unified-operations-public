---
# required metadata

title: Tax plafond
description: Tax plafond.
author: ilkond
manager: AnnBe
ms.date: 11/13/2019
ms.topic: article
ms.prod: plafond
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.9

---

# Tax plafond

[!include [banner](../includes/banner.md)]

Tax plafond is a tax-exemption process that allows companies, usually exporters, to purchase and import goods and services without paying sales tax within a limit value of their sales to foreign countries in the previous period. 
A company is a "usual exporter" when, in the previous year, 10 percent of the company's revenue value came from selling to a foreign country. To support that, the initial plafond amount and its validity dates are established at the beginning of the period. 
The company can buy without paying sales tax until the purchases value is below the initial plafond.

This topic describes how to:
 - Set up the system to use **Tax plafond** feature;
 - Work with **Tax plafond** and **Intent letter**;
 - Report Tax payments including tax plafond information.


## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Tax plafond** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up parameters
### Set up Accounts payable parameters

In **Accounts payable** > **Setup** > **Accounts payable parameters** > **Number sequences** FastTab, specify number sequences for:
 - Plafond number;
 - Intent letter number.

In **Accounts payable** > **Setup** > **Accounts payable parameters** > **Intent letters - Telematic model** FastTab, specify the reference to Intent letter telematic model configuration.

![Intent letter telematic model](media/emea-ita-exil-plafond-model.jpg)

> [!NOTE] The configuration must be preliminary imported in **Electronic reporting**. For more information about how to download ER configurations
see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs)

In **Accounts payable** > **Setup** > **Accounts payable parameters** > **Ledger and sale tax** FastTab, in the **Sales tax** section, specify **Plafond tax group** and **Default plafond date** parameters.

![Planond parameters](media/emea-ita-exil-plafond-group.jpg)

### Set up General ledger parameters

In **General ledger** > **Ledger setup** > **General ledger parameters** > **Number sequences** FastTab, specify the number sequence for **Intent letter telematic model ID**.

### Set up sales tax codes

In **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax code** \> **General** FastTab, in the **Invoicing** section, set the **Affect intent letters** option to **Yes**.

![Setting up a sales tax code](media/emea-ita-exil-intent-tax-setup.jpg)

## Create tax plafond

To register a new tax plafond, go to **Tax** > **Indirect taxes** > **Sales tax** > **Tax plafond**, on the Action pane, сlick **Functions** > **Create new** and fill in the fields for the tax plafond.

Tax plafond fields description:

| **Field name**                                                 | **Description**                                                                                                                                                                               |
|----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Plafond number**                                             | The number of the tax plafond. This value is auto-filled according to Number sequence defined for Plafond number reference in Accounts payable parameters.                                        |
| **Description**                                                | The description of the tax plafond, specified manually.                                                                                                                                    |
| **From date**                                                  | Start date of the period in which the tax plafond is effective.                                                                                                         |
| **To date**                                                    | End date of the period in which the tax plafond is effective.                                                                                                              |
| **Closed date**                                                | Auto-filled date when the tax plafond is closed.                                                                                                                                                  |
| **Initial plafond amount**                                     | Enter the amount of the tax plafond.                                                                                                                                                |
| **Initial current amount**                                     | Auto-calculated amount available on tax plafond.                                                                                                                                              |
| **Plafond warning type, amount, %.**                           | The type of check and related amount or percentage starting from which user will get warning about the tax plafond remaining amount . |
| **Settlement period**                                          | Specify the settlement period.                                                                                                                                  |
| **Operations contributing to the plafond** | Turn on/off the options for inclusion into intent letters report.                                                                                                                                            |

To review posted tax transactions for an existing tax plafond, on the Action pane, click **Plafond transactions**.

## Create intent letters

1. To create new intent letter for a vendor, go to **Accounts payable** > **Intent letters** > **Intent letters**, on the Action pane, сlick **New** and fill in the fields for the intent letter.

| **Field name**   | **Description**                                                          |
|------------------|--------------------------------------------------------------------------|
| **Posting date** | Specify posting date for the intent letter.                              |
| **Letter type**  | Select “Amount” or “Specific operation” type for the intent letter.      |
| **From date**    | Specify starting date of the period in which intent letter is effective. |
| **To date**      | Specify end date of the period in which intent letter is effective.      |
| **Amount**       | Specify amount for intent letter.                                        |

2. In **Records to include** FastTab, select vendors for which intent letters must be created using **Filter** button.

3. Click **OK** button to finalize the selection.

4.	On the next form, select **Update existing purchase orders** if you want to apply new intent letters to existing but not invoiced purchase orders for the selected vendors.

5.	Select **Re-confirm purchase orders** if you want to re-confirm purchase orders for which intent letters are applied in case they were confirmed.

6.	Select **Exclude delivered or partly delivered purchase orders** if you want to exclude delivered or partly delivered purchase orders from the list of purchase orders to be updated with intent letters.

7.	Click **OK** button to create intent letters with specified parameters.

> [!NOTE] Created intent letters are numbered automatically by the system according to the related number sequence defined for in **Accounts payable parameters**.

On **General** tab, for the created intent letters you can additionally specify the values for fields for generation of the telematic model:

| **Field name**    | **Description**                                                                                                                                                                                                                       |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **Model ID**        | Identification of the telematic model in which the letter was included. The system assigns the number according to the Number sequence specified for **Intent letter telematic model ID** reference in **General ledger parameters.** |
|   **Purchase type**   | Select type of purchase: purchases or exposures.                                                                                                                                                                                  |
> [!NOTE] **Period** type of intent letters is not supported. Creation of intent letters of this type is prevented. **Period** type itself is kept for historical data of those users which were using this type in the past as well as the **Automatic intent letter assignment** parameter on **Ledger and sales tax** Tab of **Accounts payable parameters**.

## Work with intent letters

Intent letters created for vendors can be applied to purchase orders or vendor invoice journal before invoice posting.

To apply an intent letter to a purchase order or vendor invoice journal, select the intent letter in the **Intent letter number** field of the related purchase order or vendor invoice journal. 
**Sales tax group** specified in **Plafond tax group** field of **Accounts payable parameters** will be automatically filled for the purchase order or vendor invoice journal.

![Purchase order](media/emea-ita-exil-plafond-PO.jpg)

You can also review intent letters for a specific vendor from vendor master data. 
Go to **Accounts payable** \> **Vendors** \> **All vendors**, in **Vendor** Tab, on the Action Pane, **Related information** section, click **Intent letters** to see intent letters related to the selected vendor.

## Generation of telematic model for intent letters

To generate telematic model of an intent letter, complete the following steps:

1.  Open **Tax** \> **Declarations** \> **Sales tax** \> **Intent letters – Telematic model** page, on the Action pane, click **New** to create a new record for telematic model reporting. Model ID is defined automatically according to the number sequence specified for **Intent letter telematic model ID** reference in **General ledger parameters**.

2.  Specify **Internal description** for the new telematic model in the related field.

3.  Fill in related information the tab **General** tab for the new telematic model about signatory, writer, integrative parameters and the file name.

4.  On the Action pane, click **Transfer**, select the intent letters to include in the current model.  Selected intent letters will be shown in **Intent letters** FastTab. 
> [!NOTE] Intent letters which are already included in other models can’t be selected.

5.  On the Action pane, click **Export** to generate the **Intent letter telematic model** output file.

