---
# required metadata

title: Configure screen layouts for POS
description: This topic provides information about screen layouts for the Microsoft Dynamics 365 for Operations - Retail point of sale (POS) experiences.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 90573
ms.assetid: a6868f93-02ed-4928-9f6a-3b7383e7e399
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure screen layouts for POS

This topic provides information about screen layouts for the Microsoft Dynamics 365 for Operations - Retail point of sale (POS) experiences.

The Microsoft Dynamics 365 for Operations - Retail point of sale (POS) user interface can be configured using a combination of visual profiles and screen layouts, assigned to stores, registers, and/or users.

## Visual profile
Visual profiles are assigned to registers and are used to specify the visual elements that are register-specific and shared across users. Any user who logs into the register will have the same theme, colors, and images. **Profile number** - The profile number is the unique identifier for the Visual profile. **Description** - The description allows you to specify a meaningful name that will help to identify the correct profile for your situation. **Theme** - Users can choose between the Light or Dark application themes. These settings impact the font and background colors throughout the app. **Accent color** - The accent color is used throughout the POS to differentiate or highlight certain visual elements such as tiles, command buttons, or hyperlinks. These elements are typically actionable. **Header color** - The header color allows the user to configure the color of the page header to meet the branding needs of the retailer. This feature is only available in Dynamics 365 for Operations version 1611. **Login backgrounds** - Users can specify a background image for the login screen. The file size of background images should be kept as small as possible, as storing and loading large files can have an impact on the application behavior and performance. **Application background** - The POS can also use an image as a background throughout the application in place of the solid theme color. As with the login backgrounds, it is advised to keep the file size as minimal as possible.

## Screen layouts
Screen layout configuration determines the actions, content, and placement of UI controls in the POS Welcome screen and Transaction screen. **Welcome screen **- In most cases, the Welcome screen is the page that users will see when they first log into POS. The Welcome screen can consist of a branding image and button grids that provide access to POS operations. Typically, operations that are not specific to the current transaction are placed here. **Transaction screen** - The Transaction screen is the main screen in POS for processing sales transactions and orders. The Transaction screen can be configured using the Screen layout designer. **Default start screen** - Some retailers prefer that the cashier navigate directly to the Transaction screen after logging in. The default start screen setting allows users to set this for each screen layout.

### Assignment

Screen layouts can be assigned at the store, register, or user level. The user assignment overrides the register and store assignment, and the register assignment overrides the store assignment. In a simple scenario where all users use the same layout regardless of register or role, the screen layout can be set only at the store. In cases where certain registers or users require specialized layouts, they can be assigned appropriately.

### Layout sizes

This feature only applies to Dynamics 365 for Operations version 1611. Because in many cases screen layouts can be used across multiple screen sizes and resolutions, users can configure their layout and content for each. The POS application will automatically choose the closest layout size for the device at the time of startup. A screen layout can also contain configurations for both full and compact devices. This configuration allows a user to be assigned to a single screen layout that will work across various sizes and form factors within the store. **Modern POS - Full** - Full layouts are typically best used for larger displays such as PC monitors or tablets. Users can choose which UI elements to include, determine their size and placement, and configure their detailed properties. Full layouts support both portrait and landscape configurations. **Modern POS - Compact** - Compact layouts are typically best used for phones or small tablets. Design possibilities are limited for compact devices. Users can configure the columns and fields for the receipt and totals panes.

### Screen layout designer

Each layout size within a screen layout must be configured using the Screen layout designer. The designer allows users to specify and configure the UI elements of the Transaction screen. The Screen layout designer uses ClickOnce to download, install, and launch the latest version of the application each time the user accesses it. Be sure to check browser requirements for using ClickOnce—some browsers, such as Chrome, require extensions. **Number pad** - The number pad is the main user input in the POS Transaction screen. It can be configured to show the entire on-screen pad, which is ideal for touchscreens, or only the input field, which can be used with a physical keyboard. The number pad settings are available in the full layout only. In Dynamics 365 for Operations version 1611, compact layouts always have the full number pad available from the Transaction screen. **Totals panel** - The totals panel can be configured in either one or two columns to show fields such as line count, discount amount, charges, subtotal, and tax. In Dynamics 365 for Operations version 1611, compact layouts only support a single totals column. **Receipt** -** **The receipt panel contains the sales lines, payment lines, and delivery information for the products and services processed in the POS. Users can specify columns, widths, and placement. In compact layouts in Dynamics 365 for Operations version 1611, you can also configure additional information which will appear in the row under the main line. **Customer card** - The customer card shows information pertaining to the customer currently associated with the transaction. The customer card can be configured to hide or show additional information. **Tab control** - The tab control can be placed onto the screen layout, and other controls such as the number pad, customer card, or button grids can be placed inside the tab. The tab control is a container that helps users fit more content in the screen. The tab control is only available for full layouts. **Image **- The image control can be used to show the store logo or other branding image on the transaction screen. The image control is only available for full layouts. **Recommended products** - If configured for the environment, the recommended products control will show product suggestions based on machine learning. The recommended products control is only available for full layouts in Dynamics 365 for Operations version 1611. **Custom control **- The custom control acts as a placeholder within the screen layout to allows users to reserve space for custom content. The custom control is only available for full layouts.

See also
--------

[Install the Retail POS Layout designer](install-pos-layout-designer.md)

