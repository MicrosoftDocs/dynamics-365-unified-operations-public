---
# required metadata

title: Troubleshooting guide for single or multi-user testing with Performance SDK
description: This topic provides troubleshooting information about the common issues you might encounter during single or multi-user testing with the Performance SDK. 
author: hasaid
manager: AnnBe
ms.date: 05/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 9954
ms.assetid: 7b605810-e4da-4eb8-9a26-5389f99befcf
ms.search.region: Global
# ms.search.industry: 
ms.author: jujoh
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Troubleshooting guide for single or multi-user testing with Performance SDK

[!include [banner](../includes/banner.md)]

## No client was opened in the time-out period
This issue affects only single-user tests. When the test is running, a web client opens, but a website is never loaded. Instead, there is an empty web client that has a white screen, and the following message appears at the top of the page: "This is the initial start page for the WebDriver server." The test will eventually time out and fail, and an error message will be shown.

### Error example
Initialization method <Test class name>.TestSetup threw exception. System.TimeoutException: System.TimeoutException: No client was opened in the timeout period.

### Solution
Follow steps 4 through 8 in the "Run a single-user performance test by using the Performance SDK " section of this topic. That section explains how to create a correct certificate for this type of test. It also explains how to add the thumbprint of the certificate to the wif.config file.

## Zoom factor
This issue affects only single-user tests.

### Error example
Initialization method <Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Unexpected error launching Internet Explorer. Browser zoom level was set to 200%. It should be set to 100% (NoSuchDriver).

### Solution
In Internet Explorer, you can change the zoom factor to 100 percent by changing the following registry keys:

- Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\ResetZoomOnStartup = 0
- Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\ResetZoomOnStartup2 = 0
- Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\Zoomfactor = 80000

Depending on the version of the local machine that is used, before you start the Remote Desktop Protocol (RDP) session, you might have to select Change the size of text, apps and other items. This field is available in Display settings in Windows.
If those steps don't work, try to change the size of your remote desktop before you start the RDP session, so that the default zoom level in Internet Explorer is 100 percent.

## Certificate thumbprint errors
### Error example
Initialization method MS.Dynamics.Performance.Application.TaskRecorder.TestRecord1Base.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --> 
MS.Dynamics.TestTools.CloudCommonTestUtilities.Exceptions.WebAuthenticationException: 
Failed finding the certificate for minting tokens by thumbprint: b4f01d2fc42718198852cd23957fc60a3e4bca2e

### Solution
You might receive the error message for several reasons:

- The certificate thumbprint that you copied into the CloudEnvironment.Config and wif.config files includes invisible Unicode characters. To determine whether the thumbprint contains invisible Unicode characters, paste it into a Unicode code converter, and see whether extra characters appear in the HTML/XML field. For example, you can use the Unicode converter that is available at https://r12a.github.io/apps/conversion/
- The certificate wasn't installed on the AOS machine. To verify that the certificate can be found on the AOS machine, run the following Windows PowerShell script.
cd Cert:\LocalMachine\My
Get-ChildItem | Where-Object { $_.Subject -like "CN=<name of your certificate>" }
If the thumbprint doesn't appear in the Windows PowerShell console after you run the script, the certificate can't be found. To fix the issue, copy and install the .cer file that you created earlier in this topic to all AOS machines.
- If this issue occurs when you run load tests, the setup scripts might not have installed the corresponding .pfx file correctly. Verify that the password that is specified in the CloudCtuFakeACSInstall.cmd file matches the password that was set when the certificate was created.
 
## No endpoint is listening
This issue can occur when you run single-user or multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe.

### Error example
The tests or user creation process fails, and the following error message is shown.
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.EndpointNotFoundException: There was no endpoint listening at <web address> that could accept the message. This is often caused by an incorrect address or SOAP action. 

### Solution
This issue occurs when the host that is specified in the CloudEnvironment.Config file can't be accessed from the machine that is trying to run the tests or create users.
In the CloudEnvironment.Config file, review the values that are specified by the following keys:

- <ExecutionConfigurations Key="HostName" Value="<web address of host>" />
- <ExecutionConfigurations Key="SoapHostName" Value="<web address of SOAP>" />

The web addresses that are specified by these keys must be the environment that you're testing. In a web browser on your developer machine, make sure that you can open the web address that is specified by the HostName key.
For online load tests, the environment that is specified by the HostName key in the CloudEnvironment.Config file must be publicly accessible from any machine. Therefore, if you must test a one-box environment, you won't be able to run the load test by using Visual Studio Online, because the endpoint won't be accessible outside the one-box environment.

