---
# required metadata

title: Sign up for and install the Electronic Invoicing service
description: This topic provides information about how to sign up and install the Electronic Invoicing service.
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

This topic explains how to sign up for and install the Electronic Invoicing service. There are four steps to this process. Steps 1-3 are required and step 4 is optional.

### Step 1: Sign up for the Regulatory Configuration Services 
Dynamics 365 Regulatory Configuration Services (RCS) provides the configuration and design experience that is used to configure Electronic invoicing. Resources such as environments and electronic invoicing features are created, maintained, and managed in RCS. When the resources are ready, they are published to the Electronic invoicing service.
To sign up for RCS, go to [Regulatory services](https://marketing.configure.global.dynamics.com/).

For more information about RCS, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).

### Step 2: Install the add-in for microservices in Lifecycle Services
The Electronic Invoicing service is a set of micro-services hosted in Microsoft datacenters. Be default, customers of Dynamics 365 Finance and Dynamics 365 Supply Chain management applications don't have an access to the Electronic Invoicing service. You must install it as an add-in in Lifecycle services. Installing the add-in registers your Finance or Supply Chain Management environment in the register of applications allowed to connect to the Electronic Invoicing service.

To complete this step, see [Install the add-in for microservices in Lifecycle Services](e-inv_tut-setup-electronic-invoicing_install-the-add-in.md).

### Step 3: Set up the Regulatory Configuration Services (RCS)
You will need to set up the integration between RCS and the Electronic Invoicing service and set up the main components.

To complete this step, see [Set up Regulatory Configuration Services (RCS)](e-invoicing-set-up-rcs.md).

### Step 4: Power platform plug-in admin reference
Some scenarios require integration with Microsoft Dataverse in the scope of Microsoft Power Platform. 
Currently, this is the mandatory setup to use Electronic invoicing solutions for Indonesian Electronic invoicing scenarios, and optional setup for Saudi Arabian Electronic invoicing scenarios. For more information, see [Country-specific scenarios](e-invoicing-country-specific-availability.md).

To complete this step, see [Power platform plug-in admin reference](e-invoicing-power-platform-plug-in.md).
