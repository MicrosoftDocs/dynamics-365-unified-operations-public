---
title: Category requests from vendors
description: This article describes how vendors can request procurement categories for their account. It also describes the approval process that is completed by procurement agents.
author: GalynaFedorova
ms.date: 04/19/2021
ms.topic: article
ms.search.form: VendRequestNewCategory
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-04-19
ms.dyn365.ops.version: 10.0.18
---

# Category requests from vendors

[!include [banner](../includes/banner.md)]

The category request process lets vendors request that new procurement categories be associated with their account. Those procurement categories can then be used by the related procurement and sourcing processes. (For more information, see [Procurement catalogs overview](procurement-catalogs.md).)

Category requests are initiated by vendors in the **Vendor information** workspace. They are then submitted to your agency for review and approval. Approved categories are added to the list of procurement categories for the vendor's account.

## Turn the category requests from vendors feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Allow vendors to apply for procurement categories through vendor collaboration* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

If this feature is turned on, you can still manually add procurement categories to vendor accounts. For information, see [Approve vendors for specific procurement categories](tasks/approve-vendors-specific-procurement-categories.md).

## Vendor collaboration requirements

Before a vendor can interact with category requests, it must be set up for vendor collaboration.

The vendor must have at least one vendor collaboration user. Only vendor users with the *Vendor admin (external)* security role can create and submit category requests.

For more information, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

## Set up the Vendor category request workflow

The *Vendor category request* workflow must be set up in the procurement and sourcing workflows. Vendors will submit new category requests that you can review and approve. Requested procurement categories are added to a vendor account after a category request is approved.

The following example shows how to set up a simple *Vendor category request* workflow that has a single approver. You must review your internal processes to determine the appropriate workflow setup for your agency.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing workflows**.
1. On the Action Pane, select **New**.
1. In the dialog box, select **Vendor category request workflow** to open the workflow editor.
1. Sign in to the workflow editor.
1. On the Action Pane, select **Properties**.
1. On the **Properties** page for the workflow, in the **Submission instructions** field, enter instruction text. The instructions will be visible to vendors when they submit a category request.
1. Close the **Properties** page.
1. Drag the **Approve new category request** workflow element onto the canvas.
1. Drag a link from the **Start** workflow element to the **Approve new category request** workflow element.
1. Drag a link from the **Approve new category request** workflow element to the **End** workflow element.
1. Double-tap (or double-click) the **Approve new category request** workflow element.
1. Select and hold (or right-click) the **Step 1** workflow element, and then select **Properties**.
1. On the **Properties** page for the workflow element, in the **Work item subject** field, enter subject text. This text will be shown as the value of the **Subject** field on the **Work items assigned to me** page.
1. In the **Work item instructions** field, enter instruction text. The instructions will be visible to approvers when they select **Workflow** on the Action Pane of a category request.
1. In the left pane, select **Assignment**.
1. On the **Assignment type** tab, set **Assign users to this workflow element** to *User*.
1. On the **User** tab, in the **Available users** list, select an approver. For example, select a user in the Procurement department.
1. Select the right arrow button (**\>**) to move the approver to the **Selected users** list.
1. Close the **Properties** page.
1. Select **Save and close**.
1. In the **Version notes** field, enter notes about the workflow.
1. Select **OK** to save the workflow.
1. If you're ready to start to test the workflow, select **Activate the new version**. Otherwise, select **Do not activate the new version**.
1. Select **OK** to complete the workflow setup.

> [!TIP]
> If your agency doesn't require approval of category requests, you should configure the workflow for automatic approval.

For more information about how to set up workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).

## Create and submit a category request

This section describes how vendors can use the **Vendor information** workspace to create, edit, view, and submit category requests.

### Start a new request

To start a new category request, follow these steps.

1. In the **Vendor information** workspace, select the **Category requests** tile.
1. On the **Category requests** page, on the Action Pane, select **New category request**.
1. In the **New category request** dialog box, find the category that you want to apply for by navigating the tree and/or using the filter at the top of the list. Select the checkbox for each relevant category.

    Note the following points:

    - Categories that are currently active on your vendor account are shown as selected and can't be removed.
    - You can request multiple procurement categories in a single category request.

1. Select **OK** to create the draft request.

    The new draft request now appears on the **Category requests** page.

1. Open the new draft request to review and edit it as required.

    - To view the list of categories that are currently included in the request, select the **Requested categories** FastTab.
    - To view your active categories, open the **Active categories** FactBox on the right side of the page.
    - To add a category to the request, select **Add** on the toolbar on the **Requested categories** FastTab.
    - To remove a category from the request, select the category on the **Requested categories** FastTab, and then select **Remove** on the toolbar.
    - To attach a document to the request, select **Attachments** on the Action Pane. Attached documents will be available to approvers when they review the category request.
    - To remove an attached document from the request, select **Attachments** on the Action Pane. Select the document to remove, and then select **Delete** on the Action Pane.

1. If you're ready to submit the request, select **Submit** on the Action Pane. Otherwise, just close the page and skip the remaining steps of this procedure. You can then return to the request later.
1. Read any submission instructions that appear, and then select **Submit**.
1. In the **Comment** box, enter any additional information that is required. Then select **Submit** to complete the request.

