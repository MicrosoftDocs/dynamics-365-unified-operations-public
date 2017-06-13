---
# required metadata

title: Document generation, publishing, and printing capabilities in on-premises deployments
description: This topic describes document generation, publishing, and printing capabilities in on-premises deployments.
author: TJVass
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tjvass
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
---

# Document generation, publishing, and printing capabilities in on-premises deployments

[!include[banner](../includes/banner.md)]

This article describes the document generation, publishing, & printing capabilities present in the on-premise deployments of Microsoft Dynamics 365 for Operations.  The platform provides a fully integrated enterprise document generation experience powered by Microsoft SQL Server Reporting Services (SSRS).  The service allows users to produce standard industry documents linked to business processes like Sales Invoices, Checks, & Packing Slips from any supported device.  Administrators can use built-in tools to configure the service to allow users to securely connect to network printers.

Upgrade legacy solutions built-on the AX 2012 SQL Reporting Services framework or take advantage of modern solutions available in [Lifecycle Services (LCS)](https://lcs.dynamics.com).

## Document Publishing Services: Secure, Reliable, and Convenient
Employees spend a great deal of time on the go.  As a result, businesses depend heavily on their employees’ ability to stay productive while working remotely.  Even in today’s modern world, documents remain critical for business transactions and record keeping.  

Dynamics 365 for Operations allows customers to print documents on network printers from mobile devices, automate the creation of business documents, and use built-in tools to configure document routing instructions to multiple recipients.

**Publishing options:**
- **Email –** server based distribution of mail with reports linked as attachments.
- **Archive –** store reports for future reference and regulatory compliance
- **File –** produce a PDF file that’s downloaded directly to the browser for local printing
- **Print –** send documents directly to network printers from all supported platforms including mobile devices.

For a high-level summary of information access options available in the Cloud hosted solution, see [Printing in Finance and Operations applications](print-documents.md) for additional details.

## Comparing cloud vs on-premises
Unlike the Cloud hosted offering, the on-premise publication service renders documents as PDF file automatically downloaded to the browser.  This allows users to conveniently save documents and/or print hard copies using local connected devices.  Use built-in administrative forms to control access to network printers directly from the application.  Interact with reports on-demand or schedule automatic jobs to securely generate and distribute documents on a recurring basis.

The following illustration identifies the components involved in printing documents:

(graphic)

See related topic in the Appendix section for details on using extensions to manage availability of the embedded drill-thru links in application reports.

## Managing access to network printers
Use built-in administrative forms to manage access to network printers.  Network printers are secured per Company and shared by users of the application.  The documents are then printed using a privileged domain account based on settings supplied by the user.  With on-premise deployments of Dynamics 365 for Operations, there’s no need to install an adapter to connect to domain resources like printers and fax machines.

Here’s a screen shot of the form used to manage network printers.

(graphic)

## Appendix

### How to turn-on embedded links in business documents?
Here's the code used to enabled embedded links in PDF documents: 

(graphic)






