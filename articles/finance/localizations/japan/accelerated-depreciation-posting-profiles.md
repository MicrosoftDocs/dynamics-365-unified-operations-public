---
title: Configure accelerated depreciation parameters and posting profiles
description: For Japan, the accelerated depreciation is calculated based on Rate factor, Rate threshold, and Calculation method, with a process for configuring parameters.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetPosting
ms.dyn365.ops.version: Version 7.0.0
---

# Configure accelerated depreciation parameters and posting profiles

[!include [banner](../../includes/banner.md)]

For Japan, the accelerated depreciation calculation uses the rate factor, rate threshold, and calculation method. You can find these parameters on the accelerated depreciation document. If you configure these parameters on the fixed asset parameter, you set default values for the accelerated depreciation documents.

To post the accelerated depreciation amounts, you must first configure the main account and offset account for accelerated depreciation in the fixed asset posting profile.

This procedure walks you through setting up the accelerated depreciation parameters and posting profiles.

To complete this task, you must select the Fixed Asset configuration key.

This procedure uses the demo data company JPMF.

## Configure parameters for accelerated depreciation

To configure parameters for accelerated depreciation, follow these steps:

1. Go to Fixed assets > Setup > Fixed assets parameters.
1. Expand or collapse the Depreciation section.
1. In the Rate factor field, enter a number.
    * This number is the default value for each of the Accelerated depreciation documents.  
1. In the Rate threshold field, enter a number.
    * This number is the default value for each of the Accelerated depreciation documents.  
    * Specify which default formula to use in calculating the daily average overuse hour.  

## Configure a posting profile

To configure a posting profile, follow these steps:

1. Go to **Fixed assets > Setup > Fixed asset posting profiles**.
1. Expand or collapse the **Accelerated depreciation** section.
    * Specify the main account and offset account to use for accelerated depreciation.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
