---
title: Reassign Business performance analytics flow ownership
description: Learn how to reassign ownership of Business performance analytics flows when the original owner has left the organization or is no longer available.
author: yvishwa
ms.author: yvishwa
ms.topic: how-to
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 12/09/2025
---

# Reassign Business performance analytics flow ownership

This article explains how to reassign ownership of Business performance analytics flows when the original owner has left the organization or is no longer available.

## Prerequisites

- System Administrator access to Business performance analytics
- Access to Power Platform Admin Center

### Steps

1. Sign in to Business performance analytics as a System Administrator.
2. Open a new browser tab and paste the following URL (replace `<org url>` with your organization URL, for example, `https://<org>.crm10.dynamics.com`):

   ```
   <org url>/api/data/v9.1/workflows?<flowid>
   ```

- For each flow returned:

   - Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
   - Select the affected environment.
   - Navigate to **Resources** > **Flows**.
   - Follow [these instructions](https://learn.microsoft.com/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow) to assign new owners for each affected flow.

- After adding new owners, have the new owner complete these steps:

   - Go to [Power Apps](https://make.powerapps.com/).
   - Select the correct environment in the upper right corner.
   - Go to **Flows** in the left menu.
   - Open the details of each impacted flow.
      > [!NOTE]
      > The flow may be in the **Shared with me** tab.
   - On the right, select **Co-Owners** > **Set primary owner**.
   - Replace the existing user with yourself
   - Select **Save**.

- If the query doesn't return any records, follow these steps:
   - Add share with youself 
      - Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
      - Select the affected environment.
      - Navigate to **Resources** > **Flows**.
      - Find all flows that start with "Business performance analytics", excluding:
         - "Business performance analytics transform job"
         - "Business performance analytics initialization job"
      - Follow [these instructions](https://learn.microsoft.com/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow) to assign yourself as a co-owner for each affected flow.

   - After adding yourself as the owner
      - Go to [Power Apps](https://make.powerapps.com/).
      - Select the correct environment in the upper right corner.
      - Go to **Flows** in the left menu.
      - Find all flows that start with "Business performance analytics", excluding:
         - "Business performance analytics transform job"
         - "Business performance analytics initialization job"
            > [!NOTE]
            > The flows may be in the **Shared with me** tab.
      - Open the details of each impacted flow.
      - On the right, select **Co-Owners** > **Set primary owner**.
      - Replace the existing user with yourself.
      - Select **Save**.
