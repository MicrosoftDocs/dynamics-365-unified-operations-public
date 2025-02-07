---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Corrective and preventive action (CAPA)

## Corrective and preventive action (CAPA) overview

Corrective and preventive action (CAPA) management lets you create and maintain records of the actions taken to manage and resolve non-conformities or defects. By planning, tracking, and analyzing CAPA cases, you can develop efficient processes that can also help to resolve similar issues. CAPA management provides for a formal and controlled process for managing various types of issues arising from manufacturing, engineering, quality, or data quality sources.

CAPA management:

- Implements a case management infrastructure to identify, correct, and prevent future problems.

- Leads to corrective and/or preventive actions.

- Provides a tool to drive continuous improvement

- Provides a closed-loop system that meets current Good Manufacturing Practice (cGMP) requirements and U.S. Food and Drug Administration (FDA) expectations, which mandate a repeatable, systematic failure investigation and root cause analysis.

CAPA management in Supply Chain Management lets you capture issues and investigate, evaluate, and determine the root cause or causes of each problem so you can find a solution and decide how best to implement it. CAPA management allows you to capture and track corrective and preventive actions and then monitor and review their effectiveness. It provides features that automate the process to help drive continuous improvement. This approach supports the core disciplines for various quality standards such as Six Sigma and ISO-9000. The solution is role-based, supports electronic records and electronic signatures, and is fully compliant with FSA Title 21 CFR Part 11 regulations.

Supply Chain Management CAPA management features provide:

- Unlimited and flexible CAPA processes – A CAPA process is a user-defined list of activities that must be executed to bring a CAPA case to a satisfactory conclusion.

- A workflow-driven process – CAPA work is assigned by the system automatically based on how your CAPA processes and CAPA worker groups are defined.

- Flexible assignment of activities – Associate specific users or groups with each part of a CAPA process.

- Integration with Outlook – When work is assigned, the system can automatically send emails to notify the appropriate user that works needs their attention.

- Create CAPA cases at the point of need – CAPA cases can be created at the point of need in the system by the person who first recognizes that there is a problem that needs attention. The system automatically links each CAPA case to the record from which it was created (for example, to the specific customer, quality order, or production order that was open when the case was created).

- Trending analysis – The CAPA workspace provides analytical tools to help you analyze CAPA trends.

The following table describes tasks that employees can perform when they work with CAPA management.

| **Task**                             | **Description**                                                                                               |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| **Create a CAPA case**               | Create a new CAPA case record for a customer, vendor, product, or employee.                                   |
| **Work with a CAPA case**            | Add detailed information to a new or existing CAPA case, such as activities.                                  |
| **Update the status of a CAPA case** | Update the status of a CAPA case, for example from **Opened** to **In process**.                              |
| **Update the stage of a CAPA case**  | Update the stage in the process of working a CAPA case, for example from **Evaluation** to **Investigation**. |
| **Close a CAPA case**                | Change the status of an **Opened** case to **Closed** to indicate that the issue has been resolved.           |
| **Rank a knowledge article**         | Rank a knowledge article to indicate if it was successful in helping to close a case.                         |

## Setting up CAPA case components

Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases. You can create the components yourself or generate them from a template.

### Generate standard process from a template

1. Go to **System administration** \> **Setup** \> **Setup Advanced Quality Management**.

2. In the **General** tab, select **Create CAPA process templates**.

3. In the **Create standard CAPA process templates** dialog select **Load**.

4. Select **OK**,

### Set up CAPA categories

CAPA categories allow you to group similar case types together. Organizing CAPA cases by category can help employees identify known solutions, such as knowledge articles, for when similar issues frequently occur. This information is also used by the *Trending analysis by category* feature so employees can review whether the frequency of specific issues is declining over time.

To set up your CAPA categories, follow these steps.

1. Go to **Inventory management** &gt; **Setup** &gt; **CAPA management** &gt; **CAPA categories**.

