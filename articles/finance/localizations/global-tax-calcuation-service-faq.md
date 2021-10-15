---
# required metadata

title: Tax Calculation FAQ
description: This topic answers frequently asked questions about the Tax Calculation service functionality.
author: epodkolz
ms.date: 10/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations, global
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region:
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom:
ms.dyn365.ops.version: AX 10.0.21
---

# Tax Calculation FAQ

[!include [banner](../includes/banner.md)]

This topic answers frequently asked questions about the Tax Calculation service functionality.

## When will the service be generally available? 

The Tax Calculation service is generally available from October 2021, 10.0.21 Monthly Update. Please refer to the blog for more information [blog]().

## Will the Tax Calculation service be available on Tier-1 machines to test? 

No, Tier-2 is required at minimum. 

## Will on-premises customers be able to use this service? 

The Tax Calculation service is not currently supported for on-premises. 

## Do we need to continue maintaining tax codes and sales tax groups in F&O and Regulatory Service, or will there be an integration in the future, so you only need to maintain this in one application? 

Tax setup can be created and maintained in the Tax calculation feature in RCS. When the Tax feature is selected in Finance and Operations on the Tax calculation parameters page, the setting will be synchronized from RCS to Finance and Operations. 

## Do you expect performance to be better than the existing Finance and Operations tax engine? 

Yes, the performance of the Tax calculation service is better than the performance of the existing tax engine.  

## Do you have any plans to support Russia, Brazil, China and India? 

We do not plan to support Russia, Brazil or India currently. Please follow the plans at [Release plans on Dynamics 365 and Microsoft Power Platform release plans | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/release-plans/). 

## What is the recommendation for global implementations which involves countries like India? Can we use the GST engine provided by Microsoft and the tax calculation service on the same instance of D365 Finance/Supply chain? Or do we need to have separate instances - one for India and one for other countries? 

Yes, you can use different tax engines for different legal entities. For example, for a legal entity in India, you can use GST based on GTE, and for other legal entities you can enable the Tax calculation service. 

## Does this work with Withholding Tax? 

Withholding tax is not in scope of the Tax calculation service currently. It is still using the existing WHT engine. 

## Will return orders be supported? 

Yes, both sales and purchase return orders are supported in the 10.0.21 Monthly Update. The list of supported transaction types can be found in Tax Calculation overview - Finance | Dynamics 365 | Microsoft Docs 

## Will Free text Invoices be supported? 

Yes, Free text invoices are planned to be supported in the 10.0.23 Monthly Update. The list of supported transaction types can be found in [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).  

## Will the tax service support both Project Operations deployment options (that is, integrated and classic PMA)? 

We plan to support these operations later after GA. The list of supported transaction types can be found in [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).

## Will the Tax Calculation service ultimately replace the existing Finance tax engine (if so, when?), or will that remain supported longer term? 

The existing tax engine will co-exist with the Tax Calculation service for now. There are no plans to retire the existing tax engine currently. The Tax Calculation service will provide more and more advanced features. Please refer to [Tax Calculation overview](global-tax-calcuation-service-overview.md).

## If a transaction gets posted with incorrect tax (e.g., because of configuration), how can it be corrected? 

The correction process is the same as of today. If a user finds out that tax is incorrect before posting, the user can make a tax amount adjustment or adjust the applicability rule by changing tax groups. If incorrect tax calculation is found after the posting, then the user will have to reverse the posted document or post a tax adjustment journal. 

## What are the triggers for the Tax Calculation service to be called?  

The triggers for the Tax Calculation service in Finance and Operations are the same as the triggers for the existing tax engine today. 

## Why I can’t see any value in the drop list of the “Feature setup name” field in the setup: Tax > Setup > Tax configuration > Tax calculation parameters?

The tax calculation feature should be completed and published in RCS. Also check if the tenant between RCS and Finance and Operations is the same.

## Why I can’t turn on “Enable tax calculation service” parameter in the setup: Tax > Setup > Tax configuration > Tax calculation parameter?

Some countries are not supported yet. Check the legal entity primary address. The supported countries/regions list is available in [Supported countries/regions](global-tax-calcuation-service-overview.md#supported-countriesregions).

## What if the Feature name is empty in the Feature management workspace?

 - Check if the application version contains the following hotfix [KB597182](https://fix.lcs.dynamics.com/Issue/Details?bugId=597182&dbType=3);
 - Check if batch service is running; if not, start the batch service;
 - Check if the status of batch job “Runs Feature Translation population” is completed or not in System administration > Inquires > Batch jobs; if it is withhold, set it to wait; if it is waiting, wait till it finishes.


