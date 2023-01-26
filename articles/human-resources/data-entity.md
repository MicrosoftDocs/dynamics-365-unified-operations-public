---
# required metadata

title: Human Resources data entities added in Dynamics 365 Human Resources 10.0.32
description: This article provides details aabout the data entities and templates that were added in Dynamics 365 Human Resources 10.0.32.
author: jcart
ms.date: 01/26/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---


# Human Resources data entities and templates

Multiple DMF (Data Management Framework) entities have been added for Human Resources for the 10.0.32 release. Below is a summarized list of entities 
that have been added by module. We will add more detailed documentation about entities and usage later.

## Data entities 

Multiple DMF (Data Management Framework) entities have been added for Human Resources for the 10.0.32 release. Below is a summarized list of entities that have been 
added by module. 

>[!Note]
>You may need to refresh the entity list in your environment to see the new entities. This can be done on the **Refresh entity list**. Go to **Data management workspace>
Framework parameters > Entity settings > Refresh entity list**.

| Module | New entity coverage | Notes |
|-------------------------|-------------|------------|
| Personnel management| I-9 documents, Union agreements, Worker actions, Position actions, Default location, Primary position| |
|Attachment entities for a Worker| Worker, Certificates, Employments, Education, Exam, Person private details, Professional experience, Person screening, Worker bank
account, Injury and incidents, Identification,| All entities include ‘Attachment’ in the Target Entity name|
|Attachment entities| Job, Employment terms, Certificate types, Position, Dir party, electronic address, benefit plan employee, cade detail, fixed comp, Variable comp, 
Courses, Leave request, Discussions, Goals, Performance Journal, Certificates | All entities include ‘Attachment’ in the Target Entity name|
|Task management| Business Process Business process library task group Business process library task grouping Business process generic process Business process generic 
template| Missing Entities |
|Leave and Absence| Leave Bank transaction audit, leave of absence request and Leave type Security role |Newly added entities include, 
LeaveBankTransactionAuditTrailEntity LeaveTypeSecurityRoleEntity LeaveOfAbsenceRequestEntity|
|Case management| FMLA cases, association and certification| Newly added entities include, HcmFMLACaseAssociationEntity HcmFMLACaseCertificationEntity
HcmFMLAEligibilityDatePriorityEntity|
|Legacy benefits | Benefits eligibility, process results, eligibility status, workers, email templates, benefits expiration, ACA 1094C submission||
|Benefits administration| ACA 1094 submission| |
|Compensation| Fixed plan range utilization, performance per Org unit, process lines and actions, recommend event fixed, composite and point in timelines, recommend
event table, compensation structure V2 (dual write), survey companies, document attachments, fixed compensation change history| New entities: 
HRMCompFixedPlanUtilMatrixEntity HRMCompOrgPerfEntity HRMCompProcessLineEntity HRMCompProcessLineActionEntity HRMCompEventLineCompositeEntity HRMCompEventLineFixedEntity 
HRMCompEventLinePointInTimeEntity HRMCompEventLineEntity HcmCompensationStructureDualWriteV2Entity HcmSurveyCompanyEntity HRMCompFixedEmplAttachmentsEntity 
HRMCompVarAwardEmplAttachmentsEntity HcmWorkerActionCompFixedEmplChangeHistoryEntity|
|Foundation| User defined links User defined link base URI| |
|Employee development| Course attendees, Discussions, Goals, Skill mapping, Measurements, Performance journals| |

## Data entity templates
Data templates are a predefined list of entities for each module that can be used in a data project. Multiple default templates have been added to Human Resources 
in the 10.0.32 release. To access the templates, navigate to the Data management workspaceàTemplatesàLoad default templates. After loading the template, you can modify
these templates if needed.

>[Note]
>You may need to refresh the entity list in your environment prior to loading the templates. This can be done on the **Refresh entity list**. Go to **Data management workspace>
Framework parameters > Entity settings > Refresh entity list**.

