---
title: Copilot for Inventory Visibility
description: XXXX
author: XXXX
ms.author: XXXX
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: MM/DD/YYYY
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# Copilot for Inventory Visibility

[!include [banner](../includes/banner.md)]

In the fast-paced world of business, efficient inventory management is the linchpin of success. Copilot for Inventory Visibility emerges as the definitive solution to empower organizations across various industries in conquering the complex terrain of inventory management by using natural language.

Copilot for Inventory Visibility introduces an API-driven solution that simplifies and revolutionizes the management of your inventory.

## Prerequisites

To use the Copilot for Inventory Visibility, your system must meet the following requirement:

- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Copilot for Inventory Visibility API

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

Sample Body

```json
   {
        "Text" : "what's the inventory of product D0001 in organization usmf, site 1, location 11"
   }
```

You can change value of `LogLevel` to `Debug`, `Trace`, or `Information` in the body to see more or less detailed information.
