---
title: Advanced Quality Management Source
description: Advanced Quality Management Source document
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 11/25/2024
ms.custom: 
  - bap-template
---

# Advanced Quality Management Source

## Introduction to EDGE for AX

Fullscope EDGE for AX on Microsoft Dynamics AX is designed to provide life sciences and pharmaceutical manufacturers with the tools needed to address core issues that manufacturers face to meet the U.S. Food and Drug Administration's (FDA) Quality System Regulation 21 CFR Part 11, cGMP and other various regulatory and international standards such as ISO and Six Sigma.

Some of the key industry-specific capabilities of EDGE for AX for Microsoft Dynamics AX are:

- **Corrective Actions/Preventive Actions (CAPA)** – This feature allows users to automate processes to manage, track, and correct root causes of issues and to implement action plans to prevent the same and similar issues going forward.

- **Electronic signature requirement for CAPA case closure** – This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off

- **Flexible sampling plans** – This feature enables companies to inspect a fraction of a lot, or to skip lots altogether, to realize reduced quality and material handling costs, faster material throughput, and less redundant and destructive testing.

- **Approved customer lists (ACL)** – This feature provides greater control over what products a given customer can buy and when they can buy them, which is especially important with a product line that involves controlled substances and branded products.

- **Electronic signature (ESig)** – This feature enhancement provides greater security of the digital signatures to meet the latest government requirements and regulations.

- **Electronic Batch Record (EBR)** – This feature enables users to view all of the versions, methods, and characteristics for the production of BOM items and Formula items. This is referred to as a Master Manufacturing Record that maintains all of the methods that could be utilized to produce the item. This feature also allows users to view and print reports of the actual versions, test values, attribute values, quality order results of all of the items produced and the ingredients consumed. This is referred to as a Batch Production Record that captures the actual version and methods used to produce the item.

- **Instrument Calibration** – This new feature adds capability around tracking individual test instrument tags, supports an on-going calibration process for the instrument tag and tracks usage of given tags against the quality order tests.

- **Quality Associations for Returns and Transfers** – This feature enhances the capability of quality associations by offering the ability to automatically create quality orders triggered from a sales return or a transfer order.

- **Customer-Specific COAs** – This feature supports the setup and application of customer COA requirements. The specific customer will drive details such as whether or not a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results (pass and/or fail) should be replaced with standard verbiage. In addition, customer-specific COA's can be generated automatically from the sales order packing slip posting process.

- **Production Dispensing** – This feature enables users to segregate the dispensing area and activities from the picking activities.

- **Quick Results Entry** – This feature enables users to very quickly and easily enter test results on a quality order from a consolidated view which includes visibility to test minimum, maximum and target values.

- **Quality Order Usability Improvements –** Several usability improvements were added to the quality order process. The option to skip a quality order test has been added. When a decision is made not to perform a test on a given quality order, that can now be noted on the quality order without losing visibility to the original test. When a test is skipped, all validations on the test is by-passed and the test is changed to not be included in results so that AQL calculations are still performed on the remaining tests. Quality order "Priority" Level and "Assigned to" tester are new data elements on the quality order that can be used to sort and filter on the quality work that needs to be completed. Result notes can now also be recorded for a given test result line. Finally, test instrument tags are always checked to see if the selected tag is already on an open quality order. This validation is not important to all businesses so now there is a parameter that drives this functionality and the validation can be skipped if not required.

## Corrective Action and Preventive Action (CAPA)

You use CAPA management to create and maintain records of the corrective or preventive action taken to manage and resolve non-conformities or defects involving products. By planning, tracking, and analyzing CAPA cases, you can develop efficient processes that can be helpful in resolving similar issues.

### Setting up CAPA case components

Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases.

#### CAPA categories

First, you create CAPA categories, which allow you to group similar case types together. Organizing CAPA cases by category can help employees identify known solutions, such as knowledge articles, if similar issues frequently occur. This information is also used by the Trending analysis by category feature so employees can review whether the frequency of specific issues is declining over time. You set up CAPA categories in the **CAPA categories** form.

| **Path: Inventory management \> Setup \> CAPA management \> CAPA categories** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a new CAPA category. |  |
| Delete | Delete a CAPA category.</br>**Note:** You cannot delete a category if it is currently assigned to an active CAPA case. |  |
| User defined CAPA subcategory | Define multiple selections for a specified user defined subcategory. |  |
| **Fields** | &nbsp; | &nbsp; |
| CAPA category | The name of the CAPA category. | General category groupings:<br /></br>Product related, Vendor related, Customer related</br>Detailed category groupings:</br>Bulk production related, Production labeling related, Packaging production related; Production resource related. |
| Description | The description of the CAPA category. |  |
| CAPA subcategory type | The subcategory for the CAPA category | When selecting a User defined value for the subcategory you will setup multiple subcategories that can be selected for that CAPA category. |

#### CAPA worker groups

After setting up CAPA categories, you will need to create CAPA worker groups. CAPA worker groups allow you to group users together for CAPA purposes. The CAPA worker groups are used on CAPA Processes to assign activities. A CAPA worker group can be assigned to stages or specific activities. It is used to validate the appropriate worker assigned or can be used as a defaulting mechanism if a specific user is not assigned. You set up CAPA worker groups in the **CAPA worker groups** form.

| **Path: Inventory management \> Setup \> CAPA management \> CAPA worker groups** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a new CAPA worker group. |  |
| Delete | Delete a CAPA worker group.<ul><li>**Note:** You cannot delete a worker group if it is currently assigned to CAPA case activities.</li></ul> |  |
| **FastTabs** | &nbsp; | &nbsp; |
| Group settings | Set up and view group settings abut a specific CAPA worker group. Includes details related to whether all members of the group can change the stage of the CAPA case and whether or not the CAPA administrator should be an implied member of the group and/or the default worker for the group. |  |
| Worker assignments | Set up and view the worker assignments for the selected CAPA worker group. |  |
| **Fields** | &nbsp; | &nbsp; |
| CAPA worker group | The name of the CAPA worker group. | Common examples include Investigator, Implementer, Approver and Verifier. |
| Name | The description of the CAPA worker group. |  |
| Allow any member to change stage | Select this check box if all workers within this CAPA worker group are allowed to change the stage of the CAPA case. |  |
| Implied member of this worker group (CAPA administrator) | Select this check box if the CAPA administrator, assigned on the Inventory management parameters, should be an implied member of this CAPA worker group. | Alternatively, the CAPA administrator can be assigned to the CAPA worker group but if the CAPA administrator is changed, this will require more maintenance. |
| Default worker (CAPA administrator) | Select this check box if the CAPA administrator should be the default worker for this CAPA worker group. |  |
| Worker | Workers can be assigned to a CAPA worker group by either using the Worker assignments FastTab by using the New button or by changing to the Assign tab and using the arrows to assign workers.</br>**Note:** You can delete workers from the CAPA worker group by using the Delete button on the Overview tab or by using the right arrow on the Assign tab. | Workers are set up through the Human Resources menu. Workers are associated to a given User Id through the Relations action. |
| Allowed | Once a worker is assigned to the CAPA worker group, select the Allowed checkbox if this worker can advance the CAPA Case to the next stage.</br>**Note:** If the "Allow any member to change stage" checkbox is selected, then the Allowed checkbox on the Worker assignment is not used. You only need to specify this checkbox if you want to limit which workers within the group can advance the stage of the CAPA Case. |  |
| Default worker | If the CAPA administrator is not the default worker of the worker group, you can select which worker is the default worker for this CAPA worker group. The default worker is used when creating a CAPA case or when CAPA cases are advancing stages. |  |

#### CAPA processes

After you set up the CAPA worker groups, you can set up the hierarchical processes you plan to use for managing and resolving CAPA cases. When a CAPA case is created, a CAPA process can be assigned. This will guide the case through the assigned process so that activities can be automatically generated as the CAPA Case advances through the stages. You set up CAPA processes in the **CAPA processes** form.

| **Path: Inventory management \> Setup \> CAPA management \> CAPA processes** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **FastTabs** | &nbsp; | &nbsp; |
| General | Set up and view general information about the CAPA process and activity. The information includes the purpose of the activity, start and end dates and time for performing the activity, and CAPA worker group and worker responsible for the activity. |  |
| Exit criteria | Set up and view the exit criteria for the selected CAPA process.</br>**Note:** Activities identified as required must be completed before you can exit the process. |  |
| **Buttons** | &nbsp; | &nbsp; |
| New | Create a new CAPA process. |  |
| Delete | Delete a CAPA process. |  |
| Save as | Save the current process to a new name. |  |
| Functions | Save the current process or copy an existing CAPA process to a template. |  |
| Inquiry | Open the **All CAPA cases** form to view all CAPA cases using the selected CAPA Process for your company. |  |
| Actions (From the Hierarchy) | From the hierarchy directly or by using the Actions button, levels and activities can be added to the tree. Options include: Create level, Create action, Create appointment, Create event, Create task, Delete, Details. | There are four types of activities used by CAPA cases: Action, Appointment, Event and Task. |
| **Fields** | &nbsp; | &nbsp; |
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

### Basic CAPA tasks

The following table describes tasks that employees can perform when they work with CAPA management.

| **Task**                             | **Description**                                                                                               |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| **Create a CAPA case**               | Create a new CAPA case record for a customer, vendor, product, or employee.                                   |
| **Work with a CAPA case**            | Add detailed information to a new or existing CAPA case, such as activities.                                  |
| **Update the status of a CAPA case** | Update the status of a CAPA case, for example from **Opened** to **In process**.                              |
| **Update the stage of a CAPA case**  | Update the stage in the process of working a CAPA case, for example from **Evaluation** to **Investigation**. |
| **Close a CAPA case**                | Change the status of an **Opened** case to **Closed** to indicate that the issue has been resolved.           |
| **Rank a knowledge article**         | Rank a knowledge article to indicate if it was successful in helping to close a case.                         |

### Creating and working with CAPA cases

After you set up the CAPA components, you can begin creating and working with CAPA cases to record, update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

You can set up, work with, and view CAPA cases from the **My CAPA cases** form, or if your security setup permissions allow, from the **All CAPA cases** form. You can also create new CAPA cases from other list pages and forms in Microsoft Dynamics AX where the need to open a CAPA case might originate, such as Customers, Vendors, Sales orders, Purchase orders, Return orders, and Released products.

#### CAPA case list pages

| **Path: Home OR Inventory management \> Common \> CAPA management \> My CAPA cases OR All CAPA cases** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Tabs** | &nbsp; | &nbsp; |
| CAPA case | Perform various actions for the selected CAPA case. For example, you can add a new dependent CAPA case, update the process used to manage and resolve a CAPA case, or change the current stage in the CAPA process. |  |
| General | View, create, or update activities for the selected CAPA case. |  |
| **Buttons** | &nbsp; | &nbsp; |
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
| **Fields** | &nbsp; | &nbsp; |
| Case ID | The CAPA case identification number. |  |
| Name | The name of the vendor, customer, employee, etc. from the global address book associated with the CAPA case. |  |
| Description | A brief description of the CAPA case. |  |
| Status | The status of the CAPA case, for example, **Opened** or **In process**. |  |
| CAPA category | The category assigned to the CAPA case. | The category is used for reporting purposes to analyze trends. |
| Case classification | The classification of the CAPA case. | Possible options are None, Corrective, Preventive, or Corrective and preventive. Only one option can be selected and is used for grouping and reporting purposes. |

#### Creating CAPA cases

To set up a CAPA case, you use the **New CAPA case** form.

**Note:** If your security setup permits access to the All CAPA cases menu option, then you can also create new CAPA cases from the **All CAPA cases** list page, as well as other list pages and forms in Microsoft Dynamics AX where the need to open a CAPA case might originate. For example, you can open CAPA cases from Customers, Vendors, Sales orders, Purchase orders, Return orders, Production/Batch orders, Quality orders, Non conformances, Service orders, and Released products.

| **Path: Home OR Inventory management \> \> Common \> CAPA management \> My CAPA cases OR All CAPA cases \> New button group \> CAPA case button** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **FastTabs** | &nbsp; | &nbsp; |
| General | Enter or view information about the new CAPA case, such as the name, CAPA category and CAPA process, status, and any related parent case associated to the new case. |  |
| Case log | Add, edit, or view information about the CAPA case log. |  |
| **Fields** | &nbsp; | &nbsp; |
| Name | Enter or select a name from the global address book to associate with the CAPA case. |  |
| CAPA category | Select a category for the CAPA case. |  |
| Case ID | The CAPA case identification number. This number is generated by the system. |  |
| Status | Select the status of the CAPA case. | Default status is **Opened** but can be changed to In Process when a CAPA Case is first created or later in the process. |
| Description | Enter a brief description of the CAPA case. |  |
| Priority | Select the CAPA case priority. |  |
| Parent case | Select the parent case to which the new CAPA case is associated, if applicable. |  |
| CAPA process | Select the CAPA process that will be used to resolve this case. | Optional, but if entered will drive the process to resolve the CAPA case. |
| Description | Enter a brief description of the case log. |  |
| Notes | Enter additional information about the case or the case log. |  |

#### Working with CAPA cases

After you set up a CAPA case, you use the **CAPA case** form to record update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

Depending on your security permissions, you can add and update details on this form for an open CAPA case from the My CAPA cases form or the All CAPA cases form. You can also open an existing CAPA case from other forms in Microsoft Dynamics AX, such as Customers, Vendors, Sales orders, Purchase orders, Return orders, and Released products.

| **Path: Home OR Inventory management \> \> Common \> CAPA management \> My CAPA cases OR All CAPA cases \> Select the CAPA case** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Tabs (Action pane)** | &nbsp; | &nbsp; |
| CAPA case | Open new CAPA cases and dependent cases, update details for case processes, or change the stage of a process. You can also view any supporting documents that are attached to the case. |  |
| General | Open the **Transaction log** form or the **Activities** form to view any related transactions or activities associated to the CAPA case. |  |
| **FastTabs** | &nbsp; | &nbsp; |
| General | View or edit general information about the selected CAPA case. |  |
| Case log | View, add, or edit information about the CAPA case log. |  |
| Associations | View or edit information about entities that are associated with the CAPA case. | Examples of the entities that can be associated to a CAPA case include: sales order, item, vendor, batch order. |
| Knowledge article | View or edit information about knowledge articles that are associated with the CAPA case. |  |
| Administration | View administrative details about the CAPA case, such as the date the case was opened and the user who opened it |  |
| Case Web details | View or edit company information and contacts in the Web details for the CAPA case. |  |
| **Buttons (Action pane)** | &nbsp; | &nbsp; |
| Change status | Change the status of the CAPA case, for example from **Opened** to **In Process**. |  |
| CAPA case | Open the **New CAPA case** form to set up a new CAPA case. |  |
| Dependent CAPA case | Open the **New CAPA case** form to set up a new dependent CAPA case. A dependent CAPA case is always associated to a parent CAPA case. |  |
| CAPA process | Open the **CAPA processes** form to view or maintain the process associated with the CAPA case. |  |
| Change stage | Change the position in the CAPA process flow from one level or stage to another, based on completing the tasks, actions, and activities associated with that stage. | Once a stage is advanced to, the activities associated with that stage are visible and the responsible workers are notified via an email notification. |
| Attachments | View or add attachments that are associated with the CAPA case. |  |
| **Buttons (lower pane)** | &nbsp; | &nbsp; |
| Add | Add a new line for the applicable FastTab. |  |
| Remove | Remove an existing line from the applicable FastTab. |  |
| Details | View or update details additional for the applicable FastTab. |  |
| Open | Open the selected knowledge article. |  |
| Send e-mail | Send the knowledge article in an e-mail message. |  |
| **Fields** | &nbsp; | &nbsp; |
| Case ID | The CAPA case identification number. |  |
| Description | A brief description of the CAPA case. |  |
| Parent case | The case number for the parent case that is associated with the CAPA case, if applicable. |  |
| Name | The name from the global address book of the employee, vendor or customer that is associated with the CAPA case. |  |
| CAPA category | The category assigned to the CAPA case. | The category is used for reporting purposes to analyze trends. |
| CAPA subcategory | The subcategory assigned to the CAPA case. | The subcategory is used for reporting purposes to analyze trends. |
| CAPA process | The process assigned to resolve the CAPA case. |  |
| Status | The current status of the CAPA case. |  |
| Priority | View or edit the current priority assigned to the CAPA case. |  |
| Case resolution | Identifies the resolution for the CAPA case if it has been resolved. |  |
| Notes | Additional information attached to the CAPA case. |  |

### Working with CAPA activities

After CAPA cases are created and if CAPA processes are being used, CAPA activities will be automatically created for you as CAPA cases are acted upon. When a stage is advanced, CAPA activities will be created and assigned to the appropriate person responsible with a due date depending on how the CAPA process was defined. CAPA activities can be viewed using its own menu group where you have the ability to view All CAPA activities and All Open CAPA activities as well as CAPA activities due in the current week or that are past due. Each of these options is also available where they are filtered by the current user so that only activities where the user is responsible would be included.

