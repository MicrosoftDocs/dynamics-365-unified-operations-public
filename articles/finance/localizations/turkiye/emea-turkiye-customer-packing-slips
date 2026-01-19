---
title: Export customer electronic packing slips
description: Learn how to configure and export customer electronic packing slips for Türkiye in Microsoft Dynamics 365 Finance by using UBL-TR format and Electronic reporting (ER) configurations.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 01/19/2026
ms.reviewer: johnmichalak
ms.search.region: Türkiye
ms.search.validFrom: 2026-01-19
ms.dyn365.ops.version: AX 10.0.45
---

# Export customer electronic packing slips

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and use **electronic packing slips (e-packing slips)** in Microsoft Dynamics 365 Finance for Türkiye.  
Microsoft Dynamics 365 Finance supports the generation of electronic packing slip XML file in the required **UBL-TR DespatchAdvice** format.

Before you begin, you must meet the following prerequisites:

- Your legal entity's primary address must be in Türkiye.
- The Electronic reporting (ER) configurations must be imported from Microsoft Dynamics Lifecycle Services (LCS) or Dataverse.
- A posted packing slip must exist for the sales order.
- Customers must have a valid delivery address for shipment.              **////// Bu satır Dick ile netleştirilmeli.**
- ER destinations must be configured if you want XML files to be automatically sent to file locations, email, SharePoint, or other channels.

The following ER configurations are required to generate UBL-TR packing slip documents.             **////// Tablo Dick ile değerlendirilmeli.**

| Number | ER configuration name | Type | Description |
|--------|------------------------|------|-------------|
| 1 | Invoice model | Data model | The shared data model that standardizes the structure of sales documents. It acts as the base model for generating packing slip XML output. |
| 2 | Packing slip model mapping | Model mapping | Links the Invoice data model to application data sources related to packing slips. |
| 3 | UBL Packing slip (TR) | Format | Generates Turkish electronic packing slip XML documents in the UBL-TR DespatchAdvice format. This is the final output format used for e-packing slips. |

---

## Configure parameters

This section describes how to configure the mandatory setup for generating UBL-TR electronic packing slips.

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the **UBL Packing slip (TR)** in Packing slip parameter.

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

### Configure legal entity data

To configure the legal entity for e-packing slip generation, follow these steps.

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
2. On the **Addresses** FastTab, add a valid primary address for the legal entity.
3. Select **RegistrationIDs** on ActionPane, .       **/////// İlgili legal entity için RegistrationID tanımlamasını anlatmaya gerek var mı? Learning de referans gösterilebilecek bir sayfa var mı ?** 

> [!NOTE]  
> Unlike electronic invoices, electronic packing slips do not require bank information or IBAN to be configured.        **///////// Notun gerekliliğini sorgula. XML de olmazsa hata oluşturur mu? TEST EDİLECEK!!!!**

### Configure customer account data                ////////// XML dosyasında bu seçeneklerin dışında seçim yaparak test et. TEST EDİLECEK!!!!!!

This section provides information about how to configure customer accounts for customer e-packing slips.

To configure customer account data, follow these steps.  

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
2. On the **Addresses** FastTab, add a valid address for the customer.
3. Specify the VAT ID of the customer. Learn more in [Set up VAT IDs of customers and vendors](../../localizations/turkiye/emea-turkiye-set-up-legal-entity.md#set-up-vat-ids-of-customers-and-vendors).
4. In the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
5. Set the **eInvoice attachment** option to **Yes** to attach an XML file to the electronic packing slip, if an attachment is necessary.
6. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered as the customer's contact. All available contact persons must already be defined for the selected customer.
7. On the **Sales demographics** FastTab, in the **Employee responsible** field, select the person who is considered as the vendor's contact.

   > [!NOTE]  
   > After **Registration IDs** are defined for customer and vendor accounts, the **Tax exempt number** field is automatically populated.  
   > If needed, you can also select the value manually.

> [!NOTE]  
> The delivery address and delivery terms are essential because these values are mapped into the UBL-TR DespatchAdvice XML structure.           **//////// XML de test edilmesi gerekiyor. TEST EDİLECEK!!!!!!!**

---

**////////////// Transportation management bölümü için ayrı bir başlık açılabilir.**

---

## Generate electronic packing slips

Electronic packing slips can be generated after a packing slip is posted for a sales order.

To generate an electronic packing slip XML file, follow these steps.

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. Select a sales order that has a posted packing slip.
3. On the Action Pane, select **Packing slip**.
4. Select **Send** > **Original**.

If ER destinations are configured, the XML will automatically be delivered to the defined destination.  
If no destination is configured, the XML output will be stored in the **Electronic reporting jobs** page.

:::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of the Send Original option for generating electronic documents.":::

---

## View electronic packing slips

If ER destinations are defined for electronic packing slip formats, the output files that are generated are sent to a related file destination configured for the ER destination.
Learn about how to configure destinations for generated electronic documents in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

If no Electronic reporting (ER) destinations are defined for electronic packing slip formats, output files for electronic packing slips are generated on the Electronic reporting jobs page.

To view these e-packing slip files, follow these steps.

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

    :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of Show files button in Electronic reporting jobs page.":::

1. Select **Open** to download the file that contains the electronic packing slip.

If generation of the electronic packing slip fails because of errors, to view more details about the error message select **Show log** \> **Message details**.

:::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of Message details showing error information for electronic invoice generation.":::
---

## Send electronic packing slips to ER destinations

You can set up ER destinations for electronic packing slip formats. In this case, output XML files that contain electronic packing slips are automatically sent to the defined destinations immediately after the invoices are posted.

When you post the invoices, you must turn on the **Print invoice** parameter.

Learn more about ER destinations in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
