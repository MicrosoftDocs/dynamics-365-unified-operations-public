---
# required metadata

title: Product-related translations FAQ
description: This article describes how to manage translations for products, product dimension values, and product attributes. 
author: t-benebo
ms.date: 08/06/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysTranslationDetail, SysTranslationLanguage, SysTranslationList, EcoResProductListPage, EcoResProductVariants, EcoResProductDetailsExtended, EcoResProductCreate, EcoResProductDetails, RetailSizeGroupTable, RetailStyleGroupTable, RetailColorGroupTable, PCTranslationLanguageLookup, EcoResProductCategory
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 201853
ms.assetid: c0286bba-f54b-42de-904c-81fd796bdd1d
ms.search.region: global
ms.search.industry: Product information
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Product-related translations FAQ

[!include [banner](../includes/banner.md)]

This article describes how to manage translations for products, product dimension values, and product attributes. 

## What product-related data can be translated?

You can create translations for the following product-related information:
-   Names and descriptions of products.
-   Descriptions, friendly names, and help text of product attribute values.
-   Names and descriptions of product dimension values.

You can translate the product-related information into any language that is available from the **Text translation** page. For more information, see the following section **How do I created translations for product-related information**.

## Where can I view the translated information?
You can view translations of product-related information in any external source document, such as an invoice, that uses a language where translations are available.

## How do I create translations for product-related information?
To create translations for a product, follow these steps:
1.  Click **Product information management** &gt; **Products** &gt; **Released products**.
2.  Select a product, and on the Action Pane, in the **Languages** group, click **Translations**.
3.  In the **Text translation** page, in the **Language** field, select a language. To add more languages, expand the **Language** field, and then click **OK**.
4.  In the **Translated text** group, enter translations in the **Description** and **Product name** fields.

To create translations for product attributes, follow these steps:
1.  Click **Product information management** &gt; **Products** &gt; **Released products**.
2.  Under **Setup**, click **Attributes**, and then click **Attributes**.
3.  In the **Attributes** page, click **Translate**.
4.  In the **Text translation** page, in the **Language** field, select a language. To add more languages, expand the **Language** field, and then click **OK**.
5.  In the **Translated text** group, enter translations in the **Description**, **Friendly name**, and **Help text** fields.

To create translations for product dimension values, follow these steps:
1.  Click **Product information management** &gt; **Products** &gt; **Released products**.
2.  Select a product, and then click **Product dimensions**.
3.  Select one of the links for the product dimensions: **Configurations**, **Sizes**, **Colors**, or **Style**.
4.  Select a dimension value and then click **Translate**.
5.  In the **Text translation** page, in the **Language** field, select a language. To add more languages, expand the **Language** field, and then click **OK**.
6.  In the **Translated text** group, enter translations in the **Name** and **Description** fields.

## Can the names of product variants be translated?
Product variants are based on the dimensions of a released product. Product variant names are based on a combination of dimension values. When the dimension values that are associated with a product variant are translated, the name of the product variant appears in the translated version.  

**Example**  

Your product is a T-shirt that comes in different sizes and colors and the variant names are based on the following details:
-   Product number: \#3
-   Dimensions: Size and color
-   Size dimension values: Small, Medium, Large
-   Color dimension values: Red, Green, Black

The name of a product variant that is based on the dimension values Small and Red is **\#3:Small:Red**.  

A customer wants to buy some small, red T-shirts and the name of the T-shirt must appear in French on the invoice. You translate the dimension values, Small and Red, into French, and the name of the product variant is **\#3:Petit:Rouge**.
<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>To set the preferred language of a customer, follow these steps:
<ol><li>Click <strong>Sales and marketing</strong> &gt; <strong>Common</strong> &gt; <strong>Customers</strong> &gt; <strong>All</strong> <strong>customers</strong>.</li>
<li>Double-click a customer to open the <strong>Customers</strong> page. On the <strong>General</strong> tab, in the <strong>Language</strong> field, select the <strong>language</strong>.</li>
</ol></td>
</tr>
</tbody>
</table>

## What happens if a customer has a preferred language for which no translations are available?
If translations are not available in the customer’s preferred language, the names and descriptions are displayed in the global language of your own company.

## Can I manage translations for a series of dimension values at the same time?
Dimension values are product specific and you can manage the translations for the dimension values for each product. However, if you create a dimension value group and create translations for the values in the value group, it is easier to manage the translations.   

**Example**  

Your company produces T-shirts in different styles, and each style is available in the sizes Small, Medium, and Large. The sizes are collected in one dimension value group. When a new T-shirt style is added, you can associate it with the dimension value group that is used for sizes, so that all the sizes are available for the product. You can also add or change translations for the sizes in the dimension value group at any time.  

A dimension value that is associated with a product through a dimension variant group must be maintained from the product variant group.   
To create a dimension value group, follow these steps:
1.  Click **Product information management** &gt; **Setup** &gt; **Variant groups**.
2.  Select **Size** **groups**, **Color groups**, or **Style groups**.
3.  Click **New**, and then enter a name for the group in the **Size** **group**, **Color group**, or **Style group** field. Click **Sizes**, **Colors**, or **Styles** to create lines for the groups.
4.  In the **Size** **group** lines, **Color** **group** **lines**, or **Style group lines** page, click **New**, and then create the sizes, colors, and styles for the groups.

To manage translations for values in a dimension value group, follow these steps:
1.  Follow the steps in the previous procedure for creating a dimension value group to open the **Size group lines**, **Color group lines**, or **Style group lines** page.
2.  Click **Text translation**. In the **Text translation** page, in the **Translated text** group, enter translations in the **Name** and **Description** fields.

## When can translations of product-related information be managed?
Translations of product-related information can be managed at any time. When translations are updated for a dimension value that is associated with a product, the product information is updated, regardless of whether the product has transactions.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]