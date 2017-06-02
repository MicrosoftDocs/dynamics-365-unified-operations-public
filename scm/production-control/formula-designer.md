---
# required metadata

title: Formula designer
description: Use the **Formula designer** to analyze and maintain formulas in a tree structured view. Click **Setup** to select different configurations and specify what information appears on the lines of the tree.
author: cvocph 
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

# Formula designer

[!include[banner](../includes/banner.md)]

When you open the **Formula designer** page from the **Released products** page, it displays the list of Co-Products as well as the hierarchy of the ingredients of the released product on the left side tree pane. The structure is derived from the hierarchy of formulas that are active and approved for the selected item and it's ingredients, the default order site of the item, and the actual date.  

Click **Filter** to change the initial selection in the view. By setting the display principle to **Selected/Active or Selected**, you can select individual formula or route versions to use in the view. You can select non-approved and non-active formula versions to show or maintain in the formula designer.  

**Note:** If you open the formula designer from the **Bills of materials** list page, it doesn't display route information. Currently, the selection of a formula or route version applies to all instances of the formula designer.  

The following sections describe the functionality that is available on the various tabs of the BOM designer.

## Analyze a formula structure by using the formula designer
The formula designer has two sections:

-   The tree view of the formula structure.
-   The details section, which shows details of the selected data. When you select a node in the tree view, the FastTabs in the details section are updated based on that node:
    -   **Formula line details** – Shows the details of the formula line that is selected in the tree view.
    -   **Item data** – Shows the details of the main item or the item that is used in the selected node. You can click **Edit released product** to maintain the selected item.
    -   **Formula** – Shows the header of the formula that is related to the selected node.
    -   **Route** – Shows the header of the route that is related to the selected node.
    -   **Route operations** – Shows a preview of the operations for the route. When a BOM line that is assigned to a specific operation is selected, the operation is marked as **Component needed at operations**.

## Select a formula and route
The filter that is applied for the formula and route is displayed in the header of the formula designer. You can change the filter by using the **Filter** dialog box. The following table describes the fields in this dialog box.

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
<td>If the selected finished product is a product master, you can define the active product dimensions for the main selection.<strong>Note:</strong> If you open the formula designer for a product that isn't a product master, no product dimensions can be selected in the <strong>Filter</strong> dialog box.</td>
</tr>
<tr class="even">
<td>Site</td>
<td>Change the site that the ingredient tree is displayed for. The default site is the default inventory site of the finished item.</td>
</tr>
<tr class="odd">
<td>Display principle</td>
<td>Select the version display principle that applies to the current formula structure and the current route:
<ul>
<li>When the principle is set to <strong>Active or Selected/Active</strong>, the valid formula or route version for this date is found.</li>
<li>When the principle is set to <strong>Selected/Active or Selected</strong>, you can select a formula version or route version by clicking <strong>formula</strong> &gt; <strong>formula versions</strong> or <strong>Route</strong> &gt; <strong>Route versions</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Version date</td>
<td>Enter the version date for the formula and route. The version identifies which formula version is used on a specific date, as determined by the version dates in the formula version setup.</td>
</tr>
<tr class="odd">
<td>From quantity</td>
<td>Filter the versions by selecting a specific from quantity. If you set a value, different formula and route versions might be selected.</td>
</tr>
<tr class="even">
<td>Show valid only</td>
<td>When you select the check box, the tree structure shows only formula lines that have valid dates. Right-click or double-click a formula line to open the <strong>Edit formula line</strong> page, where you can see the validity dates for that formula line.</td>
</tr>
</tbody>
</table>

When you use the formula designer to review or edit formulas that consist of one or more levels of phantoms, the route that is associated with the top item typically spans the complete formula hierarchy. To simplify the overview, you can lock the top-level route in the display by clicking **View** &gt; **Lock route**. To unlock the route, click **View** &gt; **Unlock route**.

## Add and edit formulas and formula lines
Use the **BOM lines** or **Formula** functions to modify the formula lines or formula. When you select a node in the tree, the type of the node determines that functions that are available.

| Function                            | Description                                                                                               | Node type and conditions                                                                                                                                                                                                                                                                       |
|-------------------------------------|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BOM lines &gt; Edit                 | Open a dialog box where you can edit the formula line attributes.                                             | This function is available when a formula line node is selected.                                                                                                                                                                                                                                   |
| BOM lines &gt; Delete               | Delete a formula line from the selected formula.                                                                  | This function is available when a formula line node is selected, and the formula isn't locked for editing.                                                                                                                                                                                             |
| BOM lines &gt; Add before line      | Open a dialog box where you can select a product variant to include before the selected formula line.         | This function is available when a formula line node is selected.                                                                                                                                                                                                                                   |
| BOM lines &gt; Add to component BOM | Open a dialog box where you can select a product variant to include at the end of the selected formula.       | This function is available when the node that is selected has a selected formula. If this function isn't available, a formula version might be missing for the selected item variant. In this case, you can click **Formula** &gt; **Create version** to create the missing version for the selected node. |
| BOM lines &gt; Add after line       | Open a dialog box where you can select a product variant to include after the selected formula line.          | This function is available when a formula line node is selected.                                                                                                                                                                                                                                   |
| Formula &gt; Create version             | Create a new formula version or formula for the product variant of the selected node.                             | This function is available when the formula line node that is selected is linked to an item that has a production type of **BOM** or **Formula**.                                                                                                                                                  |
| Formula &gt; Calculation                | Open a dialog box where you can run the cost or sales price calculation for the selected product variant. | This function is available when the node that is selected is related to a formula version.                                                                                                                                                                                                         |
| Formula &gt; Check                      | Validate and check the selected formula.                                                                      | This function is available when the node that is selected is related to a formula version.                                                                                                                                                                                                         |

## Configuring the tree view
Click **Setup** to customize the information that is shown in the tree view of the formula designer.

| Field group | Description                                                                                                                                                  |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BOM         | Use the check boxes to select the criteria that are shown in the tree structure. The formula designer displays the selected criteria at the bottom of both tabs. |
| Route       | Use the check boxes to select the criteria that are shown for the routes.                                                                                    |



