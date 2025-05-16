---
title: Allocate carrying amount of shared asset and goodwill to cash generating units
description: Learn how to allocate the carrying amount of shared asset and goodwill to each of the cash generating units in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetImpairmentSharedAssetAlloc_JP, AssetImpairmentPopulateAllocation_JP
ms.custom: 
  - bap-template
---

# Allocate carrying amount of shared asset and goodwill to cash generating units

[!include [banner](../../includes/banner.md)]

This article explains how to allocate the carrying amount of shared asset and goodwill to each of the cash generating units in Japan with Microsoft Dynamics 365 Finance.

In Japan, impairment accounting for shared assets and goodwill is permitted for the following two methods: 

- **Method 1**: On a bigger unit than cash generating unit (CGU). 
- **Method 2**: Allocate carrying amount of shared asset/goodwill to CGUs. 

The following procedure applies to only the CGU groups that use method 2. The procedure was completed using the demo data company JPMF.

Before you complete the procedure, you must first select the **Fixed Asset** configuration key.

To allocate the carrying amount of shared asset and goodwill to each of the cash generating units, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Impairment \> Allocation of net book value of shared assets and goodwill**. The allocation of goodwill and shared assets is applicable only to the CGU groups with method 2, and the allocation must be done before activating the CGU group.  
1. In the **Proportion** field, enter a number.
1. Select the next cash generating unit
1. In the **Proportion** field, enter a number.
1. Select **Populate allocation**. Alternatively, you can repeat the previous steps to configure the proportions individually.  
1. In the list, mark or unmark all rows.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
