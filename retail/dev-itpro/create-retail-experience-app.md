---
# required metadata

title: Create a Retail Experience app
description: This topic explains how you can apply your branding to the Retail Experience app, and release it to Google Play and the Apple App Store. 
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 251594
ms.assetid: 922881a2-f12a-41b4-8ef9-a5b31b464ef1
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Create a Retail Experience app

[!include[banner](../includes/banner.md)]


This topic explains how you can apply your branding to the Retail Experience app, and release it to Google Play and the Apple App Store. 

You can apply your branding to the Retail Experience app, and release it to Google Play and the Apple App Store. This topic explains how to build the app, connect to Microsoft Dynamics 365 for Operations, and apply your branding.

## Development tools
The Retail Experience app supports the Android and iOS phone platforms. The app is built by using Xamarin.Forms, and you must install Xamarin on your development computer. To build the iOS app, you must have a Mac that has Xamarin installed. Although you can do development for both Android and iOS on a computer that runs Microsoft Windows, you must use a Mac to complete the build for the iOS platform. If your Mac is a shared team resource, you might want to use a Mac just for the build process. You must install the Retail software development kit (SDK) on all the computers you use for development.

### Install Xamarin

You can download Xamarin from <https://www.xamarin.com/download>. For a tutorial that shows how to install Xamarin on Windows, see <https://developer.xamarin.com/videos/?v=Installing_Xamarin_on_Windows>.

### Update Xamarin

After you've installed Xamarin, you must update it to the latest stable version.

