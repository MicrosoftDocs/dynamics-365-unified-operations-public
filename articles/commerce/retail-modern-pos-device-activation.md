---
# required metadata

title: Configure, install, and activate Modern POS (MPOS)
description: This article describes how to configure, download, and install Modern POS on various platforms. It then describes how to activate Modern POS through device activation.
author: jashanno
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.custom: 20501
ms.assetid: 1a8dba89-f81b-40d5-9e1e-dba7b335600d
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2016-02-28

---

# Configure, install, and activate Modern POS (MPOS)

[!include [banner](includes/banner.md)]

> [!WARNING]
> After Commerce Scale Unit (CSU) is updated to version 10.0.29 or later, the point of sale (Modern POS or Store Commerce) version must be 10.0.27 or later (shown in point of sale as version 9.27). The migration to .NET Core is the reason for this requirement.

This article describes how to configure, download, and install Modern point of sale (MPOS) on various platforms. This article is based on the legacy self-service installer. For more information about sealed self-service installers, see [Mass deployment of sealed Commerce self-service components](dev-itpro/Enhanced-Mass-Deployment.md). It then describes how to activate Modern POS through device activation.

> [!NOTE]
> There are two Modern POS installers: Modern POS and Modern POS with offline (this installer also installs the offline database).
> - Starting in Commerce version 10.0.11, altering customized files that are stored in the ClientBroker folder could cause issues when installing a newer release. These issues might include the inability to go offline or a newer installer failing to complete successfully. A workaround is to remove the files in the ClientBroker folder in the Modern POS directory before performing the installation using the newer installer.
> - Starting in Commerce version 10.0.15, customizations to files in the Client broker folder for Modern POS can cause an error when updating from a previous version. The known workaround is to delete all files from the Client broker folder prior to running the newer Modern POS installer. For automation, this can easily be scripted as a pre-step for the installer. All files in this folder must be deleted. When this error occurs, the newer installer will update the current installation correctly.

## Technology

The self-service process lets you download the appropriate version of the Modern POS installer and install it on the physical device that you want to use as the point of sale (POS) register. Device activation is the main onboarding step that ties the physical device to a register in Headquarters. Here are the main technical functions of this feature:

- Tie a physical device to a business entity (register).
- Provide enhanced security through Microsoft Azure Active Directory (Azure AD) and a device token/ID.
- Stop unauthorized remote use of Modern POS. (In other words, deactivate a device remotely.)
- Initialize settings for easy Modern POS functioning (number sequence, hardware profile, merchant information) as the first touchpoint of the POS.
- Comply with payment card industry (PCI) standards, and report on device information from Headquarters.

> [!NOTE]
> If you are installing Modern POS for use with an on-premises environment, Modern POS does not use Azure Active Directory credentials for device activation.

## Setup

Before you start the steps that are outlined in this article, follow these steps.

- Verify that you have credentials to sign in to Headquarters.
- Verify that you have administrative or root access to install Modern POS on a device.
- Verify that you can access the Commerce Scale Unit from the device.
- Verify that the environment contains the Commerce permission groups and jobs in the **Human resources** module. These permission groups and jobs should have been installed as part of the demo data.

## Download and install Modern POS

### Verify that the device is correctly configured

1. In Headquarters, go to **Retail and Commerce** &gt; **Channels** &gt; **Channel deployment**.
2. On the **Channel deployment** page, select the **Registers** tile.
3. On the **Registers** page, select a store register. The demo data thoroughly defines the Houston store and registers for self-service. To find the Houston registers, enter **Houston** in the filter at the top of the list of devices.
4. Select a register by selecting the register number in the **Register number** column. In the Houston store, register Houston-3 is well defined and is therefore useful as an example.
5. On the page for the register, under **General**, verify that the **Support offline** option is set to **No**. To use offline support, on the Action Pane, select **Edit**, and then set **Support offline** option to **Yes**.

    > [!NOTE]
    > When using Azure Active Directory (Azure AD) authentication, POS offline will not function, as online connectivity is always required.

### Download the Modern POS installer

