---
title: Sign up for and install the Electronic Invoicing service
description: This article provides information about how to sign up for and install the Electronic Invoicing service.
author: anuchansoriya
ms.date: 01/22/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: achansoriya 
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Sign up for and install the Electronic Invoicing service

[!include [banner](../../includes/banner.md)]

This article provides information about how to sign up for and install the Electronic Invoicing service. There are three steps to this process.

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
