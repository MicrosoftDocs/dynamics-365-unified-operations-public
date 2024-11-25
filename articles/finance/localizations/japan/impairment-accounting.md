---
title: Setup impairment accounting common parameters and posting profile
description: Learn how to define impairment accounting common parameters and posting profiles, including outlines on setting up impairment parameters and posting profiles.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 02/28/2019
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetPosting
ms.dyn365.ops.version: Version 7.0.0
---

# Setup impairment accounting common parameters and posting profile

[!include [banner](../../includes/banner.md)]

Use this task to learn how to define impairment accounting common parameters and posting profiles.



To complete this task, the Fixed Assets configuration key must be selected.



This procedure uses the JPMF demo company data.


## Set up impairment parameters
1. Go to Fixed assets > Setup > Fixed assets parameters.
2. Expand the Impairment management section.
3. In the Warning period (in months) field, enter a number.
    * Example: 6 months  
4. Click the Number sequences tab. Confirm the following Number sequence codes are set up:  
 - Document ID for impairment
 - Impairment test ID
 - Cash generating unit number        

## Set up posting profile
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Click Edit.
3. Expand the Impairment management section.
4. Click Add.
5. In the Book field, type a value.
6. In the Groupings field, select an option.
7. In the Fixed asset number field, type a value.
8. In the Main account field, specify the desired values.
9. In the Offset account field, specify the desired values.
10. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
