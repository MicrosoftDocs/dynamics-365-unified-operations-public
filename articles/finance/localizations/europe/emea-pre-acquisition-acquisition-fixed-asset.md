---
title: Post the preacquisition of a fixed asset
description: This article describes how to set up and post fixed asset preacquisitions with Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Hungary
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Post the preacquisition of a fixed asset

[!include [banner](../../includes/banner.md)]

This article describes how to set up and post fixed asset preacquisitions with Microsoft Dynamics 365 Finance.

> [!NOTE]
> The functionality for posting fixed asset preacquisitions is only available for legal entities that have their primary address in Hungary or the Czech Republic. A preacquisition of a fixed asset isn't depreciable, and it doesn't affect the acquisition costs or the net book value of the fixed asset. When you post a preacquisition, the status of the fixed asset is changed to **Acquired**. A fixed asset that has the **Acquired** status isn't depreciable. By contrast, when you post an acquisition, the status is changed to **Open**, and the fixed asset is depreciable.

## Set up preacquisitions

Before you can post a preacquisition, you must complete the following steps:

1. In Dynamics 365 Finance, go to the **Fixed assets parameters** page.
1. Set the **Allow preacquisitions** option to **Yes**.
1. On the **Fixed assets** page, go to **Setup** \> **Fixed asset posting profiles** and set up a fixed asset posting profile for the preacquisition posting type.

## Post a preacquisition of a fixed asset

To post a preacquisition of a fixed asset, follow these steps.

1.  On the **Fixed assets** page, create a new journal, and enter all required applicable information.
1.  For the journal that you just created, select **Lines** to open the **Journal voucher** page.
1.  Select **New** to create a line.
1.  In the **Transaction type** field, select a transaction that has the **Pre-Acquisition** transaction type.
1.  Enter values for the remaining fields as required.
1.  Select **Validate** to validate the journal lines.
1.  Select **Proposals \> Pre-acquisition proposal**.
1.  Select **Select** to set up the selection criteria, and then select **OK**.
1.  Select **OK** to close the **Preacquisition proposal** page.
1. Select **Post \> Post** to post the preacquisition transaction. On the **Books** page, the status of the fixed asset should now be **Acquired**.

  > [!NOTE]
  > In the parameters for the acquisition/acquisition adjustment proposal, you can set the date in the **To date** field up to the date for which preacquisition transactions are selected.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
