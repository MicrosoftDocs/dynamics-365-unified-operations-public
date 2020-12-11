---
# required metadata

title: Shipping information setup
description: 
author: mkirknel
manager: tfehr
ms.date: 12/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mkirknel
ms.search.validFrom: 2020-12-04
ms.dyn365.ops.version: Release 10.0.17
---

# Shipping information setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Continue here -->

## Description of goods

The description of goods can be selected from the shipping container or folio header and is used to assist in identifying a voyage, shipping container, or folio of goods and the goods within them.

To work with goods descriptions, go to **Landed cost \> shipping information setup \> Description of goods**. Here you can view, open, create, and delete description-of-goods records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Description of goods** | The unique description of the type of goods within the defined voyage, shipping container, or folio. |
| **Description** | A description of the type of goods within a voyage, shipping container, or folio. |

## Vessels

A vessel is a unique name of a ship or vessel that is used by the shipping company or agency. At the time of voyage creation, vessels can be selected based on this table or entered into the voyage. These settings are optional and you will normally use them only of you often use the same vessels. A vessel name or number is required when creating a voyage.

To work with vessels, go to **Landed cost \> shipping information setup \> Vessels**. Here you can view, open, create, and delete vessels records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Vessel** | The unique description of the ship name/number that will be used to transport goods on a voyage. |
| **Description** | The description of the vessel, generally describing the name of the ship and the shipping company/agent. |
| **Mode of delivery** | The mode of delivery used by the identified vessel (such as _Air_, _Ocean_, or _Train_). |

## Exporters

Each exporter record identifies a vendor or exporter that can be associated as the vendor defined on a voyage. The exporter can be associated to a voyage and used for reporting.

To work with exporters, go to **Landed cost \> Shipping information setup \> Exporters**. Here you can view, open, create, and delete _exporter_ records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Exporter** | A unique name or number that will be used to identify the exporter of goods transported on a voyage. |
| **Description** | The description of the exporter, which is typically the full name of the shipping company/agent. |

## Commodity codes

Commodity codes are used to assist with customs identification and duty rate calculations for goods on a voyage. Commodity codes can be selected from the **Released products** page.

To work with commodity codes, go to **Landed cost \> Shipping information setup \> Commodity codes**. Here you can view, open, create, and delete _commodity code_ records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Commodity code** | A unique code for this type of commodity. |
| **Description** | The description of the commodity type. |

## Customs description

Customs description can be selected on the **Released products** page or on purchase order lines and is used to assist in identifying the goods for customs purposes.

To work with customs descriptions, go to **Landed cost \> Shipping information setup \> Customs description**. Here you can view, open, create, and delete _custom description_ records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Customs description** | A unique code for this type of customs classification. This will often be the official description provided by a customs authority for the description and qualitative value of the goods. |
| **Description** | A description of the customs classification. |
