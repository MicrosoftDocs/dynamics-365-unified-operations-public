---
title: Run the impairment recognition test and calculate the impairment amount on individual assets
description: Learn how to run the impairment recognition test and calculate the impairment amount on individual assets for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetImpairmentRecognitionTest_JP, SysQueryForm, AssetImpairmentCreateTest_JP, AssetImpairmentRecognitionTestResult_JP
ms.custom: 
  - bap-template
---

# Run the impairment recognition test and calculate the impairment amount on individual assets

[!include [banner](../../includes/banner.md)]

This article explains how to run the impairment recognition test and calculate the impairment amount on individual assets for Japan in Microsoft Dynamics 365 Finance.

Before you can complete the following procedure, you must maintain impairment indicators on individual assets.

The procedure uses the demo data company JPMF.

## Impairment recognition test

To run the impairment recognition test and calculate the impairment amount on individual assets, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Impairment on individual assets \> Impairment recognition test**.
1. Select **Query**.
1. In the list, find and select the **Fixed asset group** row.  
1. In the **Criteria field**, enter a value. For example, enter "TOOL-M".  
1. Select **OK**.
1. Confirm that three fixed assets with impairment indicators configured are displayed. TOOLM-000006 doesn't have any impairment adjustment, whereas TOOLM-000007 and TOOLM-000008 have adjustments of -1,750,000.00 and -2,250,000.00, respectively.  
1. Select **Save impairment** to open the drop dialog.
1. In the **Description** field, enter a value.
1. In the **Date** field, enter a date.
1. Select **OK**. The confirmation form of the impaired fixed assets is displayed and the impairment test ID is issued.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
