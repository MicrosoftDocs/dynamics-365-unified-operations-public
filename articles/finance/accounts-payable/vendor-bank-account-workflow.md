---
title: Vendor bank account workflow
description: This article describes how to set up vendor bank account approval upon create and update.
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

The vendor bank approval workflow ensures that bank data submitted by suppliers is secure, financially compliant, and protected against fraud. Businesses can evaluate and approve any incoming changes to a supplier's bank account information and make sure the provided bank details meet their organization's standards and policies. This helps reduce the risk of fraud by detecting and preventing unapproved changes.

When you enable the vendor bank account workflow, you can configure which fields will require approval and choose which actions will trigger the workflow (create from the web client, update from the web client, and/or update from import through the data entity).

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.32 or later.
- The feature that is named *Vendor bank account change proposal workflow* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up the vendor bank account workflow

Set up the vendor bank approval workflow feature by following these steps.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **General** tab, expand the **Vendor bank account approval** FastTab and make the following settings.
    - **Bank account approval (create)** – Set this option to *Yes* to require approval when a user creates a new bank account record using the web client. Set this option to *No* to allow users to create new bank account records without requiring approval. <!-- KFM: How is this affected by the **IsEnabled** checkbox settings? -->
    - **Bank account approval (update)** – Set this option to *Yes* to require approval when a user updates existing bank account records using the web client (approval will only be required for fields where **IsEnabled** is selected in the grid on this FastTab). Set this option to *No* to allow users to update all fields on existing bank account records without requiring approval.
    - **Data entity behavior (update)** – Select the behavior that should be used when updated data is imported through the data entity. This setting doesn't affect changes you make using the web client. Choose one of the following options: <!-- KFM: Only applies during update? What about create? -->
        - *Allow changes without approval* – The data entity will update values for all fields without processing the changes through the workflow.
        - *Reject changes* – The data entity will never update values for workflow-enabled fields. The import will fail for workflow-enabled fields. <!-- KFM: Will non-workflow updates still be applied, or does the entire import fail? -->
        - *Create change proposals* – The data entity will update values for non-workflow enabled fields, and will add new values for workflow-enabled fields as proposed changes. The workflow will then be started automatically.
1. In the list of vendor bank account fields, select the **IsEnabled** checkbox for every field that should require approval (in combination with the **Bank account approval (create)**, **Bank account approval (update)**, and **Data entity behavior** settings).
1. On the Action Pane, select **Save**.
1. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
1. On the Action Pane, select **New**.
1. The **Create workflow** dialog opens. Select **Workflow approval for proposed vendor change**.
1. The workflow editor app launches on your machine. (You may be asked to approve this action.) Use it to design your workflow as needed. <!-- KFM: I suppose this is what is meant to happen, but it failed when I tried it. Are we missing some steps or prerequisites? --> For details about how to design your workflow, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).
1. After saving and closing the workflow editor app, you must choose whether to activate this workflow version or keep it as inactivate.

> [!NOTE]
> Workflows provide version control, which means that you can view a list of versions you have created and choose which one is active. To view the list of available versions and choose which to activate, select a workflow listed on the **Accounts payable workflows** page, open the **Workflow** tab on the Action Pane, and select **Versions**. Only one version can be active at a time for each workflow ID.

## Add a new vendor bank account and submit it for approval

To use the web client to add a new vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor you want to set up a bank account for.
1. On the Action Pane, open the **Vendor** tab and, from the **Set up** group,  select **Bank accounts**.
1. The **Vendor bank accounts** page opens. On the Action Pane, select **New** to create a new bank account.
1. Fill in all the required fields. Fields that will require approval are marked with **(requires approval)**. <!-- KFM: Does it matter whether I fill in "requires approval" fields or not? -->
1. When you are done creating the record, select **Save**.
1. On the Action Pane, select **Workflow \> Submit** to submit your new bank account details for approval.

## Update an existing vendor bank account record and submit it for approval

To use the web client to edit an existing vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor you want to update bank information for.
1. On the Action Pane, open the **Vendor** tab and, from the **Set up** group, select **Bank accounts**.
1. The **Vendor bank accounts** page opens. On the list pane, select the account you want to edit and then select **Edit** on the Action Pane.
1. Edit the fields as needed. Each field that will require approval to change is marked with **(requires approval)**.
1. When you are done editing the record, select **Save**.
1. If you have updated at least one field that requires approval, two additional buttons appear on the action pane: **Proposed changes** and **Workflow**.
    - To review your proposed changes, select **Proposed changes** on the Action Pane to open the **Proposed changes** page. From here, you can discard the proposed value for a field by selecting the **Discard** button next to the field in the list. To discard all changes, select the **Discard all changes** button at the bottom of the page. Select **OK** to close the page.
    - To submit your changes for approval, select **Workflow \> Submit** on the Action Pane. Your changes to protected fields won't be updated until an approver has approved them.

## Follow the approval status of a new or updated vendor bank account

When vendor bank account approval is enabled, vendor bank account records include a **Review status** field in the record header, where you can track the status of any changes you've submitted for the selected record. The following table lists the possible **Review status** values and their meanings.

| Review status | Description |
|---|---|
| Draft | A new bank account record has been created and has not been submitted for approval. |
| Approved | A new bank account account record has been approved. |
| Approved, changes not submitted | A previously approved bank account record has been changed but has not been yet submitted for approval. |
| Approved, pending changes | A previously approved bank account record has been changed and it has been submitted for the approval. |

## Approve a new or updated vendor bank account

Once submitted, the workflow follows the standard workflow process. The process directs approvers to the **Vendor bank accounts** page, where they can do the following actions:

- For updates to existing bank account records, approvers must select **Proposed changes** on the Action Pane to open the **Proposed changes** page. The approver reviews the changes and then selects **Workflow \> Approve** on the Action Pane to approve them. After all approvals are completed, the fields are updated with the values that you proposed.
- For new bank account records, approvers must open the record and then review the bank account details on the **Vendor bank accounts** page and then select **Workflow \> Approve** to approve the new record. After all approvals are completed, the bank account can be used.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]