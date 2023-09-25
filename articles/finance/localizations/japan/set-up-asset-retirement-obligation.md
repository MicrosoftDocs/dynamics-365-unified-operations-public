---
title: Set up asset retirement obligation documents and enter ARO amount on a fixed asset
description: For Japan, an asset retirement obligation (ARO) document identifies one type of asset retirement obligation.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: AssetRetirementObligationDocument_JP, AssetTable, AssetRetirementObligation_JP, AssetRetirementObligationLine_JP
---
# Set up asset retirement obligation documents and enter ARO amount on a fixed asset

[!include [banner](../../includes/banner.md)]

For Japan, an asset retirement obligation (ARO) document identifies one type of asset retirement obligation. When you assign an ARO document to a fixed asset book, you can specify the cash flow that is expected to perform the obligation at asset retirement. 



Use this procedure to learn how to create ARO documents, assign it to a fixed asset and enter the estimated retirement cost.



In order to complete this procedure, the Fixed Assets configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Setup asset retirement obligation document
1. Go to **Fixed assets > Asset retirement obligations > Asset retirement obligation documents**.
2. Click **New**.
3. In the **Document ID** field, type a value.
4. In the **Document date** field, enter a date.
    * The document date is the default value that is used when assigning the ARO document to a fixed asset book.  
    * In the **Posting frequency** field, select the frequency for accruing the interest expense of the asset retirement obligation.  
5. In the **Description** field, type a value.
6. Click **Save**.

## Create a fixed asset and assign the asset retirement obligation document to it
1. Go to **Fixed assets > Asset retirement obligations > Fixed assets**.
2. Click **New**.
3. In the **Fixed asset group** field, select a fixed asset group to apply to the fixed asset.
4. In the **Name** field, enter a name for the fixed asset.
5. On the Action Pane, click **Fixed asset**.
6. Click **Asset retirement obligation**.
7. In the **Book** field, select the book of the fixed asset.
8. In the **Document ID** field, select the ID of the asset retirement document to attach to the fixed asset.

## Enter the asset retirement obligation amounts
1. On the fixed asset **Asset retirement obligation** page, on the **Estimated retirement** FastTab, select **Create** to open the drop-down menu.
2. In the **Transaction date** field, enter the date on which to recognize the asset retirement obligation
3. In the **Estimated retirement cost adjustment** field, enter the cash flow amount
4. Click **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
