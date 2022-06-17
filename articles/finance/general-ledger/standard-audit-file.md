---
# required metadata

title: Standard Audit File for Tax (SAF-T) electronic report
description: This article explains how to generate Standard Audit File for Tax (SAF-T) electronic report in Dynamics 365 Finance.
author: liza-golub
ms.author: elgolu
ms.date: 06/17/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.search.industry: 
ms.search.validFrom: 2022-06-17

---

# Standard Audit File for Tax (SAF-T) electronic report

This article explains how to set up and run Standard Audit File for Tax (SAF-T) electronic report.

The **Standard Audit File for Tax (SAF-T) electronic report** feature is available in Dynamics 365 Finance as of version 10.0.26.

If there is provided [Electronic Reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) format configuration for the country defined in primary address of your legal entity which can be run directly from ER workspace, 
you can use **Standard Audit File for Tax (SAF-T) electronic report** feature to run this ER format from **General ledger** \> **Inquires and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)** menu item.

To start using **Standard Audit File for Tax (SAF-T) electronic report** feature, follow these steps. 

1. Go to **Feature management** > **All**.
2. In the feature list, find and select **Standard Audit File for Tax (SAF-T) electronic report** feature.
3. Select **Enable now**.

When **Standard Audit File for Tax (SAF-T) electronic report** feature is enabled in **Feature management**, follow these steps to set up ER format configuration top be used.

1. In Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **General ledger parameters** page, on the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select the ER format configuration which must be used.

To generate report using selected ER format configuration in **General ledger parameters**, follow these steps.

1. In Finance, go to **General ledger** > **Inquiries and reports** > **Standard Audit File for Tax (SAF-T)** > **Standard Audit File for Tax (SAF-T)**.
2. In the dialog box of the report specify necessary parameters and click **OK**.

## Country-specific regulatory features supported by the **Standard Audit File for Tax (SAF-T) electronic report** feature

The following table provides information about some country-specific regulatory features that are supported by the **Standard Audit File for Tax (SAF-T) electronic report** feature.

| Country     | Feature name |
|-------------|--------------|
| Lithuania   | [Standard Audit File for Tax (SAF-T) for Lithuania](../localizations/emea-ltu-saf-t.md) |
| Norway      | [Standard Audit File for Tax (SAF-T) for Norway](../localizations/emea-nor-satndard-audit-file-for-tax.md) |
| Singapore   | [IRAS Audit File (IAF) for Singapore](../localizations/apac-sgp-iras-audit-file.md) |