#### CAPA activity list pages

| **Path: Home \> Common \> Activities \> CAPA activities \> All CAPA activites OR My CAPA activities OR All open CAPA activities OR My open CAPA activities OR All CAPA activities due this week OR My CAPA activities due this week OR All CAPA activities past due OR My CAPA activities past due** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Action | Create a New CAPA activity that is defined as an Action. |  |
| Appointment | Create a New CAPA activity that is defined as an Appointment. |  |
| Event | Create a New CAPA activity that is defined as an Event. |  |
| Task | Create a New CAPA activity that is defined as a Task. |  |
| Edit | Open the CAPA activity for editing. |  |
| Set as complete | Selects the option of Closed on the CAPA activity. | This represents the action of completing the work that was called for on the CAPA activity. |
| Edit in grid | Open a new window in edit mode and edit any available fields directly in the list page grid. |  |
| Delete | Delete the selected CAPA activity. | **Note:** You cannot delete an activity that is assigned to someone else but you can delete your own. |
| Attendees | View or change the attendees if the selected CAPA activity has a Category of Appointment. | Can create new activities from here by using the Actions option from the CAPA process. |
| Recurrence pattern | View or change the recurrence pattern if the selected CAPA activity has a Category of Appointment. |  |
| Refresh | Update the contents of this list page. |  |
| Export to Microsoft Excel | Export CAPA activity records to a Microsoft Excel worksheet. |  |
| Attachments | View a list of documents attached to the selected CAPA activity. |  |
| **Fields** | &nbsp; | &nbsp; |
| Date | The start date for the CAPA activity. |  |
| Purpose | The purpose or description of the CAPA activity. |  |
| Priority | The priority of the CAPA activity. | **The valid Priorities for Activities are Low, Normal or High.** |
| Category | The category of the CAPA activity. | **Valid category options are Action, Appointment, Event and Task.** |
| Type | The type of CAPA activity. | **These are user defined types that can be used for grouping and/or reporting.** |

#### Running CAPA case trending analysis

You run trending analysis to view in graphical format the volume of CAPA cases by category to analyze whether the frequency of specific issues that resulted in cases are increasing or declining over time. You can include all CAPA cases in a trending analysis or only those cases that were created as of a specific from date.

To run trending analysis using information collected for CAPA cases, use the **Trending analysis** form.

| **Path: Inventory management \> Inquiries \> CAPA management \> Trending analysis** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Tabs** | &nbsp; | &nbsp; |
| Data | Specify the criteria to use for the trending analysis. |  |
| Analytics by category | View the results of the trending analysis by category. The results are determined based on the criteria you select on the Data tab. If you select all three data options, then three graphs appear on this tab after you run the analysis. Otherwise, only the graphs for the options you select display. |  |
| Analytics by subcategory | View the results of the trending analysis by subcategory. The results are determined based on the criteria you select on the Data tab. You select a CAPA category and up to two data options. |  |
| **Fields** | &nbsp; | &nbsp; |
| From date | Select the start date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date. | Defaults to the first day of the current year |
| To date | Select the end date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date. | Defaults to the current date |
| Number of cases opened by | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases opened by specific users over the date period defined. |  |
| Number of cases by category | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases by category over the date period defined. |  |
| Trending of cases by category | Select this check box to display trending results on a Line graph, which shows the total number of CAPA cases by category over the date period defined. |  |
| CAPA category | The category assigned to the CAPA case. |  |
| Number of cases by subcategory (Top 10) | Select this check box to display trending results on a pie chart, which shows the CAPA cases by the top 10 subcategories over the date period defined. |  |
| Trending of cases by subcategory (Top 10) | Select this check box to display trending results on a Line graph, which shows the CAPA cases by the top 10 subcategories over the date period defined. |  |

## Electronic signature requirement for CAPA case closure

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one. This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off as well as when a CAPA case is reopened.

### Setting up Electronic signature requirements

Using the Organization module, you maintain the various requirements for determining which events should trigger an electronic signature. For this feature, we have added the option to indicate that a signature is required for the event "Close/Cancel CAPA case". If selected, whenever the status of a CAPA case is changed to Closed or Canceled or when a CAPA case is reopened, electronic signature is required.

| **Path: Organization administration \> Setup \> Electronic signature \> Electronic signature requirements** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Allows new electronic signature requirements to be added as User defined options. Requires customizations. |  |
| Delete | Allows a User defined electronic signature to be deleted. |  |
| Properties | Used when creating User defined electronic signature options as part of the customization. |  |
| **Fields** | &nbsp; | &nbsp; |
| Name | Represents the name of the electronic signature requirement. Built in requirements are available to the user without customizations. User defined requirements need customization. | Close/Cancel CAPA case is the new Built in Requirement that has been added as part of this feature. |
| Procedure type | Two options exist for procedure type. Built in means that they are ready to be triggered as desired without customization. User defined means that they have to be built. | This feature provides a Built in requirement as all of the work to turn this requirement on has been done as part of this feature. |
| Signature required | This checkbox represents which events in the system should drive an electronic signature to complete. | If desired, Close/Cancel CAPA Case can be selected which would then drive an electronic signature when a CAPA case is closed, cancelled or reopened. |
|  |  |  |

### Triggering Electronic signature from CAPA case close or cancel

From a CAPA Case, the Change status ribbon action is the trigger point for electronic signature if the "Close/Cancel CAPA Case" is selected under the Electronic signature requirements. The following chart represents the CAPA case status changes that trigger electronic signature.

| **<u>Initial CAPA case Status</u>** | **<u>Possible Status Changes</u>** | **<u>Will Electronic Signature be triggered?</u>** |
|-------------------------------------|------------------------------------|----------------------------------------------------|
| Opened                              | In Process                         | NO                                                 |
|                                     | Canceled                           | YES                                                |
| In Process                          | Opened                             | NO                                                 |
|                                     | Canceled                           | YES                                                |
|                                     | Closed                             | YES                                                |
| Canceled                            | Opened                             | YES                                                |
|                                     | In Process                         | YES                                                |
| Closed                              | Opened                             | YES                                                |
|                                     | In Process                         | YES                                                |

Using the Inventory Management module, you can process a CAPA case to completion. Adjusting the CAPA case status is an important step in the process. Closing or canceling a CAPA Case, will trigger an electronic signature. Additionally, if a CAPA Case has already been closed or canceled and the user wants to reopen it by changing the status back to Opened or In Process, Electronic signature will also be triggered. The user may also use the new Ribbon action of "Signature review" to review existing signatures against the selected CAPA case.

| **Path: Inventory management \> Common \> CAPA management \> All/My CAPA Cases** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Signature review | Allows the users to review all existing electronic signatures against a given CAPA case. | Using the buttons on the bottom of this form, you can see all associated electronic signature records for the selected CAPA Case. This is offering a filtered view of the Database log/Signature review. |

## Flexible sampling plans

A flexible sampling plan defines the criteria for inspecting units of items that are randomly picked from a lot to determine if the entire lot passes or fails based on the results of the inspected samplings. Typically, the number of units chosen for inspection is proportional to the total size of the lot based on rational criterion. The quality association defined for a plan identifies the activity to be inspected. For example, the activity might be a quality order to inspect a product before it is released to a customer in a sales order, or it could be a quality order to inspect a manufactured product upon completion of production.

Flexible sampling plans offer other features that allow you to modify your criteria over time based on prior testing results.

- **Sampling size variations** – Flexible sampling provides the ability to vary your item sampling over time based on test findings. For example, for the first five rounds of testing, you inspect 50% of the receipt. Assuming no quality failures were found in those rounds, you may decide to reduce the inspection sampling size to only 10% of the receipt for subsequent rounds. Rounds identify the number of times that a test is performed at a specific level before moving to the next level in the testing plan. For example, if a level requires 5 rounds of testing, then the assigned item sampling should be used for all 5 rounds before moving to the next level, which may use a different item sampling.

- **Test group flexibility** – Using a flexible sampling plan, you can change a plan's current test group, which identifies the individual tests performed, to a different test group based on inspection results. For example, if prior testing results show minimal problems in the quality of receipts, you might choose to change the test group to a less stringent set of tests. You can also specify different test groups for different levels in a flexible sampling plan.

- **Skip lot inspections** – Skip lot inspections, which are an alternative to lot-by-lot inspections, allow you to skip a set number of goods during testing. For example, a Quality manager may set up a flexible sampling plan for a long-time supplier to inspect a quantity of 10 units and then skip the next 10 units. This decision was made based on the vendor having demonstrated that the quality of their receipts is very good. Receipts that do not require inspection are put away and a quality order is not generated. With the flexibility to perform lot-by-lot inspections instead of unit-by-unit inspections, as well as the use of other features such as sampling size variations, skip lot inspections, and test group flexibility, this type of inspection plan helps to minimize time, costs, handling damage, and inspection errors for your company.

### Setting up Flexible sampling plans

You set up new flexible sampling plans in the **Flexible sampling plans** form. Each plan is made up of different testing levels that identify the testing process, such as which test group and/or item sampling, and the order in which the levels are performed. For each plan you create, if the **Alert** or **Expire AVL/Alert** option is set up for a plan level, then you can assign an alert role to be notified if the specified number of failures for that level is reached.

After you set up the criteria for each of the plan's levels, you then establish the quality association for the plan to identify the testing activities (for example, purchases, specific vendor account, and specific item) and to generate quality orders based on test results. You establish the quality association on the **Specifications** FastTab in the **Quality associations** form.

**Example:**

A manufacturing company currently uses item sampling functionality for testing goods received in shipments. However, to reduce costs associated with testing, they need greater flexibility in their testing approach. The company's testing statistics over the past year show minimal exceptions were found during their inspections of a particular item. So to reduce costs they decide to implement flexible sampling. With flexible sampling they can not only vary or reduce the sampling size based on prior testing results, but they can skip certain lots from testing as well.

| **Path: Inventory management \> Setup \> Quality control \> Flexible sampling plans** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a new flexible sampling plan. |  |
| Delete | Delete a flexible sampling plan.</br>**Note:** You cannot delete a flexible sampling plan code if dependent quality orders are currently using the plan or if activity is being tracked against the plan. To delete the plan you must first delete any dependent quality orders as well as any tracking activity. |  |
| Copy plan | Copy an existing flexible sampling plan to use in creating a new plan. For example, you might copy an existing plan that is similar to the plan you want to create, which reduces the time involved in setting up the new plan. |  |
| View activities | View the activities associated with a flexible sampling plan. These activities might include which test groups and samplings were used to create the quality orders, as well as any quality tests that were skipped based on the criteria defined in the plan. |  |
| **Fields** | &nbsp; | &nbsp; |
| Flexible sampling plan code | Define the identifier for a new flexible sampling plan. |  |
| Description | Enter or view a brief description for the new flexible sampling plan. |  |
| Alert role | Select or view the role for the employee who is to receive alerts when certain types of quality failures occur. |  |
| Last level | Select the level number for the last activity to be performed in this flexible sampling plan process. The last level is open ended and you cannot specify a number of rounds for this level. |  |
| Approved | Check if the plan is approved. You can only approve a plan if the plan has a last level and the fail and pass action level on all the plan lines are set and identify valid levels in the plan. If there is a fail action code then the plan must also have an alert role. | Only approved plan are available for selection on Quality associations |
| Level | Select or view the level number assigned to this activity level. |  |
| Item sampling | Select or view the identifier that determines the specific sampling size, for example a 10 percent sampling or a 50 unit quantity sampling. |  |
| Test group | Select or view the identifier for the test group that is responsible for creating the quality order for the specific level in the flexible sampling plan. |  |
| Rounds | Enter or view the number of testing rounds for a specific flexible sampling plan level that must pass quality order validation to advance to the next level. Once you select a level for the **Last level** field, any **Rounds** value you entered for that level is removed from the plan. It is removed from the plan intentionally to allow the last level to continue indefinitely until a number of failures regresses the plan to a prior level.</br>**Note:** The last level in the testing plan does not allow rounds because all future tests would then remain at this level indefinitely until the appropriate number of fails is met to revert the plan to a prior level. | Assume a quality association has been set up to test purchase order registrations for a certain vendor.</br>The vendor's flexible sampling plan requires that 10% of every registration be tested for 5 rounds. So if I receive 100 units, then a quality order is generated to test 10 of those units. The quality order for the first registration passes. However, the second quality order fails, but the next three pass. Assuming that round 6 passes, then the first level in the plan is accomplished as the number of passed rounds required has been met. |
| Time span (days) | Enter or view the number of days by which the specified number of rounds must be completed. This field is optional.</br>**Note:** This field works in conjunction with the **Rounds** field. If a time span is defined, then the specified number of rounds must pass inspection within this time frame to advance testing to the next level. For example, if you set the time span to 60 days and the rounds to 10, then ten quality orders for this quality association must pass within 60 days to advance to the next level in the plan. |  |
| Skip | Select this check box to enable skip lot sampling, which allows for only a fraction of the submitted lots to be inspected. When you select this check box, you must enter the skip range in the **Frequency** fields. |  |
| Test frequency | If the **Skip** field is selected, enter the first number in the Skip range. |  |
| Out of frequency | If the **Skip** field is selected, enter the last number in the Skip range. | Assume the quality association is set for Production order registrations. The flexible sampling plan associated with this reference type uses the Skip feature where the **Test frequency** field is set to **1** and **Out of frequency** is set to **5**. Based on these settings, a quality order is generated to test 1 out of every 5 registrations. The determination as to which registrations of the 5 are tested and which ones are skipped is randomly made. |
| Number of fails | Enter or view the number of failed tests allowed before the flexible sampling plan reverts to a previous testing level, which may be more or less restrictive than the current test based on prior testing results. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails before the plan reverts to a prior level. | A vendor might initially define a plan to test 10 out of 40 receipts to minimize costs associated with testing. However, because recent testing results support a notable increase in failures, the current level ends and a different level to test 20 out of 40 receipts replaces it. To the contrary, if the vendor's testing quality is consistent with no failures, then the level may be replaced by a level that requires a lower number of fails. |
| Consecutive | Select this check box if the number of fails specified in the **Number of fails** field must be consecutive failures. If selected and the number of consecutive fails is reached, then the appropriate action based on the fail action level and code is initiated. | If the number of fails allowed is set to **2** and this check box is selected, then two consecutive fails generates a predefined fail action, such as issuing an alert notification to the Quality manager. |
| Fail action level | Enter or view the level of action that is initiated when the quantity in the **Number of fails** field is reached. This action indicates that more testing is required. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails to initiate the action. For example, if two consecutive quality orders fail at Level 3, then the action defined may require that testing start over at Level 1.</br>You can assign any prior level that is currently defined in the flexible sampling plan that is at least equal to or less than the current level. |  |
| Fail action code | Select the action code that defines the action to take when the failure criteria is met or exceeded for the flexible sampling plan. All of the actions return the test sampling process to the fail action level.<ul><li>**Alert** — Return the test sampling to the Fail action level and issue an alert to the alert role specified.</li><li>**Expire/AVL/Alert** — Return the test sampling to the Fail action level, issue an alert to the alert role specified, and change the vendor or item in the **Approved Vendor List** (AVL) to **Expired** if the quality association is purchasing and an AVL is in effect for that vendor.</li><li>**None** — Return the test sampling to the Fail action level specified for the current level.</li></ul> |  |
| Pass action level | Enter or view the level of action that is initiated when the tests pass for this line.</br>You can assign any level that is currently defined in the flexible sampling plan. |  |

### Tracking activities for Flexible sampling plans

To inquire about and track activities associated to a flexible sampling plan, you use the **Flexible sampling plan activities** form. For example, the activities for a plan might specify which test groups and samplings were used for creating quality orders, as well as which quality orders were skipped based on skipping criteria defined in the plan.

Each activity captures pertinent information about the account, item, and testing level at the most granular level. For example, if a flexible sampling plan code is associated with a quality association for All vendors and a specific Item quality group, then the information displayed includes the reference type (Purchase), vendor's account number, specific item number, and the current testing level.

| **Path: Inventory management \> Periodic \> Quality management \> Flexible sampling plan activities** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Flexible sampling plan activity summary | View a summary of activity for the selected flexible sampling plan code. |  |
| Flexible sampling plan activity details | View the specific details of the flexible sampling plan you select. |  |
| Flexible sampling plans | View the specific activity details for the flexible sampling plan you select. You can also create a new flexible sampling plan from this form. |  |
| **Fields** | &nbsp; | &nbsp; |
| Flexible sampling plan code | The identifier for the flexible sampling plan. |  |
| Reference type | The type of reference for the activity.<ul><li>Sales</li><li>Purchase</li><li>Production</li><li>Co-product production</li><li>Route operation</li><li>Quarantine</li></ul> |  |
| Account | The account identifier for the reference type. | If the reference type is Sales, then this field displays the customer's account number. |
| Item number | The identifier for the item associated with the reference type. | If the reference type is Sales, then this field displays the identifier for the item sold. |
| Resource | The resource, such as a person or a machine, when the quality association is the reference type **route operation**. |  |
| Current level | The level at which the selected flexible sampling plan is currently being tested. |  |

