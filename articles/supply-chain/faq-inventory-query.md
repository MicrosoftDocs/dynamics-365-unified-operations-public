---
title: Responsible AI FAQ for Inquire into inventory with Copilot (preview)
description: This FAQ provides answers to frequently asked questions about the AI technology that's used in the "Inquire into inventory with Copilot" feature in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
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

# Responsible AI FAQ for Inquire into inventory with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](includes/preview-banner.md)]

This FAQ provides answers to frequently asked questions about the AI technology that's used in the *Inquire into inventory with Copilot* feature in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [preview-note](includes/preview-note.md)]

## What is Inquire into inventory with Copilot?

*Inquire into inventory with Copilot* is a [feature of Inventory Visibility](inventory/inventory-visibility-copilot-api.md). It accepts natural-language queries for information about products and inventory and returns natural-language responses. The functionality is available both from inside the Inventory Visibility app and through APIs (which developers can code against to create an interactive inventory chatbot for their own applications and web sites)

For example, the input could be:

> What is the inventory for Silver Chronograph Watch in USMF?

And the matching output could be:

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

## What are capabilities of Inquire into inventory with Copilot?

The system allows users of the [Inventory Visibility Add-in](inventory/inventory-visibility.md) to ask natural-language questions about products and their inventory status. The feature analyzes user input and converts incoming natural-language inquiries to the JSON query format required to call the standard product search and on-hand query APIs of Inventory Visibility. The system then converts the response back to natural language so that end users can easily read the information they're looking for.

The functionality is available both from inside the Inventory Visibility app and through APIs. Users of the Inventory Visibility app can access Copilot from anywhere in the application by selecting the Copilot button to open a sidecar chat panel. Developers can customize an existing chatbot or build their own chatbot that can interact through the [Inventory Visibility API](inventory/inventory-visibility-copilot-api.md). 

## What is the intended use of Inquire into inventory with Copilot?

The feature is intended to help daily users (such as web shoppers, salesclerks, and account managers) to quickly identify the product they're looking for and check its stock levels. The feature accepts natural-language input, so users don't need to memorize exact product IDs or search attributes. The feature eliminates the need to navigate through menus, tabs, or fields.

## How was Inquire into inventory with Copilot evaluated? What metrics are used to measure performance?

The system underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using the support email and team channel. Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of Inquire into inventory with Copilot? How can users minimize the impact of these limitations when using the system?

The system doesn't yet support product search by product category or barcode number. To minimize the impact of erroneous responses, your chatbot should be designed to tell users to enter a natural-language prompt that specifies product names, descriptions, or other attributes.

The system works best in US English. While it can be used in other languages, we don't recommend doing so, because it might not function as intended. To minimize the impact to end users and ensure transparency, your chatbot must include a clear, noticeable disclaimer stating that the system is optimized for US English only (for example, *This chatbot is designed to accept input in US English only. Using other languages might affect accuracy and user experience*.) You must use this disclaimer or create your own that meets these requirements.

Your chatbot should limit conversation sessions to 20 rounds or less and it should include a refresh button so users can start a new session.

AI-generated content should never be used without manual review or supervision. The feature applies filters on the input and output to restrict the system to only answer questions relevant to products and inventory, and only continue conversations that include benign questions and answers.

The system might lack contextual awareness and could therefore ask users to enter identical or similar conditions and questions.

## What operational factors and settings allow for effective and responsible use of Inquire into inventory with Copilot?

It's possible to call the Inquire into inventory with Copilot from a third-party logistics (3PL) application. If you choose to do this, then you must take responsibility for filtering the return messages if you need to restrict the output content.

To ensure transparency, your chatbot must include a clear, noticeable disclaimer stating that responses are generated by AI. For example, a disclaimer such as *AI-generated content can contain mistakes – please review* indicates to users that they're interacting with an AI system and AI-generated content. You must use this disclaimer or create a similar one that meets these requirements.

## See also

- [Inquire into inventory with Copilot (preview)](inventory/inventory-visibility-copilot-api.md)
