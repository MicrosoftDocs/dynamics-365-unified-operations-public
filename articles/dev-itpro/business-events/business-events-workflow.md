---
# required metadata

title: Workflow Business Events
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: ChrisGarty
manager: AnnBe
ms.date: 01/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
ROBOTS: noindex, nofollow
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Workflow Business Events

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

## How is a Workflow constructed?

Workflows components are defined in metadata and workflow elements can have event handlers that are defined in code. A developer defines these components using the Visual Studio tools.
Workflows are created in the web client by an administrator and then designed in the workflow designer. Multiple workflows can be created for the same workflow type, with one marked as default and activation rules used to activate the others. 

### Workflow components
Workflow components are defined in metadata as:
- Workflow types (aka templates)
     - In the Application Explorer: AOT > Business Process and Workflow > Workflow Types 
- Workflow elements
     - Tasks: AOT > Business Process and Workflow > Workflow Tasks
     - Approvals: AOT > Business Process and Workflow > Workflow Approvals
     - Automated Tasks: AOT > Business Process and Workflow > Workflow Automated Tasks

## Workflows at runtime
When a workflow is submitted by a user, then it is added to a queue and run via the "Workflow message processing" batch job.  

