---
# required metadata

title: Deferral posting methods example
description: This topic describes the differences in the Deferral posting methods in Revenue and expense deferrals in Subscription billing. 
author: JodiChristiansen
ms.date: 6/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Deferral posting methods

This article explains the Deferral posting options in **Revenue and expense deferral parameters** in Subscription billing. 

In **Revenue and expense deferral parameters** the **Deferral posting options** are Balance Sheet and Profit and loss. This example will help explain the differences and why you may use one method or the other. 

The Balance sheet method uses only two accounts, so less setup is involved. The Profit and loss method has two additioanl accounts for revenue, discount, and costs depending on the transaction type; Initial recognition account and Recognition offset account. These accounts are setup on the **Deferral defaults** page under Subscirption billing > Revenue and expense deferrals > Setup. The example below focuses on the revenue deferrals but the same concept can be applied for the deferred discount and deferred cost. 

## Example 

Sales invoice 1 totals $3000 and has deferred revenue. These are the distributions when the sales invoice is posted. 

Balance sheet method




