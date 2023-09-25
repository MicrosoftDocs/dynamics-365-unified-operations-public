---
title: MX-00010 Set parameters for an electronic invoice
description: This procedure walks you through setting up an electronic invoice and the PAC account to get the approval and the digital stamp.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: EInvoiceCFDIPACTable_MX, EInvoiceParameters_MX, DigitalCertificateLookup
---
# MX-00010 Set parameters for an electronic invoice

[!include [banner](../../includes/banner.md)]

This procedure walks you through setting up an electronic invoice and the PAC account to get the approval and the digital stamp. This procedure can only be completed for a legal entity with a primary address in Mexico. This procedure was created using the demo data company MXMF. The certificates used to encrypt the XML message must be previously installed and the schema XSD file must be copied in the application as well before to start this procedure.


## Set up PAC accounts
1. Go to Accounts receivable > Invoices > E-Invoices > PAC Accounts
2. Click New.
3. In the PAC account field, type a value.
4. In the Name field, type a value.
5. In the RFC number field, enter the RFC number of your PAC provider.
6. Click Save.
7. Click New.
8. In the environment field, select the type of environment where the web services are run from.
    * Check with your PAC provider about the availability of Testing and Production environments.  
9. In the Internet address field, enter the web service address of your PAC provider.
10. In the Web service field, select 'Request stamp'.
    * The request stamp web service is used to request the digital signature.  
11. In the Method name field, enter the name of operation used to request the approval of an electronic invoice.
    * Contact your PAC provider to get the operation name.  
12. Click New.
13. In the environment field, select the type of environment where the web services are ran from
    * Check with your PAC provider about the availability of testing and production environments.  
14. In the Internet address field, enter the web services address of your PAC provider.
15. In the Web service field, select 'Cancel'.
16. In the Method name field, enter the method used for Cancel operation.
    * This is the name of operation used in the web services process to cancel an electronic invoice. Contact your PAC provider to get the operation name.  

## Set up electronic invoice parameters
1. Go to Accounts receivable > Invoices > E-Invoices > Electronic invoice parameters
2. Select or clear the Enable CFDI (electronic invoice) check box.
    * For this task, change the slider to be 'Yes'.  
3. In the Certificate field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. In the CFDI version field, select an option.
    * You can check the current available version of CFDI schema on the government website.  
6. In the CFDI XML schema file field, enter the path and name of the CFDI XML Schema file.
7. In the Environment field, select an option.
8. In the PAC certificate field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. In the PAC account field, click the drop-down button to open the lookup.
12. In the list, click the link in the selected row.
13. Select or clear the Send mail check box.
14. In the E-mail ID field, click the drop-down button to open the lookup.
15. In the list, click the link in the selected row.
16. Select or clear the Send report file - PDF check box.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
