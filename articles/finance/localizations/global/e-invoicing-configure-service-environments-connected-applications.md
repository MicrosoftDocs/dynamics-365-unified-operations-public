---
title: Configure service environments and connected applications
description: Learn about how to configure your service environments and connected applications, including an overview on creating a service environment.
author: gionoder
ms.author: johnmichalak
ms.topic: article
ms.date: 02/09/2022
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-07-08
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.12
---

# Configure service environments and connected applications

[!include [banner](../../includes/banner.md)]

This article provides information about how to configure your service environments and connected applications. There are three steps to this process. Step 1 is mandatory, and steps 2 and 3 are optional.

## Step 1: Create a service environment

When you create your service environment, define the list of users who can deploy Globalization features to it. Optionally, for some of the scenarios, define the list of external applications that can communicate with the Electronic Invoicing service. Set up number sequences if you will use them in your scenarios.

To complete this step, see [Service environments](e-invoicing-service-environments.md).

## Step 2: Add certificates and secrets

Add a reference to the Microsoft Azure key vault and secrets to use them in your scenarios. This step is mandatory if actions in the processing pipelines use certificates and secrets for digital signing or communication with external web services.

To complete this step, see [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md).

## Step 3: Configure connected applications

To set up communication between Dynamics 365 Finance or Dynamics 365 Supply Chain Management applications and Electronic invoicing, you must configure Finance or Supply Chain Management to construct the call to the Electronic Invoicing service and prepare business data in a unified structure that can be transformed to the required electronic format. The applications must also correctly process responses from the service. You can complete this configuration directly in your Finance or Supply Chain Management environment, or you can complete it in Regulatory Configuration Service (RCS). If you complete the configuration in RCS, you can then deploy it to your Finance or Supply Chain Management environment. In this step, you will register the connected application for parameter deployment.

To complete this step, see [Connected applications](e-invoicing-connected-applications.md).
