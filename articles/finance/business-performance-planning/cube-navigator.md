---
title: Use Cube navigator in Business performance planning
description: Learn how to use the Cube navigator side panel to find, organise, and manage planning models in Business performance planning.
ms.date: 08/25/2026
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: article
---

# Use Cube navigator in Business performance planning

[!INCLUDE [banner](../../includes/banner.md)]

> [!NOTE]
> The Navigator experience (CubeNav) is introduced in Business performance planning version 1.16.

Cube navigator is the left-side panel on the **Cubes** page in Business performance planning. It helps you find, organize, and manage planning models (cubes) within a single workspace.

Cube navigator replaces the legacy **Draft** and **Published** lists with a more flexible structure that aligns with how finance teams organize planning models.

As financial planning and analysis processes grow, teams manage an increasing number of models across areas such as workforce, revenue, and operations. A common challenge is organizing and finding the right model efficiently.

Cube navigator addresses this challenge by introducing folders, subfolders, and search to help structure models based on business needs instead of naming conventions alone.

## Use Cube navigator

1. Go to the **Cubes** page.
1. Use the **Cube navigator** side panel.
1. Select a cube.

The selected cube loads into the workspace and is highlighted as active.

- If you don't select a cube, the first available cube is selected automatically.
- Newly created cubes are added to the list and selected by default.

### Create and organize folders

To create a folder, follow these steps:

1. In Cube navigator, select **Create folder**.
1. Enter a name.
1. Select **Confirm**.

To create a subfolder, follow these steps:

1. Select an existing folder.
1. Select **Create subfolder**.
1. Enter a name.
1. Select **Confirm**.

Folders can contain cubes and subfolders. Subfolders provide a second level of organization.

### Move and reorder cubes

Cube navigator supports drag and drop for folders, subfolders, and cubes.
You can also organize cubes by using menu actions:

- Move cubes to another folder or subfolder  
- Reorder cubes within a folder  
- Drag cubes into folders for quick organization  

### Manage cubes and folders

- Cube actions
  - Open a cube
  - Rename (draft cubes only)
  - View properties
  - Move between folders
  - Reorder  

> [!NOTE]
> You can't rename published cubes.

- Folder actions
  - Create, rename, reorder, or delete folders  

When you delete a folder, its cubes move back to the root level.

#### Search and filter

Use the **Search** box to quickly find models.

The **Search** matches:

- Cube names  
- Tags  
- Descriptions  
- Folder and subfolder names  

If no results are found, a message is displayed.

You can filter cubes by status:

- **All**  
- **Draft**  
- **Published**  

### Best practices for organizing planning models

Use these guidelines to keep your workspace clear and scalable.

- Organize by planning domain
- Use folders instead of naming conventions
- Keep the hierarchy simple
- Group related models together
 
 Organize by planning domain - Group cubes based on business function rather than technical attributes. For example:

- Workforce planning  
  - Headcount planning  
  - Compensation planning  
- Revenue planning  
  - Revenue forecast  

Use folders instead of naming conventions - Avoid encoding structure in cube names.
Instead of: `EMEA_Headcount_Forecast`
Use:

- Workforce planning  
  - EMEA  
    - Headcount planning  

Keep the hierarchy simple - Use folders for primary grouping and subfolders only when needed. Cube navigator supports:

- Top-level folders.  
- One level of subfolders.  

Group related models together - Place models that you use together in the same location. For example:

- Headcount and compensation under Workforce planning  
- Revenue and expense under Corporate planning  
