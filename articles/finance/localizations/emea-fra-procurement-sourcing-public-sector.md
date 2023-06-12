---
title: Procurement and sourcing in the public sector in France
description: This article explains how the standard features that are related to procurement and sourcing are augmented for French entities in the public sector. These features are used to help meet the requirements of the Code des Marchés Publics.
author: brpotter
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Public sector
ms.search.form: AgreementClassification, PurchAgreement, SysPolicy
---

# Procurement and sourcing in the public sector in France

[!include [banner](../includes/banner.md)]

This article explains how the standard features that are related to procurement and sourcing are augmented for French entities in the public sector. These features are used to help meet the requirements of the Code des Marchés Publics. 

## Set spending thresholds by procurement category

To set spending thresholds for purchases in the procurement categories that are defined by the Clé de Contrôle Marché, you can use the **Spending thresholds by category** purchasing policy rule . By implementing this purchasing policy rule to control spending thresholds by category, you can use the effective date attributes, predicted expenditure amounts, and threshold amounts to support your procurement practices, and to help guarantee the efficient and effective use of public funds.

## Create tranches and lots
To create tranches and lots, you can create a hierarchy of parent and child purchase agreements. The child purchase agreements act as the tranches and lots of the parent purchase agreement. The purchase agreement hierarchy has some specific characteristics:

-   A user can view the parent purchase agreement, and can see the total activity of the parent and all its related child agreements. This feature provides a single management view for reviewing and controlling activity on purchase agreements.
-   Some values from the parent purchase agreement are automatically transferred to the child agreements. For example, policies that are related to competitive advertising can be assigned to the parent purchase agreement. Those policies then apply to all the child agreements that are related to that parent.
-   Purchase agreements can have a prime contractor, co-contractors, and subcontractors. The prime contractor can be assigned to the parent purchase agreement, and a co-contractor or subcontractor can be assigned to specific child agreements.

**Note:** If you've added lines to a purchase agreement, that purchase agreement can't be used as a parent agreement. The **Create child agreement** button will no longer be available. Likewise, if you've created a child purchase agreement, you can't add lines to the parent purchase agreement. To see the relationships among parent and child purchase agreements, use the **Purchase agreement tree** page.

## Set up purchase agreement access and limits
You can set up purchase agreements so that only approved departments have access to the agreement. You can also limit the amount that each department can spend against the purchase agreement. Users who try to exceed the maximum amount that is allocated for a department receive a message, and they are prevented from confirming the release or processing the invoice. Before you can use this capability, you must set the following parameters in the **General** section of the **Accounts payable parameters** page:

-   In the **Account structure** field, select the account structure to use on the **Purchase agreement department access** page to control access to purchase agreements. The account structure must include the financial dimension segment that you use to control access to purchase agreements.
-   In the **Financial dimension** field, select the financial dimension that you use to control access to purchase agreements. Most organization use the department dimension, but some organizations might restrict access to purchase agreements to different entities within their organizations.

## Manage information about subcontractors, certifications, and milestones on purchase agreements
You can create purchase agreement classifications that add administrative fields to the purchase agreements that use the classification.

-   To add information about subcontractors to purchase agreements, select the **Subcontractors** option on the purchase agreement classification.  Purchase agreements can have a prime contractor, co-contractors, and subcontractors. The prime contractor can be assigned to the parent purchase agreement, and a co-contractor or subcontractor can be assigned to specific child agreements.
-   To add information about certifications for vendors to purchase agreements, select the **Certifications** option on the purchase agreement classification. Certification information can be used to generate a report that lets you monitor vendor compliance with certification requirements.
-   To add information about milestones and tasks to purchase agreements, select the **Activities** option on the purchase agreement classification.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
