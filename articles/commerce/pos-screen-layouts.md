---
# required metadata

title: POS user interface visual configurations
description: This article provides information about screen layouts for Dynamics 365 Commerce point of sale (POS) experiences.
author: boycezhu
ms.date: 02/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.custom: 90573
ms.assetid: a6868f93-02ed-4928-9f6a-3b7383e7e399
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2016-02-28

---

# POS user interface visual configurations

[!include [banner](includes/banner.md)]


The user interface (UI) of the Microsoft Dynamics 365 Commerce point of sale (POS) can be configured by using a combination of visual profiles and screen layouts that are assigned to stores, registers, and users. This article provides information about those configuration options.

The following illustration shows the relationships among the various entities that make up the configurable aspects of the POS UI.

![POS screen layout entities.](../commerce/media/POS-layout-configuration-entities-diagram.png)

## Visual profile

Visual profiles are assigned to registers, and they specify the visual elements that are register-specific and shared across users. Every user who signs in to the register sees the same theme, layout, colors, and images.

![POS welcome screen with Light theme.](../commerce/media/POS-Welcome-Screen-with-Light-theme.png)

![POS Transaction screen with Dark theme.](../commerce/media/POS-Transaction-Screen-with-Dark-theme.png)

- **Profile number** – The profile number is the unique identifier of the visual profile.
- **Description** – You can specify a meaningful name that will help identify the correct profile for your situation.
- **Theme** – You can select between the **Light** and **Dark** application themes. The theme affects the font and background colors throughout the application.
- **Accent color** – The accent color is used throughout the POS to differentiate or highlight specific visual elements, such as tiles, command buttons, and hyperlinks. Typically, these elements are actionable.
- **Header color** – You can configure the color of the page header to meet the retailer's branding requirements.
- **Font scheme** – You can select between the **Standard** and **Large** font schemes. The font scheme affects the font size throughout the application. The default selection is **Standard**.
- **Always show application bar labels** – When this option is turned on, the label text is always visible under the application bar buttons.
- **Layout** – You can select between the **Centered** and **Right** layouts. The layout affects the alignment of the sign-in box on the sign-in screen. The default selection is **Centered**.
- **Show date/time** – When this option is turned on, the current date and time are shown in the POS header and on the sign-in screen.
- **Keyboard** – You can select between **Default to OS keyboard** and **Show number pad** to specify the default keyboard that is used for input on the sign-in screen. The number pad is a virtual keyboard that is used primarily for touch-based devices. The default selection is **Default to OS keyboard**.
- **Logo image** – You can specify a logo image that is shown on the sign-in screen. We recommend that you use an image that has a transparent background. The file size should be kept as small as possible, because application behavior and performance can be affected when large files are stored and loaded.
- **Login background** – You can specify a background image for the sign-in screen. The file size of background images should be kept as small as possible.
- **Background** – You can specify a background image that is used instead of the solid theme color throughout the application. As for background images for the sign-in screen, the file size should be kept as small as possible.

> [!NOTE]
> The **Right** layout and date/time display don't apply to the sign-in screen in compact view.

You need to run the **1090** (**Registers**) distribution schedule job to synchronize the latest visual profile configurations to the channel database.

## Screen layouts

Screen layout configurations determine the actions, content, and placement of UI controls on the POS **Welcome** screen and **Transaction** screen.

![POS Screen layout view.](../commerce/media/POS-Screen-Layout-View.png)

- **Welcome screen** – In most cases, the welcome screen is the page that users see when they first sign in to the POS. The welcome screen can consist of a branding image and button grids that provide access to POS operations. Typically, operations that aren't specific to the current transaction are put on this screen.

    ![POS welcome screen.](../commerce/media/POS-Welcome-Screen.png)

- **Transaction screen** – The **Transaction** screen is the main screen in the POS for processing sales transactions and orders. The content and layout are configured by using the screen layout designer.

    ![POS Transaction screen.](../commerce/media/POS-Transaction-Screen.png)

- **Default start screen** – Some retailers prefer that cashiers go directly to the **Transaction** screen after sign-in. The **Default start screen** setting lets you specify the default screen that appears after sign-in for each screen layout.

### Assignment

Screen layouts can be assigned at the store, register, or user level. The user assignment overrides the register and store assignments, and the register assignment overrides the store assignment. In a simple scenario where all users use the same layout, regardless of register or role, the screen layout can be set only at the store level. In scenarios where specific registers or users require specialized layouts, those layouts can be assigned.

Depending on which level the screen layouts are assigned, you need to run the **1070** (**Channel configuration**), **1090** (**Registers**), and/or **1060** (**Staff**) distribution schedule jobs to synchronize the latest screen layout configurations to the channel database.