2. Use the buttons on the Action Pane to add and remove categories as needed. You can't delete categories that are assigned to active CAPA cases. For each category, make the following settings:

    - **CAPA category** – Enter the name of the CAPA category. General category groupings are Product related, Vendor related, Customer related. Detailed category groupings: Bulk production related, Production labeling related, Packaging production related; Production resource related.

    <!-- -->

    - **Description** – Enter a description of the CAPA category.

    <!-- -->

    - **CAPA subcategory type** – Select the subcategory for the CAPA category. The *User defined* subcategory type lets you choose from a collection of custom subcategory types that you've created for your company. See the next procedure for details about how to set up your custom subcategory types.

To set up your user-defined CAPA subcategory types, follow these steps.

1. Go to **Inventory management** &gt; **Setup** &gt; **CAPA management** &gt; **CAPA categories**.

2. On the Action Pane, select **User defined CAPA subcategory.**

3. Use the buttons on the Action Pane to add and remove subcategories as needed. For each subcategory, make the following settings:

    - **CAPA subcategory** – Enter the name of the subcategory.

    <!-- -->

    - **Description** – Enter a short description of the subcategory.

### Set up CAPA worker groups

CAPA worker groups let you group users together for CAPA purposes. You can assign a CAPA work group to each activity and stage in your CAPA process. The system uses them to validate worker assignments and can use them to set default workers when a specific worker isn't assigned.

To set up your CAPA worker groups, follow these steps.

1. Go to **Inventory management** &gt; **Setup** &gt; **CAPA management** &gt; **CAPA worker groups**.

2. Use the buttons on the Action Pane to add and remove worker groups as needed. You can't delete worker groups that are assigned to CAPA case activities.

3. For your new or selected worker group, make the following settings in the header:

    - **CAPA worker group** – Enter a name for the worker group. Common examples include *Investigator*, *Implementer*, *Approver* and*Verifier*.

    <!-- -->

    - **Name** – Enter a short description of the worker group.

4. Use the settings on the **Group settings** FastTab to set up the group, including details related to whether all members of the group can change the stage of a CAPA case and whether the CAPA administrator should be an implied member and/or default worker for the group. Make the following settings:

    - **Allow any member to change stage** – Select this check box if all workers within this CAPA worker group are allowed to change the stage of the CAPA case.

    <!-- -->

    - **Implied member of this worker group** – Select this check box if the CAPA administrator, assigned on the Inventory management parameters, should be an implied member of this CAPA worker group. Alternatively, the CAPA administrator can be assigned to the CAPA worker group but if the CAPA administrator is changed, this will require more maintenance.

    <!-- -->

    - **Default worker** – Select this check box if the CAPA administrator should be the default worker for this CAPA worker group.

5. Use the settings on the **Worker assignments** FastTab to assign workers to the group.

Workers can be assigned to a CAPA worker group by either using the Worker assignments FastTab by using the New button or by changing to the Assign tab and using the arrows to assign workers.

You can delete workers from the CAPA worker group by using the **Delete** button on the **Overview** tab or by using the right arrow on the **Assign** tab. Workers are set up through the **Human Resources** menu. Workers are associated to a given user ID through the **Relations** action.

Once a worker is assigned to the CAPA worker group, select the **Allowed** checkbox if this worker can advance the CAPA Case to the next stage.

If the **Allow any member to change stage** checkbox is selected, then the **Allowed** checkbox on the Worker assignment is not used. You only need to specify this checkbox if you want to limit which workers within the group can advance the stage of the CAPA Case.

If the CAPA administrator is not the default worker of the worker group, you can select which worker is the default worker for this CAPA worker group. The default worker is used when creating a CAPA case or when CAPA cases are advancing stages.

### CAPA processes

After you set up the CAPA worker groups, you can set up the hierarchical processes you plan to use for managing and resolving CAPA cases. When a CAPA case is created, a CAPA process can be assigned. This will guide the case through the assigned process so that activities can be automatically generated as the CAPA Case advances through the stages. You set up CAPA processes in the **CAPA processes** form.

