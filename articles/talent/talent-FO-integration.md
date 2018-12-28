---
# required metadata

title: Talent to Finance and Operations integration
description: This topic explains what data is synchronized in a Talent and finanace and Operations integration.
author: Darinkramer
manager: AnnBe
ms.date: 12/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: Talent

---

# Talent to Finance and Operations integration

[!include [banner](includes/banner.md)]

**Scenario: Is all data synchronized or just some data entities?**

With Core HR, a subset of the data is synchronized. You can find a list of all
the entities here:
https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/talent-financeandoperations-integration

For Attract and Onboard, all data is native to CDS for Apps.

**Scenario: Can I create a new mapping from scratch without using the
templates?**

Templates are the starting point. You can create your own template, but a
template is always needed when creating an integration project. You can find
more information about data integrator (DI), templates, and projects here:
<https://docs.microsoft.com/en-us/powerapps/administrator/data-integrator>

**Scenario: Can I map financial dimensions to transfer between Talent and
Finance and Operations?**

Financial dimensions aren’t currently in CDS for Apps and as a result aren’t
part of the default template. This entity is something that is planned, but no
timeline is available at this point.

For data that resides in Finance and Operations but does not exist in Talent,
linking the two systems together via “Configure Links” in Talent. For more
information on configuring links between Talent and Finance and Operations visit
the what’s new link below.

https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/whats-new-talent-october-31

![](media/e3284e2a58880a2d680b1b22156f3372.png)

**Scenario: Often when I import employees, they go into inactive workers on
Finance and Operations, is there any obvious reason this might be?**

You may get this error if employees don’t have an active employment detail
record in Talent. To verify, navigate to Personnel
Management\>Employees\>Employment History\>Date Manager, verify there is an
active employment detail record.

**Scenario: If we select to map only a subset of fields, will changes made to
non-mapped fields trigger a sync?**

Data sync follows the execution schedule. The integration will pick up a record
if any field in the record changes regardless whether the field is part of
integration mapping or not.

**Scenario I want to send only active worker changes but not the terminated
records**

With the use of Advanced query, you can filter and reshape source data before
passing it into destination.

![](media/7933e9e7cf373fcdc11a3c716f024b4e.png)

**Scenario: Can I specify which fields to send to Finance and Operations for a
specific entity?**

Fields can be added or removed from the integration task. Not all data fields
that exist on the CDS for Apps (CDS 2.0) entity will be populated from Core HR.
Additional data may be populated via PowerApps.

![](media/972f11442c01ea4064e45795382055a9.png)

**Scenario: Set up integration as batch job and lost connection to destination
system, how can we send the same set of changes to destination system?**

No special setup required for exception handling. The Data Integrator will
automatically catch and report errors happened at source/destination and will
allow manual retries. However, it doesn’t allow manual data correction. If data
needs massaging that should happen either at source or destination.

**Scenario: Can I set up Bi-Directional Integration?**

No, the Integration at this point of time is one-way (Talent to Finance and
Operations). We have a default template available to send data from Talent to
Finance and operations.

**Scenario: Can I allow record deletion as part of my integration?**

No, Data integrator will not capture deleted records for data transfer. Only
data creation and updates (UPSERT) are currently included.

**Scenario: Can I rerun the errored execution, if so, will it send a full file
or changes only?**

The first run of data integrator is always a full run, subsequent runs are
based on change tracking. When an error run is executed, it extracts the records
in scope of the run and sends out the most recent changes from CDS.

**Scenario: Saving the project is throwing and error “Project has mapping
errors”**

Check and set up integration keys, then refresh the entities in the project.

When the default template is used, the integration keys will be
automatically imported, the above issue may occur when new tasks are added to
the existing template.

**Scenario: If I have N number of legal entities where workers have employments,
do I need to create a mapping for each of them?**

Yes, for each legal entity in Finance and Operations, you'll need a separate
integration project in the data integration.

**Scenario: I need to transfer data which is not part of the default template
provided by Microsoft. Can this be done?**

Yes, the template can be modified to include additional data from other CDS for
Apps entities. The entity must be in CDS for Apps for it to be included in the
template. Additionally, fields can be added to or removed from the existing
template.

