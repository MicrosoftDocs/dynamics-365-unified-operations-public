---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 04/05/2023
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

Invoice capture officially supports the Integrated Power Platform environment. Before you can install the Invoice capture solution, set up the connection between the environment and the Microsoft Dynamics 365 Finance environment by completing the following prerequisites.

### Integrated Power Platform environment

1. In the Power Platform admin center, go to **Environment**, open the **Environment details** page, and find the environment URL.
2. Replace **\<Environment URL\>** in the following URL with the environment URL that you found, and open the "Finance and Operation Virtual Data Source configuration."

    `https://<Environment URL>/main.aspx?cmdbar=true&forceUCI=1&navbar=off&pagetype=entityrecord&etn=msdyn_financeandoperationsvirtualentity&id=47c40dcb-35d6-e911-a95e-000d3a110bbd`

3. Keep the existing entries.
4. Enter the finance and operations target URL, tenant ID, application ID, and application secret in the corresponding fields.

### Non-integrated Power Platform environment

For a non-integrated Power Platform environment, you must install the finance and operations virtual entity.

1. In the Power Platform admin center, go to **Resources \> Dynamics 365 apps**, and find "Finance and Operations Virtual Entity."
2. Select the environment, and accept the terms of service.
3. Select **Install** to install the finance and operations virtual entity in the selected environment.

> [!NOTE]
> Invoice capture is supported in version 10.0.31 and later of finance and operations apps.

## Install and set up the solution

Install the Invoice capture solution:

- Go to AppSource, and select the link for the preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). After the installation is completed, you will see the solution installed in the selected environment in Power Apps.

> [!NOTE]
> Go to **Setup system \> Manage legal entities**, and select **Manage vendors** to confirm that the entries in the list are synced from Finance.
