---
# required metadata

title: Configure and install Retail hardware station
description: This topic explains how to configure, download, and install Retail hardware station by using self-service. It also explains how to uninstall Retail hardware station.
author: jashanno
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailHardwareStation
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom: 27161
ms.assetid: eb164a9d-5538-4b6f-81ad-87e05d92eca5
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Configure and install Retail hardware station

[!include[banner](includes/banner.md)]

This topic explains how to configure, download, and install Retail hardware station by using self-service. It also explains how to uninstall Retail hardware station.

## Download Retail hardware station by using self-service

### Configure a new Retail hardware station profile (Start here for Dynamics 365 for Retail, February 2016)

> [!NOTE]
> This procedure is required only if you're running the February 2016 (RTW) version of Microsoft Dynamics 365 for Retail. If you're running version 1611, start with the next procedure.

1. Use your Microsoft Azure Active Directory (Azure AD) credentials to sign in to the Retail headquarters or Microsoft Dynamics 365 for Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware station profiles**.
3. On the **Hardware station profile** page, on the Action Pane, select **New**.
4. In the **Hardware station ID** field, enter a unique hardware station ID.

    > [!NOTE]
    > The **Name** field is used for a description of the unique hardware station profile.

5. In the appropriate fields, enter the port number, select a hardware profile, and select a package name.

    > [!NOTE]
    > Only one hardware station package is provided for an environment that has been loaded with demo data.

6. On the Action Pane, select **Save**.

### Configure a new Retail hardware station (Start here for Dynamics 365 for Retail, version 1611 or later)

> [!NOTE]
> If you're running the February 2016, non-upgraded version of Dynamics 365 for Retail (Initial release), skip step 6.

1. Use your Azure AD credentials to sign in to the Dynamics 365 for Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
3. On the **All retail stores** page, select the retail channel ID of the desired store. The details view for the store appears.

    > [!NOTE]
    > The Houston store is the most thoroughly prepared store in the demo data.

4. On the **Retail store details** page, on the **Hardware stations** FastTab, select **Add**.

    > [!NOTE]
    > The Retail Server URL that is used for the selected store is read-only. This URL will be important during the installation of Retail hardware station.

5. In the **Hardware station type** field, select **Shared** to indicate that this hardware station is an Internet Information Services (IIS), installed hardware station that will be used by external point of sale (POS) systems.

    > [!NOTE]
    > The value **Shared** signifies that the installation is a truly shared hardware station installation, and that it works through HTTPS communication. By contrast, the value **Dedicated** signifies that the hardware station is a part of Retail Modern POS, and that it works through inter-process communication.

6. Follow one of these steps, depending on the version that you're running:

    - **For version 1611:** In the appropriate fields, enter the port number, select a hardware profile, and select a package name.

        > [!NOTE]
        > Only one hardware station package is provided for an environment that has been loaded with demo data, at environment creation time.

    - **For the February 2016 version:** Select a hardware station profile.

7. Enter the host name of the computer that you're installing Retail hardware station on. Additionally, enter the electronic funds transfer (EFT) terminal ID that is associated with that computer for merchant account information.

### Download the Retail hardware station installer

1. Use your Azure AD credentials to sign in to the Retail headquarters or Dynamics 365 for Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
3. On the **All retail stores** page, select the retail channel ID of the desired store. The details view for the store appears.

    > [!NOTE]
    > The Houston store is the most thoroughly prepared store in the demo data.

4. On the **Retail store details** page, select the **Hardware stations** FastTab.

    > [!NOTE]
    > The Retail Server URL that is used for the selected store is read-only. This URL will be important during the installation of Retail hardware station.

5. Select the hardware station to download, and then select **Download**.

    > [!NOTE]
    > - Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.
    > - The correct installation package is automatically selected for download, based on the hardware station profile.

6. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)
7. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on your browser.)

### Run the installer

> [!NOTE]
> Before you run the Retail hardware station installer, make sure that the following requirements are met:
> - The installer requires that the Microsoft .NET Framework version 4.5.1 be installed on your system.
> - The installer installs Retail hardware station only on the following operating systems:
>    - Windows 7 Professional, Enterprise, or Ultimate edition (both x86 and x64 architectures). Home edition and Embedded edition aren't supported.
>    - Windows 8.1 Update 1 Pro or Enterprise edition (both x86 and x64 architectures). Standard edition isn't supported.
>    - Windows 10 Pro or Enterprise edition with Anniversary Update (both x86 and x64 architectures). Home edition isn't supported.
>    - Microsoft Windows Server 2012 R2.

The Retail hardware station installer first extracts the associated files and then begins the installation.

1. The installer validates that all prerequisites are met. If a sideloading key is required, the installer requests it. This key is found on the **Devices** page for each device, under **General**.

    > [!NOTE]
    > - If a system restart is required, the installer informs you of this requirement but can continue the installation.
    > - Before you can use hardware that is based on the Object Linking and Embedding for Retail Point of Sale (OPOS) standard, the OPOS Common Control Objects must be installed. If they aren't installed, the installer informs you of this requirement but can continue the installation.