| **Path: Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **FastTabs** |  |  |
| General | Set up and view general information about the CAPA process and activity. The information includes the purpose of the activity, start and end dates and time for performing the activity, and CAPA worker group and worker responsible for the activity. |  |
| Exit criteria | Set up and view the exit criteria for the selected CAPA process.</br>**Note:** Activities identified as required must be completed before you can exit the process. |  |
| **Buttons** |  |  |
| New | Create a new CAPA process. |  |
| Delete | Delete a CAPA process. |  |
| Save as | Save the current process to a new name. |  |
| Functions | Save the current process or copy an existing CAPA process to a template. |  |
| Inquiry | Open the **All CAPA cases** form to view all CAPA cases using the selected CAPA Process for your company. |  |
| Actions (From the Hierarchy) | From the hierarchy directly or by using the Actions button, levels and activities can be added to the tree. Options include: Create level, Create action, Create appointment, Create event, Create task, Delete, Details. | There are four types of activities used by CAPA cases: Action, Appointment, Event and Task. |
| **Fields** |  |  |
| Name | Enter or view the name for the CAPA process. |  |
| Description | Enter or view a brief description of the CAPA process. |  |
| Approved | Select this check box if the CAPA process is approved for use in managing CAPA cases. |  |
| Name | View the stage/activity name. |  |
| Activity number | View the activity number that is assigned to the activity associated with the process. This number is generated automatically. |  |
| Purpose | Enter or view the name or description for the purpose of the activity. |  |
| Calculated start in (days) | Enter or view the number of days from the start date of a CAPA case on which the activity should begin. |  |
| Calculated end in (days) | Enter or view the number of days from the end date of a CAPA case on which the activity should end. |  |
| Start time | Enter or view the start time for the activity. |  |
| End time | Enter or view the end time for the activity. |  |
| Notes | Enter or view free-form notes about the specific CAPA case activity. |  |
| CAPA worker group | Select or view the CAPA worker group that identifies the group of CAPA workers responsible for this activity. | When you enter a CAPA worker group for the Stage it will default to the activities within that stage unless indicated otherwise on the Activity. |
| Responsible | Select or view the identifier for the worker who is responsible for this activity. If one is not specified, the default from the CAPA worker group will be used when the CAPA case is being processed. | If entered, the worker selected is validated based on the CAPA worker group assigned. IF the CAPA administration is an implied member of the group, then the CAPA administrator can be manually entered as the responsible worker if desired. |
| Notify group | Enter or view if the entire CAPA worker group should be notified when stages are advanced. Select Yes, if the group should be notified. Select No, if just the responsible should be notified. Select Inherit, if this determination has been decided at a higher level in the hierarchy. | This is used for email notifications when the stage is advanced. This field on the CAPA worker group of the stage being advanced to is the determining factor. |
| Check for required activities | Select this check box to specify that certain activities in this CAPA process must be completed before the process can be closed. |  |

## Creating and working with CAPA cases

After you set up the CAPA components, you can begin creating and working with CAPA cases to record, update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

You can create new CAPA cases from a list page and the CAPA workspace and from where the need to open a CAPA case might originate, such as Customers, Vendors, Sales orders, Purchase orders, Return orders and Released products.

### CAPA case list page

