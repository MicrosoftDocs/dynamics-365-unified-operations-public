---
# required metadata

title: Setting up Electronic invoicing
description: This topic provides an overview of Electronic invoicing setup.
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

# Setting up Electronic invoicing

[!include [banner](../includes/banner.md)]


The topic describes the setup and configuration of Electronic invoicing. The setup steps must be completed in the order defined below. If a step is mandatory, skipping it will result in the functionality not working correctly and you will receive multiple failures during setup or when you use the functionality. There are optional steps that can be skipped and set up later if you need to cover related scenarios. 

Before you begin, make sure that all main components are set up correctly, that you have signed up for your instance of the Regulatory Configuration Service (RCS), and that the Electronic invoicing add-in is installed for your Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment. For more information, see [Sign up and install Electronic invoicing](e-invoicing-install-add-in-microservices-lcs.md).

Next, set up the Azure resources that Electronic invoicing needs to use to perform its work. For more information, see [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md).

When the main components are configured, work with RCS to set up the main logical components of Electronic invoicing. First, define the number of service environments you will maintain. This is the logical data and configurations partitioning where you make sure you have a boundary between a development or test environment, and the production environments. You might require several separate development and test environments to set up your development process in a flexible way. Besides service environments, set a link to your business applications like Dynamics 365 Finance or Dynamics 365 Supply Chain Management directly from RCS to set up the parameters required for proper operating with Electronic invoicing. For more information, see [Service environments](e-invoicing-service-environments.md) to get more details about environments.

After everything is set up, you can create your own Globalization features that contain different scenarios of processing electronic documents and transforming data, or importing the documents from the Global repository. For more information about how to work with Globalization features, see [Work with Globalization features](e-invoicing-working-globalization-features.md).

The topic, **[COMPLETE!: Document processing actions]** provides information about the actions in the processing pipelines that make up the process you will build within Globalization features.

If your scenarios require integration with email or SharePoint to process inbound electronic documents, you can learn how to set up and use these channels in the topic, [Processing incoming electronic documents](e-invoicing-process-incoming-electronic-documents.md).
