---
# required metadata

title: Configure, install, and activate Modern POS (MPOS)
description: This topic describes how to configure, download, and install Modern POS on various platforms. It then describes how to activate Modern POS through device activation.
author: jashanno
manager: AnnBe
ms.date: 01/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailChannelManagementWorkspace, RetailDevice, RetailTerminalTable
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 20501
ms.assetid: 1a8dba89-f81b-40d5-9e1e-dba7b335600d
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Configure, install, and activate Modern POS (MPOS)

[!include [banner](includes/banner.md)]

This topic describes how to configure, download, and install Modern POS on various platforms. It then describes how to activate Modern POS through device activation.

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

Before you start the steps that are outlined in this topic, follow these steps.

- Verify that you have credentials to sign in to Headquarters.
- Verify that you have administrative or root access to install Modern POS on a device.
- Verify that you can access the Commerce Scale Unit from the device.
- Verify that the environment contains the Commerce permission groups and jobs in the **Human resources** module. These permission groups and jobs should have been installed as part of the demo data.

## Download and install Modern POS

### Verify that the device is correctly configured

1. In Headquarters, go to **Retail and Commerce** &gt; **Channels** &gt; **Channel deployment**.
2. On the **Channel deployment** page, select the **Registers** tile.
3. On the **Registers** page, select a store register.

    > [!NOTE]
    > The demo data thoroughly defines the Houston store and registers for self-service. To find the Houston registers, enter **Houston** in the filter at the top of the list of devices.

4. Select a register by selecting the register number in the **Register number** column.

    > [!NOTE]
    > In the Houston store, register Houston-3 is well defined and is therefore useful as an example.

5. On the page for the register, under **General**, verify that the **Support offline** option is set to **No**.

    > [!NOTE]
    > To use offline support, on the Action Pane, select **Edit**, and then set **Support offline** option to **Yes**.

### Download the Modern POS installer

1. On the **Welcome** page, use the menu in the upper left to go to **Retail and Commerce** &gt; **Channels** &gt; **Channel deployment**.
2. On the **Channel deployment** page, select the **Devices** tile.
3. Select a device.

    > [!NOTE]
    > - The Houston devices are well defined. Houston-3 is useful as an example for a Microsoft Windows desktop or tablet. Houston-21 is useful as an example for a Windows Phone.
    > - When you select a device, the **Download** button on the Action Pane becomes available.

4. Select **Download**, and then select **Configuration file**.

    > [!NOTE]
    > - Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then, while the device is still selected, select **Download** again.
    > - The configuration file must be saved to the same location as the Modern POS installer. For security reasons, delete this file after installation is completed.

5. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)
6. Select **Download**, and then select **Retail Modern POS**.

    > [!NOTE]
    > - Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then, while the device is still selected, select **Download** again.
    > - The installation package that you must use varies, depending on whether you require offline support, and whether the device that Modern POS will be installed on is a Windows tablet or a phone device (such as a Windows Phone, an Android device, or an iOS device). The correct package is automatically selected for download, based on the register settings and the application type that is set for the device. If the offline package is selected for a Windows tablet, but Microsoft SQL Server isn't already installed (or if it doesn't meet the requirements for the offline package), SQL Server is downloaded and installed silently.

7. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)
8. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on your browser.)

### Run the installer on a Windows computer

> [!NOTE]
> - Before you run the Modern POS installer, make sure that all [system requirements](../fin-and-ops/get-started/system-requirements.md) are met.
> - The installer will sideload a modern application. Therefore, a Group Policy entry must be set to allow for sideloaded applications. The installer will change the associated registry key as follows to allow for this installation:
>
>    - **Path:** HKLM:SoftwarePoliciesMicrosoftWindowsAppx
>    - **Property:** AllowAllTrustedApps
>    - **Value:** 1

If you are installing Modern POS for use with an on-premises environment, you must start the installer from a command line as follows:

    ModernPosSetupOffline.exe -UseAdfsAuthentication

The Modern POS installer first extracts the associated files and then starts the installation.

1. The installer validates that all prerequisites are met.

    > [!NOTE]
    > - If a system restart is required, the installer informs you about this requirement, but the installation can typically continue.
    > - A sideloaded installation of Modern POS requires a Group Policy change. The installer informs you if this change is required and then makes the change automatically.

