---
title: Modernized customer details page in Store Commerce (preview)
description: Learn about the modernized customer details page in Store Commerce POS, including the React-based layout, Copilot insights, extensibility model, and how to enable it.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 08/14/2026
ms.reviewer: mirao
ms.custom:
  - bap-template
---

# Modernized customer details page in Store Commerce (preview)

[!INCLUDE [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.48 and later

The modernized customer details page in Store Commerce replaces the legacy customer details view with a React-based, responsive experience. The new page surfaces existing capabilities, including Copilot customer insights and recommended products, in a redesigned layout. It also introduces a richer extensibility model for partners and ISVs.

This article describes how to enable the modernized customer details page and explains what's available in versions 10.0.48 and 10.0.49.

## Prerequisites

- Store Commerce app version 10.0.48 or later

> [!NOTE]
> When you enable this feature, the legacy customer details view is automatically replaced. You can't activate both views at the same time.

## Enable the modernized customer details page

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration** > **Workspaces** > **Feature management**).
1. Search for **Enable modernized customer details page** and select **Enable now**.
1. Run the **1110 (Global configuration)** distribution schedule job to push the changes to channel databases.
1. Restart the Store Commerce app.

## What's new in version 10.0.48

### React-based page architecture

The customer details page uses React and Fluent UI, consistent with the broader Store Commerce modernization effort. The page uses a component-based structure organized into the following areas:

- **Header/Customer info section**: Renders differently depending on device form factor (desktop versus phone).
- **Command bar**: A responsive `CustomerDetailsCommandBar` component that adapts label visibility based on screen width.
- **Tab bar**: A Fluent UI `TabList` wrapper managing navigation between the four content tabs.
- **Tab content area**: Each tab renders independently, with key data preloaded for a faster experience.

This architecture aligns the customer details page with other modernized views in Store Commerce and enables the extensibility model described later in this article.

### Responsive layout

The page adapts to the device form factor automatically.

- **Desktop**: Full-width header card with customer image, name, contact information, and a horizontal command bar with labeled buttons.
- **Phone/mobile**: Compact header with key identifiers and a simplified action bar. All command bar actions except **Add to sale** are available in the **More actions** drawer. Contact actions, such as calling a phone number, are directly accessible from the header.

The page is organized into four tabs:

| Tab | Description |
| --- | ----------- |
| **Account summary** | High-level overview including Copilot insights and customer wishlists |
| **Timeline** | Customer interaction and purchase event history |
| **Account details** | Shipping addresses, loyalty cards, recent purchases, affiliations, and attributes |
| **Transactions** | Purchase transaction history with inline detail view |

### Command bar actions

The command bar offers the following three primary actions:

| Action | Description |
| ------ | ----------- |
| **Add to sale** | Adds the customer to the current cart and navigates to the cart view. |
| **Add to client book** | Adds the customer to the associate's client book. |
| **Edit account** | Opens the customer edit workflow. |

### Copilot customer insights

The Copilot **Customer insights** renders within the React-based Account summary tab. This design is a reintegration of the existing Copilot insights capability into the modernized page structure. The underlying insights content is unchanged from prior releases.

If the summary fails to generate, a refresh control appears on the tile to allow associates to try again.

### Recommended products carousel

The **Recommended products** carousel appears at the bottom of the page and surfaces AI-suggested products for the customer. Up to 30 products show on desktop, and up to 10 on mobile.

- **Desktop**: Fluent UI carousel with previous and next navigation.
- **Phone and mobile**: Horizontally scrollable card list.

Each product card includes an **Add to sale** button that adds the item directly to the cart.

### Create customer shortcut on the transaction page

A new **New customer** shortcut is available on the transaction page toolbar, so associates can quickly start a customer creation workflow without navigating away from the transaction.

## What's new in version 10.0.49

Commerce version 10.0.49 expands the modernized customer details page. It adds full modern address management, a functional timeline, modern affiliations and wishlist management, loyalty card and attribute editing, headquarters-driven section configuration, and a broader extensibility surface. You can enable all new capabilities by using the same modern customer details page feature flag.

### Address management on the Account details tab

The **Shipping addresses** tile on the Account details tab now supports per-address actions directly from its overflow (**...**) menu, in addition to the existing **Edit** action.

| Action | Description |
| ------ | ----------- |
| **Edit** | Opens the address add and edit experience for the selected address. |
| **Set as primary** | Marks the selected address as the customer's primary address, and unmarks the previous primary address. This action is offered only on non-primary addresses. A confirmation dialog warns that the current primary address is unmarked (if it exists). |
| **Remove** | Soft-deletes (deactivates) the selected address. This action is offered on every address, with a confirmation dialog. |

After any add, edit, set-primary, or remove operation, the tile refreshes in place. The current tab is preserved, and no full page reload occurs. The same actions are available from the mobile actions drawer.

### Manage addresses view

The full-page **Manage addresses** view is now React-based, and provides **Edit**, **Make primary**, and **Remove** actions for each address. This view is also used by the cart shipping flow. When an associate requests a shipping address from the cart, they can pick (select) an address from this view. Backing out cancels the selection without changing the chosen address.

### Wishlist management

In addition to the **Wishlists** tile on the **Account summary** tab, the tile now also appears on the **Account details** tab above **Recent purchases**. The tile is hidden for the default (anonymous) customer. Associates can also view and manage a customer's individual wishlists from the page, including a mobile-optimized wishlists view.

### Timeline tab

The **Timeline** tab surfaces customer purchases and recent activity in a single chronological view. Associates can edit activities directly on the timeline, delete notes, and filter the timeline by date and event type.

### Affiliations management

The modern React view presents the customer's affiliations and replaces the legacy affiliations view. Associates can add and remove customer affiliations from the **Account details** tab.

### Loyalty cards

Associates can add loyalty cards to a customer directly from the customer details flow.

### Modern create and edit customer

Creating and editing customer records now uses the React-based customer add or edit view, consistent with the rest of the modernized experience.

### Section configuration

Administrators can turn customer details page sections on or off, and reorder them, from Commerce headquarters by using POS visual profiles. Both whole sections and the individual components within paired sections can be shown, hidden, and reordered. For setup steps and the full list of configurable sections, see [Configure the customer details page layout in headquarters](#configure-the-customer-details-page-layout-in-headquarters).

### Extensibility enhancements

Version 10.0.49 expands the extensibility surface for the modernized page:

- An extension surface for the standalone modern address add or edit view.
- App bar command extensibility on the compact (phone) layout.
- Safer extension-host lifecycle handling, including disposing of custom controls when the host unmounts.

### Improved error handling

The page presents clearer error states when customer data APIs (for example, **GetCustomer**) fail.

### Resolved issues

- **Recent purchases** > **View all** now opens in card mode, with product images.
- The **Discard changes?** confirmation no longer appears when you don't make any changes.
- Shipping addresses now appear in the correct regional format for customers outside the United States.

## Configure the customer details page layout in headquarters

Starting in version 10.0.49, administrators can control the layout of the modernized customer details page from POS visual profiles in Commerce headquarters, without any code. For each page view, you can control the following aspects:

- **Which sections appear**: Enable or disable whole sections and, for paired sections, the individual components within them.
- **The order in which sections appear**: Move sections (and their components) up or down.

### Turn on layout configuration

A dedicated switch on the POS visual profile controls layout configuration.

1. In Commerce headquarters, go to **Retail and Commerce** > **POS setup** > **POS profiles** > **Visual profiles**.
1. Select the visual profile assigned to your stores.
1. On the **General** FastTab, under **Usability options**, set **Enable customer detail page layout** to **Yes**.

:::image type="content" source="media/pos-modern-customer-details-visual-profile-toggle.png" alt-text="Screenshot of the Enable customer detail page layout option under Usability options on the General FastTab of a POS visual profile." lightbox="media/pos-modern-customer-details-visual-profile-toggle.png":::

> [!NOTE]
> This switch controls only the layout configuration. You must also enable the modernized customer details page, as explained in [Enable the modernized customer details page](#enable-the-modernized-customer-details-page).

### Configure sections and components

When you turn on layout configuration, use the **Customer detail page** section of the visual profile to arrange each page view. It provides a subtab for each view: **Account summary**, **Timeline**, **Account details**, and **Transactions**.

:::image type="content" source="media/pos-modern-customer-details-layout-configuration.png" alt-text="Screenshot of the Customer detail page configuration for a POS visual profile, showing the Sections grid and the Components grid for the Account summary view." lightbox="media/pos-modern-customer-details-layout-configuration.png":::

Each subtab has two grids:

- **Sections (top grid)**: Lists the sections for that view. It has the **Position**, **Section**, and **Enabled** columns. Use the toolbar to arrange them:
  - **Move up** or **Move down**: Change a section's position (its order in POS).
  - **Enable/Disable**: Toggle whether a section appears in POS.
- **Components (bottom grid)**: For a paired section that contains multiple components, select the section row to list its components. Then use the same **Move up**, **Move down**, and **Enable/Disable** actions to order and show or hide each component.

> [!NOTE]
>
> - Paired sections always move together. A paired section (for example, **Customer information & Recent activity**) is positioned as a single unit. You order its inner parts in the **Components** grid.
> - The tab bar itself (**Account summary**, **Timeline**, **Account details**, and **Transactions**) is fixed. You can't configure it.

The following table lists the sections and components that you can configure:

| Page view | Section | Components |
| --------- | ------- | ---------- |
| Account summary | Customer information & Recent activity (paired) | Customer information, Recent activity |
| Account summary | Recent purchases | Not applicable |
| Account summary | Wish lists | Not applicable |
| Account summary | Recommended products | Not applicable |
| Account details | Addresses & Loyalty cards (paired) | Shipping addresses, Loyalty cards |
| Account details | Wish lists | Not applicable |
| Account details | Recent purchases | Not applicable |
| Account details | Affiliations & Attributes (paired) | Affiliations, Attributes |
| Account details | Recommended products | Not applicable |
| Transactions | Recommended products | Not applicable |
| Timeline | Recommended products | Not applicable |

### Publish and default behavior

- After you change the layout, save the visual profile and run the **1090 (Registers)** distribution schedule job. The next CDX channel data download applies the changes to POS.
- Disabled sections are hidden in POS, but they remain in the headquarters list so that you can re-enable them later. Hidden sections leave no empty space in POS.
- If you don't customize a page view, POS uses the default layout with all sections enabled. Therefore, existing visual profiles continue to work without migration.
- Disabling **Enable customer detail page layout** restores the default layout.
- Version 10.0.49 supports enabling, disabling, and reordering the default sections and their components. This version doesn't support adding custom sections from headquarters or fully arbitrary layouts.

## Extend the customer details page

The modernized customer details page supports the same extensibility model as the legacy customer details view. Existing extensions built for the legacy view work with the modernized page without any changes.

By extending `CustomerDetailsExtensionCommandBase` from `PosApi/Extend/Views/CustomerDetailsView`, you can add custom app bar commands to the page command bar.

The custom controls that you define for the customer details view appear in the **Additional** tab. This tab shows automatically when any custom controls are present.

Register extensions in the POS extension manifest under `components.extend.views.CustomerDetailsView.appBarCommands`.

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
| ---------------- | ------- | ------------ | ------------- |
| `initializeHandler` | `Initialize` | `CustomerDetailsInitializeData` | The extension mounts and receives the initial page state. |
| `affiliationAddedHandler` | `AffiliationAdded` | `CustomerDetailsAffiliationAddedData` | An affiliation is added to the customer. |
| `loyaltyCardsLoadedHandler` | `LoyaltyCardsLoaded` | `CustomerDetailsLoyaltyCardsLoadedData` | Loyalty card data finishes loading. |
| `wishListsLoadedHandler` | `WishListsLoaded` | `CustomerDetailsWishListsLoadedData` | Wishlist data finishes loading. |

Assign a function to any of these handler properties in your constructor to respond to the corresponding page event.

## More resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
- [Client book management](clienteling-overview.md)
- [Customer management in Store Commerce](customer-mgmt-stores.md)
