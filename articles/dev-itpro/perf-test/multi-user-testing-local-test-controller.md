---
# required metadata

title: Multi-user testing with Performance SDK and local test controller
description: This topic provides information about how tocomplete multi-user testing by using Visual Studio and Performance SDK with performance test scripts that are generated from Task Recorder. 
author: hasaid
manager: AnnBe
ms.date: 05/15/2019
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

# Multi-user testing with Performance SDK and local test controller
[!include [banner](../includes/banner.md)]

Prerequisites
1.	A Dynamics 365 for Finance and Operations development environment with Platform Update 21 or above in own your Azure subscription
2.	Visual Studio 2015 Enterprise edition in development environment
3.	A tier 2 or above sandbox with the same release (App + PU) as your development environment
4.	You had configured development environment based on Single user testing with Task recorder and Performance SDK 
5.	C# performance testing classes for your E2E scenarios had been generated and you’re able to run single user test based on Single user testing with Task recorder and Performance SDK 

Procedures
1.	Configure Dynamics 365 for Finance and Operations development environment for multi-user testing
2.	Prepare PerfSDKSample solution for multi-user testing
3.	Configure tier 2 or above sandbox for multi-user testing
4.	Run multi-user testing with local test controller
5.	Troubleshooting

Configure Dynamics 365 for Finance and Operations development environment for multi-user testing

1.	Download ODBC Driver 17 for SQL Server from here, rename the download file as msodbcsql, and copy it to folder Visual Studio Online under perfSDK folder
 
2.	Create a new environment variable TestRoot and point it to PerfSDK folde by running below cmdlet in powershell
[ENVIRONMENT]::SETENVIRONMENTVARIABLE("TESTROOT", "K:\PERFSDK\PERFSDKLOCALDIRECTORY", "USER")
 
3.	Generate and install certificate
1)	Run below commands to generated required certificate in command prompt windows as administrator. When you’re prompted for a private key password, select None.

"C:\Program Files (x86)\Windows Kits\8.1\bin\x64\makecert" -n "CN=127.0.0.1" -ss Root -sr LocalMachine -a sha256 -len 2048 -cy end -r -eku 1.3.6.1.5.5.7.3.1 -sv c:\temp\authcert.pvk c:\temp\authcert.cer

"c:\Program Files (x86)\Windows Kits\8.1\bin\x64\pvk2pfx" -pvk c:\temp\authCert.pvk -spc c:\temp\authcert.cer -pfx c:\temp\authcert.pfx

Elements in above commands:
a)	-n "CN=127.0.0.1" gives a human-readable name to the certificate. It's very important that the name of this certificate be 127.0.0.1. Otherwise, the single-user tests won't be able to run.
b)	-eku 1.3.6.1.5.5.7.3.1 gives the purpose of the certificate. It indicates that the certificate can be used as a Secure Sockets Layer (SSL) server certificate.

Following certificates would be generated and saved in C:\Temp by above commands
a)	Authcert.pvk
b)	Authcert.cer
c)	Authcert.pfx
 
2)	Install authcert.pfx and authcert.cer certificates in Local Machine\My certificate store
 
4.	Copy authcert.pfx certificate to PerfSDK folder
 
5.	Make below changes in Visual Studio Online folder of your PerfSDK
1)	Replace setup.cmd content with below commands
setx testroot "%DeploymentDirectory%"
ECHO Installing D365 prerequisites
ECHO MSIEXEC /a %DeploymentDirectory%\msodbcsql /passive /norestart IACCEPTMSODBCSQLLICENSETERMS=YES
MSIEXEC /a %DeploymentDirectory%\msodbcsql /passive /norestart IACCEPTMSODBCSQLLICENSETERMS=YES
%windir%\sysnative\windowspowershell\v1.0\powershell.exe -File %DeploymentDirectory%\install-wif.ps1
Md %DeploymentDirectory%\Common\Team\Foundation\Performance\Framework
%DeploymentDirectory%\CloudCtuFakeACSInstall.cmd %DeploymentDirectory%\authcert.pfx
 
2)	Remove %TestCertPassword% from import command of CloudCtuFakeACSInstall.cmd
 

Prepare PerfSDKSample solution for multi-user testing

1.	In Visual Studio, go to Test > Test settings, set Default processor architecture to x64
 
