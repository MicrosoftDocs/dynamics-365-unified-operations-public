---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Demand Forecasting.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Demand Forecasting

This topic describes how to fix common issues that you might encounter while working with Demand Forecasting.

## Master planning doesn’t seem to respect capacity limitations and is scheduling more than the available capacity
Master planning doesn’t seem to respect capacity limitations. Operation reserved is showing higher than capacity. 

### Resolution/Fix
When using operation scheduling with finite capacity and where a mix of requirements for both resource group and individual resources is specified on the route, there is a slight chance of overbooking due to the way the algorithm checks for capacity conflicts. This overbooking can happen when running master planning with helpers and is most dominant if there is a lot of jobs with a relatively short runtime. If it is essential that no overbooking happens for operations scheduling then there is an option to basically make the scheduling part of master planning single threaded, by turning on the "Accurate finite capacity for Operation Scheduling" flag on the master planning parameters. This option has to be added manually to the form by personalization as shown below. Note that if using this option scheduling will run slower due to the lack of parallelism.  

##  When there are two trade agreements for the same/overlapping period, then the same agreement line is always picked.
If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the same trade agreement seems to be picked each time.
