---
# required metadata

title: Flushing principles
description: This topic describes ***.

author: BibiSp
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221264
ms.assetid: dde49743-1541-4353-a030-63ca3069cd7d
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Controlling raw material consumption with the flushing principle 

[!include[banner](../includes/banner.md)]

The flushing principles...

[![](./media/scenario4.png)](./media/scenario4.png)

1.	Material warehouse
2.	Raw material picking
3.	Production input location
4.	Raw material consumption
5.	Production process
Material consumption is controlled by the following four flushing principles
•	Manual
•	Start
•	Finish
•	Picked from location
The flushing principles are configured in a defaulting hierarchy starting from the released product with the value Start. On the bill of material or formula line the flushing principle from the product can be overridden. The flushing principle on the production bill of material lines or batch order formula lines is defaulted from the product or overridden value on the bill of material or formulas.
Description of the flushing principles
Manual
Using this principle, it is indicated that material consumption will be accounted for as a manual operation . This is for example relevant  when time and quantity of consumed batch or serial numbers needs to be accounted for, for tracking purposes. In D365 manual consumption is done with the use of the production picking list journal and for items enabled for advanced warehouse processes there is a hand-held flow that support that.
Start
With the use of the flushing principle Start it is indicated that material will be automatically consumed when the production order is started. The amount of material consumed is proportional to the quantity that is started. If using the manufacturing execution system, the flushing principle Start can also be used to flush materials when an operation or process job is started.
Finish
With the use of Finish it is indicated that material will be automatically consumed when the production order is reported as finished or an operation that is set up to consume the materials is registered as completed. The amount of material consumed is proportional to the quantity that is reported as finished. If using the manufacturing execution system, the flushing principle Finish can also be used to flush material when an operation or a process job is completed.
Picked from location
With the user of Picked from location it is indicated that when the material is registered as picked for production, the material is automatically consumed. The material is registered as picked from location when work for raw material picking is completed or when material is available on the production input location and the material line is released to the warehouse. The picking list generated in the process is posted in a batch job.
