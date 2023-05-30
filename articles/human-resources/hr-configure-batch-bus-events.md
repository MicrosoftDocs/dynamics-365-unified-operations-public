---
# required metadata

title: Configure batch-based business events
description: This article describes how to configure business events to run in a batch in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 5/23/2023
ms.custom:

---

# Configure batch-based business events

[!INCLUDE [PEAP](../includes/peap-2.md)]

Customers can configure business events to run in a batch. This capability gives customers an easy way to configure and set up business events that are linked to a point in time. Business events that are available to run in a batch can be found at **Human resources shared parameters** \> **Business events**.

## Examples

Here are some examples of Human Resources business events that can run in a batch:

- Employee start date is approaching
- Course due soon 
- Certificate overdue 
- Position transition date is approaching

## Configure business events to run in a batch

1. Go to the business event catalog.
2. Select the endpoints of the business events.
3. Select **Activate** to activate the business events.
4. On the **Human Resources shared parameters** page, select **Business events**.
5. In the **Days** field, enter the batch job recurrence in days.
6. Select **Create batch jobs**, and then select **OK**.

If you select **Set default values**, all the values will be reset.