| Template name | Entities included | Module |
|-------------------------|-------------|------------|
|Case management|<ul><li>Service level agreement</li><li>
</li><li>Case category security by role</li><li>
</li><li>Injury and illness body parts</li><li>
</li><li>Injury and illness cost types</li><li>
</li><li>Injury and illness types</li><li>
</li><li>Injury and illness outcome types</li><li>
</li><li>Injury and illness severity levels</li><li>
</li><li>Injury and illness treatment types</li><li>
</li><li>Case hierarchy</li><li>
</li><li>Case categories</li><li>
</li><li>Injury or illness incidents</li><li>
</li><li>Lead priorities</li><li>
</li><li>Case detail</li><li>
</li><li>FMLA hours</li><li>
</li><li>Injury or illness costs</li><li>
</li><li>Injury or illness filings</li><li>
</li><li>Injury or illness treatments</li></ul>  |  Service management, Sales and Marketing, System administration       |
|Compensation management|<ul><li>Compensation fixed action table</li><li>
</li><li>Compensation survey companies</li><li>
</li><li>Reference point setups</li><li>
</li><li>Reference points</li><li>
</li><li>Compensation grids</li><li>
</li><li>Compensation structure</li><li>
</li><li>Compensation pay frequency</li><li>
</li><li>Compensation variable type</li><li>
</li><li>Compensation fixed plan</li><li>
</li><li>Compensation variable plan V2</li><li>
</li><li>Compensation plan eligibility rules</li><li>
</li><li>Compensation eligibility levelsCompensation vesting rules</li><li>
</li><li>Variable compensation level V2</li><li>
</li><li>Employee fixed compensation</li><li>
</li><li>Employee variable compensation</li><li>
</li><li>Employee variable compensation enrollment V2</li><li>
</li><li>Compensation merit increase target</li><li>
</li><li>Employee variable compensation enrollment overrides</li><li>
</li><li>Process results</li><li>
</li><li>Compensation process table</li><li>
</li><li>Compensation process lines</li><li>
</li><li>Compensation recommend event composite lines</li><li>
</li><li>Compensation recommend event fixed lines</li><li>
</li><li>Compensation recommend event point in time lines</li><li>
</li><li>Compensation recommend event table</li><li>
</li><li>Compensation fixed plan range utilization matrix</li><li>
</li><li>Compensation performance per organization unit</li><li>
</li><li>Compensation performance plan</li><li>
</li><li>Compensation performance allocation</li><li>
</li><li>Compensation performance rating</li><li>
</li><li>Compensation performance allocation lines</li><li>
</li><li>Total compensation statement sections header</li><li>
</li><li>The tax codes in tax groups of the Total compensation statement section</li><li>
</li><li>The benefit codes in benefit group of the Total compensation statement section</li><li>
</li><li>The earning codes of the Total compensation statement section</li></ul>| Human resources|
|Employee development|<ul><li>Certificate type</li><li>
</li><li>Classroom groups</li><li>
</li><li>Course groups</li><li>
</li><li>Course locations</li><li>
</li><li>Education disciplines</li><li>
</li><li>Discussion types</li><li>
</li><li>Goal headings</li><li>
</li><li>Institution</li><li>
</li><li>Rating models</li><li>
</li><li>Skill types</li><li>
</li><li>Performance period</li><li>
</li><li>Performance journal source type</li><li>
</li><li>Performance journal</li><li>
</li><li>Education degree</li><li>
</li><li>Education discipline categories</li><li>
</li><li>Test</li><li>
</li><li>Goal groups</li><li>
</li><li>Performance feedback</li><li>
</li><li>Professional experience competency</li><li>
</li><li>Skill mapping</li><li>
</li><li>Position of trust competency</li><li>
</li><li>Skill-mapping - main</li><li>
</li><li>Hotel</li><li>
</li><li>Course instructors</li><li>
</li><li>Course types</li><li>
</li><li>Classrooms</li><li>
</li><li>Education and discipline category associations</li><li>
</li><li>Performance journal comment entity</li><li>
</li><li>Performance journal entry links</li><li>
</li><li>Certificate competency</li><li>
</li><li>Education competency</li><li>
</li><li>Person exam</li><li>
</li><li>Educational requirements</li><li>
</li><li>Skill-mapping - certificates</li><li>
</li><li>Skill-mapping - education</li><li>
</li><li>Skill-mapping - lines</li><li>
</li><li>Skill-mapping - criteria</li><li>
</li><li>Course Location Picture</li><li>
</li><li>Courses V2</li><li>
</li><li>Course type - certificates</li><li>
</li><li>Course type default dimensions</li><li>
</li><li>Course type - education</li><li>
</li><li>Course type descriptions</li><li>
</li><li>Rating level</li><li>
</li><li>Skills</li><li>
</li><li>Course participants</li><li>
</li><li>Hotel for course</li><li>
</li><li>Course competency</li><li>
</li><li>Performance reviews</li><li>
</li><li>Review sign off</li><li>
</li><li>Review settings - reviews</li><li>
</li><li>Skill competency</li><li>
</li><li>Review template</li><li>
</li><li>Goals</li><li>
</li><li>Review goals</li><li>
</li><li>Review competencies</li><li>
</li><li>Measurements</li><li>
</li><li>Review settings - review templates</li><li>
</li><li>Goal template</li><li>
</li><li>Review template performance journals</li><li>
</li><li>Goal settings - goal templates</li><li>
</li><li>Goal settings - goals</li><li>
</li><li>Goal group templates</li><li>
</li><li>Goal template performance journals</li><li>
</li><li>Goal activities</li><li>
</li><li>Goal notes</li><li>
</li><li>Goal related journal entries</li><li>
</li><li>Project experience competency</li><li>
</li><li>Course type - skills</li><li>
</li><li>Review goal comments</li><li>
</li><li>Goal template measurements</li><li>
</li><li>Review overall comments</li><li>
</li><li>Performance review related journal entries</li><li>
</li><li>Review topic comments</li><li>
</li><li>Skill-mapping - skills</li><li>
</li><li>Goal measurements</li><li>
</li><li>Discussion template measurements</li><li>
</li><li>Discussion measurements</li></ul> | Human Resources|
|Jobs and positions|<ul><li>Compensation job type</li><li>
</li><li>Compensation job function</li><li>
</li><li>Job family</li><li>
</li><li>Job tasks</li><li>
</li><li>Jobs</li><li>
</li><li>Job detail</li><li>
</li><li>Job compensation</li><li>
</li><li>Job - areas of responsibility</li><li>
</li><li>Job - certificates</li><li>
</li><li>Job - education</li><li>
</li><li>Job - tests</li><li>
</li><li>Job - screening</li><li>
</li><li>Job - skills</li><li>
</li><li>Job - work tasks</li><li>
</li><li>Job - ADA requirements</li><li>
</li><li>Job templates</li><li>
</li><li>Job template - skills</li><li>
</li><li>Job template - work tasks</li><li>
</li><li>Job template - ADA requirements</li><li>
</li><li>Job template - areas of responsibility</li><li>
</li><li>Job template - certificates</li><li>
</li><li>Job template - education</li><li>
</li><li>Job template - screening</li><li>
</li><li>Job template test</li><li>
</li><li>Position hierarchy types</li><li>
</li><li>Position type</li><li>
</li><li>Positions V2</li><li>
</li><li>Position hierarchies</li><li>
</li><li>Position default dimensions</li><li>
</li><li>Labor unions</li><li>
</li><li>Labor union agreement</li><li>
</li><li>Position union agreement</li><li>
</li><li>Budget cost elements</li><li>
</li><li>Forecast position budget purpose account details</li></ul>| |
|Leave and absence (Multiple leave types per plan - Off)|<ul><li>Leave and absence parameters</li><li>
</li><li>Leave and absence type</li><li>
</li><li>Leave and absence type reason code</li><li>
</li><li>Leave and absence plan</li><li>
</li><li>Leave and absence enrollment</li><li>
</li><li>Leave time off request</li><li>
</li><li>Leave of absence request</li><li>
</li><li>Leave and absence bank transaction</li></ul>| Human Resources|
|Leave and absence (Multiple leave types per plan - On)|<ul><li>Leave and absence parameters</li><li>
</li><li>Leave and absence type</li><li>
</li><li>Leave and absence type reason code</li><li>
</li><li>Leave and absence suspension relationship</li><li>
</li><li>Leave and absence plan V2</li><li>
</li><li>Leave and absence plan tier V2</li><li>
</li><li>Leave and absence enrollment V2</li><li>
</li><li>Leave time off request V2</li><li>
</li><li>Leave of absence request</li><li>
</li><li>Leave and absence bank transaction V2</li><li>
</li><li>Leave and absence accrual suspension</li></ul>|Human Resources|
|Legacy benefits|<ul><li>Benefit eligibility</li><li>
</li><li>Benefit eligibility benefits</li><li>
</li><li>Benefit eligibility status</li><li>
</li><li>Benefit eligibility workers</li><li>
</li><li>Benefit expiration group</li><li>
</li><li>Benefit expiration result</li><li>
</li><li>Benefit expiration status</li><li>
</li><li>ACA coverage group assignment</li><li>
</li><li>Affordable Care Act 1094-C submission</li><li>
</li><li>Affordable Care Act 1094-C submission ale group member</li><li>
</li><li>Affordable Care Act 1094-C submission month detail</li><li>
</li><li>Affordable Care coverage groups</li><li>
</li><li>Affordable Care coverage group version</li></ul>| |

