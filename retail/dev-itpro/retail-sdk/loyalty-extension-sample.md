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

```cs
namespace Contoso
{
    namespace Commerce.Runtime.EarnRedeemLoyalty
    {
        using System;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
        using System.Collections.Generic;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        
        public class FillInLoyaltyRewardPointLinesForSalesHandler : IRequestHandler
        {
            /// <summary>
            /// Gets the collection of supported request types by this handler.
            /// </summary>
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                        typeof(FillInLoyaltyRewardPointLinesForSalesServiceRequest),
                    };
                }
            }

            /// <summary>
            /// Entry point to FillInLoyaltyRewardPointLinesForSalesServiceRequest service.
            /// </summary>
            /// <param name="request">The request to execute.</param>
            /// <returns>Returns the SalesTransaction object with the one or more LoyaltyRewardPointLines.</returns>
            public Response Execute(Request request)
            {
                ThrowIf.Null(request, "request");
                var LoyaltyRewardPointLinesForSalesServiceRequest = (FillInLoyaltyRewardPointLinesForSalesServiceRequest)request;
                SalesTransaction salesTransaction = LoyaltyRewardPointLinesForSalesServiceRequest.SalesTransaction;

                // Call the service to calculate the loyalty reward points.                
                var fillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest = new FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest(salesTransaction, LoyaltyRewardPointLinesForSalesServiceRequest.EarnSchemeLines, LoyaltyRewardPointEntryType.Earn);
                var fillInLoyaltyRewardPointLinesForEarnOrDeductServiceResponse = request.RequestContext.Execute<SingleEntityDataServiceResponse<SalesTransaction>>(fillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest);
                salesTransaction = fillInLoyaltyRewardPointLinesForEarnOrDeductServiceResponse.Entity;
                return new SingleEntityDataServiceResponse<SalesTransaction>(salesTransaction);
            }
        }
    }
}
```

**Implement post trigger for the FillInLoyaltyRewardPointLinesForSalesServiceRequest

```cs
namespace Contoso
{
    namespace Commerce.Runtime.Sample.EarnRedeemLoyalty
    {
        using System;
        using System.Collections.Generic;
        using System.Linq;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;

        class AdjustLoyatyRewardsTrigger : IRequestTrigger
        {
            public IEnumerable<Type> SupportedRequestTypes
            {
                get { return new[] { typeof(FillInLoyaltyRewardPointLinesForSalesServiceRequest) }; }
            }
            public void OnExecuted(Request request, Response response)
            {
                ThrowIf.Null(request, "request");
                var LoyaltyRewardPointSalesServiceRequest = (FillInLoyaltyRewardPointLinesForSalesServiceRequest)request;
                SalesTransaction salesTransaction = LoyaltyRewardPointSalesServiceRequest.SalesTransaction;
                                
                if (salesTransaction.LoyaltyRewardPointLines != null)
                {
                    decimal totalReedeemedPoints = 0m;
                    decimal extraEarnedPoints = 0m;
                    
                    // Find the redeemed reward lines in the transaction and calculate the total redeemed reward points
                    IEnumerable<LoyaltyRewardPointLine> redeemLoyaltyRewardPointLines = salesTransaction.LoyaltyRewardPointLines.Where<LoyaltyRewardPointLine>(line => line.EntryType == LoyaltyRewardPointEntryType.Redeem);
                    if (redeemLoyaltyRewardPointLines.Count() > 0)
                    {                        
                        foreach (var rewardPointLine in redeemLoyaltyRewardPointLines)
                        {
                            totalReedeemedPoints += rewardPointLine.RewardPointAmountQuantity;
                        }

                        // Calculate the number of extra earned points for every redeemed point.
                        // If the earning rules stated that for every $1 spent, the user earns X points and redemption rule was that Y points equal $1 then, for every redemption point the user earns X/Y extra earn points.
                        // Based on the above logic, in this sample, for every redeemed point the user earns .1/1 = .1 extra earned points.
                        extraEarnedPoints = .1m * totalReedeemedPoints; 
                    }

                    // Reduce the amount of earned points by the extraEarnedPoints calculated above.
                    IEnumerable<LoyaltyRewardPointLine> earnLoyaltyRewardPointLines = salesTransaction.LoyaltyRewardPointLines.Where<LoyaltyRewardPointLine>(line => line.EntryType == LoyaltyRewardPointEntryType.Earn);
                    if (earnLoyaltyRewardPointLines.Count() > 0)
                    {
                        earnLoyaltyRewardPointLines.FirstOrDefault().RewardPointAmountQuantity -= extraEarnedPoints;
                    }
                }
            }
            public void OnExecuting(Request request)
            { }
        }
    }
}
```


