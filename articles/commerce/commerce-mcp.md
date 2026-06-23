---
title: Dynamics 365 Commerce Model Context Protocol (MCP) server (preview)
description: Learn how the Dynamics 365 Commerce MCP server (preview) enables agentic commerce experiences for retailers, including tools, authenticated shopper workflows, client integration, and self-service enablement on a Commerce Scale Unit.
author: ashishmsft
ms.author: asharchw
ms.topic: overview
ms.reviewer: mirao
ms.search.region: Global
ms.date: 06/23/2026
ms.collection:
  - bap-ai-copilot
---
# Dynamics 365 Commerce Model Context Protocol (MCP) server (preview)

> [!IMPORTANT]
> Some or all of the functionality noted in this article is available as part of a [preview release](../fin-ops-core/dev-itpro/get-started/supplemental-terms-previews.md). The content and the functionality are subject to change.

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that connects AI agents to data systems and business logic. The **Dynamics 365 Commerce MCP server** brings that standard to Dynamics 365 Commerce's headless commerce engine. It powers your in-store, e-commerce, call center, and mobile channels as a first-class set of tools that any compatible AI agent can directly call.

With Commerce MCP, the same APIs that drive your storefront also drive an emerging new channel called **agentic commerce**. Shoppers can discover products, build carts, apply discounts, check inventory at nearby stores, complete checkout, and track orders by interacting with an AI agent, and retailers don't have to rebuild their commerce stack to make it happen.

## Supported shopper workflows

The Commerce MCP server supports a wide range of shopper workflows that cover the entire customer journey, from discovery to post-purchase.

- Discover products with inventory availability.
- Check out with personalized promotions, discounts, and coupons.
- Shop as anonymous or authenticated users/registered shoppers.
- View order activity across all channels.

## Why Commerce MCP matters

Generative AI is changing how shoppers find and buy products. They're moving from typing keywords into a search bar to describing intent in natural language to an agent, such as "Find me a waterproof hiking jacket under $150 that I can pick up tomorrow near Bellevue." For that experience to actually convert, the agent needs more than product copy. It needs a real-time inventory, the customer's saved addresses, the same promotion engine that the website uses, and a payment path the retailer trusts.

Commerce MCP addresses this need by exposing your existing Dynamics 365 Commerce headless engine through a standardized protocol:

- **No replatforming**: The MCP server runs on the same Commerce Scale Unit (CSU) that powers your other channels. Pricing, inventory, promotions, tax, payments, and order management stay in one place.
- **Omnichannel consistency**: A discount that autoapplies on the website also autoapplies in the agent. An address saved during a call-center order shows up when a shopper checks out through an agent. An order placed through an agent shows up in the website's order history and the store associate's POS.
- **Agent-platform neutrality**: Build once and connect any compliant client such as Microsoft Copilot Studio, ChatGPT, Azure AI Foundry, or your own agent host.
- **Microsoft-quality evaluations**: Every tool is gated by automated evaluations covering accuracy, schema, end-to-end agent flow, and error handling.

## Business value for retailers in the era of agentic commerce

| Outcome | How Commerce MCP delivers it |
| ------- | ---------------------------- |
| Reach new agentic surfaces without rebuilding | Connect any MCP-compliant agent to the Commerce engine you already operate. |
| Protect margin and pricing integrity | The same promotion, discount, and tax engines run in the agent channel as on the website. No drift, no shadow logic. |
| Convert intent into orders | Real-time inventory, nearby-location availability, saved addresses, and pay-by-link checkout reduce friction at the moment of decision. |
| Recognize the shopper everywhere | Authenticated C2 (consumer) shoppers see their order history, addresses, and status across every channel - agent, web, store, call center. |
| Stay compliant and auditable | Microsoft Entra ID-based authentication, scoped permissions, and Microsoft-quality evaluation gates make the agent channel highly auditable. |
| Move fast, then scale | Self-service enablement on a single CSU lets retailers pilot, and then expand. |

## Connect to the Commerce MCP server

The Commerce MCP server uses the standard MCP protocol over HTTP. Any compliant MCP client can connect to it.