|Payroll|<ul><li>Benefit accrual plan</li><li>
</li><li>Earning code group</li><li>
</li><li>Payroll tax group</li><li>
</li><li>Benefit accounting rule</li><li>
</li><li>Benefit calculation rate header</li><li>
</li><li>Benefit external reporting</li><li>
</li><li>Benefit plan default dimension</li><li>
</li><li>Pay cycle</li><li>
</li><li>Pay period</li><li>
</li><li>Pay statement header</li><li>
</li><li>Disposable income definition</li><li>
</li><li>Employer tax region</li><li>
</li><li>Form W2 Box reporting adjustment</li><li>
</li><li>Payroll parameter</li><li>
</li><li>Tax region</li><li>
</li><li>Worker tax region</li><li>
</li><li>Worker resident tax region</li><li>
</li><li>Worker position default tax region</li><li>
</li><li>Payroll premium earning policy rule type</li><li>
</li><li>Retirement Benefit Plan Detail US</li><li>
</li><li>Work cycle</li><li>
</li><li>Contribution and deduction limit of enrolled benefits</li><li>
</li><li>State holiday</li><li>
</li><li>Earning code</li><li>
</li><li>Benefit accrual rate</li><li>
</li><li>Benefit calculation rate detail</li><li>
</li><li>Payroll benefit detail</li><li>
</li><li>Benefit Tax Rule US</li><li>
</li><li>Worker arrears</li><li>
</li><li>Deduction arrears recovery</li><li>
</li><li>Disposable income definition - Benefit</li><li>
</li><li>Payment benefit accrual balance</li><li>
</li><li>Pay statement benefit lines</li><li>
</li><li>Payroll tax accounting rule</li><li>
</li><li>Payroll tax code default dimension</li><li>
</li><li>Payroll tax code details</li><li>
</li><li>Payroll tax external reporting</li><li>
</li><li>Payroll tax group code</li><li>
</li><li>Worker tax code V2</li><li>
</li><li>Tax code parameter value</li><li>
</li><li>Work period</li><li>
</li><li>Earning code detail</li><li>
</li><li>Benefit accrual earning code</li><li>
</li><li>Benefit earning basis</li><li>
</li><li>Disposable income definition - Earning</li><li>
</li><li>Earning code default dimension</li><li>
</li><li>Earning code group earning code</li><li>
</li><li>Earning external reporting</li><li>
</li><li>Premium code</li><li>
</li><li>Payroll details for positions</li><li>
</li><li>Earning code related to worker and position for V2 Entity</li><li>
</li><li>Premium code active interval</li><li>
</li><li>Accrual basis earnings</li><li>
</li><li>Earning code accounting rule</li></ul>| Payroll|

