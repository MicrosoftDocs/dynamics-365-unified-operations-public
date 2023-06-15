---
# required metadata

title: Introduction to functional locations
description: This article provides an overview of functional locations in Asset Management.
author: johanhoffmann
ms.date: 06/25/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetFunctionalLocationEditSubLocations, EntAssetFunctionalLocationLookup, EntAssetFunctionalLocationRename, EntAssetFunctionalLocation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: ["2214"]
ms.collection: get-started
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Introduction to functional locations

[!include [banner](../../includes/banner.md)]

 

This article provides an overview of functional locations in Asset Management. Functional locations are elements of a technical structure, such as the functional units in a system. Functional locations are created hierarchically, and you install assets on them. The setup of functional locations in your company depends on the company's requirements.

Here are some examples of how you can use functional locations:

- **Functional** – The functional locations can be user-oriented and used to manage assets that have similar behavior.
- **Process-related** – The functional locations can be workflow-oriented.
- **Spatial** – The functional locations can represent geographical locations or sites.

Each functional location is managed independently in Asset Management. Here are some of the useful features of functional locations:

- Set up functional location specifications.
- Set up asset specification requirements.
- Set up maintenance sequences for preventive and reactive maintenance.
- Manage installed assets.
- Track active requests and work orders that are related to installed assets.
- Track faults that are registered on assets.
- Track maintenance costs on the assets that are related to a functional location at any given time.

Functional locations provide traceability of assets in relation to requests, work orders, fault registrations, condition assessments, production stop registrations, and asset counter registrations.

> [!NOTE]
> Even if an asset is installed on various functional locations during its lifetime, the costs can be related to each location. In other words, asset costs are always related to the functional location that the asset was installed on at a given time.

Functional locations are **not** flexible. Therefore, after you set up a functional location hierarchy, you can't move locations around in it. 

After you create a functional location hierarchy, the next step is to install assets on it. For more information, see [Install assets on functional locations](../functional-locations/install-objects-on-functional-locations.md).

## All functional locations

Select **Asset management** \> **Functional locations** \> **All functional locations** to open the **All functional locations** list page. This page shows all functional locations and some of the information that is related to each. To view only active functional locations, select **Active functional locations**. To view only the functional locations that you're related to as a worker, select **My active functional locations**. (This relation is set up on the **Workers** page. For more information, see [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md).)

On the **All functional locations** list page, select a link in the **Functional location** column to view the details of the selected record. To edit the functional location, select the **Edit** button. The details view shows detailed information that is related to the location. It also includes a **Related information** pane on the right. This pane shows the functional location hierarchy. You can expand and collapse the **Related information** pane.

The buttons on the Action Pane are organized on tabs. The following table briefly describes the buttons that are related to Asset Management.

| Button name                         | Description                                                                                                                                  |
|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Edit                                | Switch between edit mode and view mode for the page.                                                                                         |
| New                                 | Create a new functional location.                                                                                                            |
| Delete                              | Delete the selected functional location.                                                                                                     |
| Rename                              | Rename the selected functional location.                                                                                                     |
| Copy functional location structure  | Copy the functional location hierarchy.                                                                                                      |
| Install asset                       | Install an asset, including child assets, on the functional location.                                                                        |
| Replace asset                       | Replace the asset hierarchy with another asset hierarchy on the functional location.                                                         |
| Cost control                        | Open the **Functional location cost control** page, where you can do a cost calculation for the selected functional location.                |
| Hour control                        | Open the **Functional location hour control** page, where you can do a cost calculation for the selected functional location.                |
| Assets                              | Open the **All assets** page, where you can view a list of assets that are related to the selected functional location.                      |
| Requests                            | Open the **Active requests** page, where you can view a list of requests that are related to the selected functional location.               |
| Work orders                         | Open the **Active work orders** page, where you can view a list of work orders that are related to the selected functional location.         |
| Faults                              | Open the **Asset faults** page, where you can view a list of asset fault registrations that are related to the selected functional location. |
| Update functional location state    | Update the stage of the selected functional location.                                                                                        |
| Lifecycle state log                 | View a log that shows the stages of the selected functional location.                                                                        |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]