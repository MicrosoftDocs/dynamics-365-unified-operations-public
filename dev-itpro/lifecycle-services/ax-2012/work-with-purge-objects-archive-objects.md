---
# required metadata

title: Intelligent Data Management Framework purge and archive objects (AX 2012)
description: 
author: annbe
manager: AnnBe
ms.date: 2015-12-04 19 - 06 - 53
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
ms.custom: 17521
ms.assetid: e28ba163-69da-45a8-b04a-c8510296791d
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: 
ms.dyn365.version: 2012

---

# Intelligent Data Management Framework purge and archive objects (AX 2012)



Add/Edit rules
--------------

A rule is the criterion that is used to filter records when a purge task or an archive task runs. This command lets you work with rules in a Purge Object or an Archive Object. The rules generally apply to the driver table, but can also be applied to a related child table. For example, the Purge Object **ProdJournalTable** includes a rule for the **ProdTable**, which is not the driver table. Regardless of how you create these rules, the "where" clause always applies to the driver table. You must understand the effect of your rule on the Purge Object or Archive Object before applying any rule. On the toolbar, click **Add/Edit rules** to open the **Add/Edit rules** window.

### Navigation of the Add/Edit rules window

The following tables provide descriptions for the controls in the **Add/Edit rules** window.
#### Panes

| Pane                          | Description                                                                                                                                                                           |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Rule collection**           | Contains a list of the rules in the Purge Object or Archive Object, and commands to create a new rule, add an expression to the existing rule, or delete a rule or an expression.     |
| **Configure rules for purge** | Provides an area to enter or modify the rule name, description, and conditions. Also provides commands to add the rule to, or update it in, the list in the **Rule collection** pane. |
| **Conditional information**   | Lets you specify conditions, or the selection criteria, for the Purge Object.                                                                                                         |

#### 

#### Buttons

#### Add/Edit rules window

| Button    | Description                                                                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Save**  | Save the changes that you made to the list in the **Rule collection** pane to the database.                                                                 |
| **Close** | Close the **Add/Edit rules** window. You are prompted to confirm the close or save your changes if you try to close the window without saving your changes. |

#### 

#### Rule collection pane

| Button             | Description                                                                                                                                                                  |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **New rule**       | Create a new rule. When you have multiple rules in the Purge Object or Archive Object, they form the "and" condition in the "where" clause of the SQL statement.             |
| **Add expression** | Create a new expression. An expression is a condition that is added to an existing rule. An expression creates an "or" condition in the "where" clause of the SQL statement. |
| **Delete**         | Delete the selected rule or expression.                                                                                                                                      |

#### 

#### Configure rules pane

| Button     | Description                                                                         |
|------------|-------------------------------------------------------------------------------------|
| **Add**    | Add the new rule or expression to the list in the **Rule collection** pane.         |
| **Update** | Update the selected rule or expression in the list in the **Rule collection** pane. |
| **Cancel** | Cancel the add or update action.                                                    |

#### 

#### Fields (across all panes)

| Field                | Description                                                                                                                                                                                        |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Rule name**        | The name of the rule or expression.                                                                                                                                                                |
| **Rule**             | The condition that you create based on the table name, the field name, and a conditional operator. This condition forms the "where" clause in the SQL statement.                                   |
| **Rule description** | A description of the rule. Enter a new description or modify an existing description here.                                                                                                         |
| **Table name**       | The table that you select from the list of all tables in the Purge Object or Archive Object.                                                                                                       |
| **Field name**       | The name of the field that you select from the list of all fields for the selected table.                                                                                                          |
| **Condition**        | The condition that you place on the table and the field. The condition list changes, depending on the field selections.                                                                            |
| **Value**            | The **Value** field switches between a text box and a list. You can select a value from the list, but cannot enter a value in the text box here. You enter the value when you create a purge task. |

### 

### Walkthrough: Add or modify a rule in a Purge Object

