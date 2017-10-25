[alt-text for image](../images/Introduction.png) ---
# required metadata

title: Enable SQL triggers in BYOD
description: Enable SQL triggers in BYOD from the BYOD export process to orchestrate downstream processes
author: SunilGarg
manager: AnnBe
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 203764
ms.assetid: 45efdabf-1714-4ba4-9a9d-217143a6c6e0
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Enable SQL triggers in BYOD

When configuring the SQL Azure connection for BYOD entity publish, you can choose to also enable SQL triggers in your BYOD. This option is available as shown below.
![Configure SQL trigger](./media/SQLTrigger.png) 
When this option is enabled, the BYOD export job will enable SQL triggers in the target BYOD. This provides an opportunity for downstream processes to hook into the trigger to orchestrate actions that must be started after records are inserted by the BYOD process. One trigger per bulk insert operation is supported. The size of the bulk insert is determined by the ‘Maximum insert commit’ size parameter in data management framework.

