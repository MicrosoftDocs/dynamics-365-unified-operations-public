---
# required metadata

title: Manage buy and sell leave policies
description: You can enable employees to buy and sell leave in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeaveBuySellPolicy, LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Human Resources

---

# Manage buy and sell leave policies

>[!Important]
>The functionality noted in this topic is currently available for customers on the stand-alone Dynamics 365 Human Resources. Some or all of the functionality will be available as part of a future release on the Finance infrastructure after Finance release 10.0.26.


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can enable employees to buy and sell leave by creating a buy and sell leave policy. You can configure these policies to use workflow for approvals, set maximum amounts and rates, and set rates for buying and selling. 

## Enable employees to buy and sell leave

1. On the **Leave and absence parameters** page, select **Yes** for **Allow employees to buy leave** and **Allow employees to sell leave**.

## Create a buy and sell leave policy

1. On the **Leave and absence** page, select the **Links** tab. 

2. Select **Buy and sell leave policy**.

3. Select **New**.

4. Enter a **Name** and **Description** for the policy under **Buy and sell leave policy**. 

5. Select a **Policy type**. 

   The available policy types are **Amount** and **Hours per week**. Select **Amount** to enter a **Fixed amount** for the maximum amounts employees can buy and sell. If you select **Hours per week**, the working time defined in the employee's assigned working time calendar is used to determine the maximum amount of the policy. 

6. Select a **Start date** and **End date** for the policy. Requests to buy or sell leave will only be available for submission during this time frame. 

7. Select a **Workflow ID** for the policy. Any buy and sell requests will use this workflow for review and approval. 

8. Under **Buy policy**, select **Full time equivalency** (FTE) to prorate the maximum amount based on the FTE defined on the employee's position. If the policy type is **Amount**, enter a **Maximum fixed amount**. 

9. Select **Add** to add the leave types for employees to buy leave. You can add multiple leave types to the policy. 

10. Enter the **Months of service** for the leave type to enable different months of service to determine the maximum amount an employee can buy. 

11. Enter the **Maximum amount** for the leave type. 

12. Enter the **Rate** at which the employee will buy the leave. 

13. Optionally enter the **Earning code** to be used for buying leave. 

14. Optionally set whether to use FTE to determine the maximum amount for the leave type. 

15. To create a sell policy, follow steps 8 through 14 under **Sell policy**. 

## Add the buy and sell leave policy to a leave and absence plan

1. On the **Leave and absence** page, select a leave and absence plan.

2. Under **Rules**, select **Buy and sell leave policy**.

## See also

[Leave and absence overview](hr-leave-and-absence-overview.md)</br>
[Configure leave and absence types](hr-leave-and-absence-types.md)</br>
[Accrue leave and absence plans](hr-leave-and-absence-accrue.md)</br>
[Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
