---
title: Shipping information setup
description: Learn how to set up shipping information for the Landed cost module, including an outline on goods descriptions and a table defining various fields.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: ITMGoodsDescriptionTable, ITMVesselTable, ITMExporterTable, ITMCommodityCodeTable, ITMCustomsDescription
ms.topic: how-to
ms.date: 09/19/2025
ms.custom:
  - bap-template
---

# Shipping information setup

[!include [banner](../../includes/banner.md)]

This article describes how to set up shipping information for the **Landed cost** module.

## <a name="description-of-goods"></a>Description of goods

Descriptions of goods help identify a voyage, shipping container, or folio of goods, and the goods in it. You can select a description of goods on the shipping container header or the folio header.

To work with descriptions of goods, go to **Landed cost** \> **Shipping information setup** \> **Description of goods**. There, you can view, open, create, and delete records for descriptions of goods. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Description of goods | Enter a unique identification name or number for the type of goods that use this description. |
| Description | Enter a description of the type of goods in this category. |

## <a name="vessels"></a>Vessels

A vessel is the unique name of a ship or vessel that a shipping company or agency uses. When you create a voyage, you must always either select or enter a vessel for it. If you often use the same vessels, you can make it faster and easier to create a new voyage by creating a vessel record for each of them. This approach lets users select the vessel from a list rather than enter the name or number manually each time.

To work with vessels, go to **Landed cost** \> **Shipping information setup** \> **Vessels**. There, you can view, open, create, and delete records for vessels. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Vessel | Enter a unique identification name or number for the ship that transports goods on a voyage. |
| Description | Enter a description of the vessel. Typically, this description identifies the name of the ship and the shipping company or agent. |
| Mode of delivery | Select the mode of delivery that the vessel uses, such as *Air*, *Ocean*, or *Train*. |

## Exporters

Each exporter record identifies a vendor or exporter that you can define as the vendor for a voyage. You can associate the exporter with a voyage and use it for reporting.

To work with exporters, go to **Landed cost** \> **Shipping information setup** \> **Exporters**. There, you can view, open, create, and delete records for exporters. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Exporter | Enter a unique identification name or number for the exporter of goods that are transported on a voyage. |
| Description | Enter a description of the exporter. Typically, this description identifies the full name of the shipping company or agent. |

## Commodity codes

Use commodity codes to help with customs identification and the calculation of duty rates for goods. You can select commodity codes on the **Released products** page. Use commodity codes for reporting.

To work with commodity codes, go to **Landed cost** \> **Shipping information setup** \> **Commodity codes**. There, you can view, open, create, and delete records for commodity codes. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Commodity code | Enter a unique code for this type of commodity. |
| Description | Enter a description of the commodity type. |

## Customs description

Customs descriptions help identify goods for customs purposes. You can select a customs description on the **Released products** page or on purchase order lines.

To work with customs descriptions, go to **Landed cost** \> **Shipping information setup** \> **Customs description**. There, you can view, open, create, and delete records for customs descriptions. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Customs description | Enter a unique code for this type of customs classification. Often, this code is the official description that a customs authority provides for the description and qualitative value of the goods. |
| Description | Enter a description of the customs classification. |
