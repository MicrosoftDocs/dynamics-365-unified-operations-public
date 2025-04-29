---
title: MX-00010 Set parameters for an electronic invoice
description: Learn how to set up an electronic invoice and a PAC account to get approval and a digital stamp in Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: EInvoiceCFDIPACTable_MX, EInvoiceParameters_MX, DigitalCertificateLookup
---

# MX-00010 Set parameters for an electronic invoice

[!include [banner](../../includes/banner.md)]

This article explains how to set up an electronic invoice and a Proveedor autorizado de certificación (PAC) account to get approval and a digital stamp in Microsoft Dynamics 365 Finance.

The following procedures can only be completed for a legal entity with a primary address in Mexico. Before you can start the procedure, the certificates used to encrypt the XML message must be installed and the schema XSD file must be copied in the application.

The procedures was created using the demo data company MXMF.

## Set up PAC accounts

To set up PAC accounts, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> E-Invoices \> PAC Accounts**.
1. Select **New**.
1. In the **PAC account** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **RFC number** field, enter the Federal Registration for Taxpayers (RFC) number of your PAC provider.
1. Select **Save**.
1. Select **New**.
1. In the **Environment** field, select the type of environment from which the web services are run. Check with your PAC provider about the availability of testing and production environments.  
1. In the **Internet address** field, enter the web service address of your PAC provider.
1. In the **Web service** field, select **Request stamp**. The request stamp web service is used to request the digital signature.  
1. In the **Method name** field, enter the name of operation used to request the approval of an electronic invoice. You can contact your PAC provider to get the operation name.  
1. Select **New**.
1. In the **Environment** field, select the type of environment from which the web services are run. Check with your PAC provider about the availability of testing and production environments.  
1. In the **Internet address** field, enter the web services address of your PAC provider.
1. In the **Web service** field, select **Cancel**.
1. In the **Method name** field, enter the name of the operation used in the web services process to cancel an electronic invoice. Contact your PAC provider to get the operation name.  

## Set up electronic invoice parameters

To set up electronic invoice parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> E-Invoices \> Electronic invoice parameters**.
1. For the **Enable CFDI (electronic invoice)** option, set the slider to **Yes**.  
1. In the **Certificate** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **CFDI version** field, select an option. You can check the current available version of the CFDI schema on the government website.  
1. In the **CFDI XML** schema file field, enter the path and name of the CFDI XML schema file.
1. In the **Environment** field, select an option.
1. In the **PAC certificate** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **PAC account** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select or clear the **Send mail** checkbox.
1. In the **E-mail ID** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select or clear the **Send report file - PDF** checkbox.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
