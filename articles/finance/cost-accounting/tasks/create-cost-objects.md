--- 
title: Create cost objects 
description: This procedure shows how to create cost objects by importing the cost center financial dimension into Cost accounting via a data connector.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CAMDimension, CAMAXFinancialDimensionMemberProviderConfiguration, CAMDimensionMember
ms.dyn365.ops.version: Version 7.0.0 
---

# Create cost objects 

[!include [banner](../../includes/banner.md)]

This procedure shows how to create cost objects by importing the cost center financial dimension into Cost accounting via a data connector. The USMF demo company was used to create this procedure. 


## Create new cost objects
1. Go to **Cost accounting > Dimensions > Cost object dimensions**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Data connector for dimension members** field, enter or select a value.
5. In the **Description** field, type a value.
6. Click **Save**.

## Configure the data connector
1. Click **Configure dimension member provider**.
    * Select **CostCenter** to import the CostCenter dimension into Cost accounting.  
2. In the **Dimension name** field, select Cost center.
3. Click **OK**.

## Import cost centers
1. Click **Import dimension members**.
2. Click **OK**.

## View the imported cost centers
1. Click **View dimension members**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
