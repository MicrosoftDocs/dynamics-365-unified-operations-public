---
# required metadata

title: Work order lifecycle states
description: This topic explains work order lifecycle states in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Work order lifecycle states

Work order lifecycle states define the states that a work order can go through, for example, Created, Scheduled, In progress, and Ended. Work order lifecycle states may be updated manually on a work order, or they may be updated automatically, for example during work order scheduling.

The work order lifecycle states required for your work orders must be attached to matching project stages in the **Project management and accounting** module > **Project management and accounting parameters**. First, you set up project stages in
**Project management and accounting**, then you set up work order lifecycle states and work order lifecycle models in **Asset Management**.

Here is a short description of the toggle buttons in the **Work order lifecycle state** form > **General** FastTab > **Work order** and **Schedule** groups:


![Figure 1](media/09-setup-for-work-orders.png)


| Field name            | Description                                                                                                                                                    |
|---------------------- |----------------------------------------------------------------------------------------------------------------------------------------------------|
| Active                | Select "Yes" if the work order should be active at this state.   |
| Add line              | Select "Yes" if it should be possible to add work order jobs to a work order at this state.                                                           |
| Delete                | Select "Yes" if it should be possible to delete a work order at this state.                                                                           |
| Delete line           | Select "Yes" if it should be possible to delete work order jobs on a work order at this state.                                                       |
| Allow scheduling      | Select "Yes" if it should be possible to schedule a work order at this state.                                                                         |
| Set actual start      | Select "Yes" to ensure that when a work order is updated to this state, the user is asked to select an actual start date and time for the work order.                                                                                                                                         |
| Set actual end        | Select "Yes" to ensure that when a work order is updated to this state, the user is asked to select an actual end date and time for the work order.                                                                                                                                           |
| Post journals         | Select "Yes" if work order journals should be automatically posted at this state. If journal posting results in an error, an Infolog message is shown, and the work order state update is canceled. If you want to check the journal lines of a work order, click **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders** or **My active work orders** > select work order in list > **Journals**. This automatic setup of work order journal posting at a certain state is the same as when you click the **Post journals** button in [Work order journals](../consumption/register-consumption.md). **Note:** If you select "Yes" on this toggle button, journals are automatically posted if no approval workflow has been set up. If your company uses the journal approval setup in **Project management and accounting** > **Setup** > **Journals** > **Journal approval**, consumption registrations must be validated and posted by a manager or clerk. |
| Process maintenance checklist     | If you select "Yes", it means that when a work order is updated to this state, all attached maintenance checklists will be processed. Processing includes posting any counter registrations made on a maintenance checklist and evaluating the result of the maintenance checklist as a whole. Maintenance checklist lines with 'Pass/Fail' results are evaluated, and if at least one maintenance checklist line has failed, the entire maintenance checklist is marked as "failed" in Asset Management.                                                                                                                                  |
| Ready                 | If you select "Yes", it means that when a work order is updated to this state, the work order job schedule status for all work order jobs created on the work order is automatically updated to "Ready".                                                                                      |
| Start                 | If you select "Yes", it means that when a work order is updated to this state, the work order job schedule status for all work order jobs created on the work order is automatically updated to "Started".                                                                                    |
| End                   | If you select "Yes", it means that when a work order is updated to this state, the work order job schedule status for all work order jobs created on the work order is automatically updated to "Ended".                                                                                      |
| Delete schedule lines | If you select "Yes", when a work order is set to this state, and it has already been scheduled, scheduling will be deleted on all work order jobs created on that work order. This means capacity reservations on the asset, the related maintenance worker, and related tools will be deleted. *Example:* Select this parameter on a work order state called "Estimated", to allow scheduling to be deleted on a work order which is 'rolled back' to this state, because rescheduling is required.                                                                                    |


## Set up project stages and work order lifecycle states

1. Click **Project management and accounting** > **Setup** > **Project management and accounting parameters**.
2. Click **Project stage**.
3. For each stage you want to use, select the project type check boxes required for your work orders. The project types define rules regarding which financial tasks are allowed, for example, create forecast, create estimates, create beginning
balances, and so on.

