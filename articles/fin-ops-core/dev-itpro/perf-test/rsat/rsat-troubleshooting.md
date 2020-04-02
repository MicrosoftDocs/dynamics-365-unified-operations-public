---
# required metadata

title: Troubleshoot the Regression suite automation tool 
description: This topic contains information about how to troubleshoot the Regression suite automation tool (RSAT).
author: robadawy
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0

---

# Troubleshoot the Regression suite automation tool 

[!include [banner](../../includes/banner.md)]

This topic contains information about how to troubleshoot the Regression suite automation tool (RSAT).

## Playback logs

To troubleshoot issues that happen during playback of a test case, open the developer error log located at **[RSAT working directory]\[test case ID]\playback\[TestName]Log.txt**. The RSAT working directory is the directory specified in the RSAT settings dialog.
Analyze the error message to determine the possible cause of a failure.

[!NOTE] For RSAT versions prior to 1.210, the log is located at **C:\Users\$YourUserName\AppData\Roaming\regressionTool\playback\[TestName]Log.txt**.

## Authentication certificate and installation

+ The authentication certificate must be created and installed by an administrator on the same computer where RSAT is installed. If it is not created by an admin, you will encounter the following error message when you try to run a test case.  

  ```Text
  Cannot access Finance and Operations environment. Verify your settings and make sure the environment is available.
  ```

+ If you have used a previous version of RSAT on the same computer, close it and uninstall it before installing a new version.

## Screen resolution

If you have selected Internet Explorer as your browser, your desktop resolution should be set to 100% to run the tests successfully. To change the settings, use Windows **Display settings > Scale and layout**, as shown in the following image:

![Setting screen resolution](media/screen-resolution.png)
 
## Test playback errors

### SOAP or HTTP request errors

If you are testing against a Standard Acceptance Test Sandbox environment (Tier2) or any other multi-box environment, and you may receive one of the following errors when you run a test.

```Text
There was no endpoint listening at https://<yourURL>soap.sandbox.operations.dynamics.com/Services/AxUserManagement/Service.svc/ws2007FedHttp that could accept the message. This is often caused by an incorrect address or SOAP action…

An error occurred while making the HTTP request to <Hostname>/Services/AxUserManagement/Service.svc/ws2007FedHttp. This could be due to the fact that the server certificate is not configured properly with HTTP.SYS in the HTTPS case. This could also be caused by a mismatch of the security binding between the client and the server.
```

Assuming that you have specified the correct SOAP hostname in the settings dialog box, run the following PowerShell scripts on your client computer where the test tool is installed.

```powershell
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false

if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319))  { Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false}
```

You can also manually set the registry keys.

### Cannot enumerate error

You may receive the following error when running a test case, or the error details may contain the following messages.

```Text
<Message>The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception.</Message>
<Message>Could not enumerate AX users</Message>  (InnerError)`
```

![Enumerate error message box](media/cannot-enumerate.png)
 
To resolve this error, verify the **Admin user name** specified in the RSAT settings dialog box. The **Admin user name** must be the email address of a user that belongs to the System Administrator role on the environment that RSAT is connecting to.

## Browser

The Chrome browser may not work with the Regression suite automation tool due to your Active Directory security settings. In this case, change your settings to use an Internet Explorer browser.

## Excel data tabs

Microsoft Excel data tabs display the system identifiers for data variables. Excel does not display friendly names.

##  Validating blank dates
If your test case requires validation that a certain control of type Date/Time is blank, you can insert the following value into the Excel cell corresponding to this control: “01/01/1900”.   

