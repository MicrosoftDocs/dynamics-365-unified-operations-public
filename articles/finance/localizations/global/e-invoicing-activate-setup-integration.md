---
title: Activate and set up integration with Electronic invoicing
description: Learn how to activate and set up the integration of Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management with Electronic invoicing.
author: gionoder
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2022
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: 
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 
---

# Activate and set up integration with Electronic invoicing

[!include [banner](../../includes/banner.md)]

Before you can activate and set up integration with Electronic invoicing, you must have a Microsoft Dynamics Lifecycle Services (LCS) project that includes Dynamics 365 Finance or Dynamics 365 Supply Chain Management. Additionally, those apps must be deployed in one of the following Azure geographies:

- United States
- Europe
- United Kingdom
- Asia
- Japan
- Switzerland
- Brazil
- United Arab Emirates
- Australia
- Canada
- France
- India

## Enable the Electronic invoicing integration feature

To enable communication between Electronic invoicing and Finance or Supply Chain Management, you must enable the **Electronic Invoicing integration** feature.

1. Sign in to your Finance or Supply Chain Management environment.
2. In the **Feature management** workspace, search for the **Electronic invoicing integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
3. Select the feature, and then select **Enable now**.

## Specify the service endpoint and environment

The service endpoint is the URL where Electronic invoicing is located. Before electronic invoices can be issued, the service endpoint must be configured in Finance and Supply Chain Management to allow for communication with the service.

The environment name that is entered in Finance and Supply Chain Management refers to the name of the service environment that is created in Regulatory Configuration Service (RCS) and published to Electronic invoicing.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
2. On the **Electronic invoicing** tab, in the **Endpoint URL** field, enter the service endpoint that has been specified for your Azure geography by using the **Service endpoint URI** parameter in RCS.
3. In the **Environment** field, enter the name of the service environment that has been published to Electronic invoicing.
4. Select **Save**, and then close the page.
