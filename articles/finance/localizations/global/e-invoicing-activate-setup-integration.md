---
title: Activate and set up integration with Electronic invoicing
description: Learn how to activate and set up the integration of Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management with Electronic invoicing.
author: gionoder
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.custom: 
  - bap-template
---

# Activate and set up integration with Electronic invoicing

[!include [banner](../../includes/banner.md)]

Before you can activate and set up integration with Electronic invoicing, you must have a Microsoft Dynamics Lifecycle Services (LCS) project that includes Dynamics 365 Finance or Dynamics 365 Supply Chain Management. Additionally, you must deploy those apps in one of the following Azure geographies:

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
1. In the **Feature management** workspace, search for the **Electronic invoicing integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
1. Select the feature, and then select **Enable now**.

## Specify the service endpoint and environment

The service endpoint is the URL where Electronic invoicing is located. Before electronic invoices can be issued, the service endpoint must be configured in Finance and Supply Chain Management to allow for communication with the service.

The environment name that you enter in Finance and Supply Chain Management refers to the name of the service environment that you create in Regulatory Configuration Service (RCS) and publish to Electronic invoicing.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
1. On the **Electronic invoicing** tab, in the **Endpoint URL** field, enter the service endpoint specified for your Azure geography by using the **Service endpoint URI** parameter in RCS.
1. In the **Environment** field, enter the name of the service environment that you published to Electronic invoicing.
1. Select **Save**, and then close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]