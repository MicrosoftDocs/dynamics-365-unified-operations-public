---
title: Standard Audit File for Tax (SAF-T) electronic report
description: This article explains how to generate the Standard Audit File for Tax (SAF-T) electronic report in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.date: 06/20/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.author: atrukawk
ms.search.validFrom: 2022-06-17
---

# Standard Audit File for Tax (SAF-T) electronic report

[!include [banner](../includes/banner.md)]

This article explains how to set up and run the Standard Audit File for Tax (SAF-T) electronic report.

The **Standard Audit File for Tax (SAF-T) electronic report** feature is available in Microsoft Dynamics 365 Finance as of version 10.0.26.

If an [Electronic Reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) format configuration is provided for the country or region that is defined in the primary address of your legal entity, and that ER format can be run directly from the ER workspace, you can use the **Standard Audit File for Tax (SAF-T) electronic report** feature to run it. To run the format, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.

Follow these steps to use the **Standard Audit File for Tax (SAF-T) electronic report** feature.

1. In Finance, open the **Feature management** workspace.
2. On the **All** tab, find and select the **Standard Audit File for Tax (SAF-T) electronic report** feature in the feature list.
3. Select **Enable now**.

After the **Standard Audit File for Tax (SAF-T) electronic report** feature is enabled, follow these steps to set up an ER format configuration.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select the ER format configuration that must be used.

Follow these steps to generate a report by using the ER format configuration that is selected in General ledger parameters.

1. Go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.
2. In the dialog box for the report, specify the required parameters, and then select **OK**.

## Country-specific regulatory features supported by the Standard Audit File for Tax (SAF-T) electronic report feature

The following table provides information about country-specific regulatory features that are supported by the **Standard Audit File for Tax (SAF-T) electronic report** feature.

| Country   | Feature name |
|-----------|--------------|
| The United Arab Emirates | [FTA Tax Audit File (FAF) in TXT format for the United Arab Emirates](../localizations/uae-faf.md) |
| Denmark                  | [Standard Audit File for Tax (SAF-T) for Denmark](../localizations/emea-dnk-saf-t.md) |
| Lithuania                | [Standard Audit File for Tax (SAF-T) for Lithuania](../localizations/emea-ltu-saf-t.md) |
| Norway                   | [Standard Audit File for Tax (SAF-T) for Norway](../localizations/emea-nor-satndard-audit-file-for-tax.md) |
| Singapore                | [IRAS Audit File (IAF) for Singapore](../localizations/apac-sgp-iras-audit-file.md) |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
