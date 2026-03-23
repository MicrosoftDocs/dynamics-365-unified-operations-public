---
title: Procurement and sourcing in the public sector in France
description: Learn how the standard features that are related to procurement and sourcing are augmented for French entities in the public sector.
author: brpotter
ms.author: brpotter
ms.topic: how-to
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form: AgreementClassification, PurchAgreement, SysPolicy
ms.custom: 
  - bap-template
---

# Procurement and sourcing in the public sector in France

[!include [banner](../../includes/banner.md)]

This article explains how French entities in the public sector can use standard features related to procurement and sourcing. Use these features to help meet the requirements of the Code des Marchés Publics.

## Set spending thresholds by procurement category

Use the **Spending thresholds by category** purchasing policy rule to set spending thresholds for purchases in the procurement categories that the Clé de Contrôle Marché defines. By implementing this purchasing policy rule to control spending thresholds by category, you can use the effective date attributes, predicted expenditure amounts, and threshold amounts to support your procurement practices and help guarantee the efficient and effective use of public funds.

## Create tranches and lots

To create tranches and lots, create a hierarchy of parent and child purchase agreements. The child purchase agreements act as the tranches and lots of the parent purchase agreement. The purchase agreement hierarchy has some specific characteristics:

- You can view the parent purchase agreement and see the total activity of the parent and all its related child agreements. This feature provides a single management view for reviewing and controlling activity on purchase agreements.
- Some values from the parent purchase agreement automatically transfer to the child agreements. For example, you can assign policies that are related to competitive advertising to the parent purchase agreement. Those policies then apply to all the child agreements that are related to that parent.
- Purchase agreements can have a prime contractor, co-contractors, and subcontractors. You can assign the prime contractor to the parent purchase agreement, and assign a co-contractor or subcontractor to specific child agreements.

> [!NOTE]
> If you add lines to a purchase agreement, you can't use that purchase agreement as a parent agreement. The **Create child agreement** button no longer appears. Likewise, if you create a child purchase agreement, you can't add lines to the parent purchase agreement. To see the relationships among parent and child purchase agreements, use the **Purchase agreement tree** page.

## Set up purchase agreement access and limits

You can set up purchase agreements so that only approved departments have access to the agreement. You can also limit the amount that each department can spend against the purchase agreement. Users who try to exceed the maximum amount that is allocated for a department receive a message, and they're prevented from confirming the release or processing the invoice. Before you can use this capability, you must set the following parameters in the **General** section of the **Accounts payable parameters** page:

- In the **Account structure** field, select the account structure to use on the **Purchase agreement department access** page to control access to purchase agreements. The account structure must include the financial dimension segment that you use to control access to purchase agreements.
- In the **Financial dimension** field, select the financial dimension that you use to control access to purchase agreements. Most organizations use the department dimension, but some organizations might restrict access to purchase agreements to different entities within their organizations.

## Manage information about subcontractors, certifications, and milestones on purchase agreements

You can create purchase agreement classifications that add administrative fields to the purchase agreements that use the classification.

- To add information about subcontractors to purchase agreements, select the **Subcontractors** option on the purchase agreement classification.  Purchase agreements can have a prime contractor, co-contractors, and subcontractors. The prime contractor can be assigned to the parent purchase agreement, and a co-contractor or subcontractor can be assigned to specific child agreements.
- To add information about certifications for vendors to purchase agreements, select the **Certifications** option on the purchase agreement classification. You can use certification information to generate a report that lets you monitor vendor compliance with certification requirements.
- To add information about milestones and tasks to purchase agreements, select the **Activities** option on the purchase agreement classification.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
