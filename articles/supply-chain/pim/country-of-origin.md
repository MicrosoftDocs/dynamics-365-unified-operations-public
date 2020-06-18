---
# required metadata

title: Country of origin
description: Many organizations issue certificates for their vendors to ensure that a product will meet a certain certification standard. These certificates are often dependent on the country of origin. Supply Chain Management country of origin features let you link a product to its country of origin and keep track of its product certifications.
author: dasani-madipalli
manager: tfehr
ms.date: 07/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: Release 10.0.13
---

# Country of origin

Many organizations issue certificates for their vendors to ensure that a product will meet a certain certification standard. These certificates are often dependent on the country of origin. Supply Chain Management country of origin features let you link a product to its country of origin and keep track of its product certifications.

<!-- KFM: If this feature is primary (or exclusively) intended to relate to hazardous and/or dual-use materials, we should mention that here. D: It isn't. You don't "have" to use it with hazardous or dual-use, but it's a pretty common use case.-->

## Configure source and destination countries

Before issuing a certificate for a product, you must link the product to its destination country and country of origin. To do this, go to **Product information management \> Setup \> Product compliance \> Country of origin \> Country of origin rules**. Then select an existing country setup to edit it, or select **New** on the Action Pane to create a new one, and make the following settings for the new or selected country:

| **Setting** | **Description** |
| --- | --- |
| **Item number** | Select the item number of the product. |
| **Destination country** | Select the country you are sending the product to. |
| **Origin country** | Select the country you are shipping the product from. |

The purpose of this setup is to help you generate a BOM report where you can include country of origin for each part that has its source and destination countries. This will help you get a holistic picture of where your parts come from and where they are going.

## Keep track of vendor certificates

Use the **Country of origin vendor certificates** page to keep track of certificates you issue to vendors.

You must decide which certificate documents you are issuing and how you will report them to customers. This feature helps you keep track of your certificates and choose whether to display the relevant certificate numbers on invoices, packing slips, and/or order confirmations.

To set up you certificate information, go to **Product information management \> Setup \> Product compliance \> Country of origin \> Country of origin vendor certificates**. Then select an existing certificate setup to edit it, or select **New** on the Action Pane to create a new one, and make the following settings for the new or selected certificate:

| **Setting** | **Description** |
| --- | --- |
| **Vendor account** | Select the vendor you issued the certificate to. |
| **Item number** | Select the item you issued the certificate for. |
| **Country/region** | The destination country or region where you must use this certificate. <!--KFM: I assumed this--true? Or is this the vendor country? How does this relate to the settings on the **Country of origin rules** page? D: Country of origin rules specifies where the product originates from. This is the country you are sending it to. Ex: product is originated in Brazil. But you are issuing the certificate for France. In this field you would put France. --> |
| **Certificate number** | Enter the identifying number of the certificate you issued. |
| **Effective** | Select the first date on which the current certificate is valid.|
| **Expiration** | Select the last date on which the current certificate is valid. |
| **Print on invoice** | Select this check box to print this certificate number on invoices addressed to the specified country during the specified date range. |
| **Print on packing slip** | Select this check box to print this certificate number on packing slips addressed to the specified country during the specified date range. |
| **Print on sales order** | Select this check box to print this certificate number on sales orders addressed to the specified country during the specified date range. |

## Include country of origin in BOM reports

When you generate a bill of materials (BOM) report, you can include the country of origin for each part that has its source and destination countries specified in the **Country of origin rules page**. To do this:

1. Go to **Product information management \> Products \> Released products**.
1. Select or create a product to open its **Released product details** page.
1. On the Action Pane, open the **Engineer** tab and, from the **BOM** group, select **Designer**.
1. A new page opens. On the Action Pane, select **BOM > Print**.
1. The **Bill of materials lines** dialog box opens. Set **Destination country** to the destination country you want to view in your report.
1. Select **OK**

A report with the information detailing the country of origin of each of the parts is generated and displayed. Here's an example of a generated report:

![Country of origin report](media/country-of-origin-report.png "Country of origin report")
