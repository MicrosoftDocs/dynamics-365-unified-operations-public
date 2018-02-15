---
# required metadata

title: Performance SDK and multiuser testing via Visual Studio Online
description: This tutorial introduces the Performance SDK and shows how to do multiuser testing via Visual Studio Online. It also shows how to convert a scenario that you recorded in Task recorder to a single-user test and then a multiuser test.
author: margoc
manager: AnnBe
ms.date: 01/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
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

# Performance SDK and multiuser testing via Visual Studio Online

[!include[banner](../includes/banner.md)]

This tutorial introduces the Performance software development kit (SDK) and shows how to do multiuser testing via Microsoft Visual Studio Online. It also shows how to convert a scenario that you recorded in Task recorder to a single-user test and then a multiuser test.

**Time to complete this tutorial:** 30 minutes

> [!NOTE]
> This tutorial requires that you access the environment as an administrator. For more information, see [Access instances](..\dev-tools\access-instances.md).

## Prerequisites

- Microsoft Visual Studio 2015 Enterprise
- A deployment that has volume data
- The Performance SDK (Look for a folder that is named **PerfSDK** on drive C or F, depending on your environment.)

## Create a single-user C# test from an XML recording

To view a video that shows how to create a single-user test, go to [https://mix.office.com/watch/qtdlasy2rcf3](https://mix.office.com/watch/qtdlasy2rcf3).

1. Use Task recorder to create a recording of the scenario that you want to test.
2. Start Microsoft Visual Studio as administrator, and build the **PerfSDKSample** project. This project is in the **PerfSDK** folder. If you've already built the project, skip this step.
3. Select **Dynamics 365** &gt; **Addins** &gt; **Create C# perf test from recording**.
4. In the **Import Task Recording** dialog box, enter the required details, and then select **Import**.

    [![Import Task Recording dialog box](./media/perf103a.png)](./media/perf103a.png)

    A C# test is generated in the Generated folder for the project that you selected.

## Run a single-user performance test by using the Performance SDK

1. In Control Panel in Microsoft Windows, select **System and Security** &gt; **System** &gt; **Advanced System Settings**. Verify that the **TestRoot** environment variable is set to the path of the PerfSDK folder.

    [![TestRoot environment variable set to the PerfSDK folder](./media/testroot.jpg)](./media/testroot.jpg)

2. Download the **selenium-dotnet-strongnamed-2.42.0.zip** and **IEDriverServer\_Win32\_2.42.0.zip** files from [http://selenium-release.storage.googleapis.com/index.html?path=2.42/](http://selenium-release.storage.googleapis.com/index.html?path=2.42/).
3. Extract the files, and copy the dynamic-link libraries (DLLs) to the **PerfSDK\\Common\\External\\Selenium** folder. Add a reference to **WebDriver.dll** to your project.

    [![DLLs in the PerfSDK\Common\External\Selenium folder](./media/perf103d.png)](./media/perf103d.png)

4. Generate and install a certificate. To generate a certificate file, open a Command Prompt window as an administrator, and run the following commands.

    ```
    C:\Program Files (x86)\Windows Kits\8.1\bin\x64>makecert -n "CN=TestAuthCert" -ss My -sr LocalMachine -a sha256 -len 2048 -cy end -r -eku 1.3.6.1.5.5.7.3.2 -sv c:\temp\authcert.pvk c:\temp\authcert.cer

    C:\Program Files (x86)\Windows Kits\8.1\bin\x64>pvk2pfx -pvk c:\temp\authcert.pvk -spc c:\temp\authcert.cer -pfx c:\temp\authcert.pfx
    ```

    Note the following elements in these commands:

    - **-n "CN=TestAuthCert"** gives a human-readable name to the certificate. You can adjust the name to suit your scenario.
    - **-eku 1.3.6.1.5.5.7.3.2** gives the purpose of the certificate. This certificate is a client authentication certificate instead of a code signing certificate, an encryption certificate, or some other type of certificate.

    When you're prompted for a private key password, select **None**.

    You should see the following files:

    - authcert.pfx
    - authcert.cer 
    - authcert.pvk

5. Install the **\*.pfx** certificate file. When you install it, make sure that you select **Local Machine**. Then copy the file to the **PerfSDK** folder.
6. Open a Microsoft Windows PowerShell window as an administrator, and run the following commands to get the thumbprint of the installed certificate.

    ```
    cd Cert:\LocalMachine\My
    Get-ChildItem | Where-Object { $_.Subject -like "CN=TestAuthCert" }
    ```

    [![Thumbprint of the installed certificate](./media/get-thumbprint.jpg)](./media/get-thumbprint.jpg)

7. In the **CloudEnvironment.Config** file, enter the thumbprint as the value for the **SelfSigningCertificateThumbprint** key.

    [![Updated CloudEnvironment.Config file](./media/config-thumbprint.jpg)](./media/config-thumbprint.jpg)

8. Follow these steps to update the **wif.config** file so that Application Object Server (AOS) trusts the certificate:

    1. Start Microsoft Internet Information Services (IIS), and find **Microsoft Dynamics 365 for Finance and Operations, Enterprise edition** in the list of sites.
    2. Select **Explore**, and find the **wif.config** file.

        [![wif.config file](./media/wifconfig.jpg)](./media/wifconfig.jpg)

    3. Update this file by entering the certificate and authority name.

        [![Updated wif.config file](./media/wif-updated.jpg)](./media/wif-updated.jpg)

    4. Restart IIS.

9. In Visual Studio, open the **PerfSDKSample** project, and find the **PurchaseReq.cs** file. This file is a sample single-user test. In the file, comment out the following lines.

    ```
    if (this.TestContext !=null)
    {
        timerProvider = new TimerProvider(this.TestContext);
    }
    ```

    [![Lines commented out in PurchaseReq.cs](./media/perf103e.png)](./media/perf103e.png)

10. Modify the **CloudEnvironment.Config** file by entering your admin user name. Here is an example.

    > [!NOTE]
    > **ConfigName** must be set to **DEVFABRIC**. 

    [![Updated CloudEnvironment.Config file](./media/perf103f.png)](./media/perf103f.png) 

11. In the **CloudEnvironment.Config** file, enter your endpoint.

    > [!NOTE]
    > If the environment is enabled for Application Request Routing (ARR), you have two endpoints. Here is an example:
    >
    > - apr-arr8aos**soap**.axcloud.test.dynamics.com
    > - apr-arr8aos.axcloud.test.dynamics.com
    >
    > In this case, you must enter both endpoints in the CloudEnvironment.Config file.
    >
    > [![Endpoints in CloudEnvironment.Config](./media/perf103upd.png)](./media/perf103upd.png)

12. Select **Test** &gt; **Test settings**, set **Default processor architecture** to **x64**, and then build the solution.
13. Select **Test** &gt; **Windows** &gt; **Test Explorer** to view the list of tests.

    > [!NOTE]
    > Sometimes, Visual Studio might not update the list of tests. In this case, restart Visual Studio, and then reopen Test Explorer.

    Your new test will be named **TestMethod**. If you change the method name of **TestMethod**, your test will receive an individual name. 

You can now run the test. When you run the test, Internet Explorer should be started, and it should replay the scenario that you recorded.

## Create a multiuser test from a single-user test

After you create a single-user test by using the information in the previous section, you can convert it to a multiuser test. Add **MS.Dynamics.TestTools.UIHelpers.Core;** to your test script, and find the following line in the **TestSetup** method.

```
Client = DispatchedClient.DefaultInstance;
```

Replace that line with the following lines.

```
DispatchedClientHelper helper = new DispatchedClientHelper();
Client = helper.GetClient();
```

Make sure that the values that you entered when you made the task recording are randomized. You might have to use the Data Expansion Tool first to generate test data.

## Set up Visual Studio Online for multiuser testing

For this example, you will use the ProcureToPay.cs file. To start Visual Studio, you must sign in to the [Visual Studio Online portal](https://app.vssps.visualstudio.com/profile/view), and then select **Open in Visual Studio**.

> [!NOTE]
> You must complete this step only one time. After you've signed in to Visual Studio Online, the settings are saved.

[![Open in Visual Studio](./media/vsonline-5-1024x323.jpg)](./media/vsonline-5.jpg)

1. Open the **PerfSDKSample** project.
2. In the **CloudEnvironment.Config** file, update the **UserFormat** entry so that it reflects the admin user URL. For example, for `admin@example.com`, use **TST\_{0}@example.com** as the user format. Additionally, change the **UserCount** value to the number of users that you want to have in your performance test.

    [![Updated CloudEnvironment.Config file](./media/vsonline-12.jpg)](./media/vsonline-12.jpg)

3. In the **PerfSDK** folder, run the following command to create test users for your environment.

    ```
    MS.Dynamics.Performance.CreateUsers.exe
    ```

    You can create as many users as you want. For example, the following command creates 150 test users for the USMF company.

    ```
    MS.Dynamics.Performance.CreateUsers.exe 150 USMF
    ```

4. Sign in to your endpoint as the admin user, and verify that users were created in the system.

### Test the sandbox environment

Up to this point, these instructions have made the assumption that you have a developer topology where the AOS machine is also your development machine.  If you would like to test a sandbox environment, you must follow these additional steps to establish trust between the sanbox and the computer running the load tests.  The computer running the load tests may be either your development machine or the test agent created by Visual Studio Online.

1. Establish a Remote Desktop connection to your sandbox AOS machine, and copy over the **.cer** file. Double-click the file to install it. When you're prompted for the certificate store, select **Personal**.
2. Start IIS, and find **AOSService** in the list of sites. Then select **Explore**, and find the **wif.config** file. Update this file by entering the certificate and authority name. (Use the values from the certificate that you generated earlier.)

    [![Updated wif.config file](./media/wif-updated.jpg)](./media/wif-updated.jpg)

3. Restart IIS.

You can now run performance tests against the topology.

> [!NOTE]
> If your topology has multiple AOS machines, you must install the certificate and update the wif.config file on each of them.

## Run the performance test

1. In the Visual Studio editor, open the **ProcureToPay.cs** file, and append the following lines in the **TestSetup** method.

    ```
    var testroot = System.Environment.GetEnvironmentVariable("DeploymentDir"); 
    if (string.IsNullOrEmpty(testroot)) 
    {
        testroot = System.IO.Directory.GetCurrentDirectory(); 
    } 
    Environment.SetEnvironmentVariable("testroot", testroot);
    ```

2. In your solution files, double-click the **vsonline.testsettings** file. In the **Test Settings** dialog box, on the **Deployment** tab, use the following settings:

    - Select the **Enable deployment** check box.
    - In the **Additional files and directories to deploy** field, make sure that the following files are listed:

        - &lt;Solution Directory&gt;\\FinancialBenchmark\\bin\\Debug\\
        - &lt;Solution Directory&gt;\\packages\\Newtonsoft.Json.6.0.5\\lib\\net45\\Newtonsoft.Json.dll
        - C:\\PerfSDK\\CloudEnvironment.Config
        - C:\\PerfSDK\\CsuClient.pfx
        - C:\\PerfSDK\\Microsoft.Dynamics.Xml.dll
        - C:\\PerfSDK\\Microsoft.IdentityModel.dll
        - C:\\PerfSDK\\MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config
        - C:\\PerfSDK\\SampleProject\\packages\\Newtonsoft.Json.6.0.5\\lib\\net45\\Newtonsoft.Json.dll
        - C:\\PerfSDK\\Visual Studio Online\\CloudCtuFakeACSInstall.cmd
        - C:\\PerfSDK\\Visual Studio Online\\install-wif.ps1

        > [!NOTE]
        > Your PerfSDK folder might differ.

3. On the **Setup and Cleanup Scripts** tab, select **setup.cmd**, which is located in **%testroot%Visual Studio Onlinesetup.cmd**.

    You might have to update your deployment configuration to reflect the certificate name (**CsuClient.pfx** in this tutorial) and password. Make sure that you add the \*.pfx file that you generated earlier, and update the following files:

    - **setup.cmd** – Update this file with **%DeploymentDirectory%CloudCtuFakeACSInstall.cmd %DeploymentDirectory%YourCertificate.pfx**.
    - **CloudCtuFakeACSInstall.cmd** – Update this file with the password of your certificate. (The password should be an empty string.)

4. On the **Additional Settings** tab, select **Run tests in 64 bit process on 64 bit machine**.
5. To run the test, open the **SampleLoadTest.loadtest** file, and select **Run Load Test**.

    [![Run Load Test](./media/perf103u.png)](./media/perf103u.png)

    When the test has finished running, you should see a summary that shows transaction results. Here is an example.

    [![Transaction results](./media/perf103v.png)](./media/perf103v.png)

6. To view various indicators for the test controller and test scenario, you can switch to the **Graphs** view.

    [![Graphs view](./media/perf103w.png)](./media/perf103w.png)

    > [!NOTE]
    > While tests are being run, information about your system isn't available in this view. To access this information, you must use Microsoft Dynamics Lifecycle Services (LCS) to monitor the CPU and memory usage of your AOS machine. Alternatively, you can set up perfmon directly on the AOS machine and set up the Microsoft Azure portal to monitor Microsoft SQL Server usage of Database Transaction Units (DTUs).

## Troubleshooting

### The web client is blank for a single-user test

When the single-user test is run and opens a web client, a website might not be loaded. Instead, the web client is blank, and a white page shows the message, "This is the initial start page for the WebDriver server." The test times out and fails, and an error message is shown.

#### Error example

```
Initialization method <Test class name>.TestSetup threw exception. System.TimeoutException: System.TimeoutException: No client was opened in the timeout period.
```

#### Solution

This issue can occur if trust hasn't been established with the LocalHostSSL certificate that was installed in the **SSL Certificate Add Failed** section above. To establish trust, make sure that the LocalHostSSL.cer file has been installed in the **Trusted Root Certification Authorities** store.

### Zoom factor

This issue only impacts single-user tests. 

#### Error example

```
Initialization method <Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Unexpected error launching Internet Explorer. Browser zoom level was set to 200%. It should be set to 100% (NoSuchDriver).
```
#### Solution

In Internet Explorer, you can change the zoom factor to 100 percent by changing the following registry keys:

- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\ResetZoomOnStartup = 0
- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\ResetZoomOnStartup2 = 0
- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\Zoomfactor = 80000
 
Depending on the version of the local machine that is used, before you start the Remote Desktop Protocol (RDP) session, you might have to select **Change the size of text, apps and other items**. This field is available in **Display settings** in Microsoft Windows. 
 
If those steps don't work, try to change the size of your remote desktop before you start the RDP session, so that the default zoom level in Internet Explorer is 100 percent.

### Certificate thumbprint errors

#### Error example

```
Initialization method MS.Dynamics.Performance.Application.TaskRecorder.TestRecord1Base.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --> 
MS.Dynamics.TestTools.CloudCommonTestUtilities.Exceptions.WebAuthenticationException: 
Failed finding the certificate for minting tokens by thumbprint: b4f01d2fc42718198852cd23957fc60a3e4bca2e
```

#### Solution

You might receive the error message for several reasons:

- The certificate thumbprint that you copied into the CloudEnvironment.Config and wif.config files includes invisible Unicode characters. To determine whether the thumbprint contains invisible Unicode characters, paste it into a Unicode code converter, and see whether extra characters appear in the **HTML/XML** field. For example, you may use the following unicode converter: https://r12a.github.io/apps/conversion/

    ![Unicode code converter](./media/sdk_unicode_code_converter.jpg)
 
- The certificate wasn't installed on the AOS machine. To verify that the certificate can be found on the AOS machine, run the following Windows PowerShell script.

    ```
    cd Cert:\LocalMachine\My
    Get-ChildItem | Where-Object { $_.Subject -like "CN=<name of your certificate>" }
    ```

    If the thumbprint doesn't appear in the Windows PowerShell console after you run the script, the certificate can't be found. To fix the issue, copy and install the .cer file that you created earlier in this topic to the AOS machine.
 
- If this issue occurs when you run load tests, the setup scripts might not have installed the corresponding .pfx file correctly. Verify that the password that is specified in the CloudCtuFakeACSInstall.cmd file matches the password that was set when the certificate was created.
 
    ![Password in the CloudCtuFakeACSInstall.cmd file](./media/set_cloudctufakeacsinstall.jpg)
 
### No endpoint is listening

This issue can occur when you run single-user or multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe.

#### Error example

The tests or user creation process fails, and the following error message is shown.

```
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.EndpointNotFoundException: There was no endpoint listening at <web address> that could accept the message. This is often caused by an incorrect address or SOAP action. 
```

#### Solution

This issue occurs when the host that is specified in the CloudEnvironment.Config file can't be accessed from the machine that is trying to run the tests or create users.
 
In the CloudEnvironment.Config file, review the values that are specified by the following keys.

- &lt;ExecutionConfigurations Key="HostName" Value="&lt;web address of host&gt;" /&gt;
- &lt;ExecutionConfigurations Key="SoapHostName" Value="&lt;web address of SOAP&gt;" /&gt;

The web addresses that are specified by these keys must be the environment that you're testing. Make sure that you can open the web address specified by the **HostName** key in a web browser from your developer machine.

For online load tests, the environment that is specified by the **HostName** field in the CloudEnvironment.Config file must be publicly accessible from any machine. Therefore, you won't be able to run the load test using Visual Studio Online to test a one-box environment since the endpoint won't be accessible outside of the one-box environment.

### Users can't be enumerated

This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe.

#### Error example

```
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Could not enumerate AX users ---> System.ServiceModel.FaultException'1[System.ComponentModel.Win32Exception]: Forbidden
```

#### Solution

There are two scenarios that can cause this error:
- The user who is specified as **SelfMintingAdminUser** must be a member of the System Administrator role. This issue occurs when the **SelfMintingAdminUser** is a user that is not assigned the System Administrator role. To verify that you've specified the correct user, you can sign in to the endpoint and view the user's roles.

![Admin user](./media/sdk_admin.png)

- The user who is specified as **SelfMintingAdminUser** has a provider other than "https://sts.windows-ppe.net/" or "https://sts.windows.net/". Sometimes the admin user will have a company specific domain included in the provider field. To work around this issue, create a user in AX with any name and email. Assign this new user the System Administrator role.  You do not need to link this user to a real Azure Active Directory user. Specify this new admin user as the **SelfMintingAdminUser** in the CloudEnvironment.config

### Forbidden request that has the Anonymous client authentication scheme

#### Error example

```
Initialization method <Test class name>.TestSetup threw exception. System.ServiceModel.Security.MessageSecurityException: System.ServiceModel.Security.MessageSecurityException: The HTTP request was forbidden with client authentication scheme 'Anonymous'. ---> System.Net.WebException: The remote server returned an error: (403) Forbidden..
```

#### Solution

This issue can occur when the number of users that you specify in the **UserCount** field in the CloudEnvironment.Config file exceeds the number of test users that you created by running MS.Dynamics.Performance.CreateUsers.exe. Make sure that you created more test users than you request in the CloudEnvironment.Config file.
 
![Cloud environment configuration](./media/cloud-env-config.png)

### At least one security token in the message could not be validated

This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe. It tends to occur when the AOS machine differs from the developer machine. 

#### Error example

```
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.Security.MessageSecurityException: An unsecured or incorrectly secured fault was received from the other party. See the inner FaultException for the fault code and detail. ---> System.ServiceModel.FaultException: At least one security token in the message could not be validated.
```

#### Solution

This issue occurs when the AOS endpoint can't validate the thumbprint of the certificate that you created. There are two possible causes:

- The certificate wasn't installed on the AOS machine. To fix the issue, copy and install the .cer file that you created earlier in this topic to the AOS machine.
- The thumbprint of the certificate wasn't added to the wif.config file on the AOS machine. To fix the issue, see step 8 of the "Run a single-user performance test by using the Performance SDK" section for details on how to add the certificate to the wif.config file. Be sure to restart IIS after you modify the wif.config file.
 
### MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config is missing from the deployment items

This issue usually occurs only when you run load tests.

#### Error example

```
<Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Could not find endpoint element with name 'ClientCommunicationManager' and contract 'Microsoft.Dynamics.Client.InteractionService.Communication.Reliable.IReliableCommunicationManager' in the ServiceModel client configuration section. This might be because no configuration file was found for your application, or because no endpoint element matching this name could be found in the client element.. at System.ServiceModel.Description.ConfigLoader.LoadChannelBehaviors(ServiceEndpoint serviceEndpoint, String configurationName)
```

#### Solution

This issue occurs when the system can't find the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file when the load tests are run, because the file wasn't added as a deployment item. Verify whether the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file is in the Out folder for the test run: 

&lt;solution path&gt;\\TestResults\\&lt;your test run&gt;\\Out

If the file is missing, add it to the deployment items in the test settings.
 
Note that there are two files that have very similar names. The name of one file ends in **\*.dll**, and the name of the other file ends in **\*.dll.config**. The **\*.dll.config** file must be in the deployment items in the test settings.
 
### CloudEnvironment.Config is missing from the deployment items

This issue usually occurs only when you run load tests.

#### Error example

```
Initialization method <Test class name>.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> MS.Dynamics.TestTools.TestLogging.EvaluateException: Assert.Fail failed. DateTime="10/13/2017 14:42:55" "The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception.".
```

#### Solution

This issue occurs when the CloudEnvironment.Config file isn't present when the tests are run. The issue typically occurs when you run load tests and the CloudEnvironment.Config file wasn't added as a deployment item. Verify whether the CloudEnvironment.Config file is in the Out folder for the test run:

&lt;solution path&gt;\\TestResults\\&lt;your test run&gt;\\Out

If the file is missing, add it to the deployment items in the test settings.

![Test settings](./media/test-settings.png)

### InteractiveClientID wasn't specified in the settings

#### Error example

```
The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception. --->
Microsoft.CE.VaultSDK.SecretProviderException: InteractiveClientId was not specified in settings
```

#### Solution

This issue occurs when the **SelfSigningCertificateThumbprint** field is left blank in the CloudEnvironment.Config file. In the CloudEnvironment.Config file, paste the thumbprint of the certificate that you created and installed in the following line.

```
<ExecutionConfigurations Key="SelfSigningCertificateThumbprint" Value="" />
```

### The remote host forcibly closed an existing connection

#### Error example

```
System.TypeInitializationException: System.TypeInitializationException: The type initializer for
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --->
System.ServiceModel.CommunicationException: An error occurred while making the HTTP request to
<Host name>/Services/AxUserManagement/Service.svc/ws2007FedHttp. This could be due to the fact 
that the server certificate is not configured properly with HTTP.SYS in the HTTPS case. This could also be caused 
by a mismatch of the security binding between the client and the server.** ---> System.Net.WebException: 
The underlying connection was closed: An unexpected error occurred on a send. ---> System.IO.IOException: 
Unable to read data from the transport connection: An existing connection was forcibly closed by the remote host. ---> 
System.Net.Sockets.SocketException: An existing connection was forcibly closed by the remote host. 
```

#### Solution

Run the following Windows PowerShell script on the development machine.

```
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false
if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319)) 
{
    Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false 
}
```
