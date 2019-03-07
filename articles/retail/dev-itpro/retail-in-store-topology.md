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

- **[Supported operations when connectivity is lost](#Supported-operations-when-connectivity-is-lost)** – This section provides a list of supported operations in each of the Retail in store topologies.
- **[Maintenance tasks](#Maintenance-tasks)** - This section provides a list of maintenance tasks that are required in each of the Dynamics 365 for Retail in store topology.
- **[Related articles](#Related-articles)** – This section provides a list of resources that provide additional details related to the concepts covered in this article.

### High-level overview
The following illustration shows a high-level description of the concepts described in this article.

![Choose the right Retail in store topology](media/CHANNEL/INSTORE/Topology.jpg)

## Supported operations when connectivity is lost
Thi list describes the various operations that are supported when the connectivity is lost in each of the Dynamics 365 for Retail in store topologies.

| Operation | Modern POS Offline<br>(without connectivity to Retail Server) | Retail Store Scale Unit<br>(without connectivity to HQ) |
| --- | :-: | :-: |
| Device Activations | | | 
| Extended Logon | ✔ | ✔ |

## Maintenance tasks
This list describes a set of maintenance tasks required in each of the Dynamics 365 for Retail in store topologies.

| Maintenance Task | Modern POS Offline<br>(on each POS terminal) | Retail Store Scale Unit<br>(on each RSSU machine) |
| --- | :-: | :-: | 
| X | X | X |

## Related articles
