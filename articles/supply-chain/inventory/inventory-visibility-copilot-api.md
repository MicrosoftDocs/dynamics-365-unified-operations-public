---
title: Inquire into inventory with Copilot (preview)
description: The inventory visibility service interacts with Microsoft Copilot to provide a natural-language inventory search function. The functionality is available both from inside the Inventory Visibility app and through APIs (which developers can code against to create an interactive inventory chatbot for their own applications and web sites).
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


# Inquire into inventory with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->


The inventory visibility service interacts with Copilot in Dynamics 365 Supply Chain Management to provide a natural-language inventory search feature. It lets users ask questions about inventory and receive answers in real time. The functionality is available both from inside the Inventory Visibility app and through APIs (which developers can code against to create an interactive inventory chatbot for their own applications and web sites). By using Copilot, organizations can gain control over their inventory and enhance operational efficiency, ultimately leading to increased profitability and improved customer satisfaction.

For example, a user might send the following natural-language query:

> What's the inventory for Silver Chronograph Watch in USMF?

And Copilot could respond with the following answer:

> Silver Chronograph Watch's product number is 81325. There are 888 Silver Chronograph Watches available in USMF. Here are the details:
>
> Location: Site 1, Location 13
>
> Available ordered quantity: 888<br>
> Available physical quantity: 888<br>
> Physical inventory quantity: 888<br>
> Posted quantity: 888
>
> This is AI-generated content. AI-generated content can contain mistakes – please review.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use natural-language inventory search with Copilot, your system must meet the following requirement:

- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Country/region availability and language support

- Inquire into inventory with Copilot is only available in English. Using it in other languages may affect accuracy and the user experience.  
- Inquire into inventory with Copilot is only available in the North America region.

## Use natural language queries in the Inventory Visibility app

Users of the Inventory Visibility app can use Copilot to ask questions about inventory and receive answers in real time. The following sections describe how to use Copilot in the Inventory Visibility app.

### Open the Copilot panel

To open the Copilot panel from anywhere in the Inventory Visibility app, select the **Copilot** button :::image type="icon" source="media/copilot-icon.png" border="false"::: in the top-right corner.

### Chat with Copilot

In the Copilot panel, you can chat with Copilot to get real-time product and on-hand inventory data by using natural language. Copilot responds to your questions based on the available data in the Inventory Visibility service.

## Use the query API

You submit inventory queries and receive results using the query API, which is defined as follows:

```txt
Path:
    /nl/iv/{environmentId}/query
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

The path URL should resemble the following example: `https://inventoryservice-copilot.weu-il301.gateway.prod.island.powerapps.com/nl/iv/{{Supply_Chain_Management_environment_id}}/query`.

The following example shows sample body content.

```json
   {
        "Text" : "What's the inventory of product D0001 in organization USMF, site 1, location 11?"
   }
```

You can choose a level of logging detail for the request by adding the optional `LogLevel` parameter in the body and setting it to `Debug`, `Trace`, or `Information`.


## See also

- [Responsible AI FAQ for Inquire into inventory with Copilot (preview)](../faq-inventory-query.md)
