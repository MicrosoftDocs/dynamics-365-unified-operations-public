--- 
title: Define resource capabilities
description: Learn how to define resource capabilities, including step-by-step processes for creating resource capabilities and assigning capacilities to resources.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac 
audience: Application User  
ms.search.form: WrkCtrCapability
---

# Define resource capabilities

[!include [banner](../../includes/banner.md)]

Resource capabilities describe what operations resources can do. During scheduling, the requirements of each job and operation are matched against the capabilities of the available resources. This task guide will help you create a resource capability and assign it to a resource. The demo data company used to create this task is USMF.


## Create a resource capability
1. Go to Resource capabilities.
2. Click New.
3. In the Capability field, type the ID of the resource capability.
    * For a given operation, you use the capability ID to specify that resources must have this capability to perform the operation.  
4. In the Description field, enter a description of the capability.

## Assign capability to a resource
1. Click Add.
2. In the Resource field, type the ID of the resource.
    * A resource capability can be assigned to one or more resources.  
3. In the Expiration field, enter a date.
    * You can use this field to specify that a resource has the capability for only a limited time.  
4. In the Priority field, enter a number.
    * When you schedule jobs and operations, you can specify whether to select resources by priority. If you choose to do this, and more than one resource can perform the job or operation by the requested date, the resource that has the lowest priority with respect to the required capability is selected.  
5. In the Level field, enter a number.
    * When you specify that a job or operation requires a particular capability, you can also specify the minimum level that is required. Use the capability level to differentiate resources that can perform the same job, but at different speeds, strengths, sizes, and so on.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]