-   **Windows:** In Microsoft Visual Studio, click **Tools** &gt; **Options** &gt;**Environment** &gt; **Xamarin** &gt; **Other**.
-   **Mac:** In Xamarin Studio, click **Check for Updates** &gt; **Update channel**. (For more information about this step, see [https://developer.xamarin.com/recipes/cross-platform/ide/change\_updates\_channel/.](https://developer.xamarin.com/recipes/cross-platform/ide/change_updates_channel/))

For more information, see [Change the Updates Channel](https://developer.xamarin.com/recipes/cross-platform/ide/change_updates_channel/).

### Connecting to a Mac

If you're developing on Windows and using the Mac just for building the iOS app then you must connect the computer that runs Windows and the Mac. For instructions, see [Connecting to the Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/connecting-to-mac/).

## Loading the solution in Visual Studio
You must modify the Retail Experience app solution before it can be loaded correctly in Visual Studio. Follow these steps.

1.  Copy the **entire** Retail SDK folder to a Xamarin-enabled computer. For example, copy it to C:RetailSdk.
2.  Open C:RetailSdkSampleExtensionsShoppingAppSample.ShoppingApp.sln, and remove the following line.

           
        Project("{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}") = "RetailSdk.Sample.ShoppingApp", "RetailSdk.Sample.ShoppingApp.csproj", "{D88688FA-C42E-48BE-8334-5A5855561913}" .

3.  Open C:RetailSdkSampleExtensionsShoppingAppiOSShoppingApp.iOS.csproj, and remove following lines.

        <Import Project="......BuildToolsMicrosoft.Dynamics.RetailSdk.Build.props" />
        <Import Project="......BuildToolsMicrosoft.Dynamics.RetailSdk.Build.settings" />
        <Import Project="$(SdkRootPath)BuildToolsMicrosoft.Dynamics.RetailSdk.Build.targets" />
        <HintPath>......ReferencesXamarin.iOS.0.0.0Xamarin.iOS.dll</HintPath>

4.  In Visual Studio, open Sample.ShoppingApp.sln, and add existing projects from the Droid and iOS folders. (Right-click the solution, and then select **Add** &gt; **Existing Projects in Visual Studio**.)
5.  Xamarin.Forms fixed an issue with the version 2.3.2.127 that is required for the app so please upgrade the Xamarin.Forms version as described below:
    1.  Open the .csproj files for both Android and iOS projects and replace the line "&lt;PkgXamarin\_Forms&gt;$(NugetPackagesRoot)Xamarin.Forms.2.3.1.114&lt;/PkgXamarin\_Forms&gt;" with &lt;PkgXamarin\_Forms&gt;$(NugetPackagesRoot)Xamarin.Forms.2.3.2.127&lt;/PkgXamarin\_Forms&gt;
    2.  Open the files package.config file for both Android and iOS projects and replace the line "&lt;package id="Xamarin.Forms" version="2.3.1.114" targetFramework="monoandroid60" /&gt;" with "&lt;package id="Xamarin.Forms" version="2.3.2.127" targetFramework="monoandroid60" /&gt;"

## Connect to a Dynamics 365 for Operations online channel
The Retail Experience app uses an online channel to show the products. You can use any online channel. Depending on your requirements, you can use a different online channel for each apps, or you can use the same online channel for both apps. Any released product that is assorted to the online channel will appear in the app. **Note:** The app can't be used to issue gift cards. Therefore, gift cards must be excluded from the assortment for the online channel that the apps use. Information about the Retail Server endpoint and the online channel is added to the config.xml file that is present in each app project. You must make the following changes in the config.xml file:

-   In the **&lt;DataServiceUrl&gt;** tag, add the URL of the Retail Server.
-   In the **&lt;MediaBaseUrl&gt;** tag, add the URL of the media server. Make sure that this URL has a slash (/) at the end.
-   In the **&lt;OperatingUnitNumber&gt;** tag, add the operating unit number of the online channel that you want to use together with the app. **Note:** Enter the complete operating unit number. For example, in the demo data, the operating unit number for Contoso online store is 068.

## Connect to a payment connector
To enable payments to be accepted from the app, you must set up a payment connector on the online channel that is used for the app. The payment connector loads the card-related controls on a host HTML page. We have added a host page that is named CardPaymentHost.html to the Retail SDK. We have also verified that this host page works with the MasterCard connector. However, you might have to edit this page to meet the requirements of the other payment providers. Different connectors might provide pages. The host page can be hosted on any website that you choose. However, we recommend that you host it on your eCommerce site, if you have an eCommerce site. After the page has been hosted, add the URL of the host page in the **&lt;CardPaymentHostPageUrl&gt;** tag.

## Update the About page
Add the following links to the about page:

-   In the **&lt;TermsOfUseUrl&gt;** tag, add a link to the license terms.
-   In the **&lt;PrivacyPolicyUrl&gt;** tag, add a link to the privacy policy.
-   In the **&lt;ThirdPartyNoticesUrl&gt;** tag, add a link to the third-party notices.

**Note:** If these links are missing, and the user clicks them, the app might stop responding. Therefore, be sure to add the links to these tags. The about page has an **&lt;EvaluationModeEnabled&gt;** tag that is used to enable Evaluation Mode view. Evaluation Mode lets retailers easily change the Retail Server endpoint without having to change any code. This feature helps retailers evaluate the app for various channels. **Evaluation Mode must be disabled in the production version of the app.** By default, Evaluation Mode is disabled in the Retail SDK.

## Apply branding
After you've successfully built the Retail Experience app by using the Microsoft sample branding, you can change icons, labels, and colors to make the app meet your own branding requirements. The following list shows some of the icons, labels, and colors that retailers might want to change. This list isn't exhaustive. **Icons**

-   **App** – The icon that users see after the app is installed on their phones.
-   **Retailer's brand** – The icon that appears on the menu flyout on Android.
-   **Shop** – The icon that appears on the menu flyout on Android, and on the tab bar on Apple iPhone.
-   **Information** – The icon that appears on the menu flyout on Android, and on the tab bar on iPhone.
-   **Shopping Cart** – The icon that appears in the upper-right corner on Android, and on the tab bar on iPhone.
-   **Search** – The icon that appears in the upper-right corner on Android and iPhone.
-   **Splash screen** – The icon that appears as the loading image on Android and iPhone.

**Labels/texts**

-   App name (the name that appears below the app icon when the app is installed on the phone)
-   Shop icon name and the corresponding page title
-   Information icon name and the corresponding page title
-   Confirmation messages that appear as toast notifications
-   "Add to cart" button text and the corresponding page title
-   "Checkout" button text and the corresponding page title
-   "Place order" button text
-   About page label and the corresponding page title

**Colors**

-   App bar (The app bar is also known as the action bar or toolbar.)
-   Status bar color
-   Accent color
-   Primary action button colors. For example, the **Add to Cart**, **Checkout**, **Place Order**, and **Continue** buttons all have the same color.

### Applying branding to the Android app

#### Icons

To change the icons for the Android app, open the Resource folder, and update the icons in each drawable folder. These drawable folders contain images for Android at different resolutions. You can either preserve the sizes of the images in these folders or change them to meet your requirements. For information about how Android handles different screen sizes, see <https://developer.android.com/guide/practices/screens_support.html>. The splash screen is put in the drawable folder and is a special type of image that Android requires. For more information about the splash screen, see <https://developer.android.com/studio/write/draw9patch.html>.

#### Label/text

To change the text labels on the Android app, open the TextResources.resx file, and edit the values of the available resources. The following table shows the name of the label/text that appears on the Android device and the corresponding property/key that must be changed in TextResources.resx. The app name is specified in the strings.xml file.

| Label/text                                                 | Property name/key                                                                                        |
|------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| App name                                                   | **App\_name**. This property can be found in the strings.xml file at ../ShoppingAppDroidResourcesvalues. |
| Shop icon name and the corresponding page title            | **MenuPage\_Products** and **Pages\_CategoryListPage\_Products**, respectively                           |
| Information icon name and the corresponding page title     | **MainTabs\_Account** and **Pages\_AccountPage\_AccountInformation**, respectively                       |
| Confirmation messages that appear as toast notifications   | Multiple messages in TextResources.resx                                                                  |
| "Add to cart" button text and the corresponding page title | **Pages\_ProductDetail\_AddToCart** and **Pages\_CartPage\_Title**, respectively                         |
| "Checkout" button text and the corresponding page title    | **Pages\_CartPage\_Checkout** and **Pages\_CheckoutPage\_Title**, respectively                           |
| "Place order" button text                                  | **Pages\_CheckoutPage\_PlaceOrder**                                                                      |
| About page label and the corresponding page title          | **Pages\_AccountPage\_About** and **Pages\_AboutPage\_Title**, respectively                              |

**Note:** Some of the resources in the TextResources.resx file aren't used by the Android app, but they are used by the iOS app. Examples include **MainTabs\_Cart** and **MainTabs\_Products**. You can change those resources from the Android app without affecting the iOS app.

#### Colors

To change the colors that appear in the Android app, open the config.xml file and colors.xml files (colors.xml is under Resources-&gt;values folder). Now change the values for **Primary** (the app bar color), **PrimaryDark** (the status bar color), **Accent**, and **ActionButtonBackground in both the files** and keep them consistent. **Note**: The product price is shown on two pages namely products list page and the product details page. The price shown on the product list page is set to green (\#008A00) and cannot be altered. However, the price shown on the product details page is governed by the value set for the "PrimaryDark" property.

### Applying branding to the iOS app

#### Icons

To change the icons on the iOS app, open the Resource folder, and update the icons. You can either preserve the sizes of the images in the folders or change them to meet your requirements.

#### Label/text

To change the text for the iOS app, open the TextResources.resx file, and edit the values of the available resources. The following table shows the name of the label/text that appears on the iOS device and the corresponding property/key that must be changed in TextResources.resx. The app name is specified in the info.plist file.

| Label/text                                                 | Property name/key                                                                                    |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| App name                                                   | **CFBundleDisplayName**. This property can be found in the info.plist file in the app's iOS project. |
| Shop icon name and the corresponding page title            | **MainTabs\_Products** and **Pages\_CategoryListPage\_Products**, respectively                       |
| Information icon name and the corresponding page title     | **MainTabs\_Account** and **Pages\_AccountPage\_AccountInformation**, respectively                   |
| Confirmation messages that appear as toast notifications   | Multiple messages in TextResources.resx                                                              |
| "Add to cart" button text and the corresponding page title | **Pages\_ProductDetail\_AddToCart** and **Pages\_CartPage\_Title**, respectively                     |
| "Checkout" button text and the corresponding page title    | **Pages\_CartPage\_Checkout** and **Pages\_CheckoutPage\_Title**, respectively                       |
| "Place order" button text                                  | **Pages\_CheckoutPage\_PlaceOrder**                                                                  |
| About page label and the corresponding page title          | **Pages\_AccountPage\_About** and **Pages\_AboutPage\_Title**, respectively                          |

**Note:** Some of the resources in the info.plist file aren't used by the iOS app, but they are used by the Android app. An example is **MenuPage\_Products**. You can change those resources from the iOS app without affecting the Android app.

#### Colors

To change the colors that appear in the iOS app, open the config.xml file, and change the values for **Primary** (the app bar color), **PrimaryDark** (the status bar color), **Accent**, and **ActionButtonBackground**. **Note**: The product price is shown on two pages namely products list page and the product details page. The price shown on the product list page is set to green (\#008A00) and cannot be altered. However, the price shown on the product details page is governed by the value set for the "PrimaryDark" property.

## Build, test and distribute apps
The next step is to build the app and test on devices. Testing will be followed by publishing the app to the public app stores. We have added the standard external links from Xamarin and Apple which explain the basics of Android and iOS app distribution.

### Android:

To test the Android app on an emulator follow the below steps on Visual Studio

1.  Select Droid as startup project, Marshmallow as Android device.
2.  Build Release | Any CPU.
3.  Run in Marshmallow emulator.

The below link from Xamarin explains how to use the Archive manager on Visual studio to **create an .apk file** that can be signed by a signing certificate. [https://developer.xamarin.com/guides/android/deployment,\_testing,\_and\_metrics/publishing\_an\_application/part\_1\_-\_preparing\_an\_application\_for\_release/\#\_Archive\_for\_Publishing\_](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/publishing_an_application/part_1_-_preparing_an_application_for_release/#_Archive_for_Publishing_) The below link from Xamarin explains how to create a signing certificate and **sign the .apk file** for adhoc and GooglePlay store distribution. [https://developer.xamarin.com/guides/android/deployment,\_testing,\_and\_metrics/publishing\_an\_application/part\_2\_-\_signing\_the\_android\_application\_package/\#\_Signing\_the\_APK\_](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/publishing_an_application/part_2_-_signing_the_android_application_package/#_Signing_the_APK_) The below link explains the steps involved with the **public distribution of an application** created with Xamarin.Android via channels such as e-mail, a private web server, Google Play, or the Amazon App Store for Android. [https://developer.xamarin.com/guides/android/deployment,\_testing,\_and\_metrics/publishing\_an\_application/](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/publishing_an_application/)

### iOS:

To test the iOS app on an emulator follow the below steps on Visual Studio

1.  Select iOS as startup project
2.  Connect to Mac as explained above
3.  Build Release | iPhone.
4.  Run it in VS.

The below link from Xamarin explains the **distribution techniques** that are available for Xamarin.iOS applications and provides pointers to more detailed documents. [https://developer.xamarin.com/guides/ios/deployment,\_testing,\_and\_metrics/app\_distribution/](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/app_distribution/) The below link from Apple explains how to **maintain your signing identities and certificates** [https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) **Note**: If you are using the certificates as a part of Apple Developer Enterprise Program if you install an app manually (e.g. for testing) then you must also manually establish trust as described in the following link. [https://support.apple.com/en-us/HT204460](https://support.apple.com/en-us/HT204460)