### Viewing activity details for Flexible sampling plans

To view specific details of all activities that have occurred against an active Flexible sampling plan, you use the **Flexible sampling plan activity details** form.

To facilitate viewing and interpreting activity, the following color-coded shading is used to designate certain rows in the Activity details list.

- **Grey shading** – Indicates a change in the testing level, for example from level 10 to level 20.

- **Lime shading** – Indicates that this level uses Skip Lot sampling and illustrates the number of quality orders that were created and the number that were skipped.

- **Red shading** – Indicates that tests for this level failed and the failed action code was initiated.

- **Blue shading** – Indicates a pass action reference line based on the current testing level.

| **Path: Inventory management \> Periodic \> Quality management \> Flexible sampling plan activities** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Flexible sampling plan activity summary | View a summary of current activities for the selected flexible sampling plan. |  |
| Overall activity statistics | View the following statistics in graphical format:<ul><li>Current round activity (Rounds) – Illustrates the number of rounds that passed and failed.</li><li>Current round activity (Quality orders) – Illustrates the number of quality orders that were created and the number that were skipped.</li><li>Overall statistics – Illustrates the current round activity for both the rounds and the quality orders.</li></ul> |  |
| Change activity level | Select a new activity level and reason code for this flexible sampling plan and enter a free-form reference. For example, assume a flexible sampling plan is defined for a specific item and vendor, and the vendor later initiates a new manufacturing process. You can assign a new flexible sampling plan level manually, as there may be issues with this new process. |  |
| Delete current level | Delete the activities for the current level. For example, if you want to repeat the current level of testing, you can use this action to delete activities for the current level and then repeat the testing process for this level. |  |
| Delete all activities | Delete all activities for this flexible sampling plan. For example, if you want to repeat all testing levels for this plan, you might want to delete all activities and then start again. |  |
| **Fields** | &nbsp; | &nbsp; |
| Flexible sampling plan code | The identifier of the flexible sampling plan.</br>**Note:** You can double-click the flexible sampling plan code to open the related flexible sampling plan to view the details for this plan. To return to activity details, close the flexible sampling plan after you view it. |  |
| Reference type | The type of reference for the activities, such as Purchase, Sales, Production, Co-product production, Quarantine, or Route operation. |  |
| Item number | The identifier of the item associated with the reference type. For example, if the reference type is **Sales**, then this field displays the identifier of the item sold. |  |
| Account selection | The account identifier of the reference type. For example, if the reference type is **Sales**, then this field displays the customer's account number. |  |
| First activity | The date on which the first activity was recorded against this reference of the flexible sampling plan. |  |
| Created date and time | The date and time that this activity was created for this specific reference to the flexible sampling plan. |  |
| Level | The current level of testing for this activity in the overall testing plan. |  |
| Test group | The identifier for the test group that was responsible for creating the quality order for this level in the flexible sampling plan. |  |
| Round number | The number of the last round of passed tests at the current level. |  |
| Item sampling | The identifier for the item sampling code that was used when creating the quality order for this level in the flexible sampling plan. |  |
| Skip | If selected, then this flexible sampling plan used skip lot sampling in the testing process. |  |
| Frequency | If skip lot sampling is allowed for this flexible sampling plan, then this is the last number in the range that was skipped during testing. |  |
| Quality order | The quality order number if a quality order was created for this activity. If a quality order was not created for the activity, for example, if skipping occurred, then this field is blank. |  |
| Status | The status of the quality order if a quality order was generated for the activity. The status values are **Pass, Fail** or **Skipped**. |  |
| Validated by | The identifier for the worker responsible for testing at the current level and who validated the quality order as **Pass** or **Fail**, if one was generated. |  |
| Validated date and time | The date and time when the quality order was validated, if applicable. |  |
| Fail action level | If the activity failed, then this is the level to which testing returns to begin retesting the activity as specified in the related flexible sampling plan. |  |
| Fail action code | If retesting is required as indicated in the **Fail action level** field, then the action code in this field defines the action needed. If retesting is not required, then this field is blank. The fail actions codes are:<ul><li>**Alert** – Return the test sampling to the previous action level and issue an alert to the alert role specified.</li><li>**Expire AVL/Alert** – Return the test sampling to the previous action level, issue an alert to the alert role specified, and change the vendor or item in the Approved Vendor List (AVL) to "expired" if the quality association is purchasing and an AVL is in effect for the vendor.</li><li>**None** – Return the test sampling to the previous action level.</li></ul> |  |
| Pass action level | If the activity level passes, then this is the level to which testing continues as specified in the related flexible sampling plan. This level is often the next level but flexibility is supported so that any level can be chosen. |  |
| Reason code | The identifier for the reason code used if the current level of activity in this plan was manually changed to a prior level. |  |
| Reference | A brief description of a change to the activity, such as a change to the status of a Quality Order. |  |
| Modified by | The identifier for the user who changed the activity. |  |
| Modified date and time | The date and time that the user changed the activity. |  |

### Viewing activity summaries for Flexible sampling plans

To view a summary of activities associated to a flexible sampling plan in summary form, you use the **Flexible sampling plan activity summary** form.

| **Path: Inventory management \> Periodic \> Quality management \> Flexible sampling plan activities** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Flexible sampling plan activity details | View activity details for the selected flexible sampling plan. |  |
| Activity graph | View a graphic that illustrates the number of rounds that passed and failed and the number of quality orders that were created and skipped. |  |
| Change activity level | Select a new activity level and reason code for this plan and enter a free-form reference. For example, assume a flexible sampling plan is defined for a specific item and vendor, and the vendor later initiates a new manufacturing process. You can create a new flexible sampling plan level manually, as there may be issues with this new process. |  |
| Quality associations | View the rules that are defined for the quality association that is used by this flexible sampling plan. |  |
| Non conformances | View non-conformances that are related to the selected flexible sampling plan. |  |
| Quality orders | View the quality orders that are related to the selected flexible sampling plan. |  |
| **Fields** | &nbsp; | &nbsp; |
| Flexible sampling plan code | The identifier for the flexible sampling plan. |  |
| Reference type | The type of reference for the activity.<ul><li>Sales</li><li>Purchase</li><li>Production</li><li>Co-product production</li><li>Route operation</li><li>Quarantine</li></ul> |  |
| Type | View the type of CAPA process. |  |
| Item number | The identifier of the item associated with the reference type. | If the reference type is **Sales**, then this field displays the identifier of the item sold. |
| Account selection | The account identifier of the reference type. For example, if the reference type is **Sales**, then this field displays the customer's account number. |  |
| Resource | The resource, such as a person or a machine, when the quality association is the reference type **route operation**. |  |
| Current level activity | View a summary of activity for the current level for this flexible sampling plan.<ul><li>**Level** - The current level number in the overall testing plan.</li><li>**Item sampling** - The item sampling that is being used at this current level of testing.</li><li>**Test group** - The test group assigned to create quality orders for this level.</li><li>**Round** - The number of the last round of passed tests at the current level.</li><li>**First date** - The date on which testing began at this level.</li></ul> |  |
| Current level details (Flexible sampling plan) | View the details of activity for the current level of activity for this flexible sampling plan. This section provides easy access to how the current level was defined based on the criteria for this specific flexible sampling plan.<ul><li>**Rounds** - The number of passed testing rounds required for this current level in the related flexible sampling plan.</li><li>**Fails** - The number of failures allowed before the testing process for this flexible sampling level stops and is replaced by a different and potentially more stringent item sampling.</li><li>**Consecutive** - Select this check box if the number specified in the **Fails** field must to be consecutive fails.</li><li>**Skip -** Select this check box to use skip lot sampling in your testing process. If you choose not to use skip lot sampling, leave this check box blank.</li><li>**Frequency** - If you select the **Skip** check box, enter the beginning and ending range of lots to be skipped during testing.</li><li>**Fail action level** - The level at which the current testing process will stop if the number of failed tests prior to this level reach the number specified in the **Fails** field. When this occurs, the Fail action code is activated and more stringent.</li></ul><ul><li>**Fail action code** - The action code that defines the action taken when the failure criteria is met or exceeded for a quality order. All of the actions return the testing to the Fail action level specified.</li></ul><ul><li>**Pass action level** - If the activity level passes, then this is the level to which testing continues as specified in the related flexible sampling plan. This level is often the next level but flexibility is supported so that any level can be chosen.</li></ul> | If the level requires 10 rounds and the time span is defined as 60, then 10 quality orders for the related quality association must pass within a 60 day period.</br>If number of fails is set to 2 and the Consecutive check box is selected, then 2 consecutive fails on the quality order activate the Fail action level and Fail action code.</br>If you specify 10 in the first field and 50 in the second field, then when testing at this level, for the next 50 possible testing rounds you randomly select only 10 rounds to test. |
| Current round activity | View a summary of results for the current round of activity for this flexible sampling plan.<ul><li>**Number of potential tests** - The number of possible tests to be performed at this level.</li><li>**Number of Quality orders created** -The number of quality orders created as of this round.</li><li>**Number of Quality orders skipped** - The number of quality orders that were skipped as of this round.</li><li>**Number of tests passed** - The number of tests that passed this level of testing.</li><li>**Number of tests failed** - The number of tests that failed this level of testing.</li><li>**Next level** - The number of the next level in the testing process.</li><li>**Fail action triggered** - Indicates whether the failed action was initiated.</li><li>**Fail action reason code** - The identifier for the fail action code if the fail action was initiated.</li></ul> |  |

## Approved customer lists (ACL)

You may often sell products and services on a recurring basis to certain customers or groups of customers who have been approved for these purchases based on their prior and on-going business relationship. By pre-approving customers, you not only expedite the sales order process and shipment of the product, but you also validate that the product is sold only to those customers who are allowed to purchase it. This also prevents a product from being sold to customers who are not authorized to buy it.

For example, one of your long time customers, Super Club, can purchase only their own private labeled products. They sell this product at both their Super Club warehouse location and their retail location, Super Mart. As a manufacturer of apple juice, you produce private label juices. You sell Super Club's private label apple juice cases only to Super Club Warehouse and Super Mart. This particular product cannot be sold to any other customer.

### Setting up approved customers

To authorize an approved customer or an approved customer group for recurring sales, or to restrict who you can sell a given product to, you use the **Approved customer list setup** form.

When you set up new approved customer/item relationships, you also establish the ACL check method, which provided the level of warning that is needed for a particular item or customer. Likewise, you also specify the type of relationship between the customer and item, which can be any of the following:

- A specific customer approved to purchase a specified item

- A specific customer approved to purchase any item in a specified item group

- A customer group approved to purchase a specified item

- A customer group approved to purchase any item in a specified item group ( "Group to Group")

### Establishing ACL check methods

When you approve a product for a customer, you also set up an ACL check method at both the customer level and the item level to confirm that this customer is approved to purchase this item. This process of verifying the customer/item combination is referred to as the ACL check method.

This method determines the action taken if you select a customer and/or item that is not listed in the item's approved customer list. It also confirms that the transaction date is within the effective approval period specified for the customer and the item. You can set up the check method to issue a warning or to prevent the transaction from being processed.

The check methods include the following:

- **No check** – No validation is performed. Therefore, any customer or item that you select is allowed.

- **Warning only** – A warning message is displayed, but you can continue with the transaction.

- **Not allowed** – An error message is displayed and this transaction is not allowed.

### Approved customer list setup

To set up and maintain customers who are approved to purchase one or more products, you use the **Approved customer list setup** form.

| **Path: Product information management (or Sales and marketing) \> Setup \> Approved customer list \> Approved customer list setup** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a customer or approved customer group relationship to an item or approved item group. |  |
| Delete | Remove a customer or approved customer group relationship to an item or approved item group. |  |
| Edit | Edit the effective and expiration dates for a customer's approval period. |  |
| View | Select a view option to locate item or approved item groups within the customer's effective date range. The two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records with an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |

| **Path: Product information management (or Sales and marketing) \> Setup \> Approved customer list \> Approved customer list setup** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Fields** | &nbsp; | &nbsp; |
| Item code | Select or view the item relationship code for which this item is approved. The values are:<ul><li>**Table** – Designates a specific item.</li><li>**Group** – Designates an approved item group.</li><li>**All** – All items are designated.</li></ul> |  |
| Item relation | Select or view the identification for the item or approved item group. |  |
| Customer code | Select or view the customer relationship code for which this item is approved. The values are:<ul><li>**Table** – Designates a specific customer.</li><li>**Group** – Designates an approved customer group.</li><li>**All** – All customers are designated.</li></ul> |  |
| Customer relation | Select or view the identification for the customer or approved customer group. |  |
| Effective | Select or view the effective date on which the ACL approval to purchase the item or items starts. The default is the current date. |  |
| Expiration | Select or view the date on which the ACL's approval to purchase the item or items expires. The default is **Never**. |  |

### Viewing customers and approved customer groups

To view lists of approved customers, you can access from any of the following forms, depending on the information you wish to obtain:

- Approved customer list

- Approved customer list by item

- Approved customer list expiration

#### Approved customer list

To set up and maintain customers who are approved to a specific item, you can also use the **Approved customer list** form. This form provides access to the Approved Customer List while filtering the data based on the Released product selected.

| **Path: Product information management \> Common \> Released products \> Sell tab \> Approved customer \> Setup** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a customer or approved customer group relationship to the item. |  |
| Delete | Remove a customer or approved customer group relationship. |  |
| Edit record | Edit the effective and expiration dates for a customer's approval period. |  |
| View | Select a view option to ACL records for the item within the customer's effective date range. The two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records with an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Item number | The identification for the product. | This defaults to the item selected. |
| Product name | The name of the product. |  |
| Customer code | Select or view the customer relationship code for which this item is approved. The values are:<ul><li>**Table** - The item is approved for this specific customer.</li><li>**Group** - The item is approved for this approved customer group.</li><li>**All** - The product is approved for all customers.</li></ul> |  |
| Customer relation | Select or view the identification for the customer or approved customer group. |  |
| Effective | Select or view the effective date on which the customer's approval to purchase the item starts. The default is the current date. |  |
| Expiration | Select or view the date on which the customer's approval to purchase the item expires. The default is **Never**. |  |

#### Approved customer list by item

To view a list of customers who are approved to purchase a specific product, you use the **Approved customer list by item** form.

| **Path: Product information management \> Common \> Products \> Released products \>**</br>**Sell tab \> Approved customer group \> Approved customers** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| View | Select a view option to locate customers within the item's effective date range. These two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records that have an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Item number | The identification for the product. |  |
| Product name | The name of the product. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Customer account | The account identification for the customer. |  |
| Name | The name of the customer |  |
| Effective | The effective date for this particular customer. |  |
| Expiration | The expiration date for this particular customer. |  |

These display-only forms, such as the one below, display a 'resolved' approved customer list. This 'resolved' concept consists of exploding either the approved customer group or approved item group to its individual records. These records are then displayed on these non-maintenance ACL forms. For example, where the form above allowed the user to maintain the approved customer group of CustGrpA for item number 40 ASD this form displays all of the customers that are approved to purchase this item. These customers shown below are assigned to the approved customer group of CustGrpA. Since these records are displaying exploded versions (resolved) of the approved customer list, the records cannot be maintained on these forms.

#### Approved customer list expiration

To view a list of customers who are approved to purchase a specific product prior to a certain expiration date, which is the date on which a customer's approval to purchase a certain product ends, use the **Approved customer list expiration** form.

| **Path: Product information management \> Common \> Products \> Released products \>**</br>**Sell tab \> Approved customer group \> Effective period** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records that have an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Item number | The identification for the product. | This defaults to the item number selected. |
| Product name | The name of the product. |  |
| As of | Select a date as of which you want to view items that are approved for purchase by this customer when you use the **View** FastTab search feature. | This defaults to the current date. |
| Include never expired | Select this check box if you wish to include in the **View** FastTab search any approved items that do not expire. |  |
| Name | The name of the customer approved to purchase this item. |  |
| Customer account | The account identification for the customer. |  |
| Effective | The effective date for this particular item. |  |
| Expiration | The expiration date for this particular item. |  |

### Viewing items and approved item groups

To view lists of approved items for a specific customer, you can access from any of the following forms, depending on the information you wish to obtain:

- Approved customer list
- Approved customer list by customer
- Approved customer list expiration

#### Approved customer list

To set up and maintain items that are approved for a specific customer, you can also use the **Approved customer list** form. This form provides access to the Approved Customer List while filtering the data based on the Customer selected.

