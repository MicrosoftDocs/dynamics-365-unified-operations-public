---
title: Using QRCode to quick connect Warehouse Management Application
description: Learn how to generate QR codes for quick Warehouse Management Application configuration
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 05/30/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSMobileDeviceMenuItem, WHSWorkUserDisplaySettings, WHSMobileAppInstallation, WHSMobileDeviceUser, WHSMobileDeviceConfiguration, WHSRFMenuItemTable, WHSParameters, WHSMobileDeviceMenuItemConfiguration, WHSMobileDeviceConnectionSettings, WHSUserSettings, SysAADClientTable, WHSMobileDeviceQRCode, WHSConnectionConfiguration
---

# Using QR Code to quick connect Warehouse Management Application

The Warehouse Management mobile app supports QR code configuration to simplify the connection setup process. Instead of manually entering connection details, users can scan a QR code that contains all necessary configuration information.

## Overview

QR codes can contain connection configuration data in JSON format, allowing for quick deployment and setup of the Warehouse Management Application across multiple devices. This method is useful for IT administrators who need to configure multiple devices or when sharing configurations with warehouse workers.

## Generating a QR Code

To generate a QR code for your Warehouse Management Application configuration:

### Step 1: Prepare your configuration JSON

Create a JSON configuration with your connection details. The JSON should follow this structure:

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

### Step 2: Generate the QR Code

You can use various online QR code generators or programmatic solutions:

#### Online QR Code Generators

- Visit any reputable QR code generator website
- Select "Text" or "JSON" format
- Paste your complete JSON configuration
- Generate and download the QR code image

#### Microsoft Edge Built-in QR Code Generator

Microsoft Edge includes a built-in QR code generator that you can use:

1. Open Microsoft Edge browser
2. Navigate to any webpage or create a new tab
3. Right-click on the page and select "Create QR code for this page" or use the address bar QR code icon
4. For custom JSON data:
   - Create a temporary text file with your JSON configuration
   - Open the file in Edge (drag and drop or File > Open)
   - Generate the QR code using Edge's built-in feature
   - Save or share the generated QR code

#### Programmatic Generation (PowerShell example)

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

// ...existing code...

### Step 3: Distribute the QR Code

Once generated, you can:

- Print the QR code for physical distribution or send it by email.
- Share it digitally via email or collaboration platforms
- Display it on screens for easy scanning
- Include it in documentation or setup guides

## Using the QR Code in the Mobile App

To use the generated QR code:

1. Open the Warehouse Management mobile application
2. Navigate to Connect
3. Select "Add from QR code Camera" or "Add from QR Code Scanner"
4. Point your device camera or beam at the QR code
5. The app will automatically import the configuration settings

## Supported Connection Types

The QR code configuration supports all connection types available in the Warehouse Management Application:

- **DeviceCode**: Interactive authentication flow
- **UsernamePassword**: Username/password authentication
