---
# required metadata

title: Intercompany expenses
description: A worker who is employed by one legal entity in an organization might perform work for another legal entity in the same organization. In this situation, you can use the intercompany expense feature to assign the worker’s expenses to the legal entity for which the work was performed.
author: ShylaThompson
manager: AnnBe
ms.date: 05/20/2020
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

## Tax posting for intercompany expenses

[!include [banner](../includes/banner.md)]

If you want to use tax groups that are associated with the loaning (source) legal entity instead of the borrowing (destination) legal entity in your expense report, you will need to configure this in the General ledger sales tax set up. 
When the General ledger parameter, **Legal entity for intercompany tax posting** is set to **Source** and **Apply sales tax taxation rules** is set to **No**, the tax combination for the loaning legal entity will be used. When the same parameter is set to **Destination**, the tax combination for borrowing legal entity will be used. 
For legal entities in the United States, when the parameter is set to **Source**, the **Sales tax receivable** field must also be configured on the new **Ledger posting groups** page. The accounting engine will use the information from this field for tax related accounting entry.   
The behavior is consistent for expense lines posted with or without a project.  
