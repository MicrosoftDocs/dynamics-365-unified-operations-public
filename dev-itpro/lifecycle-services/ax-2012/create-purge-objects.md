---
# required metadata

title: Create Intelligent Data Management Framework purge objects (AX 2012)
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 21 - 54 - 56
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17951
ms.assetid: 2ecae3f6-1163-4a0f-8db3-8b53908961ce
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Create Intelligent Data Management Framework purge objects (AX 2012)



Considerations for Purge Objects, driver tables, relations, and rules
---------------------------------------------------------------------

**Note**: Before you use Purge Objects, you must have experience in the maintenance and administration of the Microsoft Dynamics AX application and database. IDMF lets you create a Purge Object that defines a hierarchical relationship tree among the Microsoft Dynamics AX application tables. You can then apply rules to selected records based on specific criteria. Records matching the selection criteria are deleted from the whole relationship tree in the Purge Object when a purge task runs. Improper use of this framework can cause unexpected results, database corruption, and application downtime requiring full database and application recovery. Exercise extreme caution, and thoroughly test your recycling strategy in a test environment before working in the production environment. Consider the following points when working with a Purge Object:

-   Tables that store transient or intermediate data are usually good candidates for a Purge Object. You must validate the data dependency and application functionality before creating a Purge Object with such tables.
-   Verify that the table you select as the driver table for a Purge Object is a header table, such as **SalesParmTable** or **SalesQuotationTable**. A good indication, although not always accurate, is that the **TableGroup** value for such a table is **WorkSheetHeader**, **Miscellaneous**, or **Transaction**.
-   Tables with a **TableGroup** value of **Main**, **Parameter**, **Group**, and **WorkSheetLine** cannot be driver tables.
-   The driver table becomes the root parent in the hierarchical relationship tree. IDMF queries the **XRefTableRelation** table to determine the parent-child relationships.
-   Removing records from a Purge Object may cause data inconsistency in your application in these conditions:
    -   The driver table has known parent tables.
    -   The driver table has known child tables that are not added to the Purge Table as a relation.
-   Always minimize the Purge Object, and keep only the necessary relations and rules for your implementations. Consider removing a table from the Purge Object in these conditions:
    -   The table does not contain any data, and it is not likely to contain data in the future.
    -   The table stores only transient data, such as **CustTransOpen** or **SpecTrans**.
    -   The table stores open transactions.
    -   The table creates nested relationships. If a table appears multiple times on different levels in the relationship tree, with the same qualifying relationship condition or set of primary keys, consider keeping the occurrence only in the lowest-numbered level in the relationship tree.
    -   There may be multiple relationships between two tables. In that case, evaluate the relationships and functionality carefully. We recommend that you use only a single relationship in the Purge Object. However, you can use multiple relationships if necessary. Be sure to select a valid relationship using a unique index or primary key, if one exists.
    -   A table is unrelated to the driver table and makes its own Purge Object. For example, if you use **ProdTable** as a driver table, it also discovers **ProdJournalTable**, which itself is a separate Purge Object. Another example is PurchReqTable. If you use **PurchReqTable** as a driver table, it discovers **PurchParmLine**, which itself is a part of the **PurchParmTable** Purge Object.
