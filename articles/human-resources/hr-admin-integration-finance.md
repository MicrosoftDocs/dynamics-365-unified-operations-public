---
# required metadata

title: Configure integration with Finance
description: This article describes the integration between Dynamics 365 Human Resources and Dynamics 365 Finance.
author: twheeloc  
ms.date: 09/19/2023
ms.topic: article
# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure integration with Finance

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



To integrate Dynamics 365 Human Resources with Dynamics 365 Finance, you can use the Human Resources to Finance template in [Data Integrator](/powerapps/administrator/data-integrator). The Human Resources to Finance template enables data flow for jobs, positions, and workers. The template allows data to flow from Human Resources into Finance, but doesn't allow data to flow from Finance into Human Resources.

![Human Resources to Finance Integration Flow.](./media/hr-admin-integration-finance-flow.png)

The Human Resources to Finance solution provides the following types of data synchronization:

- Maintain jobs in Human Resources and sync them from Human Resources to Finance
- Maintain positions and position assignments in Human Resources and sync them from Human Resources to Finance
- Maintain employments in Human Resources and sync them from Human Resources to Finance
- Maintain workers and worker addresses in Human Resources and sync them from Human Resources to Finance

## System requirements for Human Resources

The integration solution requires the following versions of Human Resources and Finance: 

- Dynamics 365 Human Resources on Dataverse
- Dynamics 365 Finance version 7.2 and later

## Template and tasks

To access the Human Resources to Finance template.

