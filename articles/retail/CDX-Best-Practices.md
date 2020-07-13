---
# required metadata

title: Commerce Data Exchange best practices
description: This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives best practices advice for implementations.
author: jashanno
manager: AnnBe
ms.date: 05/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Retail July 2017 update
---

# Commerce Data Exchange best practices
This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives best practices advice for implementations.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment is effectively useless.  As such, it is top priority to understand what is required to configure, generate, synchronize, and verify data synchronization across a full implementation. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS and other in-store components.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the Devices implementation guide and the Commerce architecture documents. 


## Resources
*Link to Devices Implementation Guide* [Device management implementation guidance](implementation-considerations-devices.md)

*Link to Commerce Architecture* [Commerce Architecture](commerce-architecture.md)

*Link to In-store Topologies* [Select an in-store topology](dev-itpro/retail-in-store-topology.md)

*Link to MPOS installer* LINK PENDING

*Link to CSU (Self-hosted) installer* LINK PENDING

