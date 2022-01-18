---
# required metadata

title: Tutorials - setup Electonic invoicing overview
description: This topic provides overview of Electronic invoicing setup overview
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]


The article describes setup and configuring Electronic invoicing. You must follow the setup steps in the order defined below. If the step is Mandatory, skipping it will result in the not operating functionality and failures you will receive during setup of the next steps or usage of the functionality. There are some Optional steps that can be skipped and setup later if you need to cover related scenarios. 

Please, refer to main Overview section to have an understanding about components and overall processes of Electronic invoicing. This information will help you to setup the components as described below.

First, you need to make sure that all main components are setup correctly, and you have your instance of Regulatory Configuration Service (RCS) after sign up there, and Electronic invoicing Add-in is installed for your Finance and Supply Chain management environments.
Complete the steps described in the section [Sign up and install Electronic invoicing](e-inv_tut-setup-electronic-invoicing_sign-up_overview.md).

As the second step, you must setup Azure resources that will be used by Electronic invoicing during its work. Complete the steps described in section: [Setup Azure resources](e-inv_tut-setup-electronic-invoicing_azure_overview.md).

When main components are configured, you can start working with RCS to setup main logical components of Electronic invoicing. First, you need to define how many Service environments you would like to maintain. This is the logical data and configurations partitioning, to make sure you have a boundary either between development or test environment, and production environments. Moreover, you might require several separate development and test environments to setup you development process in a flexible way. Besides Service environments you should set a link to your business applications, like Dynamics 365 Finance and Supply Chain management environments, to setup parameters required for proper operating with Electronic invoicing, directly from RCS. Refer to [Setup Environments](e-inv_tut-setup-electronic-invoicing_setup-env_overview.md) to get more details about environments.

Now, finally, everything is setup and you can create your own Globalization features that contain definition of scenarios of processing electronic documents and transformation data, or import them from Global repository shared by Microsoft of your partners. You will learn how to work with Globalization features following the article: [Work with Globalization features](e-inv_tut-setup-electronic-invoicing_global-feature_overview.md).

Article **[COMPLETE!: Document processing actions]** contains details on Actions in the Processing pipelines that are the main bricks of the process you will build within Globalization features.

If your scenarios require integration with e-mail or SharePoint for processing inbound electronic documents, you can learn how to setup and use these channels in the article: [Process incoming electronic documents](e-inv_tut-setup-electronic-invoicing_process-incoming_overview.md).
