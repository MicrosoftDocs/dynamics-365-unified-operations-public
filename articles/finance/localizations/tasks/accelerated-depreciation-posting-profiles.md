---
title: Configure accelerated depreciation parameters and posting profiles
description: For Japan, the accelerated depreciation is calculated based on Rate factor, Rate threshold and Calculation method.
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
ms.search.form: AssetParameters, AssetPosting
---
# Configure accelerated depreciation parameters and posting profiles

[!include [banner](../../includes/banner.md)]

For Japan, the accelerated depreciation is calculated based on Rate factor, Rate threshold and Calculation method. These parameters are available on the accelerated depreciation document. Configuring them on the fixed asset parameter can provide default values for the accelerated depreciation documents. 



In order to post the accelerated depreciation amounts, you must configure the Main account and Offset account for Accelerated depreciation in Fixed asset posting profile first.



This procedure walks you through setting up the accelerated depreciation parameters and posting profiles.



In order to complete this task, the Fixed Asset configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Configure parameters for accelerated depreciation
1. Go to Fixed assets > Setup > Fixed assets parameters.
2. Expand or collapse the Depreciation section.
3. In the Rate factor field, enter a number.
    * This will provide a default value to each of the Accelerated depreciation documents.  
4. In the Rate threshold field, enter a number.
    * This will provide a default value to each of the Accelerated depreciation documents.  
    * Specify which default formula to use in calculating the daily average overuse hour.  

## Configure a posting profile
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Expand or collapse the Accelerated depreciation section.
    * Specify the Main account and Offset account to use for Accelerated depreciation.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
