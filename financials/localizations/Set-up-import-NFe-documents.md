---
# required metadata

title: Set up, import and verify NF-e XML documents and DANFE
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: v-gonode
manager: AnnBe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil 
# ms.search.industry: 
ms.author: v-gonode
ms.search.validFrom: 
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Set up, import and verify NF-e XML documents and DANFE

[!include[banner](../includes/banner.md)]

You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) from e-mails sent by the vendor for your company. The vendor must send them as file attachements while the acquired goods are in transit.

The following prerequisites must be in place before you start: 
 - Configured fiscal establements in your Legal Entity 
 - NF-e federal parameters - including the IBGE code selected in the tax authority parameters
 - NF-e parameters for fiscal establishments

Set up email accounts to import XML files and DANFE for NF-e:
1. On the **Configure email accounts** page, click **New** and enter the account details:
 - **Server address** - Enter the POP3 server address for the email account
 - **Port** - Enter the port number to use for the email server
 - **Required SSL** - Select this option to indicate that the server requires a Secure Socket Layer (SSL) encrypted connection
 - **Username** - Enter the user name for the email account
 - **Password** -  Etner the password for the email account

Import and verify the NF-e XML files and DANFE from emails:
1. On the **Import XML files from email** page, if necessary, enter the batch processing parameters, recurrences and schedule.
2. Click **OK** to import the XML and the DANFE files from the emails received in the email account.

The imported XML and DANFE files can be viewed on the **Received NF-e XML documents** page.
> [!NOTE] 
> Only the XML from Notas Fiscais Eletrônicas (NF-e) issued for the CNPJ of the fiscal establishments are imported from the emails

> [!NOTE] 
> The Name of the issuer of the Nota Fiscal Eletrônica (NF-e) is left blank when its tax registration ID (CNPJ) cannot be found as attribute of a vendor in **All vendors** page.

 - For a selected Nota Fiscal Eletrônica (NF-e), click **XML document** to view the XML document.
 - For a selected Nota Fiscal Eletrônica (NF-e), click **DANFE** to view the Documento Auxiliar da Nota Fiscal Eletrônica (DANFE).
 - For a selected Nota Fiscal Eletrônica (NF-e), click **Inquire status** to inquire the status of the NF-e at the SEFAZ using the access key.
> [!NOTE] 
> The status, date, and time of the inquiry are updated in the Status from SEFAZ and Date and time from the last inquiry.

Inquire about the status of NF-e access keys at the SEFAZ:
1. On the **Inquire about NF-e access key status** page, in the **Limit of cancellation** field, enter the number of hours that the vendor has to cancel the NF-e.
2. In the **Minimum inquiry interval** field, enter the minimum interval between the inquiries in minutes for the received NF-e access key at the SEFAZ.
3. If necessary, enter the batch processing parameters, recurrences and schedule.