>[!NOTE]
>If the project stage for the project type is not selected, and that project stage is used on a work order lifecycle state, the work order projects will not be updated accordingly.

4. Close **Project management and accounting parameters**.
5. Click **Asset management** > **Setup** > **Work orders** > **Lifecycle states**.
6. Click **New**, to create a new work order lifecycle state.
7. Insert an ID in the **Lifecycle state** field and a name for the lifecycle state in the **Name** field. In the **Lifecycle models** field, you can see the number of work order lifecycle models that uses the work order lifecycle state.
8. On the **General** FastTab, in the **Work order** and **Schedule** sections, select the functions that should be available for the lifecycle state by selecting "Yes" on the relevant toggle buttons. Refer to the table above for some of the lifecycle state descriptions.
9. In the **Project** section > **Stage** field, select the the project stage to be related to the work order lifecycle state.
10. In the **Project** section, select "Yes" on the **Close activities** toggle button if project activities related to each work order job should be automatically closed at this state.

>[!NOTE]
>The project activity number related to a work order job is shown in **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders** or **My active work orders** > open a work order > select work order job > **Line details** FastTab > **General** tab > **Project** section > **Activity number** field.

11. Select "Yes" on one or more of the **Copy hour forecast**, **Copy item forecast**, **Copy expense forecast** toggle buttons if you want to automatically copy work order project forecasts to work order journals at this lifecycle state.
12. In the **Schedule** group, select "Yes" on one of the toggle buttons if you want schedule status for work order jobs to be updated at this state. Refer to the descriptions of **Ready**, **Start**, **End**, and **Delete schedule lines** in the table above.
>[!NOTE]
>Schedule lines related to work order jobs are shown in **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders** or **My active work orders** > select and open work order > select a work order job on the **Work order jobs** FastTab > see related information on the **Line details** FastTab. The status of the work order job is shown on the **Schedule** tab in the **Status** field. The **Status** field may show one of the following statuses: Scheduled - Ready - Started - Stopped - Ended.

13. In the **Maintenance requests** section > **Lifecycle state** field, select the the maintenance request lifecycle state to which related maintenance requests are updated. This is an automatic update of related maintenance requests. The update can only be done if the maintenance request lifecycle state is selected in the maintenance request lifecycle model used for the maintenance request. 
14. Select "Yes" on the **Update asset BOM** toggle button if all items used on a work order should automatically be updated in **Asset BOM** when the work order is updated to this state. For example, this could be relevant for a work order lifecycle state defining that the work order is completed or ended.
15. Select "Yes" on the **Delete pool reference** toggle button if you want work orders to be automatically deleted from work order pools at this lifecycle state.
16. On the **Validate** FastTab, select "Yes" on the toggle buttons for the validation types you want to activate at this lifecycle state. In the **Type** field regarding each validation type, select the type of message that should be shown if mandatory fields related to the validation type have not been validated. If you select the message type "Error", the work order lifecycle state update is canceled until the related mandatory fields have been updated on the work order.

- The **Maintenance downtime**, **Maintenance checklist**, **Fault symptom**, **Fault cause**, and **Fault remedy** toggle buttons on the **Validate** FastTab relate to the toggle buttons in the **Mandatory** section in **Work order types** (**Asset management** > **Setup** > **Work orders** > **Work order types**). In order to activate those validations, the related toggle buttons must also be set to "Yes" on the work order type used on the work order.  
- When a work order is updated to a work order lifecycle state for which the **Maintenance checklist** toggle button is set to "Yes" on the **Validate** FastTab, it means that the mainteance checklist lines marked "Mandatory" are validated as being either 'Checked' or 'Not applicable'. If none of those registrations have been made on the mandatory lines, an info message or error or warning will be shown when the work order lifecycle state is updated to this state.  
- When a work order is updated to a work order lifecycle state for which the **Committed cost** toggle button is set to "Yes" on the **Validate** FastTab, it means that total committed costs (meaning total amount of expenses that the legal entity has committed to pay) are calculated for each work order job. An Infolog is shown if the committed cost amount is larger than zero. The types of cost commitment to be included are selected in **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Cost control** > **Cost commitments** section.  
- When a work order is updated to a work order lifecycle state for which the **Maintenance downtime** toggle button is set to "Yes", a maintenance downtime validation is made on the asset related to a work order. If a maintenance downtime registration has been made, and it does not have an 'ended' registration, a message is displayed when the work order is updated to this lifecycle state.