| **Path: Common** \> **Common** \> **CAPA management** \> **All CAPA cases** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Tabs** |  |  |
| CAPA case | Perform various actions for the selected CAPA case. For example, you can add a new dependent CAPA case, update the process used to manage and resolve a CAPA case, or change the current stage in the CAPA process. |  |
| General | View, create, or update activities for the selected CAPA case. |  |
| **Buttons** |  |  |
| CAPA case | Open the **New CAPA case** form to create a CAPA case record. |  |
| Dependent CAPA case | Open the **New CAPA case** form to create a dependent CAPA case record. A dependent case is associated to a parent case, which is identified in the **Parent case** field in the form. |  |
| Edit | Open the CAPA case for editing. |  |
| Edit in grid | Open a new window in edit mode and edit any available fields directly in the list page grid. |  |
| Change status | Change the status of the selected CAPA case, for example from **Opened** to **In process**. |  |
| Delete | Delete the selected CAPA case. | **Note:** You cannot delete a case if it has a dependent CAPA case associated to it. However, you should always exercise caution before deleting any CAPA case, including closed cases, as this information is used for trending purposes. Also, the Delete option is reserved for the CAPA Administrator Security Role. |
| CAPA process | View or change the process that is assigned to the CAPA case. | Can create new activities from here by using the Actions option from the CAPA process. |
| Change stage | Change the stage of the CAPA case. The stage is a level within the process that is used to resolve the CAPA case. Stages usually have one or more activities assigned to the stage. | Stages trigger email notifications when advanced. When using a CAPA process and a stage is advanced, the activities from that new stage are visible to the user and can be acted upon.</br>**Note:** If there are no required activities, you can skip a stage but if you do this, you cannot go back to that stage. |
| Non conformances | Open the **Non conformances** form to view the details if a non-conformance record is associated to the CAPA case. |  |
| Quality orders | Open the **Quality orders** form to view the details if a quality order is associated to the CAPA case. |  |
| Refresh | Update the contents of this list page. |  |
| Export to Microsoft Excel | Export CAPA case records to a Microsoft Excel worksheet. |  |
| Attachments | View a list of documents attached to the selected CAPA case. |  |
| Signature review | Allows the users to review all existing electronic signatures against a given CAPA case. | Using the buttons on the bottom of this signature review form, you can see all associated electronic signature records for the selected CAPA Case. This is offering a filtered view of the Database log/Signature review. |
| **Fields** |  |  |
| Case ID | The CAPA case identification number. |  |
| Name | The name of the vendor, customer, employee, etc. from the global address book associated with the CAPA case. |  |
| Description | A brief description of the CAPA case. |  |
| Status | The status of the CAPA case, for example, **Opened** or **In process**. |  |
| CAPA category | The category assigned to the CAPA case. | The category is used for reporting purposes to analyze trends. |
| Case classification | The classification of the CAPA case. | Possible options are None, Corrective, Preventive, or Corrective and preventive. Only one option can be selected and is used for grouping and reporting purposes. |

### Creating CAPA cases

To set up a CAPA case, you use the **New CAPA case** form.

**Note:** If your security setup permits access to the All CAPA cases menu option, then you can also create new CAPA cases from the **All CAPA cases** list page, as well as other list pages where the need to open a CAPA case might originate. For example, you can open CAPA cases from Customers, Vendors, Sales orders, Purchase orders, Return orders, Production/Batch orders, Quality orders, Non conformances, Service orders, and Released products.

| **Path: Common** \> **Common** \> **CAPA management** \> **All CAPA cases** \> **New button group** \> **CAPA case button** |                                                                                                                                                                      |                                                                                                                          |
|-------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Label Name**                                                                                                    | **Description**                                                                                                                                                      | **Examples/Hints**                                                                                                       |
| **FastTabs**                                                                                                      |                                                                                                                                                                      |                                                                                                                          |
| General                                                                                                           | Enter or view information about the new CAPA case, such as the name, CAPA category and CAPA process, status, and any related parent case associated to the new case. |                                                                                                                          |
| Case log                                                                                                          | Add, edit, or view information about the CAPA case log.                                                                                                              |                                                                                                                          |
| **Fields**                                                                                                        |                                                                                                                                                                      |                                                                                                                          |
| Name                                                                                                              | Enter or select a name from the global address book to associate with the CAPA case.                                                                                 |                                                                                                                          |
| CAPA category                                                                                                     | Select a category for the CAPA case.                                                                                                                                 |                                                                                                                          |
| Case ID                                                                                                           | The CAPA case identification number. This number is generated by the system.                                                                                         |                                                                                                                          |
| Status                                                                                                            | Select the status of the CAPA case.                                                                                                                                  | Default status is **Opened** but can be changed to In Process when a CAPA Case is first created or later in the process. |
| Description                                                                                                       | Enter a brief description of the CAPA case.                                                                                                                          |                                                                                                                          |
| Priority                                                                                                          | Select the CAPA case priority.                                                                                                                                       |                                                                                                                          |
| Parent case                                                                                                       | Select the parent case to which the new CAPA case is associated, if applicable.                                                                                      |                                                                                                                          |
| CAPA process                                                                                                      | Select the CAPA process that will be used to resolve this case.                                                                                                      | Optional, but if entered will drive the process to resolve the CAPA case.                                                |
| Description                                                                                                       | Enter a brief description of the case log.                                                                                                                           |                                                                                                                          |
| Notes                                                                                                             | Enter additional information about the case or the case log.                                                                                                         |                                                                                                                          |

### Working with CAPA cases

