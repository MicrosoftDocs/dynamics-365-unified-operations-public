---
# required metadata

title: Create an archive object for the Intelligent Data Management Framework (AX 2012)
description: 
author: kfend
manager: AnnBe
ms date: 2017-04-04
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
ms.custom: 17931
ms.assetid: 4d3e61d1-48aa-4e39-8112-6d211a1d0209
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Create an archive object for the Intelligent Data Management Framework (AX 2012)



Overview of Archive Objects
---------------------------

An Archive Object is a hierarchical relationship tree that you create based on a driver table. The Archive Object archives transactional records from the production database, based on the rules and selection criteria you created in the Archive Object. This topic refers to archiving as copying records from the production database to the archive database, and then deleting these records from the production database. You can create an Archive Object based either on the templates that are included in IDMF or on the discovery process.

| **Caution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| To use this topic, you must have experience in the maintenance and administration of the Microsoft Dynamics AX application and database. IDMF lets you create an Archive Object that defines a hierarchical relationship tree among the Microsoft Dynamics AX application tables. You can then apply rules to select records based on specific criteria. Records matching the selection criteria from the whole relationship tree in the Archive Object are moved from the production database to the archive database. Improper use of this framework can cause unexpected results, database corruption, and application downtime requiring full database and application recovery. Exercise extreme caution, and thoroughly test your recycling strategy in a test environment before working in the production environment. |

## Overview of the data archiving process
The archive function archives records by using a scheduled archive task. At run time, an archive task completes these tasks:

-   Select qualifying records from the driver table, based on rules that are defined for the driver table.
-   Select qualifying records from all child tables, based on the parent-child relationship.
-   Copy the qualifying records from the production database to the archive database.
-   Delete the qualifying records from the production database.

## Considerations for Archive Objects, driver tables, relations, and rules
Consider the following points when working with an Archive Object:

-   Verify that the table you select as the driver table for an Archive Object is a header table, such as **SalesTable**. A good indication, although not always accurate, is that the **TableGroup** value for such a table is **WorkSheetHeader**, **Miscellaneous**, or **Transaction**.
-   Tables with a **TableGroup** value of **Main**, **Parameter**, **Group**, and **WorkSheetLine** cannot be driver tables.
-   The driver table becomes the root parent in the hierarchical relationship tree. IDMF queries the **XRefTableRelation** table to determine the parent-child relationships.
-   Archiving records based on an Archive Object may cause data inconsistency in your application in these conditions:
    -   The driver table has known parent tables.
    -   The driver table has known child tables that are not added to the Archive Object as a relation.
-   Always minimize the Archive Object, and keep only necessary relations and rules for your implementations. Consider removing a table from the Archive Object in these conditions:
    -   The table does not contain any data, and it is not likely to contain data in the future.
    -   The table stores only transient data, such as **SalesParmTable** or **SpecTrans**.
    -   The table stores open transactions, such as **CustTransOpen** or **VendTransOpen**.
    -   The table creates nested relationships. If a table appears multiple times on different levels in the relationship tree, with the same qualifying relationship condition or set of primary keys, consider keeping the occurrence only in the lowest-numbered level in the relationship tree.
-   If a table is related to the driver table and makes its own Archive Object, it is a good candidate to be a driver table itself. For example, if you use **SalesTable** as a driver table, it discovers **PurchTable** for intercompany. In this case, consider making **PurchTable** a separate Archive Object. If the driver table and the child table are from different functional areas, and if the child table is a good candidate to be archived separately, create a separate, independent Archive Object. Consider making this child table a Related Archive Object in these conditions:
    -   This driver table and its child table must be archived together because of functional or relational dependencies.
    -   You have to add rules for correct archiving of the child table. You can only add rules for the driver table. To add rules for the child table, it has to be the driver table of a Related Archive Object. Be sure that the rules you add to the Related Archive Object do not adversely affect the archiving from the parent Archive Object.
