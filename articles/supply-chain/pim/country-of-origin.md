---
title: Country of origin
description: Learn about the country of origin feature, which lets you link a product to its country/region of origin and keep track of its product certifications.
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 11/20/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  COOVendorCerts
---

# Country of origin

[!include [banner](../includes/banner.md)]

Many organizations issue certificates to their vendors to ensure that products meet specific certification standards. These certificates often depend on the country/region of origin. The country of origin feature lets you link a product to its country/region of origin and keep track of its product certifications.

> [!IMPORTANT]
> The *Country of origin management* feature described in this article helps you keep track of vendor certificates but doesn't modify the standard functionality of invoices, packing slips, or order confirmations to include them. If you want to print out certificate numbers on one or more of these reports, then you must extend them in your project.

## Turn the country of origin feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.21, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Country of origin management feature* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure source and destination countries/regions

Before you issue a certificate for a product, you must link the product to its destination country/region and its country/region of origin.

1. Go to **Product information management \> Setup \> Product compliance \> Country of origin \> Country of origin rules**.
2. Select an existing country/region setup to edit, or select **New** on the Action Pane to create a new country/region setup.
3. Set the following values for the selected or new country/region.

    | Field | Description |
    |---|---|
    | Item number | Select the item number of the product. |
    | Destination country | Select the country/region that you're sending the product to. |
    | Origin country | Select the country/region that you're shipping the product from. |

The purpose of this setup is to help you generate a bill of materials (BOM) report where you can include the country/region of origin for each part that source and destination countries/regions are specified for. This report helps you get a holistic picture of where your parts come from and where they're going.

## Keep track of vendor certificates

You can use the **Country of origin vendor certificates** page to keep track of certificates that you issue to vendors.

You must decide which certificate documents you're issuing and how you'll report them to customers. This feature helps you keep track of your certificates. It also lets you choose whether the relevant certificate numbers appear on invoices, packing slips, and/or order confirmations.

To set up your certificate information, follow these steps.

1. Go to **Product information management \> Setup \> Product compliance \> Country of origin \> Country of origin vendor certificates**.
2. Select an existing certificate setup to edit, or select **New** on the Action Pane to create a new certificate setup.
3. Set the following settings for the selected or new certificate.

    | Field | Description |
    |---|---|
    | Vendor account | Select the vendor that you issued the certificate to. |
    | Item number | Select the item that you issued the certificate for. |
    | Country/region | The destination country/region where you must use this certificate. |
    | Certificate number | Enter the identification number of the certificate that you issued. |
    | Effective | Select the first date when the current certificate is valid.|
    | Expiration | Select the last date when the current certificate is valid. |
    | Print on invoice | If you have extended your invoice reports to support certificate numbers, then select this check box to include them when relevant. The out-of-box invoice report design doesn't provide support for certificate numbers. |
    | Print on packing slip | If you have extended your packing slip reports to support certificate numbers, then select this check box to include them when relevant. The out-of-box packing slip report deign doesn't provide support for certificate numbers. |
    | Print on sales order | If you have extended your sales order reports to support certificate numbers, then select this check box to include them when relevant. The out-of-box sales order report design doesn't provide support for certificate numbers. |

## Include the country/region of origin on BOM reports

When you generate a BOM report, you can include the country/region of origin for each part that you specified source and destination countries/regions for on the **Country of origin rules** page.

1. Go to **Product information management \> Products \> Released products**.
1. Select or create a product to open its **Released product details** page.
1. On the Action Pane, on the **Engineer** tab, in the **BOM** group, select **Designer**.
1. On the page that appears, on the Action Pane, select **BOM \> Print**.
1. In **Bill of materials lines** dialog box, set the **Destination country** field to the destination country/region that you want to view on your report.
1. Select **OK**.

A report that shows information about the country/region of origin of each part is generated and shown. Here's an example of the report.

![Country of origin report.](media/country-of-origin-report.png "Country of origin report")


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
