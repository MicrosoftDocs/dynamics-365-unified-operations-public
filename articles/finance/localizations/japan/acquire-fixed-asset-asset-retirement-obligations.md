---
title: Acquire a fixed asset with asset retirement obligations
description: Learn how to acquire a fixed asset with an asset retirement obligation (ARO) in Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Acquire a fixed asset with asset retirement obligations

[!include [banner](../../includes/banner.md)]

This article explains how to acquire a fixed asset with an asset retirement obligation (ARO) in Japan in Microsoft Dynamics 365 Finance.

For Japan, the asset retirement obligation (ARO) is discounted to present value and added to the acquisition cost of the fixed asset.

The following procedure walks you through how to acquire a fixed asset with an asset retirement obligation (ARO). The procedure uses the JPMF demo company data.

Before you can complete the following procedure, you must first select the **Fixed Assets** configuration key.

To acquire a fixed asset with an ARO, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Asset retirement obligations \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a name.
1. Select **Save**.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. In the **Account** field, specify the desired values.
1. In the **Book** field, enter a value.
1. In the **Debit** field, enter a number.
1. Select **Functions**.
1. Select **Generate asset retirement obligation transactions**. Confirm that a new record with a document type of **Asset retirement obligation** is created. 

    > [!NOTE]
    > The menu at **Functions \> Generate asset retirement obligation transactions** is used when the fixed asset is in the same journal. You can also use the menu at **Proposals \> Capitalized asset retirement obligation** for fixed assets that you already acquired. 

1. In the list, mark the selected row. The proposed amount is discounted to present value.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
