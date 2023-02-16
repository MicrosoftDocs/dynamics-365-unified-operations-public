---
title: Vendor bank account workflow
description: This article describes how to set up vendor bank account approval.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: 
ms.search.form: VendBankAccount
ms.topic: how-to
ms.date: 02/12/2023
ms.custom: bap-template
---

# Vendor bank account workflow

[!include [banner](../includes/banner.md)]

The vendor bank approval workflow in Dynamics 365 Supply Chain Management ensures that bank data submitted by suppliers is secure, financially compliant, and protected against fraud. Businesses can evaluate and approve any incoming changes to a supplier's bank account information and confirm the provided bank details meet their organization's standards and policies. This helps reduce the risk of fraud by detecting and preventing unapproved changes. 

When you enable the vendor bank account workflow, any changes submitted for specific bank-details fields will be sent through the workflow for approval. You can configure approval triggers and decide whether to use approval workflow when a supplier’s bank details are created, changed, or both. 

To use the functionality described in this article, the **Vendor bank account change proposal workflow** feature must be enabled. 

## Set up the vendor bank account workflow

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2. On the **General** tab, the **Vendor bank account approval** FastTab.
   - Set the **Bank account approval (create)** option to **Yes** to send changes to the workflow when bank account records are created.
   - Set the **Bank account approval (update)** option to **Yes** to send changes to the workflow when bank account records are update.
3. In the **Data entity behavior** field, select the option to be used when data is imported:
    - **Allow changes without approval** – The data entity can update the vendor bank account record without workflow.
    - **Reject changes** – Changes can't be made to the vendor bank account record. The import will fail for the fields that are enabled for the workflow.
    - **Create change proposals** – All fields will be changed except the fields that are enabled for the workflow. The new values for those fields will be added to the vendor bank account as proposed changes, and the workflow will be started automatically.

4. In the list of vendor bank account fields, select the **Is enabled** checkbox for every field that must be approved before changes can be made.
5. Go to **Accounts payable \> Setup \> Accounts payable workflows**, select **New**.
6. Select **Workflow approval for proposed vendor change**. 
7. Set up the workflow to match the approval process. The **Workflow approval for proposed vendor bank account change** workflow approval element will apply the changes to the vendor bank accounts.

To use the web client to add a new vendor bank account and submit it to the workflow for approval, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
2. On the Action pane, select **Vendor** tab and select **Bank accounts** in the **Set up** section.
3. Select **New** to create a new bank account and fill in the required fields
4. Select **Save**.
5. Select **Workflow \> Submit**

The workflow follows the standard workflow process. The approver can review the bank account details and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the bank account can be used.

## Change vendor bank account information and submit the changes to the workflow

When you change a field that is enabled for workflow, the **Proposed changes** page is available. This page displays the original value of the field and the new value that you entered. The field that you changed is reverted to its original value. A status message will inform you that your changes haven't been submitted. 

Every time that you change a field that is enabled for the workflow, that field is added to the **Proposed changes** page. To discard the proposed value for a field, click **Discard**. To discard all changes, click **Discard all changes**. Select **OK** to close the page.

After you have at least one proposed change, two additional tabs appear on the action pane: **Proposed changes** and **Workflow**.

1. Select **Proposed changes** to open the **Proposed changes** page and review your changes.
2. Select **Workflow \> Submit**.

The workflow follows the standard workflow process. The changes can be reviewed on the **Proposed changes** page. Select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the fields are updated with the proposed values.

When vendor bank account approval is enabled, vendor bank accounts move through the following review statuses: 

| Review status | Description       | 
|-----------------|----------------------------------------------------------------------------------|
| **Draft**           | Bank account record has been created and hasn't been submitted for approval.     | 
| **Approved**        | Bank account record has been approved.       |
| **Approved, changes not submitted**        | Previously approved bank account record has been changed but hasn't been submitted for approval.       | 
| **Approved, pending changes**        | Changed bank account record has been submitted for the approval.                           | 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
