---
# required metadata

title: Analyze – Code upgrade
description: This topic explains how to use the Code upgrade service in LCS to help estimate the tasks and effort that are required in order to upgrade a code base from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Operations.
author: tariqbell
manager: AnnBe
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8

---

# Analyze – Code upgrade

[!include[banner](../includes/banner.md)]

This topic explains how to use the Code upgrade service in Microsoft Dynamics Lifecycle Services (LCS) to help estimate the tasks and effort that are required in order to upgrade a code base from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Operations.

The Code upgrade service converts an export of your AX 2012 model store to the correct format for Dynamics 365 for Operations. However, the new version of your code won’t be fully functional until a developer resolves any issues that the service identifies but can’t resolve itself.

The Code upgrade service performs these actions:

- Directly resolve some types of conflict issues.
- For other issues, log Microsoft Visual Studio Team Services (VSTS) tasks.
- Create a version of your code in Dynamics 365 for Operations format, and check the new version into a new branch of your VSTS project.

In the Analyze phase, we use the report to help estimate the effort that is required in order to complete code conversion activities.

The following illustration shows an overview of the process for configuring the Code upgrade service.

![Configuration process for the Code upgrade service](media/codeUpgradeConfigurationProcess.png)

For information about how to configure the Code upgrade service, see [Configure the code upgrade service in Lifecycle Services](https://docs.microsoft.com/en-gb/dynamics365/operations/dev-itpro/lifecycle-services/configure-execute-code-upgrade).

The output of the Code upgrade service is designed to be consumed by a Dynamics 365 for Operations developer. This output will help the developer estimate the effort that is required in order to complete the code upgrade tasks. To form an estimate, the developer must review the tasks that the service generates in VSTS and the new version of the code that the service generates.
