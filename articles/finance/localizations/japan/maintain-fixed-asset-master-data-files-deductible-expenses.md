---
title: Maintain fixed-asset master data files for deductible expenses
description: Learn how to maintain fixed asset master data files for deductible expenses for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - AssetGroup, AssetGroupBookSetup
  - AssetTable, AssetBook
ms.custom: 
  - bap-template
---

# Maintain fixed-asset master data files for deductible expenses

[!include [banner](../../includes/banner.md)]

This article explains how to maintain fixed asset master data files for deductible expenses for Japan in Microsoft Dynamics 365 Finance.

The following procedures were created using the demo data company JPMF.

## Set up a fixed asset group

To set up a fixed asset group, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset groups**.
1. Select **New**.
1. In the **Fixed asset group** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Autonumber fixed assets** field ,select **Yes**.
1. Select a number sequence code to autogenerate the fixed asset number.
1. Select the default location for new fixed assets.
1. Select **Books**.
1. Select **New**.
1. In the **Book** field, enter a value. For example, enter "200RED_CUR".  
1. Expand the **General** section and configure the options.
1. Select **Save**.
1. Select **New**.
1. In the **Book** field, enter a value. For example, enter "250NDB_TAX".  
1. Expand the **General** section and configure the options.  
1. Select **Save**.

## Create a fixed asset

To create a fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, enter a value. You can use the fixed asset group that you created, or you can use "BUIL-M".  
1. Select **Books**.
1. Verify that the books were created automatically.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
