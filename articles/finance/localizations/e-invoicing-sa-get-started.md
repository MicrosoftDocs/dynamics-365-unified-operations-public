---
# required metadata

title: Get started with Electronic invoicing for Saudi Arabia
description: This topic provides information to get started with Electronic invoicing for Saudi Arabia.
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

This topic provides information that will help you get started with Electronic invoicing for Saudi Arabia in Dynamics 365 Finance and Dynamics 365 Supply Chain Management. The topic guides you through the configuration steps that are country-dependent in Regulatory Configuration Services (RCS), and complement the steps described in the topic, [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country-specific configuration for the Saudi Arabian electronic invoice (SA) Electronic invoicing feature

Complete the following steps before you deploy the Application setup to your Finance or Supply Chain Management Connected application.

This section complements the [Country-specific configuration of application setup](e-invoicing-get-started.md#country-specific-configuration-of-application-setup) section in the topic, **Get started with Electronic invoicing**.

1. In RCS, in the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. In the **Electronic invoicing Features** page, verify that the **Saudi Arabian electronic invoice (SA)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Configurations** tab, go to **Application specific parameters** for a selected configuration. In the **Lookups** section, make sure that **PaymentMethodSubstitutionLookup** lookup is selected.
5. In the **Conditions** section, select **Add** to add a new condition.
6. In the **Name** column, select from the list the value of the method of payment defined in the application. In the **Lookup result** column of this row, select from the list a standardized method of payment code according to [UN/EDIFACT Code list 4461](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm).
7. Add specific conditions for each method of payment defined in the system and save. 

  > [!NOTE]
  > You can also use **Blank** or **Not blank** placeholders values in the **Name** column instead of specific methods of payment.

8. Complete, publish, and deploy the **Saudi Arabian electronic invoice (SA)** feature to the service environment. For more information, see the [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment) section in the topic **Get started with Electronic invoicing**.
9. Deploy **Saudi Arabian electronic invoice (SA)** feature to the connected application. See the details in the section, [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application) in the topic, **Get started with Electronic invoicing**.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

