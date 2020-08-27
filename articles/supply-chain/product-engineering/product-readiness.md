---
# required metadata

title: Product readiness
description: Use readiness checks to ensure that the needed master data is completed for a product before it is used in transactions.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Product readiness

[!include [banner](../includes/banner.md)]

Use readiness checks to ensure that all the required master data has been specified for a product before it can be used in a transaction. With a readiness check, a user or team is made responsible to validate certain (pre-defined) product related data. When there is an open readiness check for a product, that product can't be released or used in transactions.

The **Active** check box for an engineering product, variant, or version is only enabled after all the required data has been entered and verified, and all the readiness checks have been processed. Only then can it be released to other companies and used in transactions. You can create readiness checks for new products, new variants and new engineering versions.

## Types of readiness checks

There are three types of readiness checks:

- **System checks**: The system verifies whether there is a valid record. For example, if there is an active bill of materials.
- **Manual checks**: A user verifies whether there the record is valid. For example, a readiness check may require the default order settings to be be validated. It can sometimes occur that no default order settings are actually needed, such as while the product is still being designed and therefore won't be placed in stock. However, for another product of the same type, the default order settings are required because it can be held in stock. The responsibility and knowledge to make the correct judgement lies with the user.
- **Checklist**: The user will answer a series of questions from a checklist and the system will verify whether the answers meet expectations. The subject can be anything, such as whether marketing material or product documentation is completed.

## How readiness checks are created for a new product, variant, or version

When you create a new engineering product, the system will check whether there is a readiness check policy set up on the engineering product category (applicable on released product level, released variant level, and engineering version level). If this is the case, the following things occur:

- Readiness checks are created for the product according to the applicable policy.
- The engineering version is set to inactive, which blocks the product from being used. All the versions for the specific product will be set to inactive.

If a new variant is created for a product, the system will check whether readiness checks are set up on the engineering product category (applicable on released variant level and engineering version level). If this is the case, the following things occur:

- Readiness checks are created for the product.
- The engineering version is set to inactive, which blocks the product from being used.

If a new engineering version is created for a product, the system will check whether readiness checks are set up on the engineering product category (applicable on engineering version level). If this is the case, the following things occur:

- Readiness checks are created for the product.
- The engineering version is set to inactive, which blocks the product from being used.

## View readiness checks

### View open readiness checks for a product or product version

To find the open readiness checks for a product, open its **Released products details** page. On the Action Pane, open the **Product** tab and, from the **Readiness checks** group, select **Readiness checks**. Or, from the **Product version** page, select **Readiness checks** from the group **Checklist**. <!-- KFM: Where can we find it? What is it called? BNG updated. KFM: The last sentence should name the tab. -->. 

### View open readiness checks assigned to you

To see the open readiness checks assigned to you, do one of the following:

- Go to **Project Oaktree \> Common \> Product readiness \> My open readiness checks**.
- Go to  **Product information management \> Workspaces \> Product readiness for discrete manufacturing**. <!-- KFM: Where do I find my readiness checks here? -->

The setup for who is assigned to the readiness check is done at the engineering product category. It can be a person or a team. In case a team is assigned, there is one person of the team that needs to process the readiness check. <!-- KFM: How do we make this assignment? We should probably describe this in the topic about creating categories and refer to that from here. BNG agree-->

## Process open readiness checks

<!-- KFM: This section should probably be replaced with a procedure that describes explicitly how to do these things. Both of the subsections here could be combined into a single procedure (they mostly repeat). -->

### Process system and manual readiness checks

After opening the readiness form, you can view the subject of system and manual readiness checks by selecting **View related information** on the Action Pane. From there, you can complete and/or validate the data for the readiness check. Open readiness checks have a **Status** of *Pending*, which means that it still needs to be processed. To process a readiness check, do one of the following:

- Select **Check/complete** on the Action Pane to check and complete the readiness check, after which the **Status** will update to *Passed*.
- Select **Skip** in the action pane if you prefer to skip a check that isn't mandatory. For example, you might set up a readiness check for price calculations, but while the product is still in the design phase, you could choose to skip this check. If you choose this option, the **Status** will update to *Skipped*.

Depending on how the readiness policy is configured, when a readiness check **Status** updates to *Passed*, an extra step may be required to approve the readiness check. In that case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all of the open readiness checks for new product, variant, or version have been processed and approved as needed, the item becomes active and therefore ready for use automatically.

### Process checklist readiness checks

To open a checklist, start by opening the readiness checks page and then select **Start checklist** on the Action Pane. When you have finished working through the checklist, the system will validate whether the readiness check is passed based on the settings in the questionnaire and, if so, the **Status** will update to *Passed*. If the readiness check isn't mandatory, you can instead choose to skip it, in which case the **Status** will update to *Skipped*.

Depending on how the readiness policy is configured, when a readiness check **Status** updates to *Passed*, an extra step may be required to approve the readiness check. In that case, select **Approval** to complete the readiness check. This approval step is always mandatory when the readiness check is skipped.

When all of the open readiness checks for a new product, variant, or version have been processed and approved as needed, the item becomes active and therefore ready for use automatically.

## Set up readiness checks

Because the types of data to be verified typically vary by product type, you can assign different readiness rules to each engineering product category (see also [Engineering versions and engineering product categories](engineering-versions-product-category.md)).

