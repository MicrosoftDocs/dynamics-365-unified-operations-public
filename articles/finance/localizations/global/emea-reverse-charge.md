---
title: Reverse charge mechanism for VAT/GST scheme
description: Learn how to set up the reverse charge value-added tax (VAT) for European countries/regions, Saudi Arabia, and Singapore.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Saudi Arabia, Spain, Sweden, United Kingdom, Singapore, Bahrain, Kuwait, Oman, Qatar
ms.search.validFrom: 2017-06-30
---

# Reverse charge mechanism for VAT/GST scheme

[!include [banner](../../includes/banner.md)]

This article describes a generic approach for setting up reverse charge functionality for countries and regions that adopt the VAT or GST schemes.

The country/region availability of the functionality is managed by the following features in the **Feature management** workspace.

| Feature                                              | Country/region                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No   specific feature                                | Austria </br>Belgium </br>Bulgaria </br>Croatia </br>Cyprus </br>Czech Republic </br>Denmark  </br>Estonia  </br>Finland  </br>France  </br>Germany  </br>Hungary  </br>Iceland  </br>Ireland  </br>Italy  </br>Latvia  </br>Liechtenstein  </br>Lithuania  </br>Luxembourg  </br>Netherlands  </br>Norway Poland </br>Portugal </br>Romania  </br>Saudi Arabia </br>Singapore  </br>Slovakia  </br>Slovenia  </br>Spain  </br>Sweden  </br>Switzerland  </br>United Kingdom  </br>United Arabic Emirates |
| Reverse   charge for additional countries/regions            | Bahrain  </br>Kuwait  </br>Oman  </br>Qatar                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Enable   reverse charge mechanism for VAT/GST scheme | All other countries/regions   except:  </br>Brazil  </br>India  </br>Russia                                                                                                                                                                                                                                                                                                                                                                                         |

 For more information, see the [Enable Reverse charge mechanism for VAT/GST scheme feature](#enable-reverse-charge) section later in this article.

Reverse charge is a tax schema that moves the responsibility for the accounting and reporting of VAT from the seller to the buyer of goods and services. Therefore, recipients of goods and services report both the output VAT (in the role of a seller) and the input VAT (in the role of a purchaser) on their VAT statement.

In some countries or regions, the reverse charge schema is implemented only for some goods and services, and there are additional conditions or thresholds on sales amounts. In other countries or regions, the responsibility for VAT payment depends on the status of the supplier and the buyer. If the buyer is liable to pay VAT, the supplier must clearly indicate this fact on the invoice. For example, the invoice must include the words "Reverse charge" and must indicate which positions are under the reverse charge schema.

To apply the reverse charge, complete the following setup.

## Set up sales tax codes

Use separate sales tax codes for sales operations and purchase operations.

| Sales tax code | Description |
|---|---|
| **Sales tax code for sales** | Create a sales tax code for reverse charge sales operations (**Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**). |
| **Sales tax code for purchases** | Create positive and negative sales tax codes for the reverse charge VAT for purchases (**Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**). 1. Create a sales tax code that has a positive value. 1. Create a sales tax code that has a negative value. Set the **Allow negative sales tax percentage** option to **Yes**. You must assign this negative sales tax code to an item sales tax group and then assign that item sales tax group to the items that are subject to the reverse charge VAT. For more information, see the next section, "Set up sales tax groups and item sales tax groups." |

## <a name="sales-tax-item-sales-tax-groups"></a>Set up sales tax groups and item sales tax groups

Use separate sales tax groups for sales operations and purchase operations.

| Sales tax code | Description |
|---|---|
| **Sales tax groups for sales** | Create a sales tax group for sales operations that have the reverse charge (**Tax** > **Indirect taxes** > **Sales tax** > **Sales tax groups**). On the **Setup** tab, include the sales tax code for the reverse charge in this group. Select the **Exempt** and **Reverse charge** check boxes for the sales tax code. |
| **Sales tax groups for purchases** | Create a sales tax group for purchase operations that have the reverse charge (**Tax** > **Indirect taxes** > **Sales tax** > **Sales tax groups**). On the **Setup** tab, include both positive and negative sales tax codes in this group. Select the **Reverse charge** check box for the sales tax code that has a negative value. |
| **Item sales tax groups** | Create or update the item sales tax group with the sales tax code that has a negative value (**Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**). Assign the default item sales tax group to the products and categories that are subject to the reverse charge. |

## <a name="reverse-charge-item-group"></a>Set up reverse charge item groups

On the **Reverse charge item groups** page (**Tax** > **Setup** > **Sales tax** > **Reverse charge item groups**), you can define groups of products or services, or individual products or services, that the reverse charge can apply to. For each reverse charge item group, define the list of items, item groups, and categories for sales and purchases, sales, or purchases.

## <a name="reverse-charge-rules"></a>Set up reverse charge rules

On the **Reverse charge rules** page (**Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Reverse charge rules**), you can define the applicability rules for purchase and sales purposes. You can configure a set of reverse charge applicability rules. For each rule, set the following fields:

- **Document type** – Select **Purchase order**, **Vendor invoice journal**, **Sales order**, **Free text invoice**, **Customer invoice journal**, and **Vendor invoice**.
- **Country/region type of the partner** – Select **Domestic**, **EU**, **GCC**, or **Foreign**. Alternatively, if the rule applies to all trade partners, regardless of the country or region of their address, select **All**.
- **Domestic delivery address** – Select this check box to apply the rule to deliveries within the same country or region. You can't select this checkbox for the **Vendor invoice journal** and **Customer invoice journal** document types.
- **Reverse charge item group** – Select the group that the rule can be applied to.
- **Threshold amount** – The Reverse Charge schema applies to an invoice only if the value of items and services included in the reverse charge item group exceeds the limit that you specify here.

Use the **Effective date** and **Expiration date** fields to define the period when the rule is effective.

You can also specify whether a notification appears and the document line is updated with the default reverse charge sales tax group if the condition for that document line is met. The following options are available:

- **None** – The document line isn't updated.
- **Prompt** – A notification appears to confirm that the reverse charge can be applied.
- **Set** – The document line is updated without additional notification.

## <a name="Set-up-Country/region-properties"></a>Set up Country/region properties

On the **Foreign trade parameters** page (**Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Foreign trade** &gt; **Foreign trade parameters**), on the **Country/region properties** tab, set the country/region of the current legal entity to *Domestic*. Set the **Country/region type** of the EU countries/regions that participate in the EU trade with the current legal entity to *EU*. Set the **Country/region type** of the GCC countries/regions that participate in the GCC trade with the current legal entity to *GCC*.

## Set up default parameters

To enable the functionality for reverse charge VAT, on the **General ledger parameters** page, on the **Reverse charge** tab, set the **Enable reverse charge** option to **Yes**. In the **Purchase order sales tax group** and **Sales order tax group** fields, select the default sales tax groups. When a reverse charge applicability condition is met, the sales or purchase order line is updated with these sales tax groups.

## <a name="reverse-charge-sale"></a>Reverse charge on a sales invoice

For sales under the reverse charge scheme, the seller doesn't charge VAT. Instead, the invoice lists both the items that are subject to the reverse charge VAT and the total amount of the reverse charge VAT.

When you post a sales invoice that has the reverse charge, the sales tax transactions have the **Sales tax payable** tax direction and zero sales tax. The **Reverse charge** and **Exempt** check boxes are selected.

## <a name="reverse-charge-purchase"></a>Reverse charge on a purchase invoice

For purchases under the reverse charge scheme, the purchaser who receives the invoice that has the reverse charge acts as a buyer and a seller for VAT accounting purposes.

When you post a purchase invoice that has the reverse charge, two sales tax transactions are created. One transaction has the **Sales tax receivable** tax direction. The other transaction has the **Sales tax payable** tax direction, and the **Reverse charge** check box is selected.

In the following screenshot, one transaction has the **Sales tax receivable** direction, and the other transaction has the **Sales tax payable** direction.

:::image type="content" source="../media/apac-sau-posted-sales-tax.png" alt-text="Screenshot of posted sales tax transactions showing Sales tax receivable and Sales tax payable directions.":::

## <a name="enable-reverse-charge"></a>Enable Reverse charge mechanism for VAT/GST scheme feature

In the **Feature management** workspace, find the feature and select **Enable**.

After you enable the feature, the **Reverse charge** tab is available in all legal entities. Enable the Reverse charge functionality for a legal entity by setting the **Enable reverse charge** option to **Yes**.

The following pages and menu items related to the feature setup become available:

- **Reverse charge item groups** (**Tax** > **Setup** > **Sales tax** > **Reverse charge item groups**). For more information, see the [Set up reverse charge item groups](#reverse-charge-item-group) section.
- **Reverse charge rules**  (**Tax** > **Setup** > **Sales tax** > **Reverse charge rules**). See [Set up reverse charge rules](#reverse-charge-rules).
- **Foreign trade parameters** (**Tax** > **Setup** > **Sales tax** > **Foreign trade** > **Foreign trade parameters**). See [Set up Country/region properties](#Set-up-Country/region-properties).

The **Reverse charge** checkbox becomes available on the **Sales tax group** and **Posted sales tax** pages. For more information, see the sections, [Set up sales tax groups and item sales tax groups](#sales-tax-item-sales-tax-groups), [Reverse charge on a sales invoice](#reverse-charge-sale), and [Reverse charge on a purchase invoice](#reverse-charge-purchase).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
