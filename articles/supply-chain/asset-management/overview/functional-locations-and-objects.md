---
title: Functional locations and assets
description: This article describes functional locations and assets in Asset Management. Asset Management is an advanced module for managing assets and maintenance jobs in Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Functional locations and assets

[!include [banner](../../includes/banner.md)]

This article describes functional locations and assets in Asset Management.

Asset Management is integrated seamlessly with several modules for Supply Chain Management and other finance and operations apps. The following illustration shows the interfaces with other modules.

[<img src="media/01-overview-image.png" alt="How Asset Management interfaces with other modules." title="How Asset Management interfaces with other modules" width="520" />](media/01-overview-image.png)

Asset Management lets you efficiently manage and perform all tasks that are related to managing and servicing many types of equipment in your company. This equipment includes machines, production equipment, and vehicles. Asset Management also supports solutions across numerous industries.

The following illustration shows an overview of the main functionality that is covered by Asset Management.

[<img src="media/02-overview-image.png" alt="Functionality in Asset Management." title="Functionality in Asset Management" width="520" />](media/02-overview-image.png)

Functional locations are used to manage assets on locations. This management includes tracking of asset costs on functional locations. Functional locations are structured hierarchically, and locations can have sublocations. The structure of functional locations is static. In other words, locations can't change place. Assets can be installed on functional locations and, as required, can be installed on other functional locations later.

Asset costs always follow the location of the asset. In other words, if you install an asset on a new functional location, the asset automatically uses the financial dimensions that are related to the new functional location. Therefore, asset costs are always related to the functional location that the asset is  currently installed on. This automatic handling of financial dimensions helps guarantee complete tracking of costs when your company does project controlling and reporting on functional locations.

The way that you build your hierarchy of functional locations depends on your company's requirements for maintaining internal equipment or servicing customer equipment. The following figure shows an example of functional locations that are based on geographical locations.

[<img src="media/03-overview-image.png" alt="Functional locations based on geographical locations." title="Functional locations based on geographical locations" width="520" />](media/03-overview-image.png)

The following figure shows an example of functional locations that are based on customers.

[<img src="media/04-overview-image.png" alt="Functional locations based on customers." title="Functional locations based on customers" width="520" />](media/04-overview-image.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