This section provides a walkthrough to add or modify a rule in a Purge Object.
| **Caution**                                                                                                                                                                                                                                                                                                                                                                                           |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| This walkthrough deletes and recreates an existing rule from the Purge Object for ease of learning. You must have an excellent understanding of the database design, data flow, process flow, and application functionality of the Microsoft Dynamics AX application to work with rules. An error can cause data corruption or application downtime requiring full database and application recovery. |

1.  Click **Configure** &gt; **Purge templates/Purge Object** &gt; **PurchParmTable** to open the **PurchParmTable** Purge Object. This walkthrough assumes that you are working with the Purge Object that was created from the default purge template. If you have modified the Purge Object in any way, click **Restore** to restore the Purge Object to the original version.
2.  On the toolbar, click **Add/Edit rules** to open the **Add/Edit rules** window.
3.  In the **Rule collection** pane, click the first row in the data grid to select the rule **PurchParmTable.ParmJobStatus = Executed**. Click **Delete**. Click **OK** in the **Delete** dialog box.
4.  Click **New rule**. In **Configure rules for purge**, set the following field values:
    1.  In the **Rule name** field, type Clean up.
    2.  In the **Rule description** field, type What should be cleaned up?
    3.  In the **Table name** list, select **PurchParmTable**.
    4.  In the **Field name** list, select **ParmJobStatus**.
    5.  In the **Condition** list, select **=**.
    6.  In the **Value** field, select **Executed** from the list.

5.  Click **Add**, and verify that the rule is added to the data grid in the **Rule collection** pane.
6.  Click **Save**. In the **Rules** dialog box, click **OK** to continue.
7.  Click **Close** to close the window and return to the Purge Object.

### Walkthrough: Add or modify a rule in an Archive Object

This section provides a walkthrough to add or modify a rule in an Archive Object.
1.  Click **Configure** &gt; **Archive templates/Archive Objects** &gt; **SalesTable** to open the **SalesTable** Archive Object. This walkthrough assumes that you are working with the Archive Object that was created from the default archive template. If you have modified the Archive Object in any way, use the **Show versions** command on the toolbar to revert to the original archive template that is included with the Data Management Framework.
2.  On the toolbar, click **Add/Edit rules** to open the **Add/Edit rules** window.
3.  In the **Rule collection** pane, click the second row in the data grid to select the rule **SalesTable.SalesStatus In Canceled, Invoiced**. Click **Delete**. Click **OK** in the **Delete** dialog box.
4.  In the **Rule collection** pane, click **Add expression**, and set the following field values:
    1.  In the **Rule name** field, type Status.
    2.  In the **Rule description** field, type Status values considered for archival.

5.  In the **Conditional information** pane, set the following field values:
    1.  In the **Table name** list, select **SalesTable**.
    2.  In the **Field name** list, select **SalesStatus**.
    3.  In the **Condition** list, select **In**.
    4.  In the **Value** field, select **Cancelled and Invoiced** from the list.

6.  Click **Add**, and verify that the rule is added to the data grid in the **Rule collection** pane.
7.  Click **Save**. In the **Rules** dialog box, click **OK** to continue.
8.  Click **Close** to close the window and return to the Archive Object.

## Add relations
This command lets you manually add a table to the Purge Object or Archive Object, and establish a relationship. You may have to manually add a relationship if you have custom tables in the Microsoft Dynamics AX application without a metadata relationship in the Application Object Tree (AOT). To add a relation, select a table by clicking it in the relationship tree diagram. The table you select becomes the parent table, and the table you add becomes the child in the relationship. On the toolbar, click **Add relations** to open the **Add relations** window.
### Navigation of the Add relations window

The following tables provide descriptions for the controls in the **Add relations** window.
#### Panes

| Pane                    | Description                                                                                                                                                                                                                        |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Relationships**       | Provides a list of relations that you created in the Purge Object or Archive Object. Also provides commands to create a new relation or delete an existing relation.                                                               |
| **Configure relations** | Provides an area to enter or modify the relation name, description, and conditions. Also provides commands to add the relation to, or update it in, the list in the **Relationships** pane, or to cancel the add or update action. |

