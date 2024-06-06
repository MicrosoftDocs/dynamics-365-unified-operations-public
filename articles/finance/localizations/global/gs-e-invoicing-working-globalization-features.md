---
title: Globalization feature components
description: Access an overview of Globalization feature components, including an overview on acessing electronic invoicing feature components.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.39
---

# Globalization feature components

[!INCLUDE[banner](../../includes/banner.md)]

A Globalization feature is a set of components that define the rules for data transformation in Electronic reporting (ER) configurations. These components include instructions for processing electronic documents and then sending them to or receiving them from external channels. They also include conditions that define when a feature should be run for the incoming business data.

All the components depend on each other. Globalization features make it easy to create and maintain this dependency, and to support lifecycle management and versioning of the set of components.

## Access Electronic invoicing feature components

In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.

Globalization features have several components. The **Electronic invoicing features** page includes a separate tab for each component.

- **Version** – This component supports lifecycle management of the feature. You can use it to manage status for different versions of the feature.
- **Configurations** – This component lets you manage, view, and edit related ER format and format mapping configurations that are used in the processing pipeline.
- **Setups** – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.
- **Tags** – This component lets you tag features that can be used in the Globalization blueprint for the reference.