| **Path: Sales and marketing \> Common \> Customers \> All customers \> Sell tab \> Approved customer \> Setup** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add an item or approved item group relationship to the Customer. |  |
| Delete | Remove an item or approved item group relationship. |  |
| Edit record | Edit the effective and expiration dates for an item's approval period. |  |
| View | Select a view option to ACL records for the customer within the item's effective date range. The two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records with an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Customer account | The identification for the customer. | This defaults to the customer selected. |
| Name | The name of the customer. |  |
| Item code | Select or view the item relationship code for which this customer is approved. The values are:<ul><li>**Table** - The item is approved for this specific customer.</li><li>**Group** - The item is approved for this approved customer group.</li><li>**All** - The product is approved for all customers.</li></ul> |  |
| Item relation | Select or view the identification for the item or approved item group. |  |
| Effective | Select or view the effective date on which the customer's approval to purchase the item starts. The default is the current date. |  |
| Expiration | Select or view the date on which the customer's approval to purchase the item expires. The default is **Never**. |  |

#### Approved customer list by customer

To view a list of items that are approved to be purchased by a specific customer, you use the **Approved customer list by customer** form.

| **Path: Sales and marketing \> Common \> Customers \> All customers \> Sell tab \> Approved customer \> Approved items** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records that have an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Customer account | The identification for the customer. |  |
| Name | The name of the customer. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Item number | The account identification for the item. |  |
| Product name | The name of the item. |  |
| Effective | The effective date for this particular item. |  |
| Expiration | The expiration date for this particular item. |  |

Similar to the Approved customer list by item form, these display-only forms display a 'resolved' approved customer list. This 'resolved' concept consists of exploding either the approved customer group or approved item group to its individual records. These records are then displayed on these non-maintenance ACL forms. Since these records are displaying exploded versions (resolved) of the approved customer list, the records cannot be maintained on these forms.

#### Approved customer list expiration

To view a list of items that are approved to be purchased by a specific customer prior to a certain expiration date, which is the date on which a customer's approval to purchase a certain product ends, use the **Approved customer list expiration** form.

| **Path: Sales and marketing \> Common \> Customers \> All customers \> Sell tab \> Approved customer \> Effective period** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records that have an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Customer account | The identification for the customer. | This defaults to the customer number selected. |
| Customer name | The name of the customer. |  |
| As of | Select a date as of which you want to view items that are approved for purchase by this customer when you use the **View** FastTab search feature. | This defaults to the current date. |
| Include never expired | Select this check box if you wish to include in the **View** FastTab search any approved items that do not expire. |  |
| Item number | The name of the item approved to be purchased by this customer. |  |
| Product name | The account identification for the item. |  |
| Effective | The effective date for this particular customer. |  |
| Expiration | The expiration date for this particular customer. |  |

#### Approved customer list by customer

To view a list of products that have been approved for a specific customer to purchase on a recurring basis, you use the **Approved customer list by customer** form. An approved customer is authorized to order certain products, which expedites the sales order process and allows the product to ship more quickly.

| **Path: Sales and marketing \> Common \> Sales orders \> All sales orders \>**</br>**General tab \> Related information group \> Approved items** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.<ul><li>**Current** - Select this option to display records that have an effective date prior to the current date.</li><li>**All** - Select this option to display all records.</li></ul> |  |
| **Fields** | &nbsp; | &nbsp; |
| Customer account | The account identification for the customer. | This defaults to the customer on the sales order. |
| Customer name | The name of the customer. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Item number | The item approved for this customer. |  |
| Product name | The name of the item. |  |
| Effective | The effective date for this particular item. |  |
| Expiration | The expiration date for this particular item. |  |

#### Setting up approved customer groups and approved item groups

Customer and item groups allow you to set up groups of customers and groups of items to expedite the approval process when the same set of items are approved for a specific customer, a group of customers, or all customers. If the approved item group is associated to an approved customer group, every customer in the group is authorized to purchase every item in the approved item group.

#### Setting up approved customer groups

To set up, maintain, and view a group of customers who are approved to purchase a certain item or approved item groups during the specified effective period, you use the **Approved customer groups** form. You can associate the approved customer group to one or more items, approved item groups, or all items.

| **Path: Sales and marketing \> Setup \> Approved customer list \> Approved customer groups** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add an approved customer group. |  |
| Delete | Delete the selected approved customer group.</br>**Note:** You cannot delete an approved customer group if it is currently assigned to a customer or has a record relationship in the ACL. |  |
| Add (Customer list tab) | Add a customer to this Approved Customer Group. |  |
| Remove (Customer list tab) | Remove the selected customer from the Approved Customer Group. |  |
| Remove (Assign customers using query tab) | Remove the selected customer from the query list. |  |
| Select query (Assign customers using query tab) | Opens the search query form allowing the user to enter criteria for specific customers. |  |
| Add all to group (Assign customers using query tab) | Add the selected Customers to the selected Approved customer group. |  |
| New (Approved items fast tab) | Add an item or an approved item group for the selected Approved Customer Group. |  |
| Delete (Approved items fast tab) | Remove the selected item or approved item group. |  |
| Edit (Approved items fast tab) | Edit the current ACL record. |  |
| View (Approved items fast tab) | View all or current records based on Effective and Expiration date. |  |
| **Fast tabs** | &nbsp; | &nbsp; |
| Customers | Set up, maintain, and view customers who are associated with the selected Approved Customer Group. | Use the <em>Assign customers using query</em> tab to search for and select a subset of Customers based on any combination of customer fields and values. This subset of customers, once finalized, can be added to the selected Approved customer group at the same time using the <em>Add all to group</em> button |
| Approved items | Set up, maintain, and view items or approved item groups that are approved to be purchased by customers who are associated with the selected approved customer group. |  |
| **Fields** | &nbsp; | &nbsp; |
| Approved customer group | Enter or view the unique identification for the approved customer group. |  |
| Description | Enter or view the description of the approved customer group. |  |
| Customer account (Customer list tab) | The account identification for the customer. |  |
| Search name (Customer list tab) | Search name of the Customer. |  |
| Customer group (Customer list tab) | Customer group of the Customer. |  |
| Invoice account (Customer list tab) | Invoice account of the Customer. |  |
| Customer account (Assign customers using query tab) | The account identification for the customer. |  |
| Name (Assign customers using query tab) | The name of the customer. |  |
| Approved customer group (Assign customers using query tab) | Approved customer group the customer is associated with. |  |
| Item code | Enter or view the unique identification for the item or Approved Item Group. | The options are **Table**, **Group**, or **All**. |
| Item relation | Enter or view the name of the Approved Item Group if the Item code is set to Group. Enter or view the name of the item if the Item code is set to Table. |  |
| Effective | The effective date for this particular item or Approved Item Group. |  |
| Expiration | The expiration date for this particular item or Approved Item Group. |  |

You can also assign a customer to an Approved Customer Group using the **Customer** form.

| **Path: Sales and marketing \> Common \> Customers \> All customers \> Sales order defaults FastTab** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Fields** | &nbsp; | &nbsp; |
| Approved customer group | The group to which this customer is assigned for purposes of ACL |  |
| Approved customer list check method | The method of validation that is used when creating a sales order, sales agreement or sales quotation for this customer. |  |

#### Setting up approved item groups

To set up, maintain, and view a group of products that are approved for purchase by a certain customer or customers during the specified effective period, you use the **Approved item groups** form. You can associate the item group to one or more customers, customer groups, or all customers.

| **Path: Product information management \> Setup \> Approved customer list \> Approved item groups** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add an approved item group. |  |
| Delete | Delete the selected approved item group.</br>**Note:** You cannot delete an approved item group if it is currently associated with an item or used on an ACL record. |  |
| Add (Items tab) | Add an item to this Approved Item Group. |  |
| Remove (Items tab) | Remove the selected item from the Approved Item Group. |  |
| Remove (Assign items using query tab) | Remove the selected item from the query list. |  |
| Select query (Assign items using query tab) | Opens the search query form allowing the user to enter criteria for specific items. |  |
| Add all to group (Assign items using query tab) | Add the selected Items to the selected Approved item group. |  |
| New (Approved customers fast tab) | Add a customer or an approved customer group for this Approved item group. |  |
| Delete (Approved customers fast tab) | Remove the selected customer or approved customer group. |  |
| Edit (Approved customers fast tab) | Edit the current ACL record. |  |
| View (Approved customers fast tab) | View all or current records based on Effective and Expiration date. |  |
| **Fast Tabs** | &nbsp; | &nbsp; |
| Items | Set up, maintain, and view items that are associated with the selected Approved Item Group. | Use the <em>Assign items using query</em> tab to search for and select a subset of Items based on any combination of item fields and values. This subset of items, once finalized, can be added to the selected Approved item group at the same time using the <em>Add all to group</em> button |
| Approved customers | Set up, maintain, and view customers or approved customer groups that are approved to purchase item in the select approved item group. |  |
| **Fields** | &nbsp; | &nbsp; |
| Approved item group | Enter or view the unique identification for the approved item group. |  |
| Description | Enter or view the description for the approved item group. |  |
| Item number (Item list tab) | The identification for the product. |  |
| Search name (Item list tab) | The search name of the item. |  |
| Product name (Item list tab) | The product name. |  |
| Item model group (Item list tab) | The Item model group of the item. |  |
| Item number (Assign items using query tab) | The identification for the product. |  |
| Search name (Assign items using query tab) | The search name of the item. |  |
| Approved item group (Assign items using query tab) | Approved item group the item is associated with. |  |
| Customer code | Enter or view the unique identification for the customer or Approved Customer Group. | The options are **Table**, **Group**, or **All**. |
| Customer relation | Enter or view the name of the Approved Customer Group if the Customer code is set to Group. Enter or view the name of the Customer if the Customer code is set to Table. |  |
| Effective | The effective date for this particular customer or Approved Customer Group. |  |
| Expiration | The expiration date for this particular customer or Approved Customer Group. |  |

You can also assign an item to an Approved Item Group using the **Released products** form.

| **Path: Product information management \> Common \> Released products \> Sell FastTab** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Fields** | &nbsp; | &nbsp; |
| Approved customer list check method | The method of validation that is used when creating a sales order, sales agreement or sales quotation for this item. |  |
| Approved item group | The group to which this item is assigned for purposes of ACL |  |

#### Viewing current approved items for a customer

When entering a sales order for a specific customer you can use the Item number drop-down to provide a list of items for selection to add to the sales order line. If the customer associated with the sales order has a record in the Approved Customer List then an **Approved items** tab will be visible in order to make a selection. The Other tab contains all items.

| **Path: Sales and marketing \> Common \> Sales orders \> All sales orders** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Fields** | &nbsp; | &nbsp; |
| Item number | The identification for the product. |  |
| Product name | The name of the product. |  |
| Valid for | The ACL source that provides this ACL relationship. If the item has a direct relationship with the customer then the field will be "Table". If the item has a group relationship, either through an Approved Item Group or an Approved Customer Group to which this customer is associated, the field will be "Group". |  |
| Group | When there is a group relation between the Item and Customer and the 'Valid for' field is "Group" then this field indicates the group from which the relationship was resolved or derived. |  |
| Effective | The effective date for this particular item or Approved Item Group. |  |
| Expiration | The expiration date for this particular item or Approved Item Group. |  |

You may also select the **Add lines** option on the sales order line. Click the checkbox on the added Approved items button (defaults to being checked) to display all of the resolved items that this customer is authorized to purchase.

Both of these options will only show the approved items for which the customer is currently approved to purchase. If you feel that they should be other items available to this customer you can use the Approved items from the Customer form which will show all ACL record for the selected customer regardless of Effective or Expiration date.

#### Viewing all approved items for a customer

From the sales order form you can select to display all Approved items for the customer associated with the sales order by clicking the General tab and selecting Approved items.

This provides access to the Approved Customer List by Customer form from the sales order.

#### Configuring the date validation for the Approved Customer List

When entering Effective and Expiration dates for an Approved Customer List record there is validation performed when the check method is not set to 'No check'. The dates are validation for the various documents based on the configuration selection you make in the Sales and marketing parameters form.

| **Path: Sales and marketing \> Common \> Sales orders \> All sales orders** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Fields** | &nbsp; | &nbsp; |
| Date type | The date on the document that is selected for validation against the ACL record. The values are:<ul><li>Today - Today's date or system date</li><li>Requested ship date – The requested ship date on the sales order</li><li>Requested receipt date – The requested receipt date on the sales order</li><li>Order date – The date for which the order was placed</li></ul> | This allows you to validate the sales order against the ACL when the order is expected to ship, when it is expect to be received, or when the order is placed. The values of Today and Order date will usually provide the same result. |

## Electronic Signature (ESig)

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one.

Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, aerospace and defense. They are also necessary for compliance with regulations in 21 CFR Part 11 issued by the Food and Drug Administration (FDA) in the United States.

An electronic signature by itself is not the same as a digital signature. An electronic signature is simply a substitute for a handwritten signature, while a digital signature provides additional security measures. A digital signature can help identify whether another user or process has tampered with the data. A digital signature can also be verified, and this verification cannot be refuted by the owner of the certificate that was used to sign the data. As described below, electronic signatures in Microsoft Dynamics AX have built-in digital signature functionality.

In Microsoft Dynamics AX, you can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field. Electronic signatures in Microsoft Dynamics AX have built-in digital signature functionality. Each user who signs documents must obtain a valid cryptographic certificate. When a document is signed, the private key associated with that certificate is validated.

With EDGE of AX, Electronic Signature functionality has been enhanced to increase the security of the digital signatures to meet the latest government requirements and regulations.

### Setting up Electronic signature parameters

Using the Organization module, you maintain the various parameters for defining the controls you want to place on the capture of electronic signature of the various individuals for authorization of the various processes within your organization.

| **Path: Organization administration \> Setup \> Electronic signature \> Electronic signature parameters** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Translations | Opens a form where you can enter notice text in additional languages. |  |
| **Fields** | &nbsp; | &nbsp; |
| Notice | The notice that signers will see on the **Sign document** form. You can enter any text. Typically, this text tells the user what it means to sign a document electronically, including legal implications. |  |
| Require comments | Select this option if all signers are required to enter a comment when signing. |  |
| Signature timeout | An amount of time in seconds. If a signature has not been provided in this time frame, the signing process fails. |  |
| Key expiry | Number of days a digital key will be valid from its creation. |  |
| Signature alert recipient | The user id who should receive an alert email if signature validation fails. Validation fails if the system determines that the certificate and private key provided by a user show signs of tampering. |  |
| Minimum length | Required minimum length of the passphrase. | Hint: recommend at least a minimum of 8 characters |
| Minimum alpha | Required number of alpha characters in the passphrase. |  |
| Minimum numerals | Required number of numeric characters in the passphrase. |  |
| Minimum special | Required number of special characters in the passphrase. | Hint: special characters include: !, @, #, $, %, ^, &amp;, *, (, ), ;, :, ?, &lt;, \>, -, +, =, ~ |

***\*Note: All the parameters for the Passphrase constraints work in conjunction with the Windows policy requirements. The constraints can be more complex than the Windows policy however, it cannot be less complex. For example, if Windows policy dictates minimum length of 8 characters with couple of numbers and couple of special characters and the Passphrase constraints only requires 6 characters, the password will be rejected when generating the certificate.***

## Electronic Batch Records (EBR)

Electronic batch records are a requirement of the 21 CFR Part 11 requirement placed on Life Science industries, and Pharmaceutical industries in particular. Extensions are required to standard AX functionality to enable the consolidation of production related data in order to meet those requirements. EBR is composed of two major functions. One function is the Master Manufacturing Record (MMR) which documents all of the ways an item might be produced and the various ways the characteristics might be measured. The other function is the Batch Production Record (BPR) which documents the specific way an item was produced and the actual value of the characteristics measurements. It also details the characteristics and quantities of the ingredients used to produce the item.

### Setting up Electronic Batch Record

In order to activate Electronic batch records you have to select the feature for the desired company. You must also determine which processes should be managed with the capture of electronic or digital signature.

#### Utilizing Electronic Batch Records

First, select the desired company that will be utilizing electronic batch records. Select the parameters form for the Production Control module, select the Electronic Batch Record tab and select the 'Use electronic batch records' option.

When selected, a notification will be made to the user that you must remove the approval on BOMs, Formulas or Routes prior to editing those records. This allows for the capture of the electronic signature of the personnel performing these edits. By selecting to use EBR, the 'Block editing' functions, in Production Control for the Route and the 'Block editing' functions in Inventory and warehouse management for the BOM/Formulas, will be automatically selected and the option disabled. The Block Editing feature for Routes and BOM/Formulas prevents the editing of those records when the record is already approved. It requires that the approval is removed prior to editing and once editing is completed, the approval will need to be made before the record can be used in production.</br>If you elect to remove the 'Use electronic batch records' option for the selected company, then the 'Block editing' options in the Production Control parameter form and the Inventory and Warehouse Management parameter form will become enabled; however, the values will remain selected. If you desired to edit the records without first removing the approval then you will need to manually clear the 'Block editing' selections.

