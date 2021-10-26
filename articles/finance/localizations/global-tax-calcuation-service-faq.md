---
# required metadata

title: Tax Calculation FAQ
description: This topic answers frequently asked questions about the Tax Calculation service functionality.
author: epodkolz
ms.date: 10/26/2021
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

This topic answers frequently asked questions about the Tax Calculation service functionality.

## When will the service be generally available? 

The Tax Calculation service is generally available starting with version 10.0.21 which was released in October 2021. For more information, see [Microsoft Dynamics 365 Blog
](https://cloudblogs.microsoft.com/dynamics365/bdm/2021/10/26/tax-calculation-enhancements-are-now-available-for-dynamics-365/).

## Will the Tax Calculation service be available on Tier-1 machines to test? 

No. At a minimum, Tier-2 is required for testing. 

## Will on-premises customers be able to use this service? 

The Tax Calculation service isn't currently supported for on-premises. 

## Do we need to continue maintaining tax codes and sales tax groups in Dynamics 365 Finance and Operations apps and the Regulatory Configuration Service (RCS), or will there be an integration in the future, so maintenance is only needed in one application? 

Tax setup can be created and maintained in the Tax calculation feature in RCS. When the Tax feature is selected in Finance and Operations apps on the **Tax calculation parameters** page, the setting is synchronized from RCS to your Finance and Operations apps. 

## Do you expect performance to be better than the existing Finance and Operations apps tax engine? 

The performance of the Tax calculation service is better than the performance of the existing tax engine.  

## Do you have any plans to support Russia, Brazil, China, and India? 

At this time, we do not plan to support Russia, Brazil, China, or India. For more information about country/region support, see [Release plans on Dynamics 365 and Microsoft Power Platform release plans](/dynamics365/release-plans/). 

## What is the recommendation for global implementations which involves countries like India? Can we use the GST engine provided by Microsoft and the tax calculation service on the same instance of Finance or Supply Chain Management rr do we need to have separate instances? 

You can use different tax engines for different legal entities. For example, for a legal entity in India, you can use GST based on GTE, and for other legal entities you can enable the Tax calculation service. 

## Does the Tax Calculation service work with withholding tax? 

Withholding tax is currently not in the scope of the Tax calculation service. Instead, withholding tax is still using the existing WHT engine. 

## Will return orders be supported? 

Yes. Both sales and purchase return orders are supported in version 10.0.21. The list of supported transaction types can be found in [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions). 

## Will free text invoices be supported? 

Yes. Free text invoices will be supported in version 10.0.23. The list of supported transaction types can be found in [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).  

## Will the tax service support the resource/non-stocked based and stocked/production-based deployment options for Dynamics 365 Project Operations? 

We plan to support these deployment types after the Tax Calcuation service has reached General availability. The list of supported transaction types can be found in [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).

## Will the Tax Calculation service ultimately replace the existing Finance tax engine, or will that remain supported longer term? 

The existing tax engine will co-exist with the Tax Calculation service for now. At this time, there are no plans to retire the existing tax engine. The Tax Calculation service will continue to provide more advanced features. For more information, see [Tax Calculation overview](global-tax-calcuation-service-overview.md).

## If a transaction is posted with incorrect tax, how can it be corrected? 

The correction process is the same as today. If you find out that tax is incorrect before posting, make a tax amount adjustment or adjust the applicability rule by changing tax groups. If the incorrect tax calculation is found after the posting, reverse the posted document or post a tax adjustment journal. 

## What are the triggers for the Tax Calculation service to be called?  

The triggers for the Tax Calculation service in Finance and Operations apps are the same as the triggers for the existing tax engine today. 

## Why is the drop-down list of values in the “Feature setup name” field blank on the Tax calculation parameters?

The tax calculation feature should be completed and published in RCS. Verify that the tenant between RCS and your Finance and Operations apps is the same.

## Why can’t I turn on the parameter, Enable tax calculation service?

This parameter isn't supported in some countries yet. Check the legal entity primary address against the [supported countries/regions](global-tax-calcuation-service-overview.md#supported-countriesregions) list.

## What if the Feature name is empty in the Feature management workspace?

If the **Feature name** is blank in the **Feature management** workspace, check the following:

 - If the application version contains hotfix [KB597182](https://fix.lcs.dynamics.com/Issue/Details?bugId=597182&dbType=3).
 - If the batch service is running. If the service isn't running, start it.
 - If the status of batch job, **Runs Feature Translation population** is complete. To check this, go to **System administration** > **Inquires** > **Batch jobs**. If the batch job is set to **Withhold**, set it to **Wait**. If the job is **Waiting**, wait until it has finished.