-   Verify that the relationship tree that you have created in the Purge Object actually purges the intended data from your system. A Purge Object that you create must look at all related records. Missing relationships lead to orphaned data.
-   Thoroughly test the effect of the purge on your database and application in a test environment that resembles your production environment. Test all business processes, and obtain user sign-off before trying to implement the Purge Object in the production environment.
-   When you create a Purge Object from a purge template that is included with IDMF, validate and thoroughly test the Purge Object in a test environment. These templates are created in a standard Microsoft Dynamics AX application and may not match your implementation. We recommend that you use the discovery process to create your own Purge Objects or Archive Objects, and compare them with the templates, if a matching template is available. Carefully analyze any difference between the object you created through the discovery process and the template, to determine the cause of the difference. Manually add relations and rules to, or remove relations and rules from, the Purge Objects and Archive Objects to fit your requirements.
-   Make sure that the TableGroup property is set for all custom tables in Microsoft Dynamics AX, so that the discovery process can retrieve all related tables.
-   Synchronize changes, such as adding, deleting, or updating a table in the Application Object Tree (AOT), or the data dictionary synchronization in the Microsoft Dynamics AX metadata with IDMF. Run the post-installation tasks to synchronize the metadata. For information, see the "Post-installation tasks" section in the [Data Management Framework Installation Guide](http://www.microsoft.com/en-us/download/details.aspx?id=16111).

| **Caution**                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------|
| Verify that any tables with a table group of type Transaction are part of the Purge Object only if it is acceptable to purge data from these tables. |

## Create a new Purge Object
Follow these steps to create a new Purge Object:
1.  On the toolbar, click **Create Purge Object**.
2.  In the **Create Purge Object** dialog box, select a table from the **Driver table** list. The list excludes tables from the exception list. Navigate to and select **PurchParmTable**. A driver table is the parent table that defines the relationship tree for a specific Purge Object. In a Purge Object, the driver table may have child entities, but it does not have a parent entity in the relationship tree.
3.  To continue, select the most unique index for the table. This index is used to create the parent-child relationship in the Purge Object. In the **Unique keys** field, select **ParmId**. The **ParmTableRefIdx** index is created using the **ParmID** and **TableRefID** fields. Notice that by selecting **ParmID**, you are selecting a partial key. A unique index enables the discovery process to identify related tables in the same functional area, such as Finance. If you do not select a unique index, the discovery process may find related tables from all functional areas. You must make sure that the discovery process identifies the correct functional relationships for your implementation of Microsoft Dynamics AX.
4.  Click **Discover**. IDMF uses metadata that is imported from the Microsoft Dynamics AX database, and the exception parameters list, to generate a relationship tree. The relationship tree starts with the driver table and creates a hierarchy of parent-child relationships. Make sure that your Purge Object resembles the following graphic.

![IDMF Purge object](./media/idmfpurgeobject.png) The relationship tree in this Purge Object is three levels deep. Level 0, the topmost level, contains the driver table, PurchParmTable. Level 1 contains the child entities of the driver table. The last level, level 2, contains the child entities of tables in level 1. This relationship tree is created based on the following information:
-   The Microsoft Dynamics AX metadata. The discovery process uses the metadata to create a list of related tables that form the parent-child hierarchy based on the driver table.
-   The exception parameters. Tables that belong to the exception parameters list are filtered out from the relationship tree. Use the **Administer** menu to configure the exception parameters.

Verify the relationship tree, and assess the functional effect of the tree on your Microsoft Dynamics AX application. As a result of your assessment, you may decide to manually add or remove some relations and rules. For example, when you click **Restore** in the **Properties** pane, the Purge Object is restored from the default template that ships with IDMF. The restored relationship tree in this case differs from the Purge Object you created using **PurchParmTable** as the discovery table. This is because the default template in IDMF is modified based on the functionality assessment of a standard Microsoft Dynamics AX application. The Purge Object you create through discovery may not agree with the default template that is included with IDMF, if one exists for the discovery table. Be careful with your selection of the driver table. If you select a table such as the **ProdTable** table, the relationship tree can go many levels deep, spanning many tables on each level. Such a Purge Object creates a complex relationship tree and increases the potential for error. The default template that is included with IDMF may not match the metadata of your Microsoft Dynamics AX implementation. A table in the default template that is not found in the metadata from the production database is marked invalid. An invalid table appears with a dotted red border. You must remove all invalid tables from the Purge Object. The fields that you use to create relations and rules from the valid tables are also validated. A field with a disabled configuration key is considered invalid. A valid table with invalid fields is shown with a yellow dotted border, as shown in Figure 2. You must remove any rules or relations in the Purge Object that are defined with the disabled fields. You can continue using the object after removing the invalid table or tables with invalid fields. ![IDMF Purge Object with Invalid Tables](./media/idmfpurgeobjectwithinvalidtables.png)
Navigation of the Create Purge Object workspace
-----------------------------------------------

The following tables provide descriptions for the controls in this workspace.
### Panes

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Pane</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Relationship tree pane</strong></td>
<td>Provides a graphical view of all the tables in the Purge Object. The following list describes the controls and command that you can use to navigate the relationship tree pane:
<ul>
<li>With the <strong><span class="ui">Level</span></strong> slider, you can select a level and show only the tables at the selected and higher levels.</li>
<li>With the <strong><span class="ui">Zoom</span></strong> slider, you can change the diagram size.</li>
<li>Right-click the driver table, and then click <strong><span class="ui">Remove all invalid tables</span></strong> to remove all invalid tables, together with all related tables in the nested hierarchy.</li>
<li>Right-click a table to display a menu with the following options:
<ul>
<li>Click <strong><span class="ui">Remove</span></strong> to remove the selected table and its related tables from the hierarchical tree. For example, the <strong>SpecTrans</strong> table appears in level 2 and level 3. If you right-click the table in level 2, and then select <strong><span class="ui">Remove</span></strong>, the table is removed from level 2, together with its nested child relations. The occurrence of the table remains intact in level 3.</li>
<li>Click <strong><span class="ui">Select all occurrences</span></strong> to display all occurrences of the selected table and its related tables in a dotted green border. In this case, the table <strong>SpecTrans</strong> is selected in levels 2 and 3, together with all its nested child relations.</li>
<li>Click <strong><span class="ui">Remove all occurrences</span></strong> to remove all occurrences of the selected table and its related tables. In this case, the table <strong>SpecTrans</strong> is removed from levels 2 and 3, together with all its nested child relations. The removed tables appear in a gray-colored shape with a solid red border.</li>
</ul></li>
<li>Click <strong><span class="ui">Discover</span></strong> to regenerate the hierarchical parent-child relationship for the selected table. This command is available only when you select a table with a <strong><span class="ui">TableGroup</span></strong> value of <strong><span class="ui">WorkSheetHeader</span></strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Properties</span></strong></td>
<td>Shows properties for the selected table and provides commands that you can use for the selected table. When a table in the Purge Object contains multiple relations, you can use the <span class="ui">Relations</span> node in the tree view to disable one or more relations, as detailed later in this topic.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Remove table</span></strong></td>
<td>Provides a data grid that you can use to select tables for removal from the relationship tree. This pane also provides an <span class="ui">Advanced filter</span> control that you can use to filter the data grid.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Related information</span></strong></td>
<td>Provides additional information for some of the tables. If related information is provided, read it carefully to understand the recycle relevance of the table.</td>
</tr>
</tbody>
</table>

### 

### Buttons

| Button                     | Description                                                                                                                                                                                                                                                                                                 |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Remove**                 | Remove tables that are selected in the data grid in the Remove table pane. When you remove a table, all of the child tables for the selected table are removed. The removal spans the whole relationship tree, and all nested parent-child relationships for the selected table's child tables are removed. |
| **Revert**                 | Reverse the modifications made to the Purge Object, back to the last save. This is like an "undo" command.                                                                                                                                                                                                  |
| **Show all/Show selected** | Show all tables or selected tables, and switch the label of the command button. Removed tables appear with a dotted red line around them.                                                                                                                                                                   |
| **Restore**                | Revert the Purge Object to the original source that you used to create it. If a purge template was used, the Purge Object reverts to the template that is shipped with IDMF. If the discovery process was used, the Purge Object reverts to the first Purge Object that you discovered and saved.           |

### 

### Fields (Remove table pane)

| Field                 | Description                                                           |
|-----------------------|-----------------------------------------------------------------------|
| **Check boxes**       | Select the tables that you want to remove from the relationship tree. |
| **Table name**        | The name of the table.                                                |
| **Configuration key** | The configuration key of the table.                                   |
| **Level**             | The level of the table in the relationship tree.                      |
| **Row count**         | The number of rows in the table.                                      |

## Walkthrough: Create a Purge Object
This section provides a walkthrough for working with a Purge Object.
1.  If you have not created the Purge Object already, create one.
2.  Use the **Zoom** slider to change the diagram size, so that you can read the table names easily.
3.  In the relationship tree, move the mouse pointer over the table **PurchParmTable** to see the information that is displayed in the tooltip. In the relationship tree, move the mouse pointer over the **1:N relationship description** above the **PurchParmLine** table to see the information that is displayed in the tooltip.
4.  In the **Properties** pane, expand each node in the tree view to see the information that is provided.
5.  If the **Advanced filter** control does not show the selection criteria, click the **Advanced filter** arrow. Type 1 in the level box, and then click **Search**. This changes the grid so that it shows only those tables that are in level 1.
6.  Select the **PurchParmLine** table by selecting the check box next to it.
7.  In the **Properties** pane, click **Remove**. Notice that the table **PurchParmLine**, and all its child tables in levels 1 and 2, are marked with a red border, which indicates that these tables have been removed from the relationship tree.
8.  Click the **Show all** button in the **Properties** pane. The diagram shows all the tables, with the removed tables in a gray-colored shape with solid red lines.
9.  Click **Revert** to restore the original Purge Object. The diagram now reverts to the state it was in before you deleted **PurchParmLine** in step 7.
10. Repeat steps 6, 7, and 8 to remove the tables again. You see all the removed tables in a gray-colored shape with solid red lines.
11. Click **Show selected** in the **Properties** pane to see the revised Purge Object. Verify that the removed tables are not in the Purge Object.
12. Save the Purge Object. On the toolbar, click **Save**.
13. A warning is displayed. Read the warning carefully. IDMF lets you create a Purge Object that defines a hierarchical relationship tree among the Microsoft Dynamics AX application tables. You can then apply rules to selected records based on specific criteria. Records matching the selection criteria are deleted from the entire relationship tree in the Purge Object. Improper use of IDMF can cause unexpected results, database corruption, and application downtime requiring full database and application recovery. Exercise extreme caution, and thoroughly test your recycling strategy in a test environment before working in the production environment. Click **Yes** to continue saving the Purge Object or **No** to cancel the save operation. Click **Yes** to continue with the walkthrough.
14. In the** Save as** dialog box, verify that the name is **PurchParmTable**. Click **Save**.
15. In the **Overwrite Purge Object** dialog box, click **Yes** to overwrite the Purge Object with the new version. In the **Save status** dialog box, click **OK** to continue.
16. On the toolbar, click **Purge template/Purge Objects**, and then click **PurchParmTable**. Notice that the icon of the Purge Object has changed. This change in the icon differentiates a Purge Object from a purge template.
17. Verify that the Purge Object diagram does not contain the tables you removed in step 10. Switch between **Show all/Show selected** to confirm that the removed tables still show up in the red border.
18. In the **Properties** pane, click **Revert**. The Purge Object does not change. The revert action cannot undo the changes, because the Purge Object has been saved.
19. In the **Properties** pane, click **Restore** to revert the Purge Object. The Purge Object reverts to the purge template that is included in IDMF, if one exists. If there is no default purge template, the Purge Object reverts to the first version you created through the discovery process. The restored Purge Object may be the same as, or different from, the Purge Object you started working with in step 1. The default purge template contains a modified or adjusted relationship tree based on the functional assessment of the Microsoft Dynamics AX application.
20. On the toolbar, click **Save**. Click **Yes** to overwrite the object. In the **Save status** dialog box, click **OK**. Keep the Purge Object open, because it is also used in the next section.

## Walkthrough: Disable a relation
This section provides a walkthrough for disabling relations in a table with multiple relationships.
1.  Click the **Configure** menu. On the toolbar, click **Purge template/Purge Objects**, and then select **InventJournalTable** from the list.
2.  In the relationship tree, move the mouse pointer over the **1:N relationship description** above the **InventJournalTrans** table to see the information displayed in the tooltip. Notice that this table has only one relation.
3.  In the relationship tree, move the mouse pointer over the **1:N relationship description** above the **WMSJournalTable** table to see the information displayed in the tooltip. Notice that this table has many relations.
4.  In the relationship tree, select **WMSJournalTable**.
5.  In the **Properties** pane, expand **WMSJournalTable** &gt; **Relations**. This table has many relations, and you can use the **Properties** pane to disable one or more relations. Right-click the **InventBOM** relation to open the **Disable relation** menu. The **Disable relation** menu appears only when a table has multiple relations.
6.  In the **Relations** node, right-click **InventCount**, and select **Disable relation**. Notice that the disabled relation appears in red. Right-click **InventCount**, and select **Enable relation**. Notice that the enabled relation appears in black. An excluded relation does not become part of the Purge Object. Multiple enabled relations form the "or" clause in the SQL statement that the Purge Object generates.
7.  Do not save the purge template.
    | **Caution**                                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------|
    | Exercise care, and thoroughly test the excluded relations. An erroneous or incorrect exclusion causes data corruption. |

## Purge template/Purge Objects
This command provides a list of purge templates and Purge Objects in your system. A purge template is a template that is included with IDMF with a predefined relationship tree. You can use a purge template as a starting point to create a Purge Object. You must review a purge template to make sure that it meets your requirements, and save it before you can use it in a purge task.
### Walkthrough: Work with a purge template

This section provides a walkthrough for working with a purge template.
1.  On the toolbar, click **Purge template/Purge Objects**, and then select **PurchReqTable** from the list.
2.  Review the tables, table properties, and relationship tree to understand how the delete action on the **PurchReqTable** cascades through the relationship tree in the purge template. Make sure that this relationship tree covers your application and any customizations you may have made to the Microsoft Dynamics AX application.
3.  On the toolbar, click **Save**. You can either keep the same name or change the name. Change the name to PurchReqTable\_object to identify this saved object as a Purge Object. Click **Save**.
4.  Click **OK** in the dialog box to continue.
5.  On the toolbar, click **Purge template/Purge Objects**, and compare the icons of **PurchReqTable** and **PurchReqTable\_object**.
6.  Repeat steps 1 through 3, but save the object as **PurchReqTable**, the original name.
7.  In the **Overwrite Purge Object** dialog box, click **Yes** to overwrite the object with the new version. Click **OK** to continue.
8.  Repeat step 5. Notice that the icons of a Purge Object and a saved purge template are same. This is because when you save a purge template, it becomes a Purge Object.



