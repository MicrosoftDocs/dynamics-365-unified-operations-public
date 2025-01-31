---
title: BOM designer functionality
description: Learn how you can use the BOM designer page to design and work with tree structures for bills of materials (BOMs) with an outline on analyzing BOM structures.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: BOMDesigner, BOMDesignerSetup, BOMDesignerFilterDialog, BOMDesignerBOMVersion, BOMChangeLine
ms.topic: how-to
ms.date: 01/31/2025
ms.custom: 
  - bap-template
---

# BOM designer functionality

[!include [banner](../includes/banner.md)]

This article describes how you can use the BOM designer page to design and work with tree structures for bills of materials (BOMs). To choose different configurations and specify what information appears on the lines of the tree, select **Setup**.

When you open the **BOM designer** page from the **Released products** page, it displays the hierarchy of bills of materials (BOMs) that are active and approved for the selected item, the default order site of the item, and the actual date.  

To change the initial selection in the view, select **Filter**. By setting the display principle to **Selected/Active or Selected**, you can select individual BOM or route versions to use in the view. You can select non-approved and non-active BOM versions to show or maintain in the BOM designer.  

> [!NOTE]
> If you open the BOM designer from the **Bills of materials** list page, it doesn't display route information. Currently, the selection of a BOM or route version is a property of the BOM and route version, and applies to all instances of the BOM designer.  

The following sections describe the functionality that is available on the various tabs of the BOM designer.

## Analyzing a BOM structure by using the BOM designer

The BOM designer has two sections:

- The tree view of the BOM structure.
- The details section, which shows details of the selected data. When you select a node in the tree view, the FastTabs in the details section are updated based on that node:
    - **BOM line details** – Shows the details of the BOM line that is selected in the tree view.
    - **Item data** – Shows the details of the main item or the item that is used in the selected node. To maintain the selected item, select **Edit released product**.
    - **BOM** – Shows the header of the BOM that is related to the selected node.
    - **Route** – Shows the header of the route that is related to the selected node.
    - **Route operations** – Shows a preview of the operations for the route. When a BOM line that is assigned to a specific operation is selected, the operation is marked as **Component needed at operations**.

## Selecting a BOM and route

The filter that is applied for the BOM and route is displayed in the header of the BOM designer. You can change the filter by using the **Filter** dialog box. The following table describes the fields in this dialog box.

| Field | Description |
|--|--|
| Product dimensions | If the selected finished product is a product master, you can define the active product dimensions for the main selection. **Note:** If you open the BOM designer for a product that isn’t a product master, no product dimensions can be selected in the **Filter** dialog box. |
| Site | Change the site that the BOM tree is displayed for. The default site is the default inventory site of the finished item. |
| Display principle | Select the version display principle that applies to the current BOM structure and the current route: <ul><li>When the principle is set to **Active or Selected/Active**, the valid BOM or route version for this date is found.</li><li>When the principle is set to **Selected/Active or Selected**, you can select a BOM version or route version by selecting **BOM** \> **BOM versions** or **Route** \> **Route versions**.</li></ul> |
| Version date | Enter the version date for the BOM and route. The version identifies which BOM version is used on a specific date, as determined by the version dates in the BOM version setup. |
| From quantity | Filter the versions by selecting a specific from quantity. If you set a value, different BOM and route versions might be selected. |
| Show valid only | When you select the check box, the tree structure shows only BOM lines that have valid dates. Right-click or double-click a BOM line to open the **Edit BOM line** page, where you can see the validity dates for that BOM line. |

When you use the BOM designer to review or edit BOMs that consist of one or more levels of phantoms, the route that is associated with the top item typically spans the complete BOM hierarchy. To simplify the overview, you can lock the top-level route in the display by selecting **View** \> **Lock route**. To unlock the route, select **View** \> **Unlock route**.

## Adding and editing BOMs and BOM lines

Use the **BOM lines** or **BOM** functions to modify the BOM lines or BOM. When you select a node in the tree, the type of the node determines that functions that are available.

| Function | Description | Node type and conditions |
|--|--|--|
| BOM lines \> Edit | Open a dialog box where you can edit the BOM line attributes. | This function is available when a BOM line node is selected. |
| BOM lines \> Delete | Delete a BOM line from the selected BOM. | This function is available when a BOM line node is selected, and the BOM isn't locked for editing. |
| BOM lines \> Add before line | Open a dialog box where you can select a product variant to include before the selected BOM line. | This function is available when a BOM line node is selected. |
| BOM lines \> Add to component BOM | Open a dialog box where you can select a product variant to include at the end of the selected BOM. | This function is available when the node that is selected has a selected BOM. If this function isn't available, a BOM version might be missing for the selected item variant. In this case, select **BOM** \> **Create version** to create the missing version for the selected node. |
| BOM lines \> Add after line | Open a dialog box where you can select a product variant to include after the selected BOM line. | This function is available when a BOM line node is selected. |
| BOM \> Create version | Create a new BOM version or BOM for the product variant of the selected node. | This function is available when the BOM line node that is selected is linked to an item that has a production type of **BOM** or **Formula**. |
| BOM \> Calculation | Open a dialog box where you can run the cost or sales price calculation for the selected product variant. | This function is available when the node that is selected is related to a BOM version. |
| BOM \> Check | Validate and check the selected BOM. | This function is available when the node that is selected is related to a BOM version. |

## Configuring the tree view

To customize the information that is shown in the tree view of the BOM designer, select **Setup**.

|  | Description |
|--|--|
| **BOM** | Use the check boxes to select the criteria that are shown in the tree structure. The BOM designer displays the selected criteria at the bottom of both tabs. |
| **Route** | Use the check boxes to select the criteria that are shown for the routes. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
