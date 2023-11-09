---
title: Copilot for Inventory Visibility
description: Copilot for Inventory Visibility is AI-powered inventory management solution that provides real-time inventory query, seamless system integration, and extensible solutions
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/07/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# Copilot for Inventory Visibility

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Copilot for Inventory Visibility is AI-powered inventory management solution designed to revolutionize the way businesses manage and optimize their inventory. In a dynamic and competitive marketplace, efficient and real-time inventory management is critical for success. Copilot for Inventory Visibility offers a natural-language based feature that provides real-time inventory query, seamless system integration, and extensible solutions. By partnering with Copilot, organizations can gain control over their inventory and enhance operational efficiency, ultimately leading to increased profitability and improved customer satisfaction.

Copilot for Inventory Visibility introduces an API-driven solution that simplifies and revolutionizes the management of your inventory.

## Prerequisites

To use the Copilot for Inventory Visibility, your system must meet the following requirement:

- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Copilot for Inventory Visibility API

You can interact with Copilot for Inventory Visibility by using its API.

```txt
Path:
/Copilot/nl/iv/{environmentId}/query
Method:
    Post
Headers:
    Api-Version="1.0"
Authorization="Bearer $access_token"
x-ms-client-session-id={ your session id }       // New session Id will clear chat history. 
ContentType:
    application/json
Body:
    {
        "Text" : { Your text input }
    }
```

The following example shows sample body content.

```json
   {
        "Text" : "what's the inventory of product D0001 in organization usmf, site 1, location 11"
   }
```

You can choose a level of logging detail for the request by adding the optional `LogLevel` parameter in the body and setting it to `Debug`, `Trace`, or `Information`.
