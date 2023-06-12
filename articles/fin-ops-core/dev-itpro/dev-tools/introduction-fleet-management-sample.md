---
title: Fleet Management sample application
description: This article is an overview of the Fleet Management sample application.
author: gianugo
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.collection: get-started
ms.assetid: 999b43b2-f149-4145-9d85-e2a62cd8da1e
---

# Fleet Management sample application

[!include [banner](../includes/banner.md)]

This article is an overview of the Fleet Management sample application.

The Fleet Management sample application has been provided to showcase development and foundation capabilities. Fleet Management represents a solution that an ISV might create for a car-rental agency. Fleet Management data includes vehicles which are available for renting, and customers who can rent and return these vehicles. Employees can also run a maintenance workflow on these vehicles.

For some tutorials, you will need to create the FleetManagement solution if it is not on your computer. The steps to create it are listed in [End-to-end scenario for the Fleet Management sample application](fleet-management-sample.md).

For some tutorials, you must download the Fleet Management tutorial code and other artifacts from <https://github.com/Microsoft/FMLab>.

Fleet Management is provided as a Visual Studio solution that demonstrates platform capabilities, such as:

-   Forms
-   Workflow
-   Security
-   Labels
-   Resources
-   Data
-   Business Intelligence
-   Extensions

The Fleet Management solution includes two separate projects: one for the base model and the other one for extensions to the base model. The project named FleetManagement Migrated demonstrates how a migrated application might appear after migrating code from Dynamics AX 2012. This version shows how forms that have been migrated from Microsoft Dynamics AX 2012 R3 work on a web client. These forms have been created using automated migration tools and some other manual migration steps in Visual Studio. These forms bind to X++ tables and use the X++ programming model. The project named FleetManagement Discounts (or FleetManagementExtension) demonstrates how to use extensions to customize an application. This project extends the Fleet Management sample by extending controls and tables, handling data events, and replacing business logic using a plug-in. The tutorials that accompany this article provide a more-detailed look at the Fleet Management sample. These include a Fleet Management tutorial, [End-to-end scenario for the Fleet Management sample application](fleet-management-sample.md), and a tutorial that walks through extensions, [Customize model elements through extension](../extensibility/customize-model-elements-extensions.md).

## Additional resources

[Using the Fleet Management sample](fleet-management-sample.md)

[Customize model elements using extensions](../extensibility/customize-model-elements-extensions.md)

[Develop and customize home page](developer-home-page.md)

[Download the FMLab sample code](https://github.com/Microsoft/FMLab)

[Create the FleetManagement solution](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/05/19/tutorial-create-a-fleet-management-solution-file-out-of-the-fleet-management-models-in-the-aot)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
