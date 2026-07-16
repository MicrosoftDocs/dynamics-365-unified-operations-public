---
# required metadata

title: Power Automate template-based business events
description: This article describes the templates that are available for Human Resources business events.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: how-to
ms.date: 6/11/2026
ms.custom:

---

# Power Automate template-based business events

The following templates are available for Microsoft Dynamics 365 Human Resources:

- Goal due reminder
- Review start reminder
- Review end reminder
- Task upcoming reminder
- Task overdue reminder

## Power Automate templates

To use Power Automate templates to create business events in Dynamics 365 Human Resources, follow these steps:

1. Open Power Automate.
1. On the left navigation pane, select **Templates**.
1. Search for the template name (for example, **Goal due reminder**).
1. Select the template. The flow connection is shown.
1. Select **Continue**.
1. Enter your Dynamics 365 Finance environment.

To change the recurrence of the flow, go to **Recurrence**, and update the **Interval** and **Frequency** fields. If you update the flow interval from every day to every week, the flow runs once a week and sends email notifications.

You can update the email notification in the **Conditions** section. When the **Goal due reminder** flow runs, it sends the email notification to all workers where the goal end date is the current date, and the goal isn't completed or canceled. To send notifications to all workers where a goal is due on a specific date, change the condition by using **Is less than and equal to**.
