---
# required metadata

title: Set up an e-commerce development environment to debug against a Tier 1 Retail Server VM
description: This topic provides instructions for setting up an e-commerce development environment to debug against a tier 1 Retail Server VM. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Set up an e-commerce development environment to debug against a Tier 1 Retail Server VM

[!include [banner](../../includes/banner.md)]

## Description
Dynamics 365 Commerce Tier 1 environments are generally deployed for Commerce runtime (CRT) and point of sale (POS) extension development. They are standalone environments that don't include e-commerce components. E-commerce comontents aren't included because of the software as a service (SaaS) nature of the architecture. 
There may be scenarios where you want to test calling extensions on a Tier 1 environment to allow debugging of extensions from e-commerce components. General instructions are available in the [Debug against a Tier 1 Commerce development environment](https://docs.microsoft.com/dynamics365/commerce/e-commerce-extensibility/debug-tier-1) topic. You may encounter various content server policy-related errors, though, because of cross-server calls, as the site is now calling a different Retail server.

Below is as sample error that may be displayed. The error below results from selecting a variant on a product details page.

![example error](media/unhandled-rejection-error.jpg)

In the browser debugger tools (F12), a similar error is displayed that mentions the violation of the content security policy directive.

![debugger tools error](media/debugger-tools-error.JPG)

## Resolution

### Disable the CSP check on the site

1. Go to site builder.

1. Select the site you're working on.

1. Select **Settings** in the bottom left navigation, and then select **Extensions**.

1. On the **Content security policy** tab, select **Disable content security policy**.

1. Select **Save and publish**.

> [!NOTE]
> B2C sign-in (user login) won't work in a local development environment. However, you can use guest checkouts or build page mocks to simulate a user login if needed. 

## Additional Resources
- [Get started with e-commerce online extensibility development](../e-commerce-extensibility/sdk-getting-started.md)
- [Manage Content Security Policy (CSP) on e-Commerce site](../manage-csp.md)
