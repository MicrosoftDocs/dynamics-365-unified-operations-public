---
# required metadata

title: Project Service Automation
description: This topic provides information about the Project Service Automation to Finance and Operations integration solution. This solution uses the Data Integration feature to synchronize data across instances of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and Microsoft Dynamics 365 for Project Service Automation via the Common Data Service (CDS).
author: KimANelson
manager: AnnBe
ms.date: 11/27/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2016-11-28
ms.dyn365.ops.version: AX 7.0.0

---

# Project Service Automation

The Project Service Automation to Finance and Operations integration solution uses the Data Integration feature to synchronize data across instances of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and Microsoft Dynamics 365 for Project Service Automation via the Common Data Service (CDS). The integration templates that are available with the Data Integration feature enable the flow of projects, project contracts, and project contract lines from Project Service Automation to Finance and Operations.

> [!NOTE] 
> If you are using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3.0, you must install KB 4074835.

Before you can integrate Project Service Automation with Finance and Operations, you must configure the Project Service Automation integration parameters. For more information, see Project Service Automation integration parameters.

This integration solution enables direct synchronization in the following scenarios:

- Maintain project contracts in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Create projects in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain project contract lines in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain project contract line milestones in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.

## Conceptual flow of the Project Service Automation integration with Finance and Operations

The following illustration shows how data is synchronized as part of the integration between Project Service Automation and Finance and Operations.

> [!NOTE]
> Not all templates are currently available. Templates will be released as they are completed.

[![Project Service Automation integration with Finance and Operations](./media/PSA-integration.png)](./media/PSA-integration.png)

## System requirements for Finance and Operations

To use the Project Service Automation to Finance and Operations integration solution, you must install Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3 with platform update 12 or later.

## System requirements for Project Service Automation

To use the Project Service Automation to Finance and Operations integration solution, you must install the following components:

- Microsoft Dynamics 365 for Project Service Automation version 7.2.0.69 or later
- Prospect to cash solution for Dynamics 365 for Sales, version 1.14.0.0 (v14) or later
- Project Service Automation to Operations solution for Dynamics 365 for Project Service Automation version 1.0.0.0 or later

## Install the Project Service Automation to Finance and Operations integration solution in your Project Service Automation instance


