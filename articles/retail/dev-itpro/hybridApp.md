---
# required metadata

title: Set up POS Hybrid app on Android and iOS
description: This topic shows how to set up set up POS Hybrid app on Android and iOS.
author: mugunthanm 
manager: AnnBe
ms.date: 10/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-29-10
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Set up POS Hybrid app on Android and iOS
[!include [banner](../includes/banner.md)]

This topic shows how to set up set up POS Hybrid app on Android and iOS.

## Set up and install Xamarin on Windows

### Prerequisites

-   Recommended - A physical Windows computer (not a VM) running Windows 8 or later.
-   You can use a computer with Windows 7 or earlier, in which case you’ll use the Xamarin Player for Android as the emulator.

### Set up 

1. Open **Control Panel > Programs and Features**, select  **Visual Studio 2015**. Click **Change**. When the installer opens, click **Modify**.

2. Go to **Cross-Platform Mobile Development > C#/.NET (Xamarin)**. Select **Common Tools and Software Development Kits** so that all of the options are selected. Selecting this option should also update an existing Xamarin installation, if neeeded.
  
  ![VS Xamarin Android Development Kit](./media/VSInstall.PNG)
  
3. Click **Install** and let the process run. This will take some time to complete.

4. When installation is complete, launch Visual Studio and sign in with your Microsoft account (this is the same account that you use with Windows). Check for Xamarin updates by clicking **Tools > Options > Xamarin** or **Tools > Options > Xamarin > Other**. Here you’ll find a **Check Now** link. If you do not see an option for Xamarin in **Tools > Options**, review your installation, or try restarting Visual Studio. You can also search for Xamarin in the Options dialog box. If needed, download and install the latest version.
      
5.  In the Retail SDK folder, open SampleExtensions\HybridApp\Android\solution. Build and deploy using the emulator and verify that everything appears as it should.
  
6.  Using the emulator, enter the Retail Server URL and save.
  
7.  You should be able to sign in and activate the device.

 ## Set up and install Xamarin on iOS

  1.  Download and install Xcode from <https://developer.apple.com/xcode/>. Add your Apple ID using the instructions desrcibed in [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).
  
  2.  Download and install Xamarin by following the instructions in [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).
  
  3.  When you have completed installing Xamarin on both the Windows and Mac computers, follow the instructions in [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com). After you do this, you can work with iOS and Mac from Visual Studio on the Windows computer.
  
  4.  In the Retail SDK folder, open SampleExtensions\HybridApp\iOS\solution.
      After connecting to the Mac and building the application in Visual Studio, select the iOS device type and deploy the app on the selected device.
      
         ![POS iOS app VS setting for deployment](./media/iOSSetting.png)
      
  5.  Using the Emulator, go to **Settings > RetailMPOS**. Enter the Retail Server URL.
      
         ![POS iOS app setting](./media/iOSApp.png)
      
         ![POS iOS app setting for RS URL](./media/iOSRSURL.png)
      
  6.  Launch the MPOS app. You should be able to sign in and activate the device.
