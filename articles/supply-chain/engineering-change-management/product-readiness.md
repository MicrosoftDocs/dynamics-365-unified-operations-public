---
title: Product readiness
description: Learn how you can use readiness checks to ensure that the required master data is completed for a product before it's used in transactions.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 09/28/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  EngChgReadinessPersonUserLookup, EngChgReadinessList_Assigned,EngChgProductReadinessPolicy, EngChgProductReadinessList, EngChgProductReadinessChecksInfo, EngChgProductReadinessChecks, EngChgProductReadinessCheckPart 
---

# Product readiness

[!include [banner](../includes/banner.md)]

You can use readiness checks to help ensure that all the required master data has been specified for a product before it's used in transactions. When readiness checks are used, a user or team is made responsible for validating specific predefined product-related data.

You can mark the **Active** check box for an engineering product, variant, or version after all the required data has been entered and verified, and after all the readiness checks have been processed. If one or more checks haven't been processed for the product, version, or variant, then when you try to mark the **Active** check box, you will receive a prompt warning you that not all checks have been completed.

You can create readiness checks for new engineering products, variants, and versions. You can also apply readiness checks to standard (non-engineering) products (see also [Readiness checks on standard products](#standard-products)). 

You can use standard products in transactions even though not all readiness checks have been completed. If you need to block a product from being used in transactions, use its lifecycle state. You can assign a lifecycle state that blocks a product from being used in transactions and then, after all readiness checks have been completed, assign a new lifecycle state that allows the required transactions.

## Types of readiness checks

There are three types of readiness checks:

- **System check** – The system verifies whether there is a valid record. For example, the record might be an active bill of materials (BOM).
- **Manual check** – A user verifies whether the record is valid. For example, a readiness check might require validation of the default order settings. In some cases, such as when the product is still being designed and therefore won't be placed in stock, no default order settings are required. However, default order settings might be required for another product of the same type, because the product can be held in stock. The user is responsible for knowing how to correctly decision whether a readiness check is required.
- **Checklist** – The user answers a series of questions from a checklist, and the system determines whether the answers meet expectations. The checklist can have any subject. For example, it can be used to determine whether marketing materials or product documentation is completed.

<a name="checks-engineering"></a>

## How readiness checks are created for a new engineering product, variant, or version

Readiness check policies can be applied at the released product level, the released variant level, and the engineering version level.

When you create a new *engineering product*, the system determines whether a [readiness check policy applies](#assign-policy) to it. If a readiness check policy applies, the following events occur:

- Readiness checks are created for the product, according to the applicable policy.
- The engineering version is set to inactive to block the product from being used. All engineering versions for the product are set to inactive.

If a new *variant* is created for a product, the system checks whether a readiness check policy applies to it. (Readiness checks can be applied at the released variant level and the engineering version level.) If a policy applies, the following events occur:

- Readiness checks are created for the product, according to the applicable policy.
- The engineering version and variant are set to inactive to block the product from being used.

If a new engineering *version* is created for a product, the system checks whether a readiness check policy applies to it. (Readiness checks can be applied at the engineering version level.) If a policy applies, the following events occur:

- Readiness checks are created for the product, according to the applicable policy.
- The engineering version is set to inactive to block the product from being used.

> [!NOTE]
> You can also set up readiness check policies for standard (non-engineering) products. For more information, see the [Readiness checks on standard products](#standard-products) section later in this article.

## View readiness checks

### View open readiness checks for a product or product version

To find the open readiness checks for a product, open the **Released products details** page. Then, on the Action Pane, on the **Product** tab, in the **Readiness checks** group, select **Readiness checks**.

To find the open readiness checks for a product version, open the **Engineering versions** page for a released product and choose a version. Then, on the Action Pane, on the **Product** tab, in the **Checklist** group, select **Readiness checks**.

### View open readiness checks that are assigned to you

To view the open readiness checks that are assigned to you, follow one of these steps.

- Go to **Engineering change management \> Common \> Product readiness \> My open readiness checks**.
- Go to **Product information management \> Workspaces \> Product readiness for discrete manufacturing**.

The setup that specifies who a readiness check is assigned to is done for the readiness policy. Readiness checks can be assigned to a person or a team. If a readiness check is assigned to a team, there is one person on the team who must process the readiness check.

## Process open readiness checks

### Process system and manual readiness checks

After you open the **Readiness checks** page, you can view the subject of system and manual readiness checks by selecting **View related information** on the Action Pane. You can then complete and/or validate the data for the readiness check. Open readiness checks have a **Status** value of *Pending*. This status indicates that the readiness check must still be processed. To process a readiness check, follow one of these steps.

- On the Action Pane, select **Check/complete** to review and complete the readiness check. When you've finished, the **Status** field is updated to *Passed*.
- On the Action Pane, select **Skip** if you want to skip a readiness check that isn't mandatory. For example, you set up a readiness check for price calculations. However, you decide to skip this check while the product is still in the design phase. In this case, the **Status** field is updated to *Skipped*.

Depending on the configuration of the readiness policy, when the **Status** field for a readiness check is updated to *Passed*, an extra step might be required to approve the readiness check. In this case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all the open readiness checks for a new product, variant, or version have been processed and approved as required, the item automatically becomes active and therefore ready to use.

### Process checklist readiness checks

To open a checklist, open the **Readiness checks** page, and then, on the Action Pane, select **Start checklist**. When you've completed the checklist, the system validates whether the readiness check is passed, based on the settings in the questionnaire. If the check is passed, the **Status** field is updated to *Passed*. If the readiness check isn't mandatory, you can skip it. In this case, the **Status** field is updated to *Skipped*.

Depending on the configuration of the readiness policy, when the **Status** field for a readiness check is updated to *Passed*, an extra step might be required to approve the readiness check. In this case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all the open readiness checks for a new product, variant, or version have been processed and approved as needed, the item automatically becomes active and therefore ready to use.

## Create and manage product readiness policies

Use product readiness policies to manage the readiness checks that apply to a product. Each readiness policy contains a set of readiness checks. When a readiness policy is assigned to an engineering product category or a shared product, all the products that are related to that category or shared product will have the readiness checks that are included in the readiness policy.

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
| Active | Use this option to help maintain your readiness policies. Set it to *Yes* for all readiness policies that you use. Set it to *No* to mark a readiness policy as inactive when it isn't used. Note that you can't inactivate a readiness policy that is assigned to an engineering product category or a shared product, and you can delete only inactive release policies. |

### Readiness control FastTab

For each type of readiness check that you want to include in the policy, add a row on the **Readiness control** FastTab. Use the following buttons on the FastTab toolbar to add and remove rows as you require:

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
| Questionnaire | Select the questionnaire that should be used for the checklist. The checklist is a local checklist in the company where the readiness check is done. The system must be able to evaluate whether the checklist is correctly answered. Therefore, the checklist must be set up so that an evaluation is done based on correct answers. For more information about how to create questionnaires, see [Using questionnaires](/dynamicsax-2012/appuser-itpro/using-questionnaires) and its related articles. |
| Automatic approval | Readiness check records include an **Approved** check box that indicates the approval status. Select the **Automatic approval** check box for checks that should be set to approved immediately after the assigned user completes them. Clear this check box to require explicit approval as an extra step. |
| Mandatory | Select this check box for checks that must be completed by the assigned user. Mandatory checks can't be skipped. |

<a name="assign-policy"></a>

## Assign readiness policies to standard and engineering products

When you create a new product based on an engineering category, you create both a *released product* and a related *shared product*. The way that readiness policies are resolved for a released product depends on whether the *Product readiness checks* feature is turned on for your system (see the [Readiness checks on standard products](#standard-products) section later in this article for details about this feature and how to turn it on or off).

- When the *Product readiness checks* feature is turned *off* on your system, the readiness policy is set and shown only on [engineering category](engineering-versions-product-category.md) records. To learn which policy applies to a released product, the system checks the **Product readiness policy** field for the related engineering category. You can change the readiness policy for an existing product by editing the related engineering category (not the shared product).
- When the *Product readiness checks* feature is turned *on*, it adds a **Product readiness policy** field to the **Product** page (where shared products are set up) and to the **Released product** page (where the value is read-only and is taken from the related shared product). The system finds the readiness policy for a released product by checking the related shared product. When you use an engineering category to create a new engineering product, the system creates both a shared product and a released product, and copies any **Product readiness policy** setting for the engineering category to the new shared product. You can then change the readiness policy for an existing product by editing the related shared product (not the released engineering category).

To assign a readiness policy to a shared product, follow these steps.

1. Go to **Product information \> Products \> Products**.
1. Open or create the product that you want to assign a readiness policy to.
1. On the **General** FastTab, set the **Product readiness policy** field to the name of the policy that should apply to the product.

To assign a readiness policy to an engineering category, follow these steps.

1. Go to **Engineering change management \> Setup \> Engineering product category details**.
1. Open or create the engineering category that you want to assign a readiness policy to.
1. On the **Product readiness policy** FastTab, set the **Product readiness policy** field to the name of the policy that should apply to the engineering category.

<a name="standard-products"></a>

## Readiness checks on standard products

You can enable product readiness checks for standard (non-engineering) products by turning on the *Product readiness checks* feature in Feature management. This feature makes a few small changes to the readiness check system so that it supports standard products.

### Enable or disable readiness checks on standard products

This feature requires that both the *Engineering Change Management* and *Product readiness checks* features be turned on for your system. For details about how to turn these features on or off, see [Engineering change management overview](product-engineering-overview.md).

### Create readiness policies for standard products

You create readiness policies for standard products just as you do for engineering products. See the information earlier in this article.

### Assign readiness policies to standard products

To assign a readiness policy to a standard product, open the related shared product, and set the **Product readiness policy** field to the name of the policy that should apply. For more information, see the [Assign readiness policies to standard and engineering products](#assign-policy) section earlier in this article.

### View and process readiness checks on standard products

When this feature is turned on, you view and process readiness checks for standard products just as you do for engineering product. See the information earlier in this article.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
