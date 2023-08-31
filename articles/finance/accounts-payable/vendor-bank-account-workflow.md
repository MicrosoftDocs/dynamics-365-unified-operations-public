---
title: Vendor bank account workflow
description: This article describes how to set up vendor bank account approval.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: VendBankAccount
audience: Application User
ms.topic: how-to
ms.date: 02/15/2023
ms.custom: bap-template
---

# Vendor bank account workflow

[!include [banner](../includes/banner.md)]

The vendor bank approval workflow ensures that bank data that suppliers submit is secure, financially compliant, and protected against fraud. This feature helps reduce the risk of fraud by detecting and preventing unapproved changes. Businesses can evaluate and approve any incoming changes to a supplier's bank account information, and can confirm that the provided bank details meet their organization's standards and policies.

When you enable the vendor bank account workflow, you can specify which fields require approval and which actions will trigger the workflow.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- Your finance and operations apps must be version 10.0.32 or higher.
- The feature that's named *Vendor bank account change proposal workflow* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up the vendor bank account workflow

To set up the vendor bank approval workflow feature, follow these steps.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **General** tab, on the **Vendor bank account approval** FastTab, set the following fields:

    - **Bank account approval (create)** – Set this option to *Yes* to require approval for all new bank account records, regardless of whether the web client is used or records are imported through the data entity. Set this option to *No* to allow users to create or import new bank account records without requiring approval.
    - **Bank account approval (update)** – Set this option to *Yes* to require approval when a user updates existing bank account records by using the web client. (Approval will be required only for fields where the **IsEnabled** checkbox is selected in the grid on this FastTab). Set this option to *No* to allow users to update all fields on existing bank account records without requiring approval.
    - **Data entity behavior (update)** – Select one of the following values to specify the behavior that occurs when an existing record is updated via import through the data entity. The setting doesn't affect updates that you make by using the web client.

        - *Allow changes without approval* – The data entity will update values for all fields without processing the changes through the workflow.
        - *Reject changes* – The data entity will never update values for protected fields. The import will fail if it includes updates for protected fields.
        - *Create change proposals* – The data entity will update values for non-protected fields, and it will add new values for protected fields as proposed changes. The data entity will not automatically start the workflow, and you will need to submit the proposed changes as required.

1. In the list of vendor bank account fields, select the **IsEnabled** checkbox for each field that requires approval.
1. On the Action Pane, select **Save**.
1. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
1. On the Action Pane, select **New**.
1. In the **Create workflow** dialog box, select **Workflow approval for proposed vendor change**.
1. The workflow editor app is opened on your computer. Use it to design your workflow as you require. For more information about how to use the editor, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md) and its related articles.

## Add a new vendor bank account and submit it for approval

To use the web client to add a new vendor bank account and submit it for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor that you want to set up a bank account for.
1. On the Action Pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
1. On the **Vendor bank accounts** page, on the Action Pane, select **New** to create a bank account.
1. Fill in all the required fields.
1. When you've finished creating the record, select **Save**.
1. On the Action Pane, select **Workflow \> Submit** to submit the new bank account details for approval. The new bank account record won't be available for use until an approver has approved it.

## Update an existing vendor bank account record and submit it for approval

To use the web client to edit an existing vendor bank account and submit it for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor that you want to update bank information for.
1. On the Action Pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
1. On the **Vendor bank accounts** page, in the list pane, select the account that you want to edit. Then select **Edit** on the Action Pane.
1. Edit the fields as required. Each field that will require approval when it's updated is marked **(requires approval)**.
1. When you've finished editing the record, select **Save**.
1. If you updated at least one field that requires approval, the Action Pane has two new buttons: **Proposed changes** and **Workflow**.

    - To review your proposed changes, select **Proposed changes** on the Action Pane to open the **Proposed changes** dialog box. To discard the proposed value for a field, select **Discard** next to that field in the list. To discard all changes, select **Discard all changes** at the bottom of the dialog box. When you've finished, select **OK** to close the dialog box.
    - To submit your changes for approval, select **Workflow \> Submit** on the Action Pane. Your changes to protected fields won't be updated until an approver has approved them.

## Follow the approval status of a new or updated vendor bank account

The header of every vendor bank account record includes a **Review status** field that you can use to track the approval status for the record. The following table lists the possible **Review status** values and their meanings.

| Review status | Description |
|---|---|
| *Draft* | This status indicates a new bank account record that hasn't yet been submitted for approval. |
| *Approved* | This status indicates a bank account record where all new and updated settings have been approved. |
| *Approved, changes not submitted* | This status indicates a previously approved bank account record where protected fields have been edited but haven't yet been submitted for approval. |
| *Approved, pending changes* | This status indicates a previously approved bank account record where protected fields have been edited and submitted for the approval. |

To view the workflow history and follow the progress of a record that's undergoing approval, select **Workflow \> View history** on the Action Pane.

## Approve a new or updated vendor bank account

After a record is submitted, the workflow follows the standard workflow process. It informs the appropriate approvers about the update and directs them to the **Vendor bank accounts** page, where they can perform the following actions:

- For updates to existing bank account records, approvers can view the current and proposed value for each protected field by selecting **Proposed changes** on the Action Pane. The approver reviews the changes and then selects **Workflow \> Approve** on the Action Pane to approve them. After all approvals are completed, the system updates all fields with the proposed values.
- For new bank account records, approvers must open the record, review the bank account details on the **Vendor bank accounts** page, and then select **Workflow \> Approve** to approve the new record. After all approvals are completed, the new bank account becomes available for use.
- To reject new or updated records, the approver selects **Workflow \> Reject** on the Action Pane. The record is returned to its pre-submission review status (*Draft* or *Approved, changes not submitted*), so that it can be edited and/or resubmitted as required. (To resubmit a record, the user selects **Workflow \> Resubmit** on the Action Pane.)
- To delegate the approval to another approver, the approver can select **Workflow \> Delegate** on the Action Pane.
- To cancel a workflow in progress, any user can select **Workflow \> Cancel** on the Action Pane. The record is returned to its pre-submission review status (*Draft* or *Approved, changes not submitted*), so that it can be edited and/or resubmitted as required. The original submitter might use this function to correct an error.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
