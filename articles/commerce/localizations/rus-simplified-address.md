---
# required metadata

title: Simplified customer address format in Commerce POS for Russia
description: This topic coverss the simplified Russian address format and how to enable it in Microsoft Dynamics 365 Commerce point of sale (POS) for Russia.
author: akviklis
ms.date: 08/02/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-8-02
ms.dyn365.ops.version: 10.0.21

---
# Simplified customer address format in Commerce POS for Russia

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This topic coverss the simplified Russian address format and how to enable it in Microsoft Dynamics 365 Commerce point of sale (POS) for Russia.

In Dynamics 365 Commerce POS for Russia, you can specify a customer address when you add a named customer to the cart in POS. This address along with other customer information can then be used for invoicing purposes.

The Dynamics 365 Commerce **Enable Russian simplified customer address format** feature provides the possibility to use a simplified Russian address format for retail customers in POS and Commerce headquarters.

The simplified Russian address format is only applicable to Russian customer addresses and supports the following limited set of fields according to the address format configuration in Commerce headquarters:
- **Country/region**
- **Street**
- **City**
- **State/province**
- **ZIP/postal code**

Additional information such as the district, building, building complement, apartment, group of houses, group of flats, and county can optionally be entered as a string by a cashier in the **Street** field. 

Commerce POS for Russia only allows users to create and edit simplified addresses. Such simplified addresses can then be viewed and edited in Commerce headquarters, but they cannot be created in headquarters and the simplified address format feature is disabled for changes there.

Full (that is, non-simplified) Russian addresses created in Commerce headquarters according to the address format configuration can be viewed in the POS but not edited. A warning dialog box blocks any changes if a cashier tries to edit non-simplified Russian addresses.

Whether an address is simplified or not, in the POS the full address string is displayed in the read-only **Address** text box. This address string corresponds to the **Address** field in Commerce headquarters and contains an address string built according to the country address format. In other words, the address string contains all of the country address format fields.

For more information, see [Russian address formats and import from FIAS](../../finance/localizations/rus-russian-address-format-and-import-from-fias.md).

## Enable the Russian simplified customer address format feature

To enable the Russian simplified customer address format feature in Commerce headquarters, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
1. On the **All** FastTab, turn on the **Enable Russian simplified customer address format** feature.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
