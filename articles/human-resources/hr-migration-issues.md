---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge known issues
description: This article lists issues that can occur during the Microsoft Dynamics 365 Human Resources infrastructure merge.
author: twheeloc
ms.date: 02/17/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# Dynamics 365 Human Resources infrastructure merge known issues

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Shared Dataverse environments

The Dual Write framework doesn't support linking two finance and operations app environments to the same Dataverse environment. If both of the following items share a Dataverse environment, duplicate or split the environment:

- A finance and operations app
- A current Human Resources environment

## Environment type requirements

Required environment types before migration:

- A sandbox standalone environment to validate the migration.
- If you have multiple production standalone environments, one of the environments can be migrated. Contact Microsoft Support to mark the other environments as sandboxes.

## Teams integration

The existing Human Resources app in Teams is shifting to a Microsoft Power Platform solution. For more information, see [Human Resources app in Teams](hr-admin-teams-leave-app.md).

## Dual-write integration

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps and finance and operations apps. If your organization uses dual-write for integrations, some issues might affect you. For more information about Dataverse tables and issues, see [Dataverse tables](hr-developer-entities.md).

## Custom financial dimensions

In finance and operations apps, Main account is a reserved financial dimension. If there's a custom financial dimension named Main account in standalone Human Resources, rename it before you migrate your Human Resources environment. If this dimension isn't used, remove it before the migration.
