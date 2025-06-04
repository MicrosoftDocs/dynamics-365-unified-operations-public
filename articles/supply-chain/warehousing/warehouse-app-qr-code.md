---
title: Use a QR code to connect the mobile app to Supply Chain Management
description: Learn how to generate and scan QR codes to quickly configure the Warehouse Management mobile app
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/04/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSMobileDeviceMenuItem, WHSWorkUserDisplaySettings, WHSMobileAppInstallation, WHSMobileDeviceUser, WHSMobileDeviceConfiguration, WHSRFMenuItemTable, WHSParameters, WHSMobileDeviceMenuItemConfiguration, WHSMobileDeviceConnectionSettings, WHSUserSettings, SysAADClientTable, WHSMobileDeviceQRCode, WHSConnectionConfiguration
---

# Use a QR code to connect the mobile app to Supply Chain Management

The Warehouse Management mobile app supports QR code configuration to simplify the connection setup process. Instead of manually entering connection details, you can scan a QR code that contains all necessary configuration information.

## Overview

QR codes can contain connection configuration data in JSON format, allowing for quick deployment and setup of the Warehouse Management app across multiple devices. This method is useful for IT administrators who need to configure multiple devices or when sharing configurations with warehouse workers.

## Supported connection types

The QR-based connection configuration feature supports all connection types available in the Warehouse Management mobile app, including:

- **DeviceCode** – Interactive authentication flow
- **UsernamePassword** – Username/password authentication

## Step 1: Prepare your configuration JSON

Create a JSON configuration with your connection details, as described in[Create a connection settings file or QR code](install-configure-warehouse-management-app.md#connection-file-qr). The JSON should follow this structure:

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://yourenvironment1.cloudax.dynamics.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "DeviceCode",
            "AuthCloud": "AzureGlobal"
        }
    ]
}
```

## Step 2: Generate a QR code

You can use various online QR code generators or programmatic solutions. Choose the method that best suits your needs.

### Option 1: Generate a QR code using Copilot

Follow these steps to ask Copilot to generate a QR code for your JSON configuration:

1. Open a Copilot chat session, for example by selecting the **Copilot** button in Microsoft Edge or by launching Copilot from the Windows taskbar.
1. Enter a prompt like the following, but include your specific JSON configuration:

   ```text
   Please generate a QR code for the following JSON configuration:
   {
       "ConnectionList": [
           {
               "ConnectionName": "Production",
               "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
               "Company": "USMF",
               "IsEditable": true,
               "IsDefaultConnection": true,
               "ConnectionType": "DeviceCode",
               "AuthCloud": "AzureGlobal"
           }
       ]
   }
   ```

1. Copilot generates a QR code image based on the provided JSON configuration. Download the image to your device, for example by using right-click or drag-and-drop.

### Option 2: Generate a QR code using an online QR code generator

To generate a QR code using an online QR code generator, follow these steps:

1. Visit any reputable QR code generator website. Bing can help you find one.
1. Select *Text* or *JSON* format.
1. Paste the complete JSON configuration that you prepared.
1. Generate and download the QR code image.

### Option 3: Generate a QR code using PowerShell

You can use PowerShell to generate a QR code from your JSON configuration using code similar to the following:

```powershell
# Install QR code module if not already installed
Install-Module -Name QRCodeGenerator

# Your JSON configuration
$jsonConfig = @"
{
    "ConnectionList": [
        {
            "ConnectionName": "Production",
            "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": true,
            "ConnectionType": "DeviceCode",
            "AuthCloud": "AzureGlobal"
        }
    ]
}
"@

# Generate QR Code
New-QRCode -Data $jsonConfig -OutPath "warehouse-config.png"
```

## Step 3: Distribute the QR code

Once you've generated the required QR code, you can distribute it in any of the following ways:

- Print the QR code for physical distribution or send it by email.
- Share it digitally via email or collaboration platforms.
- Display it on screens for easy scanning.
- Include it in documentation or setup guides.

> [!TIP]
> Copilot can decode a QR code if you enter a prompt such as "Please decode this QR code," and upload the image. This can be useful for verifying the contents of the QR code before distributing it.

## Step 4: Scan the QR code on each device

To use the generated QR code to configure a device, follow the procedure provided in [Import the connection settings](install-configure-warehouse-management-app.md#config).
