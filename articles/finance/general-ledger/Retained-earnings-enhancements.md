---
# required metadata

title: Currency capabilities in financial reporting
description: Financial reporting includes features that support complex currency reporting requirements.
author: jiwo
ms.date: 09/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2020-01-09
ms.dyn365.ops.version: Version 10.0.8

---

# Using Retained earnings calculation enhancements for financial reporting when using currency translation

[!include [banner](../includes/banner.md)]

When you enable this feature, any retained earnings account that has the Currency translation type set to Transaction date will calculate the accounting currency balance of the account using change in current year and the exchange rate at the end of the year. The total retained earning balance at the end of any year would be a total of each calculate year. 

   [![RetainedEarnings.](./media/RetainedEarnings.png)](./media/RetainedEarnings.png)

What happens when you turn on this feature?
Assuming that there is a December 31st year end. When the Retained earnings calculation enhancement is turned on, the change in the current year will be calculated using the currency rate as of that date. 
 
In the example above, the Retained earnings as of 12/31/2021 without the feature turned on is 250.00 and the amount in Reporting currency is $312.50 which is the 250.00 multiplied by 1.25 which was the rate as of 12/31/2021. 

However, the Retained earnings as of 12/31/2021 with the feature turned on in reporting Currency is 288.75. This number is made up of the calculated balances as shown by (d). 

  > [!NOTE] To opt in or to opt out of this feature, you must log a support ticket to get this turned on for your organization. 
