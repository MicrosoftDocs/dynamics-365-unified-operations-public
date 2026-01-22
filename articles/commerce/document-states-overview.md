---
title: Document states and lifecycle
description: Learn about the various document states of page elements in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection: get-started
ms.custom: 
  - bap-template
---
# Document states and lifecycle

[!include [banner](includes/banner.md)]

This article describes the various document states of page elements in Microsoft Dynamics 365 Commerce.

## Document state descriptions

The [Page elements](page-elements-overview.md) article lists various document types in the content management system (CMS). These document types can have several states in the authoring tool. The document states help prevent data conflicts and enforce version control. They determine who can change the documents, when the documents can be changed, and when other people can view changes.

The following table shows the possible document states of page elements in Commerce.

| Document state      | Site builder action        | Description                                                  |
| ------------------- | -------------------------- | ------------------------------------------------------------ |
| Checked out         | Select **Edit**.           | You check out the document. While a document is in this state, other authenticated system users can't change it, and any changes that you make to the document are visible only to you. |
| Saved               | Select **Save**.           | You save changes that you made to a checked-out document to the database, but you didn't yet check in or publish the document. Other authenticated system users can't see the saved changes until the author selects **Finish editing**. External users can't see the changes until the item is published. |
| Discarded check out | Select **Discard edits**.  | You discard all changes to the checked-out document, and the item reverts to the last version that was checked in. |
| Checked in          | Select **Finish editing**. | You check in the edited document. Other authenticated system users can see all changes, and they can then edit the document. Each check-in creates a document version record in the item's history. |
| Published           | Select **Publish**.        | You publish the document. The changes are pushed to your live site and become discoverable by external users. You can publish items only if you first check them in by selecting **Finish editing**. |

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