1. On the **Welcome** page, use the menu in the upper left to go to **Retail and Commerce** &gt; **Channels** &gt; **Channel deployment**.
2. On the **Channel deployment** page, select the **Devices** tile.
3. Select a device.

    > [!NOTE]
    > - The Houston devices are well defined. Houston-3 is useful as an example for a Microsoft Windows desktop or tablet. Houston-21 is useful as an example for a Windows Phone.
    > - When you select a device, the **Download** button on the Action Pane becomes available.

4. Select **Download**, and then select **Configuration file**. Note the following:

    - Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then, while the device is still selected, select **Download** again.
    - The configuration file must be saved to the same location as the Modern POS installer. For security reasons, delete this file after installation is completed. If the configuration file is not the same file name as the installer executable, either the executable must be run using the command line to specify the configuration file or you need to rename the XML configuration file to have the same base name as the executable file name.

5. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)
6. Select **Download**, and then select **Retail Modern POS**. Note the following:

    - Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then, while the device is still selected, select **Download** again.
    - The installation package that you must use varies, depending on whether you require offline support, and whether the device that Modern POS will be installed on is a Windows tablet or a phone device (such as a Windows Phone, an Android device, or an iOS device). The correct package is automatically selected for download, based on the register settings and the application type that is set for the device. If the offline package is selected for a Windows tablet, but Microsoft SQL Server isn't already installed (or if it doesn't meet the requirements for the offline package), SQL Server is no longer downloaded. Install SQL Server (and associated prerequisite features, such as Full-text search) and attempt the installer again.

7. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)
8. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on your browser.)

### Before running the Modern POS installer

