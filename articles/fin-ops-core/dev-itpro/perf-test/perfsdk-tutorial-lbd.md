---
title: Performance SDK and multiuser testing in on-premises environments
description: This article explains how to use the Performance software development kit (SDK) to do multiuser load testing in an on-premises environment.
author: ytong
ms.date: 03/22/2023
ms.topic: article
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: ytong
ms.search.validFrom: 2018-XX-XX
ms.dyn365.ops.version: Platform update 19
---

# Performance SDK and multiuser testing in on-premises environments

[!include [banner](../includes/banner.md)]

This article explains how to use the Performance software development kit (SDK) to do multiuser load testing in an on-premises environment.

  > [!IMPORTANT]
  > Visual Studio 2019 is the last version of Visual Studio that includes web performance and load testing features and will be deprecated in the future. We suggest using Apache JMeter for performance testing. For more information, see [JMeter](https://jmeter.apache.org/).


## Prerequisites

- An on-premises environment that has volume data
- A development environment that has the following characteristics:

    - Microsoft Visual Studio Enterprise or a later version is installed.
    - The Performance SDK is installed. (The SDK will likely be in K:\\PerfSDK\\PerfSDKLocalDirectory. However, depending on your environment, it might be in another location, such as C:\\PerfSDK.)
    - The on-premises environment can be accessed in a web browser. (The development virtual machine [VM] might be in the same domain as the on-premises environment, or the on-premises environment might have a publicly registered domain name.)

## Create a single-user C# test from an XML recording

1. Use Task recorder to create a recording of the scenario that you want to test.

    > [!IMPORTANT]
    > Your task recording must start on the default dashboard page. Otherwise, the test won't be able to run.

2. Start Microsoft Visual Studio as an administrator, and build the **PerfSDKSample** project. This project is in the **PerfSDK** folder. If you've already built the project, skip this step.
3. Select **Dynamics 365** &gt; **Addins** &gt; **Create C# perf test from recording**.
4. In the **Import Task Recording** dialog box, enter the required details, and then select **Import**.

    [![Import Task Recording dialog box.](./media/perf103a.png)](./media/perf103a.png)

    A C# test is generated in the Generated folder for the project that you selected.

    > [!NOTE]
    > The test that is generated might have to be edited to resolve any compilation issues.

## Run a single-user test by using the Performance SDK

### Prepare the development environment
Follow these steps in the development environment.

1. In Control Panel in Microsoft Windows, select **System and Security** &gt; **System** &gt; **Advanced System Settings**. Verify that the **TestRoot** environment variable is set to the path of the PerfSDK folder.

    [![TestRoot environment variable.](./media/EnvironmentVariable.PNG)](./media/EnvironmentVariable.PNG)

2. Download the **selenium-dotnet-strongnamed-2.42.0.zip** and **IEDriverServer\_Win32\_2.42.0.zip** files from [https://selenium-release.storage.googleapis.com/index.html?path=2.42/](https://selenium-release.storage.googleapis.com/index.html?path=2.42/), and extract the files.
3. Copy the dynamic-link libraries (DLLs) from the **selenium-dotnet-strongnamed-2.42.0.zip\net40** folder to the **PerfSDK\\Common\\External\\Selenium** folder. Also copy the **IEDriverServer.exe** from the **IEDriverServer\_Win32\_2.42.0.zip** to the **PerfSDK\\Common\\External\\Selenium** folder.

    [![DLLs in the PerfSDK\Common\External\Selenium folder.](./media/perf103d.png)](./media/perf103d.png)

4. Generate a certificate to use for authentication for the tests. To generate a certificate file, open a Command Prompt window as an administrator, and run the following commands. When you're prompted for a private key password, select **None**.

    ```Console
    "C:\Program Files (x86)\Windows Kits\8.1\bin\x64\makecert" -n "CN=127.0.0.1" -ss Root -sr LocalMachine -a sha256 -len 2048 -cy end -r -eku 1.3.6.1.5.5.7.3.1 -sv c:\temp\authcert.pvk c:\temp\authcert.cer

    "c:\Program Files (x86)\Windows Kits\8.1\bin\x64\pvk2pfx" -pvk c:\temp\authCert.pvk -spc c:\temp\authcert.cer -pfx c:\temp\authcert.pfx
    ```

    Note the following elements in these commands:

    - **-n "CN=127.0.0.1"** gives a human-readable name to the certificate. The name of this certificate must be **127.0.0.1**. Otherwise, the single-user tests won't be able to run.
    - **-eku 1.3.6.1.5.5.7.3.1** gives the purpose of the certificate. It indicates that the certificate can be used as a Secure Sockets Layer (SSL) server certificate.

    After the script has finished running, you should see the following files in **C:\\Temp**:

    - authcert.pfx
    - authcert.cer
    - authcert.pvk

5. Install the **authcert.pfx** certificate file. When you install the file, make sure that you select **Local Machine**.
6. Copy the **authcert.pfx** file to the **PerfSDK** folder.
7. Open a Microsoft Windows PowerShell window as an administrator, and run the following commands to get the thumbprint of the installed certificate.

    ```powershell
    cd Cert:\LocalMachine\My

    Get-ChildItem | Where-Object { $_.Subject -like "CN=127.0.0.1" }
    ```

8. In Visual Studio, open the **PerfSDKSample** project that is in the **PerfSDK** folder.
9. In the Visual Studio project, add a reference to the **WebDriver.dll** file in the **PerfSDK\\Common\\External\\Selenium** folder.
10. Open the **CloudEnvironment.Config** file, and replace the contents with the following template.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <EnvironmentalConfigSettings xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <EnvironmentalConfigSettingsCollection>
            <EnvironmentalConfigSetting ConfigName="DEVFABRIC">
                <!-- NOTE: the HostName value needs to be specified -->
                <ExecutionConfigurations Key="HostName" Value="[yourD365FOdomain]/namespaces/AXSF" />
                <ExecutionConfigurations Key="SoapHostName" Value="[yourD365FOdomain]/namespaces/AXSF" />
                <ExecutionConfigurations Key="SelfSigningCertificateThumbprint" Value="[ThumbprintFromPowerShell]" />
                <ExecutionConfigurations Key="AdminAuthenticatorConfigurationId" Value="SelfMintingAdminUser" />
                <ExecutionConfigurations Key="DefaultBrowser" Value="InternetExplorer" />
                <ExecutionConfigurations Key="FederationRealm" Value="spn:00000015-0000-0000-c000-000000000000" />
                <ExecutionConfigurations Key="DefaultDispatcher" Value="Microsoft.Dynamics.TestTools.Dispatcher.JsDispatcher, Microsoft.Dynamics.TestTools.Dispatcher.JsDispatcher" />
                <ExecutionConfigurationsNodes ConfigurationName="SVC">
                    <ConfigurationSpecificDetails Key="AppConfig" Value="DEVFABRIC.Config" />
                </ExecutionConfigurationsNodes>
                <ExecutionConfigurationsNodes ConfigurationName="PRF">
                    <ConfigurationSpecificDetails Key="IsAdfs" Value="True" />
                    <ConfigurationSpecificDetails Key="UserCount" Value="2" />
                    <ConfigurationSpecificDetails Key="UserFormat" Value="[AdminUserEmail]" />
                    <ConfigurationSpecificDetails Key="UserPassword" Value="[AdminUserPassword]" />
                    <ConfigurationSpecificDetails Key="UserRole" Value="-SYSADMIN-" />
                    <ConfigurationSpecificDetails Key="ThinkTime" Value="0" />
                    <ConfigurationSpecificDetails Key="Company" Value="USMF" />
                </ExecutionConfigurationsNodes>
            </EnvironmentalConfigSetting>
        </EnvironmentalConfigSettingsCollection>
        <AuthenticatorConfigurationCollection>
            <AuthenticatorConfiguration Id="SelfMintingRunnerUser" Class="MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SelfMintedTokenAuthenticator">
                <Credentials IsFromKeyVault="false" Username="daxrunneruser@daxmdsrunner.com" NetworkDomain="urn:Microsoft:Dynamics:Cloud:DaxRunner" />
            </AuthenticatorConfiguration>
            <AuthenticatorConfiguration Id="SelfMintingSysUser" Class="MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SelfMintedTokenAuthenticator">
                <Credentials IsFromKeyVault="false" Username="testuser@microsoft.com" />
            </AuthenticatorConfiguration>
            <AuthenticatorConfiguration Id="SelfMintingAdminUser" Class="MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SelfMintedTokenAuthenticator">
                <!-- NOTE: admin username needs to be specified -->
                <Credentials IsFromKeyVault="false" Username="[AdminUserEmail]" NetworkDomain="[AdfsUrl]" />
            </AuthenticatorConfiguration>
        </AuthenticatorConfigurationCollection>
    </EnvironmentalConfigSettings
    ```

11. In the **CloudEnvironment.Config** file, specify values for the following keys. These values replace the placeholder values in square brackets in the template.

    - **HostName** – Specify the URL that is used to access your on-premises environment. The URL should be **\[yourD365FOdomain\]/namespaces/AXSF**.
    - **SoapHostName** – Specify the same URL that you specified for **HostName**.
    - **SelfSigningCertificateThumbprint** – Specify the thumbprint that you retrieved from Windows PowerShell in step 7.
    - **UserFormat** – Specify the email address of a user who has the System Administrator role in your on-premises environment. The user must be an Active Directory Federation Services (AD FS) user.
    - **UserPassword** – Specify the password of the user whose email address you specified for **UserFormat**.
    - **Username** – Specify the same email address that you specified for **UserFormat**.
    - **NetworkDomain** – Specify the URL of the AD FS identity provider. You can find this value by running the following SQL query against the **AXDB** database of your on-premises deployment.

        ```sql
        select NETWORKDOMAIN, NETWORKALIAS from USERINFO where NETWORKALIAS='[AdminUserEmail]'
        ```

### Prepare the on-premises environment
Follow these steps on each Application Object Server (AOS) VM in the on-premises deployment.

1. Copy the **authcert.cer** file that you created in the [Prepare the development environment](#prepare-the-development-environment) section of this article to the AOS VM.
2. Install the **authcert.cer** certificate file. When you install the certificate, make sure that you select **Local Machine**. Also make sure that you put the certificate in the **Trusted Root Certification Authorities** store.
3. Open the **wif.config** file in a text editor. The path of the file will resemble **C:\\ProgramData\\SF\\AOS1\\Fabric\\work\\Applications\\AXSFType\_App19\\AXSF.Code.1.0.20180717001108**.

    > [!NOTE]
    > In the file path, the AOS number (**AOS1** in this example) will vary, depending on the AOS node that you're on. Additionally, the **ProgramData** folder is a hidden folder. Therefore, to see the folder in File Explorer, you must enable hidden items.

4. In the **wif.config** file, find the authority that is named `https://fakeacs.accesscontrol.windows.net`. In the list of thumbprints for this authority, add the thumbprint of the certificate that you created in the [Prepare the development environment](#prepare-the-development-environment) section. In the following example, the fourth thumbprint has been added to the `https://fakeacs.accesscontrol.windows.net` authority.

    ```xml
    <authority name="https://fakeacs.accesscontrol.windows.net/">
        <keys>
            <add thumbprint="9567B0F32F4B312FEE44ACE88A9CAAA13B7FBB86" />
            <add thumbprint="B8F659E2FDD2A6811CD72BE753FF7ACB64351AC1" />
            <add thumbprint="B51C394E6EE9578D8C54AE0A9927D8B6DCEFF84B" />
            <add thumbprint="F9112DE3D4DE65CBE39601EBDC7FBB1F8F525DED" />
        </keys>
        <validIssuers>
            <add name="https://fakeacs.accesscontrol.windows.net/" />
        </validIssuers>
    </authority>
    ```

5. Open the **AXService.exe.config** file in a text editor. You can find this file in the same directory as the **wif.config** file.
6. Search the **AXService.exe.config** file for **"Aos.AosRole"**. Replace the line that contains **"Aos.AosRole"** with the following line.

    ```xml
    <add key="Aos.AosRole" value="AosRoleUnknown" />
    ```

    > [!NOTE]
    > Setting the **AosRole** to **AosRoleUnknown** disables the limit on the number of web sessions per user. This is necessary to complete load testing with a large user load because the load test will create many sessions for a single user. Once you are finished with your load testing, reset this value to **"AosRoleWeb"**.


7. In Service Fabric Explorer, find the **Code** package for the AOS node, select the ellipse button (**...**), and then select **Restart** to restart the application.

    ![Restarting finance and operations from Service Fabric Explorer.](./media/ServiceFabricExplorerRestart.png)

### Run the single-user test

1. In the **PerfSDKSample** project, find the **PurchaseReq.cs** file. This file is a sample single-user test. In the file, comment out the following lines.

    ```csharp
    if (this.TestContext !=null)
    {
        timerProvider = new TimerProvider(this.TestContext);
    }
    ```

    [![Lines commented out in PurchaseReq.cs.](./media/perf103e.png)](./media/perf103e.png)

2. Select **Test** &gt; **Test settings**, set the **Default processor architecture** field to **x64**, and then build the solution.
3. Select **Test** &gt; **Windows** &gt; **Test Explorer** to view the list of tests.

    > [!NOTE]
    > Sometimes, Visual Studio might not update the list of tests after you create a test script from a task recording. In this case, restart Visual Studio, and then reopen Test Explorer.

4. Run the sample single-user test by right-clicking **CreatePurchReq**. Alternatively, you can run the test that you created from your task recording. When you run the test, Internet Explorer should be started, and it should replay the scenario that you recorded.

## Run a multiuser load test by using the Performance SDK

### Create a multiuser test from a single-user test

After you create a single-user test by using the information earlier in this article, you can convert it to a multiuser test. Add **MS.Dynamics.TestTools.UIHelpers.Core;** to your test script, and find the following line in the **TestSetup** method.

```csharp
Client = DispatchedClient.DefaultInstance;
```

Replace that line with the following lines.

```csharp
DispatchedClientHelper helper = new DispatchedClientHelper();
Client = helper.GetClient();
```

The test script that was generated by the Task Importer might contain a line that resembles the following line.

```csharp
UserContextRole _context = new UserContextRole(UserManagement.AdminUser);
```

Remove this line from any tests that will be run as load tests. This code is required only for single-user tests and has a negative effect on the performance of load tests.

Make sure that the values that you entered when you made the task recording are randomized.

### Run the multiuser load test

1. In the Visual Studio editor, open the **ProcureToPay.cs** file, and append the following lines in the **TestSetup** method.

    ```csharp
    var testroot = System.Environment.GetEnvironmentVariable("DeploymentDir"); 
    if (string.IsNullOrEmpty(testroot)) 
    {
        testroot = System.IO.Directory.GetCurrentDirectory(); 
    } 
    Environment.SetEnvironmentVariable("testroot", testroot);
    ```

2. Download the installer (.msi) file for Microsoft ODBC Driver 13 for SQL Server from [https://www.microsoft.com/download/details.aspx?id=50420](https://www.microsoft.com/download/details.aspx?id=50420). (Select the 64-bit version of the .msi file.) Put the file in the **Visual Studio Online** folder in the **PerfSDK** directory.
3. Modify the contents of the **setup.cmd** file in the **Visual Studio Online** folder so that they match the following code.

    ```Console
    setx testroot "%DeploymentDirectory%"
    ECHO Installing D365 prerequisites
    ECHO MSIEXEC /a %DeploymentDirectory%\msodbcsql /passive /norestart IACCEPTMSODBCSQLLICENSETERMS=YES
    MSIEXEC /a %DeploymentDirectory%\msodbcsql /passive /norestart IACCEPTMSODBCSQLLICENSETERMS=YES
    %windir%\sysnative\windowspowershell\v1.0\powershell.exe -File %DeploymentDirectory%\install-wif.ps1
    Md %DeploymentDirectory%\Common\Team\Foundation\Performance\Framework
    %DeploymentDirectory%\CloudCtuFakeACSInstall.cmd %DeploymentDirectory%\authcert.pfx
    ```

4. Modify the contents of the **CloudCtuFakeACSInstall.cmd** file so that the **Import** command has an empty string instead of **'password'**. The third line of the script should resemble the following line.

    ```powershell
    set MyStoreInstallCmd= .... $pfxcert.Import('%TestCertPath%', '', 'Exportable,PersistKeySet')....
    ```

5. In your solution files, double-click the **vsonline.testsettings** file to modify the test settings.
6. In the **Test Settings** dialog box, on the **General** tab, set the **Test run location** field to **Run tests using local computer or a test controller**.
7. On the **Deployment** tab, use the following settings:

    - Select the **Enable deployment** check box.
    - In the **Additional files and directories to deploy** field, make sure that the following files and directories are listed:

        - &lt;Solution Directory&gt;\\PerfSDKSample\\bin\\Debug\\
        - C:\\PerfSDK\\CloudEnvironment.Config
        - C:\\PerfSDK\\authcert.pfx
        - C:\\PerfSDK\\MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config
        - C:\\PerfSDK\\Visual Studio Online\\

        [![Additional files and directories to deploy field.](./media/PerfSDKOnlineTestSettings.PNG)](./media/PerfSDKOnlineTestSettings.PNG)

        > [!NOTE]
        > Your PerfSDK folder might differ.

8. On the **Setup and Cleanup Scripts** tab, select the **setup.cmd** file that is in the **Visual Studio Online** folder in the **PerfSDK** directory.
9. On the **Hosts** tab, select **Run tests in 64 bit process on 64 bit machine**.
10. To run the test, open the **SampleLoadTest.loadtest** file, and select **Run Load Test**.

    [![Run Load Test.](./media/perf103u.png)](./media/perf103u.png)

    When the test has finished running, you should see a summary that shows transaction results. Here is an example.

    [![Transaction results.](./media/perf103v.png)](./media/perf103v.png)

11. To view various indicators for the test controller and test scenario, you can switch to the **Graphs** view.

    [![Graphs view.](./media/perf103w.png)](./media/perf103w.png)

    > [!NOTE]
    > While tests are being run, information about your system isn't available in this view. To access this information, you must use Microsoft Dynamics Lifecycle Services (LCS) to monitor the CPU and memory usage of your AOS machine. Alternatively, you can set up perfmon directly on the AOS machine and set up the Microsoft Azure portal to monitor Microsoft SQL Server usage of Database Transaction Units (DTUs).

## Troubleshooting

### Zoom factor

This issue affects only single-user tests. 

#### Error example

```csharp
Initialization method <Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Unexpected error launching Internet Explorer. Browser zoom level was set to 200%. It should be set to 100% (NoSuchDriver).
```

#### Solution

In Internet Explorer, you can change the zoom factor to 100 percent by changing the following registry keys:

- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\ResetZoomOnStartup = 0
- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\ResetZoomOnStartup2 = 0
- Computer\\HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Internet Explorer\\Zoom\\Zoomfactor = 80000

Depending on the version of the local machine that is used, before you start the Remote Desktop Protocol (RDP) session, you might have to select **Change the size of text, apps and other items**. This field is available in **Display settings** in Windows. 

If those steps don't work, try to change the size of your remote desktop before you start the RDP session, so that the default zoom level in Internet Explorer is 100 percent.

### Certificate thumbprint errors

#### Error example

```csharp
Initialization method MS.Dynamics.Performance.Application.TaskRecorder.TestRecord1Base.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 
'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. --> 
MS.Dynamics.TestTools.CloudCommonTestUtilities.Exceptions.WebAuthenticationException: 
Failed finding the certificate for minting tokens by thumbprint: b4f01d2fc42718198852cd23957fc60a3e4bca2e
```

#### Solution

You might receive the error message for several reasons:

- The certificate thumbprint that you copied into the CloudEnvironment.Config and wif.config files includes invisible Unicode characters. To determine whether the thumbprint contains invisible Unicode characters, paste it into a Unicode code converter, and see whether extra characters appear in the **HTML/XML** field. For example, you can use the Unicode converter that is available at [https://r12a.github.io/apps/conversion/](https://r12a.github.io/apps/conversion/).

    ![Unicode code converter.](./media/sdk_unicode_code_converter.jpg)

- The certificate wasn't installed correctly on the AOS machine. To verify that the certificate can be found on the AOS machine, run the following Windows PowerShell script.

    ```powershell
    cd Cert:\LocalMachine\My
    Get-ChildItem | Where-Object { $_.Subject -like "CN=127.0.0.1" }
    ```

    If the thumbprint doesn't appear in the Windows PowerShell console after you run the script, the certificate can't be found. To fix the issue, copy and install the .cer file that you created earlier in this article to the AOS machine.

- If this issue occurs when you run load tests, the setup scripts might not have installed the corresponding .pfx file correctly. Verify that the password that is specified in the CloudCtuFakeACSInstall.cmd file matches the password that was set when the certificate was created.

    ![Password in the CloudCtuFakeACSInstall.cmd file.](./media/set_cloudctufakeacsinstall.jpg)

### No endpoint is listening

#### Error example

The tests process fails, and the following error message is shown.

```csharp
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.EndpointNotFoundException: There was no endpoint listening at <web address> that could accept the message. This is often caused by an incorrect address or SOAP action. 
```

#### Solution

This issue occurs when the host that is specified in the CloudEnvironment.Config file can't be accessed from the machine that is trying to run the tests or create users.

In the CloudEnvironment.Config file, review the values that are specified for the following keys:

- &lt;ExecutionConfigurations Key="HostName" Value="&lt;web address of host&gt;" /&gt;
- &lt;ExecutionConfigurations Key="SoapHostName" Value="&lt;web address of SOAP&gt;" /&gt;

The web addresses that are specified by these keys must be the environment that you're testing. In a web browser on your developer machine, make sure that you can open the web address that is specified for the **HostName** key.

### Users can't be enumerated

This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe.

#### Error example

```csharp
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Could not enumerate AX users ---> System.ServiceModel.FaultException'1[System.ComponentModel.Win32Exception]: Forbidden
```

#### Solution

Two scenarios can cause this error:

- The user who is specified as **SelfMintingAdminUser** in the CloudEnvironment.Config file must have the System Administrator role. This issue occurs when the System Administrator role isn't assigned to the user who is specified as **SelfMintingAdminUser**. To verify that you've specified the correct user, you can sign in to the endpoint and view the user's roles.

    ![Admin user.](./media/sdk_admin.png)

- An incorrect **NetworkDomain** value was specified for the user who is specified as **SelfMintingAdminUser** in the CloudEnvironment.Config file. You can find the correct value by running the following SQL query against the **AXDB** database of your on-premises deployment.

    ```sql
    select NETWORKDOMAIN, NETWORKALIAS from USERINFO where NETWORKALIAS='[AdminUserEmail]'
    ```

### At least one security token in the message could not be validated

This issue can occur when you run multiuser tests, or when you create users by using MS.Dynamics.Performance.CreateUsers.exe. It tends to occur when the AOS machine differs from the developer machine. 

#### Error example

```csharp
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.ServiceModel.Security.MessageSecurityException: An unsecured or incorrectly secured fault was received from the other party. See the inner FaultException for the fault code and detail. ---> System.ServiceModel.FaultException: At least one security token in the message could not be validated.
```

#### Solution

This issue occurs when the AOS endpoint can't validate the thumbprint of the certificate that you created. There are three possible causes:

- In the CloudEnvironment.Config file, either a value isn't specified for the **IsAdfs** key, or the value is set to **False**. Make sure that the value for the **IsAdfs** key is set to **True**.
- The certificate wasn't installed on the AOS machine. To fix the issue, copy the .cer file that you created earlier in this article to the AOS machine, and install the certificate.
- The thumbprint of the certificate wasn't added to the wif.config file on the AOS machine. To fix the issue, see step 8 in the [Run a single-user test by using the Performance SDK](#run-a-single-user-test-by-using-the-performance-sdk) section for information about how to add the certificate to the wif.config file. After you modify the wif.config file, be sure to restart the application through Service Fabric Explorer.

### MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config is missing from the deployment items

This issue usually occurs only when you run load tests.

#### Error example

```csharp
<Test class name>.TestSetup threw exception. System.InvalidOperationException: System.InvalidOperationException: Could not find endpoint element with name 'ClientCommunicationManager' and contract 'Microsoft.Dynamics.Client.InteractionService.Communication.Reliable.IReliableCommunicationManager' in the ServiceModel client configuration section. This might be because no configuration file was found for your application, or because no endpoint element matching this name could be found in the client element.. at System.ServiceModel.Description.ConfigLoader.LoadChannelBehaviors(ServiceEndpoint serviceEndpoint, String configurationName)
```

#### Solution

This issue occurs when the system can't find the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file when the load tests are run, because the file wasn't added as a deployment item. Verify that the MS.Dynamics.Test.Team.Foundation.WebClient.InteractionService.dll.config file is in the Out folder for the test run: 

&lt;solution path&gt;\\TestResults\\&lt;your test run&gt;\\Out

If the file is missing, add it to the deployment items in the test settings.

> [!IMPORTANT]
> There are two files that have very similar names. The name of one file ends in **\*.dll**, and the name of the other file ends in **\*.dll.config**. The **\*.dll.config** file must be in the deployment items in the test settings.

### CloudEnvironment.Config is missing from the deployment items

This issue usually occurs only when you run load tests.

#### Error example

```csharp
Initialization method <Test class name>.TestSetup threw exception. 
System.TypeInitializationException: System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> MS.Dynamics.TestTools.TestLogging.EvaluateException: Assert.Fail failed. DateTime="10/13/2017 14:42:55" "The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception.".
```

#### Solution

This issue occurs when the CloudEnvironment.Config file isn't present when the tests are run. The issue typically occurs when you run load tests and the CloudEnvironment.Config file wasn't added as a deployment item. Verify that the CloudEnvironment.Config file is in the Out folder for the test run:

&lt;solution path&gt;\\TestResults\\&lt;your test run&gt;\\Out

If the file is missing, add it to the deployment items in the test settings.

![Test settings.](./media/test-settings.png)

### InteractiveClientId wasn't specified in the settings

#### Error example

```Text
The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.SecretSettingsHelper' threw an exception. --->
Microsoft.CE.VaultSDK.SecretProviderException: InteractiveClientId was not specified in settings
```

#### Solution

This issue occurs when no value is specified for the **SelfSigningCertificateThumbprint** key in the CloudEnvironment.Config file. In the CloudEnvironment.Config file, find the following line, and paste in the thumbprint of the certificate that you created and installed.

```xml
<ExecutionConfigurations Key="SelfSigningCertificateThumbprint" Value="" />
```

### The remote host forcibly closed an existing connection

#### Error example

```csharp
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

```powershell
Set-ItemProperty HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false
if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319)) 
{
    Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false 
}
```

### The w3svc service wasn't found on the computer

This error only occurs when you run load tests by using Microsoft Visual Studio Online.

#### Error example
```Text
Test method MS.Dynamics.Performance.Application.GFM.PDLTrend.ProcureToPayTrend.ProcureToPaymentTrend threw exception: 
System.TypeInitializationException: The type initializer for 'MS.Dynamics.TestTools.CloudCommonTestUtilities.Authentication.UserManagement' threw an exception. ---> System.InvalidOperationException: Service w3svc was not found on computer '.'. ---> System.ComponentModel.Win32Exception: The specified service does not exist as an installed service
```

#### Solution

A hotfix is available that resolves this issue. The Microsoft Knowledge Base (KB) number is 4095640.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

