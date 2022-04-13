---
# required metadata

title: Set up POS hybrid app on Android and iOS
description: This topic shows how to set up the POS hybrid app on Android and iOS.
author: mugunthanm 
ms.date: 09/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-10-29
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Set up POS hybrid app on Android and iOS
[!include [banner](../includes/banner.md)]

This topic shows how to build and run the Retail POS hybrid app on Android and iOS devices. 

## Overview

Retail hybrid app is shell built using [Xamarin](/xamarin/). Inside the shell is a Web view controller that loads the cloud POS, which is based on the Commerce Scale Unit URL specified in the settings of this app. This is a Retail hybrid app shell for Android and iOS which will internally load the Cloud POS. For more information, see [Cloud POS](/dynamics365/unified-operations/retail/mpos-or-cpos).

## Development tools
The Retail hybrid app supports the Android and iOS phone platforms. The app is built by using Xamarin, which means that you must install Xamarin on your development computer. To build the iOS app, you must have a Mac that has Xamarin installed. Although you can do development for both Android and iOS on a computer that runs Microsoft Windows, you must use a Mac to complete the build for the iOS platform. If your Mac is a shared team resource, you might want to use a Mac just for the build process. You must copy the Retail software development kit (Retail SDK) on all the computers that you use for development. The Retail SDK is available in all developer VMs that are provisioned for using [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/).

For more information about Xamarin, see the [Xamarin documentation](/xamarin/).

## Set up and install Xamarin on Windows

To set up and install Xamarin on Windows, go to [Windows Installation](/xamarin/android/get-started/installation/windows).

### Update Xamarin

> [!NOTE]
> We recommend that you use Xamarin.Android SDK version < 10.0. 

After you've installed Xamarin, you must update it to the latest stable version (Xamarin.Android SDK version must be < 10.0).

