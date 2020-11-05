---
# required metadata

title: Localize Commerce extension resources and label files
description: This topic explains how to modify POS UI labels, POS messages, receipt labels, and error messages for Commerce Scale Unit or CRT.
author: mugunthanm
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.search.region: Global 
ms.search.industry: retail
ms.author: mumani
ms.search.validFrom: 2018-05-31
ms.dyn365.ops.version: 8.0.1

---

# Localize Commerce extension resources and label files

[!include[banner](../includes/banner.md)]


This topic explains how to modify labels in the point of sale (POS) user interface (UI), POS messages (error, warning, and information), receipt labels, and error messages for Commerce Scale Unit or Commerce Runtime Services (CRT). You can also add custom error messages for in the same way. However, for new POS extension labels, you should use the localization framework in the POS extension.

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
7. After the data is pushed, sign off, and then sign in to Cloud POS or Modern POS to see the changed labels.

### Get the text ID for POS strings

To get the text ID for a POS string, you must run the POS by using the Retail software development kit (SDK) in Debug mode. In the POS, text IDs are referred to as string IDs.

1. Start Microsoft Visual Studio 2015 in Administrator mode.
2. Open **ModernPOS** solution from **…\\RetailSDK\\POS**.
3. Set the **Solution configuration** property to **Debug**, the **Solution platforms** property to **x86**, and the **Deploy** property to **Local machine**.
4. Compile and build the solution, and then select **Deploy \> Local Machine**.
5. After the POS is deployed, sign in to it by using your operator ID and password.
6. Select the **Settings** button in the upper right of the POS window.
7. On the **Settings** page, under **Developer mode**, set the **Developer Mode** option to **Yes**.
8. Set the **Show Strings IDs** option to **Yes**.
9. Sign out of the POS, and then sign in again. The POS now shows the strings IDs in front of all the labels and messages. 

### Troubleshooting

If the **Developer Mode** option doesn't appear on the **Settings** page in the POS, verify that you're running in Debug mode. Open the **pos.js** file, and verify that **Config.isDebugMode** is set to **true**. If it's set to **false**, change the value to **true**, and then deploy the POS again. If you are unable to find **Config.isDebugMode** in the **pos.js** file. then run the **Commerce.Helpers.DeveloperModeHelper.setDeveloperMode(true);** command in the JavaScript console to turn on the developer mode. Press F12 to launch the developer command tools and select the **Console** tab to open the JavaScript console.

> [!IMPORTANT]
> You should edit the pos.js file **only** to do quick testing and to get string IDs. In these cases, after you edit the file, you should revert your changes. Any changes that you make in Microsoft cores files will be overridden during deployment. Therefore, you will lose the changes. Additionally, future versions might not support editing the pos.js file.

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