#### 

#### Buttons

| Button    | Description                                                                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Save**  | Save the changes that you made to the list in the **Relationships** pane to the database.                                                                   |
| **Close** | Close the **Add relations** window. If you try to close the window without saving your changes, you are prompted to confirm the close or save your changes. |

#### 

#### Relationships pane

| Button           | Description                                                                                                                                               |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **New relation** | Create a new relation, or a new condition for an existing relation.                                                                                       |
| **Delete**       | Delete the selected relation or condition. You cannot modify added relations. You must delete the relations, and then add them again to make any changes. |

#### 

#### Configure relations pane

| Button     | Description                                                                          |
|------------|--------------------------------------------------------------------------------------|
| **Add**    | Add a new relation or condition to the list in the **Relationships** pane.           |
| **Update** | Update the selected relation or condition in the list in the **Relationships** pane. |
| **Cancel** | Cancel an add or update action.                                                      |

#### 

#### Fields

| Field                       | Description                                                                                                                                                                                                                                           |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Include child relations** | Select this field if you have to add all the child entities of the relation that you are adding to the relationship tree. If you clear the field, the child entities of the table you are adding are not added to the Purge Object or Archive Object. |

#### 

#### Relationships pane

| Field                | Description                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **RelationsDefined** | A list of the relations in the Purge Object or Archive Object, and the conditions for each relation. This field becomes available in the list when you add a relation. |

#### 

#### Configure relations pane, Table relations area

| Field                  | Description                                                                                                                                                        |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Relation name**      | The name of the relation. You must enter a relation name to continue.                                                                                              |
| **Table name**         | The table that you selected in the Purge Object or Archive Object. You can't change this value in the window. This table is the parent entity in the relationship. |
| **Field name**         | Select the field that you want to use in the relationship.                                                                                                         |
| **Condition**          | By default, the condition is **=**. You cannot change the condition.                                                                                               |
| **Related table name** | Select the table that you are adding from the list. This table is the child entity in the relationship.                                                            |
| **Related field name** | Select the field that you want to use in the relationship.                                                                                                         |

#### 

#### Configure relations pane, Conditional information area

| Field          | Description                                                                                        |
|----------------|----------------------------------------------------------------------------------------------------|
| **Table name** | Select a table from the list. You can select either the parent or the child from the relationship. |
| **Field name** | Select the field that you want to use in the condition.                                            |
| **Condition**  | Select the condition that you want to use.                                                         |
| **Value**      | Enter the value for the condition.                                                                 |

### 

### Walkthrough: Add a relation in a Purge Object

This section provides a walkthrough to add a relation in a Purge Object.
1.  Click **Configure** &gt; **Purge templates/Purge Objects**, and then select **ProjJournalTable** from the drop-down list.
2.  In the Purge Object, click the **ProjJournalTable** table in level 0, and then click **Add relations** on the toolbar.
3.  In the **Add relations** dialog box, click **New relation**.
4.  In the **Relation name** field, enter a valid name for the relation.
5.  In the **Table relations** area, follow these steps to add the relation:
    1.  From **Field name** list, select **JournalId**.
    2.  From the **Related table** name list, select **JournalError**.
    3.  From the **Related field name** list, select **JournalId**.

6.  Click **Add**.
7.  In the **Add Relations** dialog box, click **New relation** to add a condition to the relation you just added.
8.  In the **Conditional information** area, follow these steps to add a condition:
    1.  From the **Table name** list, select a table that you want to use in the condition.
    2.  From the **Field name** list, select the field that you want to use in the condition.
    3.  From the **Condition** list, select the condition.
    4.  From the **Value** list, select the value.

9.  Click **Add** to add the condition to the data grid.
10. Click **Save**. Click **OK** to continue.
11. In the Purge Object, verify that the JournalError table you just added is shown as a child entity in level 1.
12. Save the Purge Object.

