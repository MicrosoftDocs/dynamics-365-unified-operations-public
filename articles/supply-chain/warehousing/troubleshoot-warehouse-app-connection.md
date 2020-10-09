---
# required metadata

title: Troubleshoot warehouse app connection issues
description: This topic describes how to fix common issues that you might encounter while connecting the Dynamics 365 for Finance and Operations - Warehousing application to Dynamics 365 Supply Chain Management.
author: ivanv-microsoft
manager: tfehr
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WMA
# ROBOTS: 
audience: Warehouse manager
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Warehousing
ms.author: ivanv
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.14
---

# Troubleshoot warehouse app connection issues

This topic describes how to fix common issues that you might encounter while connecting the *Dynamics 365 for Finance and Operations - Warehousing* application to Dynamics 365 Supply Chain Management.

> [!NOTE]
> If you are having issues that aren't listed on this page, please contact Microsoft Support and let us know so we can help you solve the issues and add them for the benefit of all customers.

## Trust anchor for certification path not found

This section explains what to do if the warehousing app shows a **Trust anchor for certification path not found** error when trying to connect to Supply Chain Management.

![Error on mobile device](media/WMA_TrustAnchor_Error.png "Error on mobile device")

### Scope

This issue can affect devices with the following properties:

- **OS version**: Android 4.4.x (such as Zebra TC55). (This isn't an issue on recent Android versions.)
- **Supply Chain Management location**: Cloud
- **Connection mode**: Client secret or Certificate

### Possible root cause

Microsoft may have updated the server SSL certificates used by Supply Chain Management. As a result, the root certificate and/or one of the intermediate certificates may have changed, so the new certificate isn't on the list of trusted system certificates for the mobile device. Newer versions of Android automatically update their lists of trusted certificates, but Android 4.4.x doesn't.

### Resolution

Do one of the following to fix this issue:

- Use the workaround described in the next section to update each relevant device.
- It *might* be possible to contact Zebra or Google to get an update of the system trusted certifying authority (CA) certificates. However, we have not confirmed this.
- If possible, consider replace older device(s) with devices that are running a more recent version of Android (where trusted CA certificates are updated automatically).

### Workaround

#### Step 1: Export the new root certificate from Supply Chain Management

Manually download the new root certificate using your internet browser by doing the following:

1. Sign in to Dynamics Supply Chain Management and open its front page.
1. In the address bar of your browser, select the lock icon to open the **Location is secure** dialog box.
1. In the dialog box, select **Certificate (valid)** to open the **Certificate** window for that certificate.
1. Open the **Certification path** tab of the **Certificate** window.
1. Select the top certificate shown in the hierarchy (this is the root certificate).
1. Open the **Details** tab of the **Certificate** window.
1. Select the **Copy to file** button at the bottom of the **Details** tab.
1. The **Certificate export wizard** opens. Select **Next** to continue.
1. The **Export file format** page opens. Select the **DER encoded binary X.509 (.CER)** radio button. Then select **Next** to continue.
1. The **Files to export** page opens; use it to specify a file name and location. Then select **Next** to continue.
1. The **Completing the certificate export wizard** page opens, showing the result of your export. Select **Finish**.

#### Step 2: Install the downloaded certificate onto the impacted devices

Install the downloaded certificate by doing the following:

1. Transfer the certificate you downloaded in the previous step to the device you want to update. For example, you might use an SD card or network connection to make the file available to your device.
1. Open the security settings for your device and choose the menu option to install a certificate from a file. (The exact steps for this vary based on device and OS version.)
1. The new certificate should now be shown on the **User** tab for trusted certificates.
1. Repeat this procedure for each affected device.
