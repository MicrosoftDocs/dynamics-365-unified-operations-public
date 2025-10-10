---
title: Set up and generate a printed ledger posting report for Peru
description: Learn how to set up and generate a printed ledger posting report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 10/10/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate a printed ledger posting report for Peru

[!include [banner](../../includes/banner.md)]

This article shows how to set up and print the ledger posting report for Peru in Microsoft Dynamics 365 Finance.

The printed ledger posting report provides balance information for all ledger accounts, along with the transaction date, voucher, and journal description in a format suitable for printing.

## Prerequisites

Before generating and printing the report, complete the following prerequisites:
- Set the country/region of the legal entity's address to Peru. 
- Enable the Peru country/region-specific LATAM feature and the general LATAM feature.
- Download the report configurations from the Dataverse configuration repository:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Ledger accounting reports":::                               |
| Model / Mapping | :::no-loc text="Ledger Accounting LATAM"::: |
| Format  | :::no-loc text="Trial Balance (PE)":::                   |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).
- Configure the **Electronic Reporting (ER)** parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Create a new **SSRS Reports/Services reference** record, then follow these steps.
  
  1. In the **Report/Service Id** field, enter **PrintLPost**.
  1. In the **Report/Service name** field, enter **PrintLPost**.
  1. In the **Report/Service type** field, select an **ER configuration**.
  1. In the **Model mapping name** field, select **Ledger accounting LTM**.
  1. In the **Data model definition** field, select **LedgerPosting**.
1. In the **Format mapping field**, select the required ER format.
  1. In the **list of report/service types**, enable **Ledger Posting report**.

## Print the Ledger Posting report for Peru

To print the ledger posting report for Peru, follow these steps.
1. Go to **General Ledger > Inquiries and Reports > LATAM > Ledger Posting Report**.
1. In the **Ledger posting report** dialog box, set the filters for the report.
1. In the **Report ID field**, select the corresponding report or service ID.
1. In the **From date** and **To date fields**, select the date range of the transactions that you want to print.
1. To print transactions for a specific account, select the account number in the **Account number** field.
1. Select the posting layers.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]