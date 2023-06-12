---
title: Troubleshoot the Regression suite automation tool
description: This article contains information about how to troubleshoot the Regression suite automation tool (RSAT).
author: FrankDahl
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Troubleshoot the Regression suite automation tool

[!include [banner](../../includes/banner.md)]

This article contains information about how to troubleshoot the Regression suite automation tool (RSAT).

## Playback logs

To troubleshoot issues that happen during playback of a test case, open the developer error log located at **[RSAT working directory]\\[test case ID]\\playback\\[TestName]Log.txt**. The RSAT working directory is the directory specified in the RSAT settings dialog.
Analyze the error message to determine the possible cause of a failure.

> [!NOTE]
> For RSAT versions prior to 1.210, the log is located at **C:\\Users\\[YourUserName]\\AppData\\Roaming\\regressionTool\\playback\\[TestName]Log.txt**.

## Generator logs

To troubleshoot errors when generating test execution and parameter files, enable generator logs.

Open the **Microsoft.Dynamics.RegressionSuite.WindowsApp.exe.config** file under the RSAT installation folder (for example, **C:\\Program Files (x86)\\Regression Suite Automation Tool**), and change the value in the following element from **false** to **true**.

```xml
<add key="LogGeneration" value="true" />
```

After test execution files are generated, you can find the log file under **[RSAT working directory]\\[test case ID]\\generatorLogs**

> [!NOTE]
> For RSAT versions prior to 1.210, the logs are generated under **C:\\Users\\[Username]\\AppData\\Roaming\\regressionTool\\generatorLogs**.

## Authentication certificate and installation

+ The authentication certificate must be created and installed by an administrator on the same computer where RSAT is installed. If it is not created by an admin, you will encounter the following error message when you try to run a test case.

```Plaintext
Cannot access finance and operations environment. Verify your settings and make sure the environment is available.
```

+ If you have used a previous version of RSAT on the same computer, close it and uninstall it before installing a new version.

## Screen resolution when using Internet Explorer

If you have selected Internet Explorer as your browser, your desktop resolution should be set to 100% to run the tests successfully. To change the settings, use Windows **Display settings > Scale and layout**, as shown in the following image:

![Setting screen resolution.](media/screen-resolution.png)

## Test playback errors

### SOAP or HTTP request errors

If you are testing against a Standard Acceptance Test Sandbox environment (Tier2) or any other multi-box environment, and you may receive one of the following errors when you run a test.

```Plaintext
There was no endpoint listening at https://<yourURL>soap.sandbox.operations.dynamics.com/Services/AxUserManagement/Service.svc/ws2007FedHttp that could accept the message. This is often caused by an incorrect address or SOAP action…

An error occurred while making the HTTP request to <Hostname>/Services/AxUserManagement/Service.svc/ws2007FedHttp. This could be due to the fact that the server certificate is not configured properly with HTTP.SYS in the HTTPS case. This could also be caused by a mismatch of the security binding between the client and the server.
```

Assuming that you have specified the correct SOAP hostname in the RSAT settings dialog box, run the following PowerShell scripts on your client computer where the test tool is installed.

```powershell
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false

if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319))  { Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false}
```

You can also manually set the registry keys.

### Cannot enumerate AX users error

You may receive the following error when running a test case, or the error details may contain the following messages.

```Xml
<Message>The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception.</Message>
<Message>Could not enumerate AX users</Message>  (InnerError)`
```

![Enumerate error message box.](media/cannot-enumerate.png)

To resolve this error, verify the **Admin user name** specified in the RSAT settings dialog box. The **Admin user name** must be the email address of a user that belongs to the System Administrator role on the finance and operations test environment that RSAT is connecting to. The user account (e-mail address) must also belong to the same tenant as the test environment. For example, if your test environment's tenant is **contoso.com**, the admin user must end with **\@constoso.com**.

### Unsecured fault exception

If a test case inconsistently fails with the following error, this usually indicates an incomplete configuration of the authentication thumbprints on the AOS virtual machines.

```Xml
<Message>An unsecured or incorrectly secured fault was received from the other party. See the inner FaultException for the fault code and detail.</Message>
<Message>At least one security token in the message could not be validated.</Message>
```

Typically, this error happens when the test environment has not been configured to trust the certificate that RSAT is using for authentication. (The certificate is identified by the thumbprint specified in your RSAT settings.) For example, the thumbprint could be missing in the wif.config file on the AOS virtual machine of the test environment. If you are running against a standard acceptance test environment (Tier 2 or higher), you might not have configured the authentication thumbprint on all of the AOS virtual machines. Make sure you properly add the thumbprint to the **wif.config** file on all of the AOS machines. For more information, see [Configure the test environment to trust the connection](rsat-install-configure.md#configure-the-test-environment-to-trust-the-connection).

We have also seen this error when there is a mismatch between the UTC time between the client computer (where RSAT is installed) and the finance and operations environment. This is a rare case and only happens if your administrator has incorrectly configured the UTC time. The client computer and finance and operations environment can be on different time zones; however, the UTC time on both environments must match because the authentication mechanism relies on this comparison.

## Google Chrome Browser

The Google Chrome browser may not work with the Regression suite automation tool due to your Active Directory security settings. In this case, change your RSAT settings to use the new Microsoft Edge or Internet Explorer.

## Validating blank dates

If your test case requires validation that a certain control of type Date/Time is blank, you can insert the following value into the Excel cell corresponding to this control: "01/01/1900".

## Azure DevOps connectivity

You might you see this error when you select the desired Azure DevOps project in RSAT settings: "The structure path \<iteration path\> is not valid. Verify your settings and try again". To resolve this error, open the project in Azure DevOps and navigate to the Test Plans. Verify the iteration path defined for each test plan. If the iteration path is similar to what is shown in the error, remove the existing iteration path and add a new one for the test plan and save.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