### Layout sizes

Most aspects of the POS UI are responsive, and the layout is automatically resized and adjusted based on the screen size and orientation. However, the POS **Transaction** screen must be configured for every screen resolution that is expected.

At startup, the POS application automatically selects the closest layout size that is configured for the device. A screen layout can also contain configurations for both landscape and portrait modes, and for both full-size and compact devices. Therefore, users can be assigned to a single screen layout that works across various sizes and form factors that are used in the store.

![POS layout sizes.](../commerce/media/POS-Screen-Layout-Sizes.png)

- **Name** – You can enter a meaningful name to identify the screen size.
- **Layout type** – The POS application can show its UI in various modes to provide the best user experience on a given device.

    - **Modern POS – Full** – Full layouts are typically best for larger displays, such as desktop monitors and tablets. You can select the UI elements to include, specify the size and placement of those elements, and configure their detailed properties. Full layouts support both portrait and landscape configurations.
    - **Modern POS – Compact** – Compact layouts are typically best for phones and small tablets. The design possibilities for compact devices are limited. You can configure the columns and fields for the receipt and totals panels. Certain operations that need higher screen resolutions such as reports and inventory management aren't supported in the compact layout. 

- **Width/Height** – These values represent the effective screen size, in pixels, that is expected for the layout. Remember that some operating systems use scaling for high-resolution displays.

> [!TIP]
> You can learn the layout size that is required for a POS screen by viewing the resolution in the app. Start the POS, and go to **Settings \> Session information**. POS shows the screen layout that is currently loaded, the layout size, and the resolution of the app window.

![POS session information page showing the currently loaded screen layout, layout size, and resolution of the app window.](../commerce/media/POS-Session-Information.png)

### Button grids

For each layout size in a screen layout, you can configure and assign button grids for the POS welcome screen and **Transaction** screen. Button grids for the welcome screen are automatically laid out from left to right, from the lowest number (Welcome screen 1) to the highest number.

In Full POS layouts, the placement of button grids is specified in the screen layout designer.

In Compact POS layouts, the button grids are automatically laid out from top to bottom, from the lowest number (Transaction screen 1) to the highest number. They can be accessed on the **Actions** menu.

![Compact layout button grids.](../commerce/media/Compact-View-Button-Grids.png)

> [!NOTE]
> The button sizes in the designer will scale to fit the size of the window, therefore they may not accurately reflect the actual buttons rendered in POS. To best simulate the button grid layout, adjust the designer windows to the same size as the POS.

### Images

For each layout size in a screen layout, you can specify images to include in the POS UI. For Full POS layouts, a single image can be specified for the welcome screen. This image appears as the first UI element on the left. On the **Transaction** screen, images can be used as tab images or as a logo. Compact POS layouts don't use these images.

### Screen layout designer

The screen layout designer lets you configure various aspects of the POS **Transaction** screen for each layout size, in both portrait and landscape modes, and for both Full and Compact layouts. The screen layout designer uses the ClickOnce deployment technology to download, install, and start the latest version of the application every time that users access it. Be sure to check the browser requirements for ClickOnce. Some browsers, such as Google Chrome, require extensions.

> [!IMPORTANT]
> You must configure a screen layout for each layout size that is defined and that is used by the POS.

### Full layout designer

The Full layout designer lets users drag UI controls onto the POS **Transaction** screen and configure the settings of those controls.

![POS Full layout designer (landscape mode).](../commerce/media/POS-Full-Layout-Designer-Landscape.png)

- **Import layout/Export layout** – You can export and import POS screen layout designs as XML files, so that you can easily reuse and share them across environments. It's important that you import layout designs for the correct layout sizes. Otherwise, UI elements might not fit correctly on the screen.
- **Landscape/Portrait** – If the POS device lets users switch between landscape and portrait modes, you must define a screen layout for each mode. The POS automatically detects screen rotation and shows the correct layout.
- **Layout grid** – The POS layout designer uses a 4-pixel grid. UI controls "snap" to the grid to help you correctly align the content.
- **Designer zoom** – You can zoom the designer view in and out to better view the content on the POS screen. This feature is useful when the screen resolution on the POS differs greatly from the resolution of the screen that is used in the designer.
- **Show/hide navigation bar** – For Full POS layouts, you can select whether the left navigation bar is visible on the **Transaction** screen. This feature is helpful for displays that have a lower resolution. To set the visibility, right-click the navigation bar in the designer, and select or clear the **Always visible** check box. If the navigation bar is hidden, POS users can still access it by using the menu in the upper left.

    ![Show/hide navigation bar.](../commerce/media/Navigation-Bar.PNG)

