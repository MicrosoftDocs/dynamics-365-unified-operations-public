---
# required metadata

title: Product readiness
description: Use readiness checks to ensure that the needed master data is completed for a product before it is used in transactions.
author: XXXX
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

Use readiness checks to ensure that the needed master data is completed for a product before it is used in transactions. With a readiness check, a user or team is made responsible to validate certain (pre-defined) product related data. When there is an open readiness check, the product cannot be released nor used in transactions. Only when all the data is completed and verified and the readiness checks are processed, the active check mark on the engineering version of the product is enabled, which makes the version ready to be used; it can be released to other companies and used in transactions. Readiness checks can be created for new products, new variants and new engineering versions.

## Types of readiness checks

There are three types of readiness checks:

- System checks: The system will verify if there is a valid record. As an example, if there is an active Bill of Material.
- Manual checks: The user will verify if there is a valid record. As an example, the default order settings must be validated. Based on the product in its phase, the situation can occur that there are no default order settings needed. As an example, while the product is still being designed and will not be put on stock yet. For another product of the same type however, the default order settings are required while it can be held on stock. The responsibility and knowledge to make the correct judgement lies with the user.
- Checklist: Via a checklist, the user will answer questions of the checklist and the system will verify if the answers meet the expectations. The subject can be anything like if marketing material or product documentation is completed.

## Creation of readiness checks

When creating a new engineering product, the system will verify if readiness checks are set up on the engineering product type **applicable on released product level, released variant level and engineering version level**. If this is the case, two things will happen:

- Readiness checks are created for the product
- The engineering version is not active. This will block the products from being used

In case a new variant is created for the product, the system will verify if readiness checks are setup on the engineering product type **applicable on released variant level and engineering version level**. If this is the case, two things will happen:

- Readiness checks are created for the product
- The engineering version is not active. This will block the products from being used

In case a new engineering version is created for the product, the system will verify if readiness checks are setup on the engineering product type **applicable engineering version level**. If this is the case, two things will happen:

- Readiness checks are created for the product
- The engineering version is not active. This will block the products from being used

## Viewing readiness checks

You can find the menu item for opening the readiness checks for a product on the **Released products details** page. For the readiness checks assigned to an engineering version, you can open them from the **engineering version** page.

For open readiness checks assigned to you, you can open the **My open readiness checks** page on the menu and on the Product readiness for discrete manufacturing **workspace**. The setup for who is assigned to the readiness check is done at the engineering product type. It can be a person or a team. In case a team is assigned, there is one person of the team that needs to process the readiness check.

## Processing readiness checks

### Processing system and manual readiness checks

If you have opened the readiness form, you can view de subject of the system and manual readiness checks via the **View related information** option in the action pane. This will provide the option to complete and/ or validate the data for the readiness check. When the readiness check has the status pending, the readiness check is still open, and it needs to be processed. This can be done via the following options:

- Via the option **Check/ complete** in the action pane, the readiness check can be checked/ completed and the status is updated to passed.
- Via the option **Skip** in the action pane, the readiness check can be skipped in case it is not mandatory. This can be applicable when there is no data setup which is also not required for the particular product. This can be the case for the cost price calculation for a product that is still in design. The status is updated to skipped.

In case the readiness check is updated to status passed, it depends on the settings on the engineering product type, if the approval of the readiness check needs to be done as a separate step. In case it is not automatically approved, this needs to be done an additional step. In that case, click on **Approval** to complete the readiness check. The approval checkmark is set. This approval step is always mandatory when the readiness check is skipped.

In case there are no more open readiness checks, the engineering version becomes active and therefor ready for use automatically.

### Processing checklist readiness checks

The checklist opens by clicking on **Start checklist** in the action pane. When the checklist is completed, the system will validate if the readiness check is completed based on the settings in the questionnaire and if so, the status is updated to passed. In case the readiness check is not mandatory, it can be skipped, and the status is also updated to skipped.

In case the readiness check is updated to status passed, it depends on the settings on the engineering product type, if the approval of the readiness check needs to be done as a separate step. In case it is not automatically approved, this needs to be done an additional step. In that case, click on **Approval** to complete the readiness check. The approval checkmark is set. This approval step is always mandatory when the readiness check is skipped.

## Setup readiness checks

The types of data to be verified, can be different per type of product and therefor the readiness rules can be different per engineering product type. For more information, see ……

On the fast tab Readiness control of the engineering product type, you can setup the readiness checks. Click on **Add system checks** to add system and manual readiness checks. Click on **Add existing questionnaire** to adda checklist. Complete the rest of the fields to finish the setup:

| **Setting** | Description |
| --- | --- |
| **Free text** | A free text description can be added |
| **Apply check on** | Should this readiness check be created per new released product, new released variant or new engineering version |
| **Execute in** | Is the readiness check applicable for all companies or a single company |
| **Company** | In case a single company is chosen, you must specify the company here |
| **Owner type** | Select if the readiness check is assigned to a person or a team |
| **Name** | Select the person or team to whom the check must be assigned |
| **Questionnaire** | Select the questionnaire which should be used for the checklist. This is a local checklist in the company for the readiness check. It must be setup with an evaluation based on correct answers, so the system can evaluate if the checklist is correctly answered. |
| **Automatic approval** | Will check/ complete also set the readiness check to Approved? |
| **Mandatory** | Is the readiness check mandatory or can it be skipped? |

## Readiness policy

To manage the readiness checks that apply to a product, the product readiness policies are used.

The readiness policies contains a set of readiness checks. When the readiness policy is associated to an engineering product category, all the products created from that engineering product category will have the readiness checks indicated in the readiness policy.