|Task management|<ul><li>Business calendar</li><li>
</li><li>Business calendar days</li><li>
</li><li>Group assignment</li><li>
</li><li>Group assignment member</li><li>
</li><li>Business process library task</li><li>
</li><li>Business process library task group</li><li>
</li><li>Business process library task grouping</li><li>
</li><li>Business process template</li><li>
</li><li>Business process</li><li>
</li><li>Business process template task</li><li>
</li><li>Business process task</li><li>
</li><li>Business process task assignment</li><li>
</li><li>Onboarding worker checklist header</li></ul>|Payroll|


  
|010 – System setup|<ul><li>Address and contact information purpose</li><li>
</li><li>Address books</li><li>
</li><li>Address format</li><li>
</li><li>Address parameters</li><li>
</li><li>Currencies</li><li>
</li><li>Global address book parameters</li><li>
</li><li>Name affixes</li><li>
</li><li>Name sequences</li><li>
</li><li>Organization hierarchy type</li><li>
</li><li>Relationship types</li><li>
</li><li>User groups</li><li>
</li><li>Organization hierarchy purposes</li><li>
</li><li>Exchange rates</li><li>
</li><li>Address format lines</li><li>
</li><li>Country/regions</li><li>
</li><li>System parameters</li><li>
</li><li>Units</li><li>
</li><li>States</li><li>
</li><li>Counties</li><li>
</li><li>Cities</li><li>
</li><li>Unit conversions</li><li>
</li><li>Unit translations</li><li>
</li><li>Districts V2</li><li>
</li><li>Postal codes V3</li><li>
</li><li>Legal entities</li><li>
</li><li>Operating unit</li><li>
</li><li>Team types</li><li>
</li><li>Global address book V2</li><li>
</li><li>Organization hierarchy V2 - published and draft</li><li>
</li><li>User information</li><li>
</li><li>User to person relationship</li><li>
</li><li>Teams V2</li><li>
</li><li>Security user role association</li><li>
</li><li>Party relationships</li><li>
</li><li>Party contacts</li><li>
</li><li>Party postal address V2</li><li>
</li><li>Organization name</li><li>
</li><li>Party location and role relationships</li><li>
</li><li>Party location private roles</li><li>
</li><li>Contact information and role relationships</li><li>
</li><li>User defined link base URI</li><li>
</li><li>User defined links</li></ul>|Global address book|

