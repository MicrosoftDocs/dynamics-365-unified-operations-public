---
# required metadata

title: Product readiness
description: This topics explains how you can use readiness checks to ensure that the required master data is completed for a product before it's used in transactions.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  EngChgReadinessPersonUserLookup, EngChgReadinessList_Assigned,EngChgProductReadinessPolicy, EngChgProductReadinessList, EngChgProductReadinessChecksInfo, EngChgProductReadinessChecks, EngChgProductReadinessCheckPart 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
---

# Product readiness

[!include [banner](../includes/banner.md)]

You can use readiness checks to ensure that all the required master data has been specified for a product before it's used in transactions. When readiness checks are used, a user or team is made responsible for validating specific predefined product-related data. If there is an open readiness check for a product, the product can't be released or used in transactions.

The **Active** check box for an engineering product, variant, or version is available only after all the required data has been entered and verified, and after all the readiness checks have been processed. At that point, the product, version, or variant can be released to other companies and used in transactions. You can create readiness checks for new products, new variants, and new engineering versions.

## Types of readiness checks

There are three types of readiness checks:

- **System check** – The system verifies whether there is a valid record. For example, the record might be an active bill of materials (BOM).
- **Manual check** – A user verifies whether the record is valid. For example, a readiness check might require validation of the default order settings. In some cases, such as when the product is still being designed and therefore won't be placed in stock, no default order settings are required. However, default order settings might be required for another product of the same type, because the product can be held in stock. The user is responsible for knowing how to correctly decision whether a readiness check is required.
- **Checklist** – The user answers a series of questions from a checklist, and the system determines whether the answers meet expectations. The checklist can have any subject. For example, it can be used to determine whether marketing materials or product documentation is completed.

## How readiness checks are created for a new product, variant, or version

When you create a new engineering **product**, the system determines whether a readiness check policy has been set up for the engineering product category. (Readiness check policies can be applied on the released product level, the released variant level, and the engineering version level.) If a policy has been set up, the following events occur:

- Readiness checks are created for the product, according to the applicable policy.
- The engineering version is set to inactive to block the product from being used. All the versions for the specific product that is involved are set to inactive.

If a new **variant** is created for a product, the system checks whether readiness checks have been set up on the engineering product category. (Readiness checks can be applied on released variant level and the engineering version level.) If a readiness check has been set up, the following events occur:

- Readiness checks are created for the product.
- The engineering version is set to inactive to block the product from being used.

If a new engineering **version** is created for a product, the system checks whether readiness checks have been set up on the engineering product category. (Readiness checks can be applied on the engineering version level.) If a readiness check has been set up, the following events occur:

- Readiness checks are created for the product.
- The engineering version is set to inactive to block the product from being used.

## View readiness checks

### View open readiness checks for a product or product version

To find the open readiness checks for a product, open the **Released products details** page. Then, on the Action Pane, on the **Product** tab, in the **Readiness checks** group, select **Readiness checks**.

To find the open readiness checks for a product version, open the **Product version** page. Then, in the **Checklist** group, select **Readiness checks**.

### View open readiness checks that are assigned to you

To view the open readiness checks that are assigned to you, follow one of these steps.

- Go to **Engineering change management \> Common \> Product readiness \> My open readiness checks**.
- Go to **Product information management \> Workspaces \> Product readiness for discrete manufacturing**.

The setup that specifies who a readiness check is assigned to is done for the engineering product category. Readiness checks can be assigned to a person or a team. If a readiness check is assigned to a team, there is one person on the team who must process the readiness check. For more information, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

## Process open readiness checks

### Process system and manual readiness checks

After you open the readiness page, you can view the subject of system and manual readiness checks by selecting **View related information** on the Action Pane. You can then complete and/or validate the data for the readiness check. Open readiness checks have a **Status** value of *Pending*. This status indicates that the readiness check must still be processed. To process a readiness check, follow one of these steps.

- On the Action Pane, select **Check/complete** to check and complete the readiness check. When you've finished, the **Status** field is updated to *Passed*.
- On the Action Pane, select **Skip** if you want to skip a readiness check that isn't mandatory. For example, you set up a readiness check for price calculations. However, you decide to skip this check while the product is still in the design phase. In this case, the **Status** field is updated to *Skipped*.

Depending on the configuration of the readiness policy, when the **Status** field for a readiness check is updated to *Passed*, an extra step might be required to approve the readiness check. In this case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all the open readiness checks for a new product, variant, or version have been processed and approved as required, the item automatically becomes active and therefore ready to use.

### Process checklist readiness checks

To open a checklist, open the readiness checks page, and then, on the Action Pane, select **Start checklist**. When you've completed the checklist, the system validates whether the readiness check is passed, based on the settings in the questionnaire. If the check is passed, the **Status** field is updated to *Passed*. If the readiness check isn't mandatory, you can skip it. In this case, the **Status** field is updated to *Skipped*.

Depending on the configuration of the readiness policy, when the **Status** field for a readiness check is updated to *Passed*, an extra step might be required to approve the readiness check. In this case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all the open readiness checks for a new product, variant, or version have been processed and approved as needed, the item automatically becomes active and therefore ready to use.

