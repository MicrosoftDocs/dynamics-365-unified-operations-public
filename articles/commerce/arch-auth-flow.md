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

### Supported Authentication Flows 
The following tables describes the set of supported authentication mechanisms for APIs that require either **POS device activation / token** or **end-user authentication**.

|API Category|Scenario|Supported Authentication Method|Required Setup|Additional details|
|----------|-----------|------------|------------|------------|
|**Employee**|**Dynamics 365 POS authentication flows \*** |Simple Cashier Username & Password |Configure worker in Dynamics 365 F&O / Commerce HQ with username and password. |[POS worker logon](https://docs.microsoft.com/en-us/dynamics365/commerce/retail-modern-pos-device-activation#create-a-worker) |
| | |AAD Credentials  |Configure worker in Dynamics 365 F&O / Commerce HQ mapping to AAD credentials. |[Enable Azure Active Directory authentication for POS sign-in](https://docs.microsoft.com/en-us/dynamics365/commerce/aad-pos-logon) |
| | |Extended Logon Credentials (e.g. barcode or MSR)  |Configure worker in Dynamics 365 F&O / Commerce HQ configured for extended logon. |[Set up extended logon functionality for MPOS and Cloud POS](https://docs.microsoft.com/en-us/dynamics365/commerce/extended-logon) |
|**Customer**|**Dynamics 365 e-Commerce authentication flows**|Site user authentication using AAD B2C |Create an AAD B2C application. Add the AAD B2C application to the accepted list of identity providers in Dynamics 365 F&O / HQ. Configure the AAD B2C application in the e-Commerce Site Builder.|[Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant)  [Set up custom pages for user sign-ins](https://docs.microsoft.com/en-us/dynamics365/commerce/custom-pages-user-logins)|
| | |Site user authentication using external identity provider that supports Open ID Connect |Create an AAD B2C application and configure it to support external identity providers.<br>Add the AAD B2C application to the accepted list of identity providers in Dynamics 365 F&O / HQ.</br>Configure the AAD B2C application in the e-Commerce Site Builder. |[Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant) |
| | | |Add the AAD B2C application to the accepted list of identity providers in Dynamics 365 F&O / HQ. | 
| | | |Configure the AAD B2C application in the e-Commerce Site Builder. |[Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant) |
|**Application**|**3rd party app or service authentication flows**|AAD Service to Service / application authentication |Add external identity provider to the accepted list of identity providers in Dynamics 365 F&O / HQ. | |

\* POS logon requires device activation for each terminal. Learn more under [Point of Sale (POS) device activation](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-device-activation).

### Unsupported Authentication Flows

|Scenario|Unsupported scenario|Details|
|----------|-----------|------------|
|**Dynamics 365 POS authentication flows**|**Dynamics 365 POS authentication flows** |Authentication without device activation / token. |All POS related Commerce Scale Unit APIs require a device activation / token for authentication. |

## Dynamics 365 POS Employee Authentication Flows
![Dynamics 365 POS Employee Authentication Flows](./media/arch-auth-flow-1.jpg)

## Dynamics 365 e-Commerce Customer Authentication Flows
![Dynamics 365 POS Employee Authentication Flows](./media/arch-auth-flow-2.jpg)

## 3rd Party e-Commerce Customer Authentication Flows
![Dynamics 365 POS Employee Authentication Flows](./media/arch-auth-flow-3.jpg)

## 3rd Party Application Authentication Flows
![Dynamics 365 POS Employee Authentication Flows](./media/arch-auth-flow-4.jpg)
