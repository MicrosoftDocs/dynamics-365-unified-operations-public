---
title: EUR-00015 Set up VAT ID
description: Learn about how to set up VAT ID registration prerequisites such as setting up a registration type and assigning it to a registration category in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: TaxRegistrationType, TaxRegistrationTypeCreate, TaxRegistrationLegislationTypes
---
# EUR-00015 Set up VAT ID

[!include [banner](../../includes/banner.md)]

This article explains how to set up VAT ID registration prerequisites such as setting up a registration type and assigning it to a registration category in Microsoft Dynamics 365 Finance.

The following procedure walks you through how to set up VAT ID registration prerequisites. for more information about registration IDs and registration ID processing, see [Registration IDs](emea-registration-ids.md). 

The procedure is intended for system administrators, and the information here applies to all European countries/regions. The procedure was created using the demo data company DEMF with Germany as the legal entity primary address. 

To set up VAT ID registration prerequisites, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Registration types \> Registration types**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, enter "VAT ID".
1. In the **Description** field, VAT number.
1. In the **Country/region** field, enter or select a value. For example, enter "DEU".
1. In the **Unique** field, select **Yes** to verify that the VAT ID is unique.  
1. In the **Primary for country/region** field, select **Yes** if the VAT ID should be effective for all addresses belonging to the specified country/region.  
1. Select **Create**.
1. Select **Add**.
1. In the **Country/region** field, enter or select a value. For example, enter "ITA".
1. In the **Format** field, enter "###########". When you enter a registration ID of this type for the selected country/region, the registration ID is verified against this format.  
1. Select the **Unique** checkbox to verify that the VAT ID is unique.  
1. Select the **Primary for country/region** checkbox if the VAT ID should be effective for all addresses belonging to the specified country/region.  
1. Select **Save**.
1. Go to **Organization administration \> Global address book \> Registration types \> Registration categories**.
1. Select **New**.
1. In the **Country/region** field, enter or select a value. For example, enter "VAT ID, DEU".
1. In the **Registration category** field, select **VAT ID**. Assign the registration type that you created earlier to a predefined **Registration** category.  
1. Select **New**.
1. In the **Country/region** field, enter or select a value. For example, enter "VAT ID, ITA".
1. In the **Registration category** field, select **VAT ID**. Assign the registration type that you created to a predefined registration category.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
