---
# required metadata

title: Finance and Operations Connector
description: This topic provides information about the Finance and Operations Connector for Microsoft Flow and Logic Apps
author: Sunil-Garg
manager: AnnBe
ms.date: 03/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom:
ms.dyn365.ops.version: 2019-02-28
---

# Finance & Operations Connector

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

The Dynamics 365 for Finance and Operations connector allows a Microsoft Flow, PowerApps, Data Integrator and Logic Apps to integrate with an instance of Dynamics 365 for Finance and Operations. An integration can use the available actions to affect a Create, Update or a Delete operation in the target instance among other things. It is recommended to read the following referenced articles as a pre-requisite to familiarize with background topics before proceeding further.

**References**

| **Topic**                                                               | **Content**                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Understanding connectors in general                                     | <https://docs.microsoft.com/en-us/connectors/>                                                                                                                                                                                                                                                                                                                                                           |
| Understanding Dynamics 365 for Finance and Operations integration API’s | <https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/data-management-api?toc=/fin-and-ops/toc.json https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/odata?toc=/fin-and-ops/toc.json https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/recurring-integrations?toc=/fin-and-ops/toc.json> |

**Actions in Dynamics 365 for Finance and Operations**

This section describes the actions that are available in the Dynamics 365 for Finance and Operations connector.

**Get a record**

This action can be used to fetch a record for a specific data entity from the target instance of Dynamics 365 for Finance and Operations.

*Instance* refers to the URL of the target instance of Dynamics 365 for Finance and Operations to which connector must connect. The expected value is to enter the URL without the ‘https://’ prefix or choose one from the drop down. The instance drop down shows the list of all Dynamics 365 for Finance and Operations environment(s) that are deployed and the user has access to in the Azure active
directory tenant of the user account that was used to log into the specific client like Microsoft Flow, PowerApps or Logic App.

*Entity name* refers to the data entity in Dynamics 365 for Finance and Operations from which the record must be fetched. The drop down shows the list of data entities from the target environment.

*Object id* refers to the primary key(s) fields that must be specified to uniquely identify the record that must be fetched. The following syntax must be followed to specify the keys.

**Create a record**

This action can be used to create data record in Dynamics 365 for Finance and Operations for a data entity.

*Instance* refers to the URL of the target instance of Dynamics 365 for Finance and Operations to which connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop down. The instance drop down shows the list of all Dynamics 365 for Finance and Operations environment(s) that are deployed in the Azure active directory tenant
of the user account that was used to log into the specific client like Microsoft Flow, PowerApps or Logic App.

*Entity name* refers to the data entity in Dynamics 365 for Finance and Operations in which the record must be created. The drop down shows the list of data entities from the target environment.

Based on the selected data entity, the list fields will be displayed and will  vary.

**Update a record**

This action can be used to update an existing data record in Dynamics 365 for Finance and Operations for a data entity. The usage is same as explained for create a record action.

**Delete a record**

This action can be used to delete an existing data record in Dynamics 365 for Finance and Operations for a data entity. The usage is same as explained for get a record action.

**Execute action**

This action can be used to invoke methods on a data entity to perform a business action in Dynamics 365 for Finance and Operations.

*Instance* refers to the URL of the target instance of Dynamics 365 for Finance and Operations to which connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop down. The instance drop down shows the list of all Dynamics 365 for Finance and Operations environment(s) that are deployed in the Azure active directory tenant
of the user account that was used to log into the specific client like Microsoft Flow, PowerApps or Logic App.

*Action* refers to the method on the data entity that must be executed in Dynamics 365 for Finance and Operations. Based on the chosen method, the list of fields displayed will be different. These fields represent the parameters for the selected method.

**Get list of entities**

This action can be used to get the list of entities for further use in the app that is being developed.

*Instance* refers to the URL of the target instance of Dynamics 365 for Finance and Operations to which connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop down. The instance drop down shows the list of all Dynamics 365 for Finance and Operations environment(s) that are deployed in the Azure active directory tenant
of the user account that was used to log into the specific client like Microsoft Flow, PowerApps or Logic App.
