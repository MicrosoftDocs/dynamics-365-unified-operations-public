---
# required metadata

title: Document states and lifecycle
description: This topic covers the various document states of page elements in Microsoft Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Document states and lifecycle


[!include [banner](includes/banner.md)]

This topic covers the various document states of page elements in Microsoft Dynamics 365 Commerce.

## Document state descriptions

The [Page elements](page-elements-overview.md) topic lists various documents types in the content management system (CMS). These document types can have several states in the authoring tool. The document states help prevent data conflicts and enforce version control. They determine who can change the documents, when the documents can be changed, and when changes can be viewed by other people.

The following table shows the possible document states of page elements in Commerce.

| Document state | Description |
|---|---|
| Checked out | When a CMS item is checked out to you, it can't be edited by any other authenticated system users. Any changes that you make to the item are visible only to you. |
| Checked in | When a CMS item is checked in, all changes are visible to other authenticated system users, and those users can then check out the item and edit it. Each check-in creates a document version record in the item's history. |
| Published | When a CMS item is published, it's pushed to your live site and becomes discoverable on the internet by non-authenticated external users. Items can be published only if they have been checked in. |
| Saved | Changes that have been made to a checked-out CMS item can be saved to the CMS before the item is checked in or published. These saved changes aren't visible to other authenticated system users until the item is checked in. They aren't visible to external users until the item is published. |
| Discarded check out | When a checked-out CMS item is discarded, all saved changes are deleted, and the item reverts to the version that was most recently checked in. |

## Additional resources

[Ways to add content](add-manage-content.md)

[Page model glossary](page-elements-overview.md)

[Work with publish groups](publish-groups.md)

[Work with modules](work-with-modules.md)

[Work with fragments](work-with-fragments.md)

[Templates and layouts overview](templates-layouts-overview.md)

[Customize site navigation](customize-site-navigation.md)
