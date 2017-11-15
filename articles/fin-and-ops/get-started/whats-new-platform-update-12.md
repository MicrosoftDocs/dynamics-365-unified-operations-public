---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 12 (October 2017)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 12. This version was released in October 2017.
author: tonyafehr
manager: AnnBe
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tonyafehr
ms.search.scope:  Operations, UnifiedOperations, Platform
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: e577d51d-42d2-47c5-b388-93c8219c692a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-09-30 
ms.dyn365.ops.version: Platform update 12 

---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 12 (October 2017)

[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 12. This version was released in October 2017 and has a build number of XXXXXXXXXXXXXX.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 12, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=856083).

Browser client - Discover and learn currently available keyboard shortcuts
--------------------------------------------------------------------------

You no longer need to search through documentation to learn keyboard shortcuts.
Instead, you can now discover currently available keyboard shortcuts directly
from the user interface. Simply right-click on a control and select **View
shortcuts**. This will open a dialog box listing the shortcuts that you can use
based on where you are on the page. 

For more information, see [Keyboard shortcuts](shortcut-keys.md).

Export B2B users to Azure AD 
-----------------------------

You can automatically export business-to-business (B2B) users to Azure Active
Directory (Azure AD).

In the past, B2B users were exported manually to a .csv file. Then the Azure AD
tenant administrator had to use this file to manually add the users to Azure AD
using the Azure portal.

To enable the automatic export feature, a one-time setup and configuration
process must be completed. When the process is completed, you can use
the Provision new user workflow task to automatically export B2B users to Azure
AD.

The one-time set up and configuration means that you'll need to:

-   Set up a B2B invitation service application in Azure AD.

-   Configure the B2B invitation service settings in Finance and Operations.

For more information, see [Export B2B users to Azure AD](../../dev-itpro/sysadmin/implement-b2b.md).

Personalizations can easily be shared with one or more roles in your organization
---------------------------------------------------------------------------------

Personalization capabilities enable a user to make changes to the user
interface, such as renaming labels, adding, moving or hiding controls, resizing,
adding or re-ordering grid columns on forms across the application.
Personalization also makes it possible for an end user to create new workspaces
showing content from within the application as well as from Power BI. These
features reduce the need to make customizations to the application and instead
allow a user to potentially create the required user interface, either starting
from scratch or by modifying ready-made content.

Administrators already have the ability to export a personalization done by a
user and apply that to other users or roles within the organization through an
import process. This will be simplified by allowing an administrator to share
personalizations with others from the personalization administration form,
without having to import the personalization.

Additionally, this feature gives the administrator more control over how to
apply a personalization. Instead of replacing existing personalizations, an
administrator can optionally choose to add the new personalizations to any
existing ones.   

Reporting: Document Routing Agent scale improvements
----------------------------------------------------

The Document Routing Agent has been enhanced to offer support for more network
printer devices. With the ability to support up to 50 network printers, clients
are better prepared to handle common printing workloads. Simply upgrade the
Document Routing Agent after deploying the latest platform update to take
advantage of the intelligent document queue management.

**Note:** Refer to the following installation instructions to deploy the latest
version of the Document Routing Agent onto local print servers hosted on the
corporate domain, [Install the Document Routing Agent to enable network printer
devices](../../dev-itpro/analytics/install-document-routing-agent.md).
