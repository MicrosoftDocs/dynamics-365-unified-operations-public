

---
# required metadata

title: Formula designer
description: enter a key sentence
author: YuyuScheller 
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: enter AOT form names (PlanActivity, ReqSupplyDemandSchedule)
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# BOM designer functionality

[!include[banner](../includes/banner.md)]


This article describes how you can use the BOM designer page to design and work with tree structures for bills of materials (BOMs). You can click Setup to select different configurations and specify what information appears on the lines of the tree.

When you open the **BOM designer** page from the **Released products** page, it displays the hierarchy of bills of materials (BOMs) that are active and approved for the selected item, the default order site of the item, and the actual date.  

Click **Filter** to change the initial selection in the view. By setting the display principle to **Selected/Active or Selected**, you can select individual BOM or route versions to use in the view. You can select non-approved and non-active BOM versions to show or maintain in the BOM designer.  

**Note:** If you open the BOM designer from the **Bills of materials** list page, it doesn't display route information. Currently, the selection of a BOM or route version is a property of the BOM and route version, and applies to all instances of the BOM designer.  

The following sections describe the functionality that is available on the various tabs of the BOM designer.

## Analyzing a BOM structure by using the BOM designer
The BOM designer has two sections:

-   The tree view of the BOM structure.
-   The details section, which shows details of the selected data. When you select a node in the tree view, the FastTabs in the details section are updated based on that node:
    -   **BOM line details** – Shows the details of the BOM line that is selected in the tree view.
    -   **Item data** – Shows the details of the main item or the item that is used in the selected node. You can click **Edit released product** to maintain the selected item.
    -   **BOM** – Shows the header of the BOM that is related to the selected node.
    -   **Route** – Shows the header of the route that is related to the selected node.
    -   **Route operations** – Shows a preview of the operations for the route. When a BOM line that is assigned to a specific operation is selected, the operation is marked as **Component needed at operations**.

## Selecting a BOM and route
The filter that is applied for the BOM and route is displayed in the header of the BOM designer. You can change the filter by using the **Filter** dialog box. The following table describes the fields in this dialog box.

<table>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Product dimensions</td>
<td>If the selected finished product is a product master, you can define the active product dimensions for the main selection.<strong>Note:</strong> If you open the BOM designer for a product that isn't a product master, no product dimensions can be selected in the <strong>Filter</strong> dialog box.</td>
</tr>
<tr class="even">
<td>Site</td>
<td>Change the site that the BOM tree is displayed for. The default site is the default inventory site of the finished item.</td>
</tr>
<tr class="odd">
<td>Display principle</td>
<td>Select the version display principle that applies to the current BOM structure and the current route:
<ul>
<li>When the principle is set to <strong>Active or Selected/Active</strong>, the valid BOM or route version for this date is found.</li>
<li>When the principle is set to <strong>Selected/Active or Selected</strong>, you can select a BOM version or route version by clicking <strong>BOM</strong> &gt; <strong>BOM versions</strong> or <strong>Route</strong> &gt; <strong>Route versions</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Version date</td>
<td>Enter the version date for the BOM and route. The version identifies which BOM version is used on a specific date, as determined by the version dates in the BOM version setup.</td>
</tr>
<tr class="odd">
<td>From quantity</td>
<td>Filter the versions by selecting a specific from quantity. If you set a value, different BOM and route versions might be selected.</td>
</tr>
<tr class="even">
<td>Show valid only</td>
<td>When you select the check box, the tree structure shows only BOM lines that have valid dates. Right-click or double-click a BOM line to open the <strong>Edit BOM line</strong> page, where you can see the validity dates for that BOM line.</td>
</tr>
</tbody>
</table>

When you use the BOM designer to review or edit BOMs that consist of one or more levels of phantoms, the route that is associated with the top item typically spans the complete BOM hierarchy. To simplify the overview, you can lock the top-level route in the display by clicking **View** &gt; **Lock route**. To unlock the route, click **View** &gt; **Unlock route**.

## Adding and editing BOMs and BOM lines
Use the **BOM lines** or **BOM** functions to modify the BOM lines or BOM. When you select a node in the tree, the type of the node determines that functions that are available.

| Function                            | Description                                                                                               | Node type and conditions                                                                                                                                                                                                                                                                       |
|-------------------------------------|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BOM lines &gt; Edit                 | Open a dialog box where you can edit the BOM line attributes.                                             | This function is available when a BOM line node is selected.                                                                                                                                                                                                                                   |
| BOM lines &gt; Delete               | Delete a BOM line from the selected BOM.                                                                  | This function is available when a BOM line node is selected, and the BOM isn't locked for editing.                                                                                                                                                                                             |
| BOM lines &gt; Add before line      | Open a dialog box where you can select a product variant to include before the selected BOM line.         | This function is available when a BOM line node is selected.                                                                                                                                                                                                                                   |
| BOM lines &gt; Add to component BOM | Open a dialog box where you can select a product variant to include at the end of the selected BOM.       | This function is available when the node that is selected has a selected BOM. If this function isn't available, a BOM version might be missing for the selected item variant. In this case, you can click **BOM** &gt; **Create version** to create the missing version for the selected node. |
| BOM lines &gt; Add after line       | Open a dialog box where you can select a product variant to include after the selected BOM line.          | This function is available when a BOM line node is selected.                                                                                                                                                                                                                                   |
| BOM &gt; Create version             | Create a new BOM version or BOM for the product variant of the selected node.                             | This function is available when the BOM line node that is selected is linked to an item that has a production type of **BOM** or **Formula**.                                                                                                                                                  |
| BOM &gt; Calculation                | Open a dialog box where you can run the cost or sales price calculation for the selected product variant. | This function is available when the node that is selected is related to a BOM version.                                                                                                                                                                                                         |
| BOM &gt; Check                      | Validate and check the selected BOM.                                                                      | This function is available when the node that is selected is related to a BOM version.                                                                                                                                                                                                         |

