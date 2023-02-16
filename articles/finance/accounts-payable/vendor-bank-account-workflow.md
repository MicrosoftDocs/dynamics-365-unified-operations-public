---
title: Vendor bank account workflow
description: This article describes how to set up vendor bank account approval.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: VendBankAccount
ms.topic: how-to
ms.date: 02/15/2023
ms.custom: bap-template
---

# Vendor bank account workflow

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The vendor bank approval workflow ensures that bank data submitted by suppliers is secure, financially compliant, and protected against fraud. Businesses can evaluate and approve any incoming changes to a supplier's bank account information and confirm the provided bank details meet their organization's standards and policies. This feature helps reduce the risk of fraud by detecting and preventing unapproved changes.

When you enable the vendor bank account workflow, you can configure which fields will require approval and choose which actions will trigger the workflow.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.32 or later.
- The feature that is named *Vendor bank account change proposal workflow* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up the vendor bank account workflow

Set up the vendor bank approval workflow feature by following these steps.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **General** tab, expand the **Vendor bank account approval** FastTab and make the following settings.
    - **Bank account approval (create)** – Set this option to *Yes* to require approval for all new bank account records (both when using web client and when importing through the data entity). Set this option to *No* to allow users to create or import new bank account records without requiring approval.
    - **Bank account approval (update)** – Set this option to *Yes* to require approval when a user updates existing bank account records using the web client (approval will only be required for fields where **IsEnabled** is selected in the grid on this FastTab). Set this option to *No* to allow users to update all fields on existing bank account records without requiring approval.
    - **Data entity behavior (update)** – Select the behavior to use when updating a vendor bank account record by importing through the data entity. This setting doesn't affect changes you make using the web client. Choose one of the following options:
        - *Allow changes without approval* – The data entity will update values for all fields without processing the changes through the workflow.
        - *Reject changes* – The data entity will never update values for workflow-enabled fields. The import will fail if it includes updates for workflow-enabled fields.
        - *Create change proposals* – The data entity will update values for non-protected fields, and will add new values for workflow-enabled fields as proposed changes. The data entity starts the workflow automatically as needed.
1. In the list of vendor bank account fields, select the **IsEnabled** checkbox for each field that should require approval (based on the **Bank account approval (create)**, **Bank account approval (update)**, and **Data entity behavior** settings).
1. On the Action Pane, select **Save**.
1. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
1. On the Action Pane, select **New**.
1. The **Create workflow** dialog opens. Select **Workflow approval for proposed vendor change**.
1. The workflow editor app launches on your machine. Use it to design your workflow as needed. For details about how to design your workflow, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).

## Add a new vendor bank account and submit it for approval

To use the web client to add a new vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor you want to set up a bank account for.
1. On the Action Pane, open the **Vendor** tab and, from the **Set up** group,  select **Bank accounts**.
1. The **Vendor bank accounts** page opens. On the Action Pane, select **New** to create a new bank account.
1. Fill in all the required fields.
1. When you're done creating the record, select **Save**.
1. On the Action Pane, select **Workflow \> Submit** to submit your new bank account details for approval. Your new bank account record won't be available for use until an approver has approved it.

## Update an existing vendor bank account record and submit it for approval

To use the web client to edit an existing vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor you want to update bank information for.
1. On the Action Pane, open the **Vendor** tab and, from the **Set up** group, select **Bank accounts**.
1. The **Vendor bank accounts** page opens. On the list pane, select the account you want to edit and then select **Edit** on the Action Pane.
1. Edit the fields as needed. Each field that will require approval when updated is marked with **(requires approval)**.
1. When you're done editing the record, select **Save**.
1. If you've updated at least one field that requires approval, the Action Pane shows two new buttons: **Proposed changes** and **Workflow**.
    - To review your proposed changes, select **Proposed changes** on the Action Pane to open the **Proposed changes** dialog. From here, you can discard the proposed value for a field by selecting the **Discard** button next to the field in the list. To discard all changes, select the **Discard all changes** button at the bottom of the page. Select **OK** to close the page.
    - To submit your changes for approval, select **Workflow \> Submit** on the Action Pane. Your changes to protected fields won't be updated until an approver has approved them.

## Follow the approval status of a new or updated vendor bank account

Vendor bank account records include a **Review status** field in the record header, where you can track the approval status for the selected record. The following table lists the possible **Review status** values and their meanings.

| Review status | Description |
|---|---|
| *Draft* | Indicates a new bank account record that hasn't been submitted for approval. |
| *Approved* | Indicates a bank account record where all new and updated settings have been approved. |
| *Approved, changes not submitted* | Indicates a previously approved bank account record where protected fields have been edited but haven't yet been submitted for approval. |
| *Approved, pending changes* | Indicates a previously approved bank account record where protected fields have been edited and submitted for the approval. |

To view the workflow history, and follow the progress of a record under approval, select **Workflow \> View history** on the Action Pane.

## Approve a new or updated vendor bank account

Once submitted, the workflow follows the standard workflow process. The workflow will inform the appropriate approvers about the update and direct them to the **Vendor bank accounts** page, where they can do the following actions:

- For updates to existing bank account records, approvers can view the current and proposed value for each protected field by selecting **Proposed changes** on the Action Pane. The approver reviews the changes and selects **Workflow \> Approve** on the Action Pane to approve them. After all approvals are complete, the system updates all fields with the proposed values.
- For new bank account records, approvers must open the record, review the bank account details on the **Vendor bank accounts** page, and then select **Workflow \> Approve** to approve the new record. After all approvals are completed, the new bank account becomes available for use.
- To reject the new or updated record, the approver selects **Workflow \> Reject** on the Action Pane. This selection will return the record to its pre-submission **Review status** (*Draft* or *Approved, changes not submitted*) so it can be edited and/or submitted again as needed (by selecting **Workflow \> Resubmit** on the Action Pane).
- To delegate the approval to another approver, the approver can select **Workflow \> Delegate** on the Action Pane.
- To cancel a workflow in progress, any user can select **Workflow \> Cancel** on the Action Pane. This selection will return the record to its pre-submission **Review status** (*Draft* or *Approved, changes not submitted*) so it can be edited and/or submitted again as needed. This function might typically be used by the original submitter to correct an error.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
