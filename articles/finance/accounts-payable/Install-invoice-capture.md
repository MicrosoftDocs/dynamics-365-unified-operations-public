---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution with integration to Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 09/25/2022
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

Prerequisites for installing Invoice capture solution:
a)	Register an application and add a client secret to Azure Active Directory (Azure AD) under your Azure subscription. For more information, see [Register a web application with AAD](../../dev-itpro/data-entities/services-home-page.md#register-a-web-application-with-aad). 

>[!NOTE] 
> You will want to note the **Application (client) ID**, **Client secret**, and **Tenant ID** values. These values will be needed later.

b)	Register the Azure application in a Dynamics 365 Finance environment. For more information, see [Register your external application](../../dev-itpro/data-entities/services-home-page.md#register-your-external-application).

## Install and set up

Go to AppSource and select the link for preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). 
Once the installation is completed, you'll see the solution installed in selected environment in Power Apps.

Download the [assistant solution](https://github.com/InvoiceCapture/InstallationTools/releases/download/latest/msdyn_InvoiceCaptureIntallationTools.zip) to set up the following:

-	Set up the communication between Power Platform and Dynamics 365 Finance environment
-	Set up connection reference for Dataverse and Office 365 Outlook that will be used by the channel

To complete the setup, follow these steps:

1.	In Power Apps, go to your environment, and select **Import solution**.
2.	Click **Browse**, select the solution package provided and click **Next**.
3.	Click **Next**.
4.	Assign an existing connection or create a new one by clicking **+New connection**.
5.	After successful import, open **Dynamics 365 Invoice capture – Installation Tools**.
6.	Run the Cloud flow to set up the connection between **Invoice capture** in Power Platform and Dynamics 365 Finance. 
7.	Click **Run** with the parameters below:
    •	**Dynamics 365 Finance Url**: URL for Dynamics 365 Finance environment, which you want to integrate with.  
    •	**Tenant ID**: The tenant ID for the Dynamics 365 Finance environment.
    •	**Client ID**: the Azure application ID that was registered.
    •	**Client Secret**: the client secret that was generated for the Azure application.


