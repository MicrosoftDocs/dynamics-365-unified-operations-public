---
# required metadata

title: Sign up for and install the Electronic Invoicing service
description: This topic provides information about how to sign up for and install the Electronic Invoicing service.
author: dkalyuzh
ms.date: 02/07/2022
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

# Sign up for and install the Electronic Invoicing service

[!include [banner](../includes/banner.md)]

This topic provides information about how to sign up for and install the Electronic Invoicing service. There are four steps to this process. Steps 1 through 3 are required, and step 4 is optional.

### Step 1: Sign up for Regulatory Configuration Service

Regulatory Configuration Service (RCS) provides the configuration and design experience that is used to configure Electronic invoicing. Resources such as environments and electronic invoicing features are created, maintained, and managed in RCS. When the resources are ready, they are published to the Electronic Invoicing service.

For more information about RCS, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).

To sign up for RCS, go to the [Regulatory Configuration Service](https://marketing.configure.global.dynamics.com/) page.

### Step 2: Install the add-in for microservices in Microsoft Dynamics Lifecycle Services

The Electronic Invoicing service is a set of microservices that is hosted in Microsoft datacenters. By default, customers of Dynamics 365 Finance and Dynamics 365 Supply Chain Management don't have access to the Electronic Invoicing service. You must install it as an add-in in Microsoft Dynamics Lifecycle Services (LCS). When you install the add-in, your Finance or Supply Chain Management environment is registered in the register of applications that are allowed to connect to the Electronic Invoicing service.

To complete this step, see [Install the add-in for microservices in Lifecycle Services](e-invoicing-install-add-in-microservices-lcs.md).

### Step 3: Set up RCS

You must set up the integration between RCS and the Electronic Invoicing service. You must also set up the main components.

To complete this step, see [Set up Regulatory Configuration Service (RCS)](e-invoicing-set-up-rcs.md).

### Step 4: Microsoft Power Platform plug-in admin reference

Some scenarios require integration with Dataverse in the scope of Microsoft Power Platform.

Currently, this setup is mandatory if you will use Electronic invoicing solutions for Indonesian electronic invoicing scenarios. However, it's optional for Saudi Arabian electronic invoicing scenarios. For more information, see [Availability of Electronic invoicing features by country or region](e-invoicing-country-specific-availability.md).

To complete this step, see [Microsoft Power Platform plug-in admin reference](e-invoicing-power-platform-plug-in.md).
