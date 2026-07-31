---
title: Manage global vendor capabilities (preview)
description: Manage non-transactional vendor capabilities so you can profile, evaluate, and segment suppliers across legal entities.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage global vendor capabilities (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Global vendor capabilities help organizations capture what a supplier offers at a shared, cross-entity level. These records support vendor profiling rather than transaction processing, so teams can compare suppliers, evaluate fit, and segment vendors based on strategic needs. Capability data is stored in Dataverse and managed in the Supplier Engagement app.

## Understand what capabilities represent

Global vendor capabilities describe non-transactional attributes such as the following examples:

- Products that the vendor specializes in
- Market segments that the vendor serves
- Quality standards that the vendor follows
- Process capabilities that matter in specialized industries

Because you maintain this information at the global vendor level, procurement teams can review a supplier's broader business fit before they decide whether to qualify, approve, or release the vendor to legal entities.

## Use capabilities for evaluation and segmentation

Capabilities help internal teams answer business questions that transactional data alone can't answer. For example, you can use capability data to identify suppliers that support a target industry, hold a required quality standard, or provide a specialized manufacturing process.

That broader view supports activities such as:

- Comparing suppliers during sourcing and onboarding
- Grouping suppliers for category or market analysis
- Identifying suppliers that meet regional or technical requirements
- Supporting business reviews with richer profile information

## Organize capabilities in hierarchies

Capabilities can be arranged in parent-child relationships so that complex offerings are easier to understand and maintain. A hierarchy lets you group broad business areas under more specific capability records.

For example, a top-level capability such as *Manufacturing services* might contain child capabilities for *Precision machining*, *Injection molding*, and *Assembly*. This structure helps users capture both the supplier's broad service area and the detailed specialties underneath it.

## Understand how capabilities differ from procurement categories

Global vendor capabilities are different from procurement categories in Supply Chain Management:

- **Global vendor capabilities** are used for profiling, evaluation, and business alignment.
- **Procurement categories** are used for operational and transactional classification in purchasing processes.

Capability data isn't synchronized to Supply Chain Management. That separation helps organizations keep strategic supplier profiling distinct from the procurement structures that drive transactions.

## Assign capabilities to global vendors

To assign capabilities to global vendors, [open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Capabilities** tab. Use the various **Edit** buttons on this page to add or edit capabilities in each capability category (**Products**, **Segments**, **Capabilities**, or **Quality**).

Learn more in [Configure capabilities (preview)](configure-capabilities.md).

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Create a global vendor](supplier-engagement-create-global-vendor.md)
- [Manage certificates](supplier-engagement-manage-certificates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
