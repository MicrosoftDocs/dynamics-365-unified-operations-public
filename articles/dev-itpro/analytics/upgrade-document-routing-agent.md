---
# required metadata

title: Upgrade the Document Routing Agent
description: This topic explains how to upgrade the Document Routing Agent.
author: TJVass
manager: AnnBe
ms.date: 04/06/2018
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

The Platform update 12 release of Dynamics 365 for Finance and Operations includes a number of significant enhancements in components used to deliver network printing capabilities. These updates include a redesigned print job queue management solution that allows the  service to scale to satisfy high volume printing requirements. Although, the Print Job Management service is backward compatible with in-market versions of the Document Routing Agent (DRA) client, it is highly recommended that customers upgrade **all** existing DRA clients hosted on-premises.

Failure to upgrade existing installments of the Document Routing Agent to Platform update 12 or later may result in the following issues:
- Observable performance degradation in the Dynamics 365 for Finance and Operations applications
- Potential loss of documents associated with orphaned print jobs
- Inconsistent handling for printed documents with custom margins

IT administrators must perform the following procedures on each domain resource used to host a DRA for Finance and Operations.

## Get started
To continue running the DRA as a windows service, you'll need both the user name and password of the domain account used to run the service.  This information must be available after completing the upgrade process.  The active service account information can be accessed in the **Services** for the **Microsoft Dynamics 365 Document Routing Service**.

![Services window](media/Services_dialog.png)

## Uninstall existing Document Routing Agent (DRA)
Open the **Programs and Features** window, and then find and uninstall the **Microsoft Dynamics 365 for Finance and Operations: Document Routing** application.

![Uninstall or change a program window](media/Programs_and_Features_dialog.png)

During the uninstallation process, you'll likely be prompted with the following dialog:

![Document Routing Agent Uninstall dialog](media/Uninstall_DRA_services.png)

> [!Important]
> Select **Automatically close applications and attempt to restart them after setup is complete.**

## Install the latest Document Routing Agent
To install the latest Document Rounting Agent available with your subscription, see [Install the Document Routing Agent to enable network printer devices](install-document-routing-agent.md).

