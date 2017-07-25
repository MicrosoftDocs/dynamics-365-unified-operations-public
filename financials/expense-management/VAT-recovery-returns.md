---
# required metadata

title: Export and send VAT recovery returns
description: The recovery of Value Added Tax (VAT) is a two-part process. The first part of the recovery process is to identify and verify all expenses that are eligible for recovery and to calculate the total recoverable amount. The second part of the process is to file the VAT returns with all required documentation. 
author: saraschi2
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer:  twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi2
ms.search.validFrom: 
ms.dyn365.ops.version: AX 7.0.0
---

# Export and send VAT recovery returns

[!include[banner](../includes/banner.md)]
The recovery of Value Added Tax (VAT) is a two-part process. The first part of the recovery process is to identify and verify all 
expenses that are eligible for recovery and to calculate the total recoverable amount. The second part of the process is to file the 
VAT returns with all required documentation. 

A third-party company is often needed to complete the two parts. Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 
can help you complete the first part of this process so that you only have to use the third-party company for filing the VAT returns. 

As part of the process, you export VAT information to a Microsoft Excel worksheet. Before you begin the export, verify the following: 
 - All expense reports have the required receipts attached. 
 - All receipts are issued in the name of your company and not the employee who incurred the expense. 
 - The correct sales tax codes have been used. 

After all of the VAT information has been exported and the status of the expense transaction is set to ready for recovery, you can 
begin to file the returns with the local government.

On the **Expense tax recovery** page, select **Open** in the **Status** filter and then select the country/region that the taxes are 
being recovered from. Click **Export to Excel**. 

The VAT information for the selected transactions is exported to a worksheet in Microsoft Excel. You can attach the worksheet to an
e-mail message and send it to the company that is filing the VAT return on your behalf. 
