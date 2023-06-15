---
# required metadata

title: Fixed asset impairment accounting on cash-generating units for Japan
description: This article gives the user an overview of the conceptual model for impairment accounting for Japan. 
author: kfend
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetAllocationGoodwillSharedAsset_JP, AssetCashGeneratingUnit_JP, AssetCashGeneratingUnitGroup_JP, AssetImpairmentRecognitionMethod1_JP, AssetImpairmentRecognitionMethod2_JP
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Japan
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed asset impairment accounting on cash-generating units for Japan

[!include [banner](../includes/banner.md)]

This article introduces the features for fixed asset impairment, and the primary objective is to give you an overview of the conceptual model for impairment accounting. 

Fixed assets might be susceptible to impairment (decline) of their value because of factors such as poor management, new competition, and technological innovations. Impairment losses are stated in a profit and loss account. The impairment value is measured by comparing the value of the fixed asset or income generating unit with its recoverable amount. The recoverable amount is the highest value that can be obtained from selling the fixed asset or income that is generated from operation of the fixed asset. In Japan, impairment of fixed assets is done in accordance with No. 6 of Japanese generally accepted accounting principles (GAAP), where a two-step method is used. The first step is a recognition test of impairment loss, and the second step is measurement of the impairment loss. After impairment, the recoverable amount will be the new net book value of the fixed asset for future depreciation calculation. The impairment work process includes the following major tasks.

## CGU groups
The primary page is **CGU groups** (**Fixed assets** > **Setup** > **Impairment** > **CGU groups**). CGU groups are the entire combination of the impairment process. In a given CGU group, a user can assign one particular fixed asset to only one cash generating unit. This restriction doesn't apply when the user creates a different CGU group and then creates cash generating units under that group. Creating multiple CGU groups is useful for simulations to find the most appropriate grouping of fixed assets.

## Cash-generating unit (CGU)
The primary page is **Cash generating groups** (**Fixed assets** &gt; **Setup** &gt; **Impairment** &gt; **CGU groups**). A user can create cash-generating units under a CGU group and then assign individual fixed assets to each cash-generating unit. The user can also directly assign the fixed assets to the CGU group if those assets are shared assets or goodwill. Impairment on shared assets and goodwill will be tested and measured on the CGU group unit, in compliance with Method I under Japanese GAAP. A user can also apply Method II. In this case, the user will have to allocate the net book value of the shared assets and goodwill to each cash generating unit.

### Optional: Allocating the net book value of shared assets and goodwill

The primary page is **Allocation of net book value of goodwill and shared asset** (**Fixed assets** &gt; **Setup** &gt; **Impairment** &gt; **Allocation of net book value of goodwill and shared asset**). If a user chooses to apply Method II in a CGU group, the net book value of shared assets and goodwill must be allocated to each cash generating unit.

## Impairment recognition test
The primary page is **Fixed assets** > **Periodic tasks** > **Impairment on individual assets** > **Impairment recognition (Method I: on a bigger group than CGU/Impairment recognition (Method II: Allocate carrying amount of shared asset/goodwill to CGUs)**. The pages are different, depending on whether Method I or Method II is applied. The first step of impairment is the recognition test which you can run by selecting **Recognistion test**. Future cash flow that isn't discounted is used as a standard that the carrying amount (or net book value) is compared against. If this future cash flow isn't enough to cover the net book value of the asset, the impairment measurement must recognize the journal amount.

## Measurement of the impairment amount
The second step is measurement of the impairment amount. The recoverable amount is subtracted from the net book value of the fixed asset to calculate the impairment amount. The recoverable amount is either the value in use or the market value of the asset, whichever is higher. The two steps are done on the same page.

## Posting the impairment
After the recognition test and measurement of the impairment amount, the user can post the impairment amount to each fixed asset. After posting, the depreciation proposal will consider the impairment amount and propose the correct depreciation amount.

## Reports and other required operations
The user can use the **Impairment reports and transactions** inquiry pages to retrieve detailed information about the impairment transactions. Specific operations are required after an impairment is posted, such as adjustment on the corporate tax declaration. The user will have to manually calculate and post these operations.

## Additional resources
- [Impairment accounting for fixed assets for Japan](apac-jpn-impairment-accounting-fixed-assets.md)
- [Propose and post the impairment amount on a cash generating unit](./tasks/propose-post-impairment-amount-cash-generating-unit.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
