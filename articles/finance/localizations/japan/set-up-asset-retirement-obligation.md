---
title: Set up asset retirement obligation documents and enter ARO amount on a fixed asset
description: Learn how to set up asset retirement obligation documents and enter the ARO amount on a fixed asset for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetRetirementObligationDocument_JP, AssetTable, AssetRetirementObligation_JP, AssetRetirementObligationLine_JP
ms.custom: 
  - bap-template
---

# Set up asset retirement obligation documents and enter ARO amount on a fixed asset

[!include [banner](../../includes/banner.md)]

This article explains how to set up asset retirement obligation documents and enter the asset retirement obligation (ARO) amount on a fixed asset for Japan in Microsoft Dynamics 365 Finance.

For Japan, an asset retirement obligation (ARO) document identifies one type of asset retirement obligation. When you assign an ARO document to a fixed asset book, you can specify the cash flow that is expected to perform the obligation at asset retirement. 

Use the following procedures to create an ARO document, assign it to a fixed asset, and enter the estimated retirement cost.

In order to complete the following procedures, you must first select the **Fixed Asset** configuration key.

The procedures use the demo data company JPMF.

## Set up an asset retirement obligation document

To set up an asset retirement obligation document, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Asset retirement obligations \> Asset retirement obligation documents**.
1. Select **New**.
1. In the **Document ID** field, enter a value.
1. In the **Document date** field, enter a date. The document date is the default value used when assigning the ARO document to a fixed asset book.  
1. In the **Posting frequency** field, select the frequency for accruing the interest expense of the asset retirement obligation.  
1. In the **Description** field, enter a value.
1. Select **Save**.

## Create a fixed asset and assign the asset retirement obligation document to it

To create a fixed asset and assign the asset retirement obligation document to it, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Asset retirement obligations \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, select a fixed asset group to apply to the fixed asset.
1. In the **Name** field, enter a name for the fixed asset.
1. On the Action Pane, select **Fixed asset**.
1. Select **Asset retirement obligation**.
1. In the **Book** field, select the book of the fixed asset.
1. In the **Document ID** field, select the ID of the asset retirement document to attach to the fixed asset.

## Enter the asset retirement obligation amounts

To enter the asset retirement obligation amounts, follow these steps.

1. On the fixed asset **Asset retirement obligation** page, on the **Estimated retirement** FastTab, select **Create** to open the drop-down menu.
1. In the **Transaction date** field, enter the date on which to recognize the asset retirement obligation.
1. In the **Estimated retirement cost adjustment** field, enter the cash flow amount.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
