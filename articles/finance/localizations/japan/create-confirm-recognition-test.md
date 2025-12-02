---
title: Create and confirm recognition test
description: Learn how to create and confirm recognition tests for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetImpairmentManageTestResult_JP, AssetImpairmentRecognition_JP
ms.custom: 
  - bap-template
---

# Create and confirm recognition test

[!include [banner](../../includes/banner.md)]

This article explains how to create and confirm recognition tests for Japan in Microsoft Dynamics 365 Finance.

In Japan, impairment of fixed assets is done using a two-step method in accordance with Japanese generally accepted accounting principles (GAAP). The first step (*Method I*) tests whether an impairment is needed, and the second step (*Method II*) calculates the impairment amount if needed.

The following procedure walks you through how to run the two-step process in a recognition test and then get it ready for posting. This procedure was created using the demo data company JPMF.

Before you complete the procedure, you must first select the **Fixed Asset** configuration key.

To create and confirm a recognition test, follow these steps.

1. In Dynamics 365 Finance, for Method I, go to **Fixed assets \> Periodic tasks \> Impairment recognition (Method I: on a bigger group than CGU)**. For Method II, go to **Fixed assets \> Periodic tasks \> Impairment recognition (Method II: Allocate carrying amount of shared asset/goodwill to CGUs)**.  
1. Select **New**.
1. In the **CGU group** field, enter a value.
1. In the **Date** field, enter the date on which to post the impairment transaction.  
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Select **Recognition test**.
1. Select **Run test**. The recognition test compares the sum of the net book value with the undiscounted cash flow of each cash generating unit to determine if calculation of the impairment amount is needed.  
1. Select **Calculate**. If the test result is "Yes", the recognition test subtracts the recoverable amount from the net book value to determine the impairment adjustment amount. The impairment adjustment amount is distributed to each of the fixed assets for posting.  
1. Select **Confirm**. You only can post confirmed recognition tests.  
1. Select **Yes**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
