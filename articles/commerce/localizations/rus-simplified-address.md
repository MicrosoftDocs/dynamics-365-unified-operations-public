---
# required metadata

title: Customer simplified address format in POS for Russia
description: This topic provides an overview of the simplified Russian address format in Microsoft Dynamics 365 Commerce for Russia.
author: akviklis
ms.date: 08/02/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: 
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-8-02
ms.dyn365.ops.version: 10.0.21

---
# Russian simplified customer address format

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This topic describes how to manage customer address information in Commerce point of sale (POS) for Russia. You can specify customer address when you add a named customer to the cart in POS. This address along with other customer information can then be used for invoicing purposes.

To configure Commerce headquarters settings to enable and use this functionality, follow these steps:
1. Go to **System administration \> Workspaces \> Feature management**.
1. On the **All** tab, turn on the **Enable Russian simplified customer address format** feature.

The feature provides a possibility to enable the Russian address format in a simplified way for retail customers in Microsoft Dynamics 365 Commerce for Russia. This simplified format is introduced in POS and Commerce headquarters.

This format is applicable for Russia only and supports the following limited set of fields according to the address format setup in Commerce headquarters:
- Country/region,
- Street,
- City,
- State/province,
- ZIP/postal code.

Additional information such as the district, building, building complement, apartment, group of houses, group of flats, and county may be entered as a string by a cashier in the Street field. 

On POS side in Russia it is allowed to create and edit only simplified addresses. Such simplified address cannot be created in Commerce headquarters.

The full (that is non-simplified) Russian addresses created in Commerce headquarters according to the address format setup can be viewed in POS but not edited. The warning dialog blocks any changes if a cashier tries to edit such non-simplified Russian addresses.

Whether the address is simplified or not, the full address string is displayed on POS in the read-only "Address" text box. This address string is corresponding to the Address field in Commerce headquarters and contains an address string built in line with the country address format (that is, contains all the fields according to the address format).

For more information, see [Russian address formats and import from FIAS](../../finance/localizations/rus-russian-address-format-and-import-from-fias.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
