--- 
# required metadata 
 
title: Manage worker accommodations
description: This procedure walks through the steps for setting up work environment accommodation types, such as ergonomic chairs or periodic breaks. 
author: ShielaSogge
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations, Human Resources 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: USA
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Manage worker accommodations

[!include [banner](../../../includes/banner.md)]

This procedure walks through the steps for setting up work environment accommodation types, such as ergonomic chairs or periodic breaks. It also shows how to assign these accommodation types to a worker, and either approve or deny the accommodation type. The demo data company used to create this procedure is USMF.


## Setup accommodations
1. Go to Human resources > Setup > Accommodation types.
2. Click New.
3. In the Accommodation type field, enter a name for the accommodation. Example: Keyboard.
4. In the Description field, enter a description for the accommodation. Example: Ergonomic Keyboard.
5. In the Note field, enter any information that helps to clarify the accommodation.
6. Click Save.
7. Close the page.

## Assign accommodations
1. Go to Human resources > Workers > Employees.
2. From the list, select an employee.
3. Click the employee's name to view details about the employee who is requesting the accommodation.
4. Expand the Personal information FastTab.
5. Click Accommodations.
6. Click New.
7. In the Accommodation type field, select the appropriate accommodation. Example: Keyboard
8. In the Job task field, enter the work task that requires the accommodation.
9. In the Status field, enter the appropriate status. Example: Reasonable
    * The following statuses are available. Requested indicates that the accommodation has been created but not yet reviewed. Reasonable indicates that the accommodation is reasonable and will be granted. Undue hardship indicates that the accommodation will place an unreasonable burden on the employer, and has been denied. In this example, the request was approved immediately because the accommodation request was minimal.  
10. In the Accepted field, select the person who accepted the accommodation request.
11. Click Select.
12. In the Accepted date field, enter the date and time when the accommodation request was accepted.
13. Expand the Note section.
14. In the Financial field, enter any information or resource costs that helps to clarify the impact of the accommodation.
    * If the accommodation has been denied, the Reply field can be used to indicate why a request was denied.  
15. Click Save.