## Users can't be enumerated
This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe.

### Error example
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Could not enumerate AX users ---> System.ServiceModel.FaultException'1[System.ComponentModel.Win32Exception]: Forbidden

### Solution
Two scenarios can cause this error:

- The user who is specified as SelfMintingAdminUser in the CloudEnvironment.config file must have the System Administrator role. This issue occurs when the System Administrator role isn't assigned to the user who is specified as SelfMintingAdminUser. To verify that you've specified the correct user, you can sign into the endpoint and view the user's roles.
- The user who is specified as SelfMintingAdminUser in the CloudEnvironment.config file has a Provider other than "<https://sts.windows-ppe.net/>" or "<https://sts.windows.net/>". Sometimes, a company-specific domain is included in the Provider field for the admin user. 

To work around this issue, in Finance and Operations, create a user who has any name and email address. Assign the System Administrator role to the new user. You don't have to link the user to a real Azure Active Directory user. Specify this new admin user as SelfMintingAdminUser in the CloudEnvironment.config file.

## The HTTP request was forbidden with client authentication scheme 'Anonymous'
### Error example
Initialization method <Test class name>.TestSetup threw exception. System.ServiceModel.Security.MessageSecurityException: System.ServiceModel.Security.MessageSecurityException: The HTTP request was forbidden with client authentication scheme 'Anonymous'. ---> System.Net.WebException: The remote server returned an error: (403) Forbidden..

### Solution
Two known scenarios can cause this error:

- The test users are created by running MS.Dynamics.Performance.CreateUsers.exe without any arguments. Here is an example.

  MS.Dynamics.Performance.CreateUsers.exe

  If the CreateUsers script is run without any arguments, the email addresses of test users that are created won't be correctly formatted. If these users are used to run the tests, the tests will generate the forbidden request error. You can verify that this scenario is causing the error by viewing the users in Microsoft Dynamics 365 for Finance and Operations. The incorrect email addresses of the test users will resemble the email addresses in the following illustration.

  To resolve the issue, delete the test users who have incorrectly formatted email addresses. Rerun the CreateUsers script and specify the user count and company as shown here.

  MS.Dynamics.Performance.CreateUsers.exe [UserCount] [CompanyCode]

- The number of users that you specify in the UserCount field in the CloudEnvironment.Config file exceeds the number of test users that you created by running MS.Dynamics.Performance.CreateUsers.exe. Make sure that you created at least as many test users as you request in the CloudEnvironment.Config file.
 
## At least one security token in the message could not be validated
This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe. It tends to occur when the AOS machine differs from the developer machine.

### Error example
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.Security.MessageSecurityException: An unsecured or incorrectly secured fault was received from the other party. See the inner FaultException for the fault code and detail. ---> System.ServiceModel.FaultException: At least one security token in the message could not be validated.

### Solution
This issue occurs when the AOS endpoint can't validate the thumbprint of the certificate that you created. There are two possible causes:

- The certificate wasn't installed on the AOS machine. To fix the issue, copy the .cer file that you created earlier in this topic to the AOS machine, and install it.
- The thumbprint of the certificate wasn't added to the wif.config file on the AOS machine. To fix the issue, see step 8 in the "Run a single-user performance test by using the Performance SDK " section for information about how to add the certificate to the wif.config file. Be sure to restart IIS after you modify the wif.config file.

## MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config is missing from the deployment items
This issue usually occurs only when you run load tests.

### Error example
<Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Could not find endpoint element with name 'ClientCommunicationManager' and contract 'Microsoft.Dynamics.Client.InteractionService.Communication.Reliable.IReliableCommunicationManager' in the ServiceModel client configuration section. This might be because no configuration file was found for your application, or because no endpoint element matching this name could be found in the client element.. at System.ServiceModel.Description.ConfigLoader.LoadChannelBehaviors(ServiceEndpoint serviceEndpoint, String configurationName)

### Solution
This issue occurs when the system can't find the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file when the load tests are run, because the file wasn't added as a deployment item. Verify whether the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file is in the Out folder for the test run:
<solution path>\TestResults\<your test run>\Out
If the file is missing, add it to the deployment items in the test settings.
There are two files that have very similar names. The name of one file ends in *.dll, and the name of the other file ends in *.dll.config. The *.dll.config file must be in the deployment items in the test settings.

## CloudEnvironment.Config is missing from the deployment items
This issue usually occurs only when you run load tests.

