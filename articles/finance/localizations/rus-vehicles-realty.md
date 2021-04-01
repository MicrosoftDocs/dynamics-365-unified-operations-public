---
# required metadata

title: Vehicles and realty as fixed assets (Russia)
description: This topic explains how to set up and use vehicles and realty as fixed assets for Russia.
author: ShylaThompson
ms.date: 03/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Vehicles and realty as fixed assets (Russia)

[!include [banner](../includes/banner.md)]

## Set up the depreciation start date for vehicle and realty assets

Use the **Depreciation groups** page to set up the start date for depreciation of fixed assets of the **Realty** and **Vehicle** types.

You can specify that the calculation of depreciation should be based on the registration date of the asset. If an asset is registered after it's put into operation, depreciation is calculated from the first day of the month of registration. If an asset is registered before it's put into operation, depreciation is calculated from the first day of the month after the asset is put into operation.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2. Create a depreciation group, and enter the required details.
3. On the **General** FastTab, in the **Depreciation start date** field, select **Date of the registration** to specify that the registration date of a fixed asset should be used as the depreciation start date.

## Specify the registration date for vehicle and realty assets

1. Go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select **New** to create a fixed asset, and enter the required details.
3. On the **General** FastTab, in the **Type** field, select **Realty**.
4. On the **Technical information** FastTab, in the **Date of the registration** field, select the registration date of the fixed asset.
5. In the **Removal from the register date** field, select the date when the asset should be removed from the tax register.

For more information about asset depreciation, see [Calculate depreciation (Russia)](rus-depreciation-calculation.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]