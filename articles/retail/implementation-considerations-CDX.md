---
# required metadata

title: Commerce Data Exchange implementation guidance
description: This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives an overview, implementation tips, and overall guidance that should be considered as you plan your implementation in regards to forms, setup, configuration, best practices, and more.
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

# Commerce Data Exchange implementation guidance
This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives an overview, implementation tips, and overall guidance that should be considered as you plan your implementation in regards to forms, setup, configuration, best practices, and more.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment is effectively useless.  As such, it is top priority to understand what is required to configure, generate, synchronize, and verify data synchronization across a full implementation. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS and other in-store components.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the Devices implementation guide and the Commerce architecture documents. 

### Important Headquarters forms
The **Channel database** page is  ADD DESCRIPTION.
Add image for this...

The **Channel database group** page is  ADD DESCRIPTION.
Add image for this...

The **Channel profile** page is  ADD DESCRIPTION.
Add image for this...

The **Offline profile** page is  ADD DESCRIPTION.
Add image for this...

The **Channel schema** page is  ADD DESCRIPTION.
Add image for this...

The **Distribution schedule** page is  ADD DESCRIPTION.
Add image for this...

The **Scheduler job** page is  ADD DESCRIPTION.
Add image for this...

The **Scheduler subjob** page is  ADD DESCRIPTION.
Add image for this...

The **Data sync interval** page is   ADD DESCRIPTION. 


Additional details as required......


### Data synchronization overview
Data is generated and flows in a very specific way.  It is important to understand how this occurs to be able to understand how best to configure the timing and select what data to be synchronized. 

**Insert data sync flow diagram (Commerce Architecture - Data Synchronization (JPG))**

This diagram shows the direction and flow of data to be synchronized downward from Headquarters and the transactional data to be flowed upwards... ADD MORE INFO TO DESCRIBE.

**Insert data configuration flow diagram (Commerce Architecture - Forms flow)**

This diagram shows the different forms in Headquarters and how the configuration flow functions together to be able to generate data... ADD MORE INFO TO DESCRIBE.



## Implementation considerations
This section describes some things that you should consider as you plan to implement features that are related to data management and configuration.



**OPEN QUESTIONS IN THIS DOC**
Verify Working folders are no longer required with Commerce Batch Service (Azure Batch for now)




## Resources
*Link to Devices Implementation Guide* [Device management implementation guidance](implementation-considerations-devices.md)
*Link to Commerce Architecture* [Commerce Architecture](commerce-architecture.md)
*Link to MPOS installer*
*Link to CSU (Self-hosted) installer*

