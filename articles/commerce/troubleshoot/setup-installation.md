---
# required metadata

title: Troubleshoot Store Commerce setup and installation issues
description: This topic explains how to troubleshoot Store Commerce setup and installation issues.
author: Mugunthan-Mani
ms.date: 12/05/2022
ms.topic: Troubleshooting
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2022-05-12
ms.dyn365.ops.version: 10.0.25

---


### Troubleshoot Store Commerce setup and installation issues

This topic explains how to troubleshoot Store Commerce setup and installation issues.

#### I can't activate the app and get a connectivity error message

After you enter the valid CPOS URL, you might receive a connectivity error such as "A connectivity error has occurred, and your device can't connect to the Cloud POS. The Cloud POS URL typed may have some issues." In this case, review the URL for typographical errors, or determine whether Cloud POS can't be reached because it's offline.

Additionally, verify that the CSU version is 10.0.25 (9.35.\*.\*) or later. CPOS version 10.0.25 or later is required to use Store Commerce.

#### Installation issues

During installation, you might receive an error such as "A version (9.\*.\*.\*) of this product (Modern POS) has been previously installed through the legacy installer." To fix the error, you must uninstall the MPOS app for all the users on the machine and try again. You can confirm whether MPOS has been removed for all the users by running the following PowerShell command.

```PowerShell
Get-AppxPackage | Where-Object {$_.PackageFullName -like "Microsoft.Dynamics.*.Pos"} | Remove-AppxPackage -Allusers
```

#### I can't activate the app due to an invalid URL or error state

If the CPOS URL that you entered isn't valid and you want to change it, or if the app is in an error state during activation, you can restart the process by resetting the app. Note that the Store Commerce app will save only a valid CPOS URL.

To reset the app, follow these steps.

1. On the Windows **Start** menu, select and hold (or right-click) the app, and then select **More \> App settings**.
2. Scroll down the app settings page until you find the **Reset** button.
3. Select **Reset**, and then, when you're prompted, confirm that you want to reset the app.
