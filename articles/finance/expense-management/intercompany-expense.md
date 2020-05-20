---
# required metadata

title: Intercompany expenses
description: A worker who is employed by one legal entity in an organization might perform work for another legal entity in the same organization. In this situation, you can use the intercompany expense feature to assign the worker’s expenses to the legal entity for which the work was performed.
author: ShylaThompson
manager: AnnBe
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TrvParameters
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Intercompany expenses

[!include [banner](../includes/banner.md)]

A worker who is employed by one legal entity in an organization might perform work for another legal entity in the same organization. 
In this situation, you can use the intercompany expense feature to assign the worker’s expenses to the legal entity for which the 
work was performed. The legal entity that employs the worker is called the loaning legal entity. The legal entity for which the worker 
incurs expenses is called the borrowing legal entity. 

Before a worker can create and submit expenses for work that is performed for a different legal entity, in the loaning legal entity, 
on the **Expense management parameters** page, select the **Allow intercompany expense lines** option. 

# Tax Posting for Intercompany expenses

[!include [banner](../includes/banner.md)]

If you desire to use Tax groups associated with the loaning or source legal entity instead of the borrowing or destination legal entity in your expense report, then you will need to configure this in the General Ledger sales tax set up. 
When GL parameter "Legal entity for intercompany tax posting" is set to "Source" and "Apply sales tax taxation rules" is "NO", the tax combination for the loaning or source legal entity will be used. When the same parameter is set to "Destination", the tax combination for Borrowing or destination legal entity will be used. 
For US legal entities, when the above GL parameter is set to "Source", the "Sales Tax receiveable" field also needs to be configured in the new Ledger posting groups form. The accounting engine will use the information from this field for tax related accounting entry.   
The behavior is consistent for expense lines posted with or without a Project.  
