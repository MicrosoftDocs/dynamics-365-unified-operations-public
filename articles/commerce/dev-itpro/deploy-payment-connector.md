---
# required metadata

title: Deploy payment connectors
description: This topic describes how to deploy a payment connector package to the appropriate components. 
author: aamirallaqaband
manager: AnnBe
ms.date: 05/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: aamiral
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Deploy payment connectors

[!include [banner](../includes/banner.md)]

Overview
--------

This topic guides IT professionals or value-added resellers (VARs) through the process of deploying a payment connector to the appropriate components. We assume that the payment connector has been implemented and tested by the payment provider or the payment independent software vendor (ISV), and that it's ready for validation and subsequent production deployment in a customer environment.

This topic doesn't include information about how to package a payment connector by using the Retail software development kit (SDK). For information about how to download the SDK, see [Retail software development kit (SDK) architecture](retail-sdk/retail-sdk-overview.md). For guidelines about how to package a payment connector, see the Retail SDK packaging document in the downloaded SDK. 

This topic also doesn't include information about how to deploy the payment web application, payment front-end processor, or payment back-end processor, because those applications are managed by payment providers or payment ISVs. If you're using Microsoft Dynamics AX 7.0 (February 2016), you must apply KB 3183058 before you create the Commerce deployable package.

## Payment packaging folder
A payment provider or a payment ISV creates a payment connector. The payment connector will include some or all of the following folders:

> [!NOTE]
> You can find these folders in ...\\RetailSDK\\PaymentExternals.

-   **IPaymentProcessor Assemblies** – This folder contains the assembly that implements the IPaymentProcessor interface, and its dependent assemblies.
-   **Payment Web Files** – This folder contains the callback HTML, JavaScript, or CSS files that are required in order to enable the payment accepting page. Payment connector developers will provide these web files if their payment accepting page requires them.
-   **IPaymentDevice Assemblies** – This folder contains the assembly that implements the IPaymentDevice interface and payment request handlers, and the interface's dependent assemblies. These assemblies are used in Hardware station and Modern Point of Sale (Modern POS) to communicate with payment terminal devices, such as VeriFone MX925. If you don't have a payment terminal device, you don't need these files.

To package the payment connector files, the payment provider or payment ISV must copy the payment assemblies to the correct folder in ...\\RetailSDK\\PaymentExternals. After the payment assemblies are copied, use **msbuild** from the root of the Retail SDK folder to generate the deployable packages. After the **msbuild** operation is completed, you can find the following deployable package in ...\\RetailSDK\\Packages\\RetailDeployablePackage. In versions that are earlier than AX 7.0, the deployable package will be in \\RetailSDK\\Packages\\.

-   **Application Object Server (AOS) payment package** – ***The AOS payment package is obsolete and is no longer supported. If you upload the AOS payment package to Microsoft Dynamics Lifecycle Service (LCS), you will receive an unsupported package error. Use the new Commerce deployable package instead.*** If you're using AX 7.0, apply the latest binary hotfix before you generate the package.

    > [!NOTE]
    > In newer versions, we won't generate an AOS payment package.

-   **Commerce deployable package** – This package includes payment plus all the other channel components. This package is this combined package for all extension components.

Before you start, you must have these items:

-   Payment connector files
-   Commerce deployable packages that are built by using the Retail SDK (see the list earlier in this topic)
-   Access to your cloud-hosted environment on LCS

## Commerce deployable packages (automated deployment)
A Commerce deployable package is an asset that can be consumed by the LCS deployment service. When you package a payment connector and other extensions as a deployable package, you can either install the payment connector as a customization to an existing solution or slipstream it as part of a new deployment. The following types of packages can contain payment connectors:

-   **AOSPaymentPackage** – This type of package deploys one or more payment connectors to AOS. (**The AOS payment package is obsolete and is no longer supported.**)

-   **RetailDeployablePackage** – This type of package deploys one or more payment connectors to the following components:

    -   Commerce Scale Unit, Commerce runtime, and database scripts
    -   Cloud POS
    -   Self-service installer, which enables installation of the following:

        -   Hardware station
        -   Modern POS

### Upload and deploy deployable packages

