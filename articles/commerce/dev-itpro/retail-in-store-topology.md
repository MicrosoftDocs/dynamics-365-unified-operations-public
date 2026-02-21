---
title: Select an in-store topology
description: This article provides an overview of the various Microsoft Dynamics 365 Commerce in-store topologies.
author: Reza-Assadi
ms.date: 02/19/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2019-03-01
ms.search.form: SysMicrosoft Entra IDClientTable, RetailTransactionServiceProfile
ms.custom: 
  - bap-template
---

# Select an in-store topology

[!include [banner](../../includes/banner.md)]

This article provides an overview of the various Microsoft Dynamics 365 Commerce in-store topologies.

<a href="/dynamics365/unified-operations/retail/dev-itpro/media/channel/instore/topology.jpg" rel="Choose the Right Dynamics 365 Retail In-Store Topology diagram.">:::image type="content" source="media/CHANNEL/INSTORE/Topology.jpg" alt-text="Choose the Right Dynamics 365 Retail In-Store Topology diagram.":::</a>

## Supported capabilities when connectivity is lost

| Operation | Without connectivity to Commerce Scale Unit<br>(in Store Commerce app offline mode) | Without connectivity to headquarters<br>(Commerce Scale Unit (self-hosted)) |
| --- | :-: | :-: |
| Cross terminal shifts (such as view, suspend, resume, close) | | ✔ |
| Cross terminal transactions (such as view, suspend, resume)  | | ✔ |

## Supported operations when connectivity is lost

For a list of operations that the POS supports when it loses connectivity to headquarters, see [Online and offline point of sale (POS) operations](/dynamics365/unified-operations/retail/pos-operations).

## Supported deployment and maintenance capabilities

The Store Commerce app supports mass deployment, but Commerce Scale Unit doesn't. For more information, see [Mass deployment of self-service components](/dynamics365/unified-operations/retail/dev-itpro/retail-mass-deployment).

## Deployed components

You deploy the following components through a single installer. You don't need to install them individually.

### Store Commerce app

| Deployed component | Component type | Notes |
| --- | --- | --- |
| Store Commerce app | Windows Application | The Store Commerce app running on the register. |
| Channel Database | SQL Database | Register specific Channel Database instance hosting data for the register.

### Commerce Scale Unit (self-hosted)

| Installed component | Component type | Notes |
| --- | --- | --- |
| Commerce Scale Unit (self-hosted) | Internet Information Services (IIS) Web Service | Scale unit specific Commerce Scale Unit (self-hosted) instance used by one or more stores. |
| Channel Database | SQL Database | Scale unit specific Store specific Channel Database instance hosting data for one or more stores. |
| Async Client Service | Windows Service | Component to synchronize primary record data from the headquarters to the store and transactional data from the store to the headquarters. |
| Store Commerce for web | IIS Web Service | Store Commerce for web application that hosts POS functionality through a web browser. |

## Additional resources

[Offline point of sale (POS) functionality](/dynamics365/unified-operations/retail/pos-offline-functionality)

[Online and offline point of sale (POS) operations](/dynamics365/unified-operations/retail/pos-operations)

[Mass deployment of self-service components](/dynamics365/unified-operations/retail/dev-itpro/retail-mass-deployment)

[Configure and install Commerce Scale Unit (self-hosted)](/dynamics365/unified-operations/retail/dev-itpro/retail-store-scale-unit-configuration-installation)

[Commerce Scale Unit (self-hosted)](/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
