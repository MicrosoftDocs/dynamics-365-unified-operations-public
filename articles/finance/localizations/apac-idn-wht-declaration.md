---
# required metadata

title: Withholding tax report for Indonesia
description: This topic explains how to configure and generate the withholding tax report for Indonesia.
author: sndray
ms.date: 12/15/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: sndray
ms.search.validFrom: 2021-12-02
ms.dyn365.ops.version: 10.0.20
---

# Withholding tax report for Indonesia (ID-00005)

[!include [banner](../includes/banner.md)]

This topic explains how to set up and generate the PPH withholding tax file for legal entities in Indonesia to report withholding transactions in the e-Bupot application.

The Indonesia tax authority (DGT) determines that taxable entrepreneurs (PKP) registered at KPP Pratama as tax withholder/collector of income tax (PPh) Article 23 and/or Article 26 must report Income Tax Return Article 23 and 26 electronically by using the e-Bupot application. 

- Article 23: The report includes all withholding transactions from vendors where the country region code of the primary address is equal to Indonesia.
- Article 26: The report includes all withholding transactions from vendors where the country region code of the primary address is different from Indonesia.

## Prerequisites
The primary address of the legal entity must be in Indonesia.
In the **Feature management** workspace, the following feature must be enabled:

   - **Global withholding tax**

For more information about how to enable features, see [Feature management overview.](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)

### Download Electronic reporting configurations

Generating an import file is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in the topic, [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the import file, upload the following configurations from the repository:

- Tax declaration model.version.93.xml or later version.
- Tax declaration model mapping.version.93.153.xml or a later version.
- WHT PPh schema import (ID).version.93.14  or a later version.

## Set up General ledger parameters

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Withholding tax** tab, in the **WHT declaration format mapping** field, select **WHT PPh schema import (ID)**. 
3. Go to **Tax** > **Setup** > **Withholding tax** > **Withholding tax revenue types** to setup withholding tax revenue type **Kode Bukti Potong** and then assign these codes to the related item withholding tax groups. These codes are mandatory to generate the integration file with e-Bupot application. 

## Generate the withholding import file
The process of preparing and generating the e-bupot file for a specific period is based on the withholding tax transactions posted during the settle or post payment tax job. 
Complete the following steps to generate the file.

1. Go to **Tax** > **Declarations** > **Withholding tax** > **PPH import file e-bupot 23 and 26**.
2. Select the from date and to date for the report and then select the settlement period.
3. Enter the transaction date, and then select **OK**.
4. Select the language. All reports are translated in **en-us** and **id**.
5. Select the business type and then enter the check and document numbers. 
6. Check to see if the report is signed by the manager. This information is reported in the file. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]



