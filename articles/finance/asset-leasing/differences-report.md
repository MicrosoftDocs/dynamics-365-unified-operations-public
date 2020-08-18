---
# required metadata

title: Differences report
description: 
author: moaamer
manager: Ann Beebe
ms.date: 08/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-18
ms.dyn365.ops.version: 10.0.14
---

# Differences report

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The topic describes the Differences report, which shows the differences between information loaded into the Lease import framework and the information that's currently in the system. This lets you compare what was adjusted, updated, or added through the **Lease import framework** functionality.

1.	To view this report, open the **Differences report** page (**Asset leasing > Reports > Differences report**).
2.	The parameters form contains dynamics filters to use to specify the Import ID, Process Type, Lease ID, and many more criteria.
3.	Click **OK**.

The values in the report will vary based on the lease presented. The report will only show those fields that are differ from what is currently in the system and what is in the staging tables. The **Old value** is what is either currently in the system or that was previously in the system, depending on whether the import process has run. The **New value** are the values in the staging table and will replace the **Old value**.

