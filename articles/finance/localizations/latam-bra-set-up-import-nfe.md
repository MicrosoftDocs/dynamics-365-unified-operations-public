---
# required metadata

title: Set up, import, and verify NF-e XML documents and DANFE
description: You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) from e-mails sent by the vendor for your company.
author: v-gonode
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EFDocumentReceivedXML_BR  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil 
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: July 2017 update

---

# Set up, import, and verify NF-e XML documents and DANFE

[!include [banner](../includes/banner.md)]

You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) from emails sent by a vendor. The vendor must send these emails as file attachments during the time that the acquired goods are in transit.

The following prerequisites must be in place before you begin: 
 - Configure fiscal establishments in your legal entity. 
 - Set up NF-e federal parameters, including the IBGE code selected in the tax authority parameters.
 - Set up NF-e parameters for fiscal establishments.

## Set up email accounts to import XML files and DANFE for NF-e
- On the **Configure email accounts** page, select **New**, and enter the account details.
   - **Server address** - Enter the POP3 server address for the email account.
   - **Port** - Enter the port number to use for the email server.
   - **Required SSL** - Select this option to indicate that the server requires a Secure Socket Layer (SSL) encrypted connection.
   - **Username** - Enter the user name for the email account.
   - **Password** - Enter the password for the email account.

## Import and verify the NF-e XML files and DANFE from emails
1. On the **Import XML files from email** page, if necessary, enter the batch processing parameters, recurrences, and schedule.
2. Click **OK** to import the XML and the DANFE files from the emails received in the email account.

The imported XML and DANFE files can be viewed on the **Received NF-e XML documents** page.
> [!NOTE] 
> Only the XML from Notas Fiscais Eletrônicas (NF-e) issued for the CNPJ of the fiscal establishments are imported from the emails.

> [!NOTE] 
> The name of the issuer of the Nota Fiscal Eletrônica (NF-e) is left blank when the tax registration ID (CNPJ) cannot be found as an attribute of a vendor in the **All vendors** page.

- For a selected Nota Fiscal Eletrônica (NF-e), select **XML document** to view the XML document.
- For a selected Nota Fiscal Eletrônica (NF-e), select **DANFE** to view the Documento Auxiliar da Nota Fiscal Eletrônica (DANFE).
- For a selected Nota Fiscal Eletrônica (NF-e), select **Inquire status** to view the status of the NF-e at the SEFAZby using the status key.
  > [!NOTE] 
  > The status, date, and time of the inquiry are updated in the Status from SEFAZ and Date and time from the last inquiry.

## Inquire about the status of NF-e access keys at the SEFAZ
1. On the **Inquire about NF-e access key status** page, in the **Limit of cancellation** field, enter the number of hours that the vendor has to cancel the NF-e.
2. In the **Minimum inquiry interval** field, enter the minimum interval in minutes, between the inquiries for the received NF-e access key at the SEFAZ.
3. If necessary, enter the batch processing parameters, recurrences, and schedule.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]