---
# required metadata

title: Project Service Automation integration parameters
description: You can configure how data should default when integrating Project Service Automation Microsoft Dynamics 365 for Finance
and Operations, Enterprise edition.
author: KimANelson
manager: AnnBe
ms.date: 12/13/2017
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
ms.dyn365.ops.version: AX 7.3.0

---

# Project Service Automation integration parameters

On the Project Service Automation integration parameters page, you can configure how data default when integrating Project Service Automation with Finance and Operations. The following must be set up for projects to be successfully synchronized from Project Service Automation in Finance and Operations.

| **Tab**                      | **Field**                          | **Description**                    |
|------------------------------|------------------------------------|--------------------------------|
| **General**                  | **Default project type**               | Select how the Project type should default when projects are being synchronized from Project Service Automation if you have not provided a default value in the integration template. New projects synced will have the project type set to this value and may be updated when the project contract lines are synchronized from Project Service Automation.               |
| **Project group defaults**   | **Project type** | Click **New** to add a row where you can select the project type for which to set the default project group. A specific project type can be selected only once in the configuration.              |
|                              | **Project group**          | Select the default project group for the specified project type. When new projects are synced from Project Service Automation, the project group will be defaulted based on the project type if you have not provided a default value in the integration template.  |
