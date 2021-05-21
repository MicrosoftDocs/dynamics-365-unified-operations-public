This topic applies to Dynamics 365 Commerce version 10.0.20 and later.

The Store Commerce app in Microsoft Dynamics 365 Commerce provides rich commerce functionalities for first line workers, such as cashiers, sales associates, inventory associates, stock clerks, and store managers, to perform commerce operations like cash and carry transactions, cash/shift management, customer engagement, assisted selling, clienteling, endless aisle, order processing/fulfillment, inventory management, and reporting.

> [!NOTE]
> The Store Commerce is released as a preview app, Store Commerce app uses the [Microsoft Edge WebView2](https://docs.microsoft.com/en-us/microsoft-edge/webview2/) which is in preview, so this app must not be used in production. The Store Commerce app can be used in production once its GA (Generally available).

Store Commerce is a shell app for Windows that uses [Microsoft Edge WebView2](https://docs.microsoft.com/en-us/microsoft-edge/webview2/) to render the Cloud Point of Sale (CPOS). CPOS can run only in a web browser, but Store commerce can run as a native Windows app like [Modern Point of Sale (MPOS)](retail-modern-pos-architecture.md). Store Commerce supports local hardware station and can be directly integrated to payment terminal, printer, and cash drawer. You don't need to set up a shared hardware station to use hardware devices. 

Store Commerce uses the Chromium engine to render the UI instead of the Universal Windows Platform (UWP) app rendering framework. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. The key difference between MPOS and Store Commerce is that Store Commerce uses the Chromium engine to render the app.

## Application lifecycle management (ALM)

Store Commerce is an app that runs on a Windows device. The app will be available from [Windows Apps - Microsoft Store](https://www.microsoft.com/store/r/9PGK1J3KQ8JB) for easier discovery, download and deployment, simplifying the overall lifecycle of deployment and servicing. The Store Commerce app is both forward and backward compatible, the app can be updated independently of the Cloud Scale Unit and Extensions. The app can be easily updated by setting up the windows policy or using any Microsoft Store app supported update and deployment tools like Intune etc. The Modern POS of Sale requires more manual management to get the app, package it with extensions but the Store Commerce app greatly simplifies the ALM because its deployed from the  Microsoft Store.  

Store Commerce is a shell that renders CPOS, so you should also update CPOS to get the updated CPOS functionality. CPOS can be updated from the Cloud Scale unit (CSU). For more information about updating CSU refer [Apply updates and extensions to Commerce Scale Unit (cloud)](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/update-retail-channel)

![Store Commerce](media/StoreCommerce.PNG)

## Store Commerce is the future MPOS:

When Store Commerce has full functional parity with MPOS, it will replace MPOS. Currently, Store Commerce doesn't support running offline (when there is no connectivity to Retail Server). For more information about the different POS apps and topology, see [Choose between Modern POS (MPOS) and Cloud POS](../mpos-or-cpos.md)

## Choosing between Store Commerce and MPOS:



## Setup and installation

### Prerequisite:

+ Microsoft Edge, because the app uses the Microsoft Edge WebView2 control.

### HQ Device Setup:

For the Store Commerce app new Application type called **Store Commerce** is added in the Retail and Commerce > Channel Setup > Pos Setup > Devices, when you create a device for the Store Commerce app, select the Application type as Store Commerce.

Create a [Register](https://docs.microsoft.com/en-us/dynamics365/commerce/tasks/create-associate-registers) and [Device](https://docs.microsoft.com/en-us/dynamics365/commerce/tasks/create-associate-device) for the Store Commerce app and run the Register job from the Distribution schedule in the HQ before activating the app, please select the Application type as **Store Commerce** during the device creation.

Store Commerce is available in the Microsoft Store to download and installation. To download the app, follow these steps:

1. Open [Windows Apps - Microsoft Store](https://www.microsoft.com/store/r/9PGK1J3KQ8JB) and search for **Store Commerce**.
2. Select **Get** to install the app. 
3. In the Windows Start menu, search for Store Commerce and open the app.

After Store Commerce launches, follow these steps to configure and activate the app:

1.	In the app start page, enter the Cloud POS URL. You can find the Cloud POS URL from the LCS environment details page or at **Dynamics 365 commerce > Channel Setup > Channel Profiles**.
2.	Select **Save**.
3.	After saving the URL, follow the steps to activate Store Commerce. For the detailed steps to activate the app, see [POS activation guide](retail-device-activation.md#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation).
4.	After the app is activated, login with an employee account. You can now complete your commerce tasks.

### Troubleshooting setup issues

#### Reset the app

If you entered an invalid CPOS URL and want to change it, or the app is in an error state during activation, then you can restart the process by resetting the app.

1. Right-click the app in the Start menu and choose **More > App settings**.
2. Scroll down the app settings page to the **Reset** button.
3. Select **Reset** and acknowledge the confirmation prompt.

## Customizing the app

Store Commerce app can be customized using the POS extension support in the Retail SDK. You can modify and create the POS user experience, make out-of-box functional enhancements or modifications, add validations, and add custom features. For more information, see [Point of Sale (POS) extension overview](pos-extension/pos-extension-overview.md).

Extensions developed using the Retail SDK will work for CPOS, MPOS, and Store Commerce, but how the extension is packaged and deployed by MPOS and CPOS is different.

Because the Store Commerce renders the CPOS, you follow the CPOS packaging and deployment options for deploying the store commerce extension.

### Hardware station extension(HWS)

The app can also be extended to integrate with hardware devices, [sample extension code added in GitHub to generate Store Commerce HWS extension package](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample). For more information, see [Integrate the POS with a new hardware device](hardware-device-extension.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)] 
