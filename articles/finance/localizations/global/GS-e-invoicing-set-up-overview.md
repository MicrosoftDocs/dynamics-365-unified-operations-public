---
title: Electronic invoicing setup
description: This article provides an overview of the process for setting up and configuring Electronic invoicing.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ilikond
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing setup

[!include [banner](../../includes/banner.md)]

The article provides an overview of the process for setting up and configuring Electronic invoicing. You must complete the setup steps in the order that is specified here. If a step is mandatory, but you skip it, the functionality won't work correctly, and multiple failures will occur during subsequent steps or when you use the functionality. There are 4 steps to this process. Steps 1 through 4 are required, and step 4 is optional.

### Step 1: Install the add-in for microservices in Microsoft Dynamics Lifecycle Services

The Electronic Invoicing service is a set of microservices that is hosted in Microsoft datacenters. By default, customers of Dynamics 365 Finance and Dynamics 365 Supply Chain Management don't have access to the Electronic Invoicing service. You must install it as an add-in in Microsoft Dynamics Lifecycle Services (LCS). When you install the add-in, your Finance or Supply Chain Management environment is registered in the register of applications that are allowed to connect to the Electronic Invoicing service.

To complete this step, see [Install the add-in for microservices in Lifecycle Services](e-invoicing-install-add-in-microservices-lcs.md).

### Step 2: 

You must s.

To complete this step, see [S](e-invoicing-........md).

### Step 3: Configure the Azure resources for Electronic invoicing

Set up the Azure resources that Electronic invoicing requires to do its work. For more information, see [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md).

### Step 4: Microsoft Power Platform plug-in admin reference

Some scenarios require integration with Dataverse in the scope of Microsoft Power Platform.

Currently, this setup is mandatory if you will use Electronic invoicing solutions for Indonesian electronic invoicing scenarios. However, it's optional for Saudi Arabian electronic invoicing scenarios. For more information, see [Availability of Electronic invoicing features by country or region](e-invoicing-country-specific-availability.md).

To complete this step, see [Microsoft Power Platform plug-in admin reference](../dev-itpro/e-invoicing-power-platform-plug-in.md).











After the main components are configured, work with ....

After everything is set up, you can create your own Globalization features that define different scenarios for processing electronic documents and transforming data, or for importing the documents from the Global repository. For more information about how to work with Globalization features, see [Work with Globalization features](e-invoicing-working-globalization-features.md).

If your scenarios require integration with email or SharePoint to process inbound electronic documents, see [Processing incoming electronic documents](e-invoicing-process-incoming-electronic-documents.md) for information about how to set up and use those channels.

