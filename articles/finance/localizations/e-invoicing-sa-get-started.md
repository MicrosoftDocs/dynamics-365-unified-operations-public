---
# required metadata

title: Get started with Electronic invoicing for Saudi Arabia
description: This topic provides information that will help you get started with Electronic invoicing for Saudi Arabia.
author: ikondo
ms.date: 10/26/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 574540
ms.assetid: 
ms.search.region: Saudi Arabia
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: AX 10.0.21

---

# Get started with Electronic invoicing for Saudi Arabia

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with Electronic invoicing for Saudi Arabia in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Services (RCS). These steps complement the steps that are described in [Get started with Electronic invoicing](e-invoicing-get-started.md).

### Prerequisites

Before you complete the procedure in this section, make sure that:

1. Virtual entities for Finance and Operations are configured in **Microsoft Dataverse**. See how to configure in [Configure Dataverse virtual entities](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference) article.
2. **CustomerPaymentMethodEntity** virtual entity is enabled. See how to enable in [Enable Microsoft Dataverse virtual entities](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-virtual-entities) article.
3. Dataverse endpoint is added as a connected application in the **RCS** instance.

## Country-specific configuration for the Saudi Arabian electronic invoice (SA) Electronic invoicing feature

Follow these steps before you deploy the application setup to your connected Finance or Supply Chain Management application.

This section complements the [Country-specific configuration of application setup](e-invoicing-get-started.md#country-specific-configuration-of-application-setup) section in the "Get started with Electronic invoicing" topic that was mentioned earlier.

1. In RCS, in the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing features** page, verify that the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that **PaymentMethodSubstitutionLookup** lookup is selected.
5. In the **Conditions** section, select **Add** to add a condition.
6. In the **Name** column for the new condition, select the method of payment that is defined in the application. Then, in the **Lookup result** column, select a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
7. Add specific conditions for each method of payment that is defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **Blank** or **Not blank** placeholder value instead of a specific method of payment.

8. On the **Setups** tab, click **Edit** for a selected configuration. 
9. In the **Processing pipeline** section, turn on the **Export result** option for the **Transform document** action.
10. Complete, publish, and deploy the **Saudi Arabian electronic invoice (SA)** feature to the service environment. For more information, see the [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment) section in the "Get started with Electronic invoicing" topic.
11. Deploy the **Saudi Arabian electronic invoice (SA)** feature to the connected application. For more information, see the [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application) section in the "Get started with Electronic invoicing" topic.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
