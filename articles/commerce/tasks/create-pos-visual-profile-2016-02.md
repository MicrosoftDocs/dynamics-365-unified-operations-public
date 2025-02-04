--- 
title: Create point of sale (POS) visual profiles
description: This procedure walks through creating a new point of sale (POS) visual profile. 
author: ritakimani
ms.date: 10/31/2024
ms.topic: how-to 
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.search.industry: Retail
ms.author: ritakimani
ms.search.validFrom: 2016-06-30 
---
# Create point of sale (POS) visual profiles

[!include [banner](../includes/banner.md)]

This procedure walks through creating a new point of sale (POS) visual profile. A visual profile contains basic information that determines the appearance of POS registers. You can create several visual profiles and assign specific profiles to run on specific registers. This procedure uses the USRT demo data company.

> [!NOTE]
> - Starting with the Commerce 10.0.42 release, in Commerce headquarters you can set the **Modern transaction grid** option to **Yes** on the **POS visual profiles** form configuration (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> POS visual profiles**). This setting allows you to roll out changes for specific registers. To access this option you must first enable the **Enable modern transaction grid in POS transaction view** feature in the **Feature management** workspace (**System administration \> Workspaces \> Feature management**). This feature includes refreshed transaction, numpad, customer card, and button grids, and also enables retailers to display images in the cart view.
> - After every configuration change made in headquarters, you must run the **Registers (1090)** job to implement the change in POS.

1. Go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Visual profiles**.
2. Click **New**.
3. In the **Profile number** field, type a value.
4. In the **Description** field, type a value.
5. In the **Application type** field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. In the **Theme** field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. In the **Accent color** field, click the drop-down button to open the lookup.
10. In the list, find and select the desired record.
11. In the list, click the link in the selected row.
12. Toggle the expansion of the **Login background** section.
13. In the **Landscape image ID** field, select or enter an image ID.
14. In the** Portrait image ID** field, select or enter an image ID.
15. Toggle the expansion of the **Background** section.
16. RequestPopup the Image ID.
17. In the list, click the link in the selected row.
18. Click **Save**.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
