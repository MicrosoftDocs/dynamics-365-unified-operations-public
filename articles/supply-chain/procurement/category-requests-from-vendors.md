---
title: Category requests from vendors
description: This topic describes how vendors can request procurement categories for their account. It also includes the related approval process that is completed by the procurement agent.
author: TaylorVH
ms.date: 04/19/2021
ms.topic: article
ms.search.form: VendRequestNewCategory
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: taylorvh
ms.search.validFrom: 2021-04-19
ms.dyn365.ops.version: 10.0.18
---

# Category requests from vendors

[!include [banner](../includes/banner.md)]

The category request process allows vendors to request new procurement categories to associate with their vendor account. These procurement categories can then be utilized by the related procurement and sourcing processes (see also [Procurement catalogs overview](procurement-catalogs.md)). These requests are started in the **Vendor information** workspace by the vendor. They're then submitted to your agency for review. Approved categories are added to the list of procurement categories on the vendor's account

## Turn on this feature for your system

If your system doesn't already include the features described in this topic, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Allow vendors to apply for procurement categories through vendor collaboration* feature.

After this feature is enabled, you will still be able to add procurement categories to vendors manually when necessary, as described in [Approve vendors for specific procurement categories](tasks/approve-vendors-specific-procurement-categories.md).

## Vendor collaboration requirements

For vendors to interact with category requests, they must be set up for vendor collaboration.

The vendor must have at least one vendor collaboration user. This vendor user must have one or more of the following security roles. Vendor users with either of these roles can create and submit category requests.

- Vendor contact (external)
- Vendor admin (external)

For more information, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

## Vendor category request workflow setup

The *Vendor category request workflow* must be set up in the procurement and sourcing workflows. Vendors will submit new category requests that you can review and approve. Requested procurement categories are added to a vendor account after a category request is approved.

The following example shows how to set up a simple *Vendor category request workflow* with a single approver. You'll need to review your internal processes to determine the appropriate workflow set up for your agency.

1. Go to **Procurement and sourcing > Setup > Procurement and sourcing workflows**.
1. Select **New** from the Action Pane.
1. Select **Vendor category request workflow** from the dialog box.
1. Allow the workflow editor to open and sign in. The workflow editor opens.
1. Select **Properties** from the Action Pane.
1. The **Properties** page for the workflow opens.
1. Enter text in the **Submission instructions** field. These instructions are visible to vendors when submitting a category request.
1. Select **Close** on the **Properties** page.
1. Drag the **Approve new category request** workflow element onto the canvas.
1. Drag a link from the **Start** workflow element to the **Approve new category request** workflow element.
1. Drag a link from the **Approve new category request** workflow element to the **End** workflow element.
1. Double-click the **Approve new category request** workflow element.
1. Right-click the **Step 1** workflow element and select **Properties**.
1. The **Properties** page for the workflow element opens.
1. Enter text in the **Work item subject** field. This text shows as the **Subject** in **Work items assigned to me**.
1. Enter text in the **Work item instructions** field. These instructions are visible to approvers when selecting **Workflow** from the Action Pane of a category request.
1. Select **Assignment** in the pane on the left.
1. On the **Assignment type** tab, select *User*.
1. Open the **User** tab and select an example approver from the list of **Available users**. For example, select a user in procurement department.
1. Click the **>** icon to move the example approver to the list of **Selected users**.
1. Close the **Properties** page.
1. Select **Save and close**.
1. Enter **Version notes** for the workflow.
1. Select **OK** to save the workflow.
1. Select **Activate the new version** if you're ready to begin testing this workflow. Otherwise select **Do not activate the new version**.
1. Select **OK** to complete the workflow setup.

> [!TIP]
> If your agency doesn't require approval of category requests, then the workflow should be configured for automatic approval.

For more information on how to set up workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).

## Create and submit a category request

This section describes how vendors can use the vendor information workspace to create, edit, view, and submit category requests.

### Start a new category request

To start a new category request:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. The **Category requests** page opens.
1. Select **New category request** from the Action Pane.
1. The **New category request** dialog box opens. Find the category you want to apply for by navigating the tree and/or using the filter at the top of the list. Then mark the check box for each relevant category. Note:

    - Categories that are currently active on your vendor account show as selected and can't be removed.
    - You can request multiple procurement categories in a single category request.

1. Select **OK** to create the draft request.
1. The new draft request now shows on the **Category requests** page.
1. Open the new draft request to review and edit it as needed.

    - To see the list of categories currently included in this request, expand the **Requested categories** FastTab.
    - To view your active categories, open the **Active categories** FactBox on the right side of the page.
    - To add a new category, select **Add** from the  **Requested categories** FastTab toolbar.
    - To remove a listed category from the request, select the target category on the **Requested categories** FastTab and then select **Remove** from the toolbar.
    - To attach a document to the request, select **Attachments** on the Action Pane. Attached documents will be available to approvers when they review the category request.
    - To remove attached documents, select **Attachments** on the Action Pane. Select the document to remove and then select **Delete** from the Action Pane.