Since the electronic batch record is maintained independently of the batch order or production order, a number sequence needs to be established. From the Production Control parameters form within the desired company select the Number Sequences tab and navigate to the Batch production record reference. Select or create a new number sequence and designate it accordingly.

#### Setting up Electronic Signature Parameters

Before setting up the requirements for electronic signature, you need to establish the parameters. These parameters are detailed in the previous chapter.

#### Setting up Electronics Signature Requirements

With the addition of EBR, new electronic signature requirements have been added. EBR requirements would normally be the posting of Picking lists, Route cards, Jobs cards, and Report as finished production journals. Other **eSignature** requirements may be desired to capture digital signatures for approving and activating BOM/Formula and Routes and the release of batch/production orders to the production floor. When EBR is in use, you should not use the Report as Finished action in the Process update action group. When EBR is in use, only production journals should be used for batch/production orders.

When the 'Post route card production journal' requirement is selected, a notification will be made to the user that the posting of Route card journals can no longer be performed automatically by Starting the Batch or Production order. Likewise, selecting 'Post picking list production journal (non-dispensing)' will make a notification that the posting of Picking list journals can no longer be performed automatically by Starting the Batch or Production order. Also, the Report as finished option of the Batch or Production order will be disabled. In order to RAF a Batch or Production order, the user will have to use the Report as finished production journal. This is due to the need to capture the electronic signature of the individuals who are posting those activities.</br>When the Route card production journal is unchecked, a notification will be made to the user that the posting of Route card journals can once again be performed automatically by Starting the Batch or Production order. Likewise, when the Picking list production journal is unchecked, a notification will be made to the user that the posting of Picking list journals can once again be performed automatically by Starting the Batch or Production order. Also, the Report as finished option of the Batch or Production order will once again be enabled.

When the 'Validate quality order' requirement is selected, a signature will be required upon the validation of quality orders. The signature will be required at the validation of the overall quality order, not the validation of the individual Test of the Test group of the quality order.

#### Configuring Work Instructions for BOM and Formula items

To establish work instructions for an ingredient line, you will need to edit the Formula line. When EBR is in use, the editing of formula lines will be blocked when the formula is approved. In order to edit the Formula you'll need to remove that approval. Access the Formula form, or the Bill of material form from the Common section of the Inventory Management module. In the form you will see the BOM/Formula version in the lower portion of the form and the BOM/Formula lines in the upper portion of the form. Click **Approve** and select to **Remove approval**. Then click **Lines** to display the multiple ingredient lines for that BOM/Formula. Select the desired ingredient and click the **Work instructions** tab. Click **Add** to add a new work instruction for that ingredient. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of adding that particular ingredient in the production process.

#### Configuring Work Instructions for Routes

To establish work instructions for an operation line, you will need to edit the Route. When EBR is in use, the editing of Routes will be blocked when the route is approved. In order to edit the Route, you'll need to remove that approval. Access the Route form from the Common section of the Production Control module. Another method to edit the Route is to access the route from the **Released Products** form from the Common section of the Product Information Management module. After you select the desired Item, select the **Engineer** tab, and click **Route** in the **View** action group. Select the desired operation and click the **Work instructions** tab. Click **Add** to add a new work instruction for that operation. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable work instruction text that is needed to convey the proper instructions or comments about the process of executing that particular operation in the production process.

#### Configuring Test Plan instructions for Test Groups

To establish test plan instruction for a test group, you will edit the actual test sequence within the test group. The test plan instruction will be visible within a quality order, but cannot be edited. Select the Test Group menu option from the Setup section in the Inventory Management module. Select the desired **Test Group** and then select the applicable **Sequence Number**. The sequence number will be related to a particular test, such as testing for the percentage of fatty acid in the product. Click the **Test** tab and the **Test Plan** will be displayed in the right side of the lower pane. Click **Add** to add a new test plan instruction for that test sequence. Select the **Type** of *Note* and enter a short**Description**. In the lower text box, enter the applicable test plan text that is needed to convey the proper instructions or comments about conducting that particular test. This might include not only the method, but the environmental parameters that should be present such as temperature, or what equipment to use to conduct the test.

Once the Test Plan instructions have been associated with the Test Group, the Quality Order that references that Test Group will display the Test Plan instructions for that particular test sequence in a read-only mode.

### Using Electronic Batch Records

Once all of the production data has been maintained for the BOM item or Formula item, then you will be able to execute inquires that are the primary functions of EBR. EBR is composed of two major functions. One function is the Master Manufacturing Record (MMR) which documents all of the methods an item might be produced and the various ways the characteristics might be measured. Specifically, this inquiry will contain all of the BOM/Formula versions that are approved to use in the manufacturing of that particular item. It includes the various Route versions that have been approved as well. This information will also contain Quality Associations referenced to the production process of the item. These quality associations result in quality orders being generated for the item. If the item is an ingredient, there may be quality associations referenced for that ingredient that may generate quality orders during an inspection. Other characteristics may be referenced for the ingredients or produced items that indicate the type of characteristic that is being measured which may be related to a particular inventory batch dimension or information related to the vendor that supplied the ingredient.

The other function is the Batch Production Record (BPR) which documents the specific way the item was produced and the actual value of the characteristics measurements. It also details the characteristics and quantities of the ingredients used to produce the item. Specifically, this inquiry will contain the particular BOM/Formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. Where the Master Manufacturing Record maintained the types of characteristics that would be measured for the item, the Batch Production Record maintains the actual values of those measured characteristics. It will contain the actual detail of the Quality Orders that were referenced by the Quality Associations in the Master Manufacturing Record (MMR).

#### Using Master Manufacturing Record inquiry

When using the Master manufacturing record inquiry from the Production control module, you will select the desired Item number. You may select a Site which will limit the BOM/Formula and Route versions to that particular site. You may select a Date or Quantity that will perform a query similar to the process utilized by Master Scheduling that will filter the BOM/Formula and Route versions to those that meet the selection criteria for the selected date and/or quantity. For example, there may be multiple formula versions for the item, one for quantities from 0 to 500 and one version for quantities greater than 500. By leaving the Quantity blank or 0 (as shown below) then all formula versions will be shown. If the Quantity was entered as 600 then only the formula version for quantities greater than 500 will be displayed. If the Site is left blank, then formula versions that are not site-specific will be displayed along with those formula versions that are site-specific.

All applicable Route versions will be displayed in the inquiry. The BOM/Formula versions and the Route version number are hyperlinks so that you may click on the number and the actual detailed form for the version will be displayed. Quality associations that are referenced as Production or Co-Product Production will be displayed with some brief information. By clicking the Details menu option for the selected Quality association the detailed form for that quality association will be displayed. The Inventory batch attributes that have been defined for the produced item will be displayed with the applicable range and target value for each characteristic.

| **Path: Production control \> Inquiries \> Electronic batch records \> Master manufacturing record** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Criteria** | &nbsp; | &nbsp; |
| Item number | Select the item for which to list the manufacturing information | Field drop down will only list items with a 'Production type' of BOM, Formula or Planning item. |
| Site | Select a specific site for the selected item |  |
| Date | Enter a from date to filter the Formula/BOM version for the selected item |  |
| Quantity | Enter a from quantity to filter the Formula/BOM version for the selected item |  |
| **FastTabs** | &nbsp; | &nbsp; |
| General | Shows some general information for the selected item |  |
| BOM/Formula versions | List of the Formula/BOM versions of the selected item based on the specified criteria |  |
| Route versions | List of the Route versions of the selected item based on the specified criteria |  |
| Quality associations | List of all Quality association relations for the selected item | Use the Details button to open the Quality association form for the selected record. |
| Inventory batch attributes | List of all Inventory batch attributes specified for the selected item |  |

#### Using Batch Production Record inquiry

When using the Batch production record inquiry from the Production control module, you will select either the desired Item number or the Batch production record associated with a specific Batch or Production order. If the item number is selected prior to the Batch production record, then the pull down of the Batch production record field will list only records associated to the specified item. If the Batch production record is selected prior to the Item number, the Item number field will default to the item number related to the Batch or Production order associated with the Batch production record ID.

The inquiry will contain the particular BOM/Formula version that was used in the production process along with the proposed ingredient quantities that were estimated to complete the production. This information will also contain the exact quantities that were used, in comparison to what was estimated or proposed, and any new ingredient that may have been substituted during the production process. The Batch Production Record will give the user the ability to view the Inventory batch attributes and any Quality orders for the produced items as well as the Inventory batch attributes, Vendor batch details and Quality orders for the raw material items used in the production process.

| **Path: Production control \> Inquiries \> Electronic batch records \> Batch production record** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Criteria** | &nbsp; | &nbsp; |
| Item number | Select the item for which to list the manufacturing information | Field drop down will only list items with a 'Production type' of BOM, Formula or Planning item. |
| Batch production record | Select the Batch production record ID for a corresponding Batch or Production order | Required field. If selected before the item number, the Item number field will default to the item number of the Batch or Production order related to the Batch production record ID. |
| **FastTabs** | &nbsp; | &nbsp; |
| Production order | Shows the Batch or Production order related to the specified Batch production record ID |  |
| Report as finished | Shows the produced items (including co/by products for formula items) for the Batch or Production order related to the specified Batch production record ID | Tab will be populated when the RAF production journal has been created.</br>Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record.</br>Inventory batch attributes button will only be active if there is Batch number for the selected record.</br>Use the Quality orders button to view the Quality orders for the selected record. |
| BOM/Formula | List the raw material items used in the production of the selected item |  |
| Picking list | Shows the information from the Picking list production journal of the Batch or Production order | Tab will be populated when the Picking list production journal has been created.</br>Use the Inventory batch attributes button to open the Inventory batch attributes form to view the attribute information for the selected record.</br>Inventory batch attributes button will only be active if there is Batch number for the selected record.</br>Use the Vendor batch details button to open the Batches form to view the vendor batch information for the selected record.</br>Vendor batch details button will only be active if there is Batch number for the selected record.</br>Use the Quality orders button to view the Quality orders for the selected record. |
| Route | List the Route version used on the Batch or Production order |  |
| Route card | Shows the information from the Route card production journal of the Batch or Production order | Tab will be populated when the Route card production journal has been created. |
| Job card | Shows the information from the Job card production journal of the Batch or Production order | Tab will be populated when the Job card production journal has been created. |
| **Tabs** | &nbsp; | &nbsp; |
| Overview (Report as finished) | List the lines for each produced item based on the Report as finished production journal | If there were multiple (partial) RAFs, then the overview tab will list each line. |
| Transactions (Report as finished) | List the individual transaction lines for the produced items from the Inventory Registration |  |
| Overview (Picking list) | List the lines for each raw material item based on the Picking list production journal | If there were multiple (partial) Picking or if there is an Automatic reservation (ex. at Estimation), then the overview tab will list each line. |
| Transactions (Picking list) | List the individual transaction lines for each raw material item from the Inventory Reservation |  |

#### Using Batch Production Record reports

The Batch production record report gives the user the ability to view/print a report using the Batch production record ID. The simplified version of the report will contain the same information reflected on the Batch production record Inquiry. On the General tab of the report, the user will have the ability to include more information for both the produced items and/or the raw material item. For the produced items, the user can choose to include the Quality order information as well as the Batch attribute value information on the report. For the raw material items, the user can choose to include the Quality order information, the Batch attribute value information as well as the Vendor batch details information on the report.

| **Path: Production control \> Reports \> Electronic batch records \> Batch production record** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Field** | &nbsp; | &nbsp; |
| Batch production record | Select the Batch production record ID for a corresponding Batch or Production order |  |
| Quality orders (Produced items) | Select to include the Quality orders for the produced items |  |
| Batch attribute values (Produced items) | Select to include the Batch attribute values for the batches of the produced items |  |
| Quality orders (Ingredients) | Select to include the Quality orders for the raw material items |  |
| Batch attribute values (Ingredients) | Select to include the Batch attribute values for the batches of the raw material items |  |
| Vendor batch details (Ingredients) | Select to include the Vendor batch details for the batches of the raw material items |  |

## Instrument Calibration

Certain test instruments that are used during quality control processes need to be regularly calibrated. Calibration is the process of evaluating and adjusting the precision and accuracy of measurement equipment and is usually defined as a performance comparison against a standard of known accuracy. Proper calibration of an instrument allows people to have a safe working environment and produces valid data for future reference. Instruments that are not calibrated regularly can result in product which has incorrectly passed or failed quality control tests. This new feature adds capability around tracking individual test instrument tags, supports an on-going calibration process for the instrument tag and tracks usage of given tags against the quality order tests.

The Instrument Calibration feature found within EDGE for AX offers enhanced quality management capability by providing robust functionality around test instrument tracking and calibration. The added functionality will give users the ability to:

- Track additional quality details related to Test instrument tags, such as Calibration groups, Test departments and Test owners.

- Track additional information on the Test instrument tag and support new actions triggered from the Test instrument tag.

- Track Test instrument type and Tag number on the quality order line and automatically assign Tag number if desired. The user can also be notified if the selected tool is not available.

- Define whether or not the Test instrument tag requires calibration and if so, to track additional details about the calibration such as Calibration users, Calibration dates, Calibration tools, Calibration procedure and Calibration history.

- Specify whether or not the Test instrument tag is to be calibrated based on Usage or Periodic schedule.

    - If the calibration takes place based on Usage, then the user can define the usage triggers. A periodic utility will evaluate if the current usage is equal to or greater than the trigger usage count and then mark the instrument for calibration and create a calibration record.

    - If the calibration takes place based on Periodic schedule, then the user can define the frequency of calibrations based on daily, monthly or yearly buckets. A schedule will be generated based on these frequencies and will populate the next calibration date field. A periodic utility will create calibration records for those instruments where the Next calibration date has been met.

- Support calibration reporting such as Calibration Certificate and Calibration Schedule Report.

- Support the ability to print Calibration labels as needed.

### Setting up Instrument Calibration

Parameters drive several components for instrument calibration. The following are the Inventory management parameters found under Quality management used by the Instrument calibration feature. The first three checks are used when processing a quality order that uses a calibrated test instrument. The system can optionally check with an error or a warning if the selected test instrument tag is currently being calibrated, if the maximum usage for the instrument tag has been exceeded and/or if the lifetime maximum usage for the instrument tag has been exceeded. If configured to do so, the system can automatically attempt to assign available test instrument tags to quality order lines when created. If not assigned automatically, they will need to be assigned manual for tests that use test instrument tags. The last four fields for the Test instrument calibration parameters are used as defaults for printing calibration labels. Calibration labels can be printed from a given test instrument tag or a given calibration record. The Calibration label will use a layout that is set as a parameter and defaulted to the test instrument type. The label can be printed to a file or to a ZPL printer. These parameters set up the default values for this data that can be overridden at printing time.

To accommodate the added functionality, the **Test instrument** form has been modified to allow the user to specify if the instrument type requires a Tag. On this standard form, there are three new fields used with instrument calibration. *Tag number required* needs to be selected to trigger additional functionality around tracking test instrument tags.*Used for calibration* indicates that this type of instrument is actually a tool used when calibrating. The*Calibration label layout* identifies what the Calibration label should look like when printed. In order to add tags to the instrument, the user will have to select the *Tag number required* field. To add tags to the instrument, the user can either click the Test instrument tags ribbon action or go to Inventory management \> Setup \> Quality control \> Test instrument tags.

For additional tracking of test instrument tags, **test locations** can optionally be defined and subsequently associated to a test instrument tag. Test locations can be used to identify the location where this test instrument tag is tested.

For additional tracking of test instrument tags, **test departments** can optionally be defined and subsequently associated to a test instrument tag. Test departments can be used to identify the department which is responsible for testing the test instrument tag.

For printing calibration labels, a **calibration label layout** can be defined. Calibration labels would be printed using a ZPL printer and therefore, ZPL code is used to define the layout. The ZPL can use any fields from the test instrument tag or from the calibration record. The default calibration label layout is defined on the Inventory management parameters. This layout will default to all new Test instruments. The layout can be changed on a given test instrument type. When a calibration label is printed, the layout from the associated test instrument type will be used. Calibration labels can be printed directly from a test instrument tag where the information from the most recent calibration will be used or directly from any calibration record.</br>Note: A sample calibration label layout is available by using the Fullscope EDGE for AX setup checklist.

When a given test instrument tag is identified as one that is calibrated, then a calibration group is required on the tag. The calibration group allows you to define how like instruments are calibrated. For example, some test instruments are calibrated annually. Others might be calibrated based on how many times it is used. Others might only be calibrated on a manual, as-needed basis. The calibration group defines these details and is set on a given test instrument tag.

