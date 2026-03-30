---
title: Withholding tax report for Indonesia
description: Learn how to configure and generate the withholding tax report for Indonesia, including an outline on setting up general ledger parameters.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/17/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-12-02
ms.dyn365.ops.version: 10.0.20
---

# Withholding tax report for Indonesia

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the PPH withholding tax declaration in Excel format that legal entities in Indonesia use to report withholding transactions in the e-Bupot application.

The Indonesia tax authority (Direktorat Jenderal Pajak, DJP) determines that taxable entrepreneurs (PKP) who register at KPP Pratama as tax withholders or collectors of income tax (PPh) Article 23 and Article 26 must electronically report Income Tax Return Article 23 and 26 by using the e-Bupot application. 

- **BPPU** – The report includes all withholding transactions from vendors where the country/region code of the primary address is the code for Indonesia, Article 23/26(4) WHT.
- **BPNR** – The report includes all withholding transactions from vendors where the country/region code of the primary address isn't the code for Indonesia, Article 26 WHT.

## Prerequisites

- The primary address of the legal entity must be in Indonesia.
- In the **General ledger parameters** > **Withholding tax**, select the **Enable global withholding tax** checlbox.

### Download Electronic reporting configurations

Implementation of the WHT declaration for Indonesia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the latest version **WHT PPh schema import (ID)** ER format from the repository. This format is based on the **Tax declaration model** configuration and uses the **Tax declaration model mapping** configuration. Model and model mapping configurations are automatically imported. Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).

## Set up General ledger parameters

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Withholding tax** tab, in the **WHT declaration format mapping** field, select **WHT PPh schema import (ID)**. 
3. Go to **Tax** \> **Setup** \> **Withholding tax** \> **Withholding tax revenue types** to set up the **Kode Bukti Potong** withholding tax revenue type and then assign the codes to the related item withholding tax groups. The codes are required to generate the integration file by using the e-Bupot application. 

## Generate the withholding import file

The process of preparing and generating the e-Bupot file for a specific period is based on the withholding tax transactions that you post during the settle or post payment tax job.

Follow these steps to generate the file.

1. Go to **Tax** \> **Declarations** \> **Withholding tax** \> **Withholding tax declaration (Indonesia)**.
2. Select the start and end dates for the report, then select the settlement period.
3. Enter the transaction date, then select **OK**.
4. Select the language. All reports are translated into US English (**en-us**) and Indonesian (**id**).
5. Select the business type, then enter the check and document numbers. 
6. Check whether the manager signed the report. The file includes this information. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
