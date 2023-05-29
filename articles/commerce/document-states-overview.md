---
title: Document states and lifecycle
description: This article covers the various document states of page elements in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.collection: get-started
ms.search.industry: 
ms.search.form: 
---
# Document states and lifecycle

[!include [banner](includes/banner.md)]

This article covers the various document states of page elements in Microsoft Dynamics 365 Commerce.

## Document state descriptions

The [Page elements](page-elements-overview.md) article lists various documents types in the content management system (CMS). These document types can have several states in the authoring tool. The document states help prevent data conflicts and enforce version control. They determine who can change the documents, when the documents can be changed, and when changes can be viewed by other people.

The following table shows the possible document states of page elements in Commerce.

| Document state      | Site builder action        | Description                                                  |
| ------------------- | -------------------------- | ------------------------------------------------------------ |
| Checked out         | Select **Edit**.           | The applicable document is checked out to you. While a document is in this state, it can't be changed by other authenticated system users, and any changes that you make to the document are visible only to you. |
| Saved               | Select **Save**.           | Changes that have been made to a checked-out document are saved to the database, but the document isn't yet checked in or published. The saved changes aren't visible to other authenticated system users until the author selects **Finish editing**. They aren't visible to external users until the item is published. |
| Discarded check out | Select **Discard edits**.  | All changes to the checked-out document are discarded, and the item reverts to the last version that was checked in. |
| Checked in          | Select **Finish editing**. | The edited document is checked in. All changes are visible to other authenticated system users, and those users can then edit the document. Each check-in creates a document version record in the item's history. |
| Published           | Select **Publish**.        | The document is published, and the changes are pushed to your live site and become discoverable by external users. Items can be published only if they have first been checked in by selecting **Finish editing**. |

## Additional resources

[Ways to add content](add-manage-content.md)

[Page model glossary](page-elements-overview.md)

[Work with publish groups](publish-groups.md)

[Enable and use cross-channel sharing](cross-channel-sharing.md)

[Work with modules](work-with-modules.md)

[Work with fragments](work-with-fragments.md)

[Templates and layouts overview](templates-layouts-overview.md)

[Customize site navigation](customize-site-navigation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
