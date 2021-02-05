---
# required metadata

title: Quarterly VAT communication report
description: This topic provides information about Quarterly VAT communication report in Italy.
author: LizaGolub
manager: AnnBe
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
---

# Quarterly VAT communication report

[!include [banner](../includes/banner.md)]

According to Legislative Decree no. 127/2015, article 1, and Decree Law 78/2010,
article 21, **Periodic VAT payment communication** (**Comunicazione IVA
periodica con prospetto di liquidazione, LIPE**) information must be transmitted
electronically in XML format to the Italian tax authorities.

## Set up the Quarterly VAT communication (LIPE) report

### Prerequisites

Before you set up the **Quarterly VAT communication (LIPE)** report, follow
these steps.

1.  Go to **Organization administration** \> **Organizations** \> **Legal
    entities**.

2.  On the **Registration numbers** FastTab, in the **Italy** section, in the
    **Fiscal code** field, enter your organization's fiscal code. (This code has
    between 11 and 16 digits.)

3.  On the **Tax registration** FastTab, in the **Tax exempt number** field,
    enter your organization's tax exempt number. (This number has 11 digits.)

### Create a number sequence

According to the requirements, the name of the **Quarterly VAT Communication
(LIPE)** report must consist of several components:

-   An International Organization for Standardization (ISO) 3166-1 alpha-2
    country code

-   An 11-character or 16-character tax code, followed by an underscore (_)

-   A file type (**LI**), followed by an underscore (_)

-   A five-character progressive number that consists only of lowercase letters
    a–z, uppercase letters A–Z, or numbers 0–9

Here are some examples:

-   ITAAABBB99T99X999W_LI_00001.xml

-   IT99999999999_LI_00002.xml

For the progressive number, a system number sequence is used. Go to
**Organization administration** \> **Number sequences** \> **Number sequences**,
and create a number sequence. This number sequence must be continuous and five
characters long, and it must be alphanumeric (that is, it must consist only of
lowercase letters a–z, uppercase letters A–Z, and numbers 0–9).

![Set up number sequence for Quarterly VAT Communication (LIPE) report](.media/num-seq.png)

Find more information about how to set up number sequences in [Set up number sequences](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-number-sequences) section.

### Import and update Electronic reporting configurations

1.  Import the latest versions of the following Electronic reporting (ER)
    configurations for the **Quarterly VAT communication** format.

| Configuration name                        | Type             | Description                                                                                                                             |
|-------------------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Italian tax reports model                 | Model            | The common data model for Italian tax reports.                                                                                          |
| Quarterly VAT Communication model mapping | Model mapping    | The model mapping for data collection from Microsoft Dynamics 365 Finance to the Italian **Quarterly VAT Communication (LIPE)** report. |
| Quarterly VAT Communication               | Exporting format | The ER format for the **Italian Quarterly VAT Communication (LIPE)** report in XML format.                                              |

For more information, see [Download ER configurations from the Global repository](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo).

>   **Important**

>   Be sure to import the most recent versions of these configurations. The
>   description of each version usually includes the number of the Microsoft
>   Knowledge Base (KB) article that explains the changes that were introduced
>   in that version.

2.  After all the ER configurations from the preceding table are imported, set
    the **Default for model mapping** option to **Yes** for the **Quarterly VAT
    Communication model mapping** configuration.

3.  Go to **Workspaces** \> **Electronic reporting**.

4.  Select **Italian tax report model** \> **Quarterly VAT Communication**, and
    then, on the Action Pane, select **Create configuration**.

5.  In the drop-down dialog box, select the **Derive from Name: Quarterly VAT
    Communication** option, enter a name and description for the new format, and
    then select **Create configuration**.

![Derive ER format to create the format for your company](.media/derive-er-format.png)

>   The new format includes all the fields and mapping from the original. In the
>   new format, you can make changes to meet your company's requirements.

6.  Select the new format, and then, on the Action Pane, select **Designer**.

    The **Format designer** page is divided into two parts. The left side shows
    a format structure (XML scheme), and the right side shows a data model
    (data).

    For more information about ER, see [Electronic reporting (ER) overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting?toc=/dynamics365/finance/toc.json))

>   Values for the following tags of the report are collected from tax
>   transactions that are posted in the system. The values consider the specific
>   tax codes that your company uses and the tax directions that are applicable
>   to your company's operations.

-   TotaleOperazioniAttive

-   TotaleOperazioniPassive

-   IvaEsigibile

-   IvaDetratta

    To set up tax codes for the report, on the **Format designer** page, on the
    **Mapping** tab, expand **Model** \> **AccountingData** \> **MonthlyData**,
    select the **ActiveVATOperations** node, and then select **Edit**.

![Edit formula for active VAT operations](.media/edit-formula-active-vat-operations.png)

7.  In the **'Calculated field' data source properties** dialog box, select
    **Edit formula**.

8.  Update the formula with the tax codes that your company uses and the tax
    direction that is applicable to your company's operations. Manually define
    the tax codes as string values. For the tax directions, select values from
    the **TaxDirection_Type** data source on the left side of the **Formula
    designer** page.

![Add your company's tax codes in formula designer](.media/formula-designer.png)

>   When the report is generated, the system will use the conditions that are
>   defined for the **ActiveVATOperations** node to calculate values for the
>   **TotaleOperazioniAttive** and **IvaEsigibile** tags of the report.

9.  When you've finished editing the formula, save your changes, close the
    **Formula designer** page, and select **OK** in the **'Calculated field'
    data source properties** dialog box.

10.  On the **Format designer** page, on the **Mapping** tab, expand **Model** \>
    **AccountingData** \> **MonthlyData**, select the **PassiveVATOperations**
    node, and then select **Edit**.

11.  In the **'Calculated field' data source properties** dialog box, select
    **Edit formula**.

12.  Update the formula with the tax codes that your company uses and the tax
    directions that are applicable to your company's operations, as you did for
    the **ActiveVATOperations** node, to define the conditions that the system
    will use calculate the values for the **TotaleOperazioniPassive** and
    **IvaDetratta** tags of the report.

13.  To specify the number sequence that the system should use for the
    progressive numbers that are included in the file name for the report file,
    on the **Format designer** page, on the **Mapping** tab, select **Add
    root**.

14.  In the drop-down dialog box, expand **Dynamics 365 for Operations**, and
    then select **Number sequence**.

![Add number sequence to your format](.media/add-num-seq.png)

15.  Enter a name, select the number sequence that you created earlier, and then
    select **OK** to create the number sequence.

![Specify a name for your number sequence in ER format](.media/num0seq-name.png)

16.  On the **Format designer** page, select **File** on the left side, and then,
    on the **Mapping** tab, select the **Edit** button (pencil symbol) for the
    **File name** field.

![Edit formula for name of the file with number sequence name](.media/file-name-edit.png)

17.  Update **"IT"&model.Frontispiece.FiscalCode&"_LI_00000"** with a formula
    that includes a link to the new number sequence:
    **"IT"&model.Frontispiece.FiscalCode&"_LI_"&LIPE_file_num**. Here,
    **LIPE_file_num** is the name that you gave to the number sequence. To add
    **LIPE_file_num** to the formula, click Add data source button. When you've
    finished, select **Save**.

![Edit formula for name of the file with number sequence name](.media/file-name-formula-designer.png)

18.  Save your changes in the ER format, and complete the configuration.
