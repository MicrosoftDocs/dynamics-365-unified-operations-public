---
title: Data management and integration by using data entities overview
description: Learn about data management and integration via a brief overview of the mechanics of synchronous and asynchronous integration.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 10/29/2025
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer
ms.assetid: 8aa25787-5920-4277-acff-7011200133f4
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Data management and integration by using data entities overview

[!include [banner](../includes/banner.md)]

This article provides a brief overview of synchronous and asynchronous integration.

## Synchronous services

Synchronous integrations are straightforward. Any entity that has **Is public** enabled is automatically available as a service application programming interface (API) at the following URL: `https://[BaseURL]/Data/<<Data Entity Public Collection Name>>`.

The OData protocol exposes endpoints where you can interact with all public-enabled entities.

**Supported protocol:** OData V4.0

**Data format:** JSON

**Metadata URL:** `https://[BaseURL]/Data/$metadata`

## Data import/export and recurring integration scenarios

Integration through the data management platform provides more capabilities and higher throughput for inserting and extracting data through entities. Typically, data goes through three phases in this integration scenario:

- **Source** – These are inbound data files or messages in the queue. Typical data formats include CSV, XML, and tab-delimited.
- **Staging** – These are automatically generated tables that map closely to the data entity. When **Data management enabled** is **true**, staging tables are generated to provide intermediate storage. This lets the framework do high-volume file parsing, transformation, and some validations.
- **Target** – This is the data entity where data is imported.

The following diagram shows an inbound flow.

:::image type="content" source="./media/over6.png" alt-text="Screenshot of inbound data flow diagram showing the three phases: source files, staging tables, and target data entity.":::

## Known limitations in data import/export

When you import text files, string sizes are limited to 32,768 characters. If there's a string larger than this, the imported string is truncated. This is a limitation in the underlying implementation and is due to SQL Server Integration Services (SSIS).

If you need to import strings that are larger than 32,768 characters, we recommend that you use container entity fields.

For more information, watch the FastTrack Tech Talk video: [Dynamics 365 for Operations – Tech Talk: Integration](https://www.youtube.com/watch?v=fooBvQhIo6I).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