1. Open [Power Apps Admin Center](https://admin.powerapps.com/). 

2. Select **Projects**, and then select **New project** in the upper-right corner. Create a new project for each legal entity that you want to integrate into in Finance.

3. Select the **Human Resources (Human Resources Dataverse to Finance)** to synchronize records from Human Resources to Finance.

The template uses the following underlying tasks to synchronize records from Human Resources to Finance:

- **Job Functions to Compensation Job Function**
- **Departments to Operating Unit**
- **Job Types to Compensation Job Type**
- **Jobs to Jobs**
- **Jobs to Job Detail**
- **Position Types to Position Type**
- **Job Positions to Base Position**
- **Job Positions to Position Details**
- **Job Positions to Position Durations**
- **Job Positions to Position Hierarchies**
- **Workers to Worker**
- **Employments to Employment**
- **Employments to Employment Detail**
- **Position Worker Assignment to Position Worker Assignments**
- **Worker Addresses to Worker Postal Address V2**

## Template mappings

In the following template mapping tables, the name of the task contains the entities used in each application. The source (Human Resources) is on the left and the destination (Finance) is on the right.

### Job Functions to Compensation Job Function

| Dataverse table (source) | Finance entity (destination) |
|-------------------------------------|---------------------------------------------|
| cdm\_name (cdm\_Job   Function Name)  | JOBFUNCTIONID   (JOBFUNCTIONID)            |
| cdm\_description   (cdm\_description) | DESCRIPTION   (DESCRIPTION)                 |

### Departments to Operating Unit

| Dataverse table (source)           | Finance entity (destination) |
|-----------------------------------------------|---------------------------------------------|
| cdm\_name (cdm\_name)                           | NAME (NAME)                                 |
| cdm\_departmentnumber   (cdm\_departmentnumber) | OPERATINGUNITNUMBER   (OPERATINGUNITNUMBER) |
|                                               | OPERATINGUNITTYPE   (OPERATINGUNITTYPE)     |
| cdm\_description   (cdm\_description)           | NAMEALIAS   (NAMEALIAS)                     |

### Job Types to Compensation Job Type

| Dataverse table (source)   | Finance entity (destination) |
|---------------------------------------|---------------------------------------------|
| cdm\_name (cdm\_name)                   | JOBTYPEID   (JOBTYPEID)                     |
| cdm\_description   (cdm\_description)   | DESCRIPTION   (DESCRIPTION)                 |
| cdm\_exemptstatus   (cdm\_exemptstatus) | EXEMPTSTATUS   (EXEMPTSTATUS)               |

### Jobs to Jobs

| Dataverse table (source)                           | Finance entity (destination)           |
|---------------------------------------------------------------|-------------------------------------------------------|
| cdm\_name (cdm\_name)                                           | JOBID (JOBID)                                         |
| cdm\_maximumnumberofpositions   (cdm\_maximumnumberofpositions) | MAXIMUMNUMBEROFPOSITIONS   (MAXIMUMNUMBEROFPOSITIONS) |
| cdm\_allowedunlimitedpositions   (cdm\_allowunlimitedpositions) | ALLOWUNLIMITEDPOSITIONS   (ALLOWUNLIMITEDPOSITIONS)   |
| cdm\_description   (cdm\_description)                           | DESCRIPTION   (DESCRIPTION)                           |
| cdm\_jobdescription   (cdm\_jobdescription)                     | JOBDESCRIPTION   (JOBDESCRIPTIONS)                    |

### Jobs to Job Detail

| Dataverse table (source)                             | Finance entity (destination) |
|-----------------------------------------------------------------|---------------------------------------------|
| cdm\_name (cdm\_name)                                             | JOBID (JOBID)                               |
| cdm\_jobtypeid.cdm\_name   (Job Type (Job Type Name))             | JOBTYPEID   (JOBTYPEID)                     |
| cdm\_jobfunctionid.cdm\_name   (Job Function (Job Function Name)) | FUNCTIONID   (FUCNTIONID)                   |
| cdm\_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                     |
| cdm\_validto (Valid To)                                        | VALIDTO (VALIDTO)                           |
| cdm\_defaultfulltimeequivalent   (Default Full-time Equivalent)   | FULLTIMEEQUIVALENT   (FULLTIMEEQUIVALENT)   |

### Position Types to Position Type

| Dataverse table (source)       | Finance entity (destination) |
|-------------------------------------------|---------------------------------------------|
| cdm\_name (cdm\_name)                       | POSITIONTYPEID   (POSITIONTYPEID)           |
| cdm\_description   (cdm\_description)       | DESCRIPTION   (DESCRIPTION)                 |
| cdm\_classification   (cdm\_classification) | CLASSIFICATION   (CLASSIFICATION)           |

### Job Positions to Base Position

| Dataverse table (source)           | Finance entity (destination) |
|-----------------------------------------------|---------------------------------------------|
| cdm\_jobpositionnumber   (Job Position Number) | POSITIONID (POSITIONID)                      |

### Job Positions to Position Details

| Dataverse table (source)              | Finance entity (destination)       |
|--------------------------------------------------------------------------|---------------------------------------------------|
| cdm\_jobpositionnumber  (Job Position Number)                            | POSITIONID (POSITIONID)                             |
| cdm\_jobid.cdm\_name   (Job (Name))                                        | JOBID (JOBID)                                    |
| cdm\_description   (cdm\_description)                                        | DESCRIPTION   (DESCRIPTION)                       |
| cdm\_departmentid.cdm\_departmentnumber   (Department (Department Number)) | DEPARTMENTNUMBER   (DEPARTMENTNUMBER)             |
| cdm\_positiontypeid.cdm\_name   (Position Type (Name))                     | POSITIONTYPEID   (POSITIONTYPEID)                 |
| cdm\_avaialableforassignment   (Available for Assignment)                 | AVAILABLEFORASSIGNMENT   (AVAILABLEFORASSIGNMENT) |
| cdm\_validfrom   (Valid From)                                            | VALIDFROM   (VALIDFROM)                           |
| cdm\_validto (Valid To)                                                 | VALIDTO (VALIDTO)                               |
| cdm\_fulltimeequivalent   (Full-time Equivalent)                           | FULLTIMEEQUIVALENT   (FULLTIMEEQUIVALENT)         |

### Job Positions to Position Durations

| Dataverse table (source)             | Finance entity (destination) |
|-------------------------------------------------|---------------------------------------------|
| cdm\_jobpositionnumber   (Job Position Number)   | POSITIONID (POSITIONID)                      |
| Calculated   Activation (Calculated Activation) | VALIDFROM (VALIDFROM)                        |
| Calculated   Retirement (Calculated Retirement) | VALIDTO (VALIDTO)                         |

### Job Positions to Position Hierarchies

| Dataverse table (source)        | Finance entity (destination) |
|-----------------------------------------------------------------------------------------------|---------------------------------------------|
| cdm\_jobpositionnumber   (Job Position Number)                                                 | POSITIONID(POSITIONID)                      |
| cdm\_parentjobpositionid.cdmjobpositionnumber   (cdm\_parentjobpositionid.cdmjobpositionnumber) | PARENTPOSITIONID (PARENTPOSITIONID)         |
| cdm\_validfrom   (Valid From)                                                                  | VALIDFROM   (VALIDFROM)                     |
| cdm\_validto (Valid   To)                                                                      | VALIDTO (VALIDTO)                           |
| HIERARCHYTYPENAME   (HIERARCHYTYPENAME)                                                       | HIERARCHYTYPENAME   (HIERARCHYTYPENAME)     |


### Workers to Worker
| Dataverse table (source)           | Finance entity (destination)       |
|-----------------------------------------------|---------------------------------------------------|
| cdm\_birthdate   (cdm\_birthdate)               | BIRTHDATE   (BIRTHDATE)                           |
| cdm\_gender   (cdm\_gender)                     | GENDER (GENDER)                                   |
| cdm\_primaryaddress   (cdm\_primaryaddress)     | PRIMARYCONTACTEMAIL   (PRIMARYCONTACTEMAIL )      |
| cdm\_primarytelephone   (cdm\_primarytelephone) | PRIMARYCONTACTPHONE   (PRIMARYCONTACTPHONE)       |
| cdm\_facebookidentity   (cdm\_facebookidentity) | PRIMARYCONTACTFACEBOOK   (PRIMARYCONTACTFACEBOOK) |
| cdm\_twitteridentity   (cdm\_twitteridentity)   | PRIMARYCONTACTTWITTER   (PRIMARYCONTACTTWITTER)   |
| cdm\_linkedinIdentity   (cdm\_linkedinIdentity) | PRIMARYCONTACTLINKEDIN   (PRIMARYCONTACTLINKEDIN) |
| cdm\_websiteurl   (cdm\_websiteurl)             | PRIMARYCONTACTURL   (PRIMARYCONTACTURL)           |
| cdm\_firstname   (cdm\_firstname)               | FIRSTNAME   (FIRSTNAME)                           |
| cdm\_middlename   (cdm\_middlename)             | MIDDLENAME   (MIDDLENAME)                         |
| cdm\_lastname   (cdm\_lastname)                 | LASTNAME (LASTNAME)                               |
| cdm\_workernumber   (cdm\_workernumber)         | PERSONNELNUMBER   (PERSONNELNUMBER)               |
| cdm\_type (cdm\_type)                           | WORKERTYPE   (WORKERTYPE)                         |
| cdm\_state   (cdm\_state)                       | WORKSTATUS   (WORKERSTATUS)                       |

### Employments to Employment

| Dataverse table (source)                             | Finance entity (destination) |
|-----------------------------------------------------------------|---------------------------------------------|
| cdm\_employmentstartdate   (cdm\_employmentstartdate)             | EMPLOYMENTSTARTDATE   (EMPLOYMENTSTARTDATE) |
| cdm\_employmentenddate   (cdm\_employmentenddate)                 | EMPLOYMENTENDDATE   (EMPLOYMENTENDDATE)     |
| cdm\_workertype   (cdm\_workertype)                               | WORKERTYPE   (WORKERTYPE)                   |
| cdm\_workerid.cdm\_workernumber   (cdm\_workerid.cdm\_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)         |
| cdm\_companyid.cdm\_companycode   (cdm\_companyid.cdm\_companycode) | LEGALENTITYID   (LEGALENTITYID)             |

### Employments to Employment Detail

| Dataverse table (source)                             | Finance entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm\_employmentstartdate   (cdm\_employmentstartdate)             | EMPLOYMENTSTARTDATE   (EMPLOYMENTSTARTDATE)   |
| cdm\_employmentenddate   (cdm\_employmentenddate)                 | EMPLOYMENTENDDATE   (EMPLOYMENTENDDATE)       |
| cdm\_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                       |
| cdm\_validto (Valid   To)                                        | VALIDTO (VALIDTO)                             |
| cdm\_workerstartdate   (cdm\_workerstartdate)                     | WORKERSTARTDATE   (WORKERSTARTDATE)           |
| cdm\_lastdateworked   (cdm\_lastdateworked)                       | LASTDATEWORKED   (LASTDATEWORKED)             |
| cdm\_transitiondate   (cdm\_transitiondate)                       | TRANSITIONDATE   (TRANSITIONDATE)             |
| cdm\_employerunitofnotice   (cdm\_employerunitofnotice)           | EMPLOYERUNITOFNOTICE   (EMPLOYERUNITOFNOTICE) |
| cdm\_workerunitofnotice   (cdm\_workerunitofnotice)               | WORKERUNITOFNOTICE   (WORKERUNITOFNOTICE)     |
| cdm\_workerid.cdm\_workernumber   (cdm\_workerid.cdm\_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm\_companyid.cdm\_companycode   (cdm\_companyid.cdm\_companycode) | LEGALENTITYID   (LEGALENTITYID)               |
| cdm\_employernoticeamount   (cdm\_employernoticeamount)           | EMPLOYERNOTICEAMOUNT   (EMPLOYERNOTICEAMOUNT) |
| cdm\_workernoticeamount   (cdm\_workernoticeamount )              | WORKERNOTICEAMOUNT   (WORKERNOTICEAMOUNT)     |

### Position Worker Assignment to Position Worker Assignments

| Dataverse table (source)                             | Finance entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm\_workerid.cdm\_workernumber   (cdm\_workerid.cdm\_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm\_jobpositionnumber   (Job Position Number)                   | POSITIONID(POSITIONID)                        |
| cdm\_validfrom   (Valid From)                                    | VALIDFROM   (VALIDFROM)                       |
| cdm\_validto (Valid To)                                        | VALIDTO (VALIDTO)                             |

### Worker Addresses to Worker Postal Address V2

| Dataverse table (source)                             | Finance entity (destination)   |
|-----------------------------------------------------------------|-----------------------------------------------|
| cdm\_workerid.cdm\_workernumber   (cdm\_workerid.cdm\_workernumber) | PERSONNELNUMBER   (PERSONNELNUMBER)           |
| cdm\_addresstype   (cdm\_addresstype)                             | ADDRESSLOCATIONROLES   (ADDRESSLOCATIONROLES) |
| cdm\_line1   (cdm\_line1)                                         | ADDRESSSTREET   (ADDRESSSTREET)               |
| cdm\_city (cdm\_city)                                             | ADDRESSCITY   (ADDRESSCITY)                   |
| cdm\_stateorprovince   (cdm\_stateorprovince)                     | ADDRESSSTATE   (ADDRESSSTATE)                 |
| cdm\_postalcode   (cdm\_postalcode)                               | ADDRESSZIPCODE(ADDRESSZIPCODE)                |
| cdm\_countryregion   (cdm\_countryregion)                         | ADDRESSCOUNTRYREGION(ADDRESSCOUNTRYREGION)    |
| cdm\_addressnumber   (cdm\_addressnumber)                         | ADDRESSLOCATIONID(ADDRESSLOCATIONID)          |
| cdm\_ispreferred   (cdm\_ispreferred)                             | ISPRIMARY   (ISPRIMARY)                       |
| cdm\_county   (cdm\_county)                                       | ADDRESSCOUNTYID(ADDRESSCOUNTYID)              |
| cdm\_addresstype   (cdm\_addresstype)                             | ADDRESSDESCRIPTION(ADDRESSDESCRIPTION)        |

## Integration considerations

The integration from Human Resources to Finance attempts to match records based on the ID. If the records match, the Data Integrator overwrites the data in Finance with the values in Human Resources. However, an issue may occur if logically these are different records and the same ID was generated in either Human Resources or Finance based on the respective number sequence.

This issue can occur with **Worker**, which uses **Personnel number** to make the match, and **Positions**. Jobs don't use number sequences. As a result, if the same job ID exists in both Human Resources and Finance, the Human Resources information overwrites the Dynamics 365 Finance information. 

To prevent issues with duplicate IDs, you can either add a prefix on the [number sequence](/dynamics365/unified-operations/fin-and-ops/organization-administration/number-sequence-overview?toc=%2fdynamics365%2funified-operations%2ftalent%2ftoc.json), or set a beginning number on the number sequence that is beyond the range of the other system. 

The location ID used for worker address isn't part of a number sequence. When integrating a worker address from Human Resources to Finance, if the worker address already exists in Finance, a duplicate address record may be created. 

The following illustration shows an example of a template mapping in Data Integrator. 

![Template Mapping.](./media/IntegrationMapping.png)

## Migration considerations

As part of the migration from Human Resources to Finance, the dual-write maps are also supported.

The following table shows the mapping from Data Integrator maps to equivalent dual-write maps.

| Data Integrator map | Dual-write map |
|---------------------|----------------|
| Job functions to Compensation job function | Compensation job function (cdm\_jobfunctions) |
| Departments to Operating unit | Department V2 (cdm\_departments) |
| Job types to Compensation job type | Compensation job type (cdm\_jobtypes) |
| Jobs to Jobs | Jobs dual-write (cdm\_jobs) |
| Position types to Position type | Position type (cdm\_positiontypes) |
| <ul><li>Job positions to Base position</li><li>Job positions to Position details</li><li>Job positions to Position durations</li><li>Job positions to Position hierarchies</li></ul> | Job positions dual-write (cdm\_jobpositions) |
| Workers to Worker | Worker (cdm\_workers) |
| <ul><li>Employments to Employment</li><li>Employments to Employment detail</li></ul> | Employment per company (cdm\_employments) |
| Position worker assignment to Position worker assignments | Position worker assignments V2 (cdm\_positionworkerassignmentmaps) |
| Worker addresses to Worker postal address V2 | Worker postal addresses dual-write (cdm\_workeraddresss) |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