> [!NOTE]
> The examples in the following sections use the placeholder `https://<your-csu-host>/mcp`. Replace it with the MCP endpoint of your enabled Commerce Scale Unit.

### Microsoft Copilot Studio

Copilot Studio supports MCP servers as custom tools. In your agent, add a custom MCP connector pointing at your CSU's MCP endpoint, register the agent's app identity in Microsoft Entra ID, and authorize the client ID in the Commerce **Allowed MCP clients** list (see [Authentication](#authentication)).

### Visual Studio Code

Add the Commerce MCP server to your **mcp.json** file (workspace or user scope):

```json
{
  "servers": {
    "d365-commerce": {
      "url": "https://<your-csu-host>/mcp",
      "transport": "http",
      "auth": {
        "type": "oauth",
        "tenantId": "<your-tenant-id>",
        "clientId": "<your-app-registration-client-id>"
      }
    }
  }
}
```

### Claude Desktop

In **claude_desktop_config.json**, register Commerce MCP under `mcpServers`. Claude Desktop supports HTTP MCP servers with bearer token authentication. Supply a token obtained from your Entra ID app registration.

```json
{
  "mcpServers": {
    "d365-commerce": {
      "url": "https://<your-csu-host>/mcp",
      "headers": {
        "Authorization": "Bearer <entra-id-bearer-token>"
      }
    }
  }
}
```

### OpenAI ChatGPT

> [!NOTE]
> This section is for custom connectors/Responses API.

Register the Commerce MCP endpoint as a remote MCP server on your ChatGPT workspace or in the Responses API `tools` array. Provide the Entra ID bearer token in the `Authorization` header.

## Tools

The Commerce MCP server provides tools that directly map to the headless Commerce engine. Every tool returns the same data shape that the website and store experiences receive. So, the behavior is consistent across channels.

### Catalog and discovery

| Tool | Description |
| ---- | ----------- |
| `search_products` | Search products by keywords with optional refinement filters. It returns products (`RecordId`, `ItemId`, `Name`, `Price`) and available refiners. Use `RecordId` as `Product ID` for `add_product_to_cart` or `get_product_by_id`. |
| `get_product_by_id` | Get complete product details by `RecordId` or `ItemId`. |

### Cart and checkout

| Tool | Description |
| ---- | ----------- |
| `create_cart` | Create an empty cart. Returns the cart ID for subsequent operations. |
| `add_product_to_cart` | Add a product to cart. If the product already exists in the cart, use `update_cart_line` instead. If the operation fails, it might be because you're attempting to add a master product - Use `get_product_by_id` to get the variants and ask the user to select the variant options. |
| `update_cart_line` | Update product quantity in the cart. Set quantity to `0` to remove the item. |
| `get_cart` | Get complete cart details with items, prices, discounts, and taxes. |
| `update_cart_address` | Set customer info and shipping address. It returns the cart with recalculated totals and taxes. |
| `get_cart_delivery_options` | Get available shipping methods with costs. You should invoke `update_cart_address` first. |
| `create_payment_link` | Create a payment link using the delivery method provided by the customer. It requires the following parameters: (1) `update_cart_address` to set the address information, and (2) `get_cart_delivery_options` for the user to select a delivery mode method invoking this action. |

### Discounts and coupons

Promotions configured in Commerce headquarters apply automatically through the agent channel. There's no separate promotion engine. Quantity threshold (including customer-specific), mix and match, payment method, and shipping method discounts autoapply during the cart and checkout flows.

| Tool | Description |
| ---- | ----------- |
| `apply_coupon_code` | Apply a coupon to a cart. It returns the updated cart totals. |
| `remove_coupon_code` | Remove a previously applied coupon. |

### Order activity

| Tool | Description |
| ---- | ----------- |
| `get_order_details` | Get complete details for a specific order for any order identifier supported by Dynamics 365 Commerce. It returns the full order information. For anonymous customers looking up by confirmation number, provide the email used for the order. |
| `get_order_history` | List a signed-in shopper's orders across all channels (web, store, call center, agent). |

### Inventory and locations

| Tool | Description |
| ---- | ----------- |
| `search_store_inventory` | Search product inventory availability across stores. **Important:** `maxStores=1` (default) checks only the current store or warehouse. A result of zero or out-of-stock doesn't mean other stores lack the product. When a user asks about nearby stores, other locations, or whether another store has the item, always invoke again with the `maxStores` value set to `5` or more. For retail store channels, no location is needed for any `maxStores` value - The channel address is used as the search origin. For online channels with `maxStores=1`, no location is needed - It returns the channel's warehouse inventory. For online channels with `maxStores > 1`, the latitude and longitude are required - If these values aren't already known from the conversation, ask the customer for their location before invoking this tool. It returns the available quantity and store details ordered by distance. |

### Saved customer data

| Tool | Description |
| ---- | ----------- |
| `get_saved_delivery_addresses` | Return delivery addresses on file for the authenticated shopper, so the agent can offer a one-tap shipping selection instead of asking the shopper to type an address. |

## Authenticated workflows for C2 shoppers

Commerce MCP provides end-to-end support for authenticated C2 (consumer) shoppers. Every tool detects the shopper's authentication state and adjusts its behavior:

- **Anonymous calls** return public catalog, pricing, and inventory data, and support guest cart and pay-by-link checkout.
- **Authenticated calls** unlock customer-specific pricing, customer-specific discounts, saved addresses, order history, and order tracking.

Authentication is propagated as a user context on top of the agent's app identity (see [Authentication](#authentication)). The shopper signs in once through the agent's host (for example, an OBO flow from Copilot Studio or a delegated sign-in in a custom agent), and the same identity flows through to the Commerce engine.

### Order activity across every channel

After authentication, a shopper can ask the agent things such as:

- *"Show me my recent orders"*
- *"Where's my order from last week?"*
- *"What did I buy in store on my last visit?"*

The agent uses `get_order_history` and `get_order_details` to return orders regardless of the channel they were placed on (web, brick-and-mortar POS, call center, mobile, or a previous agent conversation). This behavior is what omnichannel means in practice: the customer sees one history.

### Seamless authenticated checkout

Authenticated checkout removes the slowest part of the conversation, which is typing an address. With Commerce MCP:

1. The shopper builds a cart through the agent.
1. The agent calls `get_saved_delivery_addresses` and presents the addresses on file ("Ship to home in Redmond, or office in Bellevue?").
1. The shopper picks one. The agent calls `update_cart_address` with the chosen address.
1. The agent calls `get_cart_delivery_options` and surfaces shipping choices.
1. The agent calls `create_payment_link`. The shopper completes payment on the hosted pay-by-link page.
1. The order lands in Commerce and is immediately visible to the shopper, the call center, and the store associate's clienteling tools.

No address re-entry. No payment data handled by the agent. Same checkout fidelity as the website.

## Business scenario: Build agentic commerce on Dynamics 365 Commerce

Imagine **Fabrikam Outdoor**, a multinational outdoor retailer running Dynamics 365 Commerce across e-commerce, 250 stores, a call center, and a mobile app. Fabrikam decides to launch an agent on its website and inside its mobile app, and to publish that agent to ChatGPT and Copilot Studio so their customers can shop wherever they already are.

Without Commerce MCP, Fabrikam would have to wrap dozens of custom APIs, replicate its promotion logic, build its own inventory lookup, and reimplement order tracking. Promotions and tax would inevitably drift between channels. Customer service would inherit a long tail of "The agent told me one price, the website charged me another" tickets.

With Commerce MCP, Fabrikam:

1. Enables MCP on a single Commerce Scale Unit from LCS (see [Self-service enablement](#self-service-enablement-on-a-commerce-scale-unit)).
1. Registers their agents as Microsoft Entra ID applications and authorizes their client IDs in the Commerce **Allowed MCP clients** list.
1. Builds the agent in Copilot Studio (for web and mobile experience) and exposes the same agent on ChatGPT and Claude through the MCP endpoint.
1. Ships agentic commerce with the same headless engine that powers their website - same catalog, same prices, same autoapplied promotions, same inventory, same saved addresses, and same orders.

A returning customer:

1. Signs into Fabrikam's mobile app.
1. Asks for a three-season tent under $400 available for store pickup nearby.
1. Sees a mix and match offer the engine autoapplied.
1. Picks a saved home address.
1. Completes pay-by-link.
1. Receives a delivery confirmation.

A week later, the same shopper asks ChatGPT, "Where's my Fabrikam tent?". The MCP-backed agent recognizes the authenticated identity, invokes `get_order_details`, and reports that the product shipped this morning. The order, the promotion, the address, and the status all came from one engine - the one that Fabrikam already operates.

## Self-service enablement on a Commerce Scale Unit

Commerce MCP provides a self-service toggle in Lifecycle Services (LCS) to enable or disable the MCP endpoint on a single Commerce Scale Unit (CSU) at any time, with no Microsoft support ticket required.

> [!IMPORTANT]
> You can enable MCP on only one CSU per environment at a time.

### Enable or disable MCP on a CSU

From the Commerce Scale Unit details page in LCS, select **Enable MCP** to turn on the MCP endpoint for that CSU, or select **Disable MCP** to turn it off for that CSU. The change is self-service and takes effect after the operation completes. The button label reflects the current state.

## Authentication

Commerce MCP authentication aligns with the MCP specification and the Microsoft security baseline. Agents always call Commerce MCP under a user context and present a bearer token issued for that user. The MCP server validates the token and the Commerce platform handles authorization.

### Identity model

Commerce MCP supports two identity modes:

| Mode | Used for | Token shape |
| ---- | -------- | ----------- |
| **User context (C1/C2)** | Personalized data: Saved addresses, order history, customer-specific pricing, and discounts. | Entra ID bearer token carrying a delegated user assertion (for example, an OBO token) representing the signed-in employee (C1) or shopper (C2). |
| **Limited anonymous** | Guest discovery, guest cart, pay-by-link checkout for unauthenticated shoppers. | Entra ID bearer token issued for anonymous shopper access. |

### Authorization

The Commerce platform handles authorization. The platform applies channel, role, and customer-scoped permissions to each tool call based on the identity in the token.

### Tools by identity

| Tool | Anonymous | Authenticated |
| ---- | --------- | ------------- |
| `search_products` | ✓ | ✓ |
| `get_product_by_id` | ✓ | ✓ |
| `create_cart` | ✓ | ✓ |
| `add_product_to_cart` | ✓ | ✓ |
| `update_cart_line` | ✓ | ✓ |
| `get_cart` | ✓ | ✓ |
| `update_cart_address` | ✓ | ✓ |
| `get_cart_delivery_options` | ✓ | ✓ |
| `create_payment_link` | ✓ | ✓ |
| `apply_coupon_code` | ✓ | ✓ |
| `remove_coupon_code` | ✓ | ✓ |
| `search_store_inventory` | ✓ | ✓ |
| `get_order_history` | | ✓ |
| `get_order_details` | | ✓ |
| `get_saved_delivery_addresses` | | ✓ |

## Prerequisites

> [!IMPORTANT]
> Commerce MCP is only available on cloud-hosted Commerce Scale Units. It isn't supported on self-hosted instances, including on-premises and hybrid deployments.

Before you enable Commerce MCP, confirm the following prerequisites:

- A Dynamics 365 Commerce environment with at least one Commerce Scale Unit on version **10.0.48** or later.
- Lifecycle Services (LCS) access with permission to manage the environment's CSUs.
- A Microsoft Entra ID tenant in which you can register agent applications calling the MCP server.

### Commerce MCP Setup

Configure the Microsoft Entra External ID tenant and app registrations that Commerce MCP relies on for authentication.

#### Create a Microsoft Entra External tenant on Azure

This section describes how to create a Microsoft Entra External tenant in the Microsoft Azure portal. For more information, see [Create a new tenant with external configurations](/entra/external-id/customers/how-to-create-external-tenant-portal).

1. Sign in to the [Azure portal](https://portal.azure.com).
1. On the Azure portal page, under **Azure Services**, select **Create a resource**. Make sure to use the subscription and directory that you connect with your Commerce environment.
1. Go to **Identity** > **Microsoft Entra External ID**.
1. On the **Basics** tab, on the **Create a tenant** page, enter the following information:
   - For **Tenant Name**, enter the tenant name (for example, *Contoso Customers*).
   - For **Domain Name**, enter the domain (for example, *Contosocustomers*).
   - For **Location**, select your geographic location. Ensure that it's correct, because you can't change this selection later.
1. Select **Next: Add a subscription**.
1. On the **Add a subscription** tab, enter the following information:
   - For **Subscription**, select your subscription.
   - For **Resource group**, select a resource group. If there are no available resource groups, select **Create new**, add a name, and then select **OK**.
   - If **Resource group location** appears, select the geographic location of the resource group.
1. Select **Next: Review + create**.
1. If the information you entered is verified as correct, select **Create**. The tenant creation process can take up to 30 minutes. You can monitor the progress in the **Notifications** pane. After the tenant is created, you can access it in both the Microsoft Entra administrator center and the Azure portal.

#### App registration for the Retail Server

When you register an application, you create a trust relationship between your app and the Microsoft identity platform. Follow these steps to create the Retail Server app registration:

1. Sign in to the [Azure portal](https://portal.azure.com).
1. If you have access to multiple tenants, use the **Directory + subscription** filter on the top menu to select the tenant where you want to register the application.
1. Search for and select **Microsoft Entra ID**.
1. Under **Manage**, select **App registrations**, and then select **New registration**.
1. Enter a name for your application. Users of your app might see this name, and you can change it later.
1. For **Supported account types**, choose **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
1. Leave the **Redirect URI** field at its default value.
1. Select **Register** to complete the initial app registration.
1. Select **Expose an API** and then select **Add a scope**. Provide the **Scope name**, under **Consent** select **Admins and users**, and provide the admin consent display name and description.
1. Set **State** to **Enabled**.
1. Select **Add scope** to complete the scope registration.
1. After the scope is created, copy the **Application ID URI** (which begins with `api://…`). This value is the Server Resource ID that you use later.

#### App registration for the client

1. Repeat steps 2–8 from the preceding procedure, using a different name for this app registration.
1. Select **API permissions**.
1. On the **Request API permissions** page, select **APIs my organization uses** and search for the Retail Server app you created. Select the API, check the permission, and then in the new window select **Add permissions**.
1. Under **Manage** > **Authentication (Preview)**, select **Settings**, and under the **Web and SPA setting** section, select **Access tokens**.
1. Under **Manage** > **Authentication (Preview)**, select **Redirect URI configuration** and add the agent host URI (for example, the ChatGPT app or Microsoft Copilot Studio agent URI) as the redirect URI.
1. When registration is complete, the Azure portal shows the **Overview** pane for the app registration. Note the **Application (client) ID** - This ID uniquely identifies your application in the Microsoft identity platform.

#### Add a client secret

The client secret is a string value that your app can use to identify itself. You need this value when you configure the AI agent (for example, the ChatGPT app or a Microsoft Copilot Studio agent).

1. In the Azure portal, in **App registrations**, select the client app you registered.
1. Select **Certificates & secrets** > **New client secret**.
1. Add a description for the client secret.
1. Select a duration.
1. Select **Add**.
1. Record the secret's value so that you can use it in your client application configuration.

#### Register the client app

Register the client app in finance and operations so that the Retail Server trusts it:

1. In Commerce Headquarters, go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce shared parameters**.
1. On the **Identity providers** FastTab, select the provider with type **Microsoft Entra ID B2C (access_token)**. The values on the **Relying parties** FastTab are set based on your selection.
1. On the **Relying parties** FastTab, select **Add**. Enter the client ID generated during the client app registration (not the Retail Server app). Set **Type** to **Confidential** and **UserType** to **Application**.
1. On the action pane, select **Save**.
1. Select the new relying party. On the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter the Application ID URI (the `api://…` URI generated during the Retail Server app registration), or the application ID GUID.
1. Go to **Retail and commerce** > **Retail and commerce IT** > **Distribution schedule**, and run Commerce Data Exchange (CDX) job 1110.

### Configure Azure AD B2C for existing e-commerce customers

This guidance applies to existing Dynamics 365 Commerce e-commerce framework customers that use Azure Active Directory B2C tenants to manage customer identities.

The current Dynamics 365 Commerce e-commerce framework uses OpenID Connect (OIDC) ID tokens as part of its default customer sign-in and sign-up experience. However, AI agents and MCP based integrations need OAuth 2.0 access tokens to access protected APIs on behalf of authenticated users.

To enable existing Dynamics 365 Commerce e-commerce customers to interact with AI agents powered by the Commerce MCP server, you can configure the Commerce online channel profile as explained in the following sections. After you complete this configuration, customers can sign in to agent-powered experiences and interact with AI agents backed by the Commerce MCP server.

#### Configure the online channel Azure B2C configuration profile

In Commerce headquarters, open the online channel and create or update the Azure B2C configuration profile with the following values:

- **Tenant name**: Enter the name of the Azure AD B2C tenant that manages customer identities.
- **Login domain name** (optional): This value is used to construct the issuer URL that Commerce uses to retrieve identity provider metadata and access tokens. In most cases, you can leave this field blank. Commerce uses the tenant ID to generate the login domain name automatically, unless the domain in the Azure AD B2C tenant is changed manually.
- **Application ID**: Enter the client ID of the Azure AD B2C application.
- **Application secret**: Enter the client secret for the Azure AD B2C application. For security reasons, don't enter the application secret directly in this field. Store the secret in Azure Key Vault, and then provide the Key Vault configuration details in Commerce headquarters. If Key Vault isn't already configured, go to the next section "Set up Azure Key Vault to store the application secret."
- **Scope**: Enter the access scope URL for the Azure AD B2C application. To learn how to configure the scope, go to the section "Set up the scope for the Azure AD B2C application."
- **Audience**: Enter the target resource that the client application requests access to when acquiring an OAuth 2.0 access token. For this configuration, use the same client ID as the Azure AD B2C application.

:::image type="content" source="media/commerce-mcp-b2c-configuration-profile.png" alt-text="A screenshot displaying the Azure AD B2C configuration profile parameters." lightbox="media/commerce-mcp-b2c-configuration-profile.png":::

#### Set up Azure Key Vault to store the application secret

1. In an Azure subscription that your organization manages, create an Azure Key Vault to store the application secret.
1. Register a client application and create a client secret that the application can use to access the Key Vault.
1. Grant the registered application **Get** and **List** permissions on the Key Vault.
1. Configure the Key Vault settings in Commerce headquarters:
   - **Key Vault URL**: URL of the created Key Vault.
   - **Key Vault Client**: Client ID of the client application created to access the Key Vault.
   - **Key Vault secret key**: Client secret of the application created to access the Key Vault.
   - **Secrets**: Add a secret that points to the secret stored in Azure Key Vault. Use the format `vault://<secret-name>`.

#### Set up the scope for the Azure AD B2C application

1. Add a new scope named `accessUser` to the Azure AD B2C application.
1. Grant admin consent to this scope.

#### Map the online channel profile to the online store

Associate the configured online channel Azure B2C profile with the online store so that shopper sign-in flows use the agent ready configuration.

:::image type="content" source="media/commerce-mcp-b2c-online-store-profile.jpg" alt-text="A screenshot showing how to map the online channel Azure B2C profile to the online store." lightbox="media/commerce-mcp-b2c-online-store-profile.jpg":::

#### Set up the profile in Commerce site builder

Use the Azure AD B2C tenant settings to populate this profile. For the client GUID, use the application that you configured for the online channel profile.

> [!NOTE]
> When you set up the sign-up user policy in the Azure AD B2C tenant, mark the following fields as required: **Email Address**, **Display Name**, **Surname**, and **Given Name**.

:::image type="content" source="media/commerce-mcp-b2c-site-authentication-profile.jpg" alt-text="A screenshot displaying the site authentication profile fields." lightbox="media/commerce-mcp-b2c-site-authentication-profile.jpg":::

:::image type="content" source="media/commerce-mcp-b2c-required-fields.jpg" alt-text="A screenshot showing the required fields in the Azure AD B2C sign-up user policy." lightbox="media/commerce-mcp-b2c-required-fields.jpg":::

## Related information

- [Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
- [Register an application in Microsoft Entra ID](/entra/identity-platform/quickstart-register-app)
- [Microsoft Copilot Studio](/microsoft-copilot-studio/)
