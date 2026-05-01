---
title: Set SPED EFD contributions
description: Learn how to set up parameters and generate the SPED EFD - Contributions statement for Brazil, including a step-by-step process for SPED FED requirements.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# Set SPED EFD contributions

[!include [banner](../../includes/banner.md)]

You generate the SPED EFD - Contributions statement in the **Fiscal books** module. It gathers information about social contribution tax on gross revenue for the Social Integration Program (PIS) and the Contribution for Social Security Financing (COFINS).

Follow these steps to set up the requirements for SPED EFD - Contributions text files.

1. Select **Fiscal books** > **Setup** > **Tax statements parameters**.
1. Select **EFD - Contributions**, and then, on the **Setup parameters** tab, select **Open**.

    The **EFD – Contributions parameters** page appears, where you can enter the required information for SPED EFD - Contributions text files.

1. In the **Type of activity** field, select the activity type:

    - Industrial or equivalent
    - Services
    - Retail
    - Financial activity
    - Real estate activity
    - Others

1. Set the **Large company** option to **Yes** to identify the size of company. This option is used in SPED REINF statements.
1. In the **Layout version** field, select the version of the SPED EFD layout. 
1. In the **Legal entity type** field, select the type of legal entity.
1. In the **Company type** field, select the type of company:

    - PJ in general
    - PJ member of financial system
    - Insurance or capitalization societies or open-ended complementary pensions funds

1. In the **Legal nature** field, enter the code for the legal nature, according to the SPED EFD table.
1. Set the **CPRB** option to **Yes** to enable CPRB tax assessment. This option is used in SPED REINF statements.
1. In the **Tax classification code** field, select the tax classification code. This field is used in SPED REINF statements.
1. Set the **International agreement for exemption of fines** option to **Yes**.
1. In the **Assessment regimen** field, select the assessment schema that is used for SPED EFD - Contributions:

    - **Non cumulative** – Calculate assessments based on billings or debits and purchases and deductions or credits.
    - **Cumulative** – Calculate assessments based on billings that don't have any deductions or credits.
    - **Both** – Calculate assessments based on both the **Non cumulative** and **Cumulative** regimens.

1. In the **Booking and assessment criteria** field, select the criteria to use to book the tax credit.
1. In the **Type of assessment contribution** field, select the type of assessment contribution.
1. In the **Credit allocation method** field, select the method of credit allocation:

    - Direct
    - Proportional distribution

    This field is available only if you selected **Non cumulative** or **Both** in the **Assessment regimen** field.

1. In the **NFe and ECF options** field, select the reporting option for NFe transactions:

    - **Consolidated** – Consolidate all NFe transactions into one record on the C18X fiscal report.
    - **Detailed** – List all individual transactions on the fiscal report.

1. On the **Fiscal establishment** tab, enter the required SPED ECD information.
1. On the **Rule for taxation code** tab, select the taxation code and fiscal value to prevent records C100 and D100 from being generated.

## Special requirements for layout version 006 and later

### Record 0900

The system automatically generates record 0900 in the SPED EFD - Contributions text files to provide details about the revenue composition for the specified booking period. You must generate this record when you transmit the original SPED EFD - Contributions file after the regular delivery time (that is, after the tenth working day of the second month of the booking period).

This record is available in layout version 006 and later. Select this option when you run the SPED EFD - Contributions file.

### M410 (PIS) and M810 (COFINS)

The system automatically generates records M410 and M810 in the SPED EFD - Contributions text files for revenue transactions where a fiscal value is set to **2:Exempt** or **3:without debit/credit**.

The implementation of layout version 006 changes the way that field 02 (**NAT\_REC**) is determined. This layout version uses an additional configuration. Previous layout versions use specific fixed values.

## Prerequisites

Before you generate PIS and COFINS tax assessments and enable the generation of records M410 and M810 that have the correct revenue source determination, go to **Fiscal books** > **Setup** > **PIS and COFINS tables** > **Revenue sources code**, and select the following parameters.

| Field | Description |
|---|---|
| Revenue source type | Select the type of revenue source, according to the relationship that is included in the tables that provide details about the nature of revenue by tax situation (for example, tables 4.3.10 and 4.3.11). The tax authority publishes these tables. |
| Revenue source code | Enter the code for the revenue source. |
| Description | Enter a description of the revenue source code. |
| Valid from and to date | Enter the dates when this revenue source is applicable. |

Go to **Fiscal books** > **Setup** > **PIS and COFINS tables** > **Revenue source per item** to set up the revenue source determination.

| Field | Description |
|---|---|
| Item code | Specify whether the revenue source determination applies to an item code, a group of items, or all items: **Table** – The source revenue applies to a single item code. If you select this option, select the item code in the **Item relation** field. **Group** – The source revenue applies to an item group. If you select this option, select the item group in the **Item relation** field. **All** – The source revenue applies to all items. If you select this option, leave the **Item relation** field blank. |
| Item relation | If you selected **Table** in the **Item code** field, select the item code that is associated with the revenue source. If you selected **Group**, select an item group. If you selected **All**, leave this field blank. |

## Generate a SPED EFD - Contributions text file

1. Go to **Fiscal books** > **Common** > **Booking period**.
1. Select the related booking period, and then select **Tax statements** > **EFD Contributions** > **Execute**.
1. In the **Type of situation** field, select the type of situation.
1. In the **File type** field, select **Original** or **Substitute**.
1. In the **Layout version** field, select the latest version that is available.
1. In the **Identification reason** field, select the related identification.
1. Set the **Late submission** option to **Yes** to generate record 0900.

> [!NOTE]
> To use batch processing, select **Batch**, and then specify the options for batch processing execution. Use batch processing if you want to generate the file later, or if you want to generate the file on a server instead of on your computer.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
