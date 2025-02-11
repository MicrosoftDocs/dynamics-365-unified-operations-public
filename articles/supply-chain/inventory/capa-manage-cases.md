---
title: Manage CAPA cases (preview)
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

# Manage CAPA cases (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Use corrective and preventive action (CAPA) cases to record, update, track, follow up on, and close issues that are raised by your customers, vendors, or employees.

## Use the CAPA case workspace to view, open, manage, and analyze your CAPA cases

The CAPA case workspace provides a central location where you can create, view, and manage all CAPA cases in the system.

The workspace provides several different tabs that let you view various lists of cases and activities, including those that are assigned to you, only those that are open, only those that are due in the current week, and more. You can also search for CAPA cases related to a specific customer, vendor, sales order, purchase order, return order, or released product.

From the workspace, you can quickly view details, set the status of a listed case activity, advance to the next process stage of a case, and more.

To open the workspace, go to **Inventory management** \> **Workspaces** \> **CAPA management**.

## View CAPA cases on list pages

To view all CAPA cases related to a selected customer, vendor, sales order, purchase order, return order, or released product, open or select the relevant record and then do one of the following:

- For customers or vendors – On the **General** tab, in the **Accounts** group, select **CAPA case**.
- For sales orders, purchase orders, or return orders – On the **General** tab, in the **CAPA** group, select **View CAPA cases**.
- For released products – On the **General** tab, in the **Maintain CAPA cases** group, select **View CAPA cases**.

To view and work with all CAPA cases in the system, use one of the following navigation paths.

- Go to **Inventory management** \> **Periodic tasks** \> **CAPA management** \> **All CAPA cases**.
- Go to **Common** \> **Common** \> **CAPA management** \> **All CAPA cases**.

To view and work only with the CAPA cases that you are responsible for, use one of the following navigation paths.

- **Inventory management** \> **Periodic tasks** \> **CAPA management** \> **My CAPA cases**
- **Common** \> **Common** \> **CAPA management** \> **My CAPA cases**

## FastTabs on the CAPA case details page

When you open a CAPA case record from the workspace or any list page, the details page provides the following FastTabs. Use the fields and settings on each FastTab to view or edit information about the CAPA case.

- **General** – View or edit general information about the selected CAPA case. Many of these values are set when the case is created, as described earlier in this article.
- **Service level agreement** – <!-- KFM: description needed -->
- **Email notifications** – View, add, and edit people who should be emailed when selected events occur with the current capa case (such as when the case or one of its activities changes status to *Closed*, *Canceled*, or *Reopened*).
- **Case log** – View, add, or edit information about the CAPA case. The system adds log entries automatically when certain events occur, such as when the case is created, when it changes status, or when activities are completed. You can also add log entries manually.
- **Associations** – View or edit information about records that are associated with the CAPA case. Examples of the records that can be associated to a CAPA case include: sales order, item, vendor, batch order. Often, one or more these associations are set automatically based on where the user was when creating the case, but you can add more of them as you work with the case.
- **Knowledge article** – View or edit information about knowledge articles that are associated with the CAPA case.
- **Administration** – View administrative details about the CAPA case, such as the date the case was opened and the user who opened it.
- **Resolution** – View or edit information about how the case was resolved.

## Create a new CAPA case

You can create CAPA cases from many different pages in the system, including pages where you work with records from which CAPA cases might originate, such as customers, vendors, sales orders, purchase orders, return orders, and released products. You can also create them from the **All CAPA cases** and **My CAPA cases** pages.  When you create a CAPA case from a related or originating record, the case is linked to that record automatically.

1. Go to the customer, vendor, sales order, purchase order, return order, or released product record from which the CAPA case originates.
1. Depending on what page you're working on, do one of the following steps. <!-- KFM: there might be more of these (?) -->
    - For customers or vendors – On the **General** tab of the Action Pane, in the **New** group, select **CAPA case**.
    - For sales orders, purchase orders, or return orders – On the **General** tab of the Action Pane, in the **CAPA** group, select **Create CAPA case**.
    - For released products – On the **General** tab of the Action Pane, in the **Maintain CAPA cases** group, select **Create CAPA case**.
    - For nonconformance records – On the Action Pane, select **Functions** \> **Create CAPA case**.
    - From the **All CAPA cases** or **My CAPA cases** page – To create a new, unlinked CAPA case, select **New** \> **CAPA case** on the Action Pane. To create a new CAPA case that is linked to an existing case, select the parent case on the grid and then select **New** \> **Dependent CAPA case** on the Action Pane.
    - From the CAPA management workspace – Select **Create new** \> **CAPA case** from the Action Pane or select the new CAPA case button on the **CAPA case summary** FastTab.

