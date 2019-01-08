---
# required metadata

title: Retail transaction consistency checker
description: This topic describes the retail transaction consistency checker functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 1/08/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Distributed order management (DOM)
**Retail transaction consistency checker**

**Overview**

With Retail statement posting, it has been observed that the posting
process fails at times due to inconsistent data in the retail
transaction tables. The data in the retail transaction tables get
inconsistent either due to a bug in the POS application or when these
transactions are incorrectly imported from third party POS systems. Some
examples of this inconsistent data that has been observed in the past
are a) transaction total on the header table does not match the
transaction total on the lines b) line count on the header table does
not match with the no. of lines in the transaction table c) taxes on the
header table does not match the tax amount on the lines etc. When these
inconsistent transactions are picked up by statement posting process, it
ends up creating inconsistent Sales invoices & payment journals and the
entire statement posting process fails as a result. Recovering the
statements from such a state involves complex data fixes across multiple
transaction tables.

To address this issue and to identify & isolate these inconsistent
transactions before they are picked up by the statement posting process,
a consistency checker feature has been introduced and the below chart
explains the posting process with the transaction consistency checker

<img src="media/image1.png" style="width:6.5in;height:3.10556in" />

**Consistency checker**

-   A new batch process called as “Validate store transactions” has been
    introduced under the area path: ‘Retail &gt; Retail IT &gt; POS
    posting’ which needs to be configured for periodic runs. The set-up
    of this batch process is very similar to the ‘Calculate statement in
    batch’ and ‘Post statement in batch’ process wherein the batch job
    can be scheduled based on Store organization hierarchy. It is
    recommended that customers configure this batch process to run
    multiple times in a day and schedule it such that it runs at the end
    of every P-job execution. In the current release, this batch process
    checks the consistency for the retail transaction tables for the
    below two scenarios:

    -   Customer account: Validates the customer account on the retail
        transaction tables exist in the HQ customer master

    -   Line count: Validates that the no. of lines as captured on the
        transaction header table matches the no. of lines in the sales
        transaction tables.

-   The result of the validation check by the batch process are
    appropriately tagged on the retail transaction. Accordingly, the
    “Validation status” field on the retail transaction record is either
    set to “Successful” or “Error” and the date of the last validation
    run is set on the field “Last validation time”.

-   Users can have more descriptive error text of the validation failure
    by selecting the relevant retail store transaction record and
    clicking on the “Validation errors” button

-   Transactions that fail the validation check or transactions that
    have not been validated will not be pulled into the statements.
    During the Calculate statement process, users will get notified if
    there are transactions that could have been included on the
    statement but have not been done so as they are failing the
    validation check or have not been validated.

-   As of date, the only mechanism to fix the transaction with
    validation errors is by contacting Microsoft Support. In a future
    release, capability will be built for users to fix the validation
    failed records through the user interface and adequate logging &
    auditing capabilities will be made available to trace the history of
    the modifications.

Notes:

-   Additional rules for consistency check will be added in future
    releases to ensure that the transactions records are validated for
    all the possible scenarios before they are pulled into statements
