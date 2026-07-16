---
title: Vendor workflow
description: Learn about the vendor overflow, including overviews on setting up the vendor workflow and changing vendor information and submitting changes to the workflow.
author: sunfzam
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-08-30
ms.search.form: Vendor
ms.dyn365.ops.version: 8.0.4
---

# Vendor workflow

[!include [banner](../includes/banner.md)]

When you use the vendor workflow, it sends changes to specific fields to the workflow for approval before adding them to the vendor.

## Set up the vendor workflow

Before you can use the workflow feature, you must enable it.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **General** tab, on the **Vendor approval** FastTab, set the **Enable vendor approvals** option to **Yes**.
1. In the **Data entity behavior** field, select what action should be used when data is imported:

    - **Allow changes without approval** – The data entity can update the vendor record without processing it through the workflow.
    - **Reject changes** – You can't make changes to the vendor record. The import fails for the fields that are enabled for the workflow.
    - **Create change proposals** – All fields are changed except the fields that are enabled for the workflow. The new values for those fields are added to the vendor as proposed changes. The data entity doesn't automatically start the workflow, and you need to submit the proposed changes as required.

1. In the list of vendor fields, select the **Enable** checkbox for every field that must be approved before the changes can be made.
1. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
1. Select **New**.
1. Select **Proposed vendor changes workflow**.
1. Set up the workflow so that it matches your approval process. The **Workflow approval for proposed vendor change** workflow approval element applies the changes to the vendor.

## Change vendor information and submit the changes to the workflow

When you change a field that the workflow enables, the **Proposed changes** page appears. This page shows the original value of the field and the new value that you entered. The field that you changed reverts to its original value. A status message informs you that your changes aren't submitted.

Every time you change a field that the workflow enables, the field is added to the list on the **Proposed changes** page. To discard the proposed value for a field, use the **Discard** button next to the field in the list. To discard all changes, use the **Discard all changes** button at the bottom of the page. Select **OK** to close the page.

After you have at least one proposed change, two additional tabs appear on the action pane: **Proposed changes** and **Workflow**.

1. Select **Proposed changes** to open the **Proposed changes** page and review your changes.
1. Select **Workflow \> Submit** to submit the changes to workflow.

    The status on the page changes to **Changes pending approval**.

The workflow follows the standard workflow process. The approver is directed to the **Vendor** page where they can review the changes on the **Proposed changes** page and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the fields are updated with the values that you proposed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
