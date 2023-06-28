---
# required metadata

title: Dual-use goods
description: This article explains how to keep track of products that are identified as dual-use goods, store certificate numbers for each relevant product and destination country, and print valid certificate numbers on relevant invoices, packing slips, and/or sales orders.
author: t-benebo
ms.date: 07/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  COODualUseCerts, COORules, COODualUseCountries
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-15
ms.dyn365.ops.version: 10.0.9
---

# Dual-use goods

[!include [banner](../includes/banner.md)]

Dual-use goods are typically items that have both civilian and military applications. For example, a chemical might be used as either a fertilizer or an explosive. Many countries/regions have special regulations that apply to the export, import, and transportation of dual-use goods. Therefore, it's important that companies that are involved in the international trade of dual-use goods keep track of the various policies and certificates.

The dual-use feature helps companies keep track of products that are identified as dual-use goods, stores certificate numbers for each relevant product and destination country/region, and print valid certificate numbers on relevant invoices, packing slips, and/or sales orders. It helps ensure that, when your products are shipped, they always include up-to-date certifications.

Consider the following scenario:

1. The **Dual use country setup** page in your system indicates that shipments to France require a certification.
2. The **Released product details** page for product X-100 indicates that it's a dual-use good. Together, the code, category, group, and regime indicate the export control classification that the product belongs to.
3. The **Dual use certificates** page includes a certificate for product X-100 when it's shipped to France. This certificate expires January 1, 2020.
4. On June 17, 2020, you create a sales order for a customer company that is based in France, and the order includes product X-100.
5. When you confirm the sales order, the system determines the following information:

    1. Does the order include any products that are dual-use goods?
    2. If the order includes dual-use goods, does the destination country/region require dual-use certificates?
    3. If the country/region requires dual-use certificates, does a valid certificate exist for each dual-use good for the destination country/region?

6. The order includes product X-100, the product is being shipped to France, and a French certificate exists for the product. However, the certificate has expired. Therefore, you receive the following warning message: "Dual use certificates for one or more dual-use items in this sales order aren't valid. Do you want to proceed with the confirmation?"

This article explains how to configure all the settings that are required to set up dual-use goods and support this scenario.

## Define dual-use requirements for each relevant country/region

Different countries/regions have different requirements for dual-use goods. You use the **Dual use country setup** page to keep track of the countries/regions that do and don't require a certificate. The information that you specify here is checked when you create sales orders, and you will be reminded to provide the required certifications.

To set up the information about dual-use requirements for different countries/regions, follow these steps.

1. Go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use country setup**.
2. Select an existing country/region setup to edit it, or select **New** on the Action Pane to create a new country/region setup.
3. Set the following values for the selected or new country/region setup.

    | Field | Description |
    |---|---|
    | Country/region | Select the country/region that you're tracking requirements for. |
    | Certificate Required | Select this check box for countries/regions that require a certification for dual-use goods. Clear it for countries/regions that don't require this certification. |

## Create dual-use categories

Dual-use goods must often be categorized according to their export control classification number (ECCN). The ECCN is an alphanumeric code that categorizes items based on factors such as the commodity and technology. The **Dual use categories** page helps you make a list of the categories that you use, for reporting purposes.

To set up dual-use categories, follow these steps.

1. Go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use categories**.
2. Select an existing category to edit it, or select **New** on the Action Pane to create a new category.
3. Set the following values for the selected or new category.

    | Fields | Description |
    |---|---|
    | Dual use code | Enter the full ECCN code (for example, *3A001*).|
    | Dual use category | Enter the commerce control list (CCL) category part of the ECCN code. For example, for the ECCN code *3A001*, this value is *3*. |
    | Dual use group | Enter the product group part of the ECCN code. For example, for the ECCN code *3A001*, this value is *A*. |
    | Dual use regime | Enter the regime code for the item. This code identifies the reason why the item is classified as a dual-use good. For example, for the ECCN code *3A001*, this value is *001*. |

## Apply dual-use categories to products

To identify a product as a dual-use good and apply a dual-use category to it, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select or create a product to open its **Released product details** page.
1. On the **Foreign trade** FastTab, set the **Dual use products** option to **Yes** to identify the current product as a dual-use good.
1. Set the **Dual use code** field to the code that applies to the current product. (You defined this code on the **Dual use categories** page.)

> [!NOTE]
>
> The system makes the following dual-use checks when it generates a sales confirmation:
>
> 1. Does the order include any dual-use goods?
> 1. If so, does the destination country/region require dual-use certificates?
> 1. If so, do certificates exist for each dual-use good for the destination country/region, and are those certificates valid for the confirmed ship dates?
> 1. If the answers to questions 1 and 2 are "Yes" and the answer to question 3 is "No", then the system shows a warning to inform the user that dual-use certificates are missing for one or more dual-use goods in the sales order. The user should probably obtain the required certificates and try again, but could instead overrule the warning and proceed with the sales confirmation if they wish.

## Set up dual-use certificates

You use the **Dual use certificates** page to set up and manage the required dual-use certificates for each product and country/region. You can track each certificate's details, such as the country/region and the dates of validity. You can also set options to specify where this information should be printed. For example, the information can be printed on the invoice, packing slip, and/or sales order. This setup is checked when you create a sales order.

1. Go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use certificates**.
2. Select an existing certificate to edit it, or select **New** on the Action Pane to create a new certificate.
3. Set the following values for the selected or new certificate.

    | Field | Description |
    |---|---|
    | Item number | Select the item number of the dual-use good that this certificate applies to. |
    | Country/region | The destination country or region where you must use this certificate. |
    | Certificate number | The number that appears on the certificate that is issued to the vendor or customer. |
    | Effective | Select the first date when the current certificate is valid.|
    | Expiration | Select the last date when the current certificate is valid. |
    | Print on invoice | Select this check box to print the certificate number on invoices that are addressed to the specified country/region during the specified date range. |
    | Print on packing slip | Select this check box to print the certificate number on packing slips that are addressed to the specified country/region during the specified date range. |
    | Print on sales order | Select this check box to print the certificate number on sales orders that are addressed to the specified country/region during the specified date range. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
