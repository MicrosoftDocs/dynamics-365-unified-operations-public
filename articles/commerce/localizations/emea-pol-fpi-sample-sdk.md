---

# required metadata

title: Deployment guidelines for the fiscal registration service integration sample for Germany (legacy)
description: This topic provides guidelines on how to deploy the fiscal integration sample for Germany from the Retail SDK
author: josaw
ms.date: 11/12/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Germany
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---
# Deployment guidelines for the fiscal registration service integration sample for Germany (legacy)

This topic provides guidelines on how to deploy the fiscal registration service integration sample for Germany from the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information about this fiscal integration sample, see [Fiscal registration service integration sample for Germany](emea-deu-fi-sample.md). The fiscal integration sample for Germany is part of the Retail SDK. For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md). This sample consists of extensions for the CRT and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.
