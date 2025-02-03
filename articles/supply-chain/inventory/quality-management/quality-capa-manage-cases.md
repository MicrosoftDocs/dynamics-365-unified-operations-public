---
title: Manage CAPA cases
description: CAPA cases let you record, update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Manage CAPA cases

[!include [banner](../../includes/banner.md)]

After you set up the CAPA components, you can begin creating and working with CAPA cases to record, update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

You can set up, work with, and view CAPA cases from the **My CAPA cases** form, or if your security setup permissions allow, from the **All CAPA cases** form. You can also create new CAPA cases from other list pages and forms in Microsoft Dynamics AX where the need to open a CAPA case might originate, such as Customers, Vendors, Sales orders, Purchase orders, Return orders, and Released products.

## CAPA case list pages

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

## Creating CAPA cases

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

## Working with CAPA cases

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