1.  Open your LCS project page.
2.  In the **More tools** section, click **Asset library**.
3.  Select **Software package**, and then click the plus sign (**+**).
4.  Enter a name and description, and select the correct package type, as described in the following table.

    | Deployable package                    | Deployable package type in LCS |
    |---------------------------------------|--------------------------------|
    | AOSPaymentPackage (**Not supported**) | Binary hotfix                  |
    | RetailDeployablePackage               | Combined commerce package        |

5.  Click **Upload**.
6.  Select the zipped package, upload it, and then click **Confirm**.

After you've uploaded your deployable packages to the LCS asset library, you can deploy them to your environments through the LCS portal. After you've validated your deployment in your sandbox environment, you can create a service request to deploy it to your production environment. For more information, see [Apply a deployable package](../../dev-itpro/deployment/apply-deployable-package-system.md).

#### Download and run installers on client computers

The self-service package contains the installers for both Hardware station and Modern POS. After your deployable packages have been applied to your environment, you can download the updated Hardware station and Modern POS installers. For information about how to download Hardware station and Modern POS, and install them on client computers, see [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md).

## Manual deployment
This section describes how to manually deploy a payment connector. You can use a manual deployment to test locally in a developer environment. This developer environment can be either cloud-hosted or on a downloadable virtual hard disk (VHD).

### Put the payment connector assemblies and files in the correct locations

Payment connectors are pluggable. In a development environment, you can put the correct files in the correct locations on the server. The following table shows which files should go in which location.

|                                                                            | Contents of the IPaymentProcessor Assemblies folder                       | Contents of the Payment Web Files folder | Contents of the IPaymentDevice Assemblies folder |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------|
| Application Object Server (AOS)                                            | &lt;*Aos.PackageDirectory*&gt;/bin/Connectors/ &lt;*Aos.WebRoot*&gt;/bin/ | &lt;*Aos.WebRoot*&gt;/Connectors/        | Not applicable                                   |
| Commerce Scale Unit                                                              | &lt;*RS.WebRoot*&gt;/bin/                                                 | Not applicable                           | Not applicable                                   |
| Cloud POS                                                                  | Not applicable                                                            | &lt;*CPOS.WebRoot*&gt;/Connectors/       | Not applicable                                   |
| Remote Hardware Station (Internet Information Services \[IIS\])            | &lt;*HWS.WebRoot*&gt;/bin/                                                | Not applicable                           | &lt;*HWS.WebRoot*&gt;/bin/                       |
| Modern POS Local Hard Station (Information Protection and Control \[IPC\]) | &lt;*MPOS.AppRoot*&gt;/ClientBroker/                                      | Not applicable                           | &lt;*MPOS.AppRoot*&gt;/ClientBroker/             |
| E-commerce                                                                 | Not applicable                                                            | &lt;*ECOM.WebRoot*&gt;/Connectors/       | Not applicable                                   |

Here is a key to the preceding table:

-   &lt;*Aos.PackageDirectory*&gt; is the package directory of AOS. You can find the path from the web.config file for AOS (key = **Aos.PackageDirectory**).
-   &lt;*Aos.WebRoot*&gt; is the web application root of AOS.
-   &lt;*RS.WebRoot*&gt; is the web application root of Commerce Scale Unit.
-   &lt;*HWS.WebRoot*&gt; is the web application root of a remote Hardware Station.
-   &lt;*MPOS.AppRoot*&gt; is the app installation folder of Modern POS (for example, C:\\Program Files (x86)\\Microsoft Dynamics AX70\\Retail Modern POS).
-   &lt;*ECOM.WebRoot*&gt; is the web application root of an e-commerce website.

The Payment Web Files folder usually contains a subfolder. Be sure to copy the whole subfolder to the target locations.

## Use a payment connector with an e-commerce site
E-commerce sites aren't deployed in LCS-managed environments. You should work with your partner to decide how to host an e-commerce site. If the payment connector requires payment web files, you must deploy those web files to your e-commerce site. If your payment connector doesn't require payment web files, no additional steps are required. For information about how to deploy payment web files to an e-commerce site, see the [Put the payment connector assemblies and files in the correct locations](deploy-payment-connector.md#put-the-payment-connector-assemblies-and-files-in-the-correct-locations) section earlier in this topic.

Additional resources
--------

[Guide to implementing a payment connector and a payment device](https://download.microsoft.com/download/e/2/7/e2735c65-1e66-4b8d-8a3c-e6ef3a319137/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device_update.pdf)

[Create retail deployable packages](retail-sdk/retail-sdk-packaging.md)
