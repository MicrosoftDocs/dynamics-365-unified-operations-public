---
# required metadata

title: Fleet Management sample application overview
description: This topic is an overview of the Fleet Management sample application.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 79892
ms.assetid: 999b43b2-f149-4145-9d85-e2a62cd8da1e
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fleet Management sample application overview

This topic is an overview of the Fleet Management sample application.

The Fleet Management sample application has been provided to showcase development and foundation capabilities. Fleet Management represents a solution that an ISV might create for a car-rental agency. Fleet Management data includes vehicles which are available for renting, and customers who can rent and return these vehicles. Employees can also run a maintenance workflow on these vehicles. **Note**

For some tutorials, you will need to create the FleetManagement solution if it is not on your computer. The steps to create it are listed in [Tutorial: Create a Fleet Management solution file out of the Fleet Management models in the AOT](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/05/19/tutorial-create-a-fleet-management-solution-file-out-of-the-fleet-management-models-in-the-aot).

For some tutorials, you must download the Fleet Management tutorial code and other artifacts from <https://github.com/Microsoft/FMLab>.

Fleet Management is provided as a Visual Studio solution that demonstrates platform capabilities, such as:

-   Forms
-   Workflow
-   Security
-   Labels
-   Resources
-   Data
-   Business Intelligence
-   Extensions

The Fleet Management solution includes two separate projects: one for the base model and the other one for extensions to the base model. The project named FleetManagement Migrated demonstrates how a migrated application might appear after migrating code from Dynamics AX 2012. This version shows how forms that have been migrated from Microsoft Dynamics AX 2012 R3 work on a web client. These forms have been created using automated migration tools and some other manual migration steps in Visual Studio. These forms bind to X++ tables and use the X++ programming model. The project named FleetManagement Discounts (or FleetManagementExtension) demonstrates how to use extensions to customize an application. This project extends the Fleet Management sample by extending controls and tables, handling data events, and replacing business logic using a plug-in. The tutorials that accompany this article provide a more-detailed look at the Fleet Management sample. These include a Fleet Management tutorial, [Using the Fleet Management sample](fleet-management-sample.md), and a tutorial that walks through extensions, [Customize model elements using Extensions](..\extensibility\customize-model-elements-extensions.md).

See also
--------

[Using the Fleet Management sample](fleet-management-sample.md)

[Customize model elements using extensions](../extensibility/customize-model-elements-extensions.md)

[Developer Home Page](developer-home-page.md)

[Download the FMLab sample code](https://github.com/Microsoft/FMLab)

[Create the FleetManagement solution](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/05/19/tutorial-create-a-fleet-management-solution-file-out-of-the-fleet-management-models-in-the-aot)