### Error example
Initialization method <Test class name>.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> MS.Dynamics.TestTools.TestLogging.EvaluateException: Assert.Fail failed. DateTime="10/13/2017 14:42:55" "The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception.".

### Solution
This issue occurs when the CloudEnvironment.Config file isn't present when the tests are run. The issue typically occurs when you run load tests and the CloudEnvironment.Config file wasn't added as a deployment item. Verify whether the CloudEnvironment.Config file is in the Out folder for the test run:
<solution path>\TestResults\<your test run>\Out
If the file is missing, add it to the deployment items in the test settings.
 
## InteractiveClientId wasn't specified in the settings
### Error example
The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception. --->
Microsoft.CE.VaultSDK.SecretProviderException: InteractiveClientId was not specified in settings

### Solution
This issue occurs when the SelfSigningCertificateThumbprint field is left blank in the CloudEnvironment.Config file. In the CloudEnvironment.Config file, find the following line, and paste in the thumbprint of the certificate that you created and installed.
<ExecutionConfigurations Key="SelfSigningCertificateThumbprint" Value="" />

## The remote host forcibly closed an existing connection
### Error example
System.TypeInitializationException: System.TypeInitializationException: The type initializer for
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --->
System.ServiceModel.CommunicationException: An error occurred while making the HTTP request to
<Host name>/Services/AxUserManagement/Service.svc/ws2007FedHttp. This could be due to the fact 
that the server certificate is not configured properly with HTTP.SYS in the HTTPS case. This could also be caused 
by a mismatch of the security binding between the client and the server.** ---> System.Net.WebException: 
The underlying connection was closed: An unexpected error occurred on a send. ---> System.IO.IOException: 
Unable to read data from the transport connection: An existing connection was forcibly closed by the remote host. ---> 
System.Net.Sockets.SocketException: An existing connection was forcibly closed by the remote host. 

### Solution
Run the following Windows PowerShell script on the development machine.
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false
if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319)) 
{
    Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false 
}

## Service w3svc was not found on computer
This error only occurs when you run load tests by using Visual Studio Online.

### Error example
Test method MS.Dynamics.Performance.Application.GFM.PDLTrend.ProcureToPayTrend.ProcureToPaymentTrend threw exception: 
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Service w3svc was not found on computer '.'. ---> System.ComponentModel.Win32Exception: The specified service does not exist as an installed service

### Solution
A hotfix is available that resolves this issue. The Microsoft Knowledge Base (KB) number is 4095640.

## The driver can be downloaded at http://selenium-release.storage.googleapis.com/index.html 
This issue affects only single-user test.

### Error example
The file K:\ perfSDK\PerfSDKLocalDirectory \SampleProject\TestResults\Admin501201994c_devae648d1909-1 2018-06-25 03_40_51\Out\Common\External\Selenium\IEDriverServer.exe does not exist. The driver can be downloaded at http://selenium-release.storage.googleapis.com/index.html 

### Solution
Copy Common\External\Selenium folder under <Your_PerfSDK_Folder> to <Your_PerfSDK_Folder>\SampleProject\ PerfSDKSample\bin\Debug folder
Failed finding the certificate for minting tokens by thumbprint: <your certificate thumbprint>
Error example
 
### Resolution
Make sure you install the generated certificate in each AOS of your sandbox environment

## The action you are trying to perform requires a connection to Visual Studio Team Services.
This issue only affects multi-user tests.

### Error example
 

### Resolution
When connect to Azure DevOps, please use the old URI formatting (<Azure_DevOps_Account>.visualstudio.com) instead of dev.azure.com/<Azure_DevOps_Account>. Also, brows to Azure DevOps with old URI and click on “Open in Visual Studio” from there.

## Could not load file or assembly 'aoskernel.dll' or one of its dependencies
This error only affects multi-user tests.

### Error example
 
### Resolution
Make use you’re using ODBC Driver 17 in an environment with PU20 or above

## AzureActiveDirectoryConfiguration node is missing in CloudEnvironment.config
### Error example
 Initialization method MS.Dynamics.Performance.Application.TaskRecorder.SalesOrderCreationAndConfirmationBase.TestSetup threw exception. System.TypeInitializationException: System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.MissingFieldException: AzureActiveDirectoryConfiguration node is missing in CloudEnvironment.config.

### Resolution
Replace all “MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.AadAuthenticator”  with “MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SelfMintedTokenAuthenticator” in AuthenticatorConfigurationCollection section of CloudEnvironment.config

## Multiple warning message before and after multi-user testing with Azure DevOps
### Error example
 
 
### Resolution
No impact just ignore them.

