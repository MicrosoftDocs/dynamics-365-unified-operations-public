---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 10 (August 2017)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 10. This version was released in August 2017.
author: tonyafehr
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: NOINDEX, NOFOLLOW 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 10 

---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 10 (August 2017)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 10. This version was released in August 2017 and has a build number of 7.0.4641.16233.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 10, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=856083).

## Browser client - Net Promoter Score integration

This feature will periodically prompt the user to provide feedback and rank their satisfaction with Dynamics 365 for Finance and Operations, Enterprise edition.

## Browser client - Support for keyboard shortcut sequences

Dynamics 365 for Finance and Operations, Enterprise edition is a complex product that supports a large number of keyboard shortcuts to allow keyboard-only users to be productive. To ensure that there will be a sufficient number of choices for selecting keyboard shortcuts for upcoming features and to allow grouping of shortcuts for similar actions, key sequences are now supported. A key sequence allows a particular action to be triggered by pressing two key combinations sequentially. For example, the key sequence (Alt+M, N), which is Alt+M followed immediately by pressing the N key, is a new shortcut for moving focus to the navigation bar. See the [Keyboard shortcuts](shortcut-keys.md) topic for more examples of key sequences in the product, notably shortcuts for actions related to the Task recorder.

## Build and maintain mobile workspaces using X++ classes

This release introduces a new model for creating and maintaining mobile workspaces through X++ classes in Microsoft Visual Studio. This allows for more flexibility and power in development, in addition to significant improvements to app performance. In this model, developers can create complex queries/structures without having to create forms. It's also possible to programmatically develop and edit the code supplying the data to the mobile workspaces. As a result, maintaining mobile workspaces is significantly improved in this new model. The App designer is still a valuable tool to quickly build mobile workspaces and can be used in combination with the new model when creating mobile workspaces. For more information, see "Server-side development" in [Mobile platform resources](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md).

## Excel add-in enables passing header context to detail records

This feature will make users more productive when using the Excel add-in to create and edit transactional data, by allowing the creation of header records in addition to line records. For example, for journal entry, you can use Open Lines in Excel for a journal, publish that journal, and then create a new journal directly in Excel. This removes the need to return to the Finance and Operations client. In addition, the productive relational lookup experiences that users expect from the Excel add-in is available for header records, like journals, just as they are for the related line records, like journal lines. For more information, see [Create Open in Excel experiences](../../dev-itpro/office-integration/office-integration-edit-excel.md).

## Skype support for Human Resources and Retail

Skype integration is now enabled in all applications that have been developed using the cloud platform. While Skype integration has been enabled in the Finance and Operations apps for some time, this feature is also available in other applications, including Human Resources and Retail.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]