---
# required metadata

title: Choose the right in store topology
description: This topic This article provides an overview of various Dynamics 365 for Retail in store topologies.
author: rassadi
manager: AnnBe
ms.date: 03/04/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: SysAADClientTable, RetailTransactionServiceProfile
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.search.region: Global
# ms.search.industry: 
ms.author: jashanno
ms.search.validFrom: 2019-03-01

---

# Choose the right retail in store topology

[!include [banner](../../includes/banner.md)]

This article provides a detailed overview of the various Dynamics 365 for Retail in store topologies. 

## Key terms
| Term | Description |
|---|---|
| Retail Store Scale Unit (RSSU) | Retail Store Scale Unit is a set of components that can be deployed in a customer enviornment (e.g. inside a store) that can support continuous operations as connectivity to the back office or headquarters (HQ) is lost. |

## Overview
The sections in this topic describe the following steps, which you must complete to set up an environment with N-1 components. These steps assume that Retail headquarters is already deployed, and that an AX 2012 R3 environment is currently running.

- **[Supported capabilities and features when connectivity is lost](#Supported-capabilities-and-features-when-connectivity-is-lost)** – An overview of supported capabilities and features in each of the Retail in store topologies when connectivity to the HQ is lost.
- **[Deployed components](#Deployed-components)** - An overview of the deployed Dynamics 365 Components required to operate each of the Retail in store topologies.
- **[Hardware and sofware requirements](#Hardware-and-sofware-requirements)** - An overview of the minimum hardware and software requirements to operate each of the Retail in store topologies.
- **[Maintenance tasks](#Maintenance-tasks)** - An overview of the maintenance tasks that are required to host and operate each of the Dynamics 365 for Retail in store topology.
- **[Related articles](#Related-articles)** – A List of resources with additional details related to the concepts covered in this article.

### High-level overview
![Choose the right Retail in store topology](media/CHANNEL/INSTORE/Topology.jpg)

## Supported capabilities and features when connectivity is lost
| Operation | Modern POS Offline<br>(without connectivity to Retail Server) | Retail Store Scale Unit<br>(without connectivity to HQ) |
| --- | :-: | :-: |
| Device Activations | | | 
| Extended Logon | ✔ | ✔ |

## Deployed components
The components described below are deployed through a single installer and therefore do not need to be installed individually.

### Modern POS
| Installed Component | Component Type | Notes |
| --- | --- | --- |
| Modern POS App | Universal Windows Platform (UWP) Application |
| Modern POS Client Broker | Universal Windows Platform (UWP) Application |
| Channel Database | SQL Database |

### Retail Store Scale Unit
| Installed Component | Component Type | Notes |
| --- | --- | --- |
| Retail Server | IIS Web Service | Local Retail Server instance |
| Channel Database | SQL Database |
| Asycn Client Service | Windows Service | 

## Hardware and sofware requirements
|  | Modern POS | Retail Store Scale Unit | 
| --- | --- | --- |
| Deployed Dynamics 365 Components | Modern POS Installer with offline capabilities | Retail Server (IIS Web Service)<br>Channel Database (SQL Database)<br>Async Client (Windows Service) |

## Maintenance tasks
| Maintenance Task | Modern POS Offline<br>(on each POS terminal) | Retail Store Scale Unit<br>(on each RSSU machine) |
| --- | :-: | :-: | 
| X | X | X |

## Related articles
- [Offline point of sale (POS) functionality](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/pos-offline-functionality)
- [Retail Store Scale Unit](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin)
- [Configure and install retail store scale unit](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-store-scale-unit-configuration-installation)
