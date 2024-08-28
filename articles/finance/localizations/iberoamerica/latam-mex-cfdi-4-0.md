---
title: CFDI layout version 4.0
description: Learn about Comprobante Fiscal Digital por Internet (CFDI) layout version 4.0 for Mexico, including outlines on parameters for working with version 4.0.
author: ankviklis
ms.author: ankviklis
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/21/2022
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2022-04-01
ms.search.form: CustPosting, VendParameters
---

# CFDI layout version 4.0

[!include [banner](../../includes/banner.md)]

If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), enable electronic invoicing by using the fields in the **CFDI** area of the **Electronic invoice parameters** page.

To work with version 4.0, set the following values for the electronic invoice parameters:

- On the **Electronic invoice parameters** page, in the **CFDI version** field, select **4.0**.
- On the **CFDI** tab, in the **CFDI XML scheme file** and **CFDI Payment XML schema file** fields, select a new XML scheme file.
- On the **Electronic invoice parameters** page, in the **Period** field, you can set a default period type. The value in this field is used for Comprobante Fiscal Digital por Internet (CFDI) global invoices. You can update this value when you post a sales order invoice, free text invoice, or invoice proposal. If a customer's Registro Federal de Contribuyentes (RFC) number is 'XAXX010101000', the system populates the **InformacionGlobal** element in the XML file with **Periodicidad**, **Meses**, and **Año** attributes.
- On the **CFDI withholding** tab, in the **CFDI XML scheme file** field, select a new XML scheme file.
- Go to **Accounts receivable** \> **Customers**, and then, on the **Invoice and delivery** FastTab, in the **Electronic invoices** section, enter the tax regime for customers.

For a temporary export, open the customer record, and then, on the **Invoice and delivery** tab, set the **Temporary export** option to **Yes**. This setting is used as a default value for related sales orders or free text invoices.

When you post a vendor invoice, you can add a CFDI reference to the related invoice by selecting **Attachments** \> **CFDI reference**.

If the **Withholding type** field in the purchase order line details has a value of **28**, the two new fields, **Bimonthly profit amount** and **ISR corresponding amount**, are included in the details of the CFDI withholding journal. Enter a value in these two fields. The corresponding attributes are then set in the XML file.

For more information about CFDI settings and how to work with CFDI documents, see the following topics:

- [CFDI layout version 3.3](latam-mex-cfdi-3-3.md)
- [E-invoicing CFDI](mx-00010-e-invoicing-cfdi.md)
- [Electronic invoices (CFDI)](latam-mex-CFDI-electronic-invoices.md)
- [Waybill (Carta de Porte) complement](latam-mex-carta-de-porte.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
