---
# required metadata

title: CFDI layout version 4.0
description: This topic provides information about Comprobante Fiscal Digital por Internet (CFDI) layout version 4.0 for Mexico.
author: sndray
ms.date: 4/1/2022
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

If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), you enable electronic invoicing
by using the fields in the **CFDI** area of the **Electronic invoice parameters** page.

To start work with version 4.0 you should set up the following in Electronic invoice parameters (**Organization administration /> Setup /> Einvoice**):

-	Set Version 4.0 (CFDI version field)
-	Select new xml scheme file (**CFDI XML scheme file** and **CFDI Payment XML schema file** fields on **CFDI** tab and **CFDI XML scheme file** field on **CFDI withholding** tab)

In the case of temporary export, you can set **Temporary export** option to **Yes** in a customer record (**Invoice and delivery** tab, inherited By default in sales order and Free text invoices).

If Withholding type (Purchase order line details) is equal to **28** then two new fields (Bimonthly profit amount, ISR corresponding amount) are appeared in CFDI withholding journal details. A user should fill in these two fields and corresponding attributes are populated in the xml file.

You can find details of CFDI setting and how to work with CFDI documents under the following links:

-	[CFDI layout version 3.3](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/latam-mex-cfdi-3-3)
-	[E-invoicing CFDI[(https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tasks/mx-00010-e-invoicing-cfdi)
-	[Electronic invoices (CFDI)](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/latam-mex-cfdi-electronic-invoices)
-	[Waybill (Carta de Porte) complement](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/latam-mex-carta-de-porte)  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
