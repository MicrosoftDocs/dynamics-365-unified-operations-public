---
# required metadata

title: Electronic invoicing setup
description: This topic provides an overview of the process for setting up and configuring Electronic invoicing.
author: dkalyuzh
ms.date: 02/28/2022
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

# Electronic invoicing setup

[!include [banner](../includes/banner.md)]

The topic provides an overview of the process for setting up and configuring Electronic invoicing. You must complete the setup steps in the order that is specified here. If a step is mandatory, but you skip it, the functionality won't work correctly, and multiple failures will occur during subsequent steps or when you use the functionality. 

Before you begin, make sure that all main components are set up correctly, that you have signed up for Regulatory Configuration Service (RCS) and have an instance of RCS, and that the Electronic invoicing add-in is installed for your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment. For more information, see [Sign up and install Electronic invoicing](e-invoicing-install-add-in-microservices-lcs.md).

Next, set up the Azure resources that Electronic invoicing requires to do its work. For more information, see [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md).

After the main components are configured, work with RCS to set up the main logical components of Electronic invoicing. First, define the number of service environments that you will maintain. In this way, you define the logical data and configuration partitioning to ensure that you have a boundary between a development or test environment and the production environments. To set up your development process in a flexible way, you might require several separate development and test environments. In addition to defining service environments, set a link to your business applications, such as Finance or Supply Chain Management, directly from RCS to set up the parameters that are required for proper operation with Electronic invoicing. For more information about environments, see [Service environments](e-invoicing-service-environments.md).

After everything is set up, you can create your own Globalization features that define different scenarios for processing electronic documents and transforming data, or for importing the documents from the Global repository. For more information about how to work with Globalization features, see [Work with Globalization features](e-invoicing-working-globalization-features.md).

If your scenarios require integration with email or SharePoint to process inbound electronic documents, see [Processing incoming electronic documents](e-invoicing-process-incoming-electronic-documents.md) for information about how to set up and use those channels.