|System and shared|<ul><li>Address and contact information purpose</li><li>
</li><li>Address books</li><li>
</li><li>Address format</li><li>
</li><li>Address parameters</li><li>
</li><li>Chart of accounts</li><li>
</li><li>Currencies</li><li>
</li><li>Expression</li><li>
</li><li>Financial dimensions</li><li>
</li><li>Fiscal calendar</li><li>
</li><li>Global address book parameters</li><li>
</li><li>Main account categories</li><li>
</li><li>Name affixes</li><li>
</li><li>Name sequences</li><li>
</li><li>Organization hierarchy type</li><li>
</li><li>Relationship types</li><li>
</li><li>System email template</li><li>
</li><li>User groups</li><li>
</li><li>System email template message</li><li>
</li><li>Main account</li><li>
</li><li>Organization hierarchy purposes</li><li>
</li><li>Workflow parallel branch</li><li>
</li><li>Workflow version</li><li>
</li><li>Exchange rates</li><li>
</li><li>Fiscal calendar period</li><li>
</li><li>Financial dimension translations</li><li>
</li><li>Financial dimension format</li><li>
</li><li>Dimension attribute activation</li><li>
</li><li>Address format lines</li><li>
</li><li>Advanced rule structures active group</li><li>
</li><li>Financial dimension sets</li><li>
</li><li>Consolidation groups and accounts</li><li>
</li><li>Country/regions</li><li>
</li><li>Financial dimension value translations</li><li>
</li><li>Financial dimension values</li><li>
</li><li>Workflow version notes</li><li>
</li><li>Workflow subworkflow</li><li>
</li><li>Workflow system parameters</li><li>
</li><li>Workflow element</li><li>
</li><li>System parameters</li><li>
</li><li>States</li><li>
</li><li>Workflow element action</li><li>
</li><li>Workflow element link</li><li>
</li><li>Workflow element notification</li><li>
</li><li>Workflow step</li><li>
</li><li>Workflow element outcome message</li><li>
</li><li>Units</li><li>
</li><li>Workflow version notification</li><li>
</li><li>Number sequence code</li><li>
</li><li>Account structures active group</li><li>
</li><li>Counties</li><li>
</li><li>Cities</li><li>
</li><li>Number sequence group</li><li>
</li><li>Number sequence references</li><li>
</li><li>Workflow version notification message</li><li>
</li><li>Workflow escalation path</li><li>
</li><li>Workflow line item</li><li>
</li><li>Workflow step message</li><li>
</li><li>Workflow element notification message</li><li>
</li><li>Unit conversions</li><li>
</li><li>Unit translations</li><li>
</li><li>Districts V2</li><li>
</li><li>Postal codes V3</li><li>
</li><li>Workflow work item queue</li><li>
</li><li>Workflow work item queue assignee</li><li>
</li><li>Legal entities</li><li>
</li><li>Workflow work item queue assignment</li><li>
</li><li>Workflow work item queue assignment rule</li><li>
</li><li>Operating unit</li><li>
</li><li>Workflow work item queue group</li><li>
</li><li>Workflow work item queue relation table</li><li>
</li><li>Team types</li><li>
</li><li>Global address book V2</li><li>
</li><li>Organization hierarchy V2 - published and draft</li><li>
</li><li>User information</li><li>
</li><li>User to person relationship</li><li>
</li><li>Teams V2</li><li>
</li><li>Security user role association</li><li>
</li><li>Party relationships</li><li>
</li><li>Party contacts</li><li>
</li><li>Party postal address V2</li></ul>| Global address book, Workflow and System administration|


