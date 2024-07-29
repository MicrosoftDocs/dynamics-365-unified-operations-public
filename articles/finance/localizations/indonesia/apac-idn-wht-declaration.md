---
title: Withholding tax report for Indonesia
description: Learn how to configure and generate the withholding tax report for Indonesia, including an oultine on setting up general ledger parameters.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/10/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-12-02
ms.dyn365.ops.version: 10.0.20
---

# Withholding tax report for Indonesia (ID-00005)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the PPH withholding tax file that legal entities in Indonesia use to report withholding transactions in the e-Bupot application.

The Indonesia tax authority (DGT) determines that taxable entrepreneurs (PKP) that are registered at KPP Pratama as tax withholders/collectors of income tax (PPh) Article 23 and/or Article 26 must electronically report Income Tax Return Article 23 and 26 by using the e-Bupot application. 

- **Article 23** – The report includes all withholding transactions from vendors where the country/region code of the primary address is the code for Indonesia.
- **Article 26** – The report includes all withholding transactions from vendors where the country/region code of the primary address isn't the code for Indonesia.

## Prerequisites

- The primary address of the legal entity must be in Indonesia.
- In the **Feature management** workspace, the **Global withholding tax** feature must be enabled. For more information about how to enable features, see [Feature management overview.](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)

### Download Electronic reporting configurations

Generation of an import file is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the import file, upload the following configurations from the repository:

- **Tax declaration model.version.93.xml** or a later version
- **Tax declaration model mapping.version.93.153.xml** or a later version
- **WHT PPh schema import (ID).version.93.14**  or a later version

## Set up General ledger parameters

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Withholding tax** tab, in the **WHT declaration format mapping** field, select **WHT PPh schema import (ID)**. 
3. Go to **Tax** \> **Setup** \> **Withholding tax** \> **Withholding tax revenue types** to set up the **Kode Bukti Potong** withholding tax revenue type and then assign the codes to the related item withholding tax groups. The codes are required to generate the integration file by using the e-Bupot application. 

## Generate the withholding import file

The process of preparing and generating the e-Bupot file for a specific period is based on the withholding tax transactions that were posted during the settle or post payment tax job.

Follow these steps to generate the file.

1. Go to **Tax** \> **Declarations** \> **Withholding tax** \> **PPH import file e-bupot 23 and 26**.
2. Select the "from" date and "to" date for the report, and then select the settlement period.
3. Enter the transaction date, and then select **OK**.
4. Select the language. All reports are translated into US English (**en-us**) and Indonesian (**id**).
5. Select the business type, and then enter the check and document numbers. 
6. Check whether the report has been signed by the manager. This information is reported in the file. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
