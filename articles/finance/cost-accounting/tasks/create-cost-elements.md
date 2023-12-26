---
title: Create cost elements
description: There are several ways to create cost elements in Cost accounting.
author: kfend
ms.date: 08/29/2022
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: CAMDimension, CAMAXMainAccountDimensionMemberProviderConfiguration, CAMDimensionMember
---
# Create cost elements 

[!include [banner](../../includes/banner.md)]

There are several ways to create cost elements in Cost accounting. This procedure shows how to create cost elements by importing main accounts via a data connector. The USMF demo company was used to create this procedure. This procedure is for a Cost accounting feature that was added in Dynamics 365 for Operations, version 1611.


## Create new cost elements
1. Go to **Cost accounting > Dimensions > Cost element dimensions**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Data connector for dimension members** field, enter or select a value.
5. In the **Description** field, type a value.
6. Click **Save**.

## Configure the data connector
1. Click **Configure dimension member provider**.
2. In the **Chart of accounts** field, enter or select a value.
    * Select **Shared** to use the shared chart of accounts.  
3. Click **New**.
4. In the list, mark the selected row.
    * You can apply filters to accounts to meet your criteria.  
5. In the **From main account** field, enter or select a value.
6. In the **To main account** field, enter or select a value.
7. Click **OK**.

## Import main accounts
1. Click **Import dimension members**.
    * Main accounts will be imported into Cost accounting and used as cost elements.  
2. Click **OK**.

## View the imported accounts as cost elements
1. Click **View dimension members**.
    * View the imported ledger accounts as cost elements in your business that costs can flow to.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
