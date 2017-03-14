---
# required metadata

title: Access Dynamics 365 for Operations instances
description: This topic describes how to access development instances of Microsoft Dynamics 365 for Operations, configure on-premises development VMs, and find important configurations settings for developers and administrators.
author: RobinARH
manager: AnnBe
ms.date: 2015-10-16 23 - 42 - 46
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 10031
ms.assetid: 4be8b7a1-9632-4368-af41-6811cd100a37
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Access Dynamics 365 for Operations instances

This topic describes how to access development instances of Microsoft Dynamics 365 for Operations, configure on-premises development VMs, and find important configurations settings for developers and administrators.

Definitions
-----------

| Term      | Definition                                                                                                                                                                                                                                       |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| End user  | A user who accesses Microsoft Dynamics 365 for Operations through the web client. The end user must have Microsoft Azure Active Directory (Azure AD) credentials to access an instance and must be provisioned/added as a user of that instance. |
| Developer | A user who will develop code through the Microsoft Visual Studio environment. A developer requires Remote Desktop access to development environment (VM). The developer account must be an administrator on the VM.                              |

### Environments

Dynamics 365 for Operations is deployed in two modes:

-   A cloud environment that is provisioned through Microsoft Dynamics Lifecycle Services (LCS), and that supports various topologies (developer, demo, and high availability)
-   A local (on-premises) development virtual machine (VM) that is downloaded from LCS

## Cloud environment that is provisioned through LCS
When a cloud environment is provisioned through LCS, the following events occur:

-   The user who requests the cloud environment is provisioned as the administrator in that environment.
-   A user who requests access through LCS will be able to access the cloud environment through Remote Desktop.

### Accessing an instance through a URL

The system can be accessed by end users. The administrator can add users to this system by using the **Users** page in the instance. Note that these additional users don't have to be users in LCS. You obtain the base URL for the cloud environment from your LCS project site.

1.  Go to your LCS project page.
2.  In the **Environments** section, click the deployed environment.
3.  When the environment page opens, you can access the application by clicking **Login** &gt; **Log on to Dynamics 365 for Operations** in the upper-right corner. ****
4.  Use valid end user credentials to sign in to the application. If the current LCS user is the user who originally deployed the environment, that user is probably a valid end user and the administrator of the application.
5.  In your browser, make a note of the Dynamics 365 for Operations base URL after you sign in. For example, the base URL might be **https://dynamicsAx7aosContoso.cloud.dynamics.com**.

### Accessing the cloud instance through Remote Desktop

Some cloud environments can be accessed both as an end user and as a developer. The developer gets access to the system through Remote Desktop credentials. The Remote Desktop credentials are obtained from the environment page on the LCS project site (see the illustration earlier in this topic).

1.  Click the VM name.
2.  Use the local administrator user name and password that are shown to connect to the cloud VM through Remote Desktop. You can reveal the password by clicking the eye icon.

After you sign in to the environment through Remote Desktop, if you want to access the local application from the browser, use the same base URL that you use to access the application from a remote computer. The previous section explains how to obtain this base URL from LCS.

## VM that is running onpremises
An environment virtual hard disk (VHD) is made available for download from LCS, so that it can be set up on a local machine. This system is intended to be accessed by a developer.

1.  On the main page for your LCS project, in the **Environments** section, click the plus sign (**+**), and then click **Locally**. You're taken to the Connect site.
2.  Go to the **Downloads** page to download the latest VHD.
3.  In Microsoft Hyper-V Manager, create a local VM from the VHD that you downloaded. It's a good idea to give your VM the recommended 16 gigabytes (GB) of memory and two virtual processors. Don't use dynamic memory allocation.

### Retail configuration

A newer downloadable VHD is also provided, in **Preview** state, to support Retail point-of-sale (POS) customization scenarios. This VHD is based on Microsoft Windows Server 2016 and lets you test your customized Retail POS app in an emulator on the VM. Except for this difference, both VHDs are self-contained and support the same set of developer scenarios. To use the downloadable VHD for POS customizations, you must also follow this step.

-   On the host computer, enable Nested VM support. For more information, see [Run Hyper-V in a Virtual Machine with Nested Virtualization](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/nesting).

### Running the Virtual Machine (VM) locally