| **Path: Inventory management \> Setup \> Quality control \> Calibration groups** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **General** | &nbsp; | &nbsp; |
| Calibration group | Name of the group, used to group tags together with similar calibration details. | Monthly, Annually, Manually, 1000Usages |
| Calibration method | Select the method that determines when the instrument is calibrated. | Manual - Select this option to manually calibrate the instrument.</br>Usage - Select this option to base calibration on the use of the instrument on Quality tests.</br>Periodic - Select this option to base calibration on a specific time frame. |
| Calibration period | Select the calibration periodic frequency for the instrument.</br>Note: This field will only be active and is required when the Calibration method is Periodic. | Day - Select this option to specify that the frequency specified will be based on days.</br>Month - Select this option to specify that the frequency specified will be based on months.</br>Year - Select this option to specify that the frequency specified will be based on years. |
| Calibration period frequency | The numeric frequency of when the instrument is to be calibrated.</br>Note: This field will only be active and is required when the Calibration method is Periodic. | For example, if Calibration period is Month, than a 3 in this field represents the fact that the instrument tag should be calibrated every 3 months. |
| Calibration usage update method | The usage method to be used when updating current usage of the test instrument based on the usage of the quality order test line.</br>Note: This field is only active and is required when the Calibration method is Usage. | Fixed increment - Select this option to update the usage count by the specified Usage increment each time a Quality order with the Instrument tag is validated.</br>Test quantity - Select this option to update the usage count by the specified test quantity of a Quality order test each time a Quality order with the Instrument tag is validated. |
| Usage increment | The increment by which to increase the usage count of an instrument each time it is used.</br>Note: This field is only active and is required when the Calibration method is Usage and the Calibration usage update method is Fixed increment. | For example, with a usage increment of 2, you can indicate that with every validated quality order, no matter how many units are tested, the usage count should be updated twice. |
| Usage count trigger for calibration | The numeric value used to trigger a calibration for a given instrument. The instrument can still be used until the Maximum usage before calibration is met.</br>Note: This field is only active and is required when the Calibration method is Usage. | For example, if the usage count trigger is 100, then after a given test instrument tag reaches 100 usages, when run, the periodic job to create calibration records will create one for this test instrument tag. |
| Maximum usage before calibration | The maximum number of times the instrument tag should be used before it is calibrated.</br>Note: This field is only active and is required when the Calibration method is Usage. | For example, the usage count trigger could be 100 but the maximum usage before calibration could be 125. This means that calibration could be triggered after 100 but the tag can still be used, until it reaches 125 usages. Inventory management parameter is used to determine if the quality order checks for maximum usage before calibration. |
| Lifetime usage maximum | The maximum time the instrument should be used over its lifetime.</br>Note: This field is only active when the Calibration method is Usage. | For example, the lifetime usage maximum could be 10000, which means even after it has been calibrated, the instrument tag should only be used 10000 times and then it should be marked as out of service. Inventory management parameter is used to determine if the quality order checks for lifetime usage maximum. |

When a given test instrument tag is identified as one that is calibrated, then a **calibration procedure** may be attached to the test instrument tag. The procedure provides details on exactly how the tag should be calibrated. The calibration procedure also can track if an external vendor is involved in the calibration process. This data is stored for informational purposes. Attachments can also be added to the Calibration procedure. If attachments are available, they will be transferred from the procedure to the test instrument tag to associated calibration records.

The main element of this feature revolves around the test instrument tag. A given test instrument type can have many tags, which uniquely defines the instrument. This form supports many details about the test instrument tag. For example, the tag will specify data such as the Manufacturer, Warranty number, Acquisition date and Specifications. The instrument tag can also be designated for Calibration. When calibration is required, a Calibration group defines the method and calibration details regarding the test instrument tag.

| **Path: Inventory management \> Setup \> Quality control \> Test instrument tags** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Main** | &nbsp; | &nbsp; |
| Tag number | The Test instrument tag identification. | Uniquely identifies the specific instrument. |
| Tag description | A brief description of the Test instrument tag. | This field describes the unique tag number of the instrument type. |
| Test instrument type | The Test instrument for which the tag is associated with. | Examples could include Scale, Thermometer, Oximeter, etc. |
| Instrument description | The description of the Test instrument. | The description of the type of instrument. |
| Instrument usage status | The current status of the selected Test instrument tag. | Valid values are Available, Calibration and Out of service. |
| Check if test instrument is being calibrated | The action to take on a quality order when the Instrument usage status of the selected tag is Calibration. Defaults from the Quality management tab of the Inventory and warehouse management parameters to new Test instrument tags but can be changed by test instrument tag. | The available options are:<ul><li>Not allowed - When selected, if the selected tag is being calibrated, it will not be allowed to be used on a Quality order test.</li><li>Warning only - When selected, if the selected tag is being calibrated, it will be allowed to be used on a Quality order test with a warning message.</li><li>No check - When selected, if the selected tag is being calibrated, it will be allowed to be used on a Quality order test.</li></ul> |
| Restricted use | Indicates if the selected test instrument is for restricted use. | Informational purposes only. |
| Used for calibration | Indicates if the selected test instrument is used in a calibration process.</br>Note: Field is not editable; defaults from the Test instrument form. | If used for calibration, then it can be entered as a Calibration tool while calibrating an instrument. |
| **FastTabs** | &nbsp; | &nbsp; |
| General | Contains general information about the tag of the test instrument. |  |
| Calibration details | Contains information specific to the calibration of the test instrument tag. |  |
| Manufacturer data | Contains information specific to the manufacturer of the test instrument tag. |  |
| Test procedures | Contains additional procedural information for the selected test instrument tag. |  |
| Specifications | Contains additional specifics for the selected test instrument tag. |  |
| Notes | Contains additional notes applicable to the selected test instrument tag. |  |
| **General FastTab** | &nbsp; | &nbsp; |
| Serial number | The serial number of the test instrument tag manufacturer. |  |
| Owner | The owner of the test instrument tag. |  |
| Acquisition date | The date on which the test instrument tag was acquired. |  |
| Fixed asset number | Unique key for identification of fixed assets; used if the test instrument tag is tied to a fixed asset number. | Informational purposes only. Could be used with reporting if desired. |
| Customer account | The customer account that this test instrument tag is related to. | The specific test instrument tag can belong to and/or be assigned to a specific customer. |
| Vendor account | The vendor account that this test instrument tag is related to. | The specific test instrument tag can belong to and/or be assigned to a specific vendor. |
| Test area | The test area that the test instrument is associated with. | This field is a standard AX field that is being reused on this form based on standard logic. |
| Test department | The department that is responsible for the test instrument. | A new setup table created for this feature. |
| Test location | The location for the specific test instrument. | A new setup table created for this feature. |
| Unit | The Unit of measure associated with the values recorded from this test instrument. | Defined on the test instrument type. |
| Precision | The precision of a measurement (value describes the number of digits that are used to express that value) that can be used when recording results from this test instrument. | Defined on the test instrument type. |
| **Calibration details FastTab** | &nbsp; | &nbsp; |
| Calibration required | Indicates if calibration is required for the test instrument. | If not selected, then the entire FastTab is not editable. |
| Calibration procedure name | The name of the procedure used for calibration of the test instrument. |  |
| External calibrating vendor | The account number of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form. |
| External vendor name | The name of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| Calibration start date | The date that calibration calculations should be driven from for the first calibration. | For example, if the Calibration method is periodic and performed every 3 months, this date represents the 3 months from what date. This date should default to the current date for a new record and can be changed up until the point that a calibration is performed on the instrument. |
| Usage count since last calibration | The number of times this instrument has been used since its last calibration. This field applies only when the Calibration method is Usage and is used to determine when the next calibration is due. | When the instrument is calibrated/ approved, this value shall be reset to zero. |
| Lifetime usage count | Represents the number of times the instrument tag has been used over its lifetime; used to determine when lifetime usage is reached. | If the associated Calibration method is Usage, then this field is populated by the system but can be overridden by the Override usage data Functions ribbon action. If the associated Calibration method is Manual or Periodic, then this field will not be populated by the system but can still be changed by using the Override usage data Functions ribbon action. |
| Calibration group | The method in which the test instrument is calibrated. Defaults in all the details related to how this test instrument tag should be calibrated. This field is mandatory when calibration is required. | Depending on the Calibration group selected, the corresponding Calibration group details will be displayed. For example, if a group with a method of Usage is selected then the Calibration group details will appear displaying the setup of the usage information |
| Completion assignee | The user who is generally assigned to complete the calibration of this instrument. |  |
| Approval assignee | The user who is generally assigned to approve the calibration of this instrument. |  |
| Started date | The date when the most recent instrument calibration was started. | These date fields represent a set of dates based on the last closed calibration. They are updated by the calibration process when the associated test instrument tag has a calibration that is closed. |
| Completion date | The date when the most recent instrument calibration was completed. |  |
| Calibration result | The result of the most recent instrument calibration. |  |
| Approval date | The date when the most recent instrument calibration was approved. |  |
| Next calibration date | The date when the next instrument calibration is scheduled.</br>Note: This field applies only when the Calibration Method is Periodic or Manual. For manual calibration method, then this field is editable. For periodic calibration method, this field is automatically calculated using the Calibration approved date, Calibration period and Calibration period frequency. | For example:</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Day(s), the Calibration Period Frequency is 10 then the Next Calibration Date will calculate to be 1/11/2013.</br>OR</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Month(s), the Calibration Period Frequency is 3 then the Next Calibration Date will calculate to be 4/1/2013.</br>OR</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Year(s), the Calibration Period Frequency is 1 then the Next Calibration Date will calculate to be 1/1/2014. |
| Date calibration certificate printed | The date when the Instrument calibration certificate was last printed. |  |
| **Manufacturer data FastTab** | &nbsp; | &nbsp; |
| Manufacturer | The name of the test instrument tag manufacturer. | Manufacturer data is all for informational purposes only. |
| Manufacturer part number | The manufacturer part number of the test instrument tag. |  |
| Model number | The model number of the test instrument tag. |  |
| Manufacture date | The date when the test instrument tag was manufactured. |  |
| Warranty number | The warranty number of the test instrument tag. |  |
| Warranty expiry | The date of the expiry of the warranty on the test instrument tag. |  |
| **Test procedures FastTab** | &nbsp; | &nbsp; |
| Test procedures | Used to add any additional test procedures to support the Calibration procedures. |  |
| **Specifications FastTab** | &nbsp; | &nbsp; |
| Specifications | Used to add any specifications to the test instrument. |  |
| **Notes FastTab** | &nbsp; | &nbsp; |
| Notes | Used to add any notes applicable to the test Instrument. | Specific instructions on use or other such comments could be entered here. |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a new Test instrument tag. |  |
| Delete | Delete a Test instrument tag. | You cannot delete a test instrument tag if it used on any quality orders in the system or if any calibrations have been done on it. |
| Functions | Use the Function options to modify the calibration information of the selected instrument tag:</br>Select Calibrate instrument to calibrate the selected test instrument tag.</br>Select Reschedule calibration to change/update the date of the next calibration of the selected instrument tag.</br>Select Override usage data to change/update the values in the Usage count since last calibration and Lifetime usage count fields of the selected instrument tag. |  |
| Inquiry | Select to see the calibration history of the selected instrument tag. |  |
| Update usage status | Use this option to update the status of the selected instrument tag:</br>Select Out of service to remove the instrument tag from commission. The instrument will have to be calibrated before it can become available.</br>Select Available to make the instrument active. This status may indicate that the instrument was recently calibrated. |  |
| Print | Select to print either a Calibration label or Calibration certificate. |  |
| Attachments | Select to add/view/modify documents attached to the selected instrument tag. |  |

### Using Instrument calibration process

To automatically create a record of the calibration of a test instrument, there is a batch job called Create calibration record that is available for the user to execute as needed. The user will have the ability to run the job based on a specific Approval date, Calibration method, Tag number or several other options.

Additionally, calibration records can be created manually from the Test instrument tag or from the Calibration test instrument list page directly.

On the Calibrate test instrument list page, the user will be able to Start, Complete and Approve the calibration of a test instrument. As the test instrument tag is being calibrated, the calibration record can be updated with all of the resulting details. When completing a calibration, there are three available result possibilities: Pass, Limited pass (the instrument can still be used but within a limited scope) or Fail. For failed calibrations, the user has the option to make the instrument out of service or leave it as being calibrated. For passed calibrations, the calibration record needs to be approved. E-signature can optionally be set up for the approval of the calibration record.

A completed or approved calibration can be reopened at any point and there will be a history of all reopened calibrations.

To create calibration records in batch, the **Create calibration record** job can be utilized. The job has many options available to base the calibration record creation on such as by calibration method, next calibration date, and test instrument type or usage status. For example, the following shows a situation where we want the system to create calibration records for all test instrument tags that have a test instrument type of Scale and the next calibration date is before January 6, 2015. This option is accessible via the menu path: Inventory management \> Periodic \> Quality management \> Create calibration records.

Additionally, instrument calibration records can be created manually from the Instrument **calibration list page** by using the New Calibrate instrument ribbon action. This list page also shows all calibration records already created and supports a filter that can show All, Open or Closed calibration records. The Calibrate instrument list page shows the test instrument type, tag number, who started the calibration and when, who completed the calibration and when and who approved the calibration and when. It also shows the Calibration result which will be either Open, Pass, Limited pass or Fail.

The **Test instrument calibration record detail** form allows recording of all activity to calibrate the specific test instrument tag. Use this form to set up and maintain the calibration of test instrument tags when using the Test instrument calibration functionality.

| **Path: Inventory management \> Periodic \> Quality management \> Calibrate test instruments (Detail form)** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **FastTabs** | &nbsp; | &nbsp; |
| General | Contains general information about the Test instrument/tag for which the calibration record is created. |  |
| Test procedures | Contains additional procedural information for calibrating the Test instrument/tag for which the calibration record is created. |  |
| Specifications | Contains additional specifics for calibrating the Test instrument/tag for which the calibration record is created. |  |
| Notes | Contains additional notes for calibrating the Test instrument/tag for which the calibration record is created. |  |
| **General FastTab** | &nbsp; | &nbsp; |
| Test instrument type | The Test instrument that is being calibrated. |  |
| Description | The description of the Test instrument. |  |
| Tag number | The tag number of the Test instrument being calibrated. |  |
| Description | The description of the Test instrument tag. |  |
| Instrument usage status | Indicates the current status of the Test instrument tag. | From this form, it is a display field and will display as Available, Calibration or Out of Service. |
| Calibration procedure name | The calibration procedure used on the selected calibration record. | This will default from the test instrument tag but can be changed on the calibration record. |
| Description | The description of the calibration procedure. |  |
| External calibrating vendor | The account number of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| External vendor name | The name of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| Calibration procedure | The procedures as specified on the Calibration procedure form. | Field is not editable; defaults from the Calibration procedures form |
| Started by | The user that started the calibration. | This field is updated by the Start calibration action. |
| Started date | The date the calibration was started. | This field is updated by the Start calibration action. |
| Completion assignee | The user responsible for assigning the user that will complete the calibration. | This field defaults from the test instrument tag but can be modified. |
| Completion by | The user that completed the calibration. | This field is updated by the Complete calibration action. |
| Completion date | The date the calibration was completed. | This field is updated by the Complete calibration action. |
| Calibration result | The result of the calibration of the test instrument. | This field is updated by the Complete calibration action. Valid options for this field are Open, Pass, Limited pass and Fail. |
| Approval assignee | The user responsible for assigning the user that will approve the calibration. | This field defaults from the test instrument tag but can be modified. |
| Approval by | The user that approved the calibration. | This field is updated by the Approve calibration action. |
| Approval date | The date the calibration was approved. | This field is updated by the Approve calibration action. |
| **Test procedures FastTab** | &nbsp; | &nbsp; |
| Test procedures | Used to add any additional test procedures to support the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Specifications FastTab** | &nbsp; | &nbsp; |
| Specifications | Used to add any specifications for the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Notes FastTab** | &nbsp; | &nbsp; |
| Notes | Used to add any notes applicable to the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Buttons** | &nbsp; | &nbsp; |
| New – Calibrate instrument | Create a new calibration record. | Can only create one open calibration record at a time for a given test instrument tag. |
| New – CAPA Case | Create a new CAPA case for the selected calibration record. | Automatically creates associations on the CAPA case to the test instrument tag and the calibration record. |
| Maintain – Edit | Edit the selected calibration record. | Cannot be edited once it is approved unless it is reopened. |
| Maintain – Delete | Delete the selected calibration record. |  |
| Functions - Assign calibration tools | Select to add instruments that are used in the calibration process of the test instrument for which the calibration record is created. | In order for the tool to be available to assign to a calibration record, it must be marked as Use for calibration. If it requires tags, then tags will also need to be specified. |
| Functions – Start calibration | Select to start the calibration of the test instrument for which the calibration record is created. | Updates the Started by and Started Date fields on the calibration record. |
| Functions – Complete calibration | Select to complete the calibration of the test instrument for which the calibration record is created. | Updates the Completed by and Completed Date fields on the calibration record. |
| Functions – Approve calibration | Select to approve the calibration of the test instrument for which the calibration record is created. | Updates the Approved by and Approved Date fields on the calibration record. |
| Functions – Reopen calibration | Select to reopen a completed or approved calibration record. | Clears out completed and approved fields and writes a reopen calibration history record. |
| Inquiry – Calibration reopen history log | Select to view a history of the calibration records reopened of the test instrument for which the calibration record is created. |  |
| Print – Calibration label | Select to print the calibration label for the selected calibration record. | The Calibration record has to either be completed or approved in order to print a Calibration label. |
| Print – Calibration certificate | Select to print the calibration certificate for the selected calibration record. | The Calibration record has to either be completed or approved in order to print a Calibration certificate |
| Attachments | Select to add/view/modify documents attached to the selected calibration record. |  |

