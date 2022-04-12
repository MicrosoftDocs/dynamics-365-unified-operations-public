---
# required metadata

title: Globalization feature components
description: This topic provides an overview of Globalization feature components.
author: dkalyuzh
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Globalization feature components

[!include [banner](../includes/banner.md)]

A Globalization feature is a set of components that define the rules for data transformation in Electronic reporting (ER) configurations. These components include instructions for processing electronic documents and then sending them to or receiving them from external channels. They also include conditions that define when a feature should be run for the incoming business data.

All the components depend on each other. Globalization features make it easy to create and maintain this dependency, and to support lifecycle management and versioning of the set of components.

## Access Electronic invoicing feature components 

1. Sign in to your Regulatory Configuration Service (RCS) account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.

    Globalization features have several components. The **Electronic invoicing features** page includes a separate tab for each component.

    - **Version** – This component supports lifecycle management of the feature. You can use it to manage status for different versions of the feature.
    - **Configurations** – This component lets you manage, view, and edit related ER format and format mapping configurations that are used in the processing pipeline.
    - **Setups** – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.
    - **Environments** – This component lets users of Globalization services, such as an e-invoicing service, manage the environment where the feature version setup is used. It also lets them grant authorization to the users who will have access to the feature version setup.
    - **Organizations** – This component lets users share the feature with external organizations.
    - **Tags** – This component lets you tag features that can be used in the Globalization blueprint for the reference.
