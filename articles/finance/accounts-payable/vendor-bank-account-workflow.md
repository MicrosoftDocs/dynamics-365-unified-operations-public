---
title: Vendor bank account workflow
description: This article describes how to set up vendor bank account approval.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: 
ms.search.form: VendBankAccount
ms.topic: how-to
ms.date: 02/15/2023
ms.custom: bap-template
---

# Vendor bank account workflow

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The vendor bank approval workflow ensures that bank data submitted by suppliers is secure, financially compliant, and protected against fraud. Businesses can evaluate and approve any incoming changes to a supplier's bank account information and make sure the provided bank details meet their organization's standards and policies. This helps reduce the risk of fraud by detecting and preventing unapproved changes.

The vendor bank approval workflow in Dynamics 365 Supply Chain Management ensures that bank data submitted by suppliers is secure, financially compliant, and protected against fraud. Businesses can evaluate and approve any incoming changes to a supplier's bank account information and make sure the provided bank details meet their organization's standards and policies. This helps reduce the risk of fraud by detecting and preventing unapproved changes. 

When you enable the vendor bank account workflow, any changes submitted for specific bank-details fields will be sent through the workflow for approval. You can configure approval triggers and decide whether to invoke the approval workflow when a supplier’s bank details are created, changed, or both. 

## Turn the feature on

To use the functionality described in this article, the **Vendor bank account change proposal workflow** feature must be turned on for your system. 

## Set up the vendor bank account workflow

Before you can use the workflow feature, you must enable it.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **General** tab, expand the **Vendor bank account approval** FastTab.
   - Set the **Bank account approval (create)** option to Yes to send changes to the workflow upon bank account record creation..
    - Set the **Bank account approval (update)** option to Yes to send changes to the workflow upon bank account record update.
1. In the **Data entity behavior** field, select the behavior that should be used when data is imported:

    - **Allow changes without approval** – The data entity can update the vendor bank account record without processing it through the workflow.
    - **Reject changes** – Changes can't be made to the vendor bank account record. The import will fail for the fields that are enabled for the workflow.
    - **Create change proposals** – All fields will be changed except the fields that are enabled for the workflow. The new values for those fields will be added to the vendor bank account as proposed changes, and the workflow will be started automatically.

1. In the list of vendor bank account fields, select the **IsEnabled** checkbox for every field that must be approved before the changes can be made.
1. Go to **Accounts payable \> Setup \> Accounts payable workflows**.
1. Select **New**.
1. Select **Workflow approval for proposed vendor change**. 
1. Set up the workflow so that it matches your approval process. The **Workflow approval for proposed vendor bank account change** workflow approval element will apply the changes to the vendor bank accounts.

To use the web client to add a new vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. On the Action pane, select **Vendor** tab and select **Bank accounts** option in the **Set up** section.
1. Select New to create a new bank account.
1. Fill in all required fields and select **Save**.
1. Select **Workflow \> Submit**
1. The workflow follows the standard workflow process. The approver can review the bank account details and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the bank account can be used.

## Update an existing vendor bank account record and submit it for approval

When you change a field that is enabled for the workflow, the **Proposed changes** page appears. This page shows the original value of the field and the new value that you entered. The field that you changed is reverted to its original value. A status message will inform you that your changes haven't been submitted. 

Every time that you change a field that is enabled for the workflow, that field is added to the list on the **Proposed changes** page. To discard the proposed value for a field, use the **Discard** button next to the field in the list. To discard all changes, use the **Discard all changes** button at the bottom of the page. Select **OK** to close the page.

## Follow the approval status of a new or updated vendor bank account

When vendor bank account approval is enabled, vendor bank account records include a **Review status** field in the record header, where you can track the status of any changes you've submitted for the selected record. The following table lists the possible **Review status** values and their meanings.

The workflow follows the standard workflow process. The approver is directed to the **Vendor bank accounts** page where the changes can be reviewed on the **Proposed changes** page and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the fields are updated with the values that you proposed.

When vendor bank account approval is enabled, vendor bank accounts move through  4 review statuses, from *Draft* to *Approved*. 

| Review status | Description       | |
|-----------------|----------------------------------------------------------------------------------|---------------------------|
| Draft           | Bank account record has been created and has not been submitted for approval.     | 
| Approved        | Bank account record has been approved.       |
| Approved, changes not submitted        | Previously approved bank account record has been changed but has not been yet submitted for approval.                                 | 
| Approved, pending changes        | Changed bank account record has been submitted for the approval.                                                             | 

- For updates to existing bank account records, approvers must select **Proposed changes** on the Action Pane to open the **Proposed changes** page. The approver reviews the changes and then selects **Workflow \> Approve** on the Action Pane to approve them. After all approvals are completed, the fields are updated with the values that you proposed.
- For new bank account records, approvers must open the record and then review the bank account details on the **Vendor bank accounts** page and then select **Workflow \> Approve** to approve the new record. After all approvals are completed, the bank account can be used.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
