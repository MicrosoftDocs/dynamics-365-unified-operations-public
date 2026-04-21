---
title: Modernized customer details page in Store Commerce
description: Learn about the modernized customer details page in Store Commerce POS, including the React-based layout, Copilot insights, extensibility model, and how to enable it.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modernized customer details page in Store Commerce (preview)

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.48 and later

The modernized customer details page in Store Commerce replaces the legacy customer details view with a React-based, responsive experience. The new page surfaces existing capabilities — including Copilot customer insights and recommended products — in a redesigned layout, and introduces a richer extensibility model for partners and ISVs.

This article describes how to enable the modernized customer details page and explains what's available in version 10.0.48.

## Prerequisites

- Store Commerce app version 10.0.48 or later
- The following feature flag must be enabled in Commerce headquarters:
  - `Dynamics.AX.Application.RetailModernCustomerDetailsPageFeature`

> [!NOTE]
> When this feature flag is enabled, the legacy customer details view is automatically replaced. The two views cannot be active simultaneously.

## Enable the modernized customer details page

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
2. Search for **Enable modernized customer details page** and select **Enable now**.
3. Run the **1110 (Global configuration)** distribution schedule job to push the changes to channel databases.
4. Restart the Store Commerce app.

---

## What's new in version 10.0.48

### React-based page architecture

The customer details page has been rebuilt using React and Fluent UI, consistent with the broader Store Commerce modernization effort. The page uses a component-based structure organized into the following areas:

- **Header / customer info section** — renders differently depending on device form factor (desktop vs. phone)
- **Command bar** — a responsive `CustomerDetailsCommandBar` component that adapts label visibility based on screen width
- **Tab bar** — a Fluent UI `TabList` wrapper managing navigation between the four content tabs
- **Tab content area** — each tab renders independently, with key data preloaded for a faster experience

This architecture aligns the customer details page with other modernized views in Store Commerce and enables the extensibility model described later in this article.

### Responsive layout

The page adapts to the device form factor automatically.

- **Desktop:** Full-width header card with customer image, name, contact information, and a horizontal command bar with labeled buttons.
- **Phone/mobile:** Compact header with key identifiers and a simplified action bar. All command bar actions except **Add to sale** are available in the **More actions** drawer. Contact actions such as calling a phone number are accessible directly from the header.

The page is organized into four tabs:

| Tab | Description |
|-----|-------------|
| **Account summary** | High-level overview including Copilot insights and customer wishlists |
| **Timeline** | Customer interaction and purchase event history |
| **Account details** | Shipping addresses, loyalty cards, recent purchases, affiliations, and attributes |
| **Transactions** | Purchase transaction history with inline detail view |

### Command bar actions

Three primary actions are available from the command bar.

| Action | Description |
|--------|-------------|
| **Add to sale** | Adds the customer to the current cart and navigates to the cart view |
| **Add to client book** | Adds the customer to the associate's client book |
| **Edit account** | Opens the customer edit workflow |

### Copilot customer insights

The Copilot **Customer insights** tile is now rendered within the React-based Account summary tab. This is a re-integration of the existing Copilot insights capability into the modernized page structure — the underlying insights content is unchanged from prior releases.

If the summary fails to generate, a refresh control appears on the tile to allow the associate to try again.

### Recommended products carousel

The **Recommended products** carousel appears at the bottom of the page and surfaces AI-suggested products for the customer. Up to 30 products are shown on desktop, and up to 10 on mobile.

- **Desktop:** Fluent UI carousel with previous/next navigation.
- **Phone/mobile:** Horizontally scrollable card list.

Each product card includes an **Add to sale** button that adds the item directly to the cart.

### Create customer shortcut on the transaction page

A new **New customer** shortcut is available on the transaction page toolbar, allowing associates to quickly start a customer creation workflow without navigating away from the transaction.

---

## Extend the customer details page

The modernized customer details page supports the same extensibility model as the legacy customer details view. Existing extensions built for the legacy view are compatible with the modernized page with no changes required.

Extensions can add custom app bar commands to the page command bar by extending `CustomerDetailsExtensionCommandBase` from `PosApi/Extend/Views/CustomerDetailsView`.

Custom controls defined for the customer details view appear in the **Additional** tab, which is shown automatically when any custom controls are present.

Extensions are registered in the POS extension manifest under `components.extend.views.CustomerDetailsView.appBarCommands`.

The manifest schema for a `CustomerDetailsView` extension entry is:

```json
{
  "components": {
    "extend": {
      "views": {
        "CustomerDetailsView": {
          "appBarCommands": [
            {
              "name": "<command name>",
              "description": "<command description>",
              "modulePath": "<relative path to your command module>"
            }
          ]
        }
      }
    }
  }
}
```

### Page events available to extension commands

`CustomerDetailsExtensionCommandBase` exposes message handlers that fire automatically as the page loads data:

| Handler property | Message | Payload type | When it fires |
|-----------------|---------|-------------|---------------|
| `initializeHandler` | `Initialize` | `CustomerDetailsInitializeData` | The extension mounts and receives the initial page state |
| `affiliationAddedHandler` | `AffiliationAdded` | `CustomerDetailsAffiliationAddedData` | An affiliation is added to the customer |
| `loyaltyCardsLoadedHandler` | `LoyaltyCardsLoaded` | `CustomerDetailsLoyaltyCardsLoadedData` | Loyalty card data finishes loading |
| `wishListsLoadedHandler` | `WishListsLoaded` | `CustomerDetailsWishListsLoadedData` | Wishlist data finishes loading |

Assign a function to any of these handler properties in your constructor to respond to the corresponding page event.

---

## Coming in the next release

The following capabilities are under active development and are planned for a future release:

| Capability | Description |
|------------|-------------|
| **Inline add affiliation** | Add affiliations to a customer directly from the Account details tab, without opening a separate dialog |
| **Tag management** | View and manage customer tags from the customer details page |
| **Wishlist product details** | View product names and prices directly within a customer's wishlist on the Account details tab |

> [!NOTE]
> Features listed in this section are subject to change. They do not represent a commitment to ship in any specific release.

---

## Additional resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
- [Copilot in Dynamics 365 Commerce overview](copilot-overview.md)
- [Client book management](clienteling-overview.md)
- [Customer management in Store Commerce](customer-mgmt-stores.md)
