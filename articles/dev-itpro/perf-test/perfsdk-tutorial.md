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
- Performance SDK (Look for a folder that is named **PerfSDK** on drive C or F, depending on your environment.)

## Create a single-user C# test from an XML recording

To view a video that shows how to create a single-user test, go to [https://mix.office.com/watch/qtdlasy2rcf3](https://mix.office.com/watch/qtdlasy2rcf3).

1. Use Task recorder to create a recording of the scenario that you want to test.
2. Start Microsoft Visual Studio as administrator, and build the **PerfSDKSample** project. This project is in the **PerfSDK** folder. If you've already built the project, skip this step.
3. Select **Dynamics 365** > **Addins** > **Create C# perf test from recording**.
4. In the **Import Task Recording** dialog box, enter the required details, and then select **Import**.

    [![Import Task Recording dialog box](./media/perf103a.png)](./media/perf103a.png)

    A C# test is generated in the **Generated** folder for the project that you selected.

## Run a single-user performance test by using the Performance SDK

1. In Control Panel, select **System and Security** > **System** > **Advanced System Settings**. Verify that the **TestRoot** environment variable is set to the path of the PerfSDK folder.

    [![TestRoot environment variable set to the PerfSDK folder](./media/testroot.jpg)](./media/testroot.jpg)[](./media/perf103c.png)

2. Download **selenium-dotnet-strongnamed-2.42.0.zip** and **IEDriverServer\_Win32\_2.42.0.zip** from [http://selenium-release.storage.googleapis.com/index.html?path=2.42/](http://selenium-release.storage.googleapis.com/index.html?path=2.42/).
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
6. Open a Microsoft Windows PowerShell window as an administrator, and run the following command to get the thumbprint of the installed certificate.

    ```
    PS Cert:\LocalMachine\My> cd Cert:\LocalMachine\My
    PS Cert:\LocalMachine\My> Get-ChildItem | Where-Object { $_.Subject -like "CN=TestAuthCert" }
    ```

    [![Thumbprint of the installed certificate](./media/get-thumbprint.jpg)](./media/get-thumbprint.jpg)

7. In the **CloudEnvironment.Config** file, enter the thumbprint as the value for the **SelfSigningCertificateThumbprint** key.

    [![Updated CloudEnvironment.Config file](./media/config-thumbprint.jpg)](./media/config-thumbprint.jpg)

8. Follow these steps to update the **wif.config** file so that Application Object Server (AOS) trusts the certificate:

    1. Start Internet Information Services (IIS), and find **Microsoft Dynamics 365 for Finance and Operations, Enterprise edition** in the list of sites.
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

    Your new test will be named **TestMethod**. If you change the method name of **TestMethod**, your test will get an individual name. 

You can now run the test. When you run the test, Internet Explorer should be started, and it should replay the scenario that you recorded.

## Create a multiuser test from a single-user test

After you create a single-user test by using the information in the previous section, you can convert it to a multiuser test. Add **MS.Dynamics.TestTools.UIHelpers.Core;** to your test script, and replace the following line in the **TestSetup** method.

```
Client = DispatchedClient.DefaultInstance;
With
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

For this step, you must have a developer topology. Follow the instructions in the previous section. You must follow these additional steps to establish trust between your developer topology and/or the Visual Studio Online test agent.

1. Establish a Remote Desktop connection to your AOS machine, and copy over the .cer file. Double-click the file to install it. When you're prompted for the certificate store, select **Personal**.
2. Start IIS, and find **AOSService** in the list of sites. Then select **Explore**, and find the **wif.config** file. Update this file by entering the certificate and authority name. (Use the values from the certificate that you generated earlier.)

    [![Updated wif.config file](./media/wif-updated.jpg)](./media/wif-updated.jpg)

3. Restart IIS.

You can now run performance tests against the topology.

> [!NOTE]
> If your topology has multiple AOS machines, you must install certificate and update the wif.config file on each of them.

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

6. To view different indicators for the test controller and test scenario, you can switch to the **Graphs** view.

    [![Graphs view](./media/perf103w.png)](./media/perf103w.png)

    > [!NOTE]
    > Information about your system while testing isn't available in this view. To access this information, you must use Microsoft Dynamics Lifecycle Services (LCS) to monitor the CPU and memory usage of your AOS machine. Alternatively, you can set up perfmon directly on the AOS machine, and set up the Windows Azure portal to monitor SQL Server usage of Database Transaction Units (DTUs).

## Troubleshooting

### Blank Web Client for Single User Test
The single user test runs and opens a web client.  A website is never loaded.  Instead, there is an empty web client with a white screen with the message "This is the initial start page for the WebDriver server" at the top of the page.  The test will eventually timeout and fail with an error message.

#### Error Example

```
Initialization method <Test class name>.TestSetup threw exception. System.TimeoutException: System.TimeoutException: No client was opened in the timeout period.
```
#### Solution
This problem can happen if trust has not been established with the LocalHostSSL certificate that was installed in the **SSL Certificate Add Failed** section above. To establish trust, ensure that the LocalHostSSL.cer has been installed in the **Trusted Root Certification Authorities** store.

### Zoom Factor
This issue occurs during single user tests. The test will fail very quickly with an error message.

#### Error Example

```Initialization method <Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Unexpected error launching Internet Explorer. Browser zoom level was set to 200%. It should be set to 100% (NoSuchDriver).
```
#### Solution
The IE zoom factor can be set to 100% by changing the following keys:
•	Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\ResetZoomOnStartup = 0
•	Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\ResetZoomOnStartup2 = 0
•	Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Internet Explorer\Zoom\Zoomfactor = 80000
 
Depending on the version of the local machine that is being used, before starting the RDP session it may be necessary to click **Change the size of text, apps and other items**. This field is available in the Windows **Display settings**. 
 
If none of this works, try changing the size of your remote desktop before starting the RDP session so that the default Internet Explorer zoom level is 100%. This is only necessary for single user tests.

### Certificate Thumbprint Errors

#### Error Example

```
Initialization method MS.Dynamics.Performance.Application.TaskRecorder.TestRecord1Base.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --> 
MS.Dynamics.TestTools.CloudCommonTestUtilities.Exceptions.WebAuthenticationException: 
Failed finding the certificate for minting tokens by thumbprint: b4f01d2fc42718198852cd23957fc60a3e4bca2e
```

#### Solution
There are a number of reasons that you could be seeing this error message:
1.	There could be invisible unicode characters in the certificate's thumbprint when you copied it into CloudEnvironment.config and wif.config.  To check this, paste your thumbprint into a Unicode code converter and see if extra characters show up in the HTML/XML field:

![Unicode code converter](./media/sdk_unicode_code_converter.jpg)
 

 
2.	The certificate may not be installed on the AOS machine. Check that the certificate can be found on the AOS machine by running the following PowerShell script:

```
cd Cert:\LocalMachine\My
Get-ChildItem | Where-Object { $_.Subject -like "CN=<your certificate's name>" }
```


If the thumbprint is not printed in the PowerShell console after running the script, this means the certificate cannot be found and must be installed following the steps described earlier in the instructions
 
3.	If this issue is present when running load tests, it is possible that the corresponding .pfx file is not being installed correctly by the setup scripts.  Check that the password specified in CloudCtuFakeACSInstall.cmd matches the password that the certificate was created with:
 
![Match password](./media/set_cloudctufakeacsinstall.jpg)
 
### No Endpoint Listening
This issue can show up when running single or multi-user tests, or when creating users with MS.Dynamics.Performance.CreateUsers.exe.
#### Error Example
Failed with the following error:


```
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.EndpointNotFoundException: There was no endpoint listening at <web address> that could accept the message. This is often caused by an incorrect address or SOAP action. 
```

#### Solution
This issue indicates that the host specified in the CloudEnvironment.config is not accessible from the machine which is attempting to run the tests or create users.
 
In the CloudEnvironment.config file, check the values specified by the following keys:

```
<ExecutionConfigurations Key="HostName" Value="web address of host" />
<ExecutionConfigurations Key="SoapHostName" Value="web address of SOAP" />
```
The web addresses specified here must be the environment that you are testing.  Ensure that you can navigate to this web address within a web browser from your developer machine.
 
In the case of online load tests, the environment specified by the HostName field in the CloudEnvironment.config must be publicly accessible from any machine.  This means that you will not be able to load test a OneBox environment using Visual Studio Online.


### Could Not Enumerate AX Users
This issue can show up when running multi-user tests or creating users with MS.Dynamics.Performance.CreateUsers.exe.

#### Error Example

```System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Could not enumerate AX users ---> System.ServiceModel.FaultException'1[System.ComponentModel.Win32Exception]: Forbidden
```


#### Solution
The user specified as the SelfMintingAdminUser must have the System Administrator role. This error will occur when the wrong user is specified as the SelfMintingAdminUser. You can check that you are specifying the correct user by logging onto the endpoint and viewing the user's roles.

![Administrator user](./media/sdk_admin.png)

### Forbidden Request with Client Authentication Scheme 'Anonymous'

#### Error Example
```
Initialization method <Test class name>.TestSetup threw exception. System.ServiceModel.Security.MessageSecurityException: System.ServiceModel.Security.MessageSecurityException: The HTTP request was forbidden with client authentication scheme 'Anonymous'. ---> System.Net.WebException: The remote server returned an error: (403) Forbidden..
```

#### Solution
This issue can occur when the number of users specified by the UserCount field in the CloudEnvironment.config  is greater than the number of test users created by running MS.Dynamics.Performance.CreateUsers.exe.  Ensure that you created more test users than you are requesting in CloudEnvironment.config
 
![Cloud environment configuration](./media/cloud-env-config.png)

### At Least One Security Token Could Not Be Validated
This issue can show up when running multi-user tests or creating users with MS.Dynamics.Performance.CreateUsers.exe. The issue tends to be present when the AOS machine is a different machine than the developer machine. 

#### Error Example


```System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.Security.MessageSecurityException: An unsecured or incorrectly secured fault was received from the other party. See the inner FaultException for the fault code and detail. ---> System.ServiceModel.FaultException: At least one security token in the message could not be validated.
```

#### Solution
This issue is caused by the AOS endpoint not being able to validate the thumbprint of the certificate you created. The two possible reasons for this are the following:
1.	The certificate has not been installed on the AOS machine.
2.	The thumbprint of the certificate was not added to the wif.config file on the AOS machine.
 
For the case where the certificate has not been installed on the AOS machine, copy the .cer file that you created earlier in the instructions to the AOS machine. Install the .cer file in the "Trusted Root Certification Authorities" store on the AOS machine
 
For the case where the thumbprint of the certificate has not been added to the wif.config, please refer back to the section that describes the lines that must be added to the wif.config. Be sure to perform IISRESET after modifying wif.config.
 
### Missing MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config in Deployment Items
This issue usually only occurs when performing load tests.

#### Error Example

```
<Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Could not find endpoint element with name 'ClientCommunicationManager' and contract 'Microsoft.Dynamics.Client.InteractionService.Communication.Reliable.IReliableCommunicationManager' in the ServiceModel client configuration section. This might be because no configuration file was found for your application, or because no endpoint element matching this name could be found in the client element.. at System.ServiceModel.Description.ConfigLoader.LoadChannelBehaviors(ServiceEndpoint serviceEndpoint, String configurationName)
```

#### Solution
This is caused by being unable to locate the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file when the load tests run. This happens when the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file was not added as a deployment item. To verify that this is the case, check if the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config is in the out folder for the test run: 

```
<solution path>\TestResults\<your test run>\Out
```

If the config file is missing, simply add it to the deployment items in the test settings in the same way as in Issue 6.
 
Note that there are two very similarly named files. One is *.dll and one is *.dll.config. The *.dll.config must be in the deployment items in the test settings.
 
### Missing CloudEnvironment.config in Deployment Items
This issue usually only occurs when performing load tests.

#### Error Example

```
Initialization method <Test class name>.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> MS.Dynamics.TestTools.TestLogging.EvaluateException: Assert.Fail failed. DateTime="10/13/2017 14:42:55" "The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception.".
```

#### Solution
This issue is caused when the CloudEnvironment.config file is not present when the tests run. Typically shows up when running load tests and the CloudEnvironment.config file was not added as a deployment item. To verify that this is the case, check if the CloudEnvironment.config is in the out folder for the test run: <solution path>\TestResults\<your test run>\Out
If the config file is missing, simply add it to the deployment items in the test settings:


![Test settings](./media/test-settings.png)

### InteractiveClientID was not Specified in Settings

#### Error Example
```The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception. --->
Microsoft.CE.VaultSDK.SecretProviderException: InteractiveClientId was not specified in settings
```

#### Solution
This error occurs when the field SelfSigningCertificateThumbprint is left blank in the CloudEnvironment.config file. Paste the thumbprint of the certificate you created and installed in the following line in the CloudEnvironment.config file:

```
<ExecutionConfigurations Key="SelfSigningCertificateThumbprint" Value="" />
``` 
### An Existing Connection was Forcibly Closed by the Remote Host

#### Error Example

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
Run the following Windows PowerShell script on the development machine:

```
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false
if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319)) 
{ 
 Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false 
}
```
