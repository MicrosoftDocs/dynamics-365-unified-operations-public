---
# required metadata

title: Configure integration with dataverse tables
description: This article describes the integration between Dynamics 365 Human Resources and Dataverse.
author: anschmidt  
ms.date: 12/06/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-12-07
ms.dyn365.ops.version: Human Resources

---

# Configure integration with Dataverse Tables


To integrate Microsoft Dynamics 365 Human Resources with dataverse, you can use the [Data Integrator](/powerapps/administrator/data-integrator). The Human Resources to Dataverse template enables data flow for jobs, positions workers and others. The template allows data to flow from Human Resources into Dataverse and vice versa, creating a write in both systems.


## System requirements for Human Resources

The integration solution requires the following versions of Human Resources and Finance: 

- Dynamics 365 Finance version 7.2 and later
- Dynamics CRM environment with a Database created and Dynamics 365 apps allowed

## Template and tasks

To access the Human Resources to Finance template.

1. Open [Power Apps Admin Center](https://admin.powerapps.com/). 

2. Under your environment, Select **Dynamics 365 Apps**, and then select **App source** on the top banner. Search for "Dual-write Human Resources" or use this direct 
link: https://appsource.microsoft.com/en-US/product/dynamics-365/mscrm.hcm_dualwrite to install.

3. After installing, go to Dynamics 365 Finance.
4. Open the **Data Management** workspace. 
5. Click on **Dual Write**. 

6. Follow the process for linking your environment for at least one company in your organization. 

7. When finished setting up a link to your Dataverse environment, click **Apply Solution**. This will apply the solution and install the mappings into the integrator 
app.

## Template mappings

In the following template mapping tables, the name of the task contains the entities used in each application. Finance is found on the left and Dataverse on the right.

### Bank account disbursements (Dual-write) to Bank Account Disbursement
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ACCOUNTIDENTIFICATIONID        | cdm_bankaccountid.cdm_accountidentification        |
| AMOUNT                         | cdm_amount                                         |
| PRIORITY                       | cdm_disbursementpriority                           |
| PERSONNELNUMBER                | cdm_bankaccountid.cdm_workerid.cdm_workernumber    |
| REMAINDER                      | cdm_isremainder                                    |



### Benefit calculation rate detail (Dual-write) to Benefit Calculation Rate Detail
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CONTRIBUTIONMETHOD             | cdm_contributionmethod                             |
| EFFECTIVE                      | cdm_effective                                      |
| EMPLOYERCONTRIBUTION           | cdm_employercontribution                           |
| EXPIRATION                     | cdm_expiration                                     |
| WORKERDEDUCTION                | cdm_workerdeduction                                |
| NAME                           | cdm_calculationrateid.cdm_name                     |



### Benefit calculation rate header to Benefit Calculation Rate
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| NAME                           | cdm_name                                           |
| TIERTYPE                       | cdm_tiertype                                       |



### Benefit option to Benefit Option
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ALLOWBENEFICIARYDESIGNATIONS   | cdm_allowbeneficiarydesignations                   |
| ALLOWDEPENDENTCOVERAGE         | cdm_allowdependentcoverage                         |
| BENEFITOPTIONID                | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| ISWAIVE                        | cdm_iswaived                                       |



### Benefit type to Benefit Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| BENEFITTYPEID                  | cdm_name                                           |
| CONCURRENTENROLLMENT           | cdm_concurrentenrollment                           |
| DESCRIPTION                    | cdm_description                                    |
| PAYROLLCATEGORY                | cdm_payrollcategory                                |



### Business calendar to Business Process Calendar
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CALENDARID                     | cdm_name                                           |
| NAME                           | cdm_calendarname                                   |
| STARTDATE                      | cdm_startdate                                      |
| ENDDATE                        | cdm_enddate                                        |
| ISOPENMONDAY                   | cdm_ismondayopen                                   |
| ISOPENTUESDAY                  | cdm_istuesdayopen                                  |
| ISOPENWEDNESDAY                | cdm_iswednesdayopen                                |
| ISOPENTHURSDAY                 | cdm_isthursdayopen                                 |
| ISOPENFRIDAY                   | cdm_isfridayopen                                   |
| ISOPENSATURDAY                 | cdm_issaturdayopen                                 |
| ISOPENSUNDAY                   | cdm_issundayopen                                   |



### Business process to Business Process Header
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PROCESSID                      | cdm_processid                                      |
| PROCESSTYPE                    | cdm_processtype                                    |
| GENERICSUBTYPE                 | cdm_genericsubtype                                 |
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| STATUS                         | cdm_status                                         |
| TARGETDATE                     | cdm_targetdate                                     |
| STARTDATETIME                  | cdm_startdatetime                                  |
| ENDDATETIME                    | cdm_enddatetime                                    |
| RESOLVEDBYPERSONNELNUMBER      | cdm_resolvedbyid.cdm_workernumber                  |
| PROCESSOWNERPERSONNELNUMBER    | cdm_processownerid.cdm_workernumber                |
| SOURCETEMPLATENAME             | cdm_sourcetemplateid.cdm_name                      |
| SOURCETEMPLATEPROCESSTYPE      | cdm_sourcetemplateid.cdm_businessprocesstype       |
| SOURCETEMPLATEGENERICSUBTYPE   | cdm_sourcetemplateid.cdm_genericsubtype            |



### Business process library task group to Business Process Library Task Group
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PROCESSTYPE                    | cdm_processtype                                    |
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Business process stage to Business Process Stage
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PROCESSTYPE                    | cdm_businessprocesstype                            |
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| SEQUENCENUMBER                 | cdm_sequencenumber                                 |



### Business process task to Business Process Task
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| DUEDATE                        | cdm_duedate                                        |
| TASKID                         | cdm_taskid                                         |
| INSTRUCTIONS                   | cdm_instructions                                   |
| COMPLETIONDATETIME             | cdm_completiondatetime                             |
| ASSIGNMENTTYPE                 | cdm_assignmenttype                                 |
| ISOPTIONAL                     | cdm_isoptional                                     |
| NAME                           | cdm_name                                           |
| STATUS                         | cdm_status                                         |
| RESOLVEDBY_PERSONNELNUMBER     | cdm_resolvedbyid.cdm_workernumber                  |
| TEMPLATETASKID                 | cdm_templatetaskid.cdm_taskid                      |
| ASSIGNEDWORKER_PERSONNELNUMBER | cdm_assignedworkerid.cdm_workernumber              |
| PROCESSID                      | cdm_processheaderid.cdm_processid                  |
| ASSIGNEDGROUP_NAME             | cdm_assignedgroupid.cdm_name                       |
| ASSIGNEDPOSITION_POSITIONID    | cdm_assignedposition.cdm_jobpositionnumber         |



### Business process template to Checklist Template Header
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PROCESSTYPE                    | cdm_businessprocesstype                            |
| GENERICSUBTYPE                 | cdm_genericsubtype                                 |
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| CALENDARID                     | cdm_businessprocesscalendarid.cdm_name             |
| PERSONNELNUMBER                | cdm_processownerid.cdm_workernumber                |
| ISACTIVE                       | cdm_isactive                                       |



### Business process template task to Checklist Template Task
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| TASKID                         | cdm_taskid                                         |
| NAME                           | cdm_name                                           |
| TEMPLATEHEADER_PROCESSTYPE     | cdm_businessprocesstemplateheaderid.cdm_businessprocesstype |
| TEMPLATEHEADER_GENERICSUBTYPE  | cdm_businessprocesstemplateheaderid.cdm_genericsubtype |
| TEMPLATEHEADER_NAME            | cdm_businessprocesstemplateheaderid.cdm_name       |
| DESCRIPTION                    | cdm_description                                    |
| DUEDATEOFFSETDAYS              | cdm_duedateoffsetdays                              |
| MENUITEMTYPE                   | cdm_tasklinktype                                   |
| MENUITEM                       | cdm_tasklink                                       |
| CONTACTPERSON_PERSONNELNUMBER  | cdm_contactpersonid.cdm_workernumber               |
| ASSIGNMENTTYPE                 | cdm_assignmenttype                                 |
| ASSIGNEDWORKER_PERSONNELNUMBER | cdm_assignedworkerid.cdm_workernumber              |
| ASSIGNEDPOSITION_POSITIONID    | cdm_assignedpositionid.cdm_jobpositionnumber       |
| ASSIGNEDGROUP_NAME             | cdm_assignedgroupid.cdm_name                       |
| ISOPTIONAL                     | cdm_isoptional                                     |
| INSTRUCTIONS                   | cdm_instructions                                   |



### Calculation frequency to Benefit Calculation Frequency
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| FREQUENCY                      | cdm_name                                           |
| FREQUENCYCONTROL               | cdm_frequencycontrol                               |
| ISIMMUTABLE                    | cdm_isimmutable                                    |



### Calculation frequency pay period to Benefit Calculation Frequency Pay Period
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CALCULATIONFREQUENCYID         | cdm_benefitcalculationfrequencyid.cdm_name         |
| PERIODSTARTDATE                | cdm_payperiodid.cdm_periodstartdate                |
| PAYCYCLEID                     | cdm_payperiodid.cdm_paycycleid.cdm_name            |



### Calendar to Work Calendar
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CALENDARID                     | cdm_name                                           |
| CALENDARNAME                   | cdm_description                                    |
| WORKCALENDARHOLIDAYID          | cdm_workcalendarholidayid.cdm_name                 |



### Compensation fixed action table to Fixed Compensation Event
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ACTION                         | cdm_name                                           |
| ACTIVE                         | cdm_isactive                                       |
| DESCRIPTION                    | cdm_description                                    |
| TYPE                           | cdm_eventtype                                      |



### Compensation fixed plan to Compensation Fixed Plan
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PLAN                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| TYPE                           | cdm_type                                           |
| EFFECTIVEDATE                  | cdm_effectivedate                                  |
| EXPIRATIONDATE                 | cdm_expirationdate                                 |
| CURRENCY                       | cdm_transactioncurrencyid.isocurrencycode          |
| PAYFREQUENCY                   | cdm_payfrequency.cdm_name                          |
| HIRERULE                       | cdm_hirerule                                       |
| OUTOFRANGETOLERANCE            | cdm_outofrangetolerance                            |
| RECOMMENDATIONALLOWED          | cdm_recommendationallowed                          |
| COMPENSATIONSTRUCTURE          | cdm_compensationgrid.cdm_name                      |
| REFPOINTSETUPID                | cdm_referencepointsetupline.cdm_referencepointsetupid.cdm_name |
| CONTROLPOINT                   | cdm_referencepointsetupline.cdm_name               |



### Compensation grids to Compensation Grid
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| GRIDID                         | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| EFFECTIVEDATE                  | cdm_effectivedate                                  |
| EXPIRATIONDATE                 | cdm_expirationdate                                 |
| REFERENCESETUP                 | cdm_referencepointsetupid.cdm_name                 |
| TYPE                           | cdm_type                                           |
| CURRENCY                       | cdm_transactioncurrencyid.isocurrencycode          |



### Compensation job function to Job Function
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| JOBFUNCTIONID                  | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Compensation job type to Job Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| JOBTYPEID                      | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| EXEMPTSTATUS                   | cdm_exemptstatus                                   |



### Compensation pay frequency to Compensation Pay Frequency
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PAYRATECONVERSION              | cdm_name                                           |
| PERIOD                         | cdm_period                                         |
| DESCRIPTION                    | cdm_description                                    |
| ANNUALCONVERSIONFACTOR         | cdm_annualconversionfactor                         |
| HOURLYCONVERSIONFACTOR         | cdm_hourlyconversionfactor                         |
| MONTHLYCONVERSIONFACTOR        | cdm_monthlyconversionfactor                        |
| WEEKLYCONVERSIONFACTOR         | cdm_weeklyconversionfactor                         |



### Compensation regions to Compensation Region
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| LOCATION                       | cdm_name                                           |



### Compensation variable plan V2 to Compensation Variable Plan
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| VARIABLEAWARDBASIS             | cdm_awardbasis                                     |
| AWARDBASISCALCULATION          | cdm_awardbasiscalculation                          |
| CALCULATIONTYPE                | cdm_calculationtype                                |
| DESCRIPTION                    | cdm_description                                    |
| ENABLEENROLLMENT               | cdm_enableenrollment                               |
| ENABLELEVELS                   | cdm_enablelevels                                   |
| ENABLERECOMMENDATION           | cdm_enablerecommendation                           |
| HIRERULE                       | cdm_hirerule                                       |
| LEVERAGE100PERCENT             | cdm_leverage100percent                             |
| LEVERAGEMAXIMUM                | cdm_leveragemaximum                                |
| LEVERAGEMINIMUM                | cdm_leverageminimum                                |
| LEVERAGEOVEROBJECTIVE          | cdm_leverageoverobjective                          |
| LEVERAGEUNDEROBJECTIVE         | cdm_leverageunderobjective                         |
| PERCENTOFBASIS                 | cdm_percentofbasis                                 |
| PLANID                         | cdm_name                                           |
| VARIABLECOMPENSATIONTYPE       | cdm_variablecompensationtypeid.cdm_name            |
| UNITCURRENCYCODE               | transactioncurrencyid.isocurrencycode              |
| UNITRELATIONSHIP               | cdm_unitrelationship                               |
| UNITVALUE                      | cdm_unitvalue                                      |
| NUMBEROFUNITSREAL              | cdm_numberofunits                                  |
| EFFECTIVEDATE                  | cdm_effectivedate                                  |
| EXPIRATIONDATE                 | cdm_expirationdate                                 |
| VESTINGRULE                    | cdm_vestingruleid.cdm_name                         |
| LEVERAGETOLERANCEMAX           | cdm_leveragetolerancemax                           |
| LEVERAGETOLERANCEMIN           | cdm_leveragetolerancemin                           |



### Compensation variable type to Compensation Variable Plan Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| TYPE                           | cdm_awardtype                                      |
| VARIABLECOMPENSATIONTYPE       | cdm_name                                           |



### Compensation vesting rules to Vesting Rule
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| NOTE                           | cdm_notes                                          |
| VESTINGRULE                    | cdm_name                                           |



### Department V2 to Department
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| OPERATINGUNITNUMBER            | cdm_departmentnumber                               |
| NAME                           | cdm_name                                           |
| SEARCHNAME                     | cdm_description                                    |
| PARTYTYPE                      | cdm_partytype                                      |



### Dual Write Tax Region to Tax Region
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CITY                           | cdm_city                                           |
| COUNTRYORREGION                | cdm_countryorregion                                |
| COUNTY                         | cdm_county                                         |
| STATE                          | cdm_stateorprovince                                |
| TAXREGIONNAME                  | cdm_name                                           |



### Dual Write Worker Identification to Worker Person Identification Number
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| ENTRYTYPE                      | cdm_entrytype                                      |
| EXPIRATIONDATE                 | cdm_expirationdate                                 |
| IDENTIFICATIONNUMBER           | cdm_identificationnumber                           |
| IDENTIFICATIONTYPEID           | cdm_identificationtypeid.cdm_name                  |
| ISPRIMARY                      | cdm_isprimary                                      |
| ISSUEDATE                      | cdm_issuedate                                      |
| ISSUINGAGENCYID                | cdm_issuingagencyid.cdm_name                       |
| WORKERNUMBER                   | cdm_workerid.cdm_workernumber                      |



### Compensation structure to Compensation Structure
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| AMOUNT                         | cdm_amount                                         |
| GRID                           | cdm_compensationgridid.cdm_name                    |
| LEVELID                        | cdm_compensationlevelid.cdm_name                   |
| REFERENCEPOINTLINENUMBER       | cdm_referencepointid.cdm_linenumber                |
| REFERENCESETUP                 | cdm_referencepointid.cdm_referencepointsetupid.cdm_name |
| REFERENCEPOINT                 | cdm_referencepointid.cdm_name                      |



### Earning code to Payroll Earning Code
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| EARNINGCODE                    | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| INCLUDEINPAYMENTTYPE           | cdm_includeinpaymenttype                           |
| QUANTITYUNIT                   | cdm_quantityunit                                   |
| TRACKFMLAHOURS                 | cdm_trackfmlahours                                 |
| ISPRODUCTIVE                   | cdm_isproductive                                   |



### Employee fixed compensation to Worker Fixed Compensation
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| COMPENSATIONLEVELID            | cdm_compensationlevelid.cdm_name                   |
| TYPE                           | cdm_compensationtype                               |
| EFFECTIVEDATE                  | cdm_effectivedate                                  |
| EXPIRATIONDATE                 | cdm_expirationdate                                 |
| LINENUMBER                     | cdm_linenumber                                     |
| PAYFREQUENCY                   | cdm_payfrequencyid.cdm_name                        |
| PAYRATE                        | cdm_payrate                                        |
| PLAN                           | cdm_planid.cdm_name                                |
| POSITIONID                     | cdm_positionid.cdm_jobpositionnumber               |
| PROCESSTYPE                    | cdm_processtype                                    |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| ACTION                         | cdm_eventid.cdm_name                               |
| STEP                           | cdm_referencepointsetuplineid.cdm_name             |
| REFPOINTSETUPID                | cdm_referencepointsetuplineid.cdm_referencepointsetupid.cdm_name |



### Employment per company to Employment
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| EMPLOYMENTENDDATE              | cdm_employmentenddate                              |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| EMPLOYMENTSTARTDATE            | cdm_employmentstartdate                            |
| WORKERTYPE                     | cdm_workertype                                     |
| DIMENSIONDISPLAYVALUE          | cdm_dimensiondisplayvalue                          |
| ADJUSTEDWORKERSTARTDATE        | cdm_adjustedworkerstartdate                        |
| EMPLOYERNOTICEAMOUNT           | cdm_employernoticeamount                           |
| EMPLOYERUNITOFNOTICE           | cdm_employerunitofnotice                           |
| WORKERUNITOFNOTICE             | cdm_workerunitofnotice                             |
| WORKERNOTICEAMOUNT             | cdm_workernoticeamount                             |
| LASTDATEWORKED                 | cdm_lastdateworked                                 |
| PROBATIONENDDATE               | cdm_probationenddate                               |
| TRANSITIONDATE                 | cdm_transitiondate                                 |
| TRANSITIONREASONCODENAME       | cdm_transitionreasoncode.cdm_name                  |
| WORKERSTARTDATE                | cdm_workerstartdate                                |
| VALIDTO                        | cdm_validto                                        |
| VALIDFROM                      | cdm_validfrom                                      |



### Ethnic origins to Ethnic Origin
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ETHNICORIGINID                 | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Group assignment to Business Process Group Assignment
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| ISACTIVE                       | cdm_isactive                                       |



### Identification type to Worker Person Identification Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| IDENTIFICATIONTYPEID           | cdm_name                                           |
| ALLOWEDVALUES                  | cdm_allowedvalues                                  |
| FIXEDLENGTH                    | cdm_fixedlength                                    |
| IDENTIFICATIONNUMBERFORMAT     | cdm_identificationnumberformat                     |



### Issuing agency to Person Identification Issuing Agency
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| EMAIL                          | cdm_email                                          |
| EXTENSION                      | cdm_extension                                      |
| FAX                            | cdm_fax                                            |
| ISSUINGAGENCY                  | cdm_name                                           |
| MOBILEPHONE                    | cdm_mobilephone                                    |
| INTERNETADDRESS                | cdm_websiteurl                                     |
| NAME                           | cdm_description                                    |
| PAGER                          | cdm_pager                                          |
| SMS                            | cdm_sms                                            |
| TELEPHONE                      | cdm_telephone                                      |
| TELEXNUMBER                    | cdm_telex                                          |
| ADDRESSCITY                    | cdm_city                                           |
| ADDRESSCOUNTY                  | cdm_county                                         |
| ADDRESSDESCRIPTION             | cdm_addressdescription                             |
| ADDRESSSTATE                   | cdm_stateorprovince                                |
| ADDRESSSTREET                  | cdm_street                                         |
| ADDRESSZIPCODE                 | cdm_postalcode                                     |
| ADDRESSCOUNTRYREGIONISOCODE    | cdm_countryregion                                  |



### Job Positions Dual Write to Job Position
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| POSITIONID                     | cdm_jobpositionnumber                              |
| ACTIVATION                     | cdm_activation                                     |
| AVAILABLEFORASSIGNMENT         | cdm_availableforassignment                         |
| COMPENSATIONREGIONID           | cdm_compensationregionid.cdm_name                  |
| DEPARTMENTID                   | cdm_departmentid.cdm_departmentnumber              |
| DESCRIPTION                    | cdm_description                                    |
| FULLTIMEEQUIVALENT             | cdm_fulltimeequivalent                             |
| JOBID                          | cdm_jobid.cdm_name                                 |
| PARENTPOSITIONID               | cdm_parentjobpositionid.cdm_jobpositionnumber      |
| POSITIONTYPEID                 | cdm_positiontypeid.cdm_name                        |
| RETIREMENT                     | cdm_retirement                                     |
| TITLEID                        | cdm_titleid.cdm_name                               |
| VALIDFROM                      | cdm_validfrom                                      |
| VALIDTO                        | cdm_validto                                        |



### Jobs Dual-write to Job
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| JOBID                          | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| JOBDESCRIPTION                 | cdm_jobdescription                                 |
| ALLOWUNLIMITEDPOSITIONS        | cdm_allowunlimitedpositions                        |
| MAXIMUMNUMBEROFPOSITIONS       | cdm_maximumnumberofpositions                       |
| JOBFUNCTIONID                  | cdm_jobfunctionid.cdm_name                         |
| JOBTYPEID                      | cdm_jobtypeid.cdm_name                             |
| TITLEID                        | cdm_titleid.cdm_name                               |
| VALIDFROM                      | cdm_validfrom                                      |
| VALIDTO                        | cdm_validto                                        |
| DEFAULTFULLTIMEEQUIVALENCY     | cdm_defaultfulltimeequivalent                      |



### Language codes to Language
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| LANGUAGECODEID                 | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Leave and absence bank transaction V2 to Leave Bank Transaction
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| AMOUNT                         | cdm_amount                                         |
| LEAVETYPEID                    | cdm_leavetypeid.cdm_type                           |
| LEAVEPLANID                    | cdm_leaveplanid.cdm_name                           |
| TRANSACTIONDATE                | cdm_transactiondate                                |
| TRANSACTIONNUMBER              | cdm_transactionnumber                              |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| TRANSACTIONTYPE                | cdm_transactiontype                                |



### Leave and absence enrollment V2 to Leave Enrollment
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| STARTDATE                      | cdm_startdate                                      |
| ENDDATE                        | cdm_enddate                                        |
| CUSTOMDATE                     | cdm_customdate                                     |
| ACCRUALSTARTDATE               | cdm_accrualstartdate                               |
| ACCRUALDATEBASIS               | cdm_accrualdatebasis                               |
| ISACCRUALSUSPENDED             | cdm_isaccrualsuspended                             |
| LEAVEPLANID                    | cdm_leaveplanid.cdm_name                           |
| TIERBASIS                      | cdm_tierbasis                                      |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |



### Leave and absence plan V2 to Leave Plan
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ACCRUALFREQUENCY               | cdm_accrualfrequency                               |
| NAME                           | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| STARTDATE                      | cdm_startdate                                      |
| LEAVETYPEID                    | cdm_leavetypeid.cdm_type                           |



### Leave and absence type to Leave Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| TYPE                           | cdm_type                                           |
| EARNINGCODEID                  | cdm_earningcodeid.cdm_name                         |



### Leave and absence type reason code to Leave Type Reason Code
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| LEAVETYPE                      | cdm_typeid.cdm_type                                |
| REASONCODEID                   | cdm_reasoncodeid.cdm_name                          |



### Leave time-off request detail to Leave Request Detail
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| AMOUNT                         | cdm_amount                                         |
| LEAVEDATE                      | cdm_leavedate                                      |
| REQUESTID                      | cdm_leaverequestid.cdm_leaverequestnumber          |
| TYPE                           | cdm_leavetypeid.cdm_type                           |



### Leave time-off request header to Leave Request
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| REQUESTID                      | cdm_leaverequestnumber                             |
| REQUESTDATE                    | cdm_requestdate                                    |
| STATUS                         | cdm_status                                         |
| COMMENT                        | cdm_comment                                        |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |



### Levels to Compensation Level
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| TYPE                           | cdm_type                                           |
| DESCRIPTION                    | cdm_description                                    |
| LEVEL                          | cdm_name                                           |



### Onboarding process header to Onboard Process Header
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PROCESSID                      | cdm_processheaderid.cdm_processid                  |
| ONBOARDEDEMPLOYEEPERSONNELNUMBER | cdm_onboardedemployeeid.cdm_workernumber           |
| EMPLOYMENTPERSONNELNUMBER      | cdm_employmentid.cdm_workerid.cdm_workernumber     |
| LEGALENTITYID                  | cdm_employmentid.cdm_companyid.cdm_companycode     |
| EMPLOYMENTSTARTDATE            | cdm_employmentid.cdm_employmentstartdate           |



### Pay cycle to Pay Cycle
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PAYCYCLEID                     | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| PAYCYCLEFREQUENCY              | cdm_frequency                                      |



### Pay period to Pay Period
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| COMMENTS                       | cdm_description                                    |
| DEFAULTPAYMENTDATE             | cdm_defaultpaymentdate                             |
| PAYCYCLEID                     | cdm_paycycleid.cdm_name                            |
| PERIODENDDATE                  | cdm_periodenddate                                  |
| PERIODSTARTDATE                | cdm_periodstartdate                                |
| STATUS                         | cdm_status                                         |



### Payroll details for positions to Payroll Position Detail
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PAYCYCLEID                     | cdm_paycycle.cdm_name                              |
| POSITIONID                     | cdm_position.cdm_jobpositionnumber                 |
| VALIDFROM                      | cdm_validfrom                                      |
| VALIDTO                        | cdm_validto                                        |
| ANNUALREGULARHOURS             | cdm_annualregularhours                             |
| PAIDBYLEGALENTITY              | cdm_paidby.cdm_companycode                         |



### Position Default Dimensions Dual Write to Job Position Dimension
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DIMENSIONDISPLAYVALUE          | cdm_dimensiondisplayvalue                          |
| POSITIONID                     | cdm_jobpositionid.cdm_jobpositionnumber            |



### Position type to Position Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| POSITIONTYPEID                 | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| CLASSIFICATION                 | cdm_classification                                 |



### Position worker assignments V2 to Position Worker Assignment
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| POSITIONID                     | cdm_jobpositionid.cdm_jobpositionnumber            |
| VALIDFROM                      | cdm_validfrom                                      |
| VALIDTO                        | cdm_validto                                        |
| IsPrimaryPosition              | cdm_isprimaryposition                              |



### Reason codes to Reason Code
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| REASONCODEID                   | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| ISABSENCEAPPLICABLE            | cdm_isabsenceapplicable                            |
| ISAPPLICATIONAPPLICABLE        | cdm_isapplicationapplicable                        |
| ISCOMPENSATIONAPPLICABLE       | cdm_iscompensationapplicable                       |
| ISCREATENEWPOSITIONAPPLICABLE  | cdm_iscreatenewpositionapplicable                  |
| ISEDITPOSITIONAPPLICABLE       | cdm_iseditpositionapplicable                       |
| ISHIREAPPLICABLE               | cdm_ishireapplicable                               |
| ISSKILLMAPPINGAPPLICABLE       | cdm_isskillmappingapplicable                       |
| ISTERMINATIONAPPLICABLE        | cdm_isterminationapplicable                        |
| ISTRANSFERAPPLICABLE           | cdm_istransferapplicable                           |



### Reference Point Setup Line (Dual-write) to Compensation Reference Point Setup Line
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| DESCRIPTION                    | cdm_description                                    |
| LINENUM                        | cdm_linenumber                                     |
| REFPOINTID                     | cdm_name                                           |
| REFPOINTSETUPID                | cdm_referencepointsetupid.cdm_name                 |



### Reference point setups to Compensation Reference Point Setup
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| REFERENCESETUP                 | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| TYPE                           | cdm_compensationtype                               |



### Skill types to Skill Type
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| SKILLTYPE                      | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Titles to Title
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| TITLEID                        | cdm_name                                           |



### Variable compensation level V2 to Compensation Variable Plan Level
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| AWARDAMOUNT                    | cdm_awardamount                                    |
| AWARDPERCENT                   | cdm_awardpercent                                   |
| AWARDUNITSREAL                 | cdm_awardunits                                     |
| COMPENSATIONLEVELID            | cdm_compensationlevelid.cdm_name                   |
| PLANID                         | cdm_compensationvariableplanid.cdm_name            |



### Veteran status to Veteran Status
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| VETERANSTATUSID                | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |
| ISPROTECTEDVETERAN             | cdm_isprotectedveteran                             |



### Work Calendar Enrollments to Work Calendar Enrollment
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| STARTDATE                      | cdm_employmentid.cdm_employmentstartdate           |
| PERSONNELNUMBER                | cdm_employmentid.cdm_workerid.cdm_workernumber     |
| CALENDARID                     | cdm_workcalendarid.cdm_name                        |
| COMPANYID                      | cdm_employmentid.cdm_companyid.cdm_companycode     |



### Work calendar holiday to Work Calendar Holiday
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ID                             | cdm_name                                           |
| DESCRIPTION                    | cdm_description                                    |



### Work calendar holiday line to Work Calendar Holiday Line
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| HOLIDAYID                      | cdm_workcalendarholidayid.cdm_name                 |
| NAME                           | cdm_name                                           |
| HOLIDAYDATE                    | cdm_holidaydate                                    |



### Worker to Worker
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PERSONNELNUMBER                | cdm_workernumber                                   |
| FIRSTNAME                      | cdm_firstname                                      |
| MIDDLENAME                     | cdm_middlename                                     |
| LASTNAME                       | cdm_lastname                                       |
| WORKERTYPE                     | cdm_type                                           |
| WORKERSTATUS                   | cdm_status                                         |
| PRIMARYCONTACTEMAIL            | cdm_primaryemailaddress                            |
| PRIMARYCONTACTPHONE            | cdm_primarytelephone                               |
| PRIMARYCONTACTFACEBOOK         | cdm_facebookidentity                               |
| PRIMARYCONTACTTWITTER          | cdm_twitteridentity                                |
| PRIMARYCONTACTLINKEDIN         | cdm_linkedinidentity                               |
| PRIMARYCONTACTURL              | cdm_websiteurl                                     |
| GENDER                         | cdm_gender                                         |
| BIRTHDATE                      | cdm_birthdate                                      |
| NAME                           | cdm_fullname                                       |



### Worker bank accounts to Worker Bank Account
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ACCOUNTIDENTIFICATION          | cdm_accountidentification                          |
| ADDRESSCITY                    | cdm_city                                           |
| ADDRESSCOUNTRYREGIONID         | cdm_countryorregion                                |
| ADDRESSCOUNTY                  | cdm_county                                         |
| ADDRESSDESCRIPTION             | cdm_addressdescription                             |
| ADDRESSDISTRICTNAME            | cdm_districtname                                   |
| ADDRESSPOSTBOX                 | cdm_postofficebox                                  |
| ADDRESSSTATE                   | cdm_stateorprovince                                |
| ADDRESSZIPCODE                 | cdm_postalcode                                     |
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| BANKACCOUNTNUMBER              | cdm_bankaccountnumber                              |
| BANKACCOUNTTYPE                | cdm_bankaccounttype                                |
| EMAIL                          | cdm_email                                          |
| EXTENSION                      | cdm_extension                                      |
| FAX                            | cdm_fax                                            |
| INTERNETADDRESS                | cdm_websiteurl                                     |
| MOBILEPHONE                    | cdm_mobilephone                                    |
| ROUTINGNUMBER                  | cdm_routingnumber                                  |
| TELEPHONE                      | cdm_telephone                                      |
| TELEXNUMBER                    | cdm_telexnumber                                    |
| BANKIBAN                       | cdm_iban                                           |
| SWIFTNO                        | cdm_swiftcode                                      |
| BANKLOCATIONCODE               | cdm_banklocationcode                               |
| BRANCHNAME                     | cdm_branchname                                     |
| BRANCHNUMBER                   | cdm_branchnumber                                   |
| ROUTINGNUMBERTYPE              | cdm_routingnumbertype                              |
| ACCOUNTHOLDER                  | cdm_accountholder                                  |
| NAMEOFPERSON                   | cdm_nameofperson                                   |
| NAME                           | cdm_description                                    |
| ADDRESSSTREET                  | cdm_line1                                          |
| ADDRESSSTREETNUMBER            | cdm_line2                                          |



### Worker personal details to Worker Personal Detail
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| BIRTHDATE                      | cdm_birthdate                                      |
| PERSONBIRTHCITY                | cdm_birthcity                                      |
| GENDER                         | cdm_gender                                         |
| EXPATRIATEENDDATE              | cdm_expatriateenddate                              |
| EXPATRIATESTARTDATE            | cdm_expatriatestartdate                            |
| DISABLEDVETERAN                | cdm_isdisabledveteran                              |
| DECEASEDDATE                   | cdm_deceaseddate                                   |
| DISABLEDVERIFICATIONDATE       | cdm_disabledveteranverificationdate                |
| EDUCATION                      | cdm_education                                      |
| ETHNICORIGINID                 | cdm_ethnicoriginid.cdm_name                        |
| ISDISABLED                     | cdm_isdisabled                                     |
| ISFULLTIMESTUDENT              | cdm_isfulltimestudent                              |
| ISEXPATRIATERULINGAPPLICABLE   | cdm_isexpatriaterulingapplicable                   |
| MARITALSTATUS                  | cdm_maritalstatus                                  |
| MILITARYSERVICESTARTDATE       | cdm_militaryservicestartdate                       |
| MILITARYSERVICEENDDATE         | cdm_militaryserviceenddate                         |
| NUMBEROFDEPENDENTS             | cdm_numberofdependents                             |
| NATIVELANGUAGEID               | cdm_nativelanguageidid.cdm_name                    |
| NATIONALITYCOUNTRYREGION       | cdm_nationalitycountryregion                       |
| PERSONBIRTHCOUNTRYREGION       | cdm_birthcountryregion                             |
| FATHERBIRTHCOUNTRYREGION       | cdm_fatherbirthcountryregion                       |
| MOTHERBIRTHCOUNTRYREGION       | cdm_motherbirthcountryregion                       |
| CITIZENSHIPCOUNTRYREGION       | cdm_citizenshipcountryregion                       |
| VETERANSTATUSID                | cdm_veteranstatusid.cdm_name                       |



### Worker postal addresses dual-write to Worker Address
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| PERSONNELNUMBER                | cdm_workerid.cdm_workernumber                      |
| ADDRESSLOCATIONID              | cdm_addressnumber                                  |
| ADDRESSLOCATIONROLES           | cdm_addresstype                                    |
| EFFECTIVE                      | cdm_effectivedate                                  |
| EXPIRATION                     | cdm_expirationdate                                 |
| ADDRESSSTREET                  | cdm_street                                         |
| ADDRESSSTREETNUMBER            | cdm_streetnumber                                   |
| ADDRESSCITY                    | cdm_city                                           |
| ADDRESSCOUNTRYREGIONISOCODE    | cdm_countryregion                                  |
| ADDRESSSTATE                   | cdm_stateorprovince                                |
| ADDRESSCOUNTYID                | cdm_county                                         |
| ADDRESSDESCRIPTION             | cdm_description                                    |
| ADDRESSLATITUDE                | cdm_latitude                                       |
| ADDRESSLONGITUDE               | cdm_longitude                                      |
| ADDRESSZIPCODE                 | cdm_postalcode                                     |
| ADDRESSPOSTBOX                 | cdm_postofficebox                                  |
| ISPRIMARY                      | cdm_ispreferred                                    |



### Working time to Work Calendar Time Interval
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| ENDTIME                        | cdm_endtime                                        |
| STARTTIME                      | cdm_starttime                                      |
| WORKCALENDARDATE               | cdm_workcalendardayid.cdm_calendardate             |
| WORKCALENDARID                 | cdm_workcalendarid.cdm_name                        |
| WORKCALENDARID                 | cdm_workcalendardayid.cdm_workcalendarid.cdm_name  |



### Working times to Work Calendar Day
| Finance entity                 | Dataverse table                                    | 
|--------------------------------|----------------------------------------------------|
| CALENDARDATE                   | cdm_calendardate                                   |
| WORKCALENDARID                 | cdm_workcalendarid.cdm_name                        |
| WORKINGDAYDEFINITION           | cdm_status                                         |





## Integration considerations

- All changes made to data on either system will be subject to validation by the other system. If a failure occurs, data won't be written in either system. 

- All writes are subject to data defaulting (if custom logic occurs in Finance).

- The dual-write integrator app uses Integration keys to map between the two systems. Sometimes, it's difficult to choose the correct integration key, especially if there are multiple that satisfy the requirements. To help with this, below is a list of suggested integration keys for your mappings. 

| Dataverse Table                          | Integration Keys |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Bank Account Disbursement                | cdm_bankaccountid.cdm_accountidentification, cdm_bankaccountid.cdm_workerid.cdm_workernumber, cdm_companyid.cdm_companycode|
| Benefit Calculation Frequency            | cdm_name|
| Benefit Calculation Frequency Pay Period | cdm_payperiodid.cdm_periodstartdate, cdm_payperiodid.cdm_paycycleid.cdm_name, cdm_benefitcalculationfrequencyid.cdm_name|
| Benefit Calculation Rate                 | cdm_name|
| Benefit Calculation Rate Detail          | cdm_workerdeduction, cdm_effective, cdm_calculationrateid.cdm_name|
| Benefit Option                           | cdm_name|
| Benefit Type                             | cdm_name|
| Business Process Calendar                | cdm_name|
| Business Process Group Assignment        | cdm_name|
| Business Process Header                  | cdm_processid|
| Business Process Library Task Group      | cdm_processtype, cdm_name|
| Business Process Stage                   | cdm_name, cdm_businessprocesstype, cdm_companyid.cdm_companycode|
| Business Process Task                    | cdm_taskid|
| Business Unit                            | |
| Checklist Template Header                | cdm_businessprocesstype, cdm_name, cdm_genericsubtype|
| Checklist Template Task                  | cdm_taskid|
| Company                                  | cdm_companycode|
| Compensation Fixed Plan                  | cdm_name, cdm_company.cdm_companycode|
| Compensation Grid                        | cdm_name, cdm_companyid.cdm_companycode|
| Compensation Level                       | cdm_name|
| Compensation Pay Frequency               | cdm_name, cdm_companyid.cdm_companycode|
| Compensation Reference Point Setup       | cdm_name, cdm_companyid.cdm_companycode|
| Compensation Reference Point Setup Line  | cdm_name, cdm_referencepointsetupid.cdm_name, cdm_referencepointsetupid.cdm_companyid.cdm_companycode|
| Compensation Region                      | cdm_name|
| Compensation Structure                   | cdm_compensationlevelid.cdm_name, cdm_referencepointid.cdm_name, cdm_referencepointid.cdm_referencepointsetupid.cdm_name, cdm_referencepointid.cdm_referencepointsetupid.cdm_companyid.cdm_companycode, cdm_companyid.cdm_companycode, cdm_compensationgridid.cdm_name, cdm_compensationgridid.cdm_companyid.cdm_companycode|
| Compensation Variable Plan               | cdm_name, cdm_companyid.cdm_companycode|
| Compensation Variable Plan Level         | cdm_companyid.cdm_companycode, cdm_compensationvariableplanid.cdm_name, cdm_compensationvariableplanid.cdm_companyid.cdm_companycode, cdm_compensationlevelid.cdm_name|
| Compensation Variable Plan Type          | cdm_name, cdm_companyid.cdm_companycode|
| Currency                                 | isocurrencycode|
| Department                               | cdm_departmentnumber|
| Employment                               | cdm_employmentstartdate, cdm_workerid.cdm_workernumber, cdm_companyid.cdm_companycode|
| Ethnic Origin                            | cdm_name|
| Fixed Compensation Event                 | cdm_name, cdm_companyid.cdm_companycode|
| Job                                      | cdm_name|
| Job Function                             | cdm_name|
| Job Position                             | cdm_jobpositionnumber|
| Job Position Dimension                   | cdm_jobpositionid.cdm_jobpositionnumber, cdm_companyid.cdm_companycode|
| Job Type                                 | cdm_name|
| Language                                 | cdm_name|
| Leave Bank Transaction                   | cdm_transactiondate, cdm_transactiontype, cdm_transactionnumber, cdm_leavetypeid.cdm_type, cdm_leavetypeid.cdm_companyid.cdm_companycode, cdm_companyid.cdm_companycode, cdm_workerid.cdm_workernumber|
| Leave Enrollment                         | cdm_startdate, cdm_leaveplanid.cdm_name, cdm_leaveplanid.cdm_companyid.cdm_companycode, cdm_companyid.cdm_companycode, cdm_workerid.cdm_workernumber|
| Leave Plan                               | cdm_name, cdm_companyid.cdm_companycode|
| Leave Request                            | cdm_leaverequestnumber, cdm_companyid.cdm_companycode|
| Leave Request Detail                     | cdm_leavedate, cdm_leavetypeid.cdm_type, cdm_leavetypeid.cdm_companyid.cdm_companycode, cdm_leaverequestid.cdm_leaverequestnumber, cdm_leaverequestid.cdm_companyid.cdm_companycode|
| Leave Type                               | cdm_type, cdm_companyid.cdm_companycode|
| Leave Type Reason Code                   | cdm_reasoncodeid.cdm_name, cdm_typeid.cdm_type, cdm_typeid.cdm_companyid.cdm_companycode|
| Onboard Process Header                   | cdm_processheaderid.cdm_processid|
| Organization                             | |
| Pay Cycle                                | cdm_name|
| Pay Period                               | cdm_periodstartdate, cdm_paycycleid.cdm_name, cdm_periodenddate|
| Payroll Earning Code                     | cdm_name|
| Payroll Position Detail                  | cdm_validfrom, cdm_validto, cdm_position.cdm_jobpositionnumber|
| Person Identification Issuing Agency     | cdm_name|
| Position Type                            | cdm_name|
| Position Worker Assignment               | cdm_validfrom, cdm_jobpositionid.cdm_jobpositionnumber|
| Reason Code                              | cdm_name|
| Skill Type                               | cdm_name|
| Tax Region                               | cdm_stateorprovince, cdm_name, cdm_countryorregion, cdm_county, cdm_city|
| Team                                     | azureactivedirectoryobjectid, membershiptype|
| Title                                    | cdm_name|
| User                                     | azureactivedirectoryobjectid|
| Vesting Rule                             | cdm_name, cdm_companyid.cdm_companycode|
| Veteran Status                           | cdm_name|
| Work Calendar                            | cdm_name, cdm_companyid.cdm_companycode|
| Work Calendar Day                        | cdm_calendardate, cdm_companyid.cdm_companycode, cdm_workcalendarid.cdm_name, cdm_workcalendarid.cdm_companyid.cdm_companycode|
| Work Calendar Enrollment                 | cdm_employmentid.cdm_employmentstartdate, cdm_employmentid.cdm_workerid.cdm_workernumber, cdm_employmentid.cdm_companyid.cdm_companycode|
| Work Calendar Holiday                    | cdm_name|
| Work Calendar Holiday Line               | cdm_holidaydate, cdm_workcalendarholidayid.cdm_name|
| Work Calendar Time Interval              | cdm_starttime, cdm_workcalendardayid.cdm_calendardate, cdm_workcalendardayid.cdm_companyid.cdm_companycode, cdm_workcalendardayid.cdm_workcalendarid.cdm_name, cdm_workcalendardayid.cdm_workcalendarid.cdm_companyid.cdm_companycode, cdm_companyid.cdm_companycode, cdm_workcalendarid.cdm_name, cdm_workcalendarid.cdm_companyid.cdm_companycode|
| Worker                                   | cdm_workernumber|
| Worker Address                           | cdm_addressnumber, cdm_addresstype, cdm_workerid.cdm_workernumber|
| Worker Bank Account                      | cdm_accountidentification, cdm_workerid.cdm_workernumber|
| Worker Fixed Compensation                | cdm_linenumber, cdm_effectivedate, cdm_companyid.cdm_companycode, cdm_positionid.cdm_jobpositionnumber, cdm_workerid.cdm_workernumber, cdm_eventid.cdm_name, cdm_eventid.cdm_companyid.cdm_companycode, cdm_planid.cdm_name, cdm_planid.cdm_company.cdm_companycode|
| Worker Person Identification Number      | cdm_identificationnumber, cdm_workerid.cdm_workernumber, cdm_identificationtypeid.cdm_name|
| Worker Person Identification Type        | cdm_name|
| Worker Personal Detail                   | cdm_workerid.cdm_workernumber|