**Scenario: I just started with a newly created Finance and Operations
environment and Talent environment and I am getting the error: The data value
violates integrity constraints.**

Reasons for this error can include:

- The data transfer resulted in duplicate records extraction at source (CDS).

- Data transfer has null values for fields which are mandatory in Finance and
Operations. Verify the data that is in CDS and meets the requirements of Finance and
Operations.

**Scenario: If there are errors in execution and the Employee ID did not sync,
how do I navigate to the right history job which has the failed employee?**

Data integrator will create multiple projects in Finance and Operations. The
relationship between data integrator task and the Finance and Operations project
is one to one.

Trace the time from data integrator execution history and look for index -1
project in Finance and Operations. If the task \# is 9 in data integrator and
then the index in Finance and Operations is 8.

1. Capture Task index from data integrator. (In this case it is 9.)

![](media/1801a3b66b1ac2b5f344737d0f59cee0.png)

1. Track time of execution of project.

![](media/7a18e2f06607a94711e34c81ad754203.png)

1. In Finance and Operations, identify index - 1. In this case, the
project with suffix 8 and execution time of index 0 project matches with
execution time in Step 2.

![](media/18790db37e8d4dfd81590534d899b992.png)

**Scenario: After integrating Talent and Finance and operations, I don’t see my
talent data in Finance and Operations.**

The integration to Finance and Operations is a two-step process. First verify
that the talent data is updated and available in CDS. This is a near real time
sync and can be verified in PowerApps by looking at the data within the data
entities.

![](media/dbfb351a24b74e60283055598f4e1f1f.png)

If the data is not appearing as expected in CDS, verify that the entity is
supported in the integration. To include additional data in CDS, this will
require a change on the Microsoft side.

If the entity is supported and the data is available in CDS, Verify the mapping
is correct in the Data Integrator. If the integrator mapping looks good, then
verify the data management Jobs have successfully run. Errors may occur during
the execution of the batch jobs. For more information on Data Management see
documentation at the link below.

**Scenario: The addresses for my employees are incorrect when importing them into
Finance and Operations.**

The number sequence for Location ID uses the same pattern in both Talent and
Finance and Operations. The number sequence needs to be unique on both sides so
there are not address collisions when integrating data from CDS to Finance and
Operations.

During implementation of Talent verify Number Sequences are not the same in
Talent and Finance and Operations. Validate that all number sequences are not
identical where data may be maintained in both systems.

**Scenario: When creating my connection set, I am unable to see the connection in
the connection drop down.**

Make sure when creating your connections, make sure you choose Dynamics 365 for
Operations (currently in preview) and Common Data Service.

**Scenario: When syncing employments, I get errors like “CompanyInfo_FK” doesn’t
exist and “The value '12/31/2154 11:59:59 pm' in field 'Employment end date' is
not found in the related table 'Employment'.”**

Ensure that you are mapping to the correct legal entities. Legal entity syncing
is not part of the default template, so it is expected that for each legal
entity that is present in Talent/CDS is also present in Finance and Operations.
Also, make sure that you are selecting the correct legal entities for the
associated Connection Set.

**Scenario: After setting up project, field mapping on finance side seem to be
empty.**

Refresh data entities in Finance and Operations: **Data management \> Framework
Parameters \> Entity settings \> Refresh entity list.** This should take couple
of minutes to complete then you should see those mappings; this issue happens
when you Spun up brand new

![cid:image002.png\@01D49839.6C126650](media/edf1033809985cfd217308af8d5f98af.png)

cid:image002.png\@01D49839.6C126650

cid:image002.png\@01D49839.6C126650

**Useful links:**

Data Integrator (DI):

<https://docs.microsoft.com/en-us/powerapps/administrator/data-integrator>

<https://docs.microsoft.com/en-us/powerapps/administrator/data-integrator-error-management>

<https://docs.microsoft.com/en-us/powerapps/administrator/powerapps-gdpr-dsr-guide-systemlogs>

Data Management:

https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/data-entities-data-packages?toc=/fin-and-ops/toc.json
