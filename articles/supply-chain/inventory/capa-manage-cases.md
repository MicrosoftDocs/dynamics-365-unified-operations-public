---
title: Manage CAPA cases
description: Learn how to use corrective and preventive action (CAPA) cases to record, update, track, follow up on, and close issues that your customers, vendors, or employees raise.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSInventCAPAWorkspace, QMSCAPACaseDetail, QMSCAPAAnalytics
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Manage CAPA cases

[!include [banner](../../includes/banner.md)]

Use corrective and preventive action (CAPA) cases to record, update, track, follow up on, and close issues that your customers, vendors, or employees raise.

## Use the CAPA case workspace to view, open, manage, and analyze CAPA cases

The CAPA case workspace provides a central location where you can create, view, and manage all CAPA cases in the system.

The workspace provides several tabs where you can view various lists of cases and activities. Here are some examples:

- Cases and activities that are assigned to you
- Open cases and activities
- Cases and activities that are due during the current week

You can also search for CAPA cases that are related to a specific customer, vendor, sales order, purchase order, return order, or released product.

From the workspace, you can quickly view details, set the status of a listed case or activity, move a case to the next process stage, and more.

To open the workspace, go to **Inventory management** \> **Workspaces** \> **CAPA management**.

## View CAPA cases on list pages

To view all CAPA cases that are related to a selected customer, vendor, sales order, purchase order, return order, or released product, open or select the relevant record, and then follow one of these steps.

- **For customers or vendors:** On the Action Pane, on the **General** tab, in the **Accounts** group, select **CAPA case**.
- **For sales orders, purchase orders, or return orders:** On the Action Pane, on the **General** tab, in the **CAPA** group, select **View CAPA cases**.
- **For released products:** On the Action Pane, on the **General** tab, in the **Maintain CAPA cases** group, select **View CAPA cases**.

To view and work with all CAPA cases in the system, follow one of these steps.

- Go to **Inventory management** \> **Periodic tasks** \> **CAPA management** \> **All CAPA cases**.
- Go to **Common** \> **Common** \> **CAPA management** \> **All CAPA cases**.

To view and work with only the CAPA cases that you're responsible for, follow one of these steps.

- Go to **Inventory management** \> **Periodic tasks** \> **CAPA management** \> **My CAPA cases**.
- Go to **Common** \> **Common** \> **CAPA management** \> **My CAPA cases**.

## FastTabs on the CAPA case details page

When you open a CAPA case record from the workspace or any list page, the details page provides the following FastTabs. Use the fields and settings on these FastTabs to view or edit information about the CAPA case.

- **General** – View or edit general information about the selected CAPA case. Many of the values on this FastTab are set when the case is created.
- **Email notifications** – View, add, and edit people who should be emailed when selected events occur for the current CAPA case (for example, when the status of the case or one of its activities is changed to *Closed*, *Canceled*, or *Reopened*).
- **Case log** – View, add, or edit information about the CAPA case. The system automatically adds log entries when specific events occur (for example, when the case is created, its status is changed, or activities are completed). Additionally, you can manually add log entries.
- **Associations** – View or edit information about records that are associated with the CAPA case. Examples of these records include sales order, item, vendor, and batch order records. Often, one or more of these associations are automatically set, based on where the user was when they created the case. However, you can add more associations as you work with the case.
- **Knowledge article** – View or edit information about knowledge articles that are associated with the CAPA case.
- **Administration** – View administrative details about the CAPA case. Examples include the date when the case was opened and the user who opened it.
- **Resolution** – View or edit information about how the CAPA case was resolved.

## Create a new CAPA case

You can create CAPA cases from many different pages in the system, including pages where you work with records that CAPA cases might originate from. Examples of those records include customer, vendor, sales order, purchase order, return order, and released product records. You can also create CAPA cases from the **All CAPA cases** and **My CAPA cases** pages. When you create a CAPA case from a related or originating record, the case is automatically linked to that record.