After you set up a CAPA case, you use the **CAPA case** form to record update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

Depending on your security permissions, you can add and update details on this form for an open CAPA case from the My CAPA cases form or the All CAPA cases form. You can also open an existing CAPA case from other forms, such as Customers, Vendors, Sales orders, Purchase orders, Return orders and Released products.

| **Path: Common** \> **Common** \> **CAPA management** \> **My CAPA cases** \> **Select the CAPA case** |                                                                                                                                                                                         |                                                                                                                                                        |
|------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Label Name**                                                                                 | **Description**                                                                                                                                                                         | **Examples/Hints**                                                                                                                                     |
| **Tabs (Action pane)**                                                                         |                                                                                                                                                                                         |                                                                                                                                                        |
| CAPA case                                                                                      | Open new CAPA cases and dependent cases, update details for case processes, or change the stage of a process. You can also view any supporting documents that are attached to the case. |                                                                                                                                                        |
| General                                                                                        | Open the **Transaction log** form or the **Activities** form to view any related transactions or activities associated to the CAPA case.                                                |                                                                                                                                                        |
| **FastTabs**                                                                                   |                                                                                                                                                                                         |                                                                                                                                                        |
| General                                                                                        | View or edit general information about the selected CAPA case.                                                                                                                          |                                                                                                                                                        |
| Case log                                                                                       | View, add, or edit information about the CAPA case log.                                                                                                                                 |                                                                                                                                                        |
| Associations                                                                                   | View or edit information about entities that are associated with the CAPA case.                                                                                                         | Examples of the entities that can be associated to a CAPA case include: sales order, item, vendor, batch order.                                        |
| Knowledge article                                                                              | View or edit information about knowledge articles that are associated with the CAPA case.                                                                                               |                                                                                                                                                        |
| Administration                                                                                 | View administrative details about the CAPA case, such as the date the case was opened and the user who opened it                                                                        |                                                                                                                                                        |
| Case Web details                                                                               | View or edit company information and contacts in the Web details for the CAPA case.                                                                                                     |                                                                                                                                                        |
| **Buttons (Action pane)**                                                                      |                                                                                                                                                                                         |                                                                                                                                                        |
| Change status                                                                                  | Change the status of the CAPA case, for example from **Opened** to **In Process**.                                                                                                      |                                                                                                                                                        |
| CAPA case                                                                                      | Open the **New CAPA case** form to set up a new CAPA case.                                                                                                                              |                                                                                                                                                        |
| Dependent CAPA case                                                                            | Open the **New CAPA case** form to set up a new dependent CAPA case. A dependent CAPA case is always associated to a parent CAPA case.                                                  |                                                                                                                                                        |
| CAPA process                                                                                   | Open the **CAPA processes** form to view or maintain the process associated with the CAPA case.                                                                                         |                                                                                                                                                        |
| Change stage                                                                                   | Change the position in the CAPA process flow from one level or stage to another, based on completing the tasks, actions, and activities associated with that stage.                     | Once a stage is advanced to, the activities associated with that stage are visible and the responsible workers are notified via an email notification. |
| Attachments                                                                                    | View or add attachments that are associated with the CAPA case.                                                                                                                         |                                                                                                                                                        |
| **Buttons (lower pane)**                                                                       |                                                                                                                                                                                         |                                                                                                                                                        |
| Add                                                                                            | Add a new line for the applicable FastTab.                                                                                                                                              |                                                                                                                                                        |
| Remove                                                                                         | Remove an existing line from the applicable FastTab.                                                                                                                                    |                                                                                                                                                        |
| Details                                                                                        | View or update details additional for the applicable FastTab.                                                                                                                           |                                                                                                                                                        |
| Open                                                                                           | Open the selected knowledge article.                                                                                                                                                    |                                                                                                                                                        |
| Send e-mail                                                                                    | Send the knowledge article in an e-mail message.                                                                                                                                        |                                                                                                                                                        |
| **Fields**                                                                                     |                                                                                                                                                                                         |                                                                                                                                                        |
| Case ID                                                                                        | The CAPA case identification number.                                                                                                                                                    |                                                                                                                                                        |
| Description                                                                                    | A brief description of the CAPA case.                                                                                                                                                   |                                                                                                                                                        |
| Parent case                                                                                    | The case number for the parent case that is associated with the CAPA case, if applicable.                                                                                               |                                                                                                                                                        |
| Name                                                                                           | The name from the global address book of the employee, vendor or customer that is associated with the CAPA case.                                                                        |                                                                                                                                                        |
| CAPA category                                                                                  | The category assigned to the CAPA case.                                                                                                                                                 | The category is used for reporting purposes to analyze trends.                                                                                         |
| CAPA subcategory                                                                               | The subcategory assigned to the CAPA case.                                                                                                                                              | The subcategory is used for reporting purposes to analyze trends.                                                                                      |
| CAPA process                                                                                   | The process assigned to resolve the CAPA case.                                                                                                                                          |                                                                                                                                                        |
| Status                                                                                         | The current status of the CAPA case.                                                                                                                                                    |                                                                                                                                                        |
| Priority                                                                                       | View or edit the current priority assigned to the CAPA case.                                                                                                                            |                                                                                                                                                        |
| Case resolution                                                                                | Identifies the resolution for the CAPA case if it has been resolved.                                                                                                                    |                                                                                                                                                        |
| Notes                                                                                          | Additional information attached to the CAPA case.                                                                                                                                       |                                                                                                                                                        |

