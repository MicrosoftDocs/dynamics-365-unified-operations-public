--- 
# required metadata 
 
title: Category pricing rules to create trade agreements
description: This procedure demonstrates how to create sales price trade agreements using a category pricing rule. 
author: scott-tucker
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, RetailDiscountPricingWorkspace, RetailPricingDiscountCategoryPriceRule, RetailCategoryPriceRule, EcoResCategorySingleLookup, RetailCategoryPriceWizard, PriceDiscAdm, PriceDiscAdmTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: scotttuc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Category pricing rules to create trade agreements

[!include [banner](../includes/banner.md)]

Category price rule feature is applicable on scenarios where the sales price to the customer is dependent on Price rules such as Markup, Margin or Fixed Amount on the price basis such as Purchase Price or Inventory cost. The sales price in this case will be updated for all the items which falls under particular category which is being updated.

To use category price rules for updating sales price, follow the steps as mentioned below.
 
1.	Go to Retail and Commerce > Pricing and discounts > Category price rules. System will show you existing category price rules.111
2.	To create a new category price rule, click New.
3.	In the Account code field, select appropriate value. The field drives Account selection field further. 
i.	If you select Account code as Table, then system will let you select Customer in account selection field.
ii.	If you select Account code as Group, then system will let you select Customer price group.
iii.	If you select Account code as All, then the resultant trade agreement will be valid for all customers.
4.	Click on the dropdown on Category field notice that when you click on category dropdown, you have ability to change the hierarchy also. 
5.	In the tree, select the appropriate hierarchy value for which prices needs to be updated. For example, you can select Action Sports (Action Sports) from the dropdown. After selecting the category value, click on Ok.
6.	In the vendor account field, select the vendor code if the price update is needed for a particular vendor only. If the intended price update is not vendor specific, you can keep it blank. This field will act as a filter within the category to limit the products this rule applies to
7.	In the Price basis field, select appropriate option.
i.	Markup - A percentage of the price basis is used to calculate the sales price. For example, a product that costs 10.00 and sells for 15.00 has a markup of 50 percent.
ii.	Margin – A percentage of the sales price is used to calculate the amount of profit. For example, a product that costs 10.00 and sells for 15.00 has a margin of 33.3 percent.
iii.	Fixed Amount – An amount that is added to the price basis is used to calculate the sales price. For example, a product that costs 10.00 and sells for 15.00 has a fixed amount of 5.00.
Use Fixed Amount if the price has to be the same for all products.
8.	In the Amount/Percent field, enter number as required. 
9.	Select the appropriate Price basis from the dropdown. You can select following:
i.	Base cost – Purchase price from the item Purchase tab
ii.	Base price – Sales price from the item Sell tab.
iii.	Current price – Sales price considering Trade agreement.
iv.	Purchase price – Identified as purchase price from trade agreement having specified vendor.
v.	Inventory cost – Identified as current average inventory cost for specified inventory dimensions. 
vi.	Price group – Identified as sales price from trade agreement having specified customer price group.
vii.	Latest Purchase price – Identified as purchase price from the latest vendor invoice having specified vendor.
10.	After entering the base information for category price rule, click Generate trade agreements.
11.	You will see option for Product selection. Select the appropriate value and click Next.
12.	On the page that appears, select the currency and date range for the trade agreement. You can also set  'Find Next'  or 'Expire previous trade agreements' to be true as required. Click next after selecting appropriate values.
13.	System shows the summary information for trade agreement that will be created. You can run the process in batch by checking 'Run as batch job' or through user interface. Click Finish
14.	System will create trade agreement for your review. You can make necessary changes and you can post the trade agreement to make it effective.
