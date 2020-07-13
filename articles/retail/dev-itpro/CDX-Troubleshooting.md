---
# required metadata

title: Commerce Data Exchange troubleshooting
description: This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.
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

# Commerce Data Exchange troubleshooting
This topic is intended for IT personas who are implementing functionality related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. This document focuses on troubleshooting CDX in implementations.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment could become effectively useless.  As such, it is crucial to understand the process of troubleshooting any issue that arises in regards to data synchronization. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS (With or without an offline database) and other in-store components.  Reviewing this document should provide some general guidance on how to mitigate or fix some issues and highlight when it is best to create a support request and what data is most important to speed up a request for support.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the CDX implementation guide, the CDX best practices, and the Commerce architecture documents. 


## Resources
[Commerce Architecture](../commerce-architecture.md)
[Select an in-store topology](retail-in-store-topology.md)
[CDX best practices](../implementation-considerations-CDX.md)
[Device management implementation guidance](../implementation-considerations-devices.md)
*Link to MPOS installer* LINK PENDING

*Link to CSU (Self-hosted) installer* LINK PENDING