- **POS controls** – The POS layout designer supports the following controls. You can configure many controls by right-clicking and using the shortcut menu.

    ![POS UI controls.](../commerce/media/POS-UI-Controls.png)

    - **Number pad** – The number pad is the main mechanism for user input on the POS **Transaction** screen. You can configure the control so that the full number pad is shown. This option is ideal for touchscreen devices. Alternatively, you can configure it so that only the input field is shown. In this case, a physical keyboard is used for input. The number pad settings are available only for Full layouts. For Compact layouts, the full number pad is always shown on the **Transaction** screen.
    - **Totals panel** – You can configure the totals panel in either one column or two columns, to show values such as the line count, discount amount, charges, subtotal, and tax. Compact layouts support only a single column.
    - **Receipt panel** – The receipt panel contains the sales lines, payment lines, and delivery information for the products and services that are processed in the POS. You can specify columns, widths, and placement. In Compact layouts, you can also configure additional information that appears in the row under the main line.
    - **Customer card** – The customer card shows information about the customer who is associated with the current transaction. You can configure the customer card to hide or show additional information.
    - **Tab control** – You can add the tab control to a screen layout, and then put other controls, such as the number pad, customer card, or button grids, in it. The tab control is a container that helps you fit more content on the screen. The tab control is available only for Full layouts.
    - **Image** – You can use the image control to show the store's logo or another branding image on the **Transaction** screen. The image control is available only for Full layouts.
    - **Recommended products** – If the recommended products control is configured for the environment, it shows product suggestions, based on machine learning.
    - **Custom control** – The custom control acts as a placeholder in the screen layout and lets you reserve space for custom content. The custom control is available only for Full layouts.

### Compact layout designer

Like the Full layout designer, the Compact layout designer lets you configure the POS screen layout for phones and small tablets. However, in this case, the layout itself is fixed. You can configure the controls in the layout by right-clicking and using the shortcut menu. However, you can't use drag-and-drop operations for additional content.

![Compact layout designer.](../commerce/media/Compact-Layout-Designer.png)

### Button grid designer

The button grid designer lets you configure button grids that can be used on the POS welcome screen and **Transaction** screen for both Full and Compact layouts. The same button grid can be used across layouts and layout types. Like the screen layout designer, the button grid designer uses the ClickOnce deployment technology to download, install, and start the latest version of the application every time that users access it. Be sure to check the browser requirements for ClickOnce. Some browsers, such as Google Chrome, require extensions.

![Button grid designer.](../commerce/media/Button-Grid-Designer.png)

- **New button** – Click to add a new button to the button grid. By default, new buttons appear in the upper-left corner of the grid. However, you can arrange buttons by dragging them in the layout.

    > [!IMPORTANT]
    > The contents of the button grid can overlap. When you arrange buttons, make sure that they don't hide other buttons.

- **New design** – Click to automatically set up a button grid layout by specifying the number of buttons per row and column.
- **Button properties** – You can configure button properties by right-clicking the button and using the shortcut menu.

    ![Button grid button properties.](../commerce/media/Button-grid-button-properties.png)

    - **Action** – In the list of applicable POS operations, select the operation that is invoked when the button is clicked in the POS.

        For the list of supported POS operations, see [Online and offline point of sale (POS) operations](pos-operations.md).

    - **Action parameters** – Some POS operations use additional parameters when they are invoked. For example, for the Add product operation, users can specify the product to add.
    - **Button text** – Specify the text that appears on the button in the POS.
    - **Hide button text** – Use this check box to hide or show the button text. Button text is often hidden for small buttons that show only an icon.
    - **Tooltip** – Specify additional Help text that appears when users mouse over the button.
    - **Size in columns/Size in rows** – You can specify how tall and wide the button is.

        ![POS button sizes in rows and columns.](../commerce/media/POS-Button-Sizes-In-Rows-And-Columns.png)

    - **Custom font** – When you select the **Enable custom font for POS** check box, you can specify a font other than the default system font for the POS.
    - **Custom theme** – By default, POS buttons use the accent color from the visual profile. When you select the **Use custom theme** check box, you can specify additional colors.

        > [!NOTE]
        > The Store Commerce app and Store Commerce for web only use the **Back color** and **Font color** values.

    - **Button image** – Buttons can include images or icons. Select among the available images that are specified at **Retail and Commerce \> Channel setup \> POS setup \> POS \> Images**.

![Example button grid in the POS.](../commerce/media/Example-Button-Grid-In-POS.png)

## Additional resources

[Install the Retail point of sale (POS) layout designer](install-pos-layout-designer.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