### Using Instrument Calibration Tags on a Quality order

The specification of a test instrument on a Quality order line has been expanded to include the selection of a test instrument tag. When a test instrument that is selected for use on a Quality order requires a tag, the Quality order cannot be validated without the selection of a tag on the quality order result line.

There is an added field in the Inventory and warehouse management parameters called Automatically assign test instrument tag number on quality order line that when selected, will sort through the tags for the instrument and select the best available tag for the quality test. If this parameter is not selected, the user will have to manually select a tag on the Quality order line or the Quality order results line when the quality order is updated.

If a tag has an Instrument usage status of Out of service then it will not be available for selection. If the tag has an Instrument usage status of Calibration, depending on the specific of the tag, it may or may not be available for selection on the Quality test. Additionally, depending on parameter validations, the system might also optionally either warn or send an error to the user, if the chosen test instrument tag has exceeded its maximum usage and/or its lifetime usage. Also, if the chosen test instrument tag is currently being used on an open quality order, a warning message will also be provided to the user.

Once validated, if the chosen test instrument tag is calibrated based on Usage then the usage counts on the test instrument tag are updated based on the quality order. The current usage count and the lifetime usage count will be incremented by either the test quantity or the usage increment depending on the details of the calibration group on the test instrument tag.

### Printing Calibration Reports

There are three calibration related reports provided:

- Test Instrument Calibration Certificates

- Test Instrument Calibration Labels

- Test Instrument Calibration Schedule

Calibration certificates can also be generated in mass directly from the menu path: Inventory management \> Reports \> Quality management \> Test instrument calibration certificates. The Calibration certificates and the Calibration labels can both be printed from a test instrument tag or from a specific calibration record. If printed from the test instrument tag, they include details from the last closed calibration. If printed from a specific calibration record, it will print details from that specific calibration.

Once generated, it can be saved to a file or printed directly to a printer of your choosing. Here is an example of a Calibration certificate:

Test instrument calibration labels assume the use of a label printer. The calibration label layout uses ZPL code to generate the label. When printing a Calibration label, it generates ZPL code that can be immediately recognized and printed by a ZPL Printer in a specified layout or a ZPL reader can be used to view it. When choosing the ribbon action to Print Calibration label, the default destination will come from the Inventory parameters but can be modified at printing time and it supports the option to print the code to a file or to send it directly to a ZPL printer for immediate printing. This layout can be defined using the Calibration label layout setup and can support different layouts for different test instrument types.

Test instrument Calibration schedule report can be printed directly from the menu path: Inventory management \> Reports \> Quality management \> Test instrument calibration schedule. The print destination supports the option to print the report to the screen or directly to a printer of your choice. This report is designed to provide a list of test instruments that need to be calibrated. However, the selection criteria provided supports many options such as by Owner or Calibration method. By using the Show all due today option, it will create a list of test instrument tags where the Next calibration due date is before today.

## Quality Associations for Returns and Transfers

Quality associations establish the criteria for what events should trigger the automatic creation of Quality orders to test product quality. For this feature, we have added two triggers: Sales returns and Transfer orders.

### Setting up Quality associations for Returns and Transfers

Quality associations drive automatic creation of quality orders. Standard AX supports the following Reference Types: Sales, Purchase, Production, Co-Product Production, Route operation, Quarantine. This feature adds the ability to create a Quality association for a Reference type of Sales Return and Transfer.

All existing functionality provided by the Quality association feature is supported from these two new types. For example, subsequent processing can be blocked until the created quality order is validated.

For the Reference type of Sales return, the Document type option of Packing slip will trigger the creation of the quality order. Blocking subsequent processing of the packing slip or invoice is available. For Sales returns, the quality order can be triggered based on Customer, Customer group, or All Customers and based on Item, Item group or All Items.

For the Reference type of Transfer, the Document type option of Picking list, Ship transfer order or Receive could trigger the creation of the quality order. Blocking subsequent processing of the Picking list, shipping the transfer order or receiving the transfer order are all available options. For Transfer orders, the quality order can be triggered based on Item, Item group or All Items.

Here we demonstrate an example of setting up a quality association that indicates that a Quality order should be automatically triggered for a **Sales return** after the Packing slip process is posted for Item: RM1. The quality association tells the system what test group and item sampling should be used on the quality order. Additionally, this example indicates that subsequent invoicing of that sales return should be blocked until the quality order is validated.

Here we demonstrate an example of setting up a quality association that indicates that a Quality order should be automatically triggered for a **Transfer** before the Ship transfer order process is completed Item: RM1. The quality association tells the system what test group and item sampling should be used on the quality order. Additionally, this example indicates that receiving that transfer should be blocked until the quality order is validated.

### Inquiring on Quality related topics from Sales Returns and Transfers

This feature also added inquiries from the sales return and the transfer so that the user has easy visibility into the associated quality orders. For example, the above Quality association generated this quality order when the Ship transfer order process was attempted to be posted from the Transfer order. From the transfer order, access from Inquiries directly to the related quality order now available. The same visibility is provided from a sales return.

## Customer specific Certificate of Analysis

A Certificate of Analysis (COA) is a document provided to customers who require documentation of items they purchase. The COA describes specific tests performed to confirm the quality of a given item lot. It should list tests performed, the tolerance/outcome allowed for each test, results of the tests on a sample of that item lot, and lot expiration date.

Standard Dynamics AX provides the ability to create a basic Certificate of Analysis from the quality order or from the menu directly after selecting a quality order. On the Test group, there is a flag on the test to indicate whether that test should be included on the COA. There is currently no ability to vary the content of the COA by customer and there is no ability to automatically create/print a COA at sales order packing slip posting time.

The Customer specific Certificate of analysis feature in the EDGE for AX functionality will address some of the gaps in the current COA feature. The new feature has the following main components:

- A way to group customers for COA-related purposes and set up COA customer requirements on Test groups and Quality orders.

- Setup and support application of COA Customer requirements by Customer/Group/All:

    - Include/Exclude by test

    - Use Customer-specific min/max ranges

    - Suppress min/max values

    - Replace actual pass/fail test results with standard verbiage

- Optionally, print independent batch attributes and their values

- Setup and support application of COA Customer requirements by Customer/Group/All for:

    - From Quality order manually

    - From Sales order packing slip post automatically

    - From Inventory batch manually

    - From Inventory management menu directly

- Visibility to additional details on the COA Report

### Setting up and maintaining Customer COA requirements

Customers can be grouped for COA purposes by assigning the customer to a COA Customer group. COA customer groups can be created from this menu path: Inventory management \> Setup \> Certificate of analysis \> COA Customer group. Customers can be added to a given group from this form or from the customer directly.

On a given test group, by quality test, customer COA requirements can be defined for all customers, a COA customer group or specific customers. When setting up these requirements, the user can specify whether given tests can be excluded from the COA, if minimum and maximum values should be suppressed, if customer specific batch attribute ranges should be printed instead of standard ranges and / or if actual test results, pass or fail, should be replaced with standard verbiage instead of actual results.

Once the customer COA requirements are established on the test group, the requirements will default to all quality orders that use that test group but the requirements can be modified on the quality order directly. In the example below, if the COA was printed for Customer US-002, T1 would not be included. For all customers in COA-CG1, when the COA was generated for one of them, this test would be included, customer specific batch attribute range would be used, if available, instead of the standard range and if the test passed, the actual result would be replaced with the verbiage: Within spec.

| **Path: Inventory management \> Setup \> Quality control \> Test groups \> Line \> Customer COA requirements OR Path: Inventory management \> Periodic \> Quality management \> Quality orders \> Line \> Customer COA requirements** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| Test group | The name of the test group. |  |
| Test | The name of the test | There can be multiple tests on a given test group or quality order. The Customer COA requirements can be different by test. |
| Attribute | The name of the batch attribute associated with the test. | If no batch attribute is provided, then the ribbon actions related to batch attributes will be disabled. |
| Customer code | Customer specific COA requirements can be entered for all customers, a COA customer group or a specific customer. | Valid values are Table, Group, All. |
| Customer relation | Select either a specific COA customer group or a specific customer. Options will be based on the selection of the Customer code field. | If All is selected as the Customer code, then no value is entered in this field. If Group is selected as the Customer code, then valid values would be any COA customer group. IF Customer is selected as the Customer code, then valid values would be any customer. |
| Exclude | Indicates if the test should appear on customer's COA. | Generally speaking, all tests are assumed to be included except those specifically marked here as excluded. |
| Use customer specific batch attribute ranges | Indicates whether the customer specific batch attribute range should be used for the customer's COA. | If no customer specific batch attribute range if found, then the standard range will print. |
| Suppress Min/Max values | Indicates if the Minimum and Maximum values of the Test should be suppressed on the customer's COA. | For example, for a given test, let's assume that the Minimum is 1 and the Maximum is 10 and the Result is 1. For certain customers, it might be desirable that the Range does not display at all so not to draw attention to the fact that the result just passed the quality test. |
| Replace pass results | When populated, the verbiage will replace the test results on the customer's COA if the test is passed. | Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as "Within specifications" for a pass. |
| Replace fail results | When populated, the verbiage will replace the test results on the customer's COA if the test is failed. | Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as "Outside acceptable range" for a failure. |
| **Buttons** | &nbsp; | &nbsp; |
| New | Add a new requirement line. | When creating new COA requirements, remember that the most specific reference found for a given test will be used. For example, if I have a record for a specific customer and one for ALL and the COA is being generated for the specific customer; those requirements will be used on the report. |
| Delete | Delete the selected requirement line. |  |
| Batch attributes – Product specific | Open the product specific batch attribute form for the batch attribute on the Test group test. | Note: If accessed from the Quality order form, will have the option to view the Product specific or Product/Customer specific batch attribute. If accessed from the Test group, since a customer is not known, only the Product specific batch attribute will be accessible. These are inquiries only. |
| Batch attributes – Customer specific | Open the product and customer specific batch attribute form for the batch attribute on the Test group test. |  |

### Using Customer COA requirements

The customer COA requirements will be utilized whenever a customer specific COA is generated. A customer specific COA can be generated from the Inventory management menu, a Quality order, an Inventory batch, or automatically from the Sales order Packing slip process. From the menu, a specific quality order, or a specific Inventory batch, the customer specific COA will be triggered by the user choosing a customer account for the COA. Once a customer account is selected and the print option is chosen, the system will automatically look at the customer COA requirements for the specific customer selected and the details of the COA will be adjusted based on the specific requirements for that customer. Standard print destination options are available such as printing the COA to the screen, printer, file or email. If the standard COA is desired, then no customer account should be selected. This will trigger the system to generate the standard COA and the Customer COA requirements will not be utilized. When generating COA's from the Packing slip posting process, only customer specific COA's are generated for all item/batch combinations on the sales orders that have quality orders identified. The default print destination from this process is defined on the Inventory management parameters under Print Management for Customer specific COA's. The chart below identifies multiple ways to access the COA.

| **<u>Options</u>** | **<u>Menu path</u>** | **<u>Helpful hints</u>** |
|-------------------------|-------------------------|-------------------------|
| Menu directly | Inventory management \> Inquiries \> Quality management \> Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Must select a quality order in both cases. |
| Quality order | Inventory management \> Periodic \> Quality management \> Quality order</br>Ribbon: Inquiries \> Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Since access is from a quality order, the Quality order is assumed in both cases. |
| Inventory batch | Inventory management \> Inquiries\> Dimensions \> Batches</br>Ribbon: Inquiries \> Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Since access is from an inventory batch, the Certificate of analysis Quality order (found on the General tab) on the Inventory Batch is used in both cases to generate the COA. If the Certificate of analysis quality order needs to be updated, the ribbon action "Reset COA Quality order" can be used to change the quality order that drives the details of the COA.</br>Note: This option, including generating the standard COA from here, is new functionality only available with EDGE for AX. |
| Sales order packing slip post process | <u>For individual sales order:</u></br>Sales and marketing \> Common \> Sales orders \> All sales orders</br>Ribbon: Pick and pack \> Generate \> Packing slip</br><u>For multiple sales orders:</u></br>Sales and marketing \> Periodic \> Sales update \> Packing slip</br>(Add new orders to the list, select the checkbox to Print customer specific Certificate of analysis.) | Only customer specific COA's are printed from this process. Based on the customer placing the order, the system will print a customer specific COA for every item/batch combination on the order that has a Certificate of analysis Quality order specified on the Batch. No COA will be printed for items not batch-controlled or for items where the batch does not have a Quality order specified.</br>Note: The option to Print Customer specific COA is initially defaulted from the Accounts Receivable parameters from the Updates tab. This parameter will default to new customers. The checkbox on the Packing slip process form will default from the customer if processing for a single order. If processing for multiple orders, this checkbox will need to be selected if printing customer specific COA's are desired. |

### Printing Customer specific COA

The example below demonstrates how to access the Certificate of analysis form from a specific quality order. In this example, we have requested a customer specific COA for Customer US-027.

Customer specific COA's can be adjusted based on the customer and will include more information than what is included on the standard COA. The customer COA requirements for the specific customer will drive details such as whether or not a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results should be replaced with standard verbiage. In addition, customer specific COA's provide a specific customer section on the report which includes Customer name, description, and contact information. Product and Tracking dimensions will also be included as well as batch dates such as Batch expiration date and Best Before Batch Date. Optionally, customer specific COA's can include independent batch attributes and their values. These are batch attributes associated to the batch that were not specifically tested on the quality order in question but are still important details about the quality of the product. There is a parameter on the Batch attribute (Include on COA independent of quality order) that will default to the Batch attribute by product if the batch attribute should be included in the Independent batch attribute section of the COA if not specifically tested on the quality order. If the Customer specific COA was generated automatically from the Sales Order Packing slip process, the Sales order number and packing slip date will also display on the report. Here is an example of the Customer specific COA requested from a quality order for Customer US-027. Notice that the Customer COA requirements were used. For example, for Test T1, the actual test result was suppressed and replaced with the standard verbiage: Within spec. Also notice the Customer details section and the Independent batch attribute section. These are only available on customer specific COA's.

## Production Dispensing

Three basic principles drive the design of Production dispensing – unidirectional flow of materials and personnel, segregation of hazardous and non-hazardous materials, separation of storage and manufacturing items and spaces. In the past, convenience dictated the placement of dispensing areas, traditionally located right near warehouses where the materials were stored. Today, the dispensing area is viewed as the entry point to manufacturing and the transition point for materials coming from the warehouse and entering process areas, so specific criteria will determine the best location. Some materials can be weighed into intermediate bulk containers, such as corn starch or lactose used as fillers and binders for the formation of tablets and the filling of capsules. Some materials need to be transferred to production in its original container and may need to be dedicated until dispensing has been completed.

### Setting up Production Dispensing

In order to activate Production Dispensing you have to select the feature for the desired company or site. For that company or site, you can also configure a parameter to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list. The final selection allows the identification of a folder/directory on the server for the placement of ASCII files from weight scales.

In the Journals tab of the Production Control parameters, you need to select a default journal for the Dispensing ticket. When Production Dispensing is activated, the pick list will be split into two pick lists – one for dispensed items and one for non-dispensed items.

If there are Electronic Signature requirements, you can select to have the electronic signature captured at various points in the process. Specifically for Production Dispensing, there is a new requirement than can be selected that captures the digital signature of the user that posts dispensing ticket production journals.

You select the item on the Released Product form that you desire to handle with production dispensing. Under the Manage Inventory FastTab, you select the 'Dispensing control' option. If the product should only be dispensed by authorized personnel (as opposed to any user) then you select the 'Authorized personnel' option. You can also select default tolerances for dispensing with the Overdispense and Underdispense fields. These defaults will be populated on the formula lines when the product is included as an ingredient in the formula.

You can refine the tolerances on the Setup tab for the selected dispensed ingredient. You can also configure the ingredient to allow or not allow over-dispensing or over-picking with a reverse pick list.

