---
title: Inquire into inventory with Copilot through API (preview)
description: The inventory visibility service interacts with Microsoft Copilot to provide a natural-language inventory search function. The functionality is implemented as an API, so developers can easily integrate it into their own applications and web sites. 
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


# Inquire into inventory with Copilot through API (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

The inventory visibility service interacts with Copilot in Dynamics 365 Supply Chain Management to provide a natural-language inventory search feature. It lets users ask questions about inventory and receive answers in real time. The functionality is provided as an API, so developers can easily use it to create an interactive inventory chatbot for their own applications and web sites. By using Copilot, organizations can gain control over their inventory and enhance operational efficiency, ultimately leading to increased profitability and improved customer satisfaction.

For example, a user might send the following natural-language query:

> What is the inventory for Silver Chronograph Watch in USMF?

And Copilot could respond with the following answer:

> Silver Chronograph Watch's product number is 81325. There are 888 Silver Chronograph Watches available in USMF. Here are the details:
>
> Location: Site 1, Location 13
>
> Available ordered quantity: 888<br>
> Available physical quantity: 888<br>
> Physical inventory quantity: 888<br>
> Posted quantity: 888

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use natural-language inventory search with Copilot, your system must meet the following requirement:

- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Use the query API

You submit inventory queries and receive results using the query API, which is defined as follows

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
        "Text" : "What's the inventory of product D0001 in organization USMF, site 1, location 11?"
   }
```

You can choose a level of logging detail for the request by adding the optional `LogLevel` parameter in the body and setting it to `Debug`, `Trace`, or `Information`.
