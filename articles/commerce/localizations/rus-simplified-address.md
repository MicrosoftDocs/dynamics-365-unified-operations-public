---
title: Simplified customer address format in Commerce POS for Russia
description: This article describes the simplified Russian address format and explains how to enable it in Microsoft Dynamics 365 Commerce point of sale (POS) for Russia.
author: EvgenyPopovMBS
ms.date: 08/11/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Russia
ms.author: josaw
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
ms.search.industry: Retail
---
# Simplified customer address format in Commerce POS for Russia

[!include[banner](../includes/banner.md)]

This article describes the simplified Russian address format and explains how to enable it in Microsoft Dynamics 365 Commerce point of sale (POS) for Russia.

In Dynamics 365 Commerce POS for Russia, you can specify a customer address when you add a named customer to the cart. This address, together with other customer information, can then be used for invoicing purposes.

The **Enable Russian simplified customer address format** feature for Dynamics 365 Commerce enables a simplified Russian address format to be used for retail customers in POS and Commerce headquarters.

The simplified Russian address format is applicable only to Russian customer addresses. It supports the following limited set of fields that is based on the address format configuration in Commerce headquarters:

- Country/region
- Street
- City
- State/province
- ZIP/postal code

In the **Street** field, cashiers can optionally enter additional information as a string. This information includes the district, building, building complement, apartment, group of houses, group of flats, and county.

Users can create and edit simplified addresses in Commerce POS for Russia. The simplified addresses can then be viewed and edited in Commerce headquarters. However, users can't create simplified addresses in Commerce headquarters. Additionally, the simplified address format feature is disabled for changes there.

Full (that is, non-simplified) Russian addresses that are created in Commerce headquarters according to the address format configuration can be viewed in the POS. However, they can't be edited there. Cashiers who try to edit non-simplified Russian addresses receive a warning message, and the change is blocked.

In the POS, the read-only **Address** field always shows the full address string, regardless of whether an address is simplified. This address string corresponds to the **Address** field in Commerce headquarters and is built according to the country/region's address format. In other words, the address string contains all the fields from the country/region's address format.

For more information, see [Russian address formats and import from FIAS](../../finance/localizations/rus-russian-address-format-and-import-from-fias.md).

## Enable the Russian simplified customer address format feature

To enable the **Russian simplified customer address format** feature in Commerce headquarters, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
1. On the **All** FastTab, turn on the **Enable Russian simplified customer address format** feature.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
