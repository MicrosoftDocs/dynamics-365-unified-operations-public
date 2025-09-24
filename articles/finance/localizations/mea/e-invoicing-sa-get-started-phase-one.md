---
title: Get started with electronic invoicing for Saudi Arabia - Phase one
description: Learn how to get started with phase one of electronic invoicing for Saudi Arabia in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 06/05/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Get started with electronic invoicing for Saudi Arabia - Phase one

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with phase one of electronic invoicing for Saudi Arabia in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. This article guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS). These steps complement the steps that are described in [Get started with electronic invoicing](../e-invoicing-get-started.md).

### Prerequisites

Before you complete the steps in this article, the following prerequisites must be met: 

- Import the **Saudi Arabian electronic invoice (SA)** electronic invoicing feature into RCS from the Global repository. For more information, see [Import an electronic invoicing feature from the Microsoft configuration provider](../e-invoicing-get-started.md#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider).
- In Dataverse, configure virtual entities for Finance and Supply Chain Management. For more information, see [Configure Dataverse virtual entities](../../../fin-ops-core/dev-itpro/power-platform/admin-reference.md).
- Enable the **CustomerPaymentMethodEntity** virtual entity. For more information, see [Enable Microsoft Dataverse virtual entities](../../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).
- Add the Dataverse endpoint as a connected application in the RCS instance. For more information, see [Create a connected application](../e-invoicing-get-started-service-administration.md#create-a-connected-application).

## Country/region-specific configuration for the Saudi Arabian electronic invoice (SA) electronic invoicing feature

Before you deploy the application setup to your connected Finance or Supply Chain Management application, complete the following procedure.

This section complements the [Country/region-specific configuration of application setup](../e-invoicing-get-started.md#country-specific-configuration-of-application-setup) section of the "Get started with electronic invoicing" article.

To configure the Saudi Arabian electronic invoice (SA) electronic invoicing feature, follow these steps.

1. In RCS, in the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
1. On the **Electronic invoicing features** page, verify that the **Saudi Arabian electronic invoice (SA)** electronic invoicing feature is selected.
1. On the **Versions** tab, verify that the **Draft** version is selected.
1. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that the **PaymentMethodSubstitutionLookup** lookup is selected.
1. In the **Conditions** section, select **Add** to add a condition.
1. In the **Name** column for the new condition, select the method of payment that's defined in the application. Then, in the **Lookup result** column, select a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
1. Add specific conditions for each method of payment that's defined in the system, and save your changes.

    > [!NOTE]
    > In the **Name** column, you can select the **&ast;Blank&ast;** or **&ast;Not blank&ast;** placeholder value instead of a specific method of payment.

1. On the **Setups** tab, select **Edit** for the selected configuration.
1. In the **Processing pipeline** section, turn on the **Export result** option for the **Transform document** action.
1. Complete, publish, and deploy the **Saudi Arabian electronic invoice (SA)** feature to the service environment. For more information, see [Deploy the electronic invoicing feature to Service environment](../e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment).
1. Deploy the **Saudi Arabian electronic invoice (SA)** feature to the connected application. For more information, see [Deploy the electronic invoicing feature to Connected application](../e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application).

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with electronic invoicing](../e-invoicing-get-started.md)
- [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
