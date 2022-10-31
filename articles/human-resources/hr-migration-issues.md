---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge known issues
description: This article lists issues that can occur during the Microsoft Dynamics 365 Human Resources infrastructure merge.
author: twheeloc
ms.date: 10/27/2022
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

The Dual Write framework doesn't support linking two finance and operations app environments to the same Dataverse environment. If you have a Dataverse environment that is shared with both a finance and operations app and a current Human Resources environment, you must either duplicate or split the Dataverse environment.

## Environment type requirements

The following environment types are required before you can do the migration:

- If you don't have any sandbox standalone environments, you must create one to validate the migration.
- If you have multiple production standalone environments, one of them can be migrated. Contact Microsoft Support to mark the other environments as sandboxes.

## Teams integration

The existing Human Resources app in Teams is currently being shifted to a Microsoft Power Platform solution. For more information, see [Human Resources app in Teams](hr-admin-teams-leave-app.md).

## Licensing

There are no changes to the licensing for Dynamics 365 Human Resources in the following areas: 

- **Minimum number of license purchase requirement**
- **Licenses to a production environment and a sandbox environment** – If you have existing standalone Human Resources licenses that include one production environment and one sandbox environment, the same number of licenses will be available on the finance and operations infrastructure.
- **Additional sandbox licenses** – If you've purchased additional sandbox licenses for the standalone Human Resources application, the same number of licenses 
will be available for sandbox environments on the finance and operations infrastructure. 
