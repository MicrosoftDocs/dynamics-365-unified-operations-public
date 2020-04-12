---
# required metadata

title: Create service object relations   
description: This topic describes how to create service object relations for a service agreement and a service order.
author: ShylaThompson
manager: tfehr
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable, SMAAgreementTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ShylaThompson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Create service object relations 

[!include [banner](../includes/banner.md)]


This topic describes how to create service object relations for a service agreement and a service order. When you a create service object relation, you associate the service object to a service agreement or service order. When a customer requests service for an item that is a service object, you can select the service object from the list of service object relations.

## Create a service object relation for a service agreement

Use the following steps to create a service object relation for a service agreement:

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  In the **Service agreements** list, select an existing service agreement, or click **New** to create a new service agreement.

3.  In the **Service agreements** form, on the **Action Pane**, on the **Service agreement** tab, in the **Relations** group, click **Service objects**.

4.  In the **Service objects** form, click **New**, and then select a service object for this service agreement.

5.  To assign a template bill of materials (BOM) to the service agreement, click **Functions**, and then select **Attach template BOM**. In the **Select template BOM** form, in the **Template BOM** field, select a template. 

## Create a service object relation for a service order

Use the following steps to create a service object relation for a service order:

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  In the **Service orders** list, select an existing service order, or create a new service order.

3.  In the **Service orders** form, on the **Action Pane**, on the **Service order** tab, in the **Relations** group, click **Service objects**.

4.  In the **Service objects** form, click **New**, and then select a service object for this service order.

5.  To assign a template BOM to the service agreement, click **Functions**, and then select **Attach template BOM**. In the **Select template BOM** form, in the **Template BOM** field, select a template. 


## See also

[Service objects overview](service-objects.md)

[Service object relations](service-object-relations.md)

[Template BOMs](template-boms.md)

  


