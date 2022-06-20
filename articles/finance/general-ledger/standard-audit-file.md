---
# required metadata

title: Standard Audit File for Tax (SAF-T) electronic report
description: This article explains how to generate the Standard Audit File for Tax (SAF-T) electronic report in Dynamics 365 Finance.
author: liza-golub
ms.author: elgolu
ms.date: 06/20/2022
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

[!include [banner](../includes/banner.md)]

This article explains how to set up and run the Standard Audit File for Tax (SAF-T) electronic report.

The **Standard Audit File for Tax (SAF-T) electronic report** feature is available in Dynamics 365 Finance as of version 10.0.26.

If there is a provided [Electronic Reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) format configuration for the country that's defined in the primary address of your legal entity which can be run directly from ER workspace, you can use the **Standard Audit File for Tax (SAF-T) electronic report** feature to run this ER format. The format is run from the **General ledger** > **Inquires and reports** > **Standard Audit File for Tax (SAF-T)** > **Standard Audit File for Tax (SAF-T)** menu item.

Complete the following steps to use the **Standard Audit File for Tax (SAF-T) electronic report** feature. 

1. In Finance, go to **Feature management** > **All**.
2. In the feature list, find and select the **Standard Audit File for Tax (SAF-T) electronic report** feature.
3. Select **Enable now**.

When **Standard Audit File for Tax (SAF-T) electronic report** feature is enabled, complete the following steps to set up an ER format configuration.

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **General ledger parameters** page, on the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select the ER format configuration which must be used.

To generate a report using the selected ER format configuration in the **General ledger parameters**, follow these steps.

1. go to **General ledger** > **Inquiries and reports** > **Standard Audit File for Tax (SAF-T)** > **Standard Audit File for Tax (SAF-T)**.
2. In the dialog box of the report, specify the necessary parameters and select **OK**.

## Country-specific regulatory features supported by the Standard Audit File for Tax (SAF-T) electronic report feature

The following table provides information about country-specific regulatory features that are supported by the **Standard Audit File for Tax (SAF-T) electronic report** feature.

| Country     | Feature name |
|-------------|--------------|
| Lithuania   | [Standard Audit File for Tax (SAF-T) for Lithuania](../localizations/emea-ltu-saf-t.md) |
| Norway      | [Standard Audit File for Tax (SAF-T) for Norway](../localizations/emea-nor-satndard-audit-file-for-tax.md) |
| Singapore   | [IRAS Audit File (IAF) for Singapore](../localizations/apac-sgp-iras-audit-file.md) |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
