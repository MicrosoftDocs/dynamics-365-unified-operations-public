---
# required metadata

title: Retail Extension Resource localization
description: This topic explains how to change or modify POS UI labels, POS messages, Receipt labels and Retail server or Commerce runtime error messages.
author: mugunthanm
manager: AnnBe
ms.date: 05/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.search.region: Global 
ms.search.industry: retail
ms.author: mumani
ms.search.validFrom: 2018-05-31
ms.dyn365.ops.version: 8.0.1

---

# Retail Extension Resource localization

[!include[banner](../includes/banner.md)]


This topic explains how to change or modify POS UI labels, POS message, Receipt labels and Retail server or Commerce Runtime Services (CRT) error messages, you can also add custom error messages for Retail and CRT in the same way but for new POS extension labels you should use the localization framework in the POS extension. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail 7.2 with latest update and higher version.

## Retail POS labels and Messages (Error, warning and information)

This topic explains how to change or modify POS UI labels, POS message, Receipt labels and Retail server or CRT error messages, you can also add custom error messages for Retail and CRT in the same way but for new POS extension labels you should use the localization framework in the POS extension. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail 7.2 with latest update and higher version.

### Override POS UI labels and messages

You can override the default strings in the POS by using the language text entries in the language text form. Follow the below steps to change the POS strings:

1.  Login to Dynamics 365 for Retail or Finance and Operations.

2.  Navigate to **Retail &gt; Channel setup &gt; POS setup &gt; POS profiles &gt; Language text**.

3.  Select the **POS** tab in the Language text form.

4.  Under the **POS language text** grid, Click Add button to add the Language ID, Text ID and Text for string you want to override.

    Ex: If you want to change the string shown in the POS LogOn form from Operator ID to Employee ID for en-us, you need to add the below entry in POS language text:

    | **Language ID** | **Text ID** | **Text**    |
    |-----------------|-------------|-------------|
    | en-us           | 502         | Employee ID |

1.  Click Save in the Action bar.

2.  Navigate to **Retail &gt; Retail IT &gt; Distribution schedule**.

3.  Select the Registers (1090) job and click Run now.

4.  Deactivate and Activate POS again to show the updated labels or messages.


### How to get the Text ID for the POS strings

To get the text ID you have to run POS using the Retail SDK in debug mode.

1.  Open Visual Studio 2015 in Administrator mode.

2.  Open ModernPOS solution from …\RetailSDK\POS

3.  In VS Set the solution configuration to Debug, Solution platforms to x86 and Deploy to Local machine.

4.  Click the **Deploy > Local Machine** after compile and Build.

5.  Once the POS is deployed, login to POS using the operator ID and Password.

6.  Click the Settings button on the top right side of POS.

7.  In the Settings page, under the Developer mode, Set Developer Mode = On

8.  Set the Show Strings IDs to On.

9.  Log off and Log in again to POS, then POS will show the strings IDs before all the labels and messages.

## Troubleshooting

If POS is not showing the developer mode option in the settings page, check whether you are running in debug mode and check in pos.js file whether Config.isDebugMode = true; if its false, change the value to true and deploy the POS again.

> [!NOTE]
> You should not edit pos.js file, just for quick testing and to get the string IDs you edit the file and revert because if you do any changes in Microsoft cores files it will be overridden during deployment and you will lose the changes. Also editing the pos.js file may not be supported in the future versions.

## Override Retail server or CRT messages or Receipt strings:

1.  Login to Dynamics 365 for Retail or Finance and Operations.

2.  Navigate to **Retail > Channel setup > POS setup > POS profiles > Language text**.

3.  Select the **Retail server tab** in the Language text form.

4.  Under the **Retail server language text** grid, click the **Add** button to add the Language ID, Text ID and Text for string you want to override.

    **Ex:** When you enter wrong user name or password during logon POS will show the error message as "We didn't recognize the user name or password. Please try again.", if you want to change the message "Please enter valid user name or password." for en-us then you will add the below language ID, text ID and Text to Retail server language text.

| **Language ID** | **Text ID**                                                              | **Text**                                 |
|-----------------|--------------------------------------------------------------------------|------------------------------------------|
| en-us           | Microsoft_Dynamics_Commerce_Runtime_InvalidAuthenticationCredentials | Please enter valid user name or password |

1.  Click **Save** in the Action bar.

2.  Navigate to **Retail > Retail IT > Distribution schedule**.

3.  Select the **Registers (1090)** job and click **Run now**.

## How to get the Text ID for the Retail server or CRT messages or Receipt strings

1.  Navigate to …\RetailSDK\Documents\Resources

2.  Open the **RuntimeExceptionMessages.resx** using Visual studio if you want to modify the Retail server or CRT messages. To modify the Receipt strings, open the **RuntimeReceiptMessages.resx** file.

3.  Visual Studio will open all the messages in the resources files as Name and Value.

4.  Search for the text you are planning to change in the value column.

5.  Copy the Name against that value. This name will be used as Text ID in **Retail server language text**.

    You can also add your new CRT or RS error messages or Receipt strings to the Retail server language text form and support localization instead of hard coding everything in the code.

> [!NOTE]
> All your new message should start with the Text ID: **Microsoft_Dynamics_Commerce_**.

Ex: Suppose you want to add a new exception messages in en-us and en-uk, you will do something like this in **Retail server language text**:

| **Language ID** | **Text ID**                               | **Text**                |
|-----------------|-------------------------------------------|-------------------------|
| en-us           | Microsoft_Dynamics_Commerce_CustomId1  | My new message in en-us |
| en-uk           | Microsoft_Dynamics_Commerce_ CustomId1 | My new message in en-uk |


> [!NOTE]
> **CustomId1** is the ID used for the new messages, you can use any ID, but it should begin with **Microsoft_Dynamics_Commerce_**.

## How will you use this in your CRT Extension code

```C#
throw new CommerceException("Microsoft_Dynamics_Commerce_ CustomId1", ExceptionSeverity.Warning, null, "Custom error"); |
```