2. If you selected offline support, but a valid version of SQL Server isn't found, the installer downloads and installs Microsoft SQL Server 2014 Express with Service Pack 2 (SP2). To meet the prerequisites, SQL Server must have Full-text search installed. Additionally, a minimum of SP2 must be installed for Microsoft SQL Server 2014, or a minimum of Service Pack 3 (SP3) must be installed for Microsoft SQL Server 2012.

    > [!NOTE]
    > - The installer tries to download the correct language. However, if you require a specific language, we highly recommend that you manually install SQL Server. If the installer can't correctly determine the language, it installs the English version of SQL Server 2014 Express with SP2 by default. Typically, after the SQL installation is completed, the system requires a restart before the installation of Modern POS can continue.
    > - This process might require a long time, depending on the speed of the computer and the Internet connection. If a prerequisite fails during this step, first retry the installer. If the installer continues to fail, see the [Troubleshooting](#troubleshooting) section of this topic.

3. The installer installs Modern POS.
4. On the page that states that installation was successful, select **Close** to exit the installer.

You can now start the program.

> [!NOTE]
> This installation occurs only for the administrator user who ran the installer. For all other users, a desktop icon to install Modern POS is created. Every time that a user signs in, he or she must double-click this icon. The program will then be installed or updated, as required. If a user doesn't use the desktop icon after an update, the POS client will request that the user run from the desktop icon instead to update correctly prior to running.

### Run the installer on any other device (Windows Phone, Google Android device, or Apple iOS device)

1. If the application wasn't downloaded directly to the device, transfer the downloaded app file and the associated configuration file to the same folder on the device. Depending on the type of device, the app file will be an APPX, APK, or IPA file.

    > [!NOTE]
    > This step can be done in various ways. For example, the files can be accessed through a shared folder, transferred via USB cable, or securely mailed to the user's device.

2. Use a file explorer on the device to browse to the app directory.
3. Tap the app to begin application installation. (If the configuration file was saved to the same location, the Commerce Scale Unit URL will be automatically entered when you start the application and begin device activation.)

    > [!NOTE]
    > Some devices require that you double-tap the file to begin application installation. Some devices might not notify you that an application has been installed. On those devices, we recommend that you look at the application list to verify that the application was correctly installed.

4. When the installation is completed, you should be able to start the application from the application list on the device. For example, after you install the application on a Windows Phone, you can start it from the home screen tiles list.

You can now start the program.

## Create a worker

For this topic, we have already created workers and assigned them to the Houston address book in the demo data that is provided. Therefore, this topic will use pre-generated data.

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
18. After the new worker has been created and synced to stores, worker John Smith can sign in to any POS device that is used in the HOUSTON store that he is assigned to, and he can perform transactions on that device. However, the device must be activated first. The following section explains how to activate a device for a new worker.

### Map an Azure AD account to a worker who has POS permissions for device activation

You must complete this procedure before you activate Modern POS for a new worker.

1. In Commerce, from the **Worker** page, open the **Worker details** page for the worker that you created in the previous procedure.
2. On the Action Pane, select **Edit**.
3. On the **Commerce** tab, select the **POS permissions** link. Under **POS permission group**, verify that the value is **Manager**.
4. When you've finished, return to the **Worker details** page for the new worker.

    > [!NOTE]
    > To return to the **Worker details** page, select the **Close** button (**X**) on the right side of the Action Pane.

5. On the Action Pane, select **Commerce**, and then select **Associate existing identity**.
6. In the dialog box that appears, select the Azure AD account that is named **admin AX Admin**. (If an alternative administrator Azure AD account has been created, select that account instead.)
7. Select **OK**. In the demo data, the Azure AD account that is associated with the administrator account in Headquarters is your administrator Azure AD account.
8. On the Action Pane, select **Save**, and then refresh the page. The **External identity** section should be now updated with the new information.

    > [!NOTE]
    > The **External identifier** field will remain empty. This behavior is expected. Therefore, you can ignore it.

This procedure should be completed before you activate Retail Cloud POS or Modern POS. For more information, see [Manage Retail activation accounts and validate devices](set-up-activation-accounts-validate-devices-hq.md).

### Run the Validate Devices for Activation check

1. In Headquarters, open the **Device** page (**Retail and Commerce** &gt; **Setup POS** &gt; **Devices**).
2. Select the device to validate for device activation, and then select **Validate Devices for Activation**. For example, select device **HOUSTON-3**.
3. In the dialog box that appears, select the worker to validate the device for (that is, the worker that you mapped to the Azure AD account in the previous procedure). For example, select worker **000160**.
4. Select **OK**, and make sure that you receive the following message: "Pre-Activation validation completed for Device HOUSTON-3 and Staff 000160. Validation: Passed"

## Activate a device

1. Start Modern POS on your computer. Read the instructions on the **Before you start** page, and make sure that they are completed. Then select **Next**.
2. Select **Activate**. You're redirected to the Azure AD sign-in page.
3. Enter the Azure AD account that you mapped earlier, such as `admin@<MyCompany>.onmicrosoft.com`, and the password.
4. When activation is completed, select **Get Started**.
5. Sign in to Modern POS by using worker account **000160** and the password **123**.

The device should now be activated and ready to use.

## Update the Modern POS application

> [!NOTE]
> To learn more about deployable packages, see the article [Apply a deployable package](../dev-itpro/deployment/apply-deployable-package-system.md).

1. After a Modern POS application is uploaded into the environment, the version of the package can be selected on the device. The package listings should include the new uploaded application.
2. To update the Modern POS application, follow the steps in the [Download and install Modern POS](#download-and-install-retail-modern-pos) section. To do an in-place update, just run the newer version of the self-service installer. Uninstallation isn't required or recommended. Device activation status will be maintained after the update.
3. The installer will use the currently installed configuration settings. If the configuration file has changed, because of various configuration changes in Commerce, an update won't change the Modern POS application settings.

## Troubleshooting

### Troubleshoot installation

- Your browser blocks the download pop-up that is generated.

    **Solution:** Select either **Allow once** or **Options for this site** &gt; **Always allow** (or the equivalent commands in the browser that you're using). Then, while the correct register is still selected, select **Download** again.

- The installation package that you must use depends on whether you require offline support. The correct package is automatically selected for download. For the offline package, SQL Server must be installed and must meet the requirements for the offline package.

    **Solution:** No action is required. If SQL Server isn't already installed (or if it doesn't meet the requirements), it's downloaded and installed. The installer gives generic information about the download and installation of SQL Server Express 2014. This installation might require a long time.

- The installation occurs only for the administrator user who ran the installer, but not for any other users.

    **Solution:** The installer generates a desktop icon that is used to install, upgrade, and run Modern POS. This icon is generated for every user on the computer. When a user who must install Modern POS double-clicks this icon, the program is installed. The user can then start to use Modern POS.

- SQL Server isn't successfully downloaded and installed through the self-service Modern POS installer.

    - **Solution 1:** A list of reasons shows the prerequisites that failed. If the list includes **SMO** or **SQL Management Objects**, first try to run the installer again. SQL Server Management Objects (SMO) are installed during SQL Server installation. Therefore, it's possible that the operating system didn't pick up the registration of the executable program that you used. When you run the installer a second time, the prerequisites are retested, and the prerequisite check should correctly verify the required executable program. If the installer continues to fail, restart the system to fully complete the registration of SQL Server, and then rerun the installer.
    - **Solution 2:** Manually download and install SQL Server (Microsoft SQL Server Express or another version) by using Advanced Tools. During installation, select **Full-text search** as an additional feature.

- The installation of Modern POS fails, because the registration of performance (perf) counters failed.

    **Solution:** Follow these steps to fix this issue:

    1. Open a **Command Prompt** window as an administrator.
    2. Enter the following command.

        ```
        lodctr /s:"perf_backup.txt"
        ```

    3. Enter the following command.

        ```
        lodctr /R
        ```

    4. If the system doesn't rebuild the performance counter settings from the system backup, rerun the **lodctr /R** command.
    5. Rerun the Modern POS installer.

- If you're using a downloaded virtual hard disk (VHD) instead of a cloud-hosted environment, the downloader might fail.

    - **Solution 1:** In a downloaded VHD, the Azure storage emulator must be installed and must be running correctly. Otherwise, the self-service packages can't be downloaded correctly.
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

### Troubleshoot device activation for Modern POS

- The Microsoft account (Azure AD) sign-in page doesn't open.

    **Solution:** The Azure AD endpoint might be unreachable. Wait a few minutes, and then try again.

- After you enter the Azure AD account, you receive an error message that states that the user isn't authorized.

    **Solution:** Verify that the Azure AD user is mapped to a worker who has POS permission to activate devices. The **Manage device** permission for the worker should be set to **Yes**.

- Device activation isn't completed. It fails during one of the steps.

    **Solution:** Follow this checklist to verify that all data is correct:

    - Complete the Validate Devices for Activation check in Headquarters, and make sure that the device passes validation.
    - On the client computer where you're activating the device, access the Commerce Scale Unit URL health check, and make sure that the health check is passed. Use the following format for the URL: `https://MyCompanyNameret.axcloud.dynamics.com/commerce/healthcheck?testname=ping`
    - The worker must be mapped to an Azure AD account (under **External identity**).
    - The Azure AD account that is mapped must belong to the same tenant.
    - To map the worker to the Azure AD account, sign in to Headquarters by using the Admin account for Microsoft Dynamics Lifecycle Services (LCS).
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

**Solution:** This issue occurs because Modern POS can't make network calls to the same computer (that is, calls to itself). To mitigate this issue, you must enable an AppContainer loopback exception so that communications can occur to the same computer. Various applications will help enabling this loopback for Modern POS. For more information about loopback, see [How to enable loopback and troubleshoot network isolation](https://msdn.microsoft.com/library/windows/apps/hh780593.aspx).

## Additional resources

[Install the Retail point of sale (POS) layout designer](install-pos-layout-designer.md)
