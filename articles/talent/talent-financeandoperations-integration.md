---
# required metadata

title: Integration from Dynamics 365 Talent to Dynamics 365 Finance
description: This topic describes the integration between Talent and Finance. 
author: andreabichsel
manager: AnnBe
ms.date: 10/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope:  
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-8
ms.dyn365.ops.version: 
---

# Integration from Dynamics 365 Talent to Dynamics 365 Finance

[!include[banner](../includes/banner.md)]

This topic describes the functionality available for integration from Dynamics 365 Talent and Dynamics 365 Finance. The Talent to Finance template that is available with the [Data Integrator](https://docs.microsoft.com/powerapps/administrator/data-integrator) enables the flow of data for jobs, positions, and workers. The data flows from Talent into Finance. The template does not provide the ability for data to flow back from Finance into Talent. 

![Talent to Finance Integration Flow](./media/TalentFinOpsFlow.png)

The Talent to Finance solution provides the following types of data synchronization. 

- Maintain jobs in Talent and sync them from Talent to Finance.
- Maintain positions and position assignments in Talent and sync them from Talent to Finance.
- Maintain employments in Talent and sync them from Talent to Finance.
- Maintain workers and worker addresses in Talent and sync them from Talent to Finance.

## System requirements for Talent
The integration solution requires the following versions of Talent and Finance: 
- Dynamics 365 Talent on Common Data Service.
- Dynamics 365 Finance version 7.2 and later.

## Template and tasks

To access the template, do the following.
1. Open [PowerApps Admin Center](https://admin.powerapps.com/). 
1. Select **Projects**, and then, in the upper-right corner, select **New project** to select public templates. A new project will need to be created for each legal entity that you want to integrate into in Finance.

The following template is used to synchronize records from Talent to Finance.

- **Name of the template in Data integration:** Core HR (Talent Common Data Service to Finance)

  > [!NOTE]
  > The name of the task contains the entities used in each application. The source (Talent) is on the left and the destination
(Finance and Operations) is on the right.

The following underlying tasks are used to synchronize records from Talent to Finance.
- Job Functions to Compensation Job Function
- Departments to Operating Unit
- Job Types to Compensation Job Type
- Jobs to Jobs
- Jobs to Job Detail
- Position Types to Position Type
- Job Positions to Base Position
- Job Positions to Position Details
- Job Positions to Position Durations
- Job Positions to Position Hiearchies
- Workers to Worker
- Employments to Employment
- Employments to Employment Detail
- Position Worker Assignment to Position Worker Assignments
- Worker Addresses to Worker Postal Address V2

## Template mappings

### Job Functions to Compensation Job Function

| Common Data Service entity (source)                 | Finance and Operations entity (destination) |
|-------------------------------------|---------------------------------------------|
| cdm_name (cdm_Job   Function Name)  | JOBFUNCTIONID   (JOBFUNCTIONID)            |
| cdm_description   (cdm_description) | DESCRIPTION   (DESCRIPTION)                 |

### Departments to Operating Unit

| Common Data Service entity (source)                           | Finance and Operations entity (destination) |
|-----------------------------------------------|---------------------------------------------|
| cdm_name (cdm_name)                           | NAME (NAME)                                 |
| cdm_departmentnumber   (cdm_departmentnumber) | OPERATINGUNITNUMBER   (OPERATINGUNITNUMBER) |
|                                               | OPERATINGUNITTYPE   (OPERATINGUNITTYPE)     |
| cdm_description   (cdm_description)           | NAMEALIAS   (NAMEALIAS)                     |

### Job Types to Compensation Job Type

| Common Data Service entity (source)                   | Finance and Operations entity (destination) |
|---------------------------------------|---------------------------------------------|
| cdm_name (cdm_name)                   | JOBTYPEID   (JOBTYPEID)                     |
| cdm_description   (cdm_description)   | DESCRIPTION   (DESCRIPTION)                 |
| cdm_exemptstatus   (cdm_exemptstatus) | EXEMPTSTATUS   (EXEMPTSTATUS)               |

### Jobs to Jobs

| Common Data Service entity (source)                                           | Finance and Operations entity (destination)           |
|---------------------------------------------------------------|-------------------------------------------------------|
| cdm_name (cdm_name)                                           | JOBID (JOBID)                                         |
| cdm_maximumnumberofpositions   (cdm_maximumnumberofpositions) | MAXIMUMNUMBEROFPOSITIONS   (MAXIMUMNUMBEROFPOSITIONS) |
| cdm_allowedunlimitedpositions   (cdm_allowunlimitedpositions) | ALLOWUNLIMITEDPOSITIONS   (ALLOWUNLIMITEDPOSITIONS)   |
| cdm_description   (cdm_description)                           | DESCRIPTION   (DESCRIPTION)                           |
| cdm_jobdescription   (cdm_jobdescription)                     | JOBDESCRIPTION   (JOBDESCRIPTIONS)                    |

### Jobs to Job Detail

| Common Data Service entity (source)                                             | Finance and Operations entity (destination) |
|-----------------------------------------------------------------|---------------------------------------------|
| cdm_name (cdm_name)                                             | JOBID (JOBID)                               |
| cdm_jobtypeid.cdm_name   (Job Type (Job Type Name))             | JOBTYPEID   (JOBTYPEID)                     |
| cdm_jobfunctionid.cdm_name   (Job Function (Job Function Name)) | FUNCTIONID   (FUCNTIONID)                   |
| cdm_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                     |
| cdm_validto (Valid To)                                        | VALIDTO (VALIDTO)                           |
| cdm_defaultfulltimeequivalent   (Default Fulltime Equivalent)   | FULLTIMEEQUIVALENT   (FULLTIMEEQUIVALENT)   |

### Position Types to Position Type

| Common Data Service entity (source)                       | Finance and Operations entity (destination) |
|-------------------------------------------|---------------------------------------------|
| cdm_name (cdm_name)                       | POSITIONTYPEID   (POSITIONTYPEID)           |
| cdm_description   (cdm_description)       | DESCRIPTION   (DESCRIPTION)                 |
| cdm_classification   (cdm_classification) | CLASSIFICATION   (CLASSIFICATION)           |

### Job Positions to Base Position

| Common Data Service entity (source)                           | Finance and Operations entity (destination) |
|-----------------------------------------------|---------------------------------------------|
| cdm_jobpositionnumber   (Job Position Number) | POSITIONID (POSITIONID)                      |

### Job Positions to Position Details

| Common Data Service entity (source)                                                      | Finance and Operations entity (destination)       |
|--------------------------------------------------------------------------|---------------------------------------------------|
| cdm_jobpositionnumber  (Job Position Number)                            | POSITIONID (POSITIONID)                             |
| cdm_jobid.cdm_name   (Job (Name))                                        | JOBID (JOBID)                                    |
| cdm_description   (cdm_description)                                        | DESCRIPTION   (DESCRIPTION)                       |
| cdm_departmentid.cdm_departmentnumber   (Department (Department Number)) | DEPARTMENTNUMBER   (DEPARTMENTNUMBER)             |
| cdm_positiontypeid.cdm_name   (Position Type (Name))                     | POSITIONTYPEID   (POSITIONTYPEID)                 |
| cdm_avaialableforassignment   (Available for Assignment)                 | AVAILABLEFORASSIGNMENT   (AVAILABLEFORASSIGNMENT) |
| cdm_validfrom   (Valid From)                                            | VALIDFROM   (VALIDFROM)                           |
| cdm_validto (Valid To)                                                 | VALIDTO (VALIDTO)                               |
| cdm_fulltimeequivalent   (Fulltime Equivalent)                           | FULLTIMEEQUIVALENT   (FULLTIMEEQUIVALENT)         |

### Job Positions to Position Durations

| Common Data Service entity (source)                             | Finance and Operations entity (destination) |
|-------------------------------------------------|---------------------------------------------|
| cdm_jobpositionnumber   (Job Position Number)   | POSITIONID (POSITIONID)                      |
| Calculated   Activation (Calculated Activation) | VALIDFROM (VALIDFROM)                        |
| Calculated   Retirement (Calculated Retirement) | VALIDTO (VALIDTO)                         |

### Job Positions to Position Hiearchies

| Common Data Service entity (source)                                                                           | Finance and Operations entity (destination) |
|-----------------------------------------------------------------------------------------------|---------------------------------------------|
| cdm_jobpositionnumber   (Job Position Number)                                                 | POSITIONID(POSITIONID)                      |
| cdm_parentjobpositionid.cdmjobpositionnumber   (cdm_parentjobpositionid.cdmjobpositionnumber) | PARENTPOSITIONID (PARENTPOSITIONID)         |
| cdm_validfrom   (Valid From)                                                                  | VALIDFROM   (VALIDFROM)                     |
| cdm_validto (Valid   To)                                                                      | VALIDTO (VALIDTO)                           |
| HIERARCHYTYPENAME   (HIERARCHYTYPENAME)                                                       | HIERARCHYTYPENAME   (HIERARCHYTYPENAME)     |


### Workers to Worker
| Common Data Service entity (source)                           | Finance and Operations entity (destination)       |
|-----------------------------------------------|---------------------------------------------------|
| cdm_birthdate   (cdm_birthdate)               | BIRTHDATE   (BIRTHDATE)                           |
| cdm_gender   (cdm_gender)                     | GENDER (GENDER)                                   |
| cdm_primaryaddress   (cdm_primaryaddress)     | PRIMARYCONTACTEMAIL   (PRIMARYCONTACTEMAIL )      |
| cdm_primarytelephone   (cdm_primarytelephone) | PRIMARYCONTACTPHONE   (PRIMARYCONTACTPHONE)       |
| cdm_facebookidentity   (cdm_facebookidentity) | PRIMARYCONTACTFACEBOOK   (PRIMARYCONTACTFACEBOOK) |
| cdm_twitteridentity   (cdm_twitteridentity)   | PRIMARYCONTACTTWITTER   (PRIMARYCONTACTTWITTER)   |
| cdm_linkedinIdentity   (cdm_linkedinIdentity) | PRIMARYCONTACTLINKEDIN   (PRIMARYCONTACTLINKEDIN) |
| cdm_websiteurl   (cdm_websiteurl)             | PRIMARYCONTACTURL   (PRIMARYCONTACTURL)           |
| cdm_firstname   (cdm_firstname)               | FIRSTNAME   (FIRSTNAME)                           |
| cdm_middlename   (cdm_middlename)             | MIDDLENAME   (MIDDLENAME)                         |
| cdm_lastname   (cdm_lastname)                 | LASTNAME (LASTNAME)                               |
| cdm_workernumber   (cdm_workernumber)         | PERSONNELNUMBER   (PERSONNELNUMBER)               |
| cdm_type (cdm_type)                           | WORKERTYPE   (WORKERTYPE)                         |
| cdm_state   (cdm_state)                       | WORKSTATUS   (WORKERSTATUS)                       |

### Employments to Employment

| Common Data Service entity (source)                                             | Finance and Operations entity (destination) |
|-----------------------------------------------------------------|---------------------------------------------|
| cdm_employmentstartdate   (cdm_employmentstartdate)             | EMPLOYMENTSTARTDATE   (EMPLOYMENTSTARTDATE) |
| cdm_employmentenddate   (cdm_employmentenddate)                 | EMPLOYMENTENDDATE   (EMPLOYMENTENDDATE)     |
| cdm_workertype   (cdm_workertype)                               | WORKERTYPE   (WORKERTYPE)                   |
| cdm_workerid.cdm_workernumber   (cdm_workerid.cdm_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)         |
| cdm_companyid.cdm_companycode   (cdm_companyid.cdm_companycode) | LEGALENTITYID   (LEGALENTITYID)             |

### Employments to Employment Detail

| Common Data Service entity (source)                                             | Finance and Operations entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm_employmentstartdate   (cdm_employmentstartdate)             | EMPLOYMENTSTARTDATE   (EMPLOYMENTSTARTDATE)   |
| cdm_employmentenddate   (cdm_employmentenddate)                 | EMPLOYMENTENDDATE   (EMPLOYMENTENDDATE)       |
| cdm_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                       |
| cdm_validto (Valid   To)                                        | VALIDTO (VALIDTO)                             |
| cdm_workerstartdate   (cdm_workerstartdate)                     | WORKERSTARTDATE   (WORKERSTARTDATE)           |
| cdm_lastdateworked   (cdm_lastdateworked)                       | LASTDATEWORKED   (LASTDATEWORKED)             |
| cdm_transitiondate   (cdm_transitiondate)                       | TRANSITIONDATE   (TRANSITIONDATE)             |
| cdm_employerunitofnotice   (cdm_employerunitofnotice)           | EMPLOYERUNITOFNOTICE   (EMPLOYERUNITOFNOTICE) |
| cdm_workerunitofnotice   (cdm_workerunitofnotice)               | WORKERUNITOFNOTICE   (WORKERUNITOFNOTICE)     |
| cdm_workerid.cdm_workernumber   (cdm_workerid.cdm_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm_companyid.cdm_companycode   (cdm_companyid.cdm_companycode) | LEGALENTITYID   (LEGALENTITYID)               |
| cdm_employernoticeamount   (cdm_employernoticeamount)           | EMPLOYERNOTICEAMOUNT   (EMPLOYERNOTICEAMOUNT) |
| cdm_workernoticeamount   (cdm_workernoticeamount )              | WORKERNOTICEAMOUNT   (WORKERNOTICEAMOUNT)     |

### Position Worker Assignment to Position Worker Assignments

| Common Data Service entity (source)                                             | Finance and Operations entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm_workerid.cdm_workernumber   (cdm_workerid.cdm_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm_jobpositionnumber   (Job Position Number)                   | POSITIONID(POSITIONID)                        |
| cdm_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                       |
| cdm_validto (Valid   To)                                        | VALIDTO (VALIDTO)                             |

### Worker Addresses to Worker Postal Address V2

| Common Data Service entity (source)                                             | Finance and Operations entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm_workerid.cdm_workernumber   (cdm_workerid.cdm_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm_addresstype   (cdm_addresstype)                             | ADDRESSLOCATIONROLES   (ADDRESSLOCATIONROLES) |
| cdm_line1   (cdm_line1)                                         | ADDRESSSTREET   (ADDRESSSTREET)               |
| cdm_city (cdm_city)                                             | ADDRESSCITY   (ADDRESSCITY)                   |
| cdm_stateorprovince   (cdm_stateorprovince)                     | ADDRESSSTATE   (ADDRESSSTATE)                 |
| cdm_postalcode   (cdm_postalcode)                               | ADDRESSZIPCODE(ADDRESSZIPCODE)                |
| cdm_countryregion   (cdm_countryregion)                         | ADDRESSCOUNTRYREGION(ADDRESSCOUNTRYREGION)    |
| cdm_addressnumber   (cdm_addressnumber)                         | ADDRESSLOCATIONID(ADDRESSLOCATIONID)          |
| cdm_ispreferred   (cdm_ispreferred)                             | ISPRIMARY   (ISPRIMARY)                       |
| cdm_county   (cdm_county)                                       | ADDRESSCOUNTYID(ADDRESSCOUNTYID)              |
| cdm_addresstype   (cdm_addresstype)                             | ADDRESSDESCRIPTION(ADDRESSDESCRIPTION)        |

## Integration considerations
When integrating data from Talent to Finance, the integration will attempt to match records based on the ID. If the match
occurs, the data in Finance will be overwritten with the values in Talent. However, an issue may occur if logically
these are different records and the same ID was generated in either Talent or Finance based on the respective number sequence.

The areas where this can occur are Worker, which uses Personnel number to make the match, and Positions. Jobs do not use number sequences. As a result, if the same job ID is present in both Talent and Finance, the Talent information will overwrite the Finance and Operations information. 

To prevent issues with duplicate IDs, you can either add a prefix on the [number sequence](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/organization-administration/number-sequence-overview?toc=/dynamics365/unified-operations/talent/toc.json), or set a beginning number on the number sequence that is beyond the range of the other system. 

The location ID used for worker address isn't part of a number sequence. When integrating a worker address from Talent to Finance, if the worker address already exists in Finance, a duplicate address record may be created. 

The following illustration shows an example of a template mapping in Data Integrator. 

![Template Mapping](./media/IntegrationMapping.png)




