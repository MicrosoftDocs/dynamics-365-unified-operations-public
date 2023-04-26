---
title: Deploy payment connectors
description: This article describes how to deploy a payment connector package to the appropriate components.
author: ShalabhjainMSFT
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.industry: Retail
---

# Deploy payment connectors

[!include [banner](../includes/banner.md)]

## Overview

This article guides IT professionals or value-added resellers (VARs) through the process of deploying a payment connector to the appropriate components. We assume that the payment connector has been implemented and tested by the payment provider or the payment independent software vendor (ISV), and that it's ready for validation and subsequent production deployment in a customer environment.

This article doesn't include information about how to package a payment connector by using the Retail software development kit (SDK). For information about how to download the SDK, see [Retail software development kit (SDK) architecture](retail-sdk/retail-sdk-overview.md). For guidelines about how to package a payment connector, see the Retail SDK packaging document in the downloaded SDK.

This article also doesn't include information about how to deploy the payment web application, payment front-end processor, or payment back-end processor, because those applications are managed by payment providers or payment ISVs. If you're using Microsoft Dynamics AX 7.0 (February 2016), you must apply KB 3183058 before you create the Commerce deployable package.

## Payment packaging folder

A payment provider or a payment ISV creates a payment connector. The payment connector will include some or all of the following folders:

> [!NOTE]
> You can find these folders in \\RetailSDK\\PaymentExternals.

- **IPaymentProcessor Assemblies** – This folder contains the assembly that implements the IPaymentProcessor interface, and its dependent assemblies.
- **Payment Web Files** – This folder contains the callback HTML, JavaScript, or CSS files that are required in order to enable the payment accepting page. Payment connector developers will provide these web files if their payment accepting page requires them.
- **IPaymentDevice Assemblies** – This folder contains the assembly that implements the IPaymentDevice interface and payment request handlers, and the interface's dependent assemblies. These assemblies are used in Hardware Station and the Store Commerce app to communicate with payment terminal devices, such as VeriFone MX925. If you don't have a payment terminal device, you don't need these files.

To package the payment connector files, copy the payment assemblies to the folder in \\RetailSDK\\PaymentExternals. After the payment assemblies are copied, use **msbuild** from the root of the Retail SDK folder to generate the deployable packages. After the **msbuild** operation is completed, you can find the deployable package in \\RetailSDK\\Packages\\RetailDeployablePackage.

- **Retail deployable package** – This package includes payments plus all the other channel extension components. This is this combined package for all extension components. RetailDeployablePackage includes the payment connectors for the following components:
    
    - Commerce Scale Unit (CSU)
    - Self-service installer, which enables installation of the following:
        - Hardware Station
        - Store Commerce app
        - Commerce scale unit (self-hosted)

> [!NOTE]
> In releases earlier than 10.0.10, the RetailDeployablePackage can be deployed to both AOS and CSU. For later releases, the RetailDeployablePackage can be deployed only to CSU. To deploy the payment connector to AOS application version 10.0.10 and later, follow the information in [Create payment packaging for Application Explorer for self-service deployment](./payment-connector-package.md).

### Upload and deploy deployable packages

1. Open your LCS project page.
2. In the **More tools** section, click **Asset library**.
3. Select **Software package**, and then click the plus sign (**+**).
4. Enter a name and description, and select the correct package type, as described in the following table.

    | Deployable package                    | Deployable package type in LCS |
    |---------------------------------------|--------------------------------|
    | RetailDeployablePackage.zip               | Combined commerce package      |

5. Click **Upload**.
6. Select the zipped package, upload it, and then click **Confirm**.

After you've uploaded your deployable packages to the LCS asset library, you can deploy them to your environments through the LCS portal. After you've validated your deployment in your sandbox environment, you can create a service request to deploy it to your production environment. For more information, see [Apply a deployable package](../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md).

#### Download and run installers on client computers

The self-service package contains the installers for both Hardware Station and the Store Commerce app. After your deployable packages have been applied to your environment, you can download the updated Hardware Station and Store Commerce app installers. <!--For information about how to download Hardware Station and the Store Commerce app and install them on client computers, see [Configure, install, and activate the Store Commerce app](../retail-modern-pos-device-activation.md).-->

## Manual deployment

This section describes how to manually deploy a payment connector. You can use a manual deployment to test locally in a developer environment. This developer environment can be either cloud-hosted or on a downloadable virtual hard disk (VHD). These steps are not applicable for sandbox or production environments.

### Put the payment connector assemblies and files in the correct locations

Payment connectors are pluggable. In a development environment, you can put the correct files in the correct locations on the server. The following table shows which files should go in which location.

|  Connector | Contents of the IPaymentProcessor Assemblies folder | Contents of the Payment Web Files folder | Contents of the IPaymentDevice Assemblies folder |
|-----------|-----------------------------|------------------------------|---|
| Commerce Scale Unit                                                              | &lt;*RS.WebRoot*&gt;/bin/                                                 | Not applicable                           | Not applicable                                   |
| Store Commerce for web                                                                  | Not applicable                                                            | &lt;*CPOS.WebRoot*&gt;/Connectors/       | Not applicable                                   |
| Remote Hardware Station (Internet Information Services \[IIS\])            | &lt;*HWS.WebRoot*&gt;/bin/                                                | Not applicable                           | &lt;*HWS.WebRoot*&gt;/bin/                       |
| Store Commerce app Local Hard Station (Information Protection and Control \[IPC\]) | &lt;*MPOS.AppRoot*&gt;/ClientBroker/                                      | Not applicable                           | &lt;*MPOS.AppRoot*&gt;/ClientBroker/             |
| E-commerce                                                                 | Not applicable                                                            | &lt;*ECOM.WebRoot*&gt;/Connectors/       | Not applicable                                   |

Here is a key to the preceding table:

- &lt;*RS.WebRoot*&gt; is the web application root of Commerce Scale Unit.
- &lt;*HWS.WebRoot*&gt; is the web application root of a remote Hardware Station.
- &lt;*MPOS.AppRoot*&gt; is the app installation folder of Modern POS (for example, C:\\Program Files\\Microsoft Dynamics 365\\Store Commerce).
- &lt;*ECOM.WebRoot*&gt; is the web application root of an e-commerce website.

The Payment Web Files folder usually contains a subfolder. Be sure to copy the whole subfolder to the target locations.

## Use a payment connector with an e-commerce site

E-commerce sites aren't deployed in LCS-managed environments. You should work with your partner to decide how to host an e-commerce site. If the payment connector requires payment web files, you must deploy those web files to your e-commerce site. If your payment connector doesn't require payment web files, no additional steps are required. For information about how to deploy payment web files to an e-commerce site, see the [Put the payment connector assemblies and files in the correct locations](deploy-payment-connector.md#put-the-payment-connector-assemblies-and-files-in-the-correct-locations) section earlier in this article.

## Additional resources

[Guide to implementing a payment connector and a payment device](https://download.microsoft.com/download/e/2/7/e2735c65-1e66-4b8d-8a3c-e6ef3a319137/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device_update.pdf)

[Create deployable packages](retail-sdk/retail-sdk-packaging.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
