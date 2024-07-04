---
title: Set up, import, and verify NF-e XML documents and DANFE
description: You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE from emails sent by the vendor for your company.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 
ms.dyn365.ops.version: July 2017 update
ms.search.form: EFDocumentReceivedXML_BR  
---

# Set up, import, and verify NF-e XML documents and DANFE

[!include [banner](../../includes/banner.md)]

You can automatically extract and import the XML from the Nota Fiscal Eletrônica (NF-e) and its DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) from emails sent by a vendor. The vendor must send these emails as file attachments during the time that the acquired goods are in transit.

The following prerequisites must be in place before you begin: 
 - Configure fiscal establishments in your legal entity. 
 - Set up NF-e federal parameters, including the IBGE code selected in the tax authority parameters.
 - Set up NF-e parameters for fiscal establishments.

> [!NOTE] 
> To use modern authentication to authenticate the connections to the POP3 server to read emails, complete the steps outlined [here](/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth) as a prerequisite to create an azure Microsoft Entra application. The application you create will have the required mailbox permissions (POP) to read emails from the shared mailbox that you are using to receive emails sent by a vendor.
> Next, add the azure Microsoft Entra application client ID, the client secret, and the tenant IDs as secrets to a key vault in azure and configure the same in Dynamics 365 Finance.

## Set up email accounts to import XML files and DANFE for NF-e
- On the **Configure email accounts** page, select **New**, and enter the account details.
   - **Server address** - Enter the POP3 server address for the email account.
   - **Port** - Enter the port number to use for the email server.
   - **Required SSL** - Select this option to indicate that the server requires a Secure Socket Layer (SSL) encrypted connection.
   - **Username** - Enter the user name for the email account.
   - **Password** - Enter the password for the email account.

- To support modern authentication due to the [deprecation of basic authentication in Exchange online](/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online), enter additional details.
   - **Use modern authentication** - Select this checkbox to use modern OAuth-based authentication to connect to the POP3 server.
   - **Server resource ID** - Enter the exchange server URI (https://outlook.office.com/ or https://outlook.office365.com/ ).
   - **Tenant ID** - Enter the key vault certificate reference for the tenant ID where the azure Microsoft Entra application that has the required mailbox permissions is hosted.
   - **Client ID** - Enter the key vault certificate reference for the app ID of the azure Microsoft Entra application that has the required mailbox permissions.
   - **Client secret** - Enter the key vault certificate reference for the client secret of the azure Microsoft Entra application.
   - **Login authority** - Enter the login authority URI (https://login.microsoftonline.com/).

> [!NOTE] 
> Only Exchange online is currently supported to import XML files using modern authentication.


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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