1. Regardless of where you are when you create your new CAPA case, the **New CAPA case** dialog opens. Make the following settings on **General** tab of the dialog:
    - **Name** – Enter or select a person's name from the global address book to associate with the CAPA case. If you started from a customer, vendor, sales order, purchase order, or return order, this is set automatically based on the record that was selected when you created the CAPA case.
    - **Case ID** – The CAPA case identification number. This number is generated by the system.
    - **Status** – Select the status of the CAPA case. The default status is *Opened*, which means it's not being worked on yet. You or the assigned worker should change it to *In process* when work begins on it.
    - **Description** – Enter a short description of the CAPA case. This description is used to identify the case in lists and reports and is shown as the heading of the case when you open it.
    - **Priority** – Select the CAPA case priority.
    - **Parent case** – If you want to associate the case with another case, select the parent case here. This is set automatically if you chose a parent case when creating the current CAPA case.
    - **CAPA category** – Select a category for the CAPA case. The category is used for reporting purposes to analyze trends.
    - **CAPA subcategory** – If the category you selected has subcategories defined for it, then select one here. The subcategory is used for reporting purposes to analyze trends.
    - **Description** – Enter a brief description of the CAPA case.
    - **Priority** – Select the CAPA case priority.
    - **CAPA process** – Select the CAPA process that should be followed to resolve this case. The CAPA process defines a series of stages, which must be completed in order, and activities, which should be completed within each stage before continuing to the next one. The process is used to guide the workers who are assigned to the case through the steps needed to resolve it.

1. If you'd like to add a log entry to the case, open the **Case log** tab and enter the details of the log entry. You can view and add log entries from the details page for a CAPA case.

1. Select **OK** to create the case and open its details.

## Work through a CAPA process

A CAPA process guides workers who are assigned to a case through each of the steps needed to resolve it. The process defines a series of stages that must be completed in order. Each stage can include one or more activities that can be completed in any order (or simultaneously). Some activities might be mandatory. All mandatory activities must be completed before the process can be advanced to the next stage.

The CAPA process automatically assigns a worker or worker group to each stage and activity (according to how the process is configured). The system uses email to notify each responsible worker or worker group when a case, stage, or activity is assigned to them. The email includes links that allow the worker to open the case, stage, or activity directly from the message. Workers can always keep an eye on which cases and activities are assigned to them by going to the **CAPA management** dashboard.

CAPA processes are defined by an administrator or manager and are applied to cases as they are created using the **CAPA process** field for the CAPA record. You can have as many processes defined as your company needs (learn more in [Set up CAPA case components](capa-set-up-case-components.md)).

When a case has a process assigned, the workflow is as follows:

