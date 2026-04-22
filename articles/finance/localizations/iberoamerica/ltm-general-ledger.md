---
title: Printing configuration for General Ledger LATAM
description: Learn about the configuration that's required to print a general ledger report for Latin America, including a process for printing the general ledger report. 
author: Fhernandez0088
ms.author: v-mpizmeny
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Printing configuration for General Ledger LATAM

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

This article describes the steps that are required to set up and print the general ledger report for Latin America (**General Ledger LATAM**).

## Prerequisites

Before you print the general ledger report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- Download the specific report configurations from the Dataverse configuration repository. These formats are applicable to all LATAM countries, except Colombia and Peru

| Element |                    Format name                    | Country |
|:-------:|:-------------------------------------------------:|:---------------------------------------:|
| Model   | :::no-loc text="Ledger accounting reports":::    | All LATAM countries |
| Model   | :::no-loc text="Ledger Accounting LATAM":::  | All LATAM countries |
| Format  | :::no-loc text="General Ledger LATAM"::: | All LATAM countries |
| Format  | :::no-loc text="General Ledger CO"::: | Colombia |
| Format  | :::no-loc text="General Ledger PE"::: | Peru |

Learn more in [Import electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

- The SSRS Reports/Services references must be configured in the following way:

  - In the **Report/Service Id** field, enter **General Ledger**.
  - In the **Report/Service name** field, enter a descriptive name.
  - In the **Report/Service type** field, select an ER configuration.
  - In the **Model mapping name** field, select **:::no-loc text="Ledger Accounting":::**.
  - In the **Data model definition** field, select **:::no-loc text="GeneralLedger":::**.
  - In the **Format mapping** field, select **:::no-loc text="General Ledger LATAM":::**. (**:::no-loc text="General Ledger CO":::** for Colombia, **:::no-loc text="General Ledger PE":::** for Peru)
  - In the **Report/Service type** field, set the **General Ledger** option to **Yes**.

- You must have transactions that have been posted.

## Print the General Ledger LATAM report

Follow these steps to print the general ledger report for Latin America.

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **General Ledger**.
1. In the **General Ledger** dialog box, in the **Report Id** field, select **General Ledger**.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. Set the **Initial legal number** field.
1. Set the **Starting page** field.
1. Set the **Starting transport value** field to continue the accumulated sum.
1. Select the posting layer to include on the report.
1. Set the **Print customer/vendor** option to **Yes** to print information per transaction.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
