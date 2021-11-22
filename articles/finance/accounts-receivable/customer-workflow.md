---
# required metadata

title: Customer workflow
description: This topic provides information about the customer workflow. You change specific fields for a customer and then send those changes for approval by using the workflow before they are added to the customer.
author: abruer
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4

---

# Customer workflow

[!include [banner](../includes/banner.md)]

The customer workflow has been added to version 8.0.4. You can change specific fields for a customer and then send those changes for approval by using the workflow before they are added to the customer.

## Set up the customer workflow

Before you can use the customer workflow feature, you must enable it.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
2. On the **General** tab, on the **Customer approval** FastTab, set the **Enable customer approvals** option to **Yes** to enable the feature.
3. In the **Data entity behavior** field, select the behavior that the data entities should use when data is imported:

    - **Allow changes without approval** – An entity can update the customer record without processing it through the workflow.
    - **Reject changes** – Changes can't be made to the customer record. The import will fail for the fields that are enabled for the workflow.
    - **Create change proposals** – All fields will be changed except the fields that are enabled for the workflow. The new values for those fields will be added to the customer as proposed changes, and the workflow will be started automatically.

4. In the list of customer fields, select then **Enable** check box for every field that must be approved before the changes can be made.
5. Go to **Accounts receivable \> Setup \> Accounts receivable workflows**.
6. Select **New**.
7. Select **Proposed customer change workflow**. 
8. Set up the workflow so that it matches your approval process. The **Workflow approval for proposed customer change** workflow approval element will apply the changes to the customer.

## Change customer information and submit the changes to the workflow

When you change a field that is enabled for the workflow, the **Proposed changes** page appears. This page shows the original value of the field and the new value that you entered. The field that you changed is reverted to its original value. A status message on the page informs you that your changes haven't been submitted.

Every time that you change a field that is enabled for the workflow, that field is added to the list of proposed changes. To discard the proposed value for a field, use the **Discard** button next to the field in the list. To discard all changes, use the **Discard all change** button at the bottom of the page. Select **OK** to close the page.

After you have at least one proposed change, two additional menus appear on the Action Pane: **Proposed changes** and **Workflow**.

1. Select **Proposed changes** to open the **Proposed changes** page and review your changes.
2. Select **Workflow \> Submit** to submit the changes to the workflow.

    The status on the page is changed to **Changes pending approval**.

The workflow follows the standard workflow process in the application. The approver is directed to the **Customer** page where the changes can be reviewed on the **Proposed changes** page and then select **Workflow \> Approve** to approve the workflow. After all approvals are completed, the fields are updated with the values that you proposed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
