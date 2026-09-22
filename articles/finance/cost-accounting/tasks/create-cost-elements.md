---
title: Create cost elements
description: There are several ways to create cost elements in Cost accounting. Learn about how to create new cost elements and configure data connectors.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/20/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CAMDimension, CAMAXMainAccountDimensionMemberProviderConfiguration, CAMDimensionMember
ms.dyn365.ops.version: Version 7.0.0
---

# Create cost elements

[!INCLUDE [banner](../../includes/banner.md)]

You can create cost elements in Cost accounting in several ways. This procedure shows how to create cost elements by importing main accounts through a data connector. This procedure uses the USMF demo company.

## Create new cost elements

1. Go to **Cost accounting** > **Dimensions** > **Cost element dimensions**.
1. Select **New**.
1. Enter a name in the **Name** field.
1. Enter or select a value in the **Data connector for dimension members** field.
1. Enter a description in the **Description** field.
1. Select **Save**.

## Configure the data connector

1. Select **Configure dimension member provider**.
1. Enter or select a value in the **Chart of accounts** field.
    * Select **Shared** to use the shared chart of accounts.  
1. Select **New**.
1. Mark the selected row in the list.
    * Apply filters to accounts to meet your criteria.  
1. Enter or select a value in the **From main account** field.
1. Enter or select a value in the **To main account** field.
1. Select **OK**.

## Import main accounts

1. Select **Import dimension members**.
    * Import main accounts into Cost accounting and use them as cost elements.  
1. Select **OK**.

## View the imported accounts as cost elements

1. Select **View dimension members**.
    * View the imported ledger accounts as cost elements in your business that costs can flow to.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
