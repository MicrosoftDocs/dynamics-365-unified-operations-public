---
# required metadata

title: Configure service environments and connected applications.
description: This topic provides information about how to configure your service environments and connected applications..
author: dkalyuzh
ms.date: 02/09/2022
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
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Configure service environments and connected applications
[!include [banner](../includes/banner.md)]

This topic provides information about setting up service environments and connected applications. This process includes the following three steps:
 - **Create a service environment**: This step is mandatory. 
 - **Add certificates and secrets**: This step is optional.
 - **Configure connected applications**: This step is optiona..

## Create a service environment
When you create your service environment, define the list of users who can deploy Globalization features to this environment. Optionally, for some of the scenarios, define the list of external applications that can communicate with the service. Set up number sequences if you are going to use them in your scenarios. 

To complete this step, see [Service environments](e-invoicing-service-environments.md).

## Add certificates and secrets 
Make a reference to the Key Vault and secrets to use them in your scenarios. This step is required when actions in the processing pipelines use certificates and secrets for digital signing or communicating with external Web services.

To complete this step, see [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md).

## Configure connected applications
Setting up communication between Dynamics 365 Finance or Dynamics 365 Supply Chain management applications and Electronic invoicing, requires that Finance or Supply Chain management be configured to construct the call to the service and prepare business data in a unified structure to be transformed to the required electronic format. The applications must also properly process responses from the service. This configuring can be done directly in your Finance or Supply Chain Management environment, or in RCS. If you complete the configuration in RCS, you can deploy it to your Finance or Supply Chain Management environment. At this step you will register the connected application for the parameters deployment.

To complete this step, see [Connected applications](e-invoicing-connected-applications.md).
