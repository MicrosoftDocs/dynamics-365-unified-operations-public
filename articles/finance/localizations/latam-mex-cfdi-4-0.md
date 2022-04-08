---
# required metadata

title: CFDI layout version 4.0
description: This topic provides information about Comprobante Fiscal Digital por Internet (CFDI) layout version 4.0 for Mexico.
author: sndray
ms.date: 4/08/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, VendParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
# ms.search.industry: 
ms.author: v-oskinaolga
ms.search.validFrom: 2022-04-01
# ms.dyn365.ops.version: 

---

# CFDI layout version 4.0

[!include [banner](../includes/banner.md)]

If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), enable electronic invoicing using the fields in the **CFDI** area of the **Electronic invoice parameters** page.

To work with version 4.0, set the following values in the Electronic invoice parameters:

-	In the **CFDI version** field, select **4.0**.
-	On the **CFDI** tab, select a new xml scheme file in the **CFDI XML scheme file** and **CFDI Payment XML schema file** fields.
- On the **CFDI withholding** tab, select a new xml scheme file in the **CFDI XML scheme file** field.
-	Go to **Account receivable** > **Customers** and on the **Invoice and delivery** FastTab, in the **ELECTRONIC INVOICES** field group, enter the tax regime for customers.

For a temporary export, open the customer record, and on the **Invoice and delivery** tab, set the **Temporary export** option to **Yes**. This value defaults to related sales orders or free text invoices. 

When you post a vendor invoice, you can add a CFDI reference to the related invoice by selecting **Attachments** > **CFDI reference**.  

If the **Withholding type** field on the Purchase order line details has a value of **28**,  then the two new fields, **Bimonthly profit amount** and **ISR corresponding amount** are included in the details of the **CFDI withholding journal**. Enter a value in these two fields. The corresponding attributes are populated in the xml file.

For more information about CFDI settings and how to work with CFDI documents, see:

-	[CFDI layout version 3.3](latam-mex-cfdi-3-3.md)
-	[E-invoicing CFDI](tasks/mx-00010-e-invoicing-cfdi.md)
-	[Electronic invoices (CFDI)](latam-mex-cfdi-electronic-invoices.md)
-	[Waybill (Carta de Porte) complement](latam-mex-carta-de-porte.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