- Make sure that all [system requirements](../fin-ops-core/fin-ops/get-started/system-requirements.md) are met. If planning to use an offline database, it is recommended to first review the [Commerce Data Exchange implementation guidance](dev-itpro/implementation-considerations-cdx.md#commerce-data-exchange-implementation-guidance) section and the related best practices content it will reference.
- It is recommended to temporarily turn off antivirus applications. It has been noted that on aggressive antivirus solutions, the installation may stall due to the antivirus solution checking active files while in use.
- The installer will sideload a modern application. Therefore, a Group Policy entry must be set to allow for sideloaded applications. The installer will change the associated registry key as follows to allow for this installation:

    - **Path:** HKLM:SoftwarePoliciesMicrosoftWindowsAppx
    - **Property:** AllowAllTrustedApps
    - **Value:** 1

- If offline is used (an offline database created), then a default SQL Server instance must exist. If SQL Server instances exist, but none are set as the default, then the installer will fail to install the offline database.

> [!NOTE]
> When using Azure Active Directory authentication, POS offline will not function as online connectivity is always required.

If you are installing Modern POS for use with an on-premises environment, you must start the installer from a command line as follows:

```Console
ModernPosSetupOffline.exe -UseAdfsAuthentication
```

> [!NOTE]
> The **UseAdfsAuthentication** parameter is only available for non-sealed MPOS. Customers that need to use Active Directory Federation Services (ADFS) authentication for an on-premises deployment using the sealed extensibility model should instead use the [Store Commerce app](dev-itpro/store-commerce.md).

### Run the Modern POS installer on a Windows computer

The Modern POS installer first extracts the associated files and then starts the installation.

1. The installer validates that all prerequisites are met. Note the following:

    - If a system restart is required, the installer informs you about this requirement, but the installation can typically continue.
    - A sideloaded installation of Modern POS requires a Group Policy change. The installer informs you if this change is required and then makes the change automatically.

2. If you selected offline support, but a valid version of SQL Server isn't found, the installer will fail during the prerequisites check. If a prerequisite fails during this step, first retry the installer. If the installer continues to fail, see the [Troubleshooting](#troubleshooting) section of this article.
3. The installer installs Modern POS.
4. On the page that states that installation was successful, select **Close** to exit the installer.

You can now start the program.

> [!NOTE]
> This installation occurs only for the administrator user who ran the installer. For all other users, a desktop icon to install Modern POS is created. Every time that a user signs in, the user must double-click this icon. The program will then be installed or updated, as required. If a user doesn't use the desktop icon after an update, the POS client will request that the user run from the desktop icon instead to update correctly prior to running.

### Run the installer on any other device (Windows Phone, Google Android device, or Apple iOS device)

1. If the application wasn't downloaded directly to the device, transfer the downloaded app file and the associated configuration file to the same folder on the device. Depending on the type of device, the app file will be an APPX, APK, or IPA file.

    Note that this step can be done in various ways. For example, the files can be accessed through a shared folder, transferred via USB cable, or securely mailed to the user's device.

2. Use a file explorer on the device to browse to the app directory.
3. Tap the app to begin application installation. (If the configuration file was saved to the same location, the Commerce Scale Unit URL will be automatically entered when you start the application and begin device activation.)

    Note that some devices require that you double-tap the file to begin application installation. Some devices might not notify you that an application has been installed. On those devices, we recommend that you look at the application list to verify that the application was correctly installed.

4. When the installation is completed, you should be able to start the application from the application list on the device. For example, after you install the application on a Windows Phone, you can start it from the home screen tiles list.

You can now start the program.

## Create a worker

For this article, we have already created workers and assigned them to the Houston address book in the demo data that is provided. Therefore, this article will use pre-generated data.

### Create a worker

1. Go to **Retail and Commerce** &gt; **Employees** &gt; **Workers**.
2. On the Action Pane, select **New** to create a new employee.
3. Enter the first and last name. For example, enter **John** as the first name and **Smith** as the last name.
4. Verify that the **Legal entity** field is set to **USRT**, the **Worker type** field is set to **Employee**, and the **Employment start date** field is set to the current date at 12 AM, so that the worker's employment starts immediately.
5. Select the **Assign a position** check box. Select position number **000544**, which is the Store manager position.
6. Set the **Personnel action type** field to **Hire Action** to hire a new employee immediately.
7. Select **Continue**.
8. On the Action Pane, select **Complete** to finish creating the new worker.
9. Return to the worker list. Search for the newly created worker (for example, John Smith). Select the worker's name to see the details of the new worker.
10. On the Action Pane, select **Edit**.
11. Verify that the language for the worker is **en-us**.
12. Under **Worker summary**, in the **Address books** field, select the **Houston** store.
13. On the **Commerce** tab, you can reset the POS password. For this tutorial, reset the password to **123**.
14. On the **Commerce** tab, under **Screen layout**, assign a screen layout. For example, select **F2MP16:9M** (**Fabrikam MPOS Manager (16:9)**).
15. On the Action Pane, select **Save**.
16. Go to **Retail and Commerce** &gt; **Periodic** &gt; **Distribution schedule**.
17. Select the **1060 – Staff** job, and then, on the Action Pane, select **Run now** to sync the worker data to the channel database.
18. After the new worker has been created and synced to stores, the worker can sign in to any POS device that is used in the HOUSTON store that the worker is assigned to, and the worker can perform transactions on that device. However, the device must be activated first. The following section explains how to activate a device for a new worker.

### Map an Azure AD account to a worker who has POS permissions for device activation

You must complete this procedure before you activate Modern POS for a new worker.

1. In Commerce, from the **Worker** page, open the **Worker details** page for the worker that you created in the previous procedure.
2. On the Action Pane, select **Edit**.
3. On the **Commerce** tab, select the **POS permissions** link. Under **POS permission group**, verify that the value is **Manager**.
4. When you've finished, return to the **Worker details** page for the new worker.

    To return to the **Worker details** page, select the **Close** button (**X**) on the right side of the Action Pane.

5. On the Action Pane, select **Commerce**, and then select **Associate existing identity**.
6. In the dialog box that appears, select the Azure AD account that is named **admin AX Admin**. (If an alternative administrator Azure AD account has been created, select that account instead.)
7. Select **OK**. In the demo data, the Azure AD account that is associated with the administrator account in Headquarters is your administrator Azure AD account.
8. On the Action Pane, select **Save**, and then refresh the page. The **External identity** section should now be updated with the new information.

    Note that the **External identifier** field will remain empty. This behavior is expected. Therefore, you can ignore it.

This procedure should be completed before you activate Retail Cloud POS or Modern POS. For more information, see [Manage activation accounts and validate devices](set-up-activation-accounts-validate-devices-hq.md).

### Run the Validate Devices for Activation check

1. In Headquarters, open the **Device** page (**Retail and Commerce** &gt; **Setup POS** &gt; **Devices**).
2. Select the device to validate for device activation, and then select **Validate Devices for Activation**. For example, select device **HOUSTON-3**.
3. In the dialog box that appears, select the worker to validate the device for (that is, the worker that you mapped to the Azure AD account in the previous procedure). For example, select worker **000160**.
4. Select **OK**, and make sure that you receive the following message: "Pre-Activation validation completed for Device HOUSTON-3 and Staff 000160. Validation: Passed"

## Activate a device

> [!NOTE]
> It is possible for the Safari browser to show an error during device activation of a Cloud POS device due to an Azure Active Directory token being unattainable. You can resolve this issue by utilizing the [Microsoft Enterprise SSO plug-in for Apple devices](/azure/active-directory/develop/apple-sso-plugin).

1. Start Modern POS on your computer. Read the instructions on the **Before you start** page, and make sure that they are completed. Then select **Next**.
2. Select **Activate**. You're redirected to the Azure AD sign-in page.
3. Enter the Azure AD account that you mapped earlier, such as `admin@<MyCompany>.onmicrosoft.com`, and the password.
4. When activation is completed, select **Get Started**.
5. Sign in to Modern POS by using worker account **000160** and the password **123**.

The device should now be activated and ready to use.

## Update the Modern POS application

> [!NOTE]
> To learn more about deployable packages, see [Apply a deployable package](../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md).

1. After a Modern POS application is uploaded into the environment, the version of the package can be selected on the device. The package listings should include the new uploaded application.
2. To update the Modern POS application, follow the steps in the [Download and install Modern POS](#download-and-install-modern-pos) section. To do an in-place update, just run the newer version of the self-service installer. Uninstallation isn't required or recommended. Device activation status will be maintained after the update.
3. The installer will use the currently installed configuration settings. If the configuration file has changed, because of various configuration changes in Commerce, an update won't change the Modern POS application settings.

> [!WARNING]
> An update of a Modern POS offline database isn't required for the installer to succeed. An offline database might maintain an older version and might not be updated if any error occurs. When customizations are updated or the update failure isn't detected, an offline database might not work correctly. In these scenarios, it's important that you fix the blocking issue and update the Modern POS again, so that the offline database is correctly updated.

## Troubleshooting

### Troubleshoot installation

- When Modern POS is in use and the POS switches offline during a transaction, the following error displays, "Cart version has changed".

    **Solution:** Select to close and continue working. This is a known issue that is currently being investigated. This error does not produce any issues.

- Your browser blocks the download pop-up that is generated.

    **Solution:** Select either **Allow once** or **Options for this site** &gt; **Always allow** (or the equivalent commands in the browser that you're using). Then, while the correct register is still selected, select **Download** again.

- The installation package that you must use depends on whether you require offline support. The correct package is automatically selected for download. For the offline package, SQL Server must be installed and must meet the requirements for the offline package.

    **Solution:** If SQL Server isn't already installed (or if it doesn't meet the requirements), installation of a supported version is required. This installation might require an extended period of time and must include the Full-text search feature.

- The installation occurs only for the administrator user who ran the installer, but not for any other users.

    **Solution:** The installer generates a desktop icon that is used to install, upgrade, and run Modern POS. This icon is generated for every user on the computer. When a user who must install Modern POS double-clicks this icon, the program is installed. The user can then start to use Modern POS.

- SQL Server isn't successfully downloaded and installed through the self-service Modern POS installer.

    - **Solution 1:** The installer no longer downloads SQL Server automatically. Download and install a supported version of SQL Server with Full-text search to meet prerequisite installation.

- The installation of Modern POS fails, because the registration of performance (perf) counters failed.

    **Solution:** Follow these steps to fix this issue:

    1. Open a **Command Prompt** window as an administrator.
    2. Enter the following command.

        ```Console
        lodctr /s:"perf_backup.txt"
        ```

    3. Enter the following command.

        ```Console
        lodctr /R
        ```

    4. If the system doesn't rebuild the performance counter settings from the system backup, rerun the **lodctr /R** command.
    5. Rerun the Modern POS installer.

- If you're using a downloaded virtual hard disk (VHD) instead of a cloud-hosted environment, the downloader might fail.

    - **Solution 1:** In a downloaded VHD, the Azure Storage Emulator must be installed and must be running correctly. Otherwise, the self-service packages can't be downloaded correctly.
    - **Solution 2:** A failure might have occurred during the process of integrating the VHD into Microsoft Hyper-V. You must manually edit permissions before the packages can be downloaded correctly. Follow these steps:

        1. In File Explorer, browse to **C:\\Microsoft Dynamics 365\\70\\Retail Server**.
        2. Right-click the **SelfServicePackages** folder, and then select **Properties**.
        3. On the **Security** tab, select **Edit**.
        4. In the **Permissions for SelfServiceDeployment** dialog box, select **Add**.
        5. In the **Select Users, Computers, Service Accounts, or Groups** dialog box, select **Locations**.
        6. In the **Locations** dialog box, select the first entry in the list (the local computer), and then select **OK**.
        7. In the **Select Users, Computers, Service Accounts, or Groups** dialog box, enter the name **IIS\_IUSRS**, and then select **Check names**. The object name should be changed to **IIS\_IUSRS**. Select **OK**.
        8. In the **Permissions for SelfServiceDeployment** dialog box, select the new **IIS\_ISURS** user. Under **Permissions for IIS\_IUSRS**, select **Allow** for the **Full control** permission. Select **OK**.
        9. In the **Open permission** dialog box, select **OK**.

- The latest iOS version does not support your self-signed certificate.

    - **Solution 1:** Utilize a domain and generate a proper domain-based certificate.
    - **Solution 2:** Download the open source OpenSSL library and perform the following after completing installation:

        1. Using PowerShell, create a private key for the root Certificate Authority (CA) using a command such as **$ openssl genrsa -des3 -out rootCA.key 2048**.
        2. You will be prompted for a password, which must be remembered for later usage.
        3. Next, generate the root certificate using a command such as **$ openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 1024 -out rootCA.pem**. There will be a prompt for the password entered previously and some basic certificate information.

            > [!NOTE]
            > The number of days the certificate is valid for can be altered. In the above example this is 1024 days.

        4. Create a new **info.ext** file and enter the following details:

            - keyUsage = keyEncipherment, dataEncipherment
            - extendedKeyUsage = 1.3.6.1.5.5.7.3.1
            - subjectAltName = @alt_names
            - [alt_names]
            - DNS.1 = &lt;FULLY QUALIFIED DOMAIN NAME OF HOST COMPUTER&gt;

        5. Generate the signing request and private key using a command such as **openssl req -new -nodes -out server.csr -newkey rsa:2048 -keyout server.key**.
        6. Issue the certificate using the previously generated root certificate using a command such as **$ openssl x509 -req -in server.csr -CA rootCA.pem -CAkey rootCA.key -CAcreateserial -out server.crt -days 500 -sha256 -extfile info.ext**. There will be another prompt for the root key password and you will need to specify the number of days that the certificate is valid (500 days in this example).
        7. Generate the IIS certificate using a command such as **$ openssl pkcs12 -inkey server.key -in server.crt -export -out server.pfx**. This command will request a new password, which will be used later when the certificate is imported.
        8. Open **Certmgr.msc** and go to **Trusted Root Certificate Authorities**. Use the **Import** action to import the previously generated **rootCA.pem** root CA file.
        9. In the same window, go to **Personal** and use the **Import** action to import the previously generated **server.pfx**.
        10. Next, open the **IIS Manager**, select the **RetailHardwareStationWebSite** and select **Edit Bindings** from the right-most menu.
        11. In the new window, select the HTTPS site binding, and then select **Edit**. In the final screen, select the newly installed certificate and select **OK**.
        12. Verify the certificate is correctly being used. In a web browser, go to `https://<hostname>/HardwareStation/ping`.
        13. Install the certificate on the iOS device:

            - Copy the **rootCA.pem** file and rename the copy to **rootCA.crt**.
            - Using OneDrive or another file hosting location, upload the **rootCA.crt** and **server.crt** so that they can be downloaded onto the iOS device.

        14. On the iOS device, go to **Settings &gt; General &gt; Profiles** and select the downloaded profile for the **rootCA.crt**. Select **Install**.
        15. Validate that the profile status updates to **Verified**. Repeat the same process for the **server.crt** file.
        16. Go to **Settings &gt; General &gt; About &gt; Certificate Trust Settings** and enable the installed root certificate.
        17. On the iOS device, use the hardware station ping URL specified previously to verify that the certificate is trusted.
        18. Open the POS application in **Non-drawer mode** and pair to the hardware station as typically performed.

### Troubleshoot device activation for Modern POS

- The Microsoft account (Azure AD) sign-in page doesn't open.

    **Solution:** The Azure AD endpoint might be unreachable. Wait a few minutes, and then try again.

- After you enter the Azure AD account, you receive an error message that states that the user isn't authorized.

    **Solution:** Verify that the Azure AD user is mapped to a worker who has POS permission to activate devices. The **Manage device** permission for the worker should be set to **Yes**.

- When using Modern POS on an Android device, the device activation and Azure AD-based POS sign-in open the Azure AD sign-in page in a standalone browser instance, but the sign-in process doesn't proceed.
  
    **Solution:** Check whether your Commerce Scale Unit is version 10.0.22 or later, and that Modern POS is version 10.0.21 or earlier. If so, you must rebuild Modern POS from the latest Commerce sample repository (version 10.0.22 or later) and then update the Modern POS application on the Android device.

- Device activation isn't completed. It fails during one of the steps.

    **Solution:** Follow this checklist to verify that all data is correct:

    - Complete the Validate Devices for Activation check in Headquarters, and make sure that the device passes validation.
    - On the client computer where you're activating the device, access the Commerce Scale Unit URL health check, and make sure that the health check is passed. Use the following format for the URL: `https://MyCompanyNameret.axcloud.dynamics.com/commerce/healthcheck?testname=ping`
    - The worker must be mapped to an Azure AD account (under **External identity**).
    - The Azure AD account that is mapped must belong to the same tenant.
    - To map the worker to the Azure AD account, sign in to Headquarters by using the Admin account for Microsoft Dynamics Lifecycle Services.
    - Make sure that the worker is set up as a Commerce user in the Manager role. (This item is checked by validation.)
    - Make sure that the channel is published. (This item is checked by validation.)
    - Make sure that the channel database has the synced data from Headquarters, and that download jobs are running.
    - Set up the hardware profile under **Registers**. (This item is checked by validation.)
    - Make sure that the register and store have a screen layout. (This item is checked by validation.)
    - Make sure that a primary address is set up for the legal entity.
    - Make sure that the language is set up for the Commerce Data Exchange: Real-time Service user profile (JBB in the demo data).
    - Make sure that the Real-time Service profile has the correct access.
    - Make sure that the electronic funds transfer (EFT) configuration value is present.

### Troubleshoot Modern POS connectivity

On a single-computer system, such as a developer topology or a demo environment, or when Commerce Scale Unit and Modern POS are installed on the same computer, Modern POS can't complete device activation.

**Solution:** This issue occurs because Modern POS can't make network calls to the same computer (that is, calls to itself). While this should never be a scenario in a production setting, the issue can be mitigated by enabling an AppContainer loopback exception so that communications can occur to the same computer. Various applications will help enable this loopback for Modern POS. For more information about loopback, see [How to enable loopback and troubleshoot network isolation](/previous-versions/windows/apps/hh780593(v=win.10)). It is important to understand that a loopback can be a security risk, so it is not recommended that you use a loopback unless absolutely necessary.

## Additional resources

[Install the POS layout designer](install-pos-layout-designer.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
