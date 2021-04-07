---
# required metadata

title: Category requests from vendors
description: 
author: 
manager: 
ms.date: 
ms.topic: 
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: 
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: 
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Category requests from vendors

[!include [banner](../includes/banner.md)]

The category request process allows vendors to request new procurement categories to associate with their vendor account. These procurement categories can then be utilized by the related procurement and sourcing processes. For more information, see [Procurement catalogs overview - Supply Chain Management | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/supply-chain/procurement/procurement-catalogs). These requests are initiated in the **Vendor information** workspace. They are then submitted to your agency for review. Approved categories are added to the list of procurement categories on the vendor&#39;s account. This functionality requires the **Allow vendors to apply for procurement categories through vendor collaboration** feature. This feature is disabled by default and can be enabled in **Workspaces > Feature management**. Contact your system administrator for help with enabling this feature.

After this feature is enabled, procurement categories can still be added to vendors manually when necessary. For more information, see [Approve vendors for specific procurement categories - Supply Chain Management | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/supply-chain/procurement/tasks/approve-vendors-specific-procurement-categories#:~:text=%20Approve%20vendors%20for%20specific%20procurement%20categories%20,DESK%20ACCESSORIES%20%28OFFICE...%207%20Select%20Save.%20More%20).

##Vendor setup
For vendors to initiate category requests they must be setup for vendor collaboration.

The vendor must have at least one vendor collaboration user with either the Vendor contact (external) or Vendor admin (external) security role. This vendor user will be able to create and submit category requests.

For more information, see [Set up and maintain vendor collaboration - Supply Chain Management | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/supply-chain/procurement/set-up-maintain-vendor-collaboration).

##Vendor category request workflow setup

The **Vendor category request workflow** must be setup in the procurement and sourcing workflows. Vendors will submit new category requests that you can review and approve. Requested procurement categories are added to a vendor account after a category request is approved.

The following is an example of setting up a simple **Vendor category request workflow** with a single approver. You will need to review your internal processes to determine what workflow setup is appropriate for your agency.

1. **Open Procurement and sourcing > Setup > Procurement and sourcing workflows**.
2. Select **New** from the Action Pane.
3. Select the **Vendor category request workflow**.
4. Login to the workflow editor.
5. The workflow editor opens.
6. Select **Properties** from the Action Pane.
7. The Properties page for the **Vendor category request workflow** opens.
8. Enter **Submission instructions**. These instructions are visible to vendors when submitting a category request.
9. Select **Close** on the **Properties** page.
10. Drag the **Approve new category request** workflow element onto the canvas.
11. Drag a link from the **Start** workflow element to the **Approve new category request** workflow element.
12. Drag a link from the **Approve new category request** workflow element to the **End** workflow element.
13. Double-click the **Approve new category request** workflow element.
14. Right-click the **Step 1** workflow element and select **Properties**.
15. The Properties page for the **Approve new category request** workflow element opens.
16. Enter a **Work item subject**. This shows as the **Subject** in **Work items assigned to me**.
17. Enter **Work item instructions**. These instructions are visible to approvers when selecting **Workflow** from the Action Pane of a Category request.
18. Select **Assignment** on the left.
19. Select an Assignment type of **User**.
20. Select the **User** tab.
21. Select an example approver from the list of **Available users**. For example, a user in procurement department.
22. Click the **\&gt;** icon to move the example approver to the list of **Selected users**.
23. Close the **Properties** page.
24. Select **Save and close**.
25. Enter **Version notes** for the workflow.
26. Select **OK** to save the workflow.
27. Select **Activate the new version** if you are ready to begin testing this workflow. Otherwise select **Do not activate the new version**.
28. Select **OK** to complete the workflow setup.

Tip: If your agency does not require approval of category requests then workflow should be configured for automatic approval.

For more information on workflow setup, see [Set Up Workflows - Business Central | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/business-central/across-set-up-workflows).

##Create and submit a category request

This section describes how vendors can use the vendor information workspace to create, edit, view, and submit category requests.

To initiate a new category request:

1. Open the vendor information workspace.
2. From the start page of the vendor information workspace, select the **Category requests** tile.
3. The **Category requests** page opens.
4. Select **New category request** from the Action Pane.
5. The **New category request** dialog box opens. Find the category you want to apply for by navigating the tree and/or using the filter at the top of the list. Then mark the check box for each relevant category. Note:
  - Categories that are currently active on your vendor account show as selected and can&#39;t be removed.
  - You can request multiple procurement categories in a single category request.
6. Select **OK** to create the draft request.
7. The new draft request now shows on the **Category requests** page.
8. Open the new draft request to review and edit it as needed.

- To see the list of categories currently included in this request, expand the **Requested categories** FastTab.
- To view your active categories, open the **Active categories** FactBox on the right side of the page.

- To add a new category, select **Add** from the  **Requested categories** FastTab toolbar.
- To remove a listed category from the request, select the target category on the **Requested categories** FastTab and then select **Remove** from the toolbar.
- To attach a document to the request, select **Attachments** on theAction Pane. Attached documents will be available to approvers when they review the category request.
- To remove attached documents, select **Attachment** s on the Action Pane. Select the document to remove and then select **Delete** from the Action Pane.

1. If you&#39;re ready to submit the request, select **Submit** from the Action Pane and follow the next steps. Otherwise just close the page to come back to it later.
2. Read any **Submission instructions** that appear here and then select **Submit**.
3. Enter additional information in the **Comment** box if needed and then select **Submit** to complete the request.

To edit a draft or recalled category request:

1. Open the **Category requests** page.
2. Select the draft or recalled request to open it.
3. Edit the request as needed and then either close or submit it (see also the previous procedure).

To submit a draft or recalled request:

1. Open the **Category requests** page.
2. Select the draft or recalled request you want to submit.
3. Select **Submit** on the Action Pane.
4. Additional instruction may appear here and then select **Submit**.
5. Enter additional information in the **Comment** box if needed and then select **Submit** to complete the request.
6. The status of the category request changes as follows:
  - _Pending review –_ Indicates that the request is in workflow.
  - _Pending approval_ – Indicates that approval is needed.

To recall a submitted request that has not yet been approved:

1. Open the **Category requests** page.
2. Select the pending request that you want to recall.
3. Select **Recall** on the Action Pane.
4. Enter additional information in the **Enter a comment** box if needed and then select **Submit** to complete the request.
5. The status of the category request changes to _Cancelled_. The request will remain in this state until you delete or resubmit it.

To delete a draft or recalled request:

1. Open the **Category requests** page.
2. Select the draft or recalled request you want to delete.
3. Select **Delete** on the Action Pane.
4. Select **Yes** to confirm the deletion.

Viewing completed requests:

1. Open the **Category requests** page.
2. The status of the category request changes as follows:
  - _Approved_ – Indicates that the request was approved. The requested categories can be seen in the following location.
    1. Open the vendor information workspace.
    2. Open More details and select **Categories**. The newly added categories will show here.
  - _Rejected_ – Indicates that the request was rejected. If needed, a new category request can be created.

##Reviewing a category request

This section describes how customers can approve, reject, and delegate vendor submitted category requests as well as view completed requests. These workflow actions are for the entire category request.

To view category requests:

1. Open **Procurement and sourcing > Vendors > Vendor collaboration requests > Category requests**.
2. The **Category requests** page opens.
3. Category requests **Pending action** will show initially.
4. To view all requests, click **Show requests** and select All.
5. Open a request to review and edit it as needed.
  - To see the list of categories currently included in this request, expand the **Requested categories** FastTab.
  - To view your active categories, open the **Active categories** FactBox on the right side of the page.
  - If documents were submitted the attachments icon will display a count of attachments. To view attached documents, select **Attachments** on the Action Pane. Select a document you want to view. Select **Open** to view the document.
  - To attach a document to the request, select **Attachments** on theAction Pane. Attached documents will be available to approvers when they review the category request.
  - To remove attached documents, select **Attachments** on the Action Pane. Select the document to remove and then select **Delete** from the Action Pane.
  - To view workflow history, select **Workflow** on the Action Pane. Select **More** and **Workflow history** from the workflow options. The **Workflow history** page will open.

To approve a pending category request:

1. Open the **Category requests** page.
2. Select the pending request you want to approve.
3. Review the category request.
4. Optionally you can select a **Reason code** and enter a **Reason comment** in the **General** FastTab.
5. Select **Workflow** on the Action Pane.
6. Select **Approve** from the workflow options.
7. Enter additional information in the **Comment** box if needed and then select **Approve** to complete the request.
8. The status of the category request changes to _Approved_ and the procurement categories are added to the vendor.

To reject a pending category request:

1. Open the **Category requests** page.
2. Select the pending request you want to reject.
3. Review the category request.
4. Select **Edit** from the Action Pane.
5. Select a **Reason code** and enter a **Reason comment** in the **General** FastTab.
6. Select **Save** from the Action Pane.
7. Select **Workflow** on the Action Pane.
8. Select **More** and **Reject** from the workflow options.
9. Enter additional information in the **Comment** box if needed and then select **Reject** to complete the request.
10. The status of the category request changes to _Rejected._ If needed, a new category request can be created by the vendor.

To delegate a pending category request to another user:

1. Open the **Category requests** page.
2. Select the pending request you want to approve.
3. Select **Workflow** on the Action Pane.
4. Select **More** and **Delegate** from the workflow options.
5. Select a **User** to assign the category request to for review.
6. Enter additional information in the **Comment** box if needed.
7. Select **Delegate** to complete the delegation. The user selected during delegation can now review the category request.

To view a vendors procurement categories after a category request is approved:

1. Open **Accounts payable > Vendors > All vendors**.
2. The **All vendors** page opens.
3. Select the vendor you want to view.
4. Select **General** from the Action Pane.
5. Select **Set up** and **Categories** from the ribbon.
6. The **Categories** page opens.
7. Procurement categories added by the category request show in the **Procurement** FastTab.
8. From here changes can be made, such as setting the **Vendor category status** to _Preferred_.
