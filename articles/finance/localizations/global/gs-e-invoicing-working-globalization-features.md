---
title: Globalization feature components
description: This article provides an overview of Globalization feature components, including an overview on accessing electronic invoicing feature components.
author: ilikond
ms.author: ikondratenko
ms.topic: overview
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.custom: 
  - bap-template
---

# Globalization feature components

[!INCLUDE[banner](../../includes/banner.md)]

A Globalization feature is a set of components that define the rules for data transformation in Electronic reporting (ER) configurations. These components include instructions for processing electronic documents and then sending them to or receiving them from external channels. They also include conditions that define when a feature should run for the incoming business data.

All the components depend on each other. Globalization features make it easy to create and maintain this dependency, and to support lifecycle management and versioning of the set of components.

## Access Electronic invoicing feature components

In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.

Globalization features have several components. The **Electronic invoicing features** page includes a separate tab for each component.

- **Version** – This component supports lifecycle management of the feature. Use it to manage status for different versions of the feature.
- **Configurations** – Use this component to manage, view, and edit related ER format and format mapping configurations that are used in the processing pipeline.
- **Setups** – Use this component to manage the setup of the related feature version for users of Globalization services, such as an e-invoicing service. Therefore, it supports the flexible construction of communication and responses rules.
- **Tags** – Use this component to tag features that you can use in the Globalization blueprint for the reference.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]