|Benefits management|<ul><li>
Employment category</li><li>
</li><li>Employment type</li><li>
</li><li>Benefits bundle</li><li>
</li><li>Benefits deduction</li><li>
</li><li>Benefits personal contacts eligibility option</li><li>
</li><li>Benefits period</li><li>
</li><li>Benefits rounding rule</li><li>
</li><li>Benefits tier code</li><li>
</li><li>Benefits plan type</li><li>
</li><li>Benefits life event type</li><li>
</li><li>Benefits life event option</li><li>
</li><li>Benefits coverage option</li><li>
</li><li>Benefits plan type coverage option</li><li>
</li><li>Benefits coverage option personal contacts eligibility option</li><li>
</li><li>Benefits waiting day</li><li>
</li><li>Benefits waiting period</li><li>
</li><li>Benefits pay frequency</li><li>
</li><li>Benefits parameters V2</li><li>
</li><li>Benefits eligibility rule</li><li>
</li><li>Benefits credit</li><li>
</li><li>Benefits credit period</li><li>
</li><li>Benefits rate</li><li>
</li><li>Benefits rate tiers</li><li>
</li><li>Benefits rate double tiers</li><li>
</li><li>Benefits program</li><li>
</li><li>Benefits program eligibility rule</li><li>
</li><li>Benefits eligibility rule additional criteria</li><li>
</li><li>Benefits plan</li><li>
</li><li>Benefits plan coverage option</li><li>
</li><li>Benefits plan eligibility rule</li><li>
</li><li>Benefits plan period</li><li>
</li><li>Benefits eligibility rule override</li><li>
</li><li>Benefits credit plan period</li></ul>| Human Resources|







