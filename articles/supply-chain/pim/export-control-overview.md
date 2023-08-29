---
title: Advanced export control overview
description: This article provides information about the advanced export control solution that lets you manage, track, and check export compliance.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 08/29/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Advanced export control overview

Companies that trade internationally in goods that are subject to external regulations and internal policies must keep track of many rules and policies. The advanced export control solution lets you express these rules, even complex ones, by using formulas that are similar to the formulas in Microsoft Excel. The system then ensures that the rules are honored throughout the sales and fulfillment process.

Dynamics 365 Supply Chain Management lets you manage, track, and verify compliance with export control restrictions before you confirm, pick, pack, ship, and invoice sales orders. You manage your export control policies by using a native Dataverse solution that interfaces directly with your Supply Chain Management instance. Supply Chain Management then enforces compliance with international trade regulations by consulting your export control policies in real time. Because the architecture is based on Dataverse, many other systems that you use can also access your export control rules through the hundreds of connectors that are available for Dataverse. You can also use the rich features of Microsoft Power Platform, such as the [Microsoft Power Fx](/power-platform/power-fx/overview) language, to extend the solution. In this way, your export control administrator can support complex scenarios by using formulas that are similar to the formulas in Excel.

The advanced export control solution provides the foundation for managing, tracking, and verifying export compliance. You can use it both with and without Supply Chain Management. The solution implements five primary concepts:

- Jurisdictions
- Codes and categories
- Restrictions
- Exceptions
- Licenses

## Jurisdictions

A jurisdiction is a set of codes, categories, restrictions, exceptions, and licenses. It represents a set of configurations that apply to incoming requests. Each jurisdiction is associated with a set of rules that indicate when the jurisdiction applies. If a rule is configured as an error, any activity that matches the rule is blocked for that jurisdiction, unless an exception exists. A rule is usually a combination of a country/region, a transaction purpose, and a set of codes and categories.

Here are some examples of export control jurisdictions:

- US International Traffic in Arms Regulation (ITAR)
- The Wassenaar Arrangement
- EU Dual Use
- Norway Liste I and II
- US Export Administration Regulations (EAR)
- Controls on exports by an individual company
- Multilateral Export Controls
- Sanctions

Jurisdictions don't have to be based on countries/regions. They can also be configured to control export activities based on your company's own policies.

## Codes and categories

The codes that make up a jurisdiction are often referred to as Export Control Classification Numbers (ECCNs). If you use the export control functionality for customs scenarios, Harmonized System (HS) codes might also be used. Codes can be linked to one or more control categories, such as *Missile Technology* or *National Security*. The set of codes and categories is unique for each jurisdiction. Each ECCN can be a member of zero or more control categories, and each control category can contain many ECCNs.

An example of an ECCN is *7A994*, which is defined by the US EAR export control jurisdiction. This ECCN applies to "Other navigation direction finding equipment, airborne communication equipment, all aircraft inertial navigation systems not controlled under 7A003 or 7A103, and other avionic equipment, including parts and components." According to the US EAR, ECCN 7A994 is a part of the *Anti Terrorism (AT)* control category.

Because ECCNs and control categories are defined by export control jurisdictions, the same ECCN can appear in more than one export control jurisdiction. Therefore, you must always specify which jurisdiction a code references. HS codes, which are used primarily for customs tracking, can also be used to manage export controls that are related to customs.

## Restrictions

Each export control jurisdiction defines a set of restrictions under which export actions should be disallowed unless an exception exists. A restriction is a set of ECCNs and/or control categories, together with a country/region, transaction purpose, and other aspects.

Often, restrictions are defined in terms of a commerce country/region chart, as in [this downloadable example from the US EAR](https://www.bis.doc.gov/index.php/documents/regulations-docs/2253-supplement-no-1-to-part-738-commerce-country-chart/file). In the example in the following illustration, a rule for the US EAR restrictions is defined based on the country/region chart. According to this rule, if an order contains any items that have an ECCN in the *MT* or *NS* control category, the system won't allow it to be sold to Angola. If a user tries to confirm an order that contains one of these items for shipment to Angola, they receive the following error message: "Action blocked by US EAR restrictions."

[<img src="media/export-control-restriction.png" alt="Example rule for the US EAR restrictions." title="Example rule for the US EAR restrictions" width="720" />](media/export-control-restriction.png#lightbox)

## Exceptions

Exceptions allow an action that a restriction would otherwise block. Common types of exceptions include blanket exemptions and corporate policies. Exceptions are defined in the same way as restrictions. However, they also provide extra requirements that apply when the exception is used. For example, a message might have to be shown to the user, or text and licenses might have to be printed on documents.

The following illustration shows an example of the setup for an exception.

[<img src="media/export-control-exception.png" alt="Example of an exception." title="Example of an exception" width="720" />](media/export-control-exception.png#lightbox)

## Licenses

Authorities issue licenses to give a company specific permission to trade in restricted items, or a set of restricted items, in a specific context. It's a common practice to specify the license under which an item can be traded for each transaction.

## Next steps

- [Enable and configure advanced export control](export-control-configure.md)
- [Work with advanced export control for products and sales orders](export-control-use.md)