Follow these steps to run the VM from Hyper-V Manager.

1.  To start the VM, click **Start**.
2.  To open the VM in a window, click **Connect**.
3.  Click the **Ctrl+Alt+Delete** button on the toolbar. The VM receives most keyboard commands, but Ctrl+Alt+Delete isn't one of them. Therefore, you must use the button or a menu command.
4.  Sign in to the VM by using the following credentials:
    -   User name: **Administrator**
    -   Password: **pass@word1**

    **Tip:** You can resize the VM window by changing the screen resolution. Right-click the desktop on the VM, and then click **Screen resolution**. Select a resolution that works well for your display.
5.  Provision the administrator user. For more information, see the next section.
6.  Start the Batch Manager Service. This step is required if you're running batch jobs or workflows.
    1.  Open a **Command Prompt** window as an administrator.
    2.  Type **net start DynamicsAxBatch**, and then press Enter.

    You can also start the service from the **Services** window.

#### Retail configuration

For the downloadable VHD for POS customizations, you must also follow these steps on the guest VM.

1.  Download and install [Microsoft Emulator for Windows 10 Mobile Anniversary Update](https://www.microsoft.com/en-us/download/details.aspx?id=53424).
2.  Start the Hyper-V host service. For more information, see [Hyper-V: The Hyper-V Virtual Machine Management service must be running](https://technet.microsoft.com/en-us/library/ee956894(v=ws.10).aspx). If errors occur during startup, you can also try to uninstall and reinstall the Hyper-V role on the guest VM.

### Provisioning the administrator user

For developer access, you must be an administrator on the instance. To provision your own credentials as an administrator, run the admin user provisioning tool that is provided on the desktop, and provide your email address (Azure AD credentials) in the tool.

1.  From the desktop, run the admin user provisioning tool as an administrator (right-click the icon, and then click **Run as administrator**).
2.  Enter your email address, and then click **Submit**.

### Retail configuration

#### For Dynamics 365 for Operations, Version 1611

1.  Run the RetailTenantUpdateTool.
    -   The icon for this tool is available on the desktop.
    -   This tool is also available at the following location: C:\windowsSystem32WindowsPowerShellv1.0PowerShell.exe -File C:\RetailSDKToolsRetailTenantUpdateTool.ps1

2.  Double-click the icon to start this tool. You will be prompted for your Azure AD credentials. You must use the same credentials that you used in the admin user provisioning tool earlier.

#### For Microsoft Dynamics AX 7.0

1.  Install [Microsoft Online Services Sign-In Assistant for IT Professionals RTW](http://go.microsoft.com/fwlink/?LinkID=286152).
2.  Install [Azure Active Directory Module for Windows PowerShell (64-bit version)](http://go.microsoft.com/fwlink/p/?linkid=236297).
3.  Query Azure AD for your tenant and user ID. Open a Windows PowerShell Integrated Scripting Environment (ISE) window with administrative privileges, and run the following command. You will be prompted for Azure AD credentials. Use the same user account that you used in the admin user provisioning tool earlier.

        $msocred = Get-Credential 
        Connect-MsolService -Credential $msocred 
        $company = Get-MsolCompanyInformation 
        Write-Host "TenantID: $($company.ObjectId)" 
        $msocred.UserName 
        $users = Get-MsolUser -SearchString "$($msocred.username)" 
        foreach($u in $users) 
        { 
            if($u.SignInName -eq $msocred.UserName) 
            { 
               Write-Host "SignInName:$($u.SignInName) UserId: $($u.ObjectId)" 
            } 
        }

    [![Command in the Windows PowerShell ISE window](./media/retailconfig02-1024x529.png)](./media/retailconfig02.png)

4.  Update the following SQL script, and run it in on AXDB for that environment. Supply values for the following parameters from the preceding Windows PowerShell script output:

    -   **TenantID** – For example, c83429a6-782b-4275-85cf-60ebe81250ee
    -   **UserId** – For example, a036b5d8-bc8c-4abe-8eec-17516ea913ec

    <!-- -->

        DECLARE @TenantId NVARCHAR(1024) 
        DECLARE @UserId NVARCHAR(1024) 
        SET @TenantId = ‘‘ 
        SET @UserId = ‘‘ 
        IF(LEN(@TenantId) > 0 AND LEN(@UserId) > 0) 
            BEGIN 
            UPDATE AxDBRAIN.dbo.SYSSERVICECONFIGURATIONSETTING SET [VALUE] = @TenantId WHERE [NAME] = ‘TENANTID’ 
            UPDATE RetailHoustonStore.ax.SYSSERVICECONFIGURATIONSETTING SET [VALUE] = @TenantId WHERE [NAME] = ‘TENANTID’ 
            UPDATE AxDBRAIN.dbo.RETAILSTAFFTABLE SET EXTERNALIDENTITYID = @TenantId, EXTERNALIDENTITYSUBID = @UserId WHERE STAFFID = ‘000160’
            END 
        ELSE 
            BEGIN 
            RAISERROR (15600, -1, -1, ‘TenantId and UserId must be set before running this script’) 
            END

5.  Reset Internet Information Services (IIS) by running **IISRESET** in an elevated **Command Prompt** window.
6.  Update the Real-time service profile to use the new admin user.
    1.  Click **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Real-time service profiles**.
    2.  Click **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Real-time service profiles**.
    3.  Edit the JBB record so that it uses the user that you used earlier (for example, **administrator@contosoax7.onmicrosoft.com**).
    4.  Run CDX Job 1070 (Staff) for the default channel database.
    5.  Verify that the job succeeded by viewing the **Download Sessions** page on the client.

### Base URL of the local application

After the user is provisioned as an administrator, that user can access the instance on the computer by navigating to the following base URL: https://usnconeboxax1aos.cloud.onebox.dynamics.com. If you're using version control and plan to connect multiple development VMs to the same Visual Studio Team Services (VSTS) project, rename your local VM. For instructions, see [Rename a local development VM to enable access to Visual Studio Team Services](http://ax.help.dynamics.com/visual-studio-online-vso-machine-renaming).

#### Retail configuration

The URL of the Retail Cloud POS app is: <https://usnconeboxax1pos.cloud.onebox.dynamics.com/> After you complete the configuration steps, this VM is provisioned with your Azure AD tenant. Your Azure AD admin account is mapped to a cashier worker account in demo data. You can use this cashier account to easily activate a Retail POS device in this environment.

-   Cashier user ID: **000160**
-   Cashier password: **123**
-   Cashier LE: **USRT**
-   Cashier store: **Houston**

## Location of packages, source code, and other AOS configurations
On a VM, you can find most of the application configuration by opening the web.config file of AOSWebApplication.

1.  Start IIS.
2.  Go to **Sites** &gt; **AOSWebApplication**.
3.  Right-click, and then click **Explore** to open File Explorer.
4.  Open the web.config file in Notepad or another text editor. The following keys are of interest to many developers and administrators:
    -   **Aos.MetadataDirectory** – This key points to the location of the packages folder that contains platform and application binaries, and also source code. (Source code is available only in development environments.) Typical values are: c:\packages, c:\AosServicePackagesLocalDirectory, and J:AosServicePackagesLocalDirectory.
    -   **DataAccess.Database** – This key holds the name of the database.
    -   **Aos.AppRoot** – This key points to the root folder of the Application Object Server (AOS) web application.

### Retail configuration

The Retail software development kit (SDK) is available at C:\RetailSDK. For more information about how to use and customize retail applications, see the following topics:
-   [Microsoft Dynamics 365 for Operations – Retail for IT Pros and developers](../retail/dev-itpro/dev-retail-home-page.md)
-   [Retail SDK overview](../retail/dev-itpro/retail-sdk-overview.md)
-   [Retail POS device activation](https://ax.help.dynamics.com/en/wiki/cloud-pos-and-modern-pos-guided-device-activation-and-client-simplifications/)

## Redeploying or restarting the runtime on the VM
To restart the local runtime and redeploy all the packages, follow these steps.

1.  Open File Explorer, and go to C:\CustomerServiceUnit.
2.  Right-click **AOSDeploy.cmd**, and then click **Run as administrator**.

This process might take a while. The process is completed when the cmd.exe window closes. If you just want to restart AOS (without redeploying the runtime), run **iisreset** from an administrator **Command Prompt** window, or restart AOSWebApplication from IIS.

