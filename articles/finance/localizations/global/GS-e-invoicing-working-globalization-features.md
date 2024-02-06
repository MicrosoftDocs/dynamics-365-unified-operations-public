---
title: Globalization features components
description: This article provides an overview of Globalization feature components.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Globalization features components

[!include [banner](../../includes/banner.md)]

A Globalization feature is a set of components that define the rules for data transformation in Electronic reporting (ER) configurations. These components include instructions for processing electronic documents and then sending them to or receiving them from external channels. They also include conditions that define when a feature should be run for the incoming business data.

All the components depend on each other. Globalization features make it easy to create and maintain this dependency, and to support lifecycle management and versioning of the set of components.

## Access Electronic invoicing feature components 

In **Globalization Studio** workspace, select the **Electronic invoicing** tile.

Globalization features have several components. The **Electronic invoicing features** page includes a separate tab for each component.
 - **Version** – This component supports lifecycle management of the feature. You can use it to manage status for different versions of the feature.
 - **Configurations** – This component lets you manage, view, and edit related ER format and format mapping configurations that are used in the processing pipeline.
 - **Setups** – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.
 - **Tags** – This component lets you tag features that can be used in the Globalization blueprint for the reference.