- In **Project management and accounting parameters**, you can set up user-defined project stages if you require special stages for your **Enterprise Asset Management** setup that are not included in the standard project setup.  
- See the [Forecasts, work orders, and projects](../integration-to-project-management-and-accounting/forecasts-work-orders-and-projects.md) section for more information on the relation between work order stages, project stages, and work order projects. The figure below shows a screenshot of the interface.  

- When you change stage on a work order to a work order stage that is not active (meaning "No" is selected on the **Active** toggle button on the **General** FastTab for that stage in the **Work order stages** view), not yet posted journals related to the work order will automatically be deleted. This is done to ensure automatic cleanup of unused data.

- However, if you manually set a work order to be inactive (**Enterprise asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders** > select work order in list > **Edit** button > **Header** link > **General** FastTab > set the **Active** toggle button to "No"), related but not yet posted journals will not automatically be deleted.

## Stage group, type, and stage relations

Stage groups refer to work flows, and stages are selected in a stage group in a sequential order. Stage groups are set up on types. Types determine the size or extent of work flows and work processes. For example, a standard work order type, "Maintenance", may be related to a work order stage group containing many stages. A "Corrective" work order type, which is used for work orders that have not been scheduled, or work orders for which the job was completed before the work order was made because of a need of urgency, may have a related work order stage group that only contains a few work order stages.

The idea behind using types is that when a type is defined on, for example, a work order or an object, the related work processes (stages) are automatically defined. Refer to the [Work order types](../setup-for-work-orders/work-order-types.md) section for more information about how to set up work order types.

**Note:** Stages, stage groups, and types apply to: [Functional locations](../setup-for-functional-locations/functional-location-stages.md) - [Objects](../setup-for-objects/object-stages.md) - [Requests](../setup-for-requests/request-stages.md) - Work orders.

The figure below shows the relation between work order types, work order stage groups, and related work order stages.

![Figure 2](media/10-setup-for-work-orders.png)

## Work order stage groups

When you have created the work order stages required for your work orders, stages can be divided into work order groups. As a minimum, one standard work order stage group should be created.

1. Click **Enterprise asset management** > **Setup** > **Work order** > **Stage** > **Stage groups**.
2. Click **New** to create a new work order stage.
3. Insert the stage group ID in the **Stage group** field and a name for the stage group in the **Name** field. In the **Stages** and **Work order types** fields, you can see the number of stages selected in the stage group, and the number of work order types that uses the stage group.
4. On the **Stages** FastTab, select the stages that should be included in the group. This is done by clicking on a stage in the **Stages remaining** section and clicking the ![forward arrow](media/13-setup-for-work-orders.png) button.
5. If you want to select all the available stages for a group, click the ![select all available stages](media/14-setup-for-work-orders.png) button. All stages are transferred to the **Stages selected** section.
6. If you want to remove a selected stage from the group, select the stage in the
**Stages selected** section and click the ![back arrow](media/15-setup-for-work-orders.png) button.
7. Click **Stage updates** to define which stages can follow a selected stage.
8. On the **General** FastTab, in the **Scheduled stage** field, select the stage that should always be selected for a work order when you have completed [Work order scheduling](../work-order-scheduling/set-up-worker-calendar.md) on that work order, regardless of the previous stage of the work order.
9. In the **Unscheduled stage** field, select the stage that should always be selected for a work order in case work order scheduling is deleted.
10. Save the work order stage group.

The figure below shows a screenshot of the interface.

![Figure 4](media/16-setup-for-work-orders.png)
