---
title: Set up and design receipt formats
description: Learn how to set up and design form layouts to control how receipts, invoices, and other documents are printed in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 01/28/2026
ms.topic: how-to
ms.search.form: RetailFormLayout
ms.reviewer: v-griffinc
ms.assetid: e530dd8e-95e2-4021-90bd-ce1235f9e250
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Set up and design receipt formats

[!include [banner](includes/banner.md)]

This article describes how to set up and design form layouts to control how receipts, invoices, and other documents print in Microsoft Dynamics 365 Commerce. Dynamics 365 Commerce includes a form layout designer that you can use to easily create and modify various kinds of form layouts.

> [!IMPORTANT]
> You must set up form layouts and receipt profiles to print receipts and other documents from the Store Commerce app and Store Commerce for web. You can include multiple form layouts in a receipt profile. You can then assign the receipt profile to a printer by modifying a hardware profile.

## Set up a receipt format

To set up a receipt format, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce > Channel setup > POS setup > POS > Receipt formats**.
1. On the **Receipt format** page, select **New** to create a new form layout, or select an existing form layout.
1. In the **Receipt format** field, enter an identifier for the form layout, and then select the type of receipt that this layout is used for. You can also enter a description and a short name for the receipt in the **Title** field.
1. On the **General** FastTab, select an option to define the print behavior:

    - **Always print** – The receipt prints automatically, as appropriate.
    - **Do not print** – The receipt doesn't print.
    - **Prompt user** – The user is prompted to print the receipt.
    - **As required** – This option is used only for gift receipts. When you select this option, the user can print a gift receipt from the **Change** page, if a gift receipt is required.

## Print images

The receipt designer includes a **Logo** variable. Use this variable to specify an image that prints on receipts. Images that print on receipts by using the **Logo** variable should be monochrome bitmap (.bmp) file types. If you specify a bitmap image in the receipt designer but it doesn't print when the receipt is sent to the printer, one of the following problems might be the cause:

- The file size is too large, or the pixel dimensions of the image aren't compatible with the printer. In this case, try to reduce the resolution or dimensions of the image file.
- Some Object Linking and Embedding for Point of Sale (OPOS) printer drivers don't implement the **PrintMemoryBitmap** method that hardware stations use to print logo images. In this case, try to add the following flag to the **HardwareStation.Extension.config** file of your dedicated or shared hardware station:

    `<add name="HardwareStation.UsePrintBitmapMethod" value="true"/>`

## Design a receipt format

Use the form layout designer to graphically create the layout of the form document. The **Receipt format designer** page has three sections: **Header**, **Lines**, and **Footer**. Some types of form layouts use elements from all three sections, whereas other types use elements from only one or two sections. To view the elements that are available for each section, select the appropriate button in the navigation pane on the left side of the page.

To design a receipt format, follow these steps:

1. In headquarters, go to **Retail and Commerce > Channel setup > POS setup > POS > Receipt formats**.
1. On the **Receipt format** page, select a form layout, and then select **Designer**.
1. Select **Run** to start the installation of the Commerce designer host.
1. On the notification bar that appears at the bottom of the Microsoft Edge window, select **Open** to start the installation of the designer. (The notification bar might appear in a different location in other browsers.) The progress indicator shows the progress of the installation process.
1. After the installation is complete, enter your Commerce user name and password, and then select **Sign in** to start the designer.
1. After your credentials are validated and the designer starts, you can start to design the receipt format or modify an existing format.
1. To create the elements of the form, select the **Header**, **Lines**, or **Footer** section, and then drag an element from that section to the workspace. Most elements contain variables that are automatically populated with data from the database. Other elements, such as **Text**, let you print custom text on the receipt.

    > [!NOTE]
    > You can specify how many lines each section spans by adjusting the number in the lower-right corner of that section. To make it easier to modify a section, increase its height by dragging the sizing bar at the bottom of the section. The height of the section on the workspace doesn't affect the number of lines on the actual receipt.

1. After you drag an element to the workspace, set the properties for the part in the **Object information** pane at the bottom of the page. Enter one or more of the following settings:

    - **Align** – Set the alignment of the field to either **Left** or **Right**.
    - **Fill char** – Specify the white space character. By default, an empty space is used, but you can enter any character.
    - **Prefix** – Enter the value that appears at the beginning of the field. This setting applies only to the **Lines** section of the layout.
    - **Characters** – Specify the maximum number of characters that the field can contain if the element contains a variable. If the text in the field is longer than the number of characters that you specify, the text is truncated to fit the field.
    - **Variable** – This check box is selected automatically if the element contains a variable and can't be customized.
    - **Font type** – Set the font style to either **Regular** or **Bold**. Bold letters use two times as much space as regular letters. Therefore, some characters might be truncated.
    - **Font size** – Set the font size to either **Regular** or **Large**. Large letters are two times higher than regular letters. Therefore, using large letters might lead to overlapping text in the receipt.
    - **Delete** – Select this button to remove the selected part from the form layout.

## Assign receipt profiles

Assign receipt profiles directly to printers through the hardware profile.

To assign receipt profiles, follow these steps:

1. In headquarters, go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Hardware profile** to open the hardware profile.
1. Select the printer. In the **Receipt profile** field, assign the receipt profile to use on the register.

> [!NOTE]
> If you use two printers, one printer can print standard 40-column thermal receipts. The second printer typically prints full-page receipt types that require more information. These receipt types include customer order receipts and customer invoices.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
