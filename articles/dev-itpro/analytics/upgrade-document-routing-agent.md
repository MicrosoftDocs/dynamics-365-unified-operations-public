---
# required metadata

title: Upgrade the Document Routing Agent
description: This topic explains how to upgrade the Document Routing Agent.
author: TJVass
manager: AnnBe
ms.date: 03/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tjvass
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Upgrade the Document Routing Agent

[!include[banner](../includes/banner.md)]

The Platform Update 12 Release includes a number of significant enhancements in components used to deliver network printing capabilities for applications delivered Dynamics 365 for Finance & Operations.  These updates include a re-imagined print job queue management solution that provides customers with a more robust service capable of scaling to satisfy the needs of enterprise deployments.  Although, the Cloud service is backwards compatible with in-market versions of the DRA, it is highly recommended that customers upgrade existing servers used to host the DRA.

Failure to upgrade existing installments of the Document Routing Agent to PU12 or later may result in the following:
	• Observable performance degradation in the Dynamics 365 for Finance & Operations applications
	• Potential loss of documents associated with orphaned print jobs
	• Inconsistent handling for printed documents with custom margins

IT Admins must perform the following steps on each domain resource used to host a Document Routing Agent for Dynamics 365 for Finance & Operations.

Getting started…
To continue running the Document Routing Agent as windows service, you'll need both the user name and password of the domain account used to run the service.  This information must be available after completing the upgrade process.  The active service account information can be accessed in the open “Services” window and find the “Microsoft Dynamics 365 Document Routing Service”.

Image

Step 1) Uninstall existing Document Routing Agent (DRA)
Open the “Programs and Features” window, and then find and uninstall the “Microsoft Dynamics 365 for Finance and Operations: Document Routing”.

Image

During the uninstallation process, you'll likely be prompted with the following dialog…
Image

**Important:** select “Automatically close applications and attempt to restart them after setup is complete.”

Step 2) Now, reinstall the latest Document Routing Agent available in your deployment
Use the instructions provided here to download and install the latest version of the Document Routing Agent available with your subscription.


