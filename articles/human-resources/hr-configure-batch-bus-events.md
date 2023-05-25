---
# required metadata

title: Business events in batch in Microsoft Dynamics 365 Human Resources
description: This article describes how to configure business events in batch in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 5/23/2023
ms.custom:

---

# Configure batch-based business events


[!INCLUDE [PEAP](../includes/peap-2.md)]

Customers can configure business events to run in batch. This provides customers with an easy way to configure and set up business events that are tied to a point in time. Business events that are available to be ran in a batch, can be found **Human resources shared parameters > Business events**.  

## Examples  

Some examples of Human Resources business events that can be in a batch:
 - Employee start date is approaching  
 - Course due soon 
 - Certificate overdue 
 - Position transition date is approaching  

## Configure business events in batch 

1. Go to **Business events catalog**. 
2. Select the **Endpoints** of the business event. 
3. Click **Activate** to activate the business events. 
4. Go to **Human Resources shared parameters**, select **Business events**.
5. In the **Days** field, enter the batch job recurrence in days.
6. Select **Create batch jobs** and click **OK**.

 If **Set default values** is selected, all of the values will be reset. 