## Working with CAPA activities

After CAPA cases are created and if CAPA processes are being used, CAPA activities will be automatically created for you as CAPA cases are acted upon. When a stage is advanced, CAPA activities will be created and assigned to the appropriate person responsible with a due date depending on how the CAPA process was defined. CAPA activities can be viewed using its own menu group where you can view All CAPA activities and All Open CAPA activities as well as CAPA activities due in the current week or that are past due. Each of these options is also available where they are filtered by the current user so that only activities where the user is responsible would be included.

### CAPA activity pages

| **Path: Home** \> **Common** \> **Activities** \> **CAPA activities** \> **All CAPA activites OR My CAPA activities OR All open CAPA activities OR My open CAPA activities OR All CAPA activities due this week OR My CAPA activities due this week OR All CAPA activities past due OR My CAPA activities past due** |                                                                                                    |                                                                                                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Label Name**                                                                                                                                                                                                                                                                                               | **Description**                                                                                    | **Examples/Hints**                                                                                                                                                                       |
| **Buttons**                                                                                                                                                                                                                                                                                                  |                                                                                                    |                                                                                                                                                                                          |
| Action                                                                                                                                                                                                                                                                                                       | Create a New CAPA activity that is defined as an Action.                                           |                                                                                                                                                                                          |
| Appointment                                                                                                                                                                                                                                                                                                  | Create a New CAPA activity that is defined as an Appointment.                                      |                                                                                                                                                                                          |
| Event                                                                                                                                                                                                                                                                                                        | Create a New CAPA activity that is defined as an Event.                                            |                                                                                                                                                                                          |
| Task                                                                                                                                                                                                                                                                                                         | Create a New CAPA activity that is defined as a Task.                                              |                                                                                                                                                                                          |
| Edit                                                                                                                                                                                                                                                                                                         | Open the CAPA activity for editing.                                                                |                                                                                                                                                                                          |
| Set as complete                                                                                                                                                                                                                                                                                              | Selects the option of Closed on the CAPA activity.                                                 | This represents the action of completing the work that was called for on the CAPA activity.                                                                                              |
| Edit in grid                                                                                                                                                                                                                                                                                                 | Open a new window in edit mode and edit any available fields directly in the list page grid.       |                                                                                                                                                                                          |
| Delete                                                                                                                                                                                                                                                                                                       | Delete the selected CAPA activity.                                                                 | **Note:** You cannot delete an activity that is assigned to someone else, but you can delete your own. |
| Attendees                                                                                                                                                                                                                                                                                                    | View or change the attendees if the selected CAPA activity has a Category of Appointment.          | Can create new activities from here by using the Actions option from the CAPA process.                                                                                                   |
| Recurrence pattern                                                                                                                                                                                                                                                                                           | View or change the recurrence pattern if the selected CAPA activity has a Category of Appointment. |                                                                                                                                                                                          |
| Refresh                                                                                                                                                                                                                                                                                                      | Update the contents of this list page.                                                             |                                                                                                                                                                                          |
| Export to Microsoft Excel                                                                                                                                                                                                                                                                                    | Export CAPA activity records to a Microsoft Excel worksheet.                                       |                                                                                                                                                                                          |
| Attachments                                                                                                                                                                                                                                                                                                  | View a list of documents attached to the selected CAPA activity.                                   |                                                                                                                                                                                          |
| **Fields**                                                                                                                                                                                                                                                                                                   |                                                                                                    |                                                                                                                                                                                          |
| Date                                                                                                                                                                                                                                                                                                         | The start date for the CAPA activity.                                                              |                                                                                                                                                                                          |
| Purpose                                                                                                                                                                                                                                                                                                      | The purpose or description of the CAPA activity.                                                   |                                                                                                                                                                                          |
| Priority                                                                                                                                                                                                                                                                                                     | The priority of the CAPA activity.                                                                 | **The valid Priorities for Activities are Low, Normal or High.**                                                                                                                         |
| Category                                                                                                                                                                                                                                                                                                     | The category of the CAPA activity.                                                                 | **Valid category options are Action, Appointment, Event and Task.**                                                                                                                      |
| Type                                                                                                                                                                                                                                                                                                         | The type of CAPA activity.                                                                         | **These are user defined types that can be used for grouping and/or reporting.**                                                                                                         |

