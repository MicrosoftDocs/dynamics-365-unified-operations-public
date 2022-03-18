--- 
title: In-progress jobs end when reporting partial quantity on last job 
description: When using the job card device to report partial quantity on the last job in a production order, all previous jobs that have status of In progress are ended. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Previous in-progress jobs are ended when reporting partial quantity on last job

## Symptoms

When using the job card device to report a partial quantity on the last job in a production order, all previous jobs on that order that have a status of In progress are automatically ended.

## Resolution

This behavior is by design. On the **Production order defaults** page, on the **Report as finished** tab, there is an option named **End-mark route**. If this topic is set to *Yes*, a route card journal is posted when a worker uses the job card device or job card terminal to report the last operation. This journal marks all the operations as completed and ends all the production jobs. When the **End-mark route** option is set to *Yes*, the system doesn't consider the job status the worker selected when they reported the last operation. The system also doesn't consider whether the worker is reporting a full or partial quantity.
