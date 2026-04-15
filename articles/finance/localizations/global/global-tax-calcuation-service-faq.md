---
title: Tax Calculation FAQ
description: This article provides answers to frequently asked questions about the functionality of the Tax Calculation, including questions about availability.
author: epodkolzina
ms.author: epodkolzina
ms.topic: faq
ms.custom: 
  - bap-template
ms.date: 03/18/2026
ms.reviewer: johnmichalak
---

# Tax calculation FAQ

This article provides answers to frequently asked questions about the functionality of the Tax Calculation.

## Will the Tax Calculation be available on tier-1 machines and on-premises machines?

Yes.

## Do I have to continue to maintain tax codes and sales tax groups in finance and operations and Globalization studio, or can I maintain them in only one place?

You can create and maintain a tax setup in the Tax calculation feature in Globalization studio. When you select the Tax feature on the **Tax calculation parameters** page in finance and operations, the setting synchronizes from Globalization studio to finance and operations.

## Do you have any plans to support Russia, Brazil, and India?

Microsoft doesn't currently plan to support Russia, Brazil, or India. For more information about country/region support, see [Release plans on Dynamics 365 and Microsoft Power Platform release plans](/dynamics365/release-plans/).

## What is the recommendation for global implementations that involve countries or regions such as India? Can I use the Goods and Services Tax (GST) engine that Microsoft provides and the Tax Calculation on the same instance of Dynamics 365 Finance or Dynamics 365 Supply Chain Management, or do I have to have separate instances?

You can use different tax engines for different legal entities. For example, for a legal entity in India, you can use GST that is based on Global Tax Engine (GTE). Then, for other legal entities, you can enable the Tax Calculation.

## If I post a transaction with incorrect tax, how can I correct it?

The correction process is the same as it currently is. If you discover that the tax is incorrect before you post the transaction, you can either make a tax amount adjustment or adjust the applicability rule by changing tax groups. If you discover that the tax is incorrect after you post the transaction, you can either reverse the posted document or post a tax adjustment journal.

## What are the triggers for calling the Tax Calculation?

The triggers for the Tax Calculation in finance and operations apps are the same as the current triggers for the existing tax engine.

## On the Tax calculation parameters page, why is the list of values in the Feature setup name field blank?

You need to complete and publish the Tax calculation feature in Globalization studio. 

## Why can't I turn on the Enable advanced tax calculation parameter?

The **Enable advanced tax calculation** parameter isn't yet supported in some countries and regions. Make sure that the primary address of the legal entity is in one of the [supported countries/regions](global-tax-calcuation-service-overview.md#supported-countriesregions).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]