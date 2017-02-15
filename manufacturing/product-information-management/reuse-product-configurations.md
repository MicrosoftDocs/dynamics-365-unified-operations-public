---
# required metadata

title: Reuse product configurations
description: You can specify that you want to automatically reuse an existing configuration for a product. Then, when a user has completed a configuration session, the system verifies whether a configuration that matches the user’s selections already exists. If a matching configuration is found, the configuration ID, corresponding bill of materials (BOM), and route are reused.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-10-07 08 - 36 - 48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PCProductConfigurationModelDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 201813
ms.assetid: a3d36c21-2cbe-48f4-bb08-605a8991c2f5
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Reuse product configurations

You can specify that you want to automatically reuse an existing configuration for a product. Then, when a user has completed a configuration session, the system verifies whether a configuration that matches the user’s selections already exists. If a matching configuration is found, the configuration ID, corresponding bill of materials (BOM), and route are reused.

Requirements for reusing configurations
---------------------------------------

To enable configurations to be reused, you must specify the following information for the components and attributes on the **Product configuration model details** page:

-   **Components and subcomponents** – On the **General** FastTab, in the **Reuse configurations** field, select **Yes**.
-   **Attributes** – On the **Attributes** FastTab, select the **Include in reuse** option. This option appears only when the related component is enabled for reuse. If you don't select any attributes for reuse, the configuration is always reused, regardless of the user’s selections during a configuration session. The attribute values in the existing configuration must match the user’s selections. For example, if the user selects **Blue** as the color during a configuration session, the system verifies whether an existing configuration of the component has the color blue.

## Resetting configuration reuse
When you reset configuration reuse, previously created configurations are no longer considered. You might want to reset configuration reuse if the BOM or route was changed, but no related attributes were changed. You reset configuration reuse on the **General** FastTab for the component.