1. Go to the customer, vendor, sales order, purchase order, return order, or released product record that the CAPA case originates from.
1. Depending on the page that you're working on, follow one of these steps.

    - **For customers or vendors:** On the Action, on the **General** tab, in the **New** group, select **CAPA case**.
    - **For sales orders, purchase orders, or return orders:** On the Action Pane, on the **General** tab, in the **CAPA** group, select **Create CAPA case**.
    - **For released products:** On the Action Pane, on the **General** tab, in the **Maintain CAPA cases** group, select **Create CAPA case**.
    - **For nonconformance records:** On the Action Pane, select **Functions** \> **Create CAPA case**.
    - **From the All CAPA cases or My CAPA cases page:**

        - To create a CAPA case that isn't linked to an existing case, on the Action Pane, select **New** \> **CAPA case**.
        - To create a CAPA case that is linked to an existing case, select the parent case in the grid, and then, on the Action Pane, select **New** \> **Dependent CAPA case**.

    - **From the CAPA management workspace:** On the Action Pane, select **Create new** \> **CAPA case**. Alternatively, on the **CAPA case summary** FastTab, select **New CAPA case**.

1. In the **New CAPA case** dialog, on the **General** tab, set the following fields:

    - **Name** – Enter or select the name of a person from the global address book to associate that person with the CAPA case. If you started from a customer, vendor, sales order, purchase order, or return order, this field is automatically set based on the record that was selected when you created the CAPA case.
    - **Case ID** – The system-generated identification number of the CAPA case.
    - **Status** – Select the status of the CAPA case. The default status is *Opened*. This status indicates that the case isn't being worked on yet. When work on the case begins, you or the assigned worker should change the status to *In process*.
    - **Description** – Enter a short description of the CAPA case. The description is used to identify the case in lists and on reports. It's also shown as the heading of the case when you open it.
    - **Priority** – Select the priority of the CAPA case.
    - **Parent case** – If you want to associate the CAPA case with another case, select the parent case. If you selected a parent case when you created this case, the association is automatically set.
    - **CAPA category** – Select a category for the CAPA case. The category is used to analyze trends for reporting purposes.
    - **CAPA subcategory** – If subcategories are defined for the category that you selected, select one. The subcategory is used to analyze trends for reporting purposes.
    - **Description** – Enter a brief description of the CAPA case.
    - **CAPA process** – Select the CAPA process that should be followed to resolve this case. The CAPA process guides workers who are assigned to the case through the steps that are required to resolve it. It defines a series of stages. These stages must be completed in order. Within each stage, the CAPA process defines activities that should be completed before the process is moved to the next stage.

1. If you want to add a log entry to the case, on the **Case log** tab, enter the details of the log entry. You can view and add log entries from the details page for a CAPA case.
1. Select **OK** to create the case and open its details.

## Work through a CAPA process

A CAPA process guides workers who are assigned to a case through the steps that are required to resolve it. It defines a series of stages that must be completed in order. Each stage can include one or more activities. The activities can be completed in any order or simultaneously. Some activities might be mandatory. All mandatory activities must be completed before the process can be moved to the next stage.

Based on the configuration of the CAPA process, a worker or worker group is automatically assigned to each stage and activity. The system uses email to notify each responsible worker or worker group when a case, stage, or activity is assigned to them. The email includes links so that the case, stage, or activity can be opened directly from the message. Workers can always track which cases and activities are assigned to them by opening the **CAPA management** dashboard.

CAPA processes are defined by an administrator or manager. The **CAPA process** field of the CAPA record is used to assign CAPA processes to cases as they are created. Your company can define as many CAPA processes as it needs. Learn more in [Set up CAPA case components](capa-set-up-case-components.md).

The workflow for CAPA processes consists of the following steps.

