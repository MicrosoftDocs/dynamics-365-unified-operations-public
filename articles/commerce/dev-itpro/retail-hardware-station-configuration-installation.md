---
title: Configure and install Retail hardware station
description: Learn how to configure, download, install, and uninstall the legacy Retail hardware station by using self-service functionality.
author: anush6121
ms.author: anvenkat
ms.date: 02/19/2026
ms.topic: how-to
ms.search.form: RetailHardwareStation
ms.reviewer: v-griffinc
ms.assetid: eb164a9d-5538-4b6f-81ad-87e05d92eca5
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Configure and install Retail hardware station

[!include [banner](../includes/banner.md)]

This article explains how to configure, download, install, and uninstall the legacy Retail hardware station by using self-service functionality.

> [!IMPORTANT]
>
> - This component uses a server certificate. You must manage server certificates for expiration. By default, a certificate expires in one calendar year (365 days).
> - Hardware station installations don't support the use of self-signed certificates. Instead, use a trusted partner certificate.

For more information about sealed self-service installers, see [Mass deployment of sealed Commerce self-service components](Enhanced-Mass-Deployment.md).

## Prerequisites

When configuring hardware station for Dynamics 365 Commerce versions 10.0.42 and later, you must add the following registry entries to support Transport Layer Security (TLS) 1.3:

- TLS 1.3\Server:Enabled=1
- TLS 1.3\Client:Enabled=1
- TLS 1.2\Server:Enabled=1
- TLS 1.2\Client:Enabled=1
- TLS 1.1\Server:Enabled=0
- TLS 1.1\Client:Enabled=0
- TLS 1.0\Server:Enabled=0
- TLS 1.0\Client:Enabled=0
- SSL 3.0\Server:Enabled=0
- SSL 3.0\Client:Enabled=0
- SSL 2.0\Server:Enabled=0
- SSL 2.0\Client:Enabled=0

When configuring hardware station for Commerce versions 10.0.41 and earlier, you must add the following registry entries to support TLS 1.2:

- TLS 1.2\Server:Enabled=1
- TLS 1.2\Client:Enabled=1
- TLS 1.1\Server:Enabled=0
- TLS 1.1\Client:Enabled=0
- TLS 1.0\Server:Enabled=0
- TLS 1.0\Client:Enabled=0
- SSL 3.0\Server:Enabled=0
- SSL 3.0\Client:Enabled=0
- SSL 2.0\Server:Enabled=0
- SSL 2.0\Client:Enabled=0

> [!NOTE]
> Any external applications or programs such as antivirus applications should exclude the registry entries listed above and the shared hardware station folder `C:\Users\RetailHardwareStationAppPool\AppData\Local\Microsoft Dynamics AX\Retail Hardware Station\`. This ensures that the registry entries and hardware station folders aren't deleted.

## Download Retail hardware station by using self-service

### Configure a new Retail hardware station

> [!NOTE]
> If you're running the February 2016, nonupgraded version of Retail (Initial release), skip step 6.

To configure a new Retail hardware station, follow these steps:

1. Use your Microsoft Entra ID credentials to sign in to the Retail trial.
1. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
1. On the **All retail stores** page, select the retail channel ID of the store you want. The details view for the store appears.

    > [!NOTE]
    > The Houston store is the most thoroughly prepared store in the demo data.

1. On the **Retail store details** page, on the **Hardware stations** FastTab, select **Add**.

    > [!NOTE]
    > The Retail Server URL that is used for the selected store is read-only. This URL is important during the installation of Retail hardware station.

1. In the **Hardware station type** field, select **Shared** to indicate that this hardware station is an Internet Information Services (IIS), installed hardware station that external point of sale (POS) systems use.

    > [!NOTE]
    > The value **Shared** signifies that the installation is a truly shared hardware station installation, and that it works through HTTPS communication. By contrast, the value **Dedicated** signifies that the hardware station is a part of the Store Commerce app, and that it works through inter-process communication.

1. Select a hardware station profile.
1. Enter the host name of the computer that you're installing Retail hardware station on. Additionally, enter the electronic funds transfer (EFT) terminal ID that is associated with that computer for merchant account information.
1. To use the configuration file or initial installation using mass deployment, enter the certificate thumbprint to be used during the installation detailed in the next section.

### Download the Retail hardware station installer

To download the Retail hardware station installer, follow these steps:

1. Use your Microsoft Entra ID credentials to sign in to the Retail headquarters or Retail trial.
1. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
1. On the **All retail stores** page, select the retail channel ID of the store you want. The details view for the store appears.

    > [!NOTE]
    > The Houston store is the most thoroughly prepared store in the demo data.

1. On the **Retail store details** page, select the **Hardware stations** FastTab.

    > [!NOTE]
    > The Retail Server URL that is used for the selected store is read-only. This URL is important during the installation of Retail hardware station.

1. Select the hardware station to download, and then select **Download**.

    > [!NOTE]
    > Browsers might block the download pop-up that is generated. You must select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.

1. On the notification bar that appears at the bottom of the Microsoft Edge window, select **Save**. (The notification bar might appear in a different place in other browsers.)
1. If needed for mass deployment or command line deployment, repeat the preceding steps for the configuration file download, which is a button next to the **Download** button that you previously selected.

    > [!NOTE]
    > - If the configuration file you download doesn't have the same base file name as the installer, either rename the XML configuration file to have the same base name or run the installer by using the command line to specify the configuration file.
    > - The configuration file isn't required for the installation of Commerce hardware station.

1. After you save the files, run the installer. (This step might differ depending on your browser.)

### Run the installer

> [!NOTE]
> Before running the Retail hardware station installer, make sure that all [system requirements](../../fin-ops-core/dev-itpro/get-started/system-requirements.md) are met.

The Retail hardware station installer first extracts the associated files and then begins the installation.

To run the installer, follow these steps:

1. The installer validates that all prerequisites are met. If a sideloading key is required, the installer requests it. You can find this key on the **Devices** page for each device, under **General**.

    > [!NOTE]
    > - If a system restart is required, the installer informs you of this requirement but can continue the installation.
    > - Before you can use hardware that is based on the Object Linking and Embedding for Retail Point of Sale (OPOS) standard, the OPOS Common Control Objects must be installed. If they aren't installed, the installer informs you of this requirement but can continue the installation.

1. Enter the Retail Server URL (for example, `https://MyCompanyNameret.axcloud.dynamics.com/Commerce`), and then select **Next**.

    > [!NOTE]
    > You can find the Retail Server URL at the top of the **Hardware stations** FastTab on the **Retail store details** page.

1. Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication.

    > [!NOTE]
    > - The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.
    > - The use of self-signed certificates isn't allowed for hardware station installations. Instead, use a trusted partner certificate.

1. The next page requests the user that should be used for the IIS application pool. By default in version 1611 and later, the installer can automatically create and use a service account. If you're on a domain or require more specific controls, clear the check box, and then enter the user name and password that the application pool should run under.
1. Enter the HTTPS port to use.

    > [!NOTE]
    > - You can find the HTTPS port in Retail. (See the configuration instructions earlier in this article).
    > - The installer automatically enters the host name. If, for any reason, you must change the host name for the installation, you can change it here. The host name must be the fully qualified domain name (FQDN) of the system, and it must be entered in the **Host name** field for the selected hardware station entry.

1. The installer installs Retail hardware station and then indicates whether the installation was successful.
1. When the installation is completed, the Install merchant information tool might start. This installer connects to the environment and installs the merchant account information (such as the EFT ID) for the selected hardware station.

    > [!NOTE]
    > - If the hardware station that you installed isn't used for payment-related work, don't close the **Install merchant information** window without completing the remaining steps. The hardware station won't work unless this installation is successfully completed.
    > - For version 10.0.6 and later, the install merchant information tool isn't used. Instead, the merchant information for the hardware station is set by the POS at the time of sign in or when the hardware station is made active. If the retail server isn't available when the hardware station is later made active, the last known merchant properties are used until the connection to the retail server is re-established. If the POS client isn't upgraded to version 10.0.6 at the same time the hardware station is upgraded, merchant properties aren't updated until the POS client is upgraded to an equal or later version.

1. The Install merchant information tool might request Microsoft Entra ID credentials. Enter the Microsoft Entra ID credentials of the user who is installing Retail hardware station.
1. The Retail Server URL is determined through the Retail hardware station installation and is entered automatically. The installer uses this URL to load the list of stores that the user is connected to via the address book.
1. Select the retail store that the hardware station was installed for.
1. Select the hardware profile that matches the hardware station that you installed on the current computer.
1. Verify that the host names and EFT terminal IDs are correct, based on the current computer and the Retail hardware station configuration that you already completed in Retail. After you verify this information, select **Install**.
1. When you receive a message that states that the merchant account information was installed correctly, exit the installer by selecting the **Close** button.

## Help secure Retail hardware station

Current security standards state that the following options should be set in a production environment:

> [!NOTE]
> The hardware station installer automatically makes these registry edits as part of the installation through self-service.

