---
title: Read connection settings from a QR code
description: Learn how to generate and scan QR codes to quickly configure the Warehouse Management mobile app.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/02/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Read connection settings from a QR code

[!INCLUDE [banner](../includes/banner.md)]

The Warehouse Management mobile app supports QR code configuration to simplify the connection setup process. Instead of manually entering connection details, you can scan a QR code that contains all the required configuration information.

QR codes can contain connection configuration data in JavaScript Object Notation (JSON) format. Therefore, you can quickly deploy and set up the Warehouse Management app across multiple devices. This method is useful for IT administrators who must configure multiple devices. It's also useful when configurations must be shared with warehouse workers.

Other ways to deliver connection settings include your mobile device management (MDM) provider, a connection settings file, and manual entry on the device. To compare them, see [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute).

## Supported connection types

The feature for QR code–based connection configuration supports all connection types that the Warehouse Management mobile app supports:

- **UsernamePassword** (recommended) – Username/password authentication. The examples in this article use this connection type.
- **DeviceCode** (not recommended) – Interactive [device code flow](warehouse-app-authenticate-user-based.md#deviceCodeFlow) authentication.

> [!IMPORTANT]
> Specify `"UsernamePassword"` in the QR codes that you generate. A QR code can still specify `"ConnectionType": "DeviceCode"`, but that flow is blocked by default in new tenants, so the code might not work. Learn more in [Device code flow authentication](warehouse-app-authenticate-user-based.md#deviceCodeFlow).

> [!NOTE]
> The examples in this article omit the optional `"UseBroker"` parameter, because you don't need to set it. Learn more in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr).

## Step 1: Prepare your configuration JSON code

Create a JSON configuration that includes your connection details. Follow the instructions in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr). The JSON code should have the following structure.

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://yourenvironment1.cloudax.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "AuthCloud": "AzureGlobal"
        }
    ]
}
```

## Step 2: Generate a QR code

There are several ways to generate a QR code. Use the method that best suits your needs.

### Option 1: Use Copilot

Follow these steps to ask Copilot to generate a QR code for your JSON configuration.

1. Open a Copilot chat session. For example, select the **Copilot** button in Microsoft Edge, or open Microsoft Copilot from the Windows taskbar.
1. Enter a prompt that resembles the following example, but that includes your specific JSON configuration.

    ```text
    Please generate a QR code for the following JSON configuration:
    {
        "ConnectionList": [
            {
                "ConnectionName": "Production",
                "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
                "Company": "USMF",
                "ConnectionType": "UsernamePassword",
                "AuthCloud": "AzureGlobal"
            }
        ]
    }
    ```

1. Copilot generates a QR code image based on the JSON configuration that you provided. Download the image to your device. For example, select and hold (or right-click) the image, and then select to download it. Alternatively, use a drag-and-drop operation.

### Option 2: Use an online QR code generator

To generate a QR code by using an online QR code generator, follow these steps:

1. Visit any reputable QR code generator website. Bing can help you find one.
1. Select *Text* or *JSON* format.
1. Paste the complete JSON configuration that you prepared.
1. Generate and download the QR code image.

### Option 3: Use PowerShell

You can use PowerShell to generate a QR code from your JSON configuration. The code resembles the following example, but it includes your specific JSON configuration.

```powershell
# Install and import QR code module if not already installed
Install-Module -Name QRCodeGenerator
Import-Module QRCodeGenerator

# Your JSON configuration
$jsonConfig = @"
{
    "ConnectionList": [
        {
            "ConnectionName": "Production",
            "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "AuthCloud": "AzureGlobal"
        }
    ]
}
"@

# Generate QR Code
New-QRCodeText $jsonConfig -OutPath "warehouse-config.png"
```

## Step 3: Distribute the QR code

After you generate the required QR code, distribute it in any of the following ways:

- Print it for physical distribution.
- Share it digitally via email or collaboration platforms.
- Display it on-screen for easy scanning.
- Include it in documentation or setup guides.

> [!IMPORTANT]
> QR codes contain connection configuration data, which might include tenant IDs and environment URLs. Treat QR codes as sensitive information and distribute them only through secure channels. Avoid posting them in publicly accessible locations.

> [!TIP]
> Copilot can decode a QR code if you enter a prompt such as "Please decode this QR code" and attach the image. This technique can be useful if you want to verify the contents of a QR code before you distribute it.

## Step 4: Scan the QR code on each device

To use the generated QR code to configure a device, follow the steps in [Import the connection settings on a device](install-configure-warehouse-management-app.md#config).
