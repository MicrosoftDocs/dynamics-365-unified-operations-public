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

## Check for orphaned flows

1. Sign in to Business performance analytics as a System Administrator.
2. Open a new browser tab and paste the following URL (replace `<org url>` with your organization URL, for example, `https://<org>.crm10.dynamics.com`):

   ```
   <org url>/api/data/v9.1/workflows?<flowid>
   ```

3. Based on the query results, proceed to one of the following sections:
   - If flows are returned, see [Reassign flow ownership when flows are returned](#reassign-flow-ownership-when-flows-are-returned).
   - If no flows are returned, see [Reassign flow ownership when no flows are returned](#reassign-flow-ownership-when-no-flows-are-returned).

## Reassign flow ownership when flows are returned

If the query returns records, follow these steps for each flow:

1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
2. Select the affected environment.
3. Navigate to **Resources** > **Flows**.
4. Follow [these instructions](https://learn.microsoft.com/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow) to assign new owners for each affected flow.

After adding new owners, have the new owner complete these steps:

1. Go to [Power Apps](https://make.powerapps.com/).
2. Select the correct environment in the upper right corner.
3. Go to **Flows** in the left menu.
4. Open the details of each impacted flow.

> [!NOTE]
> The flow may be in the **Shared with me** tab.

5. On the right, select **Co-Owners** > **Set primary owner**.
6. Replace the existing user with yourself.
7. Select **Save**.

## Reassign flow ownership when no flows are returned

If the query doesn't return any records, follow these steps:

1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).
2. Select the affected environment.
3. Navigate to **Resources** > **Flows**.
4. Find all flows that start with "Business performance analytics", excluding:
   - "Business performance analytics transform job"
   - "Business performance analytics initialization job"
5. Follow [these instructions](https://learn.microsoft.com/troubleshoot/power-platform/power-automate/flow-management/manage-orphan-flow-when-owner-leaves-org#assign-new-co-owners-to-an-orphaned-flow) to assign yourself as a co-owner for each affected flow.

After adding yourself as a co-owner, complete these steps:

1. Go to [Power Apps](https://make.powerapps.com/).
2. Select the correct environment in the upper right corner.
3. Go to **Flows** in the left menu.
4. Find all flows that start with "Business performance analytics", excluding:
   - "Business performance analytics transform job"
   - "Business performance analytics initialization job"

   > [!NOTE]
   > The flows may be in the **Shared with me** tab.

5. Open the details of each impacted flow.
6. On the right, select **Co-Owners** > **Set primary owner**.
7. Replace the existing user with yourself.
8. Select **Save**.
