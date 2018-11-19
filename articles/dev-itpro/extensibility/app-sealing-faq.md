---
# required metadata

title: Extensibility FAQ
description: This topic provides answers to some frequently asked questions about extensibility.
author: FrankDahl
manager: AnnBe
ms.date: 10/24/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9

---

# Extensibility FAQ

[!include [banner](../includes/banner.md)]

## Will source code be available after the hard seal?

Yes, source code will be available after the hard seal. It's required for effective implementation and debugging.

## How do I contact Microsoft if I have an extensibility request?

There is a special extensibility request form on the Lifecycle Services (LCS) site. 

## Where can I ask questions about extensibility patterns?

You can gain access to the Operations Extensibility group in Yammer. Operations Extensibility is an active group that has a significant amount of partner engagement. You get access via the Connect site by signing an NDA.

## Where can I find documentation about extensibility patterns?

Documentation about extensibility patterns is available on the [Extensibility home page](extensibility-home-page.md).

## Where can I get information about extensibility training?

We will announce training sessions in multiple ways. AppSource partners might receive direct invitations for some sessions. We will also announce workshops in the Operations Extensibility Yammer group and other forums.  

## What is the goal of sealing the application?

The application is being sealed as a step toward reducing upgrade costs in the ecosystem, so that customers can stay current on new releases. Customers can take advantage of new innovations that come from Microsoft and partners.

Extension packages enable better performance at design time, faster build automation, and unit testing. They also provide more efficient distribution and installation of models from independent software vendors (ISVs) and customers across different systems.

## What is Microsoft working on to support this move?

There are several areas where the product team is working to improve the extensibility of the product. This work ranges from platform changes that have broad impact to refactored application code that provides additional hook points. For details, see the Operations Extensibility Yammer group and the product release notes.

## After the application is sealed, what should customers do in a critical situation if they must make a quick change?

This scenario is very similar to a scenario where a critical bug fix is required, and the same process should be followed. As a required first step, you must create a case for support.

## Can I overlayer an ISV solution after the hard seal of the application code?

We recommend that ISVs also seal their models. This step helps achieve the broader goal of reducing upgrade costs. 

## Will I be able to overlayer an on-premises solution?

On-premises solutions will follow the same patterns as cloud solutions. Therefore, no overlayering of Microsoft code will be supported.
    
## How often will Microsoft provide external updates so that partners can see what extensibility enhancements have been made?

We plan to provide monthly updates of platform and application after Microsoft Dynamics 365 for Finance and Operations release 8.0.

## Why wasn't my extensibility request accepted?

Some extensibility requests break changes. Some of the more common potentially breaking requests are listed here along with potential workarounds. In addition, read [Creating extensions](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/add-enum-value) to understand the existing platform extension capabilities and [Tips for logging extensibility requests](https://blogs.msdn.microsoft.com/mfp/2018/09/15/tips-for-logging-extensibility-requests/) to learn more about how to create solid requests if a capability doesn't exist in the latest release.

### Why can't a unique table index be made extensible?

- Request: Make unique table indexes changeable via extension, for example by allowing an extra field to be added.
- Problem: If a unique table index changes and any data does not conform to the new index, then it would be a breaking change. Also, any query would affect it since it can now retrieve a non-unique record. For example, if a Person table had a key of "Name" and select person where name="Chris" works, but if BirthDate was added to the key, now there could be multiple records returned for "Chris".
- Workaround: Add "soft" constraints in the validateWrite or validateInsert methods.

### Why can't CountryRegionCode be made extensible? (*it already is*)
- Request: Make CountryRegionCode changeable via extension.
- Problem: Starting with Platform update 14, changes to CountryRegionCode are supported if the CountryRegionCode property already has a value. Empty CountryRegionCode properties cannot be changed because that change is more restrictive (the element would now only be available for certain countries/regions) and therefore would be a breaking change.
- Workaround: Use the existing CountryRegionCode extension capability when the element is already country/region specific.

### Why can't the Table Field properties AllowEdit, AllowEditOnCreate, Mandatory, or IgnoreEDTRelation be made extensible?
- Request: Make Table Field properties AllowEdit, AllowEditOnCreate, Mandatory, and/or IgnoreEDTRelation changeable via extension.
- Problem: The ability to change the "Allow Edit", "Allow Edit On Create", "Mandatory", and "IgnoreEDTRelation" properties on Table Fields would result in breaking changes. Changing a field to allow editing changes the intent of the field. Not allowing a field to be edited can break existing behavior. Changing a relation breaks the original intent of that relation, which is a breaking change. Making a field mandatory can result in breaking existing behavior.
- Workaround: Add new Table Fields via extension and control those as needed.
