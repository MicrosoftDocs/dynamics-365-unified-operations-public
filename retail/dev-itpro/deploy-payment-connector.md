---
# required metadata

title: Deploy a payment connector
description: This topic describes how to deploy a payment connector package to the appropriate components. 
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: aamiral
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Deploy a payment connector

[!include[banner](../includes/banner.md)]


Overview
--------

This topic guides retail IT professionals or value-added resellers (VARs) through the process of deploying a payment connector to the appropriate components. We assume that the payment connector has been implemented and tested by the payment provider or the payment independent software vendor (ISV), and that it's ready for validation and subsequent production deployment in a customer environment. This topic doesn't include information about how to package a payment connector by using the Retail software development kit (SDK). See the [Retail SDK overview](retail-sdk/retail-sdk-overview.md) for information about how to download the SDK. For guidelines about how to package a payment connector, within the downloaded SDK, review the Retail SDK Handbook section on Adding a payment connector, which became available in the SDK in hotfix KB 3183058. This topic also doesn't include information about how to deploy the payment web application, payment front-end processor, or back-end processor, because those applications are managed by payment providers or payment ISVs.

## Before you begin
A payment provider or a payment ISV creates a payment connector. The payment connector will include some or all of the following folders:

-   **IPaymentProcessor Assemblies** – This folder contains the assembly that implements the IPaymentProcesor interface, and its dependent assemblies.
-   **Payment Web Files** – This folder contains the callback HTML, JavaScript, or CSS files that are required in order to enable the payment accepting page. Payment connector developers will provide these web files if their payment accepting page requires them.
-   **IPaymentDevice Assemblies** – This folder contains the assembly that implements the IPaymentDevice interface, and its dependent assemblies. These assemblies are used in Retail Hardware station and Retail Modern Point of Sale (Modern POS) to communicate with payment terminal devices, such as VeriFone MX925. If you don’t have a payment terminal device, you don't need these files.

To package the payment connector files that a payment provider or payment ISV provides, you must uptake hotfix KB 3183058 (or later) for the Retail SDK. After you build the Retail SDK, you will obtain the following deployable packages:

-   Application Object Server (AOS) payment package
-   Retail deployable package

Before you start, you must have these items:

-   Payment connector files
-   KB 3183058 for the Retail SDK
-   Deployable packages that are built by using the Retail SDK (see the list earlier in this topic)
-   Access to your cloud-hosted environment on Microsoft Dynamics Lifecycle Service (LCS)

## Deployable packages (automated deployment)
A deployable package is an asset that can be consumed by the LCS deployment service. When you package a payment connector as a deployable package, you can install the payment connector as a customization to an existing solution or slipstream it as part of a new deployment. The following types of packages can contain payment connectors:

-   **AOSPaymentPackage** – This type of package deploys one or more payment connectors to AOS.
-   **RetailDeployablePackage** – This type of package deploys one or more payment connectors to the following components:
.    -   Retail Server
    -   Cloud POS
    -   Self-service installer, which enables installation of the following:
        -   Hardware station
        -   Modern POS

### Upload and deploy deployable packages

1.  Open your LCS project page.
2.  In the **More tools** section, click **Asset library**.
3.  Select **Software package**, and then click the plus sign (**+**).
4.  Enter a name and description, and select the correct package type, as described in the following table.
    | Deployable package      | Deployable package type in LCS |
    |-------------------------|--------------------------------|
    | AOSPaymentPackage       | Binary hotfix                  |
    | RetailDeployablePackage | Combined retail package        |

5.  Click **Upload**.
6.  Select the zipped package, upload it, and then click **Confirm**.

After you've uploaded your deployable packages to the LCS asset library, you can deploy them to your environments through the LCS portal. After you've validated your deployment in your sandbox environment, you can create a service request to deploy it to your production environment. For more information, see [Apply a deployable package](/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system).

#### Download and run installers on client computers

The self-service package contains the installers for both Hardware station and Modern POS. After your deployable packages have been applied to your environment, you can download the updated Hardware station and Modern POS installers. For information about how to download Hardware station and Modern POS, and install them on client computers, see [Retail Modern POS self-service download/installation, and device activation of Modern POS and Cloud POS](../retail-modern-pos-device-activation.md).

## Manual deployment
This section describes how to manually deploy a payment connector. You can use a manual deployment to test locally in a developer environment. This developer environment can be either cloud-hosted or on a downloadable virtual hard disk (VHD).

### Put the payment connector assemblies and files in the correct locations

Payment connectors are pluggable. In a development environment, you can put the correct files in the correct locations on the server. The following table shows which files should go in which location.

|                                                                            | Contents of the IPaymentProcessor Assemblies folder                       | Contents of the Payment Web Files folder | Contents of the IPaymentDevice Assemblies folder |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------|
| Application Object Server (AOS)                                            | &lt;*Aos.PackageDirectory*&gt;/bin/Connectors/ &lt;*Aos.WebRoot*&gt;/bin/ | &lt;*Aos.WebRoot*&gt;/Connectors/        | Not applicable                                   |
| Retail Server                                                              | &lt;*RS.WebRoot*&gt;/bin/                                                 | Not applicable                           | Not applicable                                   |
| Cloud POS                                                                  | Not applicable                                                            | &lt;*CPOS.WebRoot*&gt;/Connectors/       | Not applicable                                   |
| Remote Hardware Station (Internet Information Services \[IIS\])            | &lt;*HWS.WebRoot*&gt;/bin/                                                | Not applicable                           | &lt;*HWS.WebRoot*&gt;/bin/                       |
| Modern POS Local Hard Station (Information Protection and Control \[IPC\]) | &lt;*MPOS.AppRoot*&gt;/ClientBroker/                                      | Not applicable                           | &lt;*MPOS.AppRoot*&gt;/ClientBroker/             |
| E-commerce                                                                 | Not applicable                                                            | &lt;*ECOM.WebRoot*&gt;/Connectors/       | Not applicable                                   |

Here is a key to the preceding table:

-   &lt;*Aos.PackageDirectory*&gt; is the package directory of AOS. You can find the path from the web.config file for AOS (key = **Aos.PackageDirectory**).
-   &lt;*Aos.WebRoot*&gt; is the web application root of AOS.
-   &lt;*RS.WebRoot*&gt; is the web application root of Retail Server.
-   &lt;*HWS.WebRoot*&gt; is the web application root of a remote Hardware Station.
-   &lt;*MPOS.AppRoot*&gt; is the app installation folder of Modern POS (for example, C:\\Program Files (x86)\\Microsoft Dynamics AX70\\Retail Modern POS).
-   &lt;*ECOM.WebRoot*&gt; is the web application root of an e-commerce website.

The Payment Web Files folder usually contains a subfolder. Be sure to copy the whole subfolder to the target locations.

## Use a payment connector with an ecommerce site
E-commerce sites aren't deployed in LCS-managed environments. You should work with your partner to decide how to host an e-commerce site. If the payment connector requires payment web files, you must deploy those web files to your e-commerce site. If your payment connector doesn't require payment web files, no additional steps are required. For information about how to deploy payment web files to an e-commerce site, see the "Put the payment connector assemblies and files in the correct locations" section earlier in this article.

See also
--------

[Guide to implementing a payment connector and a payment device](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx)

[Retail SDK packaging](retail-sdk/retail-sdk-packaging.md)



