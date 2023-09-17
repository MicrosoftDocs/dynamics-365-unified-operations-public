---
title: Select an in-store topology
description: This article provides information about the various Dynamics 365 Commerce in-store topologies.
author: Reza-Assadi
ms.date: 02/02/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2019-03-01
ms.search.form: SysAADClientTable, RetailTransactionServiceProfile
---

# Select an in-store topology

[!include [banner](../../includes/banner.md)]

This article provides an overview of the various Dynamics 365 Commerce in-store topologies. 

<a href="/dynamics365/unified-operations/retail/dev-itpro/media/channel/instore/topology.jpg" rel="some text">![Choose the right store topology.](media/CHANNEL/INSTORE/Topology.jpg)</a>

## Supported capabilities when connectivity is lost
| Operation | Without connectivity to Commerce Scale Unit<br>(in Store Commerce app offline mode) | Without connectivity to headquarters<br>(Commerce Scale Unit (self-hosted)) |
| --- | :-: | :-: |
| Cross terminal shifts (such as view, suspend, resume, close) | | ✔ | 
| Cross terminal transactions (such as view, suspend, resume)  | | ✔ |

## Supported operations when connectivity is lost
For a list of operations that are supported when the POS loses connectivity to headquarters, see [Online and offline point of sale (POS) operations](/dynamics365/unified-operations/retail/pos-operations).

## Supported deployment and maintenance capabilities
Mass deployment is supported in the Store Commerce app, but not in Commerce Scale Unit. For more information, see [Mass deployment of self-service components](/dynamics365/unified-operations/retail/dev-itpro/retail-mass-deployment).

## Deployed components
The following components are deployed through a single installer. This means that they do not need to be installed individually.

### Store Commerce app
| Deployed component | Component type | Notes |
| --- | --- | --- |
| Store Commerce app | Windows Application | The Store Commerce app running on the register. |
| Channel Database | SQL Database | Register specific Channel Database instance hosting data for the register.

### Commerce Scale Unit (self-hosted)
| Installed component | Component type | Notes |
| --- | --- | --- |
| Commerce Scale Unit (self-hosted) | IIS Web Service | Scale unit specific Commerce Scale Unit (self-hosted) instance used by one or more stores. |
| Channel Database | SQL Database | Scale unit specific Store specific Channel Database instance hosting data for one or more stores. |
| Async Client Service | Windows Service | Component to synchronize master record data from the headquarters to the store and transactional data from the store to the headquarters. |
| Store Commerce for web | IIS Web Service | Store Commerce for web application that hosts POS functionality through a web browser. |

## Additional resources
### Store Commerce app offline mode
For more information about Store Commerce app offline mode, see:
- [Offline point of sale (POS) functionality](/dynamics365/unified-operations/retail/pos-offline-functionality)
- [Online and offline point of sale (POS) operations](/dynamics365/unified-operations/retail/pos-operations)
- [Mass deployment of self-service components](/dynamics365/unified-operations/retail/dev-itpro/retail-mass-deployment)

### Commerce Scale Unit (self-hosted)
The Commerce Scale Unit (self-hosted) is a set of components that can be deployed in a customer environment, such as inside a store, that can support continuous operations if connectivity to the back office or headquarters is lost. 

For more information, see:
- [Configure and install Commerce Scale Unit (self-hosted)](/dynamics365/unified-operations/retail/dev-itpro/retail-store-scale-unit-configuration-installation)
- [Commerce Scale Unit (self-hosted)](/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
