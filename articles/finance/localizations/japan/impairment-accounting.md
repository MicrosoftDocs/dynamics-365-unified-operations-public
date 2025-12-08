---
title: Set up impairment accounting common parameters and posting profiles
description: Learn how to define impairment accounting common parameters and posting profiles for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetPosting
ms.custom: 
  - bap-template
---

# Set up impairment accounting common parameters and posting profiles

[!include [banner](../../includes/banner.md)]

This article explains how to define impairment accounting common parameters and posting profiles for Japan in Microsoft Dynamics 365 Finance.

The following procedures use the JPMF demo company data.

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Set up impairment parameters

To set up impairment parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed assets parameters**.
1. Expand the **Impairment management** section.
1. In the **Warning period (in months)** field, enter a number.
1. Select the **Number sequences** tab and confirm that the following number sequence codes are set up:  
    - **Document ID for impairment**
    - **Impairment test ID**
    - **Cash generating unit number**

## Set up a posting profile

To set up a posting profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset posting profiles**.
1. Select **Edit**.
1. Expand the **Impairment management** section.
1. Select **Add**.
1. In the **Book** field, enter a value.
1. In the **Groupings** field, select an option.
1. In the **Fixed asset** number field, enter a value.
1. In the **Main account** field, enter a value.
1. In the **Offset account** field, enter a value.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