### Running CAPA case trending analysis

You run trending analysis to view in graphical format the volume of CAPA cases by category to analyze whether the frequency of specific issues that resulted in cases are increasing or declining over time. You can include all CAPA cases in a trending analysis or only those cases that were created as of a specific from date.

To run trending analysis using information collected for CAPA cases, use the **Trending analysis** form and the CAPA management workspace.

| **Path: Inventory management** \> **Inquiries and reports** \> **CAPA management** \> **Trending analysis AND Inventory management** \> **Workspaces** \> **CAPA management** |                                                                                                                                                                                                                                                                                                           |                                               |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| **Label Name**                                                                                                                                                      | **Description**                                                                                                                                                                                                                                                                                           | **Examples/Hints**                            |
| **Tabs**                                                                                                                                                            |                                                                                                                                                                                                                                                                                                           |                                               |
| Data                                                                                                                                                                | Specify the criteria to use for the trending analysis.                                                                                                                                                                                                                                                    |                                               |
| Analytics by category                                                                                                                                               | View the results of the trending analysis by category. The results are determined based on the criteria you select on the Data tab. If you select all three data options, then three graphs appear on this tab after you run the analysis. Otherwise, only the graphs for the options you select display. |                                               |
| Analytics by subcategory                                                                                                                                            | View the results of the trending analysis by subcategory. The results are determined based on the criteria you select on the Data tab. You select a CAPA category and up to two data options.                                                                                                             |                                               |
| **Fields**                                                                                                                                                          |                                                                                                                                                                                                                                                                                                           |                                               |
| From date                                                                                                                                                           | Select the start date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date.                                                                                                                         | Defaults to the first day of the current year |
| To date                                                                                                                                                             | Select the end date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date.                                                                                                                           | Defaults to the current date                  |
| Number of cases opened by                                                                                                                                           | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases opened by specific users over the date period defined.                                                                                                                                       |                                               |
| Number of cases by category                                                                                                                                         | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases by category over the date period defined.                                                                                                                                                    |                                               |
| Trending of cases by category                                                                                                                                       | Select this check box to display trending results on a Line graph, which shows the total number of CAPA cases by category over the date period defined.                                                                                                                                                   |                                               |
| CAPA category                                                                                                                                                       | The category assigned to the CAPA case.                                                                                                                                                                                                                                                                   |                                               |
| Number of cases by subcategory (Top 10)                                                                                                                             | Select this check box to display trending results on a pie chart, which shows the CAPA cases by the top 10 subcategories over the date period defined.                                                                                                                                                    |                                               |
| Trending of cases by subcategory (Top 10)                                                                                                                           | Select this check box to display trending results on a Line graph, which shows the CAPA cases by the top 10 subcategories over the date period defined.                                                                                                                                                   |                                               |
