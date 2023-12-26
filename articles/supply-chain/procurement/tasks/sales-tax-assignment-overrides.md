--- 
# required metadata 
 
title: Sales tax assignment and overrides
description: This procedure demonstrates how to assign sales tax groups to commerce channels. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailStoreTable, RetailTaxOverrideCode, RetailTaxOverrideGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Sales tax assignment and overrides

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to assign sales tax groups to commerce channels. It also walks through the process of creating a new sales tax override and assigning it to an existing sales tax override group. This procedure uses the USRT company in demo data.

1. Go to Retail and Commerce > Channels > Stores > All stores.
2. In the list, click the Channel ID link for "Houston."
3. Click Edit.
    * The "Sales tax group" field contains the list of sales tax groups for the current company. The currently assigned group is a generic "Texas" sales tax group. There are also sales tax groups for "Washington" and "Washington, King County." Sales tax groups can include applicable taxes for multiple municipalities.  
    * The "Sales tax override" field is where sales tax override groups can be mapped to the channel. Sales tax override groups can be used to group together sales tax overrides that work for multiple stores. Rather than manually assigning sales tax overrides one by one, the group can be created and assigned directly to the channels to save time.  
4. Click Save.
5. Close the page.
6. Go to Retail and Commerce > Channel setup > Sales taxes > Sales tax overrides.
7. Click New.
8. In the Sales tax override field, provide a name for your new override.
9. In the Description field, provide a description of the override.
10. Set the status to "Enable."
11. Expand or collapse the Override section.
12. In the Type field, select an option.
    * Item sales tax groups can be used to override taxes for specific items that belong to the group. For example, food items are typically taxed differently from hard goods, and would likely have their own sales tax group. Sales tax groups are groups of taxes that are applicable to a particular channel. For example, if a channel sells both retail and business-to-business, different items sales tax groups may be used. All the applicable taxes would be mapped to the sales tax group.  
    * Now you can select the "From" and "To" taxes or "From tax group" and "To tax group" to create your sales tax override. The "From" field indicates the tax or tax group to be overridden. Overriding by Item sales tax group provides different options than overriding by sales tax group. Sales tax overrides can be set up to override taxes on entire transactions or on particular lines in the transaction.  
13. Click Save.
14. Close the page.
15. Go to Retail and Commerce > Channel setup > Sales taxes > Sales tax override groups.
    * In this step you will assigned the newly created sales tax override to the sales tax override group assigned to the Houston channel.  
16. Click Edit.
17. Expand or collapse the Setup section.
18. Click Add.
19. In the Sales tax override field, click the drop-down button to open the lookup.
20. Select the previously created sales tax override from the list.
21. In the list, click the link in the selected row.
22. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]