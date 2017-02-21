---
# required metadata

title: Retail hardware station configuration and installation
description: This tutorial explains how to configure, download, and install Retail hardware station by using self-service. It also explains how to uninstall Retail hardware station.
author: josaw1
manager: AnnBe
ms.date: 2015-12-13 04 - 48 - 42
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: RetailHardwareStation
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27161
ms.assetid: eb164a9d-5538-4b6f-81ad-87e05d92eca5
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Retail hardware station configuration and installation

This tutorial explains how to configure, download, and install Retail hardware station by using self-service. It also explains how to uninstall Retail hardware station.

Download Retail hardware station by using self-service
------------------------------------------------------

### Configure a new Retail hardware station profile (Start here for Dynamics 365 for Operations, February 2016 )

**Note:** This procedure is only required if you are running the February 2016 (RTW) version of Microsoft Dynamics 365 for Operations. If you are running version 1611, start with the next procedure.

1.  Use your Microsoft Azure Active Directory (AAD) credentials to sign in to the Microsoft Dynamics Commerce headquarters or Microsoft Dynamics 365 for Operations trial.
2.  On the **Welcome** page, use the menu in the upper left to navigate to **Retail and commerce** &gt; **Channel setup &gt; POS setup &gt; POS profiles **&gt; **Hardware station profiles**.
3.  On the **Hardware station profile** page, on the Action Pane, click **New**.
4.  In the **Hardware station ID** field, enter a unique hardware station ID. **Note:** The **Name** field is used for a description of the unique hardware station profile.
5.  Enter the port number, select a hardware profile, and select a package name in the appropriate fields. **Note:** Only one hardware station package is provided for an environment that has been loaded with demo data.
6.  On the Action Pane, click **Save**.

### Configure a new Retail hardware station (Start here for Dynamics 365 for Operations version 1611)

**Note:** If you are running the February 2016 version of Dynamics 365 for Operations, pay close attention to step 5. Use your Azure AD credentials to sign in to the Dynamics 365 for Operations trial.

1.  On the **Welcome** page, use the menu in the upper left to navigate to **Retail and commerce** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
2.  On the **All retail stores** page, select the retail channel ID of the desired store. The details view for the store opens. **Note:** The Houston store is the most thoroughly prepared store in the demo data.
3.  On the **Retail store details** page, on the **Hardware stations** FastTab, click **Add**. **Note:** The Retail Server URL that is used for the selected store is read-only. This URL will be important during the installation of Retail hardware station.
4.  In the **Hardware station type** field, select **Shared**. This means that this hardware station is an IIS, installed hardware station to be used by external POS systems.
5.  **For version 1611:** Enter the port number, select a hardware profile, and select a package name in the appropriate fields. **Note:** Only one hardware station package is provided for an environment that has been loaded with demo data, at environment creation time. **For version** **February 2016:** Select a hardware station profile.
6.  Enter the host name of the computer that you're installing Retail hardware station on. Additionally, enter the electronic funds transfer (EFT) terminal ID that is associated with that computer for merchant account information.

### Download the Retail hardware station installer

1.  Use your Azure AD credentials to sign in to the Microsoft Dynamics Commerce headquarters or Dynamics 365 for Operations trial.
2.  On the **Welcome** page, use the menu in the upper left to navigate to **Retail and commerce** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
3.  On the **All retail stores** page, select the retail channel ID of the desired store. The details view for the store opens. **Note:** The Houston store is the most thoroughly prepared store in the demo data.
4.  On the **Retail store details** page, click the **Hardware stations** FastTab. **Note:** The Retail Server URL that is used for the selected store is read-only. This URL will be important during the installation of Retail hardware station.
5.  Select the hardware station to download, and then click **Download**. **Note:** Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Click **Download** again. **Note:** The correct installation package is automatically selected for download, based on the hardware station profile.
6.  On the notification bar that appears at the bottom of the Internet Explorer window, click **Save**. (The Notification bar might appear in a different place in other browsers.)
7.  After the setup installer has been saved, on the Notification bar, click **Run**. (This step might differ, depending on your browser.)

### Run the installer

**Note:** Before you run the Retail hardware station installer, make sure that the following requirements are met:

-   The installer requires that the Microsoft .NET Framework version 4.5.1 be installed on your system.
-   The installer installs Retail hardware station only on the following operating systems:
    -   Windows 7 Professional, Enterprise, or Ultimate edition (both x86 and x64 architectures). Home edition and Embedded edition aren't supported.
    -   Windows 8.1 Update 1 Pro or Enterprise edition (both x86 and x64 architectures). Standard edition isn't supported.
    -   Windows 10 Pro or Enterprise edition with Anniversary Update (both x86 and x64 architectures). Home edition isn't supported.
    -   Microsoft Windows Server 2012 or Microsoft Windows Server 2012 R2.

The Retail hardware station installer first extracts the associated files, and then begins the installation:

1.  The installer validates that all prerequisites are met. If a sideloading key is required, the installer requests it. This key is found on the **Devices** page for each device, under **General**. **Note:** If a system restart is required, the installer informs you of this requirement but can continue the installation. **Note:** Before you can use hardware that is based on the object linking and embedding for point of sale (OPOS) standard, the OPOS Common Control Objects must be installed. If they aren't installed, the installer informs you of this requirement but can continue the installation.
2.  Enter the Retail Server URL (for example, **https://MyCompanyNameret.axcloud.dynamics.com/Commerce**), and then click **Next**. **Note:** You can find the Retail Server URL at the top of the **Hardware stations** FastTab on the **Retail store details** page.
3.  Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication. **Note:** The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.
4.  Enter the user name and password that the application pool will run under. **Note:** Currently, service users aren't supported in this installer.
5.  Enter the HTTPS port to use. **Note:** You can find the HTTPS port in the hardware station profile. To access the hardware station profile, on the **Retail store details** page, on the **Hardware stations** FastTab, select the profile ID of the selected hardware station. **Note:** The installer automatically enters the host name. If, for any reason, you must change the host name for the installation, you can change it here. The host name must be the fully-qualified domain name (FQDN) of the system, and it must be entered in the **Host name** field for the selected hardware station entry.
6.  The installer installs Retail hardware station and then indicates whether the installation was successful.
7.  When the installation is completed, the Install merchant information tool starts. This installer connects to the environment and installs the merchant account information (such as the EFT ID) for the selected hardware station. **Note:** If the hardware station that was installed won't be used for payment-related work, close the **Install merchant information** window without completing the remaining steps inthis procedure.
8.  The Install merchant information tool might request Azure AD credentials. Enter the Azure AD credentials of the user who is installing Retail hardware station.
9.  The Retail Server URL is entered automatically (it's known through the Retail hardware station installation). The installer uses this URL to load the list of stores that the user is connected to via the address book.
10. Select the retail store that the hardware station was installed for.
11. Select the hardware station profile that matches the hardware station that was installed on the current computer.
12. Verify that the host names and EFT terminal IDs are correct, based on the current computer and the Retail hardware station installation that was just completed. Then click **Install**.
13. When you receive a message that states that the merchant account information was installed correctly, exit the installer by clicking the **Close** button.

## Help secure Retail hardware station
Current security standards state that the following options should be set in a production environment: **Note:** The hardware station installer will make these registry edits automatically as part of installation through self-service.

-   SSL should be disabled.
-   Only Transport Layer Security (TLS) version 1.2 (or the current highest version) should be enabled and used. **Note:** By default, SSL and all version of TLS except TLS 1.2 are disabled. To edit or enable these values, follow these steps:
    1.  Press the Windows logo key+R to open a **Run** window.
    2.  In the **Open** field, type **Regedit**, and then click **OK**.
    3.  If a **User Account Control** window appears, click **Yes**.
    4.  In the new **Registry Editor** window, navigate to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**. The following keys have been automatically entered to allow for TLS 1.2 only:
        -   TLS 1.2\\Server:Enabled=1
        -   TLS 1.2\\Server:DisabledByDefault=0
        -   TLS 1.2\\Client:Enabled=1
        -   TLS 1.2\\Client:DisabledByDefault=0
        -   TLS 1.1\\Server:Enabled=0
        -   TLS 1.1\\Client:Enabled=0
        -   TLS 1.0\\Server:Enabled=0
        -   TLS 1.0\\Client:Enabled=0
        -   SSL 3.0\\Server:Enabled=0
        -   SSL 3.0\\Client:Enabled=0
        -   SSL 2.0\\Server:Enabled=0
        -   SSL 2.0\\Client:Enabled=0
-   No additional network ports should be open, unless they are required for known, specified reasons.
-   Cross-origin resource sharing must be disabled and must specify the allowed origins that are accepted.
-   Only trusted certificate authorities should be used to procure certificates that will be used on computers that run Retail hardware station.

**Note:** It's critical that you review security guidelines for IIS and the Payment Card Industry (PCI) requirements.

## Troubleshooting
### Retail Modern POS can detect the hardware station in its list for selection, but it can't complete the pairing

**Solution:** Verify the following list of potential failure points:

-   The computer that is running Retail Modern POS trusts the certificate that is used on the computer that runs Retail hardware station.
    -   To verify this setup, in a web browser, go to the following URL: https://&lt;Computer Name&gt;:&lt;Port Number&gt;/HardwareStation/ping.
    -   This URL uses a ping to verify that the computer can be accessed, and the browser indicates whether the certificate is trusted. (For example, in Internet Explorer, a lock icon appears in the address bar. When you click this icon, Internet Explorer verifies whether the certificate is currently trusted. You can install the certificate on the local computer by viewing the details of the certificate that is shown.)
-   On the computer that runs Retail hardware station, the port that will be used by the hardware station is opened in the firewall.
-   Retail hardware station has properly installed merchant account information through the Install merchant information tool that runs at the end of the Retail hardware station installer.

### Retail Modern POS can't detect the hardware station in its list for selection

**Solution:** Either of the following factors can cause this issue:

-   Retail hardware station hasn't been set up correctly in headquarters. Use the steps earlier in this tutorial to verify that the hardware station profile and the hardware station are correctly entered.
-   The jobs haven't been run to update the channel configuration. In this case, run the 1070 job for channel configuration.

## Uninstall Retail hardware station
You can use Control Panel in Microsoft Windows to uninstall Retail hardware station.

1.  Press the Windows logo key, and then, in the search box, type **Control Panel**. In the list of search results, select **Control Panel**.
2.  In Control Panel, click **Programs** &gt; **Uninstall a program**. The **Programs and Features** window opens.
3.  Select **Microsoft Dynamics 365 for Operations for Retail hardware station**, and then click **Uninstall** above the list of programs.
4.  Wait for the uninstaller to finish removing the program.


