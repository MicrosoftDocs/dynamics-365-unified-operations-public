---
# required metadata

title: Document states overview
description: This topic covers the various document states of page elements in Dynamics 365 Commerce.
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

This topic covers the various document states of page elements in Dynamics 365 Commerce.

## Document state descriptions

The CMS document types listed in the [Page elements overview](page-elements-overview) have several different possible states within the authoring tool that affect who can edit them and when they can be edited. These different document states help enforce data conflict prevention and version control, and determine who can make changes to a document and when changes are viewable by others.

Term | Short description
---|---
Check out | When a CMS item is checked out to you, it can't be edited by any other authenticated system users.  Any changes you make to the item are only visible to you. 
Check in | When a CMS item is checked in, all changes are visible to other authenticated system users and the document is available to check out and edit.  Each check in creates a document version record in the item's history. 
Publish | When a CMS item is published, it is pushed to your live site and becomes discoverable on the internet by non-authenticated external users.  Publish can only be performed on checked in documents. 
Save | Save is an action that can be made on a checked out document to persist changes to the CMS before they are checked in or published.  These saved changes are not visible to other authenticated system users until the document is checked in, and not visible to external users until published. 
Discard check out | When a checked out CMS item is discarded, all saved changes are deleted and the item is reverted to the most recently checked in version of the item. 

## Additional resources

- [Add and manage content](add-manage-content.md)
- [Page elements overview](page-elements-overview)