You can select a user and configure that user as an authorized user by selecting the 'Authorized for production dispensing' option. If you are not authorized and the item on the dispensing ticket is configured for authorized personnel only then you will be notified that you must be authorized to post that dispensing ticket.

With Production Dispensing you now have the opportunity to generate picking lists and dispensing tickets when you release batch or production orders. You will also designate the default dispensing ticket journal that will be used. You notice that the 'Post picking list now' has been disabled so that the dispensing activity can be performed.

If the Picking list is created at Release, the user will still have to go through the Start process on the batch or production orders. Upon Starting the order, the user will have to select the Dispensing ticket journal name and select 'Never' as the Automatic BOM consumption; if not, the Picking journal will be created again.

### Using Production Dispensing

There are 3 modes of issuing materials that are supported by Production Dispensing. The first mode, the proposed quantity of the material is dispensed from the raw material warehouse. This proposed quantity is then added to the manufacturing batch for production.

The second mode, a planned transfer order is automatically generated when there is insufficient quantity of the material in the dispensing warehouse. The proposed amount is dispensed from the container in the dispensing warehouse and then added to the manufacturing batch for production. The remainder of the material in the dispensing warehouse is retained there for other batch or production orders.

The third mode, an amount is picked from the raw material warehouse and entered as the Consumption or picked amount. An amount within the tolerance of the proposed quantity is dispensed and then added to the manufacturing batch for production. The remainder (Dispensed quantity minus the Consumption quantity) is then returned to the raw material warehouse using an automatically generated reverse pick list (dispensing ticket).

Once you have released or started the batch or production order the ingredients will be added to pick lists. If the ingredient is configured as a dispensed item then it will appear on a dispensing ticket and non-dispensed items will appear of a normal pick list. Once the batch or production order is released/started the user can tell whether there are open pick lists or dispensing tickets by viewing that information on the Production Order List Page.

On the View tab for the Production order list Page there are separate action buttons for the Picking list and Dispensing ticket. Use the Picking list to interact with non-dispensed ingredients and then post the journal. Use the Dispensing ticket to interact with dispensed ingredients.

When the dispensing ticket is selected, the warehouse worker can select 'Lines' and enter the quantity of material that is being picked for the batch or production order. If so configured, the warehouse worker may pick an entire container of material (e.g. 400 lb. in the example below) for the order and then allow the machine operator to dispense from that container. Once that is completed the remainder would be returned.

The machine operator would now select the Dispensing option on the Dispensing Ticket journal to display the Dispensing Ticket form. |     |

The Dispensing Ticket production journal lines form contains a grid in the upper portion of the form that lists the dispensed ingredients. When selected, the grid in the lower portion of the form allows for entry of one or more dispensed weights that can be averaged and posted. Once the weights are entered, the procedure would be to click the 'Post dispensed' button, the Confirm menu button, optionally the Validate menu button, and finally the Post menu button.

| **Path: Production control \> Common \> All production orders \> Dispensing ticket \> Dispensing** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Overview - Upper** | &nbsp; | &nbsp; |
| Dispensed item | The dispensed item from the dispensing ticket picking list | Select the dispensed item for which to enter dispensed weights |
| Proposal | The amount, in the BOM unit, that is expected to be consumed, based on the estimated production orders. The field displays a value only if you specified that the material consumption of the production must be entered manually for the item. |  |
| Consumption | Feedback about the actual consumption, in the BOM unit. |  |
| Dispensed | The amount that is being issued for production. | This will be the resultant value after you post the dispensed weight(s). |
| **Tabs** | &nbsp; | &nbsp; |
| Overview | View or enter the posting date for physical item picking, the production number, and the lot ID. The remaining fields provide an overview of the status of the lines in the picking list journal. This overview includes the item number that is used for production, the configuration, the warehouse where the item is stored, the proposal, and the unit. The overview can also indicate whether the item is finished. |  |
| General | View or enter general identifying information. This information includes the journal number, bill of material (BOM), inventory quantity, and information about scrap and end reporting for the selected journal line. |  |
| Reference | View related inventory references and BOM information for the selected journal line. |  |
| Financial dimensions | View information about financial dimensions, such as the default dimensions and where the dimensions are used in account structures and advanced rule structures. |  |
| Inventory dimensions | View the inventory dimensions for the selected journal line. |  |
| **Buttons** | &nbsp; | &nbsp; |
| Confirm | Check the dispensed – net amount for the journal line. Also updates the journal line "Dispensed" field with the posted dispensed quantity on the form. |  |
| Validate | Check the journal for required information before you post it. |  |
| Post | Check for errors, and then post the journal. |  |
| Inventory | Check inventory information for the journal line. This information includes inventory transactions, the available inventory for the selected item, and reservations. |  |
| Print | Print the information that is on the journal line. |  |
| **Overview - Lower** | &nbsp; | &nbsp; |
| Dispensed – net | Enter the net amount that is being issued to production |  |
| Include in validation | Check to include the weight in the averaging calculation |  |
| Date and time | The current date and time when the weight was entered. |  |
| User ID | The User ID of the individual who is entering the weights. |  |
| Gross | The gross or total amount of weight being considered. |  |
| Tare | The tare or unladen weight being considered. |  |
| Scales | The Test Instrument that is used to identify the specific scale equipment related to the entered weight. |  |
| **Tabs** | &nbsp; | &nbsp; |
| General | View or enter general weight line information. This information includes the gross, tare, and net dispensed reporting for the selected journal line. |  |
| **Buttons** | &nbsp; | &nbsp; |
| Add | Allows additional weight lines to be entered for the journal line. |  |
| Remove | Removes the selected weight line from the journal. |  |
| Net weight from scales | Populates the Dispensed – net weight field from an ASCII text file in the server directory. |  |
| Gross weight from scales | Populates the Gross weight field from an ASCII text file in the server directory. |  |
| Tare weight from scales | Populates the Tare weight field from an ASCII text file in the server directory. |  |
| Post dispensed | Calculates the average weight of the lines marked with 'Include in validation' |  |

If the user had posted the form above, with the Consumption quantity greater than the Proposal quantity and the Dispensed quantity less than the Consumption quantity (and the item is configured to allow over-dispensing with reverse pick list) then the posting will automatically generate an adjustment picking list journal. The user can select the line that indicates the new journal number and then an 'Open the adjustment journal' button will appear.

## Quick Results Entry

Entering test results for all tests included on a Quality order can be cumbersome and time consuming. This feature has drastically enhanced the user interface to enter in test results for a quality order. The new Quick results entry option on the Quality order presents the data for all tests consolidated on one form, with defaulted quantities based on the Quality order quantity and informational details about minimum, maximum and target values for each test on the Quality order.

### Using Quick Result Entry

When entering results for quality order tests, the standard form can be used. This is accessible from the Results ribbon option on the quality order line. Alternatively, the Quick results entry ribbon option can be selected from the quality order header. Additionally, notice a new field on the Quality order line test grid at the bottom for "Test results exist". This field reflects whether test results have already been entered for the appropriate test line. |     |

Notice here the difference between the two forms. On the Left is the standard Results form. It is just for one test and does not include information related to Standard, Minimum and Maximum values for the test. The Result quantity needs to be entered for every row on this form. On the Right is the Quick results entry form. It has consolidated all of the tests on one form plus it includes visibility to the Standard, Minimum and Maximum test ranges for informational purposes. The Result quantity (or the Result CW quantity if the item is a Catch Weight item) is defaulted for you from the quality order quantity. The Test results can quickly be entered down the Test result column for the entire Quality order without ever leaving the form.

The Quick results entry form supports five different ribbon actions. The New and the Delete options allow the Quality order quantity to be separated out and results entered for different quantities. For example, if the quality order quantity is 5, then using the New action, a total of five lines can be entered for that test so that a different test result can be entered for each quantity. The sum of the quantities for each test must still equal the total quantity of the quality order. The Validate ribbon action, performs the required validation for the selected line and determines if the line is a pass or a fail. The Reset test results ribbon action eliminates the test result value for the given line and deselects the checkbox on the test line for Test results exist if no other line for that test has test results entered. The Split ribbon option provides the ability to take the selected line and split it into multiple lines.

There are two Split options provided. The Single line split option will take the selected line and create two lines where the sum of the quantities matches the total quantity on the selected line. For example, if the line quantity was 8 and a Split quantity of 3 is entered, the result will be two lines, one with quantity of 3 and one with a quantity of 5. Different test results can then be entered for both lines.

The second Split option is a Multiple lines split. This can be used to quickly create rows with the same test quantity. The Result quantity per line needs to be entered. The system then will determine the Total number of results lines based on the result quantity per line. For example, if the current line has a quantity of 8 and the Result quantity per line entered is 2, the system will automatically create 4 lines where there was one, each with a quantity of 2. If the number is not even, the system will do as many rows as possible with the residual in the last row. For example, if the current line has a quantity of 8 and the Result quantity per line entered is 3, the system will create 3 result lines, two lines with the quantity of 3 and the 3<sup>rd</sup> line with the residual quantity of 2 for a total quantity of 8. Note: If the item is a CW item, CW quantity fields open up on the split form to enter instead of the standard quantity fields.

| **Path: Inventory management \> Periodic \> Quality management \> Quality orders \> Quick results entry** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Overview/General tabs** | &nbsp; | &nbsp; |
| Sequence number | The sequence number of the test. | Only sequence numbers already on the quality order can be entered here. |
| Test | The identifier of the test. | Only tests already on the quality order can be entered here. |
| Description | The description of the associated test. | Display only field. |
| Result quantity | The quantity that is currently being tested and needs results documented against it. | All rows for a given test must total the quantity of the quality order for each test. |
| Result CW quantity | Same as above, but for a CW item. | Only enterable if the item on the Quality order is a CW item. |
| Standard | Target value for the test. | Coming from the test group originally but can be changed on the quality order line. On this form it is a display only field, provided for informational purposes. |
| Min | Minimum value for the test. | Coming from the test group originally but can be changed on the quality order line. On this form it is a display only field, provided for informational purposes. |
| Max | Maximum value for the test. | Coming from the test group originally but can be changed on the quality order line. On this form it is a display only field, provided for informational purposes. |
| Outcome | For qualitative tests, represents the outcome as a pre-defined variable. | Quality tests can be defined as integer, fraction or option. If Option is chosen, then enumerates are set up for possible values and the Outcome is the chosen enumerate for the given test quantity. |
| Test result | For quantitative tests, represents the result value of the test for the entered result quantity. | Quality tests can be defined as integer, fraction or option. This field is enterable and is used to enter the true result for any test that is integer or fraction based. |
| Tag number | Tag number of test instrument used to perform the test. | Used if the test group indicates that a Test instrument where tag numbers are required is used to perform the test. If so, a tag number is required to represent specifically which test instrument tag was used to perform this test. |
| Usage increment | For test instruments that use tags and are calibrated based on usage, represents what the usage count will be incremented by on Quality order validation. | If the test group indicates that test instrument tag is required and that particular test instrument tag is calibrated based on usage, this field represents the number that the usage count will be incremented by. The system attempts to determine a value for this based on the setup of the calibrated test instrument tag but it can be changed on this form. |
| Include in result | Determines whether the test line should be included or excluded. | The default is that it should be included. The system takes all test results to determine the appropriate consolidated test result (i.e. average, minimum) but will only consider those marked as "Include in result". |
| Test result (icon) | Shows whether the given test result line represents a pass or fail test result. | Represented as an icon. A Red X represents a Fail and a Green Checkmark represents a Pass. |
| Quality order | The associated quality order number. | By default, only displayed on the General tab. |
| Line number | System-assigned line number which differentiates the entry of the multiple results for a test. | By default, only displayed on the General tab. |
| Buttons |  |  |
| New | Creates a new row within the Quick results entry form. | Only actionable until the quality order is validated. |
| Delete | Deletes the selected row from the grid. | Only actionable until the quality order is validated. |
| Split | Splits the given row into 2 or more rows depending on how the split is defined. | Only actionable until the quality order is validated. |
| Validate | Check for errors on the given line and determines if the row passes or fails the test. | Only actionable until the quality order is validated. This action is not required. Validation for all rows is performed automatically when the form is closed. |
| Reset test results | Clears the test result value for the given line and deselects the checkbox on the test line for Test results exist if no other line for that test has test results entered. | Only actionable until the quality order is validated. |

## Quality Order Usability Improvements

### Skip Test Option has been Added

It is a common business process to create a test group that has a certain number of tests but when executing that test group within a Quality order, some tests are purposefully skipped. Prior to this feature, the user would need to delete those tests if they did not want to enter in test results. Some businesses would prefer to mark the test as Skipped instead of deleting it so that it can be logged as an audit trail that it was decided to skip it. When a test is skipped, all results data is cleared and becomes uneditable and no validation needs to be done on its associated test result data such as tag numbers and test result values. Also, the skipped test is excluded from Acceptable Quality Level (AQL) calculations. Additionally, a test can be unskipped which basically returns the test back to its original state and test results can be entered as usual.

### Using Skip from Quality Order Test Line

In order to mark a Test as Skipped, you need to select the desired test line(s) and select the Skip ribbon action from the line. If test results have already been entered, the user will receive a warning message. If OK is selected from the warning message, then all results data is removed. The Test result icon, Order line result and Batch attribute values are cleared. The Update inventory batch attribute and Include results checkboxes are both unchecked and the Skip test checkbox is checked. No editing can be done on the test while it is in this Skip state. To Unskip a test that was previously skipped, you merely need to select the line and choose the Skip option again. This will put the line back into its original state. Note: When using the Unskip, it is always wise to confirm all values on the test line are correct before validating the quality order.

### Using Skip from Quick Results Entry

Using the Skip option from Quick Results Entry works the same way with a few minor exceptions. Multi-select is not allowed from Quick Results Entry and if there are multiple rows of result data for the same test, the Skip option collapses them back to their original quantities before updating the data and making the line uneditable.

### Quality Order Priority and Assigned To Tester has been Added

The effort to perform quality order testing can be extensive. Often, the work needs to be prioritized and assigned out to appropriate testing resources. To improve this process, we have added the following fields to the Quality Order Header: "Priority" and "Assigned To". These data elements by default are found on the General tab within the Assignment group box but can be personalized to the grid if sorting and filtering is desired. The Priority field is free-format and can be user defined based on business requirements. For example, a business might choose numbers between 0-100 where 100 are the most important. The Assigned to field needs to be assigned to a valid worker. Both fields are optional. Additionally, we added a Test Outcome Description field and a Result Note to the Quality Order Line Test Results to improve usability.

### Option to Not Validate Test Instrument Tag Assigned to Open Quality Order

Currently, if a Quality order test is set up with a Test Instrument that uses Tags, the system will always check to see if a selected test instrument tag is already on an open quality order. If the selected test instrument tag is found on an open quality order, a warning message is always displayed to the user. Some businesses don't need this validation so we have added a parameter in Inventory Management to indicate that this validation can be skipped. This parameter on Inventory and warehouse management parameters from the Quality management tab will default to all new test instrument tags. This parameter can also be modified on a test instrument tag basis. When validating a quality order, if this flag is selected on a chosen test instrument tag and that tag is currently assigned to an open quality order, then no warning message will be triggered on validation.

| **Path: Inventory management \> Setup \> Inventory and Warehouse Management Parameters** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Quality management tab** | &nbsp; | &nbsp; |
| Skip check for test instrument on open quality order | Select this option if you want the system to skip the validation related to if the selected test instrument tag is already assigned to an open quality order. If selected, that validation is bypassed and no warning message is triggered. If not selected, then the validation is performed and a warning message may be triggered. This value will default from the parameters for new test instrument tags but can be changed on an individual tag. | Selected or deselected. Prior releases, the system functioned as if this flag was never selected. Used as a default to test instrument tags. To skip the validation, this field must be selected on the test instrument tag. |

| **Path: Inventory management \> Setup \> Quality Control \> Test instrument tags** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
|  |  |  |
| Skip check for test instrument on open quality order | Select this option if you want the system to skip the validation related to if the selected test instrument tag is already assigned to an open quality order. If selected, that validation is bypassed and no warning message is triggered. If not selected, then the validation is performed and a warning message may be triggered. This value will default from the parameters for new test instrument tags but can be changed on an individual tag. | Selected or deselected. Prior releases, the system functioned as if this flag was never selected. |

| **Path: Inventory management \> Periodic \> Quality management \> Quality orders and Quick Result Entry** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
|  |  |  |
| Skip test | This is an uneditable field that is updated by the Skip ribbon action. If selected, then the test has been skipped, no test results will be entered and this test line will not go through standard quality order test line validations. | The default value for this field is NOT Selected. |
| Priority | Assign a priority to the Quality order for testing | Is user defined. For example, you might decide that the lower the number, the higher the priority. |
| Assigned to | Use to assign the user responsible for the Quality order testing. | Must be a valid worker. |
| Outcome description | Is the associated description of the chosen Test Outcome. |  |
| Result note | Enter any additional notes for the test results. |  |
