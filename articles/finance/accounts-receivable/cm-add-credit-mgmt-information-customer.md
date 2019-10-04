---
# required metadata

title: Add credit management information for a customer
description: 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Add credit management information for a customer

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

When you have set up the parameters that control advanced credit management, you can add additional details to each customer that will control the credit management processes and provide additional information that helps members of the collections team manage customers. You can add the additional infomation on the **Account receivable > Customers > All customers page on the Credit and collections** FastTab.

1.	Select **Yes** for **Unlimited credit limit** if you don't want your customer to be limited by any credit limit tests.
2.	Select **Yes** for **Exclude from credit management** to exclude the customer from any actions that would normally occur during credit management processes.
3.	Select the **credit management group** to be used for this customer.
4.	To calculate the credit limit in the customer's currency, enter the customer’s credit limit in the **Credit limit in customer's currency** field. The credit limit in the company currency will be converted using the exchange rates defined by the credit limit exchange rate type selected in the Credit management parameters.
5.	Enter a date in the **Last review date** field to show when the customer credit limit was last reviewed by a credit manager.
6.	Enter a date in the **Next scheduled review date** field to show when the customer is scheduled for credit review and update.
7.	Enter the **Eligible credit limit**, which is the highest possible credit limit that is allowed for the customer. The eligible credit limit represents the maximum credit that you could assign to a customer based on your review of their credit history. It can be different from the credit limit shown on the **Credit and collections** FastTab.
8.	Enter the currency value of the eligible credit limit in the **Eligible credit limit currency** field.
9.	Enter a date in the **Eligible credit limit date** field to show when the eligible credit limit was created.
10.	Enter the **Credit account status** for the customer.
11.	Enter the **Status reason** that's associated the account status.
12.	Select **Yes** in the **With agency to indicate** that the customer is currently assigned to a credit agency. This value is only for informational purposes and is not used in any credit management processes.
13.	Select **Yes** in the **Title held to indicate** field that a title is held for the company. This value is only for informational purposes and is not used in any credit management process.
14.	Enter a date in the **Business started date** field to show when the customer first started its business. This information will be used in creating risk scores.
15.	Enter a date in the the **Customer since** field to show when the first transactions were processed for this customer. This information will be used in creating risk scores.
16.	Enter notes that the credit team can use to further evaluate the customer's credit worthiness.

Also note that some information that is shown on the customer page is created by another process:

1.	The **Credit limit expiration date** is the date when the credit limit will expire. If you don't make an entry in this field is, the customers' credit limit won't expire.
2.	The **Credit limit date** is the date on which the credit limit was created. This date is updated whenever the credit limit is adjusted.
3.	**Temporary credit limits** override the customer credit limit for a period of time.  It will be used instead of the credit limit to calculate the total credit limit. It is only shown if there is an active credit limit. You can add temporary credit limits using credit limit adjustments.
4.	The amount displayed in the **Insurance and guarantees** field shows the total value of insurance and guarantees that can increase the credit limit for the customer.
5.	The **Total credit limit** fields shows the final credit limit for the customer including insurance and guarantees, and temporary credit limits.

## Temporary credit limits

Temporary credit limits override the customer credit limit for a period of time. You can add temporary credit limits using credit limit adjustments.
