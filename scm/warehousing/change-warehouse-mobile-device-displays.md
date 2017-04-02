---
# required metadata

title: Warehouse mobile device display settings
description: This article describes how to set up the appearance of a mobile device display and map keyboard shortcuts to controls such as buttons. 
author: YuyuScheller
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, WHSRFColor, WHSRFColorPicker, WHSWorkUserDisplaySettings
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 29071
ms.assetid: 931a02e8-b561-45e3-9c44-06b875ced1b4
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Warehouse mobile device display settings

This article describes how to set up the appearance of a mobile device display and map keyboard shortcuts to controls such as buttons. 

This article applies to "advanced warehousing" features in Warehouse management. Mobile devices can be used for many of the tasks that warehouse workers perform.

## Specify styles and map keyboard shortcuts
As part of the mobile device configuration, you can define different layouts for mobile devices. To do this, you must know the name of the Cascading Style Sheets (CSS) file and the Active Server Page Extension (ASPX) file. Default files are installed as part of the Warehouse Mobile Devices Portal installation. If you don’t know the file names, ask your system administrator. You can define a new style on the **Mobile device display settings** page:

-    In the **CSS file** field, enter the name of your CSS file. Include the .css file name extension.
-   In the **Mobile device display settings view** field, specify the ASPX file. Do **not** include the .aspx file name extension.

The CSS and ASPX files must be located in a specific directory, so that the Internet Information Services (IIS) application can load them. It might be useful to define different CSS files if you're running the mobile device functionality in different browsers or on different kinds of hardware that require different layout control. Simple settings such as the background color, the font and font size for text, and the width and behavior of buttons, can easily be controlled by different use of CSS files. The ASPX file is used to display the mobile site on the server-side ASP.NET application. The file controls how the overall structure of the HTML is laid out. It's a good idea to customize this functionality only if you have serious structural issues with the HTML and JavaScript, and must change this code for your specific devices. To map the HTML controls on the mobile device page to keyboard shortcuts, on the **Mobile device display settings** page, in the **Keyboard shortcut** field, assign the numeric codes for the keys. You can use the **View codes for keyboard shortcuts** menu on the mobile device to find the numeric character codes. Note that the mappings might differ, depending on the hardware that is used. You must use the following syntax to create the mapping:

&lt;control name&gt;(&lt;key name&gt;)=&lt;key code&gt;;

Here is an explanation of the parts of the syntax:

-   **&lt;control name&gt;** – The name of the control (for example, a button) that is rendered in HTML.
-   **(&lt;key name&gt;)** – The name of the keyboard key that you’re creating the shortcut for.
-   **&lt;Key code&gt;** – The numeric character code for the key to use as the shortcut key.

Here is an example:

Cancel(Esc)=27; Full(F2)=113

On all pages that include a **Cancel** button, the button will have this text:

**(Esc) Cancel**

Pressing the Esc key on the keyboard will activate the **Cancel** button. To apply the style and keyboard shortcut settings to a specific device, you must create a mapping in the **Criteria** field. You must use a .NET regular expression to create the mapping, and the expression must consist of three sections that are separated by a vertical bar (|), as shown here:

Request.UserHostAddress=&lt;user host address&gt;|HostName=&lt;user host name&gt;|Request.UserAgent=&lt;user agent&gt;

Here is an explanation of the parts of the expression:

-   **&lt;user host address&gt;** – A .NET regular expression that matches the requestor IP address.
-   **&lt;user host name&gt;** – A .NET regular expression that matches the network name of the requestor.
-   **&lt;user agent&gt;** – A .NET regular expression that matches the identifier of the browser that the requestor uses.

The following example enables Internet Explorer 8 to be used:

Request.UserHostAddress=.\*|HostName=.\*|Request.UserAgent=MSIE\\s8\\.0

You can use the **View server configuration for display settings** menu on the mobile device to find the information about the setup.

## Define text colors for messages
You can use the **Mobile device text colors** page to control the various colors that are used in system-generated messages, such as error messages. For example, the text color can indicate the purpose or severity of the message. The following types of messages are shown.

| Message type | Description                                                                                                                                                                            |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Default      | Default messages use the default color settings for all messages, as defined by the CSS file for the Warehouse Mobile Device Portal.                                                   |
| Error        | Error messages indicate an issue that the user must resolve before he or she can continue.                                                                                             |
| Success      | Success messages confirm that an action was successful.                                                                                                                                |
| Warning      | Warning messages inform the worker that there is an issue, or that there could be an issue if the worker continues. However, the worker doesn't have to resolve the issue to continue. |

To select the color, on the **Select color** page, click in the palette or type a hexadecimal color code.

## Define the date format to use on mobile devices
You can extend the list of accepted date formats for each installation. This capability can be useful if, for example, you want to provide a format that makes it easier for a worker to enter dates on a mobile device. The default format is determined by the user's default language, which is specified in the **Language** field on the **User options** page. (The same page is also used to associate an employee with a specific warehouse work user.) **Note:** The Warehouse Mobile Devices Portal doesn't use the setting of the **Date time and number format** field on the **Language and region preferences** page. To change a date format, you must be familiar with regular expressions in the Microsoft .NET Framework. For more information, see [.NET Framework Regular Expressions](http://go.microsoft.com/fwlink/?LinkId=391260). To define date formats, edit the Dates.ini file that is located at Content\\Settings\\Dates.ini on the Warehouse Mobile Devices Portal server. This file uses .NET regular expressions to specify the date format. The regular expression must contain subexpressions that create named groups for day, month, and year (DDMMYY), as shown in the following example:

^(?&lt;day&gt;\\d{2})(?&lt;month&gt;\\d{2})(?&lt;year&gt;\\d{2})$

Each subexpression requires one to two digits for the day and month, and one to four digits for the year. For example, the following subexpression defines a named group for a year, and requires a minimum of two digits or a maximum of four digits:

(?&lt;year&gt;\\d{2,4})

You can specify more than one expression in the same file. Each expression must be on a separate line. The first expression that is matched is used to parse the date.

See also
--------

[Configuration of mobile devices for warehouse work](configure-mobile-devices-warehouse.md)

