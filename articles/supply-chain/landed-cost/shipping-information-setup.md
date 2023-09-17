---
# required metadata

title: Shipping information setup
description: This article describes how to set up shipping information for the Landed cost module.
author: Weijiesa
ms.date: 03/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ITMGoodsDescriptionTable, ITMVesselTable, ITMExporterTable, ITMCommodityCodeTable, ITMCustomsDescription
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-12-04
ms.dyn365.ops.version: 10.0.17
---

# Shipping information setup

[!include [banner](../../includes/banner.md)]

This article describes how to set up shipping information for the **Landed cost** module.

## <a name="description-of-goods"></a>Description of goods

Descriptions of goods help identify a voyage, shipping container, or folio of goods, and the goods in it. You can select a description of goods on the shipping container header or the folio header.

To work with descriptions of goods, go to **Landed cost \> Shipping information setup \> Description of goods**. There, you can view, open, create, and delete records for descriptions of goods. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Description of goods | Enter a unique identification name/number for the type of goods that will use this description. |
| Description | Enter a description of the type of goods in this category. |

## <a name="vessels"></a>Vessels

A vessel is the unique name of a ship or vessel that a shipping company or agency uses. When you create a voyage, you must always either select or enter a vessel for it. If you often use the same vessels, then you can make it faster and easier to create a new voyage by creating a vessel record for each of them, thereby allowing users to select the vessel from a list rather than enter the name or number manually each time.

To work with vessels, go to **Landed cost \> Shipping information setup \> Vessels**. There, you can view, open, create, and delete records for vessels. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Vessel | Enter a unique identification name/number for the ship that will be used to transport goods on a voyage. |
| Description | Enter a description of the vessel. Typically, this description identifies the name of the ship and the shipping company/agent. |
| Mode of delivery | Select the mode of delivery that the vessel uses (such as _Air_, _Ocean_, or _Train_). |

## Exporters

Each exporter record identifies a vendor or exporter that can be defined as the vendor for a voyage. The exporter can be associated with a voyage and used for reporting.

To work with exporters, go to **Landed cost \> Shipping information setup \> Exporters**. There, you can view, open, create, and delete records for exporters. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Exporter | Enter a unique identification name/number for the exporter of goods that are transported on a voyage. |
| Description | Enter a description of the exporter. Typically, this description identifies the full name of the shipping company/agent. |

## Commodity codes

You use commodity codes to help with customs identification and the calculation of duty rates for goods. You can select commodity codes on the **Released products** page. The commodity codes can be used for reporting.

To work with commodity codes, go to **Landed cost \> Shipping information setup \> Commodity codes**. There, you can view, open, create, and delete records for commodity codes. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Commodity code | Enter a unique code for this type of commodity. |
| Description | Enter a description of the commodity type. |

## Customs description

Customs descriptions help identify goods for customs purposes. You can select a customs description on the **Released products** page or on purchase order lines.

To work with customs descriptions, go to **Landed cost \> Shipping information setup \> Customs description**. There, you can view, open, create, and delete records for custom descriptions. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Customs description | Enter a unique code for this type of customs classification. Often, this code will be the official description that is provided by a customs authority for the description and qualitative value of the goods. |
| Description | Enter a description of the customs classification. |
