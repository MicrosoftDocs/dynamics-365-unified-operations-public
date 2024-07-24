---
title: Tax Calculation FAQ
description: Access answers frequently asked questions about the functionality of the Tax Calculation service, including questions about availability.
author: epodkolzina
ms.author: epodkolzina
ms.topic: faq
ms.custom: 
  - bap-template
ms.date: 10/26/2021
ms.reviewer: johnmichalak
ms.dyn365.ops.version: AX 10.0.21
---

# Tax Calculation FAQ

This article answers frequently asked questions about the functionality of the Tax Calculation service.

## When will the Tax Calculation service be generally available?

The Tax Calculation service is generally available as of version 10.0.21, which was released in October 2021. For more information, see [Tax calculation enhancements are now available for Dynamics 365](https://cloudblogs.microsoft.com/dynamics365/bdm/2021/10/26/tax-calculation-enhancements-are-now-available-for-dynamics-365/) on the Microsoft Dynamics 365 blog.

## Will the Tax Calculation service be available on Tier-1 machines for testing?

No. At a minimum, Tier 2 is required for testing.

## Will on-premises customers be able to use the Tax Calculation service?

No, the Tax Calculation service isn't currently supported for on-premises.

## Do I have to continue to maintain tax codes and sales tax groups in finance and operations apps and Regulatory Configuration Service (RCS), or will there eventually be an integration, so that maintenance is required in only one application?

A tax setup can be created and maintained in the Tax calculation feature in RCS. When the Tax feature is selected on the **Tax calculation parameters** page in finance and operations apps, the setting is synchronized from RCS to your finance and operations apps.

## Do you expect the performance to be better than the performance of the existing finance and operations apps tax engine?

The performance of the Tax Calculation service is better than the performance of the existing tax engine.

## Do you have any plans to support Russia, Brazil, China, and India?

We don't currently plan to support Russia, Brazil, China, or India. For more information about country/region support, see [Release plans on Dynamics 365 and Microsoft Power Platform release plans](/dynamics365/release-plans/).

## What is the recommendation for global implementations that involve countries or regions such as India? Can I use the Goods and Services Tax (GST) engine that Microsoft provides and the Tax Calculation service on the same instance of Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or do I have to have separate instances?

You can use different tax engines for different legal entities. For example, for a legal entity in India, you can use GST that is based on Global Tax Engine (GTE). Then, for other legal entities, you can enable the Tax Calculation service.

## Does the Tax Calculation service work with withholding tax?

Withholding tax isn't currently in the scope of the Tax Calculation service. Withholding tax still uses the existing WHT engine.

## Will return orders be supported?

Yes, both sales return orders and purchase return orders are supported in version 10.0.21. For the list of supported transaction types, see [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).

## Will free text invoices be supported?

Yes, free text invoices will be supported in version 10.0.23. For the list of supported transaction types, see [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).

## Will the Tax Calculation service support the resource/non-stocked-based and stocked/production-based deployment options for Dynamics 365 Project Operations?

We plan to support these deployment types after the Tax Calculation service has reached General availability. For the list of supported transaction types, see [Supported transactions](global-tax-calcuation-service-overview.md#supported-transactions).

## Will the Tax Calculation service eventually replace the existing Finance tax engine, or will that tax engine continue to be supported over the longer term?

For now, the existing tax engine will co-exist with the Tax Calculation service. There are currently no plans to retire the existing tax engine. The Tax Calculation service will continue to provide more advanced features. For more information, see [Tax Calculation overview](global-tax-calcuation-service-overview.md).

## If a transaction is posted with incorrect tax, how can it be corrected?

The correction process is the same as it currently is. If you discover that the tax is incorrect before you post the transaction, you can either make a tax amount adjustment or adjust the applicability rule by changing tax groups. If you discover that it's incorrect after you post the transaction, you can either reverse the posted document or post a tax adjustment journal.

## What are the triggers for calling the Tax Calculation service?

The triggers for the Tax Calculation service in finance and operations apps are the same as the current triggers for the existing tax engine.

## On the Tax calculation parameters page, why is the list of values in the Feature setup name field blank?

The Tax calculation feature should be completed and published in RCS. Verify that the tenant between RCS and your finance and operations apps is the same.

## Why can't I turn on the Enable tax calculation service parameter?

The **Enable tax calculation service** parameter isn't yet supported in some countries and regions. Make sure that the primary address of the legal entity is in one of the [supported countries/regions](global-tax-calcuation-service-overview.md#supported-countriesregions).

## What should I do if the Feature name field in the Feature management workspace is blank?

If the **Feature name** field in the **Feature management** workspace is blank, verify the following information:

- The application version contains hotfix [KB597182](https://fix.lcs.dynamics.com/Issue/Details?bugId=597182&dbType=3).
- The batch service is running. If it isn't running, start it.
- The status of the **Runs Feature Translation population** batch job is **Complete**. To verify the job's status, go to **System administration** \> **Inquiries** \> **Batch jobs**. If the batch job is set to **Withhold**, set it to **Wait**. If the job's status is **Waiting**, wait until the job has finished running.

