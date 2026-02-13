---
title: Upgrade from AX 2012 - Deploy a demo environment for analysis
description: Learn how to deploy a demo environment during the Analyze phase of upgrading from Microsoft Dynamics AX 2012 to finance and operations.
author: johnmichalak
ms.author: johnmichalak
ms.topic: install-set-up-deploy
ms.date: 11/11/2025
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

When you deploy a demo finance and operations environment, you gain hands-on experience with the program and can explore new features that you might be interested in. You also have an opportunity to validate differences in the program for your business processes, so that you can identify potential gaps or confirm that no gaps exist. At this stage in your upgrade project, your data and code aren't available in the environment. Therefore, you have limited ability to validate that everything conforms to your business process. However, this step is the first step in that work stream.

If you didn't yet purchase licenses and you're using a free trial, follow the steps in [Deploy a demo environment](../deployment/deploy-demo-environment.md) to deploy a demo environment to a Microsoft Azure subscription that you bring yourself.

If you already purchased licenses, you receive a link to configure a special type of project in Microsoft Dynamics Lifecycle Services: an implementation project. The implementation project lets you deploy a dev/test environment and a sandbox environment. For more information about this type of environment deployment, see [Upgrade from AX 2012 - Data upgrade in sandbox environments](data-upgrade-self-service.md).

> [!IMPORTANT]
> Before you run the upgrade, apply the latest **Quality Update** for the Dynamics 365 version you're using.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