1. Create a new CAPA case and assign a **CAPA process** to it. It initially has a **Status** of *Opened*.
1. Select or open the case (for example, from the **CAPA management** workspace) and then select **Change status** \> **In process** (if you're in the workspace, this command is in the toolbar; if you're on the details page or another page, it's on the **CAPA case** tab of the Action Pane). This setting marks the case as being actively worked on and makes it possible to progress through the various stages of the process.
1. The process starts with the first stage (for example, *Definition*). The system generates each of the activities configured for that stage (for example, there might be a single activity called *Identify the problem*).
1. The system emails the **Employee responsible** contacts for the case, the active stage, and each active activity belonging to that stage.
1. Workers assigned to each activity can now work on their activities, take notes about each activity, and eventually mark them as completed. There are several ways that employees can get to the details page for an activity.
    - Select a link in the email sent to them when the activity was generated.
    - Go to the **CAPA management** workspace and browse activities listed on the various tabs (such as **My open activities**).
    - Go to the **CAPA management** workspace and open any tab that lists CAPA cases (such as **My open cases**). Select a case and then choose **View activities** from the toolbar. All activities for the selected CAPA case that belong to stages that have been started so far are listed here. Select an activity to go to its details page
    - Open the details of a CAPA case. On the Action Pane, open the **CAPA case** tab and select **Case process**. Navigate the process tree, expand a stage, and select an activity (the tree only shows activities for stages that have been started until now). Select the **Activity number** link to view the details for that activity.

1. The worker now works on the activity, enters notes into the details page for the activity, and fills out the form as needed. When the worker is done, they close the activity (mark it as complete). There are several ways to close an activity: <!-- KFM: I don't think we need to document the various fields and FastTabs on this page, so I've removed those details from this draft. Agree? -->
    - From the **CAPA management** workspace, select the activity on any tab where it appears and select **Set as complete** from the toolbar.
    - From the activity details page, open the **Activity** tab on the Action Pane and select **Set as complete**.
    - From the activity details page, open the **Status** FastTab and set **Closed** to *Yes*.

1. After all mandatory activities for the current stage have been closed, an employee with permission to do so can advance the case to the next stage. You can skip a stage if necessary, but once you advance to a stage, you can't go back to a previous one. There are several ways to advance a CAPA case to the next stage in its process:
    - From the **CAPA management** workspace, select the CAPA case on any tab where it appears. Then select **Change stage** from the toolbar and choose the stage you want to advance to.
    - From the CAPA case details page, open the **CAPA case** FastTab, select **Change stage** and choose the stage you want to advance to.

1. The selected new stage now starts. The system generates each of the activities configured for that stage, sends out emails to the responsible employees, and updates the **CAPA management** workspace, just as with the first stage in the process.

1. The process continues until all of the required activities are completed and you're ready to close the case. Often, you'll start by opening the CAPA case details and filling out the fields on the **Resolution** FastTab to document the outcome of the case. Then mark the case as closed. There are several ways to close a CAPA case:
    - From the **CAPA management** workspace, select the CAPA case on any tab where it appears and select **Set as complete** from the toolbar.
    - From a CAPA case list or details page, open the **CAPA Case** tab on the Action Pane and select **Change status** \> **Closed**.

> [!TIP]
> To see a graphical overview of the process hierarchy for the current CAPA case, follow these steps:
>
> 1. Open the details page for the relevant CAPA case.
> 1. On the far-right pane, select the **Related information** button :::image type="icon" source="media/related-information-button.png" border="false"::: to open the **Related information** pane (also called the FactBox pane).
> 1. Expand the **Process tree** FastTab to see the list of stages in the current process.
> 1. From here, you  can expand any stage to see the activities that belong to it, provided that the stage has been started so its activities have been created. You can right-click on an activity to open its details.

<!-- KFM: Maybe add a section about how to print CAPA reports -->

## Analyze CAPA case statistics

<!-- KFM: I modified this section to provide more instructions but describe fewer specific fields. Agree? -->

Supply Chain Management provides graphical displays that let you analyze CAPA case generation and progress. Use these statistics to identify trends, frequent issues, bottlenecks, and areas for improvement in your CAPA processes.

Statistical graphs are provided at two locations: the **CAPA management** workspace and **Trending analysis** page. Both displays are similar, though there are a few minor differences in the data that they show.

### Analyze statistics using the CAPA management workspace

To view statistics on the **CAPA management** workspace, follow these steps:

1. Go to **Inventory management** \> **Workspaces** \> **CAPA management**.
1. Expand the **Statistics** FastTab.
1. Two graphs are shown.
    - Use the **Number of cases** by drop-down list to select the type of statistics you want to view in the left graph.
    - Use the **Trending of cases** by drop-down list to select the time period you want to view in the right graph.
    - Use the buttons at the top of each graph to choose its graphical style (for example, bar chart, line chart, or pie chart).

### Analyze statistics using the Trending analysis page

To view statistics on the **Trending analysis** page, follow these steps:

1. Go to **Inventory management** \> **Inquiries and reports** \> **CAPA management** \> **Trending analysis**.
1. On the **Data** tab, choose the date range and turn on each type of graph you want to see.
1. Switch to the Analytics by category tab to view your selected graphs.
1. Use the buttons at the top of each graph to choose its graphical style (for example, bar chart, line chart, or pie chart).

## Review signatures for a CAPA case

It possible (though optional) to set up the CAPA feature so that it requires an electronic signature from any user that closes, cancels, and/or reopens a CAPA case. To review the signatures applied to any CAPA case, follow these steps:

1. Open or select the CAPA case that you want to review (for example, from the **All CAPA Cases** page).
1. On the Action Pane, open the CAPA case tab and select **Signature review**.
