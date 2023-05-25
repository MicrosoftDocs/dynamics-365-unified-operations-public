---
# required metadata

title: Power automates templates based business events    
description: This article describes the templates that are available for Human Resources business events
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 5/25/2023
ms.custom:

---

# Power automates templates based business events  


[!INCLUDE [PEAP](../includes/peap-2.md)]


The following templates available for Human Resources: 
 - Goal due reminder  
 - Review start reminder 
 - Review end reminder 
 - Task upcoming reminder  
 - Task overdue reminder 


## Power automate templates 
To use Power automate templates to create business events in Microsoft Dynamics 365 Human Resources follow these steps:
1. Go to Microsoft Power Automate. 
2. Select **Templates** from the left navigation panel.
3. Search for the template name. Ex: **Goal due reminder**.
4. Select template and the flow connection will be displayed.
5. Click **Continue**. 
6. Enter your Finance environment. 

To change the occurrence of the flow, go to **Recurrence** and update the **Interval** and **Frequency**. If the flow interval is updated from every day to every week, the flow will run once a week and send 
email notifications. 

You can update email notification in the **Conditions** section. When the **Goal due reminder** flow is ran, the email notification will be sent to all workers where the goal end date is today 
and is not completed or cancelled. To send notifications to all workers where a goal is due on a specific date, change the condition using the **Is less than and equal to**. 
