---
# required metadata

title: Document states overview
description: This topic covers the various document states of page elements in Microsoft Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Document states overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers the various document states of page elements in Microsoft Dynamics 365 Commerce.

## Document state descriptions

The [Page elements overview](page-elements-overview) topic lists various documents types in the content management system (CMS). These document types can have several states in the authoring tool. The document states help prevent data conflicts and enforce version control. They determine who can change the documents, when the documents can be changed, and when changes can be viewed by other people. 

| Term | Description |
|---|---|
| Check out | When a CMS item is checked out to you, it can't be edited by any other authenticated system users. Any changes that you make to the item are visible only to you. |
| Check in | When a CMS item is checked in, all changes are visible to other authenticated system users, and those users can then check out the item and edit it. Each check-in creates a document version record in the item's history. |
| Publish | When a CMS item is published, it's pushed to your live site and becomes discoverable on the internet by non-authenticated external users. Items can be published only if they have been checked in. |
| Save | Changes that have been made to a checked-out CMS item can be saved to the CMS before the item is checked in or published. These saved changes aren't visible to other authenticated system users until the item is checked in. They aren't visible to external users until the item is published. |
| Discard check out | When a checked-out CMS item is discarded, all saved changes are deleted, and the item reverts to the version that was most recently checked in. |

## Additional resources

- [Add and manage content](add-manage-content.md)
- [Page elements overview](page-elements-overview)
