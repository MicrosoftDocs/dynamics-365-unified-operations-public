---
title: Import connection settings from a QR code
description: Learn how to generate and scan connection setup QR codes to import JSON settings into the Warehouse Management mobile app.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/29/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Import connection settings from a QR code

[!INCLUDE [banner](../includes/banner.md)]

A *connection setup QR code* contains Warehouse Management mobile app settings in JavaScript Object Notation (JSON) format. Scan it to import the environment URL, company, and authentication preferences instead of entering them manually. You can use the same code to configure multiple devices.

> [!NOTE]
> *Connection setup isn't authentication.* To set up the connection on Android, iOS/iPadOS, or Windows, scan a *connection setup QR code* in the Warehouse Management mobile app by going to **Connection setup** > **Add from QR code**. Setting up the connection isn't the same as authenticating (signing in). On Android and iOS/iPadOS only, workers can authenticate by using a different *sign-in QR code* on the Microsoft Entra ID sign-in page and enter the worker's PIN. Learn more in [QR code and PIN sign-in for the Warehouse Management mobile app](warehouse-app-authenticate-qr-code.md).

Other ways to deliver connection settings include your mobile device management (MDM) provider, a connection settings file, and manual entry on the device. To compare them, see [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute).

## Supported connection types

A connection setup QR code can configure any connection type supported by the app. The connection type determines how the worker signs in after import:

- **UsernamePassword** (recommended) – Username/password authentication. The examples in this article use this connection type.
- **DeviceCode** (not recommended) – Interactive [device code flow](warehouse-app-authenticate-user-based.md#deviceCodeFlow) authentication.

> [!IMPORTANT]
> Specify `"UsernamePassword"` in the connection setup QR codes that you generate. A code can still specify `"ConnectionType": "DeviceCode"`, but that flow is blocked by default in new tenants, so sign-in might fail after import. Learn more in [Device code flow authentication](warehouse-app-authenticate-user-based.md#deviceCodeFlow).

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

To import a connection setup QR code, follow the instructions in [Import the connection settings on a device](install-configure-warehouse-management-app.md#config). Use **Add from QR code**, not the Microsoft Entra ID sign-in page. The worker signs in separately after the settings are imported.
