---
title: Advanced export control overview
description: Manage, track, and check export compliance with an advanced export control solution that implements five primary concepts (jurisdictions, codes and categories, restrictions, exceptions, and licenses).
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Advanced export control overview

Companies that trade internationally in goods that are subject to external regulations and internal policies need to keep track of many different rules and policies. The advanced export control solution lets you express these rules, including complex ones, using formulas similar to those in Microsoft Excel. The system ensures that the rules are honored throughout the sales and fulfillment process.

Supply Chain Management lets you manage, track, and verify compliance with export control restrictions prior to confirming, picking, packing, shipping, and invoicing sales orders. You manage your export control policies using a native Microsoft Dataverse solution that interfaces directly with your Supply Chain Management instance. Supply Chain Management then enforces compliance with international trade regulations by consulting your export-control policies in real time. The Dataverse-based architecture means that many of the other systems you use can also access your export control rules thanks to the hundreds of connectors available for Dataverse.  Likewise, you can use the rich features of Microsoft Power Platform (like the [Microsoft Power Fx](/power-platform/power-fx/overview) language) to extend the solution, allowing your export control administrator to support complex scenarios using formulas like those in Microsoft Excel.

The advanced export control solution provides the foundation for managing, tracking, and checking export compliance. You can use it both with and without Supply Chain Management. The solution implements five primary concepts:

- Jurisdictions
- Codes and categories
- Restrictions
- Exceptions
- Licenses

## Jurisdictions

A jurisdiction is a set of codes, categories, restrictions, exceptions, and licenses. It represents a set of configurations that apply to incoming requests. Each jurisdiction is associated with a set of rules that indicate when the jurisdiction applies. If a rule is configured as an error, then any activity matching the rule will be blocked for that jurisdiction unless an exception exists. A rule is usually a combination of a country, a transaction purpose, and a set of codes and categories.

The following list provides a set of examples of export control jurisdictions:

- US International Traffic in Arms Regulation (ITAR)
- The Wassenaar Arrangement
- EU Dual Use
- Norway Liste I and II
- US Export Administration Regulations (EAR)
- Controls on exports by an individual company
- Multilateral Export Controls
- Sanctions

Jurisdictions don't necessarily need to be based on countries/regions. They can also be configured to control export activities based on your company's own policies.

## Codes and categories

The codes that make up a jurisdiction are often referred to as Export Control Classification Numbers (ECCNs). If you use the export control functionality for customs scenarios, then Harmonized System (HS) codes may also be used. Codes can be linked to one or more control categories such as *Missile Technology* or *National Security*. The set of codes and categories is unique for each jurisdiction. Each ECCN may be a member of zero or more control categories, and each control category may contain many ECCNs.

An example of an export control classification number is *7A994*, which is defined by the United States Export Administration Regulations (US EAR) export control jurisdiction. This classification number applies to "Other navigation direction finding equipment, airborne communication equipment, all aircraft inertial navigation systems not controlled under 7A003 or 7A103, and other avionic equipment, including parts and components." According to the US EAR, ECCN 7A994 is a part of the *Anti Terrorism (AT)* control category.

Because ECCNs and control categories are defined by export control jurisdictions, the same ECCN may appear in more than one export control jurisdiction. For this reason, you must always specify which jurisdiction a code references. HS codes, which are used primarily for customs tracking, may also be used as codes to manage export controls related to customs.

## Restrictions

Each export control jurisdiction defines a set of restrictions under which export actions should be disallowed unless an exception exists. Often, restrictions are defined in terms of a commerce country/region chart, as seen in [this downloadable example from the US EAR](https://www.bis.doc.gov/index.php/documents/regulations-docs/2253-supplement-no-1-to-part-738-commerce-country-chart/file). A restriction is a set of ECCNs and/or control categories, together with a country, transaction purpose, and other aspects.

The following screenshot shows a sample rule for the US EAR restrictions based on the country chart. Based on this rule, the system wouldn't allow any order containing an item with an ECCN in the MT or NS control categories to be sold to Angola. If a user attempted to confirm an order containing one of these items to be shipped to Angola, they would see the error message "Action blocked by US EAR restrictions."

[<img src="media/export-control-restriction.png" alt="Example rule for the US EAR restrictions." title="Example rule for the US EAR restrictions" width="720" />](media/export-control-restriction.png#lightbox)

## Exceptions

Exceptions allow an action even though a restriction would otherwise block it. Common types of exceptions include blanket exemptions, and corporate policies. Exceptions are defined the same way as restrictions, but also provide extra requirements that apply when the exception is used, such as the need to display a message to the user or to print text and licenses on documents.

The following screenshot shows an example exception setup.

[<img src="media/export-control-exception.png" alt="Example of an exception." title="Example of an exception" width="720" />](media/export-control-exception.png#lightbox)

## Licenses

Licenses are issues by authorities to provide specific permissions that allow a company to trade restricted items, or a set of restricted items, in a specific context. It's a common practice to specify the license under which an item can be traded for each specific transaction.

## Next steps

- [Enable and configure advanced export control](export-control-configure.md)
- [Work with advanced export control in products and sales orders](export-control-use.md)
