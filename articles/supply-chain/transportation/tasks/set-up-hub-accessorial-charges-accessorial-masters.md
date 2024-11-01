--- 
title: Set up hub accessorial charges and accessorial masters
description: Learn how to create an accessorial master for a hub and use that master to create a hub accessorial charge, including step-by-step processes. 
author: lisascholz
ms.author: lisascholz
ms.topic: how-to
ms.date: 11/11/2016
ms.custom: 
ms.reviewer: kamaybac 
ms.search.form: TMSCarrierAccessorial,TMSAccessorialMaster, TMSHubAccessorial
---

# Set up hub accessorial charges and accessorial masters

[!include [banner](../../includes/banner.md)]

This procedure shows how to create an accessorial master for a hub and use that master to create a hub accessorial charge. The procedure uses the USMF dataset. This set up will typically be done by a transportation coordinator.


## Set up a hub master
1. Go to Transportation management > Setup > Rating > Accessorial masters.
2. Click New.
3. In the Accessorial master field, type a value.
4. In the Name field, type a value.
5. In the Accessorial type field, select 'Hub'.
6. Click Save.
7. Close the page.

## Set up a hub accessorial charge
1. Go to Transportation management > Setup > Rating > Hub accessorial charges.
2. Click New.
3. In the Hub accessorial ID field, type a value.
4. In the Hub field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
6. In the Hub position field, select an option.
    * You can either create the charge as a pickup or drop-off. Depending on your selection the charge will be applied to the corresponding transportation segment on your route.  
7. In the Accessorial master field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
    * Select the master you just created.  
9. Click Save.
10. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]