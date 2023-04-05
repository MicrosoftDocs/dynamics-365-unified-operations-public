---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 01/05/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Install the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> If you installed the solution in private preview, you must uninstall the old solution before you continue.

## Prerequisites

Before you can install the Invoice capture solution, you must complete the following prerequisites:

1. Register an application, and add a client secret to Microsoft Azure Active Directory (Azure AD) under your Azure subscription. For more information, see [Register a web application with AAD](../../dev-itpro/data-entities/services-home-page.md#register-a-web-application-with-aad).

    > [!NOTE]
    > Make a note of the **Application (client) ID**, **Client secret**, and **Tenant ID** values, because you will need them later.

2. Register the Azure application in a Dynamics 365 Finance environment. For more information, see [Register your external application](../../dev-itpro/data-entities/services-home-page.md#register-your-external-application).

>[!NOTE]
>Invoice capture is supported on Dynamics 365 finance and operations version 10.0.29 and later.

## Install and set up the solution

Install the Invoice capture solution:

1. Go to AppSource, and select the link for the preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). After the installation is completed, you will see the solution installed in the selected environment in Power Apps.

To complete the setup, follow these steps:  

1. Download the [assistant solution](https://github.com/InvoiceCapture/InstallationTools/releases/download/latest/msdyn_InvoiceCaptureIntallationTools.zip) to set up the following details:

    - The communication between Microsoft Power Platform and the Finance environment
    - The connection reference for Dataverse and Office 365 Outlook that will be used by the channel

2. In Power Apps, go to your environment, and select **Import solution**.
3. Select **Browse**, select the assistant solution package that you downloaded, and then select **Next**.
4. Select **Next**.
5. Assign an existing connection, or create a new one by selecting **New connection**.
6. After the package is successfully imported, open **Dynamics 365 Invoice capture – Installation Tools**.
7. Run the Cloud flow to set up the connection between the Invoice capture solution in Microsoft Power Platform and Finance.
8. Select **Run**, and specify the following parameters:

    - **Dynamics 365 Finance Url** – The URL of the Finance environment that you want to integrate with.
    - **Tenant ID** – The tenant ID for the Finance environment.
    - **Client ID** – The Azure application ID that was registered.
    - **Client Secret** – The client secret that was generated for the Azure application.

## Support 
IcM tickets are not currently the official channel for customer support. Send questions directly to daxaphelp@service.microsoft.com. 
