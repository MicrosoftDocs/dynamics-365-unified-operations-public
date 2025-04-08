---
title: Upgrade from AX 2012 - Deploy a demo environment for analysis
description: Learn how to deploy a demo environment during the Analyze phase of upgrading from Microsoft Dynamics AX 2012 to finance and operations.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 01/31/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8
---

# Upgrade from AX 2012 - Deploy a demo environment for analysis

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This article explains why and how you should deploy a demo environment during the Analyze phase of your project for upgrading from Microsoft Dynamics AX 2012 to finance and operations.

By deploying a demo finance and operations environment, you gain hands-on experience with the program and can explore new features that you might be interested in. You also have an opportunity to validate differences in the program for your business processes, so that you can identify potential gaps or confirm that no gaps exist. At this stage in your upgrade project, your data and code won’t be available in the environment. Therefore, you will have limited ability to validate that everything conforms to your business process. However, this step is the first step in that work stream.

If you haven’t yet purchased licenses, and you’re using a free trial, you can follow the steps in [Deploy a demo environment](../deployment/deploy-demo-environment.md) to deploy a demo environment to a Microsoft Azure subscription that you bring yourself.

If you’ve already purchased licenses, you received a link to configure a special type of project in Microsoft Dynamics Lifecycle Services (LCS): an implementation project. The implementation project will let you deploy a dev/test environment and a sandbox environment. For more information about this type of environment deployment, see [Upgrade from AX 2012 - Data upgrade in sandbox environments](data-upgrade-self-service.md).

> [!IMPORTANT]
> It is recommended that before you run the upgrade, that you apply the latest **Quality Update** for the Dynamics 365 version you are using.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