2.	Retrieve Thumbprint of authcert.pfx certificate in your development environment by running below cmdlets with administrator. Save it in somewhere as you will need this when you configure tier 2 or above sandbox
cd Cert:\LocalMachine\My
Get-ChildItem | Where-Object { $_.Subject -like "CN=127.0.0.1" }
	 
NOTE: In environment with PU21+, by default there is certificate with 127.0.0.1 as issuer installed. Please make sure you retrieve the thumbprint of the certificate you generated
3.	Update CloudEnvironment.config to reflect your configurations
1)	Make sure HostName and SOAPHostName match your tier 2 or above sandbox environment
2)	Add thumbprint of authcert.pfx certificate as value of SelfSigningCertificateThumbprint in CloudEnviornment.Config 
3)	Update UserCount to reflect the number of testing users in your case
4)	Update UserFormat to reflect your test users naming convention
 
4.	Configure vsonline.testsettings
1)	Set Test Run Location as Run tests using local computer or a test controller in General tab
 
NOTE: in case you don’t see vsonline.testsettings, try to reopen the solution
2)	Check “Enable deployment” in Deployment tab and add below files or folders to Additional files and directories to deploy
Add directory	K:\PerfSDK\PerfSDKLocalDirectory\SampleProject\PerfSDKSample\bin\Debug
Add directory	K:\PerfSDK\PerfSDKLocalDirectory\Visual Studio Online
Add file	K:\PerfSDK\PerfSDKLocalDirectory\CloudEnvironment.Config
Add file	K:\PerfSDK\PerfSDKLocalDirectory\authcert.pfx
Add file	K:\PerfSDK\PerfSDKLocalDirectory\MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config
 
NOTE: when you’re promoted “Deployment item not in solution folder” warning, click OK to proceed
3)	Select Run test in 64 bits process on 64 bits machine as the value of Run tests in 32 bits or 64 bits process in Hosts tab
 
4)	Apply and close Test settings window
5.	Modify your C# performance class
1)	Add below using statement to your C# perf tests
using MS.Dynamics.TestTools.UIHelpers.Core;
	   
2)	Modify method TestSetup by adding below codes to the beginning of method TestSetup()
var testroot = System.Environment.GetEnvironmentVariable("DeploymentDir");
            if (string.IsNullOrEmpty(testroot))
            {
                testroot = System.IO.Directory.GetCurrentDirectory();
            }
            Environment.SetEnvironmentVariable("testroot", testroot); 
3)	Uncomment codes with multi-user comments and comment out line “Client = DispatchedClient.DefaultInstance;” in TestSetup method
 
4)	Modify TestCleanup method as follows
 
5)	Repeat these steps for all C# performance test classes you have
6.	Build the solution
7.	Select your test class in Test Mix of SampleLoadTest.loadtest
 
8.	Update Timing (warm-up, run, and cool-down duration) of Run Settings1 [Active] in SampleLoadTest.loadtest
 
9.	Update Constant User Count in Constant Load Pattern as the total number of users you want to run the test with
 
## Configure tier 2 or above sandbox for multi-user testing

1.	Install authcert.pfx and authcert.cer certificate in Local Machine\My in each of AOS machines
 
2.	Add thumbprint of authcert.pfx certificate in wif.config of your tier 2 or above sandbox
1)	Start Internet Information Services (IIS) Manager from Administrative Tools
2)	Click on AOSService under Sites of your IIS Manager
3)	Click on Explore in Actions section in right panel, then you will find wif.config in the bottom
4)	Add thumbprint of generated certificate in above step to the bottom of authority https://fakeacs.accesscontrol.windows.net/
 
5)	Save change
6)	Do an IISRESET
7)	Repeat 1) ~ 6) in each of AOS machines
3.	Create/import test users in your target environment. And assign them with System Administrator security role
 
NOTE: You could also create test users by running MS.Dynamics.Performance.CreateUsers.exe [UserCount] [CompanyCode]. In that case, you needn’t go through step 6 mentioned in above
Run multi-user testing with local test controller

1.	Open SampleLoadTest.loadtest
2.	Click on Run Load Test
 
 
3.	Review the test output
 


## Troubleshooting
Please refer to Troubleshooting guide for single or multi-user testing with Performance SDK 
