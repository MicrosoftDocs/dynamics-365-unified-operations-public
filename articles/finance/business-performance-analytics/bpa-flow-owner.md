---
title: Reassign Business performance analytics flow ownership
description: Learn how to reassign ownership of Business performance analytics flows when the original owner has left the organization or is no longer available.
author: yashkv1
ms.author: yvishwa
ms.topic: how-to
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 12/09/2025
---

# Reassign Business performance analytics flow ownership

This article explains how to reassign ownership of Business performance analytics flows when the original owner leaves the organization or is no longer available.

## Prerequisites

- System Administrator access to Business performance analytics
- Access to Power Platform Admin Center

### Steps

1. Sign in to Business performance analytics as a System Administrator.
1. Open a new browser tab and paste the following URL (replace `<org url>` with your organization URL, for example, `https://<org>.crm10.dynamics.com`):

   ```
   <org url>/api/data/v9.1/workflows?<flowid>
   ```

For each flow returned:
  - Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
  - Select the affected environment.
  - Navigate to **Resources** > **Flows**.
  - To assign new owners for each affected flow, see [Manage orphan flows](/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow).

After adding new owners, follow these steps:
1. Go to [Power Apps](https://make.powerapps.com/).
2. Select the correct environment in the upper right corner.
3. Go to **Flows** in the left menu.
4. Open the details of each impacted flow.
      > [!NOTE]
      > The flow might be in the **Shared with me** tab.
5. On the right, select **Co-Owners** > **Set primary owner**.
6. Replace the existing user with yourself.
7. Select **Save**.

If the query doesn't return any records, follow these steps:
1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
2. Select the affected environment.
3. Navigate to **Resources** > **Flows**.
4. Find all flows that start with "Business performance analytics", excluding:
   - "Business performance analytics transform job"
   - "Business performance analytics initialization job"
5. To assign yourself as a co-owner for each affected flow, see [Manage orphan flows](/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow).


After adding yourself as the owner:
1. Go to [Power Apps](https://make.powerapps.com/).
2. Select the correct environment in the upper right corner.
3. Go to **Flows** in the left menu.
4. Find all flows that start with "Business performance analytics", excluding:
      - "Business performance analytics transform job"
      - "Business performance analytics initialization job"
            > [!NOTE]
            > The flows might be in the **Shared with me** tab.
5. Open the details of each impacted flow.
6. On the right, select **Co-Owners** > **Set primary owner**.
7. Replace the existing user with yourself.
8. Select **Save**.