-   There may be multiple relationships between two tables. In that case, evaluate the relationships and functionality carefully. We recommend that you use only a single relationship in the Archive Object. However, you can use multiple relationships if necessary. Be sure to select a valid relationship using a unique index or primary key, if one exists.
-   Do not use the archive templates that are included with IDMF to create your Archive Objects. These templates are created in a specific Microsoft Dynamics AX application and may not match your implementation. Instead, use the discovery option to create your own objects, and compare them with the templates. Tables in the templates may not be valid for your implementation. Some valid and known tables may not appear in your discovered object. Carefully analyze any difference between the objects you created through the discovery process and the templates, to determine the cause of the difference. Manually add or remove tables from the Purge Objects and Archive Objects to fit your requirements.
-   Be sure that relationships among tables are set correctly. Be sure that the **TableGroup** property is set for all custom tables.
-   Verify that the relationship tree that you have created in the Archive Object archives the intended data from your system. An Archive Object that you create must look at all related records. Missing relationships lead to orphaned data.
-   A table in the relationship tree becomes part of the archive function and becomes disabled from the master data tables list.

| **Caution**                                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Thoroughly test the effect of your Archive Objects and your archive strategy on your database and application in a test environment that resembles your production environment. Test all business processes, and obtain user sign-off before trying to implement the Archive Objects in the production environment. |

