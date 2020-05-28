---
# required metadata

title: Dynamics 365 Commerce authenticaion flow
description: This topic provides an overview of the various authentication flows for the Dynamics 365 Commerce solution.
author: samjarawan
manager: AnnBe
ms.date: 04/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: RetailITWorkspace
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: samjar
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: Release 10.0.11

---

# Dynamics 365 Commerce authentication flow

[!include [banner](includes/banner.md)]

This topic provides an overview of the various authentication flows for the Dynamics 365 Commerce solution. While there are a number of different authentication scenarios and flows currently supported on the Dynamics 365 Commerce solution as described below, it is worth noting that the core authentication infrastructure of the headless commerce engine is fully based on [OpenID Connect](https://openid.net/connect/).

## Overview
### Authentication Methods
Access to each of the APIs on the Headless Commerce Engine (i.e. Commerce Scale Unit) is natively restricted by one or more of the following roles.

1. **Employee**: These APIs require a POS device activation / token and authenticated employee to access.
1. **Customer**: These APIs require an authenticated customer and are generally used by e-Commerce site, e.g. to retrieve order history or change customer details.
1. **Application**: These APIs require application level authentication (e.g. AAD service to service authentication).
1. **Anonymous**: These APIs are primarily used by e-Commerce sites without user login.
1. **Customized APIs**: Access to these APIs can be restricted using any of the method described above, e.g. POS devices, end-user, or anonymous authentication.

The full list of Headless Commerce Engine APIs and their access restrictions can be found under [Commerce Scale Unit customer and consumer APIs](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api).

(./media/commerce-component-overview.jpg)
