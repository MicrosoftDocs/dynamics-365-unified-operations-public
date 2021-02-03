---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 14, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Andreabichsel
manager: AnnBe
ms.date: 01/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (January 14, 2020)

[!include [banner](includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This article describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2709. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### System unable to generate calendar days when importing through Data Management Framework (381195)

This change corrects an issue where importing calendar days generates the error **Invalid date format**. This error prevents the creation of work calendar date lines.

## Coming soon

A new Dataverse solution will be available soon with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** table changes | <ul><li>**Compensation region** added</li><li>**Financial dimensions** added</li></ul> |
| **Worker** table changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** table changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** table changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup tables | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calendar employment** table | <ul><li>**Work calendar table** added</li></ul> |
