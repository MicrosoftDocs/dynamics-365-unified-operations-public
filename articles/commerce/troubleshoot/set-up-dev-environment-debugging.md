---
# required metadata

title: Set up an e-commerce development environment to debug against a Tier 1 Retail Server virtual machine
description: This topic provides instructions for setting up an e-commerce development environment to debug against a Tier 1 Retail Server virtual machine. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/24/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Set up an e-commerce development environment to debug against a Tier 1 Retail Server virtual machine

[!include [banner](../../includes/banner.md)]

This topic provides instructions for setting up an e-commerce development environment to debug against a Tier 1 Retail Server virtual machine.

## Description

Dynamics 365 Commerce Tier 1 environments are generally deployed for Commerce runtime (CRT) and point of sale (POS) extension development. They are standalone environments that don't include e-commerce components. E-commerce components aren't included because of the software as a service (SaaS) nature of the architecture. 

There may be scenarios where you want to test calling extensions on a Tier 1 environment to allow debugging of extensions from e-commerce components. For general instructions on how to do this, see [Debug against a Tier 1 Commerce development environment](../e-commerce-extensibility/debug-tier-1.md). 

When debugging against a Tier 1 environment, you may encounter various content server policy-related errors due to cross-server calls, since the site is now calling a different Retail Server.

The following example image shows an error that may result from selecting a variant on a product details page.

![Error when selecting a variant on a product details page](media/unhandled-rejection-error.jpg)

The following example image shows a similar browser debugger tools (F12) error that mentions violation of the content security policy directive.

![Debugger tools error](media/debugger-tools-error.JPG)

## Resolution

### Disable the content security policy (CSP) for the site in Commerce site builder

1. Select the site you're working on.
1. Select **Settings**, and then select **Extensions**.
1. On the **Content security policy** tab, select **Disable content security policy**.
1. Select **Save and publish**.

> [!NOTE]
> Business-to-consumer (B2C) sign-in won't work in a local development environment. However, you can use guest checkouts or build page mocks to simulate a user sign-in if needed. 

## Additional resources

[Get started with e-commerce online extensibility development](../e-commerce-extensibility/sdk-getting-started.md)

[Manage content security policy (CSP) on e-commerce site](../manage-csp.md)
