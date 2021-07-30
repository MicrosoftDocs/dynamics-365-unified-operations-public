---
# required metadata

title: GST declaration for New Zealand
description: This topic explains how to configure and generate the GST return form GST101A for New Zealand.
author: sndray
ms.date: 07/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: New Zealand
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.22

---

# GST declaration form GST101A for New Zealand (NZ-00003)

[!include [banner](../includes/banner.md)]

# Overview

This topic explains how to set up and generate the GST return form GST101A for legal entities in New Zealand.

The GST return form for New Zealand is the standard document that summarizes the total output GST tax amount due, the total input GST tax amount recoverable, and the related GST tax amount  liability. The form is used for all types of taxpayers and should be completed manually through the tax authority portal. The GST return form is commonly referred to as *Filing GST returns*.

The GST return form in Dynamics 365 Finance includes the following reports:

- GST return form GST101A, where the information is consolidated in two groups of boxes (1 to 4), GST on sales and GST on expenses as is described in the legislation. Legal entity details are printed in the top of the form. It includes the GST number, the period covered by the return, due date, mailing address and daytime phone number.
 - Sales transactions details.
 - Purchase transaction details.
 
 ## Prerequisites
 
The primary address of the legal entity must be in New Zealand.In the Feature management workspace, enable the following features

- **VAT statement format reports**.  This feature enables the setup and generation of VAT and or GST statements reports by using electronic reporting formats from **Tax > Declarations > Report sales tax for settlement period** or **Settle and post sales tax**.
  
For more information about how to enable features, see Feature management overview.

In the Electronic reporting workspace, import the following Electronic Reporting formats from the repository:

- GST101A Declaration PDF(NZ)

## Import Electronic reporting configurations

The implementation of the GST return form for New Zealand is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see Electronic reporting.

To generate the GST return form and related reports in a New Zealand legal entity, you need to upload the following configurations Lifecycle Services (LCS) or the global repository:

- Tax declaration model version 96
- Tax declaration model mapping version 96.167
- GST101A Declaration PDF(NZ) version 96.4 or later version.

After you've finished downloading the ER configurations complete the following steps.

## Set up application-specific parameters
The GST declaration form includes a set of boxes (lines) that correspond to specific parts of the GST return DECLARATION. Each box should include information about the base, adjustment, and GST amounts. To include the requirements established by the form, you must configure each box with the information that is automatically provided from the sales tax transactions generated from sales, purchases, or other operations where VAT tax is posted through the sales tax code configuration.