-   **Windows** - In Microsoft Visual Studio, click **Tools** &gt; **Options** &gt;**Environment** &gt; **Xamarin** &gt; **Other**.
-   **Mac** - In Xamarin Studio, click **Check for Updates** &gt; **Update channel**. For more information about this step, see [Change the Updates Channel](https://developer.xamarin.com/recipes/cross-platform/ide/change_updates_channel/).

### Build the Android Retail hybrid app

> [!NOTE]
> We recommend that you use Visual Studio 2019 or later to build the Android app.

1. When installation is complete, launch Visual Studio and sign in with your Microsoft account (this is the same account that you use with Windows). Check for Xamarin updates by clicking **Tools > Options > Xamarin** or **Tools > Options > Xamarin > Other**. Here you'll find a **Check Now** link. If you do not see an option for Xamarin in **Tools > Options**, review your installation, or try restarting Visual Studio. You can also search for Xamarin in the **Options** dialog box. If needed, download and install the latest version.
      
2.  In the [Retail SDK folder](retail-sdk/retail-sdk-overview.md#download-the-retail-sdk), open SampleExtensions\HybridApp\Android\solution. Build and deploy using the emulator and verify that everything appears as it should.
  
3.  Using the [Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/ "Visual Studio Emulator for Android") or any emulator for Android, launch the POS hybrid app and enter the Commerce Scale Unit URL and save.
  
4.  You should be able to sign in and activate the device.

### Build the iOS Retail hybrid app

### Connecting to a Mac

If you're developing on Windows and using the Mac just for building the iOS app then you must connect the computer that runs Windows and the Mac. For instructions, see [Connecting to the Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/connecting-to-mac/).

 ## Set up and install Xamarin on iOS

For more detailed steps on installing Xamarin on iOS, refer to [Xamarin.iOS installation](/xamarin/ios/get-started/installation/).

  1.  Download and install Xcode from <https://developer.apple.com/xcode/>. Add your Apple ID using the instructions described in [Adding your account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).
  
  2.  Download and install Xamarin by following the instructions in [Installing and configuring Xamarin.iOS](https://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).
  
  3.  When you have completed installing Xamarin on both the Windows and Mac computers, follow the instructions in [Connecting to the Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com). After you do this, you can work with iOS and Mac from Visual Studio on the Windows computer.
  
  ### Build the iOS Retail hybrid app
  
  1.  In the [Retail SDK folder](/retail-sdk/retail-sdk-overview#download-the-retail-sdk), open SampleExtensions\HybridApp\iOS\solution.
      After connecting to the Mac and building the application in Visual Studio, select the iOS device type and deploy the app on the selected device.
      
       ![POS iOS app VS setting for deployment.](./media/iOSSetting.png)
      
  2.  Using the Emulator, go to **Settings > RetailMPOS**. Enter the Commerce Scale Unit URL.
      
       ![POS iOS app setting.](./media/iOSApp.png)
      
       ![POS iOS app setting for RS URL.](./media/iOSRSURL.png)
      
  3.  Launch the MPOS app. You should be able to sign in and activate the device.


## Hybrid app signing and distribution

To sign and distribute the Android and iOS app, refer to the following options:

**Android**
- [Signing the Android Application Package](/xamarin/android/deploy-test/signing/?tabs=windows)
- [Android app distribution](https://developer.android.com/distribute/marketing-tools/alternative-distribution)

**iOS**
- [iOS Code Signing](https://developer.apple.com/support/code-signing/)
- [iOS app distribution](https://developer.apple.com/documentation/xcode/preparing-your-app-for-distribution)


  
## Dedicated hardware station support for the hybrid Android app
  
Starting in release 8.1.3, dedicated hardware station support has been added to the hybrid Android app. In the same way that the Retail Modern POS has built-in support for peripheral devices, the Android app can also use the dedicated hardware station to connect to peripherals without needing to deploy an IIS-based hardware station.
Out of the box, the hybrid Android app supports using payment terminals and receipt printers over network connections. Communicating with devices over a network typically requires adherence to a proprietary communication protocol specified by the manufacturer. For the hybrid Android app, out-of-the- box integrations are provided for the Dynamics 365 Payment Connector for Adyen and Epson receipt printers. 

### Out-of-the-box supported devices

| Device | Description |
| --- | --- |
| Payment terminals | Any supported by the [Adyen Payment Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) through the Dynamics 365 Payment Connector for Adyen. |
| Receipt printer | Network-enabled Epson printers that support the Epson SOAP HTTP interface.<p>Network-enabled Star Micronics printers.</p> |
| Cash drawer | Introduced in Dynamics 365 Commerce version 10.0.8: Cash drawers that are connected to network-enabled printers via the drawer kick (d/k) port. |

Support for other payment processors and peripheral devices can be implemented by ISVs through the Payments and Hardware SDKs. 

### Set up peripherals to work with the hybrid Android app

To enable direct hardware support for the hybrid Android app, set up a dedicated hardware station in the same way it would be set up for MPOS. Instructions for setting up the dedicated, or IPC, hardware station can be found in [Retail peripherals](../retail-peripherals-overview.md#modern-pos-for-windows-with-an-ipc-built-in-hardware-station-1)

> [!NOTE]
> The dedicated hardware station provided with demo data should not be used with the hybrid Android app. To test the hybrid Android app in an environment with demo data, delete the existing hardware stations and create a new dedicated hardware station. 
>
> To do this, go to **Retail and Commerce > Channels > Stores > All stores**. Select the store that will be used, typically "HOUSTON". 
>
> In the store details form, scroll down to the **Hardware stations** FastTab. Remove the existing dedicated hardware station, then select **Add** to add a new hardware station of type **Dedicated**. A description is optional. No other details are necessary for the hardware station. 

To set up the payment connector, follow the standard setup steps noted in the [Dynamics 365 Payment Connector for Adyen](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#setup-and-configuration). Skip the section labeled "Update the Modern POS or IIS Hardware Station configuration."

For details on setting up network connected peripherals the docs [Support for network peripherals](./network-peripherals.md).

## Additional resources
- [Payments FAQ](payments-retail.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
