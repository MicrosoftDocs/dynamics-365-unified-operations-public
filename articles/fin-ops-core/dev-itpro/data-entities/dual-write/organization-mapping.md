---
# required metadata

title: Organization hierarchy in Common Data Service
description: This topic describes the integration of organizational data between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Organization hierarchy in Common Data Service

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

Because Dynamics 365 Finance is a financial system, *organization* is a core concept, and system setup starts with the configuration of an organization hierarchy. Business financials can then be tracked at the organization level and also at any level in the organization hierarchy.

Although Common Data Service doesn't have the concept of an organization hierarchy, it does have a few loose concepts, such as total sales revenue. As part of Common Data Service integration, the organization hierarchy data structure is added to Common Data Service.

## Data flow

A business ecosystem that consists of Finance and Operations apps and Common Data Service will continue to have an organization hierarchy. This organization hierarchy is built on Finance and Operations apps, but it's exposed in Common Data Service for informational and extensibility purposes. The following illustration shows the organization hierarchy information that is exposed in Common Data Service as a one-way data flow from Finance and Operations apps to Common Data Service.

![Architecture image](media/dual-write-data-flow.png)

## Templates

Organization hierarchy entity maps are available for one-way synchronization of data from Finance and Operations apps to Common Data Service.

## Templates

Product information contains all the information related to the product and its definition, such as the product dimensions or the tracking and storage dimensions. As the following table shows, a collection of entity maps is created to sync products and related information.

Finance and Operations apps | Other Dynamics 365 apps | Description
-----------------------|--------------------------------|---
Organization hierarchy purposes | msdyn_internalorganizationhierarchypurposes | This template provides one-way synchronization of the Organization Hierarchy Purpose entity.
Organization hierarchy type | msdyn_internalorganizationhierarchytypes | This template provides one-way synchronization of the Organization Hierarchy Type entity.
Organization hierarchy - published | msdyn_internalorganizationhierarchies | This template provides one-way synchronization of the Organization Hierarchy Published entity.
Operating unit | msdyn_internalorganizations | 
Legal entities | msdyn_internalorganizations | 
Legal entities | cdm_companies | Provides bidirectional synchronization of legal entity (company) information.


[!include [banner](../../includes/dual-write-symbols.md)]

[!include [Organization hierarchy purposes](includes/OrganizationHierarchyPurpose-msdyn-internalorganizationhierarchypurposes.md)]

[!include [Organization hierarchy type](includes/OrganizationHierarchyType-msdyn-internalorganizationhierarchytypes.md)]

[!include [Organization hierarchy - published](includes/OrganizationHierarchyPublished-msdyn-internalorganizationhierarchies.md)]

## Internal Organization

Internal organization information in Common Data Service comes from two entities, **operating unit** and **legal entities**.

[!include [Operating unit](includes/OperatingUnit-msdyn-internalorganizations.md)]

[!include [Legal entities](includes/LegalEntities-msdyn-internalorganizations.md)]

[!include [Legal entities](includes/LegalEntities-Companies.md)]