## Set up readiness checks

Because the types of data that must be verified typically vary by product type, you can assign different readiness rules to each engineering product category. (For more information, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).)

You can set up the readiness checks on the readiness policy. Select **Add system checks** to add system and manual readiness checks. Alternatively, select **Add existing questionnaire** to add a checklist. Then set the fields in the following table to complete the setup.

| Field | Description |
|---|---|
| Free text | You can enter a free-text description. |
| Apply check on | Select whether the readiness check should be created for each new released product, released variant, or engineering version. |
| Execute in | Select whether the readiness check applies to all companies or a single company. |
| Company | If you set the **Execute in** field to *Single company*, select the company. |
| Owner type | Select whether the readiness check is assigned to a person or a team. |
| Name | Select the person or team that the readiness check should be assigned to. |
| Questionnaire | Select the questionnaire that should be used for the checklist. The checklist is a local checklist in the company where the readiness check is done. The system must be able to evaluate whether the checklist is correctly answered. Therefore, the checklist must be set up so that an evaluation is done based on correct answers. For more information about how to create questionnaires, see [Using questionnaires](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/using-questionnaires) and its related topics. |
| Automatic approval | Select whether the readiness check should be set to approved when **Check/complete** is selected on the Action Pane. |
| Mandatory | Select whether the readiness check is mandatory, or whether it can be skipped. |

## Create and manage product readiness policies

Use product readiness policies to manage the readiness checks that apply to a product. Because a readiness policy is assigned to the engineering category, all the checks in the readiness policy apply to all the engineering products that are based on the engineering category.

Each readiness policy contains a set of readiness checks. When a readiness policy is assigned to an engineering product category, all the products that are created from that engineering product category will have the readiness checks that are indicated in the readiness policy.

To work with product readiness policies, go to **Engineering change management \> Setup \> Product readiness policies**. Then follow one of these steps.

- To create a new policy, select **New** on the Action Pane, and then set the fields as described in the following subsections.
- To edit an existing policy, select it in the list pane, select **Edit** on the Action Pane, and then set the fields as described in the following subsections.
- To delete an existing policy, select it in the list pane, select **Edit** on the Action Pane, and then, on the **General** FastTab, make sure that the **Active** option is set to *No*. Then select **Delete** on the Action Pane.

### Header

Set the following fields on the header of a product readiness policy.

| Field | Description |
|---|---|
| Name | Enter a name for the policy. |
| Description | Enter a description of the policy. |

### General FastTab

Set the following fields on the **General** FastTab of a product readiness policy.

| Field | Description |
|---|---|
| Product type | Select whether the policy applies to products of the *Item* or *Service* type. You can't change this setting after you save the record. |
| Active | Use this option to help maintain your release policies. Set it to *Yes* for all readiness policies that you use. Set it to *No* to mark a readiness policy as inactive when it isn't used. Note that you can't inactivate a readiness policy that is assigned to an engineering product category, and you can delete only inactive release policies. |

### Readiness control FastTab

For each type of readiness check that you want to include in the policy, add a row on the **Readiness control** FastTab. Use the following buttons on the **All products** FastTab to add and remove rows as you require:

- **Add check** – Add a standard readiness check to the policy. When you select this button, the **Add check** dialog box appears. There, you can select from a list of available checks.
- **Add existing questionnaire** – Add a blank row to the grid. You can then assign an existing questionnaire by setting the fields in the following table.
- **Copy** – Add a copy of the selected row to the grid.
- **Delete** – Delete the selected row from the grid.

For each row that you add, set the following fields.

| Field | Description |
| --- | --- |
| Process area | Select the area that the check is related to. |
| Type | Select whether the check is a system check, a manual check, or a checklist (questionnaire). |
| Name | If the check is a checklist, enter a name. For system and manual checks, this field is automatically set. |
| Description | If the check is a checklist, enter a description. For system and manual checks, this field is automatically set, and the description explains the focus of the check. |
| Apply checks on | Select whether the row should generate readiness checks in response to a new released product, released variant, or released version. |
| Execute in | Select whether readiness checks that the row generates apply to all companies or a single company. |
| Company | If you set the **Execute in** field to *Single company*, select the company. |
| Owner type | Select whether readiness checks that the row generates should be assigned to a person or a team. |
| Owner | Select the person or team that readiness checks that the row generates should be assigned to. |
| Questionnaire | Select the questionnaire that should be used for the checklist. The checklist is a local checklist in the company where the readiness check is done. The system must be able to evaluate whether the checklist is correctly answered. Therefore, the checklist must be set up so that an evaluation is done based on correct answers. For more information about how to create questionnaires, see [Using questionnaires](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/using-questionnaires) and its related topics. |
| Automatic approval | Readiness check records include an **Approved** check box that indicates the approval status. Select the **Automatic approval** check box for checks that should be set to approved immediately after the assigned user completes them. Clear this check box to require explicit approval as an extra step. |
| Mandatory | Select this check box for checks that must be completed by the assigned user. Mandatory checks can't be skipped. |
