---
title: Adaptive Card controls
description: Use Adaptive Cards embedded in forms in finance and operations apps
author: jaredha
ms.author: jaredha
ms.topic: article
ms.date: 02/08/2023
ms.reviewer: 
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2024-10-28
ms.dyn365.ops.version: PU66
ms.assetid: 
---

# Adaptive Card controls

[!include [banner](../includes/banner.md)]

[Adaptive Cards](https://learn.microsoft.com/adaptive-cards) are a platform-agnostic way for developers to create rich, interactive card-like interfaces that can be embedded in various applications like Microsoft Teams, Outlook, Copilot Studio chatbots, and other chat or web applications. The key benefit of Adaptive Cards is that they allow developers to design a card once and use it across multiple platforms without needing to adjust the layout for each one. The open card exchange format enables developers to describe content as a simple JSON object, making it easy to structure and manipulate cards dynamically.

The Adaptive Cards control for finance and operations apps enables developers to render Adaptive Cards natively in application forms. See [https://adaptivecards.io] for more information on Adaptive Cards, including documentation, samples, and a designer to get started in building your Adaptive Cards.

## Using Adaptive Cards
The following steps are needed to use Adaptive Cards on forms in finance and operations apps:
1. Configure the Adaptive Card template to define the card layout and formatting.
2. Define the data contract for the data properties that will populate the template.
3. Add the Adaptive Card control to the form.
4. Define the data that will populate the card.

### Configure the Adaptive Card template
The Adaptive Card template defines the layout and formatting of the data on the Adaptive Card control. 

### Add the Adaptive Card control
First, add the Adaptive Card control in the desired placement on your form. 
1. On the form in your development environment for finance and operations apps in Visual Studio, right-click the node in your form design where you want to place the Adaptive Card.
2. On the context menu, select **New > Adaptive card**.
3. On the **Properties** for the control, provide a **Name**, and select the template class created earlier in the **Template class** property.


