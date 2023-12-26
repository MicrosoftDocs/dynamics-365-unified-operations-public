---
title: Control extensibility
description: This article describes the architecture that lets developers extend the user interface and also define new user interface patterns.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: f03f1fc6-4f8f-4f42-8e38-5ecba8eac413
---

# Control extensibility

[!include [banner](../includes/banner.md)]

This article describes the architecture that lets developers extend the user interface and also define new user interface patterns.

You can extend the existing application user interface (UI) and can also define entirely new UI patterns to create compelling new user experiences. By using modern tools such as HTML5, CSS3, and jQuery, developers can define customized visualizations of business data and drastically enhance the program's interaction patterns.

## Server-side architecture

The Control Extensibility Framework takes advantage of the existing and familiar X++ language for developing server-side data access and business logic. There are no artificial restrictions on the code that developers write to build extensible controls. Instead, developers can declaratively define the modeling experience and the run-time behavior through a set of X++ class and method attributes. A developer defines one class for the design-time behavior (the X++ Build Class) and one class for the run-time behavior (the X++ RunTime class).

- In the X++ Build Class, attributes enable the definition of design-time behaviors such as custom properties in the property sheet, the addition of child controls, and extra modeling components.
- In the X++ Runtime Class, attributes are used to define the run-time properties and commands that the extensible control will access from the client. The X++ Runtime Class consumes the X++ Build Class to initialize the run-time properties, based on the values and data bindings that are specified in the property sheet.

## Client-side architecture

The client-side behavior for the control is defined by using HTML and JavaScript. In the context of a Model-View-ViewModel architecture, the HTML for the control is the View, and the JavaScript is the viewmodel. The Control Extensibility Framework provides an HTML-based binding syntax that enables elements in the HTML View to be bound to data fields and properties in the JavaScript viewmodel. In addition, the framework enables visualization behavior to be defined based on conditional expressions or logical evaluations that can react to changes in viewmodel properties or business data. The JavaScript viewmodel is automatically generated at run time, based on the properties and commands that are defined in the X++ runtime for the control. This automatically generated viewmodel lets a developer define an HTML View that consumes the properties and commands that are defined in X++. If a developer wants additional client-side properties and commands, or wants to implement visualization behavior that can't be declaratively defined in the HTML View, the developer can extend the automatically generated viewmodel. The developer can take advantage of the JavaScript framework in conjunction with the powerful jQuery library.

## Control extensibility architecture overview

The following diagram shows the artifacts that are involved and their relation to each other. [![Control extensibility architecture.](./media/extensibilitycontrolarchitecture.png)](./media/extensibilitycontrolarchitecture.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
