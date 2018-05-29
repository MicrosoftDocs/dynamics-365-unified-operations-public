---
# required metadata

title: Project Service Automation integration parameters
description: You can configure how data should default when integrating Project Service Automation with Dynamics 365 for Finance and Operations.
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
> Project tasks integration, expense transaction categories, hour estimates, expense estimates, and functionality locking is available in Dynamics 365 for Finance and Operations version 8.0. 

> Actuals integration is available in Dynamics 365 for Finance and Operations version 8.0.1.

> If you are using Dynamics 365 for Finance and Operations, Enterprise edition 7.3.0, you will be able to use the templates to integrate project tasks, expense transaction categories, hour estimates, expense estimates, actuals and configure functionality locking after installing KB 4132657 and KB 4132660. It is recommended that you install KB 4131710 if you need to reset the accounting distributions.




| **Tab**                      | **Field**                          | **Description**                    |
|------------------------------|------------------------------------|--------------------------------|
| **General**                  | **Default project type**               | Select the default for **Project type**, which is when projects are synchronized from Project Service Automation if you have not provided a default value in the integration template. During synchronization, new projects will have the **Project type** set to this value and may be updated when the project contract lines are synchronized from Project Service Automation.               |
| **General**                  | **Time category**                      | Select the default for **Time category**, which is when hour estimates are synchronized from Project Service Automation. During synchronization, new project hour forecasts in Finance and Operations will have the **Category** set to this value when the hour estimates and hour actuals are synchronized from Project Service Automation.   |
| **General**                  | **Fee category**                       | Select the default for **Fee category**, which is when fee actuals are synchronized from Project Service Automation. During synchronization, new fee transactions in Finance and Operations will have the **Category** set to this value when the fee actuals are synchronized from Project Service Automation.          |
| **Project group defaults**   | **Project type** | Click **New** to add a row where you can select the project type for which to set the default project group. A specific project type can be selected only once in the configuration.              
|                              | **Project group**          | Select the default project group for the specified project type. When new projects are synced from Project Service Automation, the **Project group** will be the default based on the project type if you have not provided a default value in the integration template.  |
| **Billing type defaults**    | **Billing type** | Click **New** to add a row where you can select the billing type for which to set the default line property. A specific billing type can be selected only once in the configuration.          |
|                              | **Line property**| Select the default line property for the specified billing type. When new hour estimates, new expense estimates, or new actuals are synced from Project Service Automation, the **Line property** will be the default based on the billing type.          |
| **Functionality locking**    |                   | Select the functionality to disable in Finance and Operations for projects and contracts that originated from Project Service Automation. For example, you can choose to turn off the ability to edit contracts and projects, create work breakdown structures, and enter timesheets in Finance and Operations. Accounting-related fields will continue to be enabled, even if they are made unavailable by the parameter setting. By default, all functionality will be enabled.           |
