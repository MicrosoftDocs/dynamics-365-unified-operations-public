---
# required metadata

title: Troubleshoot Store Commerce setup and installation issues
description: This topic explains how to troubleshoot setup and installation issues in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: mugunthanm
ms.date: 05/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2017-06-20

---

# Troubleshoot Store Commerce setup and installation issues

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic explains how to troubleshoot setup and installation issues in the Microsoft Dynamics 365 Commerce Store Commerce app.

### I can't activate the app and get a connectivity error message

After you enter the valid Cloud Point of Sale (CPOS) URL, you may receive a connectivity error message like the following:

`A connectivity error has occurred, and your device can't connect to the CPOS. The CPOS URL typed may have some issues.` 

In this case, review the URL for typographical errors, or determine whether CPOS can't be reached because it's offline.

Additionally, verify that the Cloud Scale Unit (CSU) version is 10.0.25 (9.35.\*.\*) or later. CPOS version 10.0.25 or later is required to use the Store Commerce app.

### Installation issues

During installation, you might receive an error such as the following:

`A version (9.\*.\*.\*) of this product (Modern POS) has been previously installed through the legacy installer.` 

To fix the error, you must uninstall the Modern Point of Sale (MPOS) app for all the users on the machine and then try again. You can confirm whether MPOS has been removed for all the users by running the following PowerShell command:

```PowerShell
Get-AppxPackage | Where-Object {$_.PackageFullName -like "Microsoft.Dynamics.*.Pos"} | Remove-AppxPackage -Allusers
```

### I can't activate the Store Commerce app due to an invalid URL or error state

If the CPOS URL that you entered isn't valid and you want to change it, or if the Store Commerce app is in an error state during activation, you can restart the process by resetting the app. The Store Commerce app will only save a valid CPOS URL.

To reset the Store Commerce app, follow these steps.

1. On the Windows **Start** menu, select and hold (or right-click) the app, and then select **More \> App settings**.
2. Scroll down the app settings page until you find the **Reset** button.
3. Select **Reset**, and then when prompted, confirm that you want to reset the app.