<!-- KFM: I can't find any of settings described here--it seems like all I can do is select a "readiness policy". Does the system still work like this? BNG readiness policy yes. KFM: I'm not sure where we are here (I don't have access to the feature right now); is this section accurate for the current product? -->

On the readiness policy, you can set up the readiness checks. Select **Add system checks** to add system and manual readiness checks. Select **Add existing questionnaire** to add a checklist. Complete the rest of the fields to finish the setup:

| **Setting** | Description |
| --- | --- |
| **Free text** | A free text description can be added |
| **Apply check on** | Should this readiness check be created per new released product, new released variant or new engineering version |
| **Execute in** | Is the readiness check applicable for all companies or a single company |
| **Company** | In case a single company is chosen, you must specify the company here |
| **Owner type** | Select if the readiness check is assigned to a person or a team |
| **Name** | Select the person or team to whom the check must be assigned |
| **Questionnaire** | Select the questionnaire which should be used for the checklist. This is a local checklist in the company for the readiness check. It must be set up with an evaluation based on correct answers, so the system can evaluate if the checklist is correctly answered. <!-- KFM: We should provide detailed instructions for how to set up the checklist. BNG this is standard, not only for product engineering, should not be the focus of this topic. KFM: I found this in the AX2012 docs: https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/using-questionnaires. Should we link to that?-->|
| **Automatic approval** | Will check/ complete also set the readiness check to Approved? |
| **Mandatory** | Is the readiness check mandatory or can it be skipped? |

## Create and manage product readiness policies

Use product readiness policies to manage the readiness checks that apply to a product. The readiness policy is assigned to the engineering category, so all the checks in the readiness policy will apply to the engineering products based on the engineering category.

Each readiness policy contains a set of readiness checks. When the readiness policy is associated to an engineering product category, all the products created from that engineering product category will have the readiness checks indicated in the readiness policy.

To work with product readiness policies, go to **Project Oaktree \> Setup \> Product readiness policies**. Then do one of the following:

- To create a new policy, select **New** from the Action Pane and then make settings as described in the following subsections.
- To edit an existing policy, select it from the list pane, select **Edit** on the Action Pane, and then make settings as described in the following subsections.
- To delete an existing policy, select it from the list pane. Select **Edit** on the Action Pane and, on the **General** FastTab, set **Active** to *No* if it isn't already. Then select **Delete** on the Action Pane.

### Settings in the header

Make the following settings in the header of a product readiness policy:

| Setting | Description |
| --- | --- |
| **Name** | Enter a name for the policy. |
| **Description** | Enter a description of the policy. |

### The General FastTab

The following table describes the settings available on **General** FastTab of a product readiness policy.

| Setting | Description |
| --- | --- |
| **Product type** |  Select if the policy will apply to products of type *Item* or *Service*. You can't change this setting after saving the record. |
| **Active** | Use this setting to help maintain your release policies. Set this to *Yes* for all readiness policies that you use; set it to *No* to mark a readiness policy as inactive when it is not used. Note that you can't deactivate a readiness policy that is assigned to an engineering product category, and you can only delete inactive release policies. |

### The Readiness control FastTab

Add a row on the **Readiness control** FastTab for each type of readiness check that you want to include in the policy. Use the following buttons in the **All products** FastTab to add and remove rows as needed:

- **Add check** - Adds a standard readiness check to the policy. Select this to open the **Add check** dialog box, which lists the available checks that you can choose from. <!-- KFM: Where does this list come from? Can we add more here? Should we describe each of the (default) checks shown here? BNG it is a finite list that comes out of the box, it has a relevant -->
- **Add existing questionnaire** - Adds a new blank row to the grid, which you can use to assign an existing questionnaire using the settings listed in the following table.
- **Copy** - Adds a copy of the selected row to the grid.
- **Delete** - Deletes the selected row from the grid.

For each row you add, make the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Process area** | Select the area the check is related to. |
| **Type** | Select a check type (system check, manual check or checklist (questionnaire)) |
| **Name** | For checklists, enter a name. This field is populated automatically for system and manual checks. |
| **Description** | For checklists, enter a description. For system or manual checks, it is populated automatically and explains the focus of the check. |
| **Apply checks on** | Choose whether this row will generate readiness checks in response to a new *Released product*, *Released variant*, or *Released version*. |
| **Execute in** | Choose whether readiness checks generated by this row apply to *All companies*, or to just a *Single company*. |
| **Company** | If you set **Execute in** to *Single company*, then select the applicable company here. |
| **Owner type** | Choose whether readiness checks generated by this row should be assigned to a *Team* or to an individual *Person*. |
| **Owner** | Choose the person or team who will be assigned readiness checks generated by this row (depending on the **Owner type**). |
| **Questionnaire** | Select the questionnaire which should be used for the checklist. This is a local checklist in the company for the readiness check. It must be set up with an evaluation based on correct answers, so the system can evaluate if the checklist is correctly answered. <!-- KFM: We should provide detailed instructions for how to set up the checklist. BNG is using the standard questionnaires, this should be a separate topic, not related to product engineering. KFM: Maybe link to: https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/using-questionnaires --> |
| **Automatic approval** |  Readiness check records include an **Approved** check box, which indicates approval status. Select this check box for checks that should be set to approved immediately after the assigned user has completed them. Clear this box to require explicit approval as an extra step. |
| **Mandatory** | Select this check box for checks that must be completed by the assigned user (can't be skipped). Mandatory checks can't be skipped. |
