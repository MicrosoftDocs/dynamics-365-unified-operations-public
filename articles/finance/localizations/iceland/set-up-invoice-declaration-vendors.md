--- 
title: Set up an invoice declaration for vendors
description: Learn how to set up an Icelandic invoice declaration in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak    
ms.search.region: Iceland
ms.search.validFrom: 2016-06-30
---

# Set up an invoice declaration for vendors

[!include [banner](../../includes/banner.md)]

This article explains how to set up an Icelandic invoice declaration in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to set up an Icelandic invoice declaration. The demo data company used to create this procedure is DEMF with the country/region of legal entity primary address updated to Iceland.

## Import invoice declaration GER configurations

To import invoice declaration GER configurations, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration \> Workspaces \> Electronic reporting**.
1. Select **Set active**.
1. Select **Repositories**.
1. Select **Open**.
1. Select **Show filters**.
1. Add a criterion to filter by the configuration name and enter "Vendor invoice declaration (IS)", or find the configuration in the list and select it.  
1. Apply the filter "%3".
1. Select **Import**.
1. Select **Yes**.
1. Add a criterion to filter by the configuration name and enter "Vendor invoice declaration report (IS)", or find the configuration in the list and select it.  
1. Apply the filter "%3".
1. Select **Import**.
1. Select **Yes**.

## Enable vendor invoice declaration

To enable vendor invoice declaration, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Setup \> Vendor invoice declaration**.
1. Select **New**.
1. In the **Invoice declaration** field, enter "SubC".
1. In the **Description** field, enter "Sub-contractor".
1. In the **Reporting code** field, enter "06".
1. Select **New**.
1. In the **Invoice declaration** field, enter "Gift".
1. In the **Description** field, enter "Gifts".
1. In the **Reporting code** field, enter "34".
1. In the **Record type** field, select "LA".
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
