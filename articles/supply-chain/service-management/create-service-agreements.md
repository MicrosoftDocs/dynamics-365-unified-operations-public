---
# required metadata

title: Create service agreements
description: This topic describes how to use features in the Service management and the Project management and accounting modules to create service agreements.
author: sorenva
ms.date: 02/19/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAAgreementTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create service agreements

[!include [banner](../includes/banner.md)]

This topic describes how to use features in the Service management and the
Project management and accounting modules to create service agreements.

## Create a service agreement from Service management

1. Navigate to **Service management**.
2. Select **Service agreements** to create a new service agreement line in the page header. 
3. Select **New**. Enter a description, select a reference to a project in the **Project ID** field, and fill in the rest of the fields and lines for the service agreement. Select **Save**.
4. On the **Relations** tab, select **Service objects** or **Service tasks** to create service object relations or service task relations for the service agreement. The service objects and tasks that you have created relations for can be attached on the lines of the service agreement.
5. In the lower half of the page, create service agreement lines by copying lines from a service template, another service agreement,
or manually creating the service-agreement lines.

> [!NOTE]
> If you copy lines into the service agreement from another service agreement, you can indicate whether you also want to copy service object and service task relations. If you copy these relations, they are added to any existing relations on the service agreement. If you copy service-agreement lines from a service template, the service-object and service-task relations are automatically copied
as service-object relations and service-task relations on the new service-agreement lines.

## Create service agreement lines manually

1. From the **Service agreements** page, add a service agreement line in the lines grid. 
2. Enter the appropriate information for the service agreement line. 
3. Select **Save** to save the line, and then close the page.

## Create a service agreement from Project

1. Select **Project management and accounting**.
2. Select **All projects**.
3. Select the project from the list.
4. On the **Action Pane**, select **Manage**. In the **New** Action group, select **Service** and select **Service agreement**.
5. Follow the steps in the section titled **Create a service agreement** as described earlier in this topic to enter the project reference.


## Related topics

[Develop and establish service agreements overview](service-agreements.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]