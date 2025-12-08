---
title: Depreciation of fixed assets with reduction entry posted
description: Learn how to run fixed asset depreciation with reduction entries for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Depreciation of fixed assets with reduction entry posted

[!include [banner](../../includes/banner.md)]

This article explains how to run fixed asset depreciation with reduction entries for Japan in Microsoft Dynamics 365 Finance.

The following procedure uses the JPMF demo data company.

Before you complete the procedure, select the **Fixed Asset** configuration key.

To run fixed asset depreciation with reduction entries, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Depreciation proposal**.
1. In the **To date** field, enter a date.
1. Verify that **Reduction entry allocation** is selected.
1. Optionally, select **Filter** to filter only the necessary fixed assets to help speed up the process.  
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**. The depreciation that is attributed to the reduction entry is separated from that of the underline fixed asset by document type.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
