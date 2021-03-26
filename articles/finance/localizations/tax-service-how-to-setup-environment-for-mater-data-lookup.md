---
# required metadata

title: GST on bank charges
description: This document will help you learn how to extend tax configurations to GST on bank charges.
author: kfend
manager: beya
ms.date: 02/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: pashao
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18
---



# How to setup environment for mater data lookup

[!include [banner](../includes/banner.md)]

This topic provides information about environment setup for the mater data lookup functionality of the tax calculation add-in.

1. **Setup power platform integration in LCS (Lifecycle Services)**

   Follow the steps in [Microsoft Power Platform integration - Add-ins overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/add-ins-overview).

2. **Setup F&O and Dataverse**

   Follow the [Getting the solution](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#getting-the-solution) and [Authentication and authorization](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#authentication-and-authorization) steps in [Finance and Operations and Dataverse admin reference](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference) to setup F&O and Dataverse.

3. **Import prerequisite tax service virtual entity solution** 

   Get the solution from [Tax service virtual entity](https://go.microsoft.com/fwlink/?linkid=2158160).

4. **Setup RCS (Regulatory Configuration Service)**

   Contact your Microsoft solution architect to enable following flighting in RCS.

   - ERCdsFeature
   - TaxServiceCDSFeature

   Enable following features in **Feature management**

   - (Preview) Electronic reporting Dataverse datasources support
   - (Preview) Tax Service Dataverse datasources support
   - (Preview) Globalization features

5. **Register a connected application**

   Login to RCS by admin account of your tenant. Go to **Electronic reporting -> Connected applications**. Click **New** to add a record. 

   - In **Name** field, type in a name.
   - In **Type** field, choose Dataverse.
   - In **Application** field, type in your Dataverse URL.
   - In **Tenant** field, type in your tenant.
   - In **Custom URL** field, type in your Dataverse URL appended with "/api/data/v9.1".

   Click **Check connection**, and finish the connection process. 

   [![Direct taxes (tab)](./media/tax-service-setup-environment-for-mater-date-pic1.png)](./media/tax-service-setup-environment-for-mater-date-pic1.png)

6. **Setup tax configuration**

   Go to **Electronic reporting -> Tax configurations**, import tax configurations from [Tax configurations](https://go.microsoft.com/fwlink/?linkid=2158352).

   [![Direct taxes (tab)](./media/tax-service-setup-environment-for-mater-date-pic2.png)](./media/tax-service-setup-environment-for-mater-date-pic2.png)

   Go to Taxable document model mapping (if you use Microsoft configuration, it would be **Dataverse Model Mapping**), set **Connected application** as the one you created above and set the configuration as **Default for model mapping**.

   [![Direct taxes (tab)](./media/tax-service-setup-environment-for-mater-date-pic3.png)](./media/tax-service-setup-environment-for-mater-date-pic3.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]