### Walkthrough: Add a relation in an Archive Object

1.  Click **Configure** &gt; **Archive templates/Archive Objects**, and then select **SalesTable** from the drop-down list.
2.  In the Archive Object, click the **DocuRef** table in level 1, and then click **Add relations** on the toolbar.
3.  In the **Add relations** dialog box, click **New relation**.
4.  In the **Relation name** field, enter a valid name for the relation.
5.  In the **Table relations** area, follow these steps to add the relation.
    1.  From the **Field name** list, select **ValueRecId**.
    2.  From the **Related table name** list, select **DocuValue**.
    3.  From the **Related field name** list, select **RecId**.
    4.  Click **Add**.

6.  In the **Add Relations** dialog box, click **New relation** to add a condition to the relation you just added.
7.  In the Conditional **information** area, follow these steps to add a condition:
    1.  From the **Table name** list, select a table that you want to use in the condition.
    2.  From the **Field name** list, select the field that you want to use in the condition.
    3.  From the **Condition** list, select the condition.
    4.  From the **Value** list, select the value.
    5.  Click **Add** to add the condition to the data grid.

8.  Click **Save**. Click **OK** to continue.
9.  In the Archive Object, verify that the **DocuValue** table you just added is shown as a child entity in level 1.
10. Save the Archive Object.

## Export
This command lets you export a Purge Object or an Archive Object to a file in XML format. Follow these steps to export a Purge Object:
1.  Click **Configure** &gt; **Purge template/Purge Objects**, and then select **PurchParmTable** from the list.
2.  On the toolbar, click **Export** to open the **Export Object** dialog box.
3.  By default, the file name is the driver table, which is **PurchParmTable** in this case. Navigate to a location, and then click **Save**. Click **OK** to continue.
4.  Locate the saved file, and open it in a Web browser. Review the file to understand the schema and its relationship to the graphical representation of the Purge Object. **Note:** You can take similar steps to export an Archive Object. **Note:** On the toolbar, the **Import** command appears before the **Export** command.

## Import
This command lets you import a Purge Object or an Archive Object in XML format. The following walkthrough provides hands-on instruction to reinstate a modified Purge Object to the state it was in at the time of export:
1.  Click **Configure** &gt; **Purge template/Purge Objects**, and then select **PurchParmTable** from the drop-down list.
2.  Use the **Advanced** filter to filter the data grid in the **Remove table** pane so that it shows only tables in level 1.
3.  Select all tables in the data grid, and then click **Remove**.
4.  Confirm that the relationship tree contains only **PurchParmTable**.
5.  On the toolbar, click **Save** to save the Purge Object. Respond to the prompt, and overwrite the object.
6.  On the toolbar, click **Import**. In the **Select a valid XML file** dialog box, navigate to the location of the file from the previous section, and then click **Open**. Click **OK** to continue.
7.  The Purge Object is now in the same state it was in when you exported it in the previous section. **Note:** You can take similar steps to import an Archive Object.

## Save
This command lets you save a Purge Object, or save a newer version of an Archive Object. You must save a purge template as a Purge Object before you can use it in a purge task. You must save an archive template as an Archive Object before you can use it in an archive task. The archive function does not let you overwrite an existing Archive Object. When you save an archive template or an Archive Object, you always create a new version of the Archive Object. The archive task always uses the most recent version of the Archive Object you save. Working with different versions of Archive Objects is covered in a later section of this topic.
Show versions
-------------

