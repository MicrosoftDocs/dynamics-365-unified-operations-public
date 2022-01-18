---
# required metadata

title: Electronic invoicing sign up and installtion overview
description: This topic provides overview of sign up process and installation of Electronic invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]

### Step 1 (Mandatory). Sign up to Regulatory Configuration Services (RCS)
Dynamics 365 Regulatory Configuration Services (RCS) is the functionality providing configuration and design experience, that is used to configure Electronic invoicing. Resources such as environments and electronic invoicing features are created, maintained, and managed in RCS. When the resources are ready, they are published to Electronic invoicing service.
First, you must sign up to RCS as the prerequisites for next steps. 

For RCS sign-up, go to [Regulatory services](https://marketing.configure.global.dynamics.com/).

For more information about RCS, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).

### Step 2 (Mandatory). Install the add-in for microservices in Lifecycle Services
Electronic invoicing service as a set of microservices hosted in Microsoft datacenters. Be default, customers of Dynamics 365 Finance and Supply Chain management applications don't have an access to Electronic invoicing service, and must install it as an Add-in in Lifecycle services. Installation of Add-in results in registering your Finance and Supply Chain management environment in the register of applications allowed to connect to Electronic invoicing service.

To complete the step follow instructions [Install the add-in for microservices in Lifecycle Services](e-inv_tut-setup-electronic-invoicing_install-the-add-in.md).

### Step 3 (Mandatory). Setup Regulatory Configuration Services (RCS)
At this step you will learn how to setup integration between RCS and Electronic invoicing and setup main components.

To complete the step follow instructions [Setup Regulatory Configuration Services (RCS)](e-inv_tut-setup-electronic-invoicing_setup-RC.md).

### Step 4 (Optional). Power platform plug-in admin reference
Some scenarios require integration with Dataverse, in scope of Microsoft Power platform. 
Currently this is the mandatory setup for using Electronic invoicing solutions for Indonesian Electronic invoicing scenarios, and optional setup for Saudi Arabian Electronic invoicing scenarios. You should refer to the [Country specific scenarios](e-inv_country-specific_availability.md) for the details.

To complete the step follow instructions [Power platform plug-in admin reference](e-invoicing-power-platform-plug-in.md).