2. Enter the Retail Server URL (for example, **https://MyCompanyNameret.axcloud.dynamics.com/Commerce**), and then select **Next**.

    > [!NOTE]
    > You can find the Retail Server URL at the top of the **Hardware stations** FastTab on the **Retail store details** page.

3. Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication.

    > [!NOTE]
    > The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.

4. The next page requests the user that should be used for the IIS application pool. By default in version 1611 and later, the installer can automatically create and use a service account. If you're on a domain or require more specific controls, clear the check box, and then enter the user name and password that the application pool should run under.
5. Enter the HTTPS port to use.

    > [!NOTE]
    > - You can find the HTTPS port in Dynamics 365 for Retail. (See the configuration instructions earlier in this topic).
    > - The installer automatically enters the host name. If, for any reason, you must change the host name for the installation, you can change it here. The host name must be the fully-qualified domain name (FQDN) of the system, and it must be entered in the **Host name** field for the selected hardware station entry.

6. The installer installs Retail hardware station and then indicates whether the installation was successful.
7. When the installation is completed, the Install merchant information tool starts. This installer connects to the environment and installs the merchant account information (such as the EFT ID) for the selected hardware station.

    > [!NOTE]
    > If the hardware station that was installed won't be used for payment-related work, don't close the **Install merchant information** window without completing the remaining steps. The hardware station won't work unless this installation is successfully completed.

8. The Install merchant information tool might request Azure AD credentials. Enter the Azure AD credentials of the user who is installing Retail hardware station.
9. The Retail Server URL is determined through the Retail hardware station installation and is entered automatically. The installer uses this URL to load the list of stores that the user is connected to via the address book.
10. Select the retail store that the hardware station was installed for.
11. Select the hardware profile that matches the hardware station that was installed on the current computer.
12. Verify that the host names and EFT terminal IDs are correct, based on the current computer and the Retail hardware station configuration that has already been completed in Dynamics 365 for Retail. After you've verified this information, select **Install**.
13. When you receive a message that states that the merchant account information was installed correctly, exit the installer by selecting the **Close** button.

## Help secure Retail hardware station
Current security standards state that the following options should be set in a production environment:

> [!NOTE]
> The hardware station installer automatically makes these registry edits as part of the installation through self-service.

- SSL should be disabled.
- Only Transport Layer Security (TLS) version 1.2 (or the current highest version) should be enabled and used.

    > [!NOTE]
    > By default, SSL and all version of TLS except TLS 1.2 are disabled. To edit or enable these values, follow these steps:
    > 1. Press the Windows logo key+R to open a **Run** window.
    > 2. In the **Open** field, type **Regedit**, and then select **OK**.
    > 3. If a **User Account Control** window appears, select **Yes**.
    > 4. In the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**. The following keys have been automatically entered to allow for TLS 1.2 only:
    >    - TLS 1.2\\Server:Enabled=1
    >    - TLS 1.2\\Server:DisabledByDefault=0
    >    - TLS 1.2\\Client:Enabled=1
    >    - TLS 1.2\\Client:DisabledByDefault=0
    >    - TLS 1.1\\Server:Enabled=0
    >    - TLS 1.1\\Client:Enabled=0
    >    - TLS 1.0\\Server:Enabled=0
    >    - TLS 1.0\\Client:Enabled=0
    >    - SSL 3.0\\Server:Enabled=0
    >    - SSL 3.0\\Client:Enabled=0
    >    - SSL 2.0\\Server:Enabled=0
    >    - SSL 2.0\\Client:Enabled=0

- No additional network ports should be open, unless they are required for known, specified reasons.
- Cross-origin resource sharing must be disabled and must specify the allowed origins that are accepted.
- Only trusted certificate authorities should be used to procure certificates that will be used on computers that run Retail hardware station.

> [!IMPORTANT]
> - Most common, lower-security software and services will stop working after all lower-security standards are disabled. To use them again, go to the preceding registry keys, and set the **Enabled** key from **0** to **1**.
> - It's critical that you review security guidelines for IIS and Payment Card Industry (PCI) requirements.

## Troubleshooting
### Retail Modern POS can detect the hardware station in its list for selection, but it can't complete the pairing

**Solution:** Verify the following list of potential failure points:

- The computer that is running Retail Modern POS trusts the certificate that is used on the computer that runs Retail hardware station.

    - To verify this setup, in a web browser, go to the following URL: https://&lt;Computer Name&gt;:&lt;Port Number&gt;/HardwareStation/ping
    - This URL uses a ping to verify that the computer can be accessed, and the browser indicates whether the certificate is trusted. (For example, in Internet Explorer, a lock symbol appears in the address bar. When you select this symbol, Internet Explorer verifies whether the certificate is currently trusted. You can install the certificate on the local computer by viewing the details of the certificate that is shown.)

- On the computer that runs Retail hardware station, the port that will be used by the hardware station is opened in the firewall.
- Retail hardware station has properly installed merchant account information through the Install merchant information tool that runs at the end of the Retail hardware station installer.

### Retail Modern POS can't detect the hardware station in its list for selection

**Solution:** Any one of the following factors can cause this issue:

- Retail hardware station hasn't been set up correctly in Retail headquarters. Use the steps earlier in this topic to verify that the hardware station profile and the hardware station are correctly entered.
- The jobs haven't been run to update the channel configuration. In this case, run the 1070 job for channel configuration.
- The hardware station isn't accessible from that computer. Verify that the hardware station URL ping test is accessible from a web browser. This URL can be found at the end of the hardware station installer and is in the following form: https://&lt;Computer Name&gt;:&lt;Port Number&gt;/HardwareStation/ping

## Uninstall Retail hardware station
You can use Control Panel in Microsoft Windows to uninstall Retail hardware station.

1. Press the Windows logo key, and then, in the search box, type **Control Panel**. In the list of search results, select **Control Panel**.
2. In Control Panel, select **Programs** &gt; **Uninstall a program**. The **Programs and Features** window opens.
3. Select **Microsoft Dynamics 365 for Retail for Retail hardware station**, and then select **Uninstall** above the list of programs.
4. Wait for the uninstaller to finish removing the program.