This command lets you work with different versions of an Archive Object. Use the following walkthrough to understand this functionality:
1.  Click **Configure** &gt; **Archive templates/Archive Object** &gt; **BankDeposit** to open the **BankDeposit** Archive Object.
2.  Review the Archive Object to make sure that the relationship hierarchy, tables, and rules that are contained in this Archive Object apply to your Microsoft Dynamics AX implementation.
3.  On the toolbar, click **Save**. In the **Save as** dialog box, enter a name for the Archive Object. You must provide a new name for this version of the Archive Object. If the name that you provide is already used by a different version of the Archive Object, you receive an error message. Enter BankDeposit\_1, and then click **Save**.
4.  Click **OK** to continue.
5.  On the toolbar, click **Show versions**. In the **Version history** dialog box, select **BankDeposit** from the **Archive template** list. The Archive Object list contains the different versions of the Archive Object you saved. The list contains the most recent version at the top, and therefore you see BankDeposit\_1 at the top of the list.
6.  Select any version, and then click **Show in the Archive Object list** to work with that version of the Archive Object. If you make any changes to this version and save it, the saved version becomes the most recent version and is used by the archive task at run time.
7.  Click **Close** to close the **Version history** dialog box.
8.  On the toolbar, click **Archive templates/Archive Object** &gt; **BankDeposit** to open the . **Note:** The Data Management Framework opens the most recent version of the Archive Object that you saved. The archive task uses the most recent version of the Archive Object at run time.

## Validate all
This command lets you programmatically validate all templates and objects. The purge templates and archive templates that are included with the Data Management Framework are created based on functional validation of a standard Microsoft Dynamics AX application. Your installation may not have the same license, configuration, and security keys. As a result, you have to validate the default templates against your implementation before you can use them as Archive Objects or Purge Objects. This command provides a programmatic way to validate all purge templates or all archive templates with a single click. This functionality only works with templates that are not validated yet, and ignores any previously validated templates. During the validation process, the Data Management Framework optionally removes tables from all templates and objects that have these characteristics:
-   They are not in the production database of your Microsoft Dynamics AX implementation.
-   They have a relationship or a rule on a field that has a disabled configuration key in the production database.
-   They have a record count of 0 (zero).

On the toolbar, click **Validate all** to open the **Validate all templates and Objects** window.
### Navigation of the Validate all templates and Objects window

The following tables provide descriptions for the controls in the **Validate all templates and Objects** window.
#### Buttons

| Button    | Description                                                                                                                                                                                                                                                                                                           |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Save**  | Save the changes. When you work with purge templates and Purge Objects, all existing purge templates and Purge Objects are overwritten. When working with archive templates and Archive Objects, you must provide a suffix. The changes are saved as new versions, with a suffix value that is used for the new name. |
| **Clear** | Clear the values for all the fields in the window.                                                                                                                                                                                                                                                                    |
| **Close** | Close the window.                                                                                                                                                                                                                                                                                                     |

#### 

#### Fields

| Field                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Select an object type**             | From the list, select **Purge** to validate all purge templates and Purge Objects. Select **Archive** to validate all archive templates and Archive Objects.                                                                                                                                                                                                                                                                                                                                                                |
| **Suffix name**                       | This field is only available when you select **Archive** from the **Select an object type** list. When validating objects, you overwrite existing purge templates and Purge Objects. However, you must use a suffix value to save the new versions of archive templates and Archive Objects. The suffix value is used to create a new name for the archive templates and Archive Objects. For example, if you enter 1 as the suffix name, the BankDeposit archive template is saved as BankDeposit\_1.                      |
| **Remove invalid tables**             | Select this field to remove all tables that are contained in templates and objects that are not in the production database. Removing a table from the templates and objects also removes related child tables from the relationship hierarchy, if there are any.                                                                                                                                                                                                                                                            |
| **Remove tables with invalid fields** | The templates and objects may be using invalid fields in relationships and rules. A field that is not valid can be caused by your license, disabled security keys, disabled configuration keys, or incomplete post-installation tasks, such as the database synchronization. Select this field to remove all tables that contain fields that are not valid from templates and objects. Removing a table from the templates and objects also removes related child tables from the relationship hierarchy, if there are any. |
| **Remove tables with zero row**       | Select this field to remove all tables without rows from all templates and objects. Removing a table from the templates and objects also removes related child tables from the relationship hierarchy, if there are any.                                                                                                                                                                                                                                                                                                    |



