---
# required metadata

title: Subscription billing overview
description: This article describes subscription billing in Microsoft Dynamics 365 Finance.
author: JodiChristiansen
ms.date: 04/13/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, CustVendExternalItem
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2022-02-09
ms.dyn365.ops.version: 10.0.25

---

# Subscription billing overview

[!include [banner](../includes/banner.md)]

Subscription billing enables organizations to manage subscription revenue opportunities and recurring billing through billing schedules. Complex pricing and billing models and revenue allocation are easily managed, and are billed and recognized at the line level. Multi-element revenue allocation enables allocation of revenue to comply with International Accounting Standards (International Financial Reporting Standard 15 \[IFRS 15\]) and Generally Accepted Accounting Principles (US GAAP) standards (Accounting Standards Codification Topic 606 \[ASC 606\]).

The solution has three modules that can be used independently. Alternatively, all three modules can be used together.

- **Recurring contract billing** – This module enables recurring billing and price management to provide control over pricing and billing parameters, contract renewal, and consolidated invoicing.
- **Revenue and expense deferrals** – This module eliminates manual processes and dependency on external systems by managing revenue and enabling real-time insight into monthly recurring revenue.
- **Multiple element revenue allocation** – This module helps with revenue compliance by handling pricing and revenue allocation across multiple items.

For more information about subscription billing, see [Subscription billing Power BI content](sub-bill-power-bi.md).

Subscription billing is enabled through **Feature management**. However, it can't be used with the **Revenue recognition** feature. Therefore, you must disable that feature before you enable subscription billing.

1. In the **Feature management** workspace, on the **All** tab, enter **Revenue recognition** in the filter, and then select the feature name as the filter.
2. Select the **Revenue recognition** feature, and then select **Disable**.
3. In **Feature name** filter, enter **Subscription billing**, and then select the module filter.
4. Select the **Subscription billing** feature, and then select **Enable**.
5. Select one of the three modules from the previous list, and then select **Enable**. Repeat this step for each of the other two modules.

    > [!IMPORTANT]
    > The **Subscription billing** feature must be enabled before you can enable any of the three modules.
