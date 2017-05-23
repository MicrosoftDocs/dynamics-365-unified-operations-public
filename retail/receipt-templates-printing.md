---
# required metadata

title: Receipt templates and printing
description: This article describes how to modify form layouts to control how receipts, invoices, and other documents are printed. Microsoft Dynamics 365 for Operations - Retail includes a form layout designer that you can use to easily create and modify various kinds of form layouts.
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
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 57841
ms.assetid: e530dd8e-95e2-4021-90bd-ce1235f9e250
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Receipt templates and printing

[!include[banner](includes/banner.md)]


This article describes how to modify form layouts to control how receipts, invoices, and other documents are printed. Microsoft Dynamics 365 for Operations - Retail includes a form layout designer that you can use to easily create and modify various kinds of form layouts.

**Important:** You must set up form layouts and receipt profiles to print receipts and other documents from Retail Modern POS and Cloud POS. You can include multiple form layouts in a receipt profile. You can then assign the receipt profile to a printer by modifying a hardware profile.

## Set up a receipt format
1.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS** &gt; **Receipt formats**.
2.  On the **Receipt format** page, click **New** to create a new form layout, or select an existing form layout.
3.  In the **Receipt format** field, enter an identifier for the form layout, and then select the type of receipt that this layout is used for. You can also enter a description and a short name for the receipt in the **Title** field.
4.  On the **General** FastTab, select an option to define the print behavior:
    -   **Always print** – The receipt is printed automatically, as appropriate.
    -   **Do not print** – The receipt isn't printed.
    -   **Prompt user** – The user is prompted to print the receipt.
    -   **As required** – This option is used only for gift receipts. When this option is selected, the user can print a gift receipt from the **Change** page, if a gift receipt is required.

## Design a receipt format
Use the form layout designer to graphically create the layout of the form document. The **Receipt format designer** page has three sections: **Header**, **Lines**, and **Footer**. Some types of form layouts use elements from all three sections, whereas other types use elements from only one or two sections. To view the elements that are available for each section, click the appropriate button in the navigation pane on the left side of the page.

1.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS** &gt; **Receipt formats**.
2.  On the **Receipt format** page, select a form layout, and then click **Designer**.
3.  Click **Run** to start to install the Retail designer host.
4.  On the Notification bar that appears at the bottom of the Internet Explorer window, click **Open** to start to install the one-click designer. (The Notification bar might appear in a different location in other browsers.) The progress indicator shows the progress of the installation process.
5.  After the installation is completed, enter your Dynamics 365 for Operations user name and password, and then click **Sign in** to start the designer.
6.  After your credentials are validated and the designer starts, you can start to design the receipt format or modify an existing format.
7.  To create the elements of the form, select the **Header**, **Lines**, or **Footer** section, and then drag an element from that section to the workspace. Most elements contain variables that are automatically populated with data from the database. Other elements, such as **Text**, let you print custom text on the receipt. **Note:** You can specify how many lines each section spans by adjusting the number in the lower-right corner of that section. To make it easier to modify a section, increase its height by dragging the sizing bar at the bottom of the section. The height of the section on the workspace doesn't affect the number of lines on the actual receipt.
8.  After you drag an element to the workspace, set the properties for the part in the **Object information** pane at the bottom of the page. Enter one or more of the following settings:
    -   **Align** – Set the alignment of the field to either **Left** or **Right**.
    -   **Fill char** – Specify the white space character. By default, an empty space is used, but you can enter any character.
    -   **Prefix** – Enter the value that appears at the beginning of the field. This setting applies only to the **Lines** section of the layout.
    -   **Characters** – Specify the maximum number of characters that the field can contain if the element contains a variable. If the text in the field is longer than the number of character that you specify, the text is truncated to fit the field.
    -   **Variable** – This check box is selected automatically if the element contains a variable and can't be customized.
    -   **Font type** – Set the font style to either **Regular** or **Bold**. Bold letters use two times as much space as regular letters. Therefore, some characters might be truncated.
    -   **Font size** – Set the font size to either **Regular** or **Large**. Large letters are two times higher than regular letters. Therefore, using large letters may lead to overlapping text in the receipt.
    -   **Delete** – Click this button to remove the selected part from the form layout.

## Assign receipt profiles
Receipt profiles are assigned directly to printers through the hardware profile.

1.  Open the hardware profile by clicking **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profile**.
2.  Select the printer, and then, in the **Receipt profile** field, assign the receipt profile to use on the register.

**Note:** If two printers are used, one printer can be used to print standard 40-column thermal receipts. The second printer is typically used to print full-page receipt types that require more information. These receipt types include customer order receipts and customer invoices.



