---
# required metadata

title: Loyalty extension sample
description: This topic explains how to set up the system so that customers can both earn loyalty points and pay by using loyalty points in the same transaction.
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
A retailer wants customers to be able to earn loyalty points and pay by using loyalty points in a single transaction. 

## Scenario details
The retailer has set up a loyalty scheme for the channel and associated that scheme with a loyalty program. The loyalty scheme includes some earning and redemption rules. The retailer wants customers to be able to partially pay a transaction amount by using their loyalty points. The customers should then be able to earn loyalty points for the remaining transaction amount that they pay by using other payment methods.

## Assumptions
Because of the flexibility that the loyalty setup provides, this scenario can quickly become very complex. We have made some assumptions to reduce the complexity of this sample. However, these assumptions aren't far removed from the real-world examples. Here are the assumptions:

+ No tiers are associated with the loyalty program.
+ There is a single loyalty scheme and a single loyalty reward point type.
+ There is a single earning rule that applies to all product categories. For example, this rule might specify that, for every $1 that the customer spends, he or she earns 0.1 reward point. 
+ There is a single redemption rule that applies to all product categories. For example, this rule might specify that one reward point is equivalent to $1.

> [!NOTE] 
> The earning and redemption rules that are mentioned here are just examples. For this sample, we have hard-coded the values. For a production scenario, the values should be read from the database instead.

## Customization approach
We implement this customization in two steps. In step 1, points will be earned as though loyalty points weren't used in the transaction. Then, in step 2, the extra points that were earned will be reduced, based on the points that were redeemed.

There are six service requests for the loyalty feature:

+ GetLoyaltyCardStatusServiceRequest
+ CalculateLoyaltyRewardPointsServiceRequest
+ IssueLoyaltyCardServiceRequest
+ FillInLoyaltyRewardPointLinesForSalesServiceRequest
+ FillInLoyaltyRewardPointLinesForReturnServiceRequest
+ FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest

To calculate the reward points for a cash-and-carry transaction, the system uses **FillInLoyaltyRewardPointLinesForSalesServiceRequest** for sales transaction lines. This request, in turn, uses **FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest** to do the actual reward calculation. Similarly, the system uses **FillInLoyaltyRewardPointLinesForReturnServiceRequest** for return transaction lines, and this request also uses **FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest** to do the actual reward calculation. In the out-of-box implementation of the loyalty feature, customers can't both redeem and earn loyalty points in the same transaction. In other words, if the sales transaction has a tender line for the loyalty card, **FillInLoyaltyRewardPointLinesForSalesServiceRequest** doesn't call **FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest** to calculate the reward points. 

To enable loyalty points to be redeemed and earned in the same transaction, we will work with one service request,  **FillInLoyaltyRewardPointLinesForSalesServiceRequest**.

### Step 1 

For our scenario, we must implement **FillInLoyaltyRewardPointLinesForSalesServiceRequest** in such a way that it always calls **FillInLoyaltyRewardPointLinesForEarnOrDeductServiceRequest** to calculate the reward points. However, this change will cause the system to calculate extra earned points, based on the amount that the customer pays by using loyalty points. Therefore, we must be able to reduce the earned points by an appropriate amount. This adjustment is done in step 2.

### Step 2

We take advantage of the post trigger mechanism that the extensibility framework provides on **FillInLoyaltyRewardPointLinesForSalesServiceRequest**. In the post trigger, we will use the earning and redemption rules to determine how many extra points were earned for each reward point that was redeemed. We will then subtract those extra points to get the correct amount.

#### Implement FillInLoyaltyRewardPointLinesForSalesServiceRequest 

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

#### Implement the post trigger for FillInLoyaltyRewardPointLinesForSalesServiceRequest

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
