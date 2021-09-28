--- 
title: Certification path error when setting up app connection 
description: If the Warehouse Management app shows the error "Trust anchor for certification path not found," use this page to resolve or work around the issue. 
author: ivanv-microsoft 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
ms.search.form: WMA
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: ivanv 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
# Trust anchor for certification path not found when setting up app connection

## Symptoms

When trying to connect to Supply Chain Management, the Warehouse Management app may show you the following error message:

> java.security.cert.certPathValidatorException: Trust anchor for certification path not found.

This issue can affect devices with the following properties:

- **OS version**: Android 4.4.x (such as Zebra TC55). This is not an issue on recent Android versions.
- **Supply Chain Management location**: Cloud
- **Connection mode**: Client secret or certificate

## Possible cause

Microsoft may have updated the server SSL certificates used by Supply Chain Management. As a result, the root certificate and/or one of the intermediate certificates may have changed, so the new certificate isn't on the list of trusted system certificates for the mobile device. Newer versions of Android automatically update the lists of trusted certificates, but Android 4.4.x doesn't.

## Resolution

Do one of the following to resolve this issue:

- Use the workaround described in the next section to update each relevant device.
- It *might* be possible to contact Zebra or Google to get an update of the system trusted certifying authority (CA) certificates. However, we have not confirmed this.
- If possible, consider replacing older devices with devices that are running a more recent version of Android (where trusted CA certificates are updated automatically).

### Workaround

#### Step 1: Export the new root certificate from Supply Chain Management

Manually download the new root certificate using your internet browser by doing the following:

1. Sign in to Dynamics Supply Chain Management and open the front page.

1. In the address bar of your browser, select the lock icon to open the **Location is secure** dialog box.
1. In the dialog box, select **Certificate (valid)** to open the **Certificate** window for that certificate.
1. Open the **Certification path** tab of the **Certificate** window.
1. Select the top certificate shown in the hierarchy. (this is the root certificate).
1. Open the **Details** tab of the **Certificate** window.
1. Select the **Copy to file** button at the bottom of the **Details** tab.
1. The **Certificate export wizard** opens. Select **Next** to continue.
1. The **Export file format** page opens. Select **DER encoded binary X.509 (.CER)**. Then select **Next** to continue.
1. The **Files to export** page opens, specify a file name and location. Then select **Next** to continue.
1. The **Completing the certificate export wizard** page opens, showing the result of your export. Select **Finish**.

#### Step 2: Install the downloaded certificate onto the affected devices

Install the downloaded certificate by doing the following:

1. Transfer the certificate you downloaded in the previous step to the device you want to update. For example, you might use an SD card or network connection to make the file available to your device.
1. Open the security settings for your device and choose the menu option to install a certificate from a file. (The exact steps for this vary based on device and OS version.)
1. The new certificate should now be shown on the **User** tab for trusted certificates.
1. Repeat this procedure for each affected device.
