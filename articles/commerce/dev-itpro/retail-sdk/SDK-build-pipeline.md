---
# required metadata

title: Setup Commerce SDK build pipeline.
description: This document walkthrough the steps required to setup the Azure DevOps build pipeline for the Retail SDK.
author: mugunthanm 
manager: AnnBe
ms.date: 06/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: 10.0.11
---

# Setup Commerce SDK build pipeline

[!include [banner](../../includes/banner.md)]

This document walkthrough the steps required to setup the Azure DevOps build pipeline for the Retail SDK using the Azure DevOps build agent (Microsoft hosted agent). 
For generating the build for Retail SDK, dedicated build machine is not required it will work with Azure DevOps build agent. This topic is applicable for Retail SDK version 10.0.11 or greater. 

## Prerequisite:

The Retail SDK must be added to Azure Repos Git, GitHub or VSTS. The Retail SDK is available in-Service volume drive of the LCS dev VM. Follow the steps mentioned in [this doc](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances) to provision a development VM in LCS.

## Steps to setup a build pipeline in Azure DevOps:

1.	Select Pipeline in Azure DevOps and click New pipeline.
2.	Select your source repo.
3.	Click the Pipeline and provide a name for your pipeline. Choose the Agent pool as Azure pipeline and Agent specification as vs2017-win2016.
    
    
