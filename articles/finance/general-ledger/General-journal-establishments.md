---
title: Establishments and registration IDs in general journal
description: This topic provides information on how Establishments and registration IDs are used in General journals.
author: JodiChristiansen
ms.date: 4/24/2026
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24
---

# Establishments and registration IDs in General journals

Starting in Dynamics 365 Finance version 10.0.48, you can enable the Establishment and Registration ID governance on invoices feature in Feature management to control how establishments and registration IDs are applied to invoices across finance workflows. 
This feature introduces validation rules that determine:
•	Whether an Establishment must be specified on an invoice
•	Which Registration IDs are required for each invoice party
•	When invoice posting is blocked because required regulatory identifiers are missing
•	How registration IDs are resolved and immutably stored at posting time 
These validations apply consistently across all invoice entry points, including invoices that originate from General ledger journals.
What is an establishment?
In Dynamics 365 Finance, an establishment represents an operational unit of a legal entity that performs business activities on a stable basis and might require its own regulatory identifiers for invoicing or reporting.  
A single legal entity can have one or more establishments. Although these establishments share the same legal identity, they can maintain separate operational identities for invoicing and compliance purposes. 
Establishments are modeled by:
•	Using existing Operating units
•	Including those operating units in an organizational hierarchy that is assigned the
Enterprise establishment structure purpose
Only operating units that are explicitly included in this hierarchy are treated as valid establishments by the system. 
For more information, see Establishments. 
General ledger invoice scenarios
General journals in the General ledger can be used to create invoices for customers in Accounts receivable and vendors in Accounts payable. When the establishment governance feature is enabled, invoices created from General ledger journals are subject to the same establishment and registration ID requirements as invoices that originate from other modules.[MB1.1][JC1.2]  This includes any journals that have been created but not posted. Once the feature is enabled, review all open journals for the Registration IDs and Establishments. If they are setup to default to new journals they will automatically populate when posting the existing journals. 
Module-specific invoice parameters determine whether:
•	An Establishment must be specified on the invoice
•	Establishment-level registration IDs must be validated during posting 
For example, when the Require establishment on customer invoice parameter or Require establishment on vendor invoice is enabled:
•	The Establishment field becomes available on the General journal, Invoice tab
•	The system attempts to default the establishment from financial dimensions
•	Posting is prevented if an establishment is not specified
•	The establishment value cannot be changed after the invoice is posted 
During posting, the system uses invoice party applicability rules to validate that required registration IDs exist for the legal entity, establishment[EG2.1], customer or vendor invoiced on the transaction. These rules will resolve the correct identifiers based on party role and address purpose and store those identifiers on the posted invoice for audit and compliance purposes.
Example 
Three operating units are setup using the business unit as the operating unit type. 
252 Head office 
253 Regional consulting office
254 Operational back office
The business unit is a financial dimension used in the account structure for the ledger. The three operating units are then added to the Enterprise establishment structure in Organization hierarchies.  
