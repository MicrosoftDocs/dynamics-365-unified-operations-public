---
# required metadata

title: Vendor workflow
description: Modify vendor information and use workflow to approve it.
author: sunfzam
ms.date: 03/21/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  Vendor
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4
---

# Vendor workflow

[!include [banner](../includes/banner.md)]

When the vendor workflow is used, changes that are made to specific fields are sent to the workflow for approval before they are added to the vendor.

## Set up the vendor workflow

Before you can use the workflow feature, you must enable it.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2. On the **General** tab, on the **Vendor approval** FastTab, set the **Enable vendor approvals** option to **Yes**.
3. In the **Data entity behavior** field, select what action should be used when data is imported:

    - **Allow changes without approval** – The data entity can update the vendor record without processing it through the workflow.
    - **Reject changes** – Changes can't be made to the vendor record. The import will fail for the fields that are enabled for the workflow.
    - **Create change proposals** – All fields will be changed except the fields that are enabled for the workflow. The new values for those fields will be added to the vendor as proposed changes. The data entity will not automatically start the workflow, and you will need to submit the proposed changes as required.

4. In the list of vendor fields, select the **Enable** checkbox for every field that must be approved before the changes can be made.
5. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
6. Select **New**.
7. Select **Proposed vendor changes workflow**. 
8. Set up the workflow so that it matches your approval process. The **Workflow approval for proposed vendor change** workflow approval element will apply the changes to the vendor.

## Change vendor information and submit the changes to the workflow

When you change a field that is enabled for the workflow, the **Proposed changes** page appears. This page shows the original value of the field and the new value that you entered. The field that you changed is reverted to its original value. A status message will inform you that your changes haven't been submitted. 

Every time that you change a field that is enabled for the workflow, that field is added to the list on the **Proposed changes** page. To discard the proposed value for a field, use the **Discard** button next to the field in the list. To discard all changes, use the **Discard all changes** button at the bottom of the page. Select **OK** to close the page.

After you have at least one proposed change, two additional tabs appear on the action pane: **Proposed changes** and **Workflow**.

1. Select **Proposed changes** to open the **Proposed changes** page and review your changes.
2. Select **Workflow \> Submit to submit the changes to workflow**.

    The status on the page is changed to **Changes pending approval**.

The workflow follows the standard workflow process. The approver is directed to the **Vendor** page where the changes can be reviewed on the **Proposed changes** page and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the fields are updated with the values that you proposed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