1. Create a CAPA case, and assign a CAPA process to it. The case initially has a status of *Opened*.
1. Select or open the case (for example, from the **CAPA management** workspace). Then select **Change status** \> **In process**. (If you're in the **CAPA management** workspace, the button is on the toolbar. If you're on the details page or another page, it's on the **CAPA case** tab of the Action Pane.) This status change indicates that the case is being actively worked on and enables it to move through the various stages of the process.
1. The process starts with the first stage (for example, *Definition*). The system generates the activities that are configured for the stage. (For example, there might be a single activity that is named *Identify the problem*.)
1. The system emails the **Employee responsible** contacts for the case, the active stage, and each active activity that belongs to that stage.
1. Workers can now work on each activity that they are assigned to, enter notes on the details page for the activity, and fill in information as required. Employees can access the details page for an activity in several ways:

    - Select a link in the email that was sent to them when the activity was generated.
    - Open the **CAPA management** workspace, and browse the activities that are listed on the various tabs (such as **My open activities**).
    - Open the **CAPA management** workspace, and select any tab that lists CAPA cases (such as **My open cases**). Select a case, and then, on the toolbar, select **View activities**. A list shows all activities for the selected CAPA case that belong to stages that have been started. Select an activity to open its details page.
    - Open the details of a CAPA case. On the Action Pane, on the **CAPA case** tab, select **Case process**. In the process tree, expand a stage, and select an activity. (The tree shows activities only for stages that have been started). Select the **Activity number** link to view the details for the selected activity.

1. As workers finish working on each activity, they close it (that is, mark it as completed). There are several ways to close an activity:

    - In the **CAPA management** workspace, select the activity on any tab where it appears. Then, on the toolbar, select **Set as complete**.
    - On the activity details page, on the Action Pane, on the **Activity** tab, select **Set as complete**.
    - On the activity details page, on the **Status** FastTab, set the **Closed** option to *Yes*.

1. After all mandatory activities for the current stage are closed, an employee who has the required permissions can move the case to the next stage. You can skip a stage as required. However, after you move to a stage, you can't return to a previous one. There are several ways to move a CAPA case to the next stage in its process:

    - In the **CAPA management** workspace, select the CAPA case on any tab where it appears. On the toolbar, select **Change stage**, and then select the stage that you want to move the case to.
    - On the CAPA case details page, on the **CAPA case** FastTab, select **Change stage**, and then select the stage that you want to move the case to.

1. The selected new stage begins. The system generates the activities that are configured for the stage, sends out emails to the responsible employees, and updates the **CAPA management** workspace, just as it did for the first stage in the process.
1. The process continues until all the required activities are completed and you're ready to close the case. Often, you begin by opening the CAPA case details and filling in the fields on the **Resolution** FastTab to document the outcome of the case. You then mark the case as closed. There are several ways to close a CAPA case:

    - In the **CAPA management** workspace, select the CAPA case on any tab where it appears, and then, on the toolbar, select **Set as complete**.
    - On a CAPA case list or details page, on the Action Pane, on the **CAPA Case** tab, select **Change status** \> **Closed**.

> [!TIP]
> To get a graphical overview of the process hierarchy for the current CAPA case, follow these steps.
>
> 1. Open the details page for the relevant CAPA case.
> 1. In the rightmost pane, select the **Related information** button :::image type="icon" source="media/related-information-button.png" border="false"::: to open the **Related information** FactBox pane.
> 1. On the **Process tree** FastTab, review the list of stages in the current process. You can expand any stage that has been started to view the activities that belong to it. Select and hold (or right-click) an activity to open its details.

## Analyze CAPA case statistics

Microsoft Dynamics 365 Supply Chain Management provides graphical displays that you can use to analyze CAPA case generation and progress. Use the statistics to identify trends, frequent issues, bottlenecks, and areas for improvement in your CAPA processes.

Statistical charts are provided in the **CAPA management** workspace and on the **Trending analysis** page. Although the charts in both places are similar, there are a few minor differences in the data that they show.

### Analyze statistics using the CAPA management workspace

To view statistics in the **CAPA management** workspace, follow these steps.

1. Go to **Inventory management** \> **Workspaces** \> **CAPA management**.
1. Select the **Statistics** FastTab. Two charts are shown.
1. Use the **Number of cases by** dropdown list to select the type of statistics that you want to view in the left chart.
1. Use the **Trending of cases by** dropdown list to select the period that you want to view in the right chart.
1. Use the buttons at the top of each chart to select its graphical style (for example, bar chart, line chart, or pie chart).

### Analyze statistics using the Trending analysis page

To view statistics on the **Trending analysis** page, follow these steps.

1. Go to **Inventory management** \> **Inquiries and reports** \> **CAPA management** \> **Trending analysis**.
1. On the **Data** tab, select the date range, and turn on each type of chart that you want to view.
1. Select the **Analytics by category** tab to view the selected charts.
1. Use the buttons at the top of each chart to select its graphical style (for example, bar chart, line chart, or pie chart).

## Review signatures for a CAPA case

The CAPA features can optionally be set up to require an electronic signature from any user who closes, cancels, and/or reopens a CAPA case. To review the signatures that are applied to a CAPA case, follow these steps.

1. Open or select the CAPA case that you want to review (for example, on the **All CAPA cases** page).
1. On the Action Pane, on the **CAPA case** tab, select **Signature review**.