1. If you're ready to submit the request, select **Submit** from the Action Pane and follow the next steps. Otherwise just close the page to come back to it later.
1. Read any **Submission instructions** that appear here and then select **Submit**.
1. Enter additional information in the **Comment** box if needed and then select **Submit** to complete the request.

### Edit a draft or recalled category request

To edit a draft or recalled category request:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. Select the draft or recalled request to open it.
1. Edit the request as needed and then either close or submit it (see also the previous procedure).

### Submit a draft or recalled request

To submit a draft or recalled request:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. Select the draft or recalled request you want to submit.
1. Select **Submit** on the Action Pane.
1. More instructions may appear here and then select **Submit**.
1. Enter additional information in the **Comment** box if needed and then select **Submit** to complete the request.
1. The status of the category request changes as follows:
    - _Pending review_ – Indicates that the request is in workflow.
    - _Pending approval_ – Indicates that approval is needed.

### Recall a submitted request that hasn't yet been approved

To recall a submitted request that hasn't yet been approved:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. Select the pending request that you want to recall.
1. Select **Recall** on the Action Pane.
1. Enter additional information in the **Enter a comment** box if needed and then select **Submit** to complete the request.
1. The status of the category request changes to _Cancelled_. The request will remain in this state until you delete or resubmit it.

### Delete a draft or recalled request

To delete a draft or recalled request:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. Select the draft or recalled request you want to delete.
1. Select **Delete** on the Action Pane.
1. Select **Yes** to confirm the deletion.

### View completed requests

To view completed requests:

1. Open the vendor information workspace.
1. From the start page of the vendor information workspace, select the **Category requests** tile.
1. The status of the category request changes as follows:
    - _Approved_ – Indicates that the request was approved. The requested categories can be seen by doing the following:
        1. Open the vendor information workspace.
        1. Open **More details** and select **Categories**. The newly added categories will show here.
    - _Rejected_ – Indicates that the request was rejected. If needed, a new category request can be created.

## Review category requests

This section describes how to approve, reject, and delegate vendor submitted category requests and view completed requests. These workflow actions are for the entire category request.

### View category requests

To view category requests:

1. Go to **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
1. The **Category requests** page opens.
1. Category requests of status *Pending action* will show initially.
1. To view all requests, select *All* from the **Show requests** drop-down list.
1. Open a request to review and edit it as needed.
    - To see the list of categories currently included in this request, expand the **Requested categories** FastTab.
    - To view your active categories, open the **Active categories** FactBox on the right side of the page.
    - If documents were submitted, the attachments icon will display a count of attachments. To view attached documents, select **Attachments** on the Action Pane. Select a document you want to view and then select **Open** to view the document.
    - To attach a document to the request, select **Attachments** on the Action Pane. Attached documents will be available to approvers when they review the category request.
    - To remove attached documents, select **Attachments** on the Action Pane. Select the document to remove and then select **Delete** from the Action Pane.
    - To view workflow history, select **Workflow** on the Action Pane. Select **More** and **Workflow history** from the workflow options. The **Workflow history** page will open.

### Approve a pending category request

To approve a pending category request:

1. Go to **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
1. Select the pending request you want to approve.
1. Review the category request.
1. Optionally, you can select a **Reason code** and enter a **Reason comment** on the **General** FastTab.
1. Select **Workflow** on the Action Pane.
1. Select **Approve** from the workflow options.
1. Enter additional information in the **Comment** box if needed and then select **Approve** to complete the request.
1. The status of the category request changes to _Approved_ and the procurement categories are added to the vendor.

### Reject a pending category request

To reject a pending category request:

1. Go to **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
1. Select the pending request you want to reject.
1. Review the category request.
1. Select **Edit** from the Action Pane.
1. Select a **Reason code** and enter a **Reason comment** in the **General** FastTab.
1. Select **Save** from the Action Pane.
1. Select **Workflow** on the Action Pane.
1. Select **More** and **Reject** from the workflow options.
1. Enter additional information in the **Comment** box if needed and then select **Reject** to complete the request.
1. The status of the category request changes to _Rejected._ If needed, a new category request can be created by the vendor.

### Delegate a pending category request

To delegate a pending category request to another user:

1. Go to **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
1. Select the pending request you want to approve.
1. Select **Workflow** on the Action Pane.
1. Select **More** and **Delegate** from the workflow options.
1. Select a **User** to assign the category request to for review.
1. Enter additional information in the **Comment** box if needed.
1. Select **Delegate** to complete the delegation. The user selected during delegation can now review the category request.

### View procurement categories for a vendor

To view procurement categories for a vendor after a category request is approved:

1. Go to **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
1. The **All vendors** page opens. Select the vendor you want to view.
1. Select **General** from the Action Pane.
1. Select **Set up** and **Categories** from the ribbon.
1. The **Categories** page opens. Procurement categories added by the category request show in the **Procurement** FastTab.
1. on the **Procurement** FastTab, you can make changes such as setting the **Vendor category status** to _Preferred_.
