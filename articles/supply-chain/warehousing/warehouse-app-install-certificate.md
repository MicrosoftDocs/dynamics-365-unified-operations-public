---
title: Migrate the Warehouse Management mobile app from V3 to V4 (preview)
description: Learn how to install certificate for Warehouse Management mobile application Windows to install version 4 (V4). The article includes information about setup instructions.
author: nsayginer
ms.author: nsayginer
ms.topic: how-to
ms.date: 07/11/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# How to Install the Certificate for Warehouse Management Mobile Application (Windows - Version 4) 

Version 4 (preview) of the Warehouse Mobile App is now available. This version introduces significant improvements and new features to enhance the user experience and the app's performance. If you'd like to try out the preview, you can install it directly from App Center. This document will guide you through the steps to install the required certificate on Windows.  

### Step1: Download the App 
 1. Go to [App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release).
 1. Download the **.msixbundle** file to your device.

### Step 2: Install the certificate 
 1. Right click the **.msixbundle** file that you just downloaded from AppCenter.
 1. Select **Properties**.
 1. Go to **Digital Signatures** tab. .
 1. Select the signature in the list and click **Details**.
 1. Click **View Certificate**.
 1. Certificate page will open, click **Install Certificate**.
 1. When you click on Install Certificate, Digital Certificate Wizard will open.
 1. Select **Local Machine**, then click Next.
 1. Choose **Place all certificates in the following store** \> **Browse** for **Trusted Root Certification Authorities**.
 1. Click Next.
 1. Click Finish.
    
### Step 3: Install the app
Double click on the **.msixbundle** file that you installed from AppCenter and click **Install** when it prompted.
