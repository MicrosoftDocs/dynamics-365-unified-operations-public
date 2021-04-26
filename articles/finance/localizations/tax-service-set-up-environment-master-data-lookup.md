---
# required metadata

title: Set up an environment for master data lookup
description: This topic explains how to set up your environment to use the Tax Calculation master data lookup functionality.
author: kai-cloud
ms.date: 04/21/2021
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

# Set up an environment for master data lookup

[!include [banner](../includes/banner.md)]

This topic explains how to set up your environment to use the Tax Calculation master data lookup functionality.

1. Set up power platform integration in Lifecycle Services (LCS). For more information, see [Microsoft Power Platform integration - Add-ins overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md).
2. Set up Dynamics 365 Finance and Microsoft Dataverse. For more information, see [Getting the solution](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#getting-the-solution) and [Authentication and authorization](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#authentication-and-authorization).
3. Set up the following entities. For more information, see [Enabling virtual entities](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#enabling-virtual-entities).
      - CompanyInfoEntity
      - CurrencyEntity
      - CustCustomerV3Entity
      - DeliveryTermsEntity
      - EcoResProductCategoryEntity
      - EcoResReleasedProductV2Entity
      - LogisticsAddressCityEntity
      - LogisticsAddressCountryRegionTranslationEntity
      - LogisticsAddressStateEntity
      - PurchProcurementChargeCDSEntity
      - SalesChargeCDSEntity
      - TaxGroupEntity
      - TaxItemGroupHeadingEntity
      - VendVendorV2Entity
4. Set up the Dynamics 365 Regulatory Configuration Service (RCS). 
5. Create a service request for Microsoft to enable flighting of the following features:

      - ERCdsFeature
      - TaxServiceCDSFeature

6. Go to the **Feature management** workspace, and enable the following features:

      - (Preview) Electronic reporting Dataverse datasources support
      - (Preview) Tax Service Dataverse datasources support
      - (Preview) Globalization features

5. Sign in to RCS using a tenant admin account.
6. Go to **Electronic reporting** > **Connected applications**. 
7. Select **New** to add a record, and enter the following field information. 

   - In the **Name** field, enter a name.
   - In the **Type** field, select **Dataverse**.
   - In the **Application** field, enter your Dataverse URL.
   - In the **Tenant** field, enter your tenant.
   - In the **Custom URL** field, enter your Dataverse URL and append it with "/api/data/v9.1".

8. Select **Check connection**, and finish the connection process. 

   [![Check connection button](./media/tax-service-setup-environment-for-mater-date-pic1.png)](./media/tax-service-setup-environment-for-mater-date-pic1.png)

9. Go to **Electronic reporting** > **Tax configurations**, and import tax configurations from [Tax configurations](https://go.microsoft.com/fwlink/?linkid=2158352).

   [![Tax configurations page, Tax data model tree](./media/tax-service-setup-environment-for-mater-date-pic2.png)](./media/tax-service-setup-environment-for-mater-date-pic2.png)

10. Go to the **Taxable document model mapping**, or **Dataverse Model Mapping** if you are using a Microsoft configuration, and in the **Connected application** field, select the record that you created in step 7.
11. Set **Default for model mapping** to **Yes**.

   [![Model mapping page](./media/tax-service-setup-environment-for-mater-date-pic3.png)](./media/tax-service-setup-environment-for-mater-date-pic3.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