## Overview of Related Archive Objects
The relationship tree of an Archive Object can be very complex. In order to archive data from all the related tables, complex relationship trees have to be managed. In some cases, one relationship tree has to include another relationship tree to guarantee data integrity and functionally valid archiving of data. Due to this complexity, you can create a relationship between two independent Archive Objects by adding one Archive Object in the other Archive Object. The child Archive Object is called the Related Archive Object and forms a relationship with the parent Archive Object. An archive task archives selected records from all the tables in the Archive Object and the Related Archive Object. The following steps provide a walkthrough of an Archive Object with a Related Archive Object:
1.  Use the Microsoft Dynamics AX Windows client to work with the Application Object Tree (AOT). In the AOT, expand **Data Dictionary** &gt; **Tables** &gt; **CustInvoiceSalesLink** &gt; **Relations**. Note that the **CustInvoiceSalesLink** table has two parents, **SalesTable** and **CustInvoiceJour**. Expand the **Relations** node for the **CustInvoiceJour** table. Note that the **CustInvoiceJour** table does not have a relationship with **SalesTable** in the AOT.
2.  In IDMF, click **Configure** &gt; **Archive templates/Archive Object** &gt; **SalesTable** to open the **SalesTable** Archive Object.
3.  Review the hierarchical tree, and understand the parent-child relationship. Notice that the **CustInvoiceSalesLink** table from step 1 is not in the relationship tree as a child of **SalesTable**, even though the AOT shows a relationship between the two tables. Notice that the relationship tree contains two oval shapes, named **CustInvoiceJour** and **CustPackingSlipJour**. These oval shapes represent Related Archive Objects for **SalesTable**. A Related Archive Object is an Archive Object that is part of the relationship tree of a parent Archive Object.
4.  Double-click **CustInvoiceJour**. Notice that the **CustInvoiceJour** Archive Object opens and shows the **SalesTable** in a green rectangle next to the root table, **CustInvoiceJour**. The green rectangle highlights **SalesTable** as the parent Archive Object of the **CustInvoiceJour** Archive Object. Note that the **CustInvoiceSalesLink** table is a child table of the **CustInvoiceJour** table. Double-click **SalesTable** to return to the parent Archive Object.
5.  Right-click **CustInvoiceJour**, and select **View relation**. In the **Configure Related Archive Object** window, review the relationship between the **SalesTable** and **CustInvoiceJour** tables, and then click **Close** to close the window.
6.  In the **SalesTable** Archive Object, right-click **CustInvoiceJour**, and select **Remove**. Confirm that the Related Archive Object **CustInvoiceJour** is removed.
7.  Right-click **SalesTable**, and select **Add Related Archive Object**.
8.  In the **Configure Related Archive Object** window, follow these steps:

    1.  In the **Select Related Archive Object** list, select **CustInvoiceJour**. Click **New relation**.
    2.  In the **Configure relations for Related Archive Object** pane, enter SalesTable in the **Relation name** field.
    3.  Enter a valid description in the **Relation description** field.
    4.  In the **Configure relations** pane, use the following table to select fields, and then click **Add**.
        
        | From the list          | Select the value    |
        |------------------------|---------------------|
        | **Table name**         | **SalesTable**      |
        | **Field name**         | **dataAreaId**      |
        | **Condition**          | **=**               |
        | **Related table name** | **CustInvoiceJour** |
        | **Related field name** | **dataAreaID**      |

    5.  Click **New Relation**. Using the previous step, use the **SalesID** field to create a relationship between the **SalesTable** and **CustInvoiceJour** tables. Click **Add**.
    6.  Verify that the **SalesTable** and **CustInvoiceJour** tables are related using the **DataAreaId** and **SalesID** fields.
    7.  Click **Save**. Click **OK**. Click **Close** to return to the parent SalesTable Archive Object.
    8.  Verify that the SalesTable Archive Object contains the CustInvoiceJour Related Archive Object.
    9.  Click **Save**. In the **Save as** dialog box, type SalesTable\_a, and then click **Save**. Click **OK** to continue. You must save an Archive Object with a new name.
    10. Click **Properties** on the upper-right side of the relationship tree workspace, and pin the **Properties** window to the workspace. In the relationship tree, right-click the **Related Archive Object CustInoviceJour**, and then click **Remove**. In the **Properties** window, click **Revert**. The revert action reverses the changes you have made since the last time you clicked **Save**. The revert action here brings back the Related Archive Object **CustInvoiceJour**, because you did not click **Save** after you removed the Related Archive Object.
    11. Remove the Related Archive Object **CustInvoiceJour** again. Save the Archive Object as **SalesTable\_deleted**.
    12. On the toolbar, click **Archive templates/Archive Object**. Compare the icon of the SalesTable Archive Object with other objects in the list, and notice the difference. The icon indicates that you have opened the default template and saved it as an Archive Object. You can only use an Archive Object, and not an archive template, in an archive task. Click **SalesTable**. Notice that IDMF opens the Archive Object you just saved as **SalesTable\_deleted**. IDMF lets you save multiple versions of the Archive Object and uses the most recently saved version of the Archive Object.
    13. On the toolbar, click **Show versions**. In the **Version history** window, select **SalesTable** in the **Archive template** list. Notice that the **Archive Object** list displays the different versions of **SalesTable**, with the most recent version at the top. An archive task uses the most recent version of the Archive Object.

    This walkthrough explained the concept of including a Related Archive Object in an Archive Object. You must understand the Microsoft Dynamics AX metadata and functionality thoroughly before working with an Archive Object or including a Related Archive Object in a parent Archive Object.

    Understanding the Archive Object exception list
    -----------------------------------------------

    IDMF lets you create an exception parameters list as detailed in a later section of this topic. The exception parameters list applies globally to all purge templates, Purge Objects, archive templates, and Archive Objects. In addition to the exception parameters list, IDMF lets you maintain an exception tables list specifically for Archive Objects. When you create a new Archive Object and select the driver table, IDMF displays the Archive Object exception tables window. The exception list contains tables that you can use as driver tables to create a separate and independent Archive Object. Carefully evaluate these tables to determine whether you want to include them in the relationship tree as related child tables or as Related Archive Objects. The discovery process ignores all tables in the Archive Object exception tables list and does not include them in the relationship tree, even if a relationship exists. To include a table from the Archive Object exception tables list, deselect the table, and click **Save** before you click **Continue** to begin the discovery process. In this case, the discovery process includes the deselected table if a relationship exists. You can also add other tables to the list and select to exclude the newly added table from the discovery process.

    Navigation of the Archive Object exception tables window
    --------------------------------------------------------

    The following tables provide descriptions for the controls in this window.
    #### Panes

    | Pane                        | Description                                                                                                                                           |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Main** window             | Provides the driver table, and a list of exception tables for this driver table. The list of exception tables changes, depending on the driver table. |
    | **Add new exception table** | Provides controls to add a table to the exception tables list.                                                                                        |

    #### 

    #### Buttons (main window)

    | Button       | Description                                                                                                 |
    |--------------|-------------------------------------------------------------------------------------------------------------|
    | **Save**     | Save the changes to the exception tables list, such as change to the **Status** field and any added tables. |
    | **Continue** | Continue with the discovery process for the Archive Object.                                                 |

    #### 

    #### Buttons (Add new exception tables pane)

    | Button    | Description                                                                                                                       |
    |-----------|-----------------------------------------------------------------------------------------------------------------------------------|
    | **Add**   | Add the selected table to the exception tables list. You must select a table in the **Table name** list before you click **Add**. |
    | **Clear** | Clear the **Table name** list.                                                                                                    |

    #### 

    #### Fields (main window)

    | Field                | Description                                                                                                                                                                                                                                                    |
    |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Table name**       | The name of the driver table.                                                                                                                                                                                                                                  |
    | **Exception tables** | The names of the exception tables. Each table in the list can become a driver table.                                                                                                                                                                           |
    | **Status**           | A table with the **Status** field selected is not added to the relationship tree during the discovery process, even if a relationship exists. If the **Status** field is not selected, the table is added to the relationship tree if there is a relationship. |
    | Modified by          | The Windows ID of the user who changed the status of an existing table or added a new table to the list.                                                                                                                                                       |

    #### 

    #### Fields (Add exception list)

    | Field          | Description                                                         |
    |----------------|---------------------------------------------------------------------|
    | **Table name** | Select the table that you want to add to the exception tables list. |

     Create a new Archive Object
    ----------------------------

    You can create an Archive Object by selecting a driver table and creating a relationship tree based on the driver table, instead of selecting a template that is included with IDMF. Follow these steps to create a new Archive Object:
    1.  On the toolbar, click **Create Archive Object**.
    2.  In the **Create Archive Object** dialog box, select a table from the **Driver table** list. The list excludes tables from the exception parameters list, which is covered later in this topic. Navigate to and select **WMSOrder**. A driver table is the parent table that defines the relationship tree for a specific Archive Object. In an Archive Object, the driver table may have child entities but does not have a parent entity in the relationship tree.
    3.  To continue, you must select the most unique index for the table. This index is used to create the parent-child relationship in the Archive Object. In the Unique keys field, select orderid. The **WMSOrderIdx** index is created by using the **orderid** field.
    4.  Click **Discover**. In the **Archive Object exception tables** dialog box, review the exception tables list carefully. If you want a table from the list to be included in the relationship tree, clear the **Status** field. Use the **Add new exception table** pane to add a new table to the list. The **Status** field for the newly added table is selected by default. Click **Save** to save your changes in the Archive Object exception tables window. Click **Continue** to start the discovery process and create the Archive Object.
**Note**: The **Administer** &gt; **Discovery** command lets you maintain an exception parameters list. A table that belongs to the exception parameters list, with Archive discovery selected, is excluded from the relationship tree when the Archive Object is created, even if there is a relationship between the driver table and the excluded table.

    Using the metadata that is imported from the Microsoft Dynamics AX database, the exception parameters, and the Archive Object exception tables list, IDMF generates a hierarchical relationship tree. The relationship tree starts with the driver table, in level 0, and creates a hierarchy of parent-child relationships. Make sure that your Archive Object resembles the following screen shot. Do not save the Archive Object. 
    
    ![IDMF Archive Object Expanded](./media/idmfarchiveobjectexpanded.png) 
    
    The relationship tree in this Archive Object is five levels deep. Level 0, the topmost level, contains the driver table, **WMSOrder**. Level 1 contains the child entities of the driver table. Level 2 contains child entities of tables in level 1. The last level, level 4, contains the child entities of tables in level 3. This relationship tree is created based on the following data:
    -   The Microsoft Dynamics AX metadata. The discovery process uses the metadata to create a list of related tables that form the parent-child hierarchy based on the driver table.
    -   The exception parameters. Tables that belong to the exception parameters list are filtered out of the relationship tree. Use the **Administer** menu to configure the exception parameters.
    -   The tables listed in the Archive Object exception tables dialog box. The tables you selected in this dialog box are also filtered out of the hierarchical relationship tree.

    | **Caution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Tables that you configure as master tables by clicking **Administer** &gt; **Master data tables** are replicated from the production database to the archive database by a master data synchronization task. The relationship tree created by the discovery process may include tables that are configured as master tables. Verify the tables in the relationship tree, and remove any tables that must be treated as master tables. Right-click the table, and select **Add to data replicate** to remove the table from the relationship and configure it as a master data table. If you do not remove these tables, tables in the relationship tree are automatically removed from that master data synchronization list when you save the Archive Object. |

    Verify the relationship tree, and assess the functional effect of the tree on your Microsoft Dynamics AX application. As a result of your assessment, you may have to manually add, modify, or remove some relations and rules. For example, click **Show versions** to display the Archive Object from the default template that is included with IDMF. Compare the relationship tree from the template with the relationship tree you created in the previous procedure. The relationship tree in the **WMSOrder** archive template differs from the **WMSOrder** Archive Object you created. The difference is caused by the modification made to the default template, based on the functionality assessment of the Microsoft Dynamics AX application. As demonstrated by this walkthrough, an Archive Object you create through discovery may not match the default template that is included with IDMF. Be careful with your selection of the driver table. If you select a table such as **ProdTable**, the relationship tree can go many levels deep, spanning many tables on each level. Such an Archive Object creates a complex relationship tree and increases the potential for error, and for resulting data corruption and application downtime. 
    
    ![IDMF Archive Object with Invalid Tables](./media/idmfarchiveobjectwithinvalidtables.png)
    
    The default template that is included with IDMF may not match the metadata of your Microsoft Dynamics AX implementation. A table in the default template that is not found in the metadata from the production database is marked invalid. An invalid table appears with a dotted red border, as shown in Figure 2. You must remove invalid tables. When you use fields from valid tables to create relations and rules, IDMF validates those fields. A field with a disabled configuration key is considered invalid. A valid table with invalid fields is shown with a yellow dotted border. You must either remove valid tables with invalid rules from the relationship tree or fix the relationships before you can save the Archive Object.

    Navigation of the Create Archive Object workspace
    -------------------------------------------------

    The following tables provide descriptions for the controls in this workspace.
    #### Panes

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
    <td><strong>Relationship tree</strong> pane</td>
    <td>Provides a graphical view of all the tables in the Archive Object. The following list provides controls and commands that you can use to navigate the relationship tree pane:
    <ul>
    <li>With the <strong><span class="ui">Level</span></strong> slider, you can select a level and show only the tables at the selected and higher levels.</li>
    <li>With the <strong><span class="ui">Zoom</span></strong> slider, you can change the diagram size.</li>
    <li>Right-click the driver table to work with the following commands:
    <ul>
    <li>Click <strong><span class="ui">Add Related Archive Object</span></strong> to add a Related Archive Object.</li>
    <li>Click <strong><span class="ui">Remove all invalid tables</span></strong> to remove all invalid tables, together with all their related tables, from the nested hierarchy.</li>
    </ul></li>
    <li>Right-click a child table to work with the following commands:
    <ul>
    <li>Click <strong><span class="ui">Remove</span></strong> to remove the selected table from the level, and to remove its nested child tables from the hierarchical tree. For example, the <strong>SpecTrans</strong> table appears in level 2 and level 3. If you right-click the table in level 2, and then select <strong><span class="ui">Remove</span></strong>, the table is removed from level 2, together with its nested child relations. The occurrence of the table remains intact in level 3.</li>
    <li>Click <strong><span class="ui">Select all occurrences</span></strong> to display all occurrences of the selected table and its related tables in a dotted green border. In this case, the table <strong>SpecTrans</strong> is selected in levels 2 and 3, together with all its nested child relationships.</li>
    <li>Click <strong><span class="ui">Remove all occurrences</span></strong> to remove all occurrences of the selected table and its related tables. In this case, the table <strong>SpecTrans</strong> is removed from levels 2 and 3, together with all its nested child relationships. The removed tables appear in a gray shape with a solid red border.</li>
    <li>Click <span class="ui"><strong>Add to data replicate</strong></span> to remove the selected table from the relationship tree and add it to the master tables list. This command performs these tasks:
    <ol>
    <li>Remove the selected table, together with all its nested child tables, from the relationship tree of all existing Archive Objects and archive templates.</li>
    <li>Add the selected table to the <strong><span class="ui">Recommended tables</span></strong> tab in the master data tables list (<strong><span class="ui">Administer</span></strong> &gt; <strong><span class="ui">Master data tables</span></strong>).</li>
    </ol></li>
    </ul></li>
    <li>Click <strong><span class="ui">Discover</span></strong> to regenerate the hierarchical parent-child relationship for the selected table. This command is available only when you select a table with the table group property of <strong><span class="ui">WorkSheetHeader</span></strong>.</li>
    </ul>
    <div class="alert">
    <table>
    <thead>
    <tr class="header">
    <th><strong>Note</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>A table with the symbol X in the top-right corner meets the row size or table size configuration in the Framework options window (<strong><span class="ui">Administer</span></strong> &gt; <strong><span class="ui">Framework options</span></strong>). Review these tables carefully to determine whether such tables have to be removed from the relationship and added to the master data tables list (<strong><span class="ui">Administer</span></strong> &gt; <strong><span class="ui">Master data tables</span></strong>). To add a table to the master data tables list, right-click the table, and then select <strong><span class="ui">Add to data replicate</span></strong>.</td>
    </tr>
    </tbody>
    </table>
    </div></td>
    </tr>
    <tr class="even">
    <td><strong><span class="ui">Properties</span></strong></td>
    <td>Shows properties for the selected table and provides commands that you can use for the selected table.When a table in the Archive Object contains multiple relations, you can use the <span class="ui">Relations</span> node in the tree view to disable one or more relations, as detailed later in this section.</td>
    </tr>
    <tr class="odd">
    <td><strong><span class="ui">Remove table</span></strong></td>
    <td>Provides a data grid that you can use to select tables that you want to remove from the relationship tree. This pane also provides an <span class="ui">Advanced filter</span> control that you can use to filter the data grid.</td>
    </tr>
    <tr class="even">
    <td><strong><span class="ui">Related Information</span></strong></td>
    <td>Provides additional information for some of the tables. If related information is provided, read it carefully to understand the archive relevance of the table.</td>
    </tr>
    </tbody>
    </table>

    #### 

    #### Buttons

    | Button                    | Description                                                                                                                                                                                                                                                                                              |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Remove**                | Remove tables that are selected in the data grid in the **Remove table** pane. When you remove a table, all the child tables for the selected table are removed. The removal spans the whole relationship tree, and all nested parent-child relations for the selected table's child tables are removed. |
    | **Revert**                | Reverse the modifications made to the Archive Object, back to the last save. This resembles an "undo" command.                                                                                                                                                                                           |
    | **Show allShow selected** | Show all tables or selected tables, and toggle the label of the button. Removed tables appear in gray boxes with a solid red line around them.                                                                                                                                                           |

    #### 

    #### Fields (Remove table pane)

    | Field                 | Description                                                       |
    |-----------------------|-------------------------------------------------------------------|
    | **Check boxes**       | Select tables that you want to remove from the relationship tree. |
    | **Table name**        | The name of the table.                                            |
    | **Configuration key** | The configuration key of the table.                               |
    | **Level**             | The level of the table in the relationship tree.                  |
    | **Row count**         | The number of rows in the table.                                  |

     Walkthrough: Work with an Archive Object
    -----------------------------------------

    This section provides a walkthrough for working with an Archive Object.
    1.  If you have not created the Archive Object already, create one. On the toolbar, click **Save**. In the next dialog box, read the warning message carefully, and then click **Yes**. In the **Save as** dialog box, enter **WmsOrder1**, and then click **Save**. Click **OK**.
    2.  Click the **WMSOrder** table in the hierarchy diagram.
    3.  Use the **Zoom** slider to change the diagram size so that you can read the table names easily.
    4.  In the relationship tree, move the mouse pointer over table **WMSOrder** to see the information that is displayed in the tooltip. In the relationship tree, move the mouse pointer over the **1:N relationship description** above the **WMSOrderTrans** table to see the information that is displayed in the tooltip.
    5.  In the **Properties** pane, expand each node in the tree view to see the information that is provided.
    6.  If the **Advanced** filter control does not show the selection criteria, click the **Advanced** filter arrow. Type 1 in the **Level** field, and then click **Search**. This changes the grid to show only those tables that are in level 1.
    7.  Select the **WMSOrderTrans** table by selecting the check box next to it.
    8.  In the **Properties** pane, click **Remove**. Note that table **WMSOrderTrans** and all its child tables in levels 2, 3, and 4 are removed.
    9.  Click the **Show all** button in the **Properties** pane. The diagram shows all the tables, with the removed tables in red lines.
    10. Click **Revert** to restore the original Archive Object. The diagram now reverts to the state it was in before you deleted **WMSOrderTrans** in step 8.
    11. Repeat steps 7, 8, and 9 to remove the tables again. All the removed tables appear in gray shapes with solid red lines.
    12. Click **Show selected** in the **Properties** pane to see the revised Archive Object. Verify that the removed tables are not in the Archive Object.
    13. On the toolbar, click **Save**. Click **Save** in the dialog box to save the Archive Object with a new version. You must provide a unique name when you save an Archive Object. IDMF treats the saved Archive Object as a new version of the original Archive Object or archive template.
    14. On the toolbar, click **Archive template/Archive Objects**, and then click **WMSOrder**.
    15. Verify that the Archive Object diagram does not contain the tables you removed in step 11. Switch between **Show all/****Show** selected to confirm that the removed tables still appear in gray shapes with solid red lines.
    16. In the **Properties** pane, click **Revert**. The Archive Object does not change. The revert action cannot undo the changes, because the Archive Object has been saved.
    17. On the toolbar, click **Show versions**. In the **Version history** dialog box, select **WMSOrder** from the list, and select the version of the Archive Object in the Archive Object list. Each version of the Archive Object is saved with a unique name. Therefore, each Archive Object in the list provides a different version of **WMSOrder**.
    18. Select the last item in the list, **WMSOrder**, and then click **Show** to restore the Archive Object to the first version that is included as the archive template in IDMF. The restored Archive Object differs from the Archive Object you started working with in step 1. The relationship tree in the default archive template has been adjusted based on the functional assessment of the Microsoft Dynamics AX application.
    19. On the toolbar, click **Save**. Click **Yes** to overwrite the object. In the **Save as** dialog box, enter the name for the Archive Object, and then click **Save**. Click **OK** to close the message indicating the success or failure of the save operation. Keep the Archive Object open, because it is also used in the next section.

     Archive templates/Archive Object
    ---------------------------------

    This command provides a list of archive templates and Archive Objects in your system. An archive template is a template that is included with IDMF with a predefined relationship tree. You can use an archive template as a starting point to create an Archive Object. You must review an archive template to make sure that it meets your requirements, and save it before you can use it in a scheduled archive task. This command uses the same navigation and toolbar commands as the **Create Archive Object** workspace.
    ### Walkthrough: Work with an archive template

    This section provides a walkthrough for working with an archive template.
    1.  On the toolbar, click **Archive templates/Archive Object**. Observe the icon of the **BankChequeTable** template.
    2.  Select **BankChequeTable** from the list.
    3.  Review the tables, table properties, and relationship tree to understand how the data archiving for **BankChequeTable** cascades through the relationship tree in the archive template. Make sure that this relationship tree covers your application and any customizations you may have made to the Microsoft Dynamics AX application.
    4.  On the toolbar, click **Save**. You must provide a unique name when you save an Archive Object. Change the name to BankChequeTable\_object to identify this saved object as an Archive Object. Click **Save**.
    5.  Click **OK** in the dialog box to continue.
    6.  On the toolbar, click **Archive templates/Archive Objects**. You do not see **BankChequeTable\_object** in the list. Unlike Purge Objects, Archive Objects are saved with the same name, but with a new version. In this case, the **BankChequeTable** object is created with a version name **BankChequeTable\_object**. As always, the latest version is effective.
    7.  Notice that the icon of **BankChequeTable** is changed compared to earlier, which indicates that it is saved as an object.



