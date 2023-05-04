---
title: Dynamics 365 Commerce authentication flows
description: This article provides an overview of the various authentication flows in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: Release 10.0.11
ms.custom: 
ms.assetid: 
ms.search.industry: Retail
ms.search.form: RetailITWorkspace
---

# Dynamics 365 Commerce authentication flows

[!include [banner](includes/banner.md)]

This article provides an overview of the various authentication flows in Microsoft Dynamics 365 Commerce. Although the Dynamics 365 Commerce solution currently supports several authentication scenarios and flows, the core authentication infrastructure of the Commerce Scale Unit (also known as the headless commerce engine) is fully based on [OpenID Connect](https://openid.net/connect/).

## Authentication methods

Access to each of the application programming interfaces (APIs) on the Commerce Scale Unit is natively restricted by one or more of the following roles:

- **Employee** – Access to APIs associated with this role requires point of sale (POS) device activation (a device token) and an authenticated employee.
- **Customer** – Access to APIs associated with this role requires an authenticated customer. E-Commerce sites generally use these APIs for operations such as retrieving order history and changing customer details.
- **Application** – Access to APIs associated with this role requires application-level authentication, such as Azure Active Directory (Azure AD) service-to-service authentication.
- **Anonymous** – APIs associated with this role are primarily used by e-Commerce sites without user authentication.
- **Customized APIs** – Access to APIs associated with this role can be restricted using any of the methods described above such as POS device activation, customer authentication, and anonymous authentication.

For the full list of Commerce Scale Unit APIs and their access restrictions, see [Commerce Scale Unit customer and consumer APIs](dev-itpro/retail-server-customer-consumer-api.md).

### Supported authentication methods

The following table describes the set of supported authentication methods for APIs that require either POS device activation that generates a device token or user authentication that generates a user token.

| API category | Scenario | Supported authentication method | Required setup | Additional details |
|----------|-----------|------------|------------|------------|
| Employee | Dynamics 365 POS authentication flows\* | Simple cashier user name and password | In Dynamics 365 Commerce headquarters, configure a user name and password for a worker. | [Create a worker](retail-modern-pos-device-activation.md#create-a-worker) |
| Employee | Dynamics 365 POS authentication flows\* | Azure AD credentials | In Commerce headquarters, configure a worker that is mapped to Azure AD credentials. | [Enable Azure Active Directory authentication for POS sign-in](aad-pos-logon.md) |
| Employee | Dynamics 365 POS authentication flows\* | Extended sign-in credentials (for example, by using a bar code or a magnetic stripe reader \[MSR\]) | In Commerce headquarters, configure a worker for extended sign-in. | [Set up extended sign-in functionality for Store Commerce app and Store Commerce for web](extended-logon.md) |
| Customer | Dynamics 365 Commerce authentication flows | Site user authentication by using Azure AD B2C with implicit scope flow | <ol><li>Create an Azure AD business-to-consumer (B2C) application.</li><li>In Commerce headquarters, add the Azure AD B2C application to the accepted list of identity providers.</li><li>In Commerce site builder, configure the Azure AD B2C application.</li></ol> | [Set up a B2C tenant in Commerce](set-up-b2c-tenant.md)<p>[Set up custom pages for user sign-ins](custom-pages-user-logins.md)</p> |
| Customer | Dynamics 365 Commerce authentication flows | Site user authentication by using an external identity provider that supports OpenID Connect with implicit scope flow | <ol><li>Create an Azure AD B2C application, and configure it to support external identity providers.</li><li>In Commerce headquarters, add the Azure AD B2C application to the accepted list of identity providers.</li><li>In Commerce site builder, configure the Azure AD B2C application.</li></ol> | [Set up a B2C tenant in Commerce](set-up-b2c-tenant.md)<p>[Set up custom pages for user sign-ins](custom-pages-user-logins.md)</p> |
| Customer | Third-party e-Commerce authentication flows | Site user authentication by using an external identity provider that supports OpenID Connect with implicit scope flow | In Commerce headquarters, add the external identity provider to the accepted list of identity providers. | [Configure authentication providers](/dynamics365/commerce/dev-itpro/configure-authentication-providers) |
| Application | Third-party app or service authentication flows | Azure AD service-to-service authentication/application authentication | In Commerce headquarters, add the external identity provider to the accepted list of identity providers. | |

\* Sign-in to POS requires device activation for each terminal. For more information, see [Point of Sale (POS) device activation](dev-itpro/retail-device-activation.md).

### Unsupported authentication flows

| Scenario | Unsupported authentication method | Details |
|----------|-----------|------------|
| Dynamics 365 POS authentication flows | Authentication without device activation (that is, without a device token) | All POS-related Commerce Scale Unit APIs require a device activation token for authentication. |
| Dynamics 365 Commerce authentication flows | Site user authentication by using Azure AD business-to-consumer (B2C) with authorization code or On-Behalf-Of flows | Authorization code and On-Behalf-Of flows are not currently supported with e-commerce site user authentication. |
| Third-party e-commerce authentication flows | Site user authentication by using an external identity provider that supports OpenID Connect with authorization code or On-behalf-of flows | Authorization code and On-behalf-of flows are not currently supported with e-commerce site user authentication. |

## Dynamics 365 POS employee authentication flows

The following illustration shows POS employee authentication flows in Commerce.

<a href="/dynamics365/commerce/media/arch-auth-flow-1.jpg" target="_blank">![Dynamics 365 POS employee authentication flows.](./media/arch-auth-flow-1.jpg)</a>

## Dynamics 365 e-Commerce customer authentication flows

The following illustration shows e-Commerce customer authentication flows in Commerce.

<a href="/dynamics365/commerce/media/arch-auth-flow-2.jpg" target="_blank">![Dynamics 365 e-Commerce customer authentication flows.](./media/arch-auth-flow-2.jpg)</a>

## Third-party e-Commerce customer authentication flows

The following illustration shows third-party e-Commerce customer authentication flows in Commerce.

<a href="/dynamics365/commerce/media/arch-auth-flow-3.jpg" target="_blank">![Third-party e-Commerce customer authentication flows.](./media/arch-auth-flow-3.jpg)</a>

## Third-party application authentication flows

The following illustration shows third-party application authentication flows in Commerce.

<a href="/dynamics365/commerce/media/arch-auth-flow-4.jpg" target="_blank">![Third-party application authentication flows.](./media/arch-auth-flow-4.jpg)</a>

## Additional resources

[Dynamics 365 Commerce architecture overview](commerce-architecture.md)

[Commerce Scale Unit customer and consumer APIs](dev-itpro/retail-server-customer-consumer-api.md)

[POS worker logon](retail-modern-pos-device-activation.md#create-a-worker)

[Enable Azure Active Directory authentication for POS sign-in](aad-pos-logon.md)

[Set up extended sign-in functionality for Store Commerce app and Store Commerce for web](extended-logon.md)

[Set up a B2C tenant in Commerce](set-up-b2c-tenant.md)

[Set up custom pages for user sign-ins](custom-pages-user-logins.md)

[Configure authentication providers](dev-itpro/configure-authentication-providers.md)

[Point of Sale (POS) device activation](dev-itpro/retail-device-activation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