### Edit a draft or recalled request

To edit a draft or recalled category request, follow these steps.

1. In the **Vendor information** workspace, select the **Category requests** tile.
1. Select the draft or recalled request to open it.
1. Edit the request as required, and then either close it or submit it as described in the previous procedure.

### Submit a draft or recalled request

To submit a draft or recalled category request, follow these steps.

1. In the **Vendor information** workspace, select the **Category requests** tile.
1. Select the draft or recalled request that you want to submit.
1. On the Action Pane, select **Submit**.
1. Read any submission instructions that appear, and then select **Submit**.
1. In the **Comment** box, enter any additional information that is required. Then select **Submit** to complete the request.

    The status of the category request is changed to one of the following values:

    - _Pending review_ – The request is in the workflow.
    - _Pending approval_ – Approval is required.

### Recall a submitted request that hasn't yet been approved

To recall a category request that has been submitted but hasn't yet been approved, follow these steps.

1. In the **Vendor information** workspace, select the **Category requests** tile.
1. Select the pending request that you want to recall.
1. On the Action Pane, select **Recall**.
1. In the **Enter a comment** box, enter any additional information that is required. Then select **Submit** to complete the request.

    The status of the category request is changed to _Canceled_. The request will remain in this status until you delete or resubmit it.

### Delete a draft or recalled request

To delete a draft or recalled category request, follow these steps.

1. In the **Vendor information** workspace, select the **Category requests** tile.
1. Select the draft or recalled request that you want to delete.
1. On the Action Pane, select **Delete**.
1. Select **Yes** to confirm the deletion.

### View completed requests

To view completed requests, open the **Vendor information** workspace and select the **Category requests** tile. Category requests that have been completed will have one of the following statuses:

- _Approved_ – The request was approved. To view the newly added categories, go back to the **Vendor information** workspace, open the **More details** drop-down list in the left pane, and then select **Categories**.
- _Rejected_ – The request was rejected. You can create a new category request as required.

## Review category requests

This section explains how to approve, reject, and delegate category requests that vendors submitted, and how to view completed requests. These workflow actions are for the whole category request.

### View category requests

To view category requests, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> Vendor collaboration requests \> Category requests**.

    The **Category requests** page appears. The default page view shows category requests that have a status of *Pending action*.

1. To view all requests, select *All* in the **Show requests** field.
1. Open a request to review and edit it as required.

    - To view the list of categories that are currently included in the request, select the **Requested categories** FastTab.
    - To view the active categories, open the **Active categories** FactBox on the right side of the page.
    - If documents were submitted, the  **Attachments** (paper clip) button on the Action Pane shows a count of the attached documents. To view attached documents, select the **Attachments** button. Then select the document to view and select **Open** to view it.
    - To attach a document to the request, select **Attachments** on the Action Pane. Attached documents will be available to approvers when they review the category request.
    - To remove an attached document from the request, select **Attachments** on the Action Pane. Select the document to remove, and then select **Delete** on the Action Pane.
    - To view the workflow history, select **Workflow** on the Action Pane. In the workflow options, select **More** and then **Workflow history**. The **Workflow history** page appears.

### Approve a pending category request

To approve a pending category request, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> Vendor collaboration requests \> Category requests**.
1. Select the pending request to approve.
1. Review the category request.
1. Optional: On the **General** FastTab, in the **Reason code** field, select a reason code. Then, in the **Reason comment** field, enter a comment about the reason code.
1. On the Action Pane, select **Workflow**.
1. In the workflow options, select **Approve**.
1. In the **Comment** field, enter any additional information that is required. Then select **Approve** to complete the request.

    The status of the category request is changed to _Approved_, and the procurement categories are added to the vendor account.

### Reject a pending category request

To reject a pending category request, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> Vendor collaboration requests \> Category requests**.
1. Select the pending request to reject.
1. Review the category request.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, in the **Reason code** field, select a reason code. Then, in the **Reason comment** field, enter a comment about the reason code.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Workflow**.
1. In the workflow options, select **More** and then **Reject**.
1. In the **Comment** field, enter any additional information that is required. Then select **Reject** to complete the request.

    The status of the category request is changed to _Rejected_. At this point, the vendor can create a new category request as required.

### Delegate a pending category request

To delegate a pending category request to another user, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> Vendor collaboration requests \> Category requests**.
1. Select the pending request that you want to approve.
1. On the Action Pane, select **Workflow**.
1. In the workflow options, select **More** and then **Delegate**.
1. In the **User** field, select the user to assign the category request to for review.
1. In the **Comment** field, enter any additional information that is required.
1. Select **Delegate** to complete the delegation. The selected user can now review the category request.

### View procurement categories for a vendor

To view procurement categories for a vendor after a category request is approved, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. On the **All vendors** page, select the vendor that you want to view procurement categories for.
1. On the Action Pane, open the **General** tab and, from the **Set up** group, select **Categories**.

    The **Categories** page appears. The **Procurement** FastTab shows procurement categories that were added through the category request.

1. On the **Procurement** FastTab, you can make changes if needed. For example, you can set the **Vendor category status** field to _Preferred_.
