---
# required metadata

title: Project Service Automation integration parameters
description: You can configure how data should default when integrating Project Service Automation with Dynamics 365 for Finance and Operations, Enterprise edition.
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

On the **Project Service Automation integration parameters** page, you can configure how data should default when integrating Project Service Automation with Finance and Operations. The following must be set up for projects to be successfully synchronized from Project Service Automation in Finance and Operations.

> [!NOTE]
>  Hour estimates, expense estimates, actuals and functionality locking functionality is available in Dynamics 365 for Finance and Operations version 8.0, which will be available in the Spring '18 release.




| **Tab**                      | **Field**                          | **Description**                    |
|------------------------------|------------------------------------|--------------------------------|
| **General**                  | **Default project type**               | Select default for **Project type** when projects are synchronized from Project Service Automation if you have not provided a default value in the integration template. During sychronization new projects  will have the **Project type** set to this value and may be updated when the project contract lines are synchronized from Project Service Automation.               |
| **General**                  | **Time category**                      | Select default for **Time category** when hour estimates are synchronized from Project Service Automation. During synchronization, new project hour forecasts in Finance and Operations will have the **Category** set to this value when the hour estimates and hour actuals are synchronized from Project Service Automation.   |
| **General**                  | **Fee category**                       | Select default for **Fee category** when fee actuals are synchronized from Project Service Automation. During synchronizaiton, new fee transactions in Finance and Operations will have the **Category** set to this value when the fee actuals are synchronized from Project Service Automation.          |
| **Project group defaults**   | **Project type** | Click **New** to add a row where you can select the project type for which to set the default project group. A specific project type can be selected only once in the configuration.              
|                              | **Project group**          | Select the default project group for the specified project type. When new projects are synced from Project Service Automation, the **Project group** will be the default based on the project type if you have not provided a default value in the integration template.  |
| **Billing type defaults**    | **Billing type** | Click **New** to add a row where you can select the billing type for which to set the default line property. A specific billing type can be selected only once in the configuration.          |
|                              | **Line property**| Select the default line property for the specified billing type. When new hour estimates, new expense estimates, or new actuals are synced from Project Service Automation, the **Line property** will be the default based on the billing type.          |
| **Functionality locking**    |                   | Select the functionality to disable in Finance and Operations for projects and contracts that orginated from Project Service Automation. For example, you can choose to disable the ability to edit contracts and projects, create work breakdown structures and enter timesheets in Finance and Operations. Accounting related fields will continue to be enabled, even if disabled by the parameter setting. By default, all functionality will be enabled.           |