- Disable SSL.
- Don't open any extra network ports unless known, specified reasons require them.
- Disable cross-origin resource sharing and specify the allowed origins that are accepted.
- Use only trusted certificate authorities to procure certificates for computers that run Retail hardware station.
- Enable and use only Transport Layer Security (TLS) version 1.3 (or the current highest version).

> [!NOTE]
> Starting with Commerce versions 10.0.42 and later, SSL and all versions of TLS except TLS 1.3 are disabled by default. For Commerce versions 10.0.41 and earlier, TLS 1.2 is used instead. To edit or enable these values, follow these steps:
>
> 1. Select the Windows key + R to open a **Run** command window.
> 1. In the **Open** field, enter "Regedit", and then select **OK**.
> 1. If a **User Account Control** dialog appears, select **Yes**.
> 1. In the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
>      - The following keys are automatically entered for Commerce versions 10.0.42 and later to allow for TLS 1.3 only:
>        - TLS 1.3\Server:Enabled=1
>        - TLS 1.3\Client:Enabled=1
>        - TLS 1.2\Server:Enabled=1
>        - TLS 1.2\Client:Enabled=1
>        - TLS 1.1\Server:Enabled=0
>        - TLS 1.1\Client:Enabled=0
>        - TLS 1.0\Server:Enabled=0
>        - TLS 1.0\Client:Enabled=0
>        - SSL 3.0\Server:Enabled=0
>        - SSL 3.0\Client:Enabled=0
>        - SSL 2.0\Server:Enabled=0
>        - SSL 2.0\Client:Enabled=0
>
>      - The following keys are automatically entered for Commerce versions 10.0.41 and earlier to allow for TLS 1.2 only:
>        - TLS 1.2\Server:Enabled=1
>        - TLS 1.2\Client:Enabled=1
>        - TLS 1.1\Server:Enabled=0
>        - TLS 1.1\Client:Enabled=0
>        - TLS 1.0\Server:Enabled=0
>        - TLS 1.0\Client:Enabled=0
>        - SSL 3.0\Server:Enabled=0
>        - SSL 3.0\Client:Enabled=0
>        - SSL 2.0\Server:Enabled=0
>        - SSL 2.0\Client:Enabled=0

> [!IMPORTANT]
>
> - Most common, lower-security software and services stop working after you disable all lower-security standards. To use them again, go to the preceding registry keys, and set the **Enabled** key from **0** to **1**.
> - Review security guidelines for IIS and Payment Card Industry (PCI) requirements.

## Troubleshooting

### Store Commerce app detects the hardware station in its list for selection, but it can't complete the pairing

**Solution:** Verify the following potential failure points:

- The computer that runs the Store Commerce app trusts the certificate that the computer running Retail hardware station uses.

  - To verify this setup, in a web browser, go to the following URL: `https://<Computer Name>:<Port Number>/HardwareStation/ping`
  - This URL uses a ping to verify that the computer can be accessed, and the browser indicates whether the certificate is trusted. For example, in Microsoft Edge, a lock symbol appears in the address bar. When you select this symbol, Microsoft Edge verifies whether the certificate is currently trusted. You can install the certificate on the local computer by viewing the details of the certificate that is shown.

- On the computer that runs Retail hardware station, the port that the hardware station uses is open in the firewall.
- Retail hardware station has correctly installed merchant account information through the **Install merchant information** tool that runs at the end of the Retail hardware station installer.

### Store Commerce app can't detect the hardware station in its list for selection

**Solution:** Any one of the following factors can cause this issue:

- Retail hardware station isn't set up correctly in Commerce headquarters. Use the steps earlier in this article to verify that the hardware station profile and the hardware station are correctly entered.
- The jobs to update the channel configuration didn't run. In this case, run the 1070 job for channel configuration.
- The hardware station isn't accessible from that computer. Verify that the hardware station URL ping test is accessible from a web browser. You can find this URL at the end of the hardware station installer. It's in the following form: `https://<Computer Name>:<Port Number>/HardwareStation/ping`

## Uninstall Retail hardware station

Use Control Panel in Microsoft Windows to uninstall Retail hardware station.

To uninstall Retail hardware station, follow these steps:

1. Press the Windows logo key, and then, in the search box, type **Control Panel**. In the list of search results, select **Control Panel**.
1. In Control Panel, select **Programs** &gt; **Uninstall a program**. The **Programs and Features** window opens.
1. Select **Microsoft Dynamics 365 for Retail hardware station**, and then select **Uninstall** above the list of programs.
1. Wait for the uninstaller to finish removing the program.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