## Configuring the tree view
Click **Setup** to customize the information that is shown in the tree view of the BOM designer.

| Field group | Description                                                                                                                                                  |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BOM         | Use the check boxes to select the criteria that are shown in the tree structure. The BOM designer displays the selected criteria at the bottom of both tabs. |
| Route       | Use the check boxes to select the criteria that are shown for the routes.                                                                                    |



# Formula designer

[!include[banner](../includes/banner.md)]

Use the **Formula designer** page to design and work with a formula tree structures. The designer graphically displays the formula structure. You can select different configurations and decide what information to display on the nodes of the tree.

> [!IMPORTANT]
> If you access the designer from the formula, it does not display route information, because the formula is not yet linked to a specific, finished item.

  
## Use the Designer tab

The **Designer** tab contains the following functionality:

-   A functions pane on the left part of the form that enables you to perform
    tasks such as to modify a formula version and to add formula items

-   A designer window that displays the tree structure of the formula

-   Current route information for the formula

-   A list of items

> [!NOTE]
> A site must be specified on the **Setup** tab. It must use either the default setting or one that you select. If the **Site** field is cleared, the tree does not display. If there are sub-formulas that use other sites, these do not display inside the tree. The tree displays only the information for one site at a time.

The following table shows the actions that you can perform for each function in the icon pane.

| **Function**                      | **Drag-and-drop**                               | **Click icon**   | **Right-click**      | **Double-click**               |
|-----------------------------------|-------------------------------------------------|------------------|----------------------|--------------------------------|
| Access information for the lines  | —-                                              | —-               | Line or formula      | —-                             |
| Add item                          | Formula                                         | Calculation      | —-                   | Item                           |
| Formula calculation               | —-                                              | Calculation      | Formula              | —-                             |
| Check Formula                     | —-                                              | —-               | Formula              | —-                             |
| Configuration (create/select)     | —-                                              | —-               | Configurable formula | —-                             |
| Configurations included in (view) | —-                                              | —-               | Configurable formula | —-                             |
| Configure                         | —-                                              | —-               | Configurable formula | —-                             |
| Copy lines within tree            | Copy to location. Press CTRL, and drag-and-drop | —-               | —-                   | —-                             |
| Create/Edit Formula versions      | —-                                              | Formula versions | Formula              | —-                             |
| Create/Edit route versions        | —-                                              | Route versions   | Formula              | —-                             |
| Delete                            | —-                                              | Delete record    | Line or formula      | —-                             |
| Edit line                         | —-                                              | Edit             | Line or formula      | Line                           |
| Link to operation                 | Operation number                                | —-               | —-                   | Line – insert operation number |
| Lock/Unlock route                 | —-                                              | —-               | Line or formula      | —-                             |
| Move lines within tree            | New locations                                   | —-               | —-                   | —-                             |
| Print Formula                     | —-                                              | Print            | Formula              | —-                             |
| Reload Formula                    | —-                                              | —-               | Formula              | —-                             |
| Reload route                      | —-                                              | —-               | Formula              | —-                             |
| Remove link to operation          | —-                                              | —-               | Line or formula      | Line – Delete operation number |

  
## Use the Setup tab

Use the **Setup** tab to customize the information that is shown on the **Designer** form.

| **Field group**     | **Field**             | **Description**                                                                                                                                                                                                                              |
|---------------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Search criteria** | **Display principle** | Select the version-display principle that applies to the current formula structure and the current route.                                                                                                                                    |
| —-                  | **Version date**      | Enter the version date for the formula and route. The version is used to identify which formula version to use on a specific date, as determined by the version dates in the formula-version setup.                                          |
| **Lines**           | **Show valid only**   | When the check box is selected, only formula lines that have valid dates are displayed in the tree structure. To open the **Edit formula line** form and view the validity dates for the formula line, right-click or double-click the line. |
| **Formula**         | All check-box fields  | Select the criteria to display in the tree structure. The designer displays the selected criteria at the bottom of both tabs.                                                                                                                |
| **Route**           | All check-box fields  | Select the criteria to display for the routes.                                                                                                                                                                                               |

-   When the principle is set to **Active** or **Selected/Active**, the valid
    formula or route version for this date is found.

-   The date is also used to find valid formula lines if **Show valid only** is
    selected.

  
See also


