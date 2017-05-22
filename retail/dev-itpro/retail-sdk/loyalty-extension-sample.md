---
# required metadata

title: Loyalty extension sample
description:  
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 196163
ms.assetid:
ms.search.region: Global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2017-05-15
ms.dyn365.ops.version: AX 7.0.0

---

# Loyalty extension sample
## Scenario 
The Retailer wants the capability for its customers to earn and pay by loyalty within the single transaction. 

## Scenario details
The retailer has set up a loyalty scheme for the channel with some earning and redemption rules and associated the scheme with a loyalty program. The retailer wants to allow the customers to partially pay the transaction amount using their loyalty points and earn loyalty points for the remaining transaction amount that they pay by other payment means.

## Assumption
With the flexibility provided by the loyalty set up, this scenario can get very complex very quickly. So we have made some assumptions which reduce the complexity of the sample, but these assumptions are not far away from the real world examples. Here are the assumptions:	
1. There are no tiers associated with the loyalty program.
2. There is a single loyalty scheme and a single loyalty reward point type.
3. There is a single rule in 'Earning rules' that is applicable to all the product categories -- for e.g. on every $1 the customer spends, he/she will earn .1 reward point. 
4. There is a single rule in 'Redemption rules' that is applicable to all the product categories -- for e.g. 1 reward point is equivalent to $1.

> Note: The Earnings and Redemption rules mentioned above are just examples, and for this sample we have hardcoded these values. For the production scenario, these should be read from the DB instead.

## Customization approach:
We will achieve this customization in two steps. In step 1, we will earn the points assuming loyalty points were not used in the transaction, while in step 2, we will reduce the extra earned points based on the redeemed points.

There are six service requests for the loyalty feature in Dynamics 365 for Retail, these are listed below:	
1. GetLoyaltyCardStatusServiceRequest
2. CalculateLoyaltyRewardPointsServiceRequest
3. IssueLoyaltyCardServiceRequest
4. FillInLoyaltyRewardPointLinesForSalesServiceRequest
5. FillInLoyaltyRewardPointLinesForReturnServiceRequest
6. FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest

To calculate the reward points for the cash and carry transaction, the system uses the FillInLoyaltyRewardPointLinesForSalesServiceRequest for sales transaction lines which in turn uses the FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest to do the actual reward calculation. Similarly, the system uses the FillInLoyaltyRewardPointLinesForReturnServiceRequest for the return transaction lines which also uses the FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest to do the actual reward calculation. In the out-of-the-box implementation, loyalty feature does not allow to redeem and earn loyalty in the same transaction i.e. if the sales transaction has a tender line for the loyalty card, then the FillInLoyaltyRewardPointLinesForSalesServiceRequest does not call the FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest service to calculate the reward points. 

To enable redeem and earn loyalty in the same transaction, we will be working with one service request i.e. FillInLoyaltyRewardPointLinesForSalesServiceRequest

**Step 1: 

For our scenario, we need to implement the FillInLoyaltyRewardPointLinesForSalesServiceRequest such that it always calls the FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest to calculate the reward points. However, with this change, the system would calculate some extra earn points which includes the amount paid by loyalty points. Thus, we need a way to reduce the earned points by an appropriate amount. This is accomplished in step 2.

**Step 2:

We will leverage the post trigger mechanism provided by the extensibility framework on the FillInLoyaltyRewardPointLinesForSalesServiceRequest. In the post trigger, based on the earning rules and redemption rules, we will figure out how many extra reward points have been earned for each reward point redeemed and subtract those to get the correct amount.

**Implement FillInLoyaltyRewardPointLinesForSalesServiceRequest 

**Implement post trigger for the FillInLoyaltyRewardPointLinesForSalesServiceRequest


