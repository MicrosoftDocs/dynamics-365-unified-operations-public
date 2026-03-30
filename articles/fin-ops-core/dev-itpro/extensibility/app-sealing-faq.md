---
title: Extensibility FAQ
description: Access answers to some frequently asked questions about extensibility, including questions related to source code, documentation, and more.
author: FrankDahl
ms.author: johnmichalak
ms.topic: faq
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Extensibility FAQ

[!include [banner](../includes/banner.md)]

## Will source code be available after the hard seal?

Yes, source code is available after the hard seal. It's required for effective implementation and debugging.

## How do I contact Microsoft if I have an extensibility request?

Use the special extensibility request form on the Lifecycle Services (LCS) site.

## Where can I ask questions about extensibility patterns?

You can gain access to the Operations Extensibility group on Microsoft Viva Engage. Operations Extensibility is an active group that has a significant amount of partner engagement. You get access via the Connect site by signing an NDA.

## Where can I find documentation about extensibility patterns?

Documentation about extensibility patterns is available on the [Extensibility home page](extensibility-home-page.md).

## Where can I get information about extensibility training?

The product team announces training sessions in multiple ways. Marketplace partners might receive direct invitations for some sessions. The team also announces workshops in the Operations Extensibility group on Microsoft Viva Engage and other forums.  

## What is the goal of sealing the application?

Sealing the application reduces upgrade costs in the ecosystem, so that customers can stay current on new releases. Customers can take advantage of new innovations that come from Microsoft and partners.

Extension packages enable better performance at design time, faster build automation, and unit testing. They also provide more efficient distribution and installation of models from independent software vendors (ISVs) and customers across different systems.

## What is Microsoft working on to support this move?

The product team is working on several areas to improve the extensibility of the product. This work ranges from platform changes that have broad impact to refactored application code that provides additional hook points. For details, see the Operations Extensibility group on Microsoft Viva Engage and the product release plans.

## After the application is sealed, what should customers do in a critical situation if they must make a quick change?

This scenario is similar to a scenario where a critical bug fix is required, and the same process should be followed. As a required first step, create a case for support.

## Can I overlayer an ISV solution after the hard seal of the application code?

We recommend that ISVs also seal their models. This step helps achieve the broader goal of reducing upgrade costs.

## Will I be able to overlayer an on-premises solution?

On-premises solutions follow the same patterns as cloud solutions. Therefore, no overlayering of Microsoft code is supported.

## How often will Microsoft provide external updates so that partners can see what extensibility enhancements have been made?

We plan to provide monthly updates of platform and application after Microsoft Dynamics 365 for Finance and Operations release 8.0.

## Why wasn't my extensibility request accepted?

Some extensibility requests break changes. Some of the more common potentially breaking requests are listed here along with potential workarounds. In addition, read [Creating extensions](add-enum-value.md) to understand the existing platform extension capabilities and [Tips for logging extensibility requests](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/tips-for-logging-extensibility-requests) to learn more about how to create solid requests if a capability doesn't exist in the latest release.

### Why can't EDT.StringSize be made extensible?

- Request: Make EDT.StringSize changeable via extension.
- Problem: When a table string field (FieldX) is of type "parent EDT" and is associated (through table relations) with another table's field (FieldY) of type EDT2 (EDT2 is derived from "parent EDT"). If FieldY could have a larger string by allowing EDT2.StringSize to increase, FieldX can't handle the new string size.
- Workaround: Create a new EDT and use that for the table field FieldY.

### Why can't a unique table index be extensible?

- Request: Make unique table indexes changeable via extension, for example by allowing an extra field to be added.
- Problem: If a unique table index changes and any data doesn't conform to the new index, the change breaks compatibility. Also, any query that retrieves a non-unique record is affected. For example, if a Person table had a key of "Name" and `select person where name="Chris"` works, but if BirthDate was added to the key, now there could be multiple records returned for "Chris".
- Workaround: Add "soft" constraints in the `validateWrite` or `validateInsert` methods.

### Why can't CountryRegionCode be extensible? (*it already is*)

- Request: Make CountryRegionCode changeable via extension.
- Problem: Starting with Platform update 14, changes to CountryRegionCode are supported if the CountryRegionCode property already has a value. Empty CountryRegionCode properties can't be changed because that change is more restrictive (the element is now only available for certain countries/regions) and therefore is a breaking change.
- Workaround: Use the existing CountryRegionCode extension capability when the element is already country/region specific.

### Why can't the Table Field properties AllowEdit, AllowEditOnCreate, Mandatory, or IgnoreEDTRelation be extensible?

- Request: Make Table Field properties AllowEdit, AllowEditOnCreate, Mandatory, and/or IgnoreEDTRelation changeable via extension.
- Problem: Changing the "Allow Edit," "Allow Edit On Create," "Mandatory," and "IgnoreEDTRelation" properties on Table Fields results in breaking changes. Changing a field to allow editing changes the intent of the field. Not allowing a field to be edited breaks existing behavior. Changing a relation breaks the original intent of that relation, which is a breaking change. Making a field mandatory breaks existing behavior.
- Workaround: Add new Table Fields via extension and control those as needed.

### Why can't Security Privileges be extensible?

- Request: Make Security Privilege changeable via extension.
- Problem: Changing the Security Privilege results in breaking changes because this privilege is the lowest level of security metadata.
- Workaround: Create a new Security Privilege if needed and use that.

### Why should I avoid calling and extending APIs that are marked with InternalUseOnlyAttribute?

Throughout the application, the development team strives to avoid breaking changes to APIs that customers, partners, or ISVs use. When a class or method has the **InternalUseOnlyAttribute** applied to it, it means that the API is for internal use only and could change without warning. If customers, partners, or ISVs use or extend an API with **InternalUseOnlyAttribute**, they might encounter problems because the API can change at any time. These changes require updates to their extensions before they can apply the update. This situation can lead to urgent changes and the need to recompile. Developers shouldn't depend on these classes and methods remaining unchanged.

Calls to classes and methods with the **InternalUseOnlyAttribute** result in compiler warnings. Starting in Platform update 20 to Platform update 24, targeting classes and methods with **InternalUseOnlyAttribute** by using Chain of Command results in compiler errors. In Platform update 25 and later, the compiler continues to issue warnings.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
