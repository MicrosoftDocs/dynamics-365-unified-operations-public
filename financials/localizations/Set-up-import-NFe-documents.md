---
# required metadata

title: Set up, import and verify NF-e XML documents and DANFE
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: [author's GitHub alias]
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
# ms.reviewer: [Content Strategist microsoft alias]
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Set up, import and verify NF-e XML documents and DANFE

[!include[banner](../includes/banner.md)]

You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) from e-mails sent by the vendor for your company. The vendor must send them as file attachements while the acquired goods are in transit.

As prerequisite for this this setup, you must have previously configured in your Legal Entity the fiscal establishments, the NF-e federal parameters, specially the IBGE code filled in the parameters of the tax authority, and the NF-e parameters for Fiscal establishments.

Set up email accounts to import XML files and DANFE for NF-e:
1. Click Organization administration > Electronic fiscal documents > Configure email accounts
2. In the Configure email accounts page, click New and enter the account details:
. Server address: The POP3 server address for the email account
. Port: The port number to use for the email server
. Required SSL: Check this box to indicate that the server requires a Secure Socket Layer (SSL) encrypted connection
. Username: The user name for the email account
. Password: The password for the email account

Import and verify the NF-e XML files and DANFE from emails:
1. Click Accounts payable > Periodic tasks > Electronic fiscal documents > Import XML files from email
2. If necessary, enter the batch processing parameters, recurrences and schedule
3. Click OK to import the XML and the DANFE files from the emails received in the email account

The imported XML and DANFE files can be viewed through the page:
4. Accounts payable > Periodic tasks > Electronic fiscal documents > Received NF-e XML documents:
**Note 1**: Only the XML from Notas Fiscais Eletrônicas (NF-e) issued for the CNPJ of the fiscal establishments are imported from the emails
**Note 2**: The Name of the issuer of the Nota Fiscal Eletrônica (NF-e) is left blank when its tax registration ID (CNPJ) cannot be found as attribute of a vendor in All vendors form

5. For a selected Nota Fiscal Eletrônica (NF-e), click in **XML document** to view the XML document
6. For a selected Nota Fiscal Eletrônica (NF-e), click in **DANFE** to view the Documento Auxiliar da Nota Fiscal Eletrônica (DANFE)
7. For a selected Nota Fiscal Eletrônica (NF-e), click in **Inquire status** to inquire the status of the NF-e at the SEFAZ using the access key
**Note 3:** The status, date, and time of the inquiry are updated in the Status from SEFAZ and Date and time from the last inquiry

Inquire SEFAZ about the status of NF-e access keys:
1. Click Accounts payable > Periodic tasks > Electronic fiscal documents > Inquire about NF-e access key status
2. In the Limit of cancellation field, enter the number of hours that the vendor has to cancel the NF-e
3. In the Minimum inquiry interval field, enter the minimum interval between the inquiries in minutes for the received NF-e access key at the SEFAZ
4. If necessary, enter the batch processing parameters, recurrences and schedule




