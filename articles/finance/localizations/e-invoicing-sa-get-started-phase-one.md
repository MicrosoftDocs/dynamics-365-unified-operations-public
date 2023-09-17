---

# required metadata
title: Get started with Electronic invoicing for Saudi Arabia - Phase one
description: This article provides information that will help you get started with phase one of Electronic invoicing for Saudi Arabia.
author: gionoder
ms.author: gionoder
ms.audience: Application User
ms.reviewer: kfend
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 11/28/2022
ms.custom: bap-template

---

# Get started with Electronic invoicing for Saudi Arabia - Phase one

[!include [banner](../includes/banner.md)]

This article provides information that will help you get started with phase one of Electronic invoicing for Saudi Arabia in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. This article guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS). These steps complement the steps that are described in [Get started with Electronic invoicing](e-invoicing-get-started.md).

### Prerequisites

Before you complete the steps in this article, the following prerequisites must be met: 

- Import the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature into RCS from the Global repository. For more information, see [Import an Electronic invoicing feature from the Microsoft configuration provider](e-invoicing-get-started.md#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider).
- In Dataverse, configure virtual entities for Finance and Supply Chain Management. For more information, see [Configure Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md).
- Enable the **CustomerPaymentMethodEntity** virtual entity. For more information, see [Enable Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).
- Add the Dataverse endpoint as a connected application in the RCS instance. For more information, see [Create a connected application](e-invoicing-get-started-service-administration.md#create-a-connected-application).
- Taxpayers and their software for e-invoicing must be onboarded by Saudi Arabian tax authorities. For more information about the onboarding process, see [Electronic invoicing onboarding in Saudi Arabia](e-invoicing-sa-onboarding.md).

## Country/region-specific configuration for the Saudi Arabian electronic invoice (SA) Electronic invoicing feature

Before you deploy the application setup to your connected Finance or Supply Chain Management application, complete the following procedure.

This section complements the [Country/region-specific configuration of application setup](e-invoicing-get-started.md#country-specific-configuration-of-application-setup) section of the "Get started with Electronic invoicing" article.

1. In RCS, in the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing features** page, verify that the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that the **PaymentMethodSubstitutionLookup** lookup is selected.
5. In the **Conditions** section, select **Add** to add a condition.
6. In the **Name** column for the new condition, select the method of payment that's defined in the application. Then, in the **Lookup result** column, select a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
7. Add specific conditions for each method of payment that's defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **&ast;Blank&ast;** or **&ast;Not blank&ast;** placeholder value instead of a specific method of payment.

8. On the **Setups** tab, select **Edit** for the selected configuration.
9. In the **Processing pipeline** section, turn on the **Export result** option for the **Transform document** action.
10. Complete, publish, and deploy the **Saudi Arabian electronic invoice (SA)** feature to the service environment. For more information, see [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment).
11. Deploy the **Saudi Arabian electronic invoice (SA)** feature to the connected application. For more information, see [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application).

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
