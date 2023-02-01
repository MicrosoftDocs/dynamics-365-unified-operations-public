---
title: Localize Commerce extension resources and label files
description: This article explains how to modify POS UI labels, POS messages, receipt labels, and error messages for Commerce Scale Unit or CRT.
author: josaw1
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2018-05-31
ms.dyn365.ops.version: 8.0.1
ms.search.industry: retail
---

# Localize Commerce extension resources and label files

[!include[banner](../includes/banner.md)]


This article explains how to modify labels in the point of sale (POS) user interface (UI), POS messages (error, warning, and information), receipt labels, and error messages for Commerce Scale Unit or Commerce Runtime Services (CRT). You can also add custom error messages for in the same way. However, for new POS extension labels, you should use the localization framework in the POS extension.

## POS labels and messages (error, warning, and information)

This section explains how to modify POS UI labels and POS messages by overriding the default strings.

### Override POS UI labels and messages

You can override the default strings in the POS by using the language text entries on the **Language text** page. Follow these steps to change POS strings.

1. Sign in to Commerce.
2. Go to **Retail and Commerce &gt; Channel setup &gt; POS setup &gt; POS profiles &gt; Language text**.
3. On the **Language text** page, on the **POS** tab, in the **POS language text** grid, select the **Add** button to add the language ID, text ID, and text for the string that you want to override.

    For example, you want to change the label of the **Operator ID** field on the POS sign-in page to **Employee ID** for US English (en-us). In this case, add the following entry in the **POS language text** grid.

    | Language ID | Text ID | Text        |
    |-------------|---------|-------------|
    | en-us       | 502     | Employee ID |

    > [!NOTE]
    > For information about how to get the text ID for POS strings, see the next section.

4. On the Action Pane, select **Save**.
5. Go to **Retail and Commerce &gt; Retail and Commerce IT &gt; Distribution schedule**.
6. Select the **Registers** (**1090**) job, and then select **Run now**.
7. After the data is pushed, you'll need to wait up to one hour for the localized string cache to refresh. When the refresh of the string cache is complete, sign out and sign back in to Store Commerce to display the changed labels. You can also force a cache refresh by restarting Retail Server. 

### Get the text ID for POS strings

To get the text ID for a POS string, open Store Commerce for web. Press F12 to launch the developer command tools and select the **Console** tab to open the JavaScript console. Run the **Commerce.Helpers.DeveloperModeHelper.setDeveloperMode(true);** command in the JavaScript console to turn on the developer mode.

After enabling the developer mode in the JavaScript console, navigate to the **Settings** page in POS, under the **Developer mode**, set **Developer Mode** to **Yes**. Set **Show Strings IDs** to **Yes**. Sign out of the POS, and then sign in again. The POS now shows the strings IDs in front of all the labels and messages.


## Error messages or receipt strings

This section explains how to modify error messages, or receipt strings, by overriding the default strings. It also explains how you can add new, custom error messages, or receipt strings.

### Override error messages or receipt strings

1. Sign in to Commerce.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
3. On the **Language text** page, click the **Add** button to add the language ID, text ID, and text for the string that you want to override.

    For example, when users enter an incorrect user name or password during sign-in, the POS shows the following error message: "We didn't recognize the user name or password. Please try again." For US English, you want to change the message to "Please enter valid user name or password." In this case, add the following entry in the **language text** grid.

    | Language ID | Text ID                                                              | Text                                     |
    |-------------|----------------------------------------------------------------------|------------------------------------------|
    | en-us       | Microsoft\_Dynamics\_Commerce\_Runtime\_InvalidAuthenticationCredentials | Please enter valid user name or password |

    > [!NOTE]
    > For information about how to get the text ID for error messages and receipt strings, see the next section.

4. On the Action Pane, select **Save**.
5. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
6. Select the **Registers** (**1090**) job, and then select **Run now**.

### Get the text ID for messages or receipt strings

1. Go to **…\\RetailSDK\\Documents\\Resources**.
2. In Visual Studio, open one of the following resource files:

    - **To modify error messages:** RuntimeExceptionMessages.resx
    - **To modify receipt strings:** RuntimeReceiptMessages.resx

    For every message in the resource file, Visual Studio shows a name and a value.

3. In the **Value** column, search for the text that you want to change.
4. Copy the name that corresponds to that value. You enter this name as the text ID in the **language text** grid.

### Add custom error messages or receipt strings

You can also add new error messages or new receipt strings, on the **Language text** page. In this way, you support localization instead of hard-coding everything in the code.

> [!IMPORTANT]
> The text ID of all your new messages must start with **Microsoft\_Dynamics\_Commerce\_**.

For example, you want to add a new exception message in US English (en-us) and UK English (en-uk). In this case, add entries that resemble the follow entries on the **Language text** page.

| Language ID | Text ID                                 | Text                    |
|-------------|-----------------------------------------|-------------------------|
| en-us       | Microsoft_Dynamics_Commerce_CustomId1 | My new message in US English |
| en-uk       | Microsoft_Dynamics_Commerce_CustomId1 | My new message in UK English |

> [!NOTE]
> In this example, **CustomId1** is the text ID for the new message. You can use any text ID that you want, provided that it starts with **Microsoft_Dynamics_Commerce_**.

The following example shows how to use this new message in your CRT extension code.

```C#
throw new CommerceException("Microsoft_Dynamics_Commerce_CustomId1", ExceptionSeverity.Warning, null, "Custom error")
                    {
                        LocalizedMessage = "My new message in US English.",
                        LocalizedMessageParameters = new object[] { }
                    };
```


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
