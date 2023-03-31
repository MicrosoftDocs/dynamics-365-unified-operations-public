--- 
# required metadata 
 
title: Manage worker accommodations
description: This procedure walks through the steps for setting up work environment accommodation types, such as ergonomic chairs or periodic breaks. 
author: ShielaSogge
ms.date: 01/10/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
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


[!INCLUDE [PEAP](../../../../../includes/peap-1.md)]

This procedure walks through the steps for setting up work environment accommodation types, such as ergonomic chairs or periodic breaks. It also shows how to assign these accommodation types to a worker, and either approve or deny the accommodation type. The demo data company used to create this procedure is USMF.

## Set up accommodations

1. Go to **Human resources \> Setup \> Accommodation types**.
2. Select **New**.
3. In the **Accommodation type** field, enter a name for the accommodation. For example, enter **Keyboard**.
4. In the **Description** field, enter a description of the accommodation. For example, enter **Ergonomic Keyboard**.
5. In the **Note** field, enter any information that helps clarify the accommodation.
6. Select **Save**.
7. Close the page.

## Assign accommodations

1. Go to **Human resources \> Workers \> Employees**.
2. In the list, select an employee.
3. Select the employee's name to view details about the employee who is requesting the accommodation.
4. Select the **Personal information** FastTab.
5. Select **Accommodations**.
6. Select **New**.
7. In the **Accommodation type** field, select the appropriate accommodation. For example, select **Keyboard**.
8. In the **Job task** field, enter the work task that requires the accommodation.
9. In the **Status** field, enter the appropriate status. For example, enter **Reasonable**.

    The following statuses are available:

    - **Requested** – The accommodation has been created but hasn't yet been reviewed.
    - **Reasonable** – The accommodation is reasonable and will be granted.
    - **Undue hardship** – The accommodation will place an unreasonable burden on the employer and has been denied.

    In this example, the request was immediately approved because the accommodation request was minimal.

10. In the **Accepted** field, select the person who accepted the accommodation request.
11. Select **Select**.
12. In the **Accepted date** field, enter the date and time when the accommodation request was accepted.
13. Expand the **Note** section.
14. In the **Financial** field, enter any information or resource costs that help clarify the impact of the accommodation.

    If the accommodation has been denied, you can use the **Reply** field to indicate why the request was denied.

15. Select **Save**.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
