---
# required metadata

title: CFDI layout version 4.0
description: This topic provides information about Comprobante Fiscal Digital por Internet (CFDI) layout version 4.0 for Mexico.
author: v-oskinaolga
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

If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), enable electronic invoicing by using the fields in the **CFDI** area of the **Electronic invoice parameters** page.

To work with version 4.0, set the following values for the electronic invoice parameters:

- On the **Electronic invoice parameters** page, in the **CFDI version** field, select **4.0**.
- On the **CFDI** tab, in the **CFDI XML scheme file** and **CFDI Payment XML schema file** fields, select a new XML scheme file.
- On the **CFDI withholding** tab, in the **CFDI XML scheme file** field, select a new XML scheme file.
- Go to **Accounts receivable** \> **Customers**, and then, on the **Invoice and delivery** FastTab, in the **Electronic invoices** section, enter the tax regime for customers.

For a temporary export, open the customer record, and then, on the **Invoice and delivery** tab, set the **Temporary export** option to **Yes**. This setting is used as a default value for related sales orders or free text invoices.

When you post a vendor invoice, you can add a Comprobante Fiscal Digital por Internet (CFDI) reference to the related invoice by selecting **Attachments** \> **CFDI reference**.

If the **Withholding type** field in the purchase order line details has a value of **28**, the two new fields, **Bimonthly profit amount** and **ISR corresponding amount**, are included in the details of the CFDI withholding journal. Enter a value in these two fields. The corresponding attributes are then set in the XML file.

For more information about CFDI settings and how to work with CFDI documents, see the following topics:

- [CFDI layout version 3.3](latam-mex-cfdi-3-3.md)
- [E-invoicing CFDI](tasks/mx-00010-e-invoicing-cfdi.md)
- [Electronic invoices (CFDI)](latam-mex-cfdi-electronic-invoices.md)
- [Waybill (Carta de Porte) complement](latam-mex-carta-de-porte.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
