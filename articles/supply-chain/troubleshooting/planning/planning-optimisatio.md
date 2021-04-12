---
# required metadata

title: Planning optimisation creates a planned purchase order when purchase exists within negative days if coverage code is min/max
description: Planning optimisation creates a planned purchase order when purchase exists within negative days if coverage code is min/max
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo,MpsIntegrationParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: ilebedev@microsoft.com

---

# Planning optimisation creates a planned purchase order when purchase exists within negative days if coverage code is min/max

KB Number: 4614298

Planningoptimisation creates a planned purchase order when purchase exists within negativedays if coverage code is min/max




## Resolution
This works as designed. Planning optimization does not support negative days and we do not have plans to support the parameter in the current form and shape.

Planning Optimization, however, always ensures that a planned order will not be placed within the lead time from the current date. So if purchase lead time is 10 days and there is a purchase order that is expected to arrive 8 days from now then it will be used as supply for the demand that is e.g. 5 days from now. So the suggestion for the users is to adjust lead times to cover 99.X% of scenarios. The customers can also apply for an exception to use the classic engine as a short-term solution.

We have deliverable to cover gaps in documentation.



