---
# required metadata

title: Configure your payroll integration
description: This topic provides information about configuring the integration of both Microsoft Dynamics 365 for Talent and Ceridian Dayforce so you can process a pay run.
author: jcart1106
manager: AnnBe
ms.date: 05/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Configure your payroll integration

[!include [banner](includes/banner.md)]

The integration between Microsoft Dynamics 365 for Talent, Ceridian Dayforce
relies on several configuration steps that are described in this topic. You must
configure the integration in both Talent and Dayforce before processing a pay
run.

When you use a service, such as Ceridian Dayforce, to complete pay runs, you
must enable the integration in Talent. The integration requires certain data
from Talent, so you’ll must also verify that data that’s mapped to Dayforce is
configured in Talent in a manner that supports the integration. The integration
uses the following broad categories of data:

-   Human resources data

-   Compensation data

-   Payroll data, including pay cycle, pay periods, and earning codes

-   Worker data

This topic lists the steps to follow to enable the integration and explains the
types of data and the configuration details that the integration requires.

Enable integration
==================

Within Talent, the integration will need to be enabled and you’ll need to enter
the configuration information to connect to Ceridian Dayforce. If you also want
the resulting general ledger transaction to be imported into Finance and
Operations, you’ll need to set up an Azure Storage Account and enter the
connection string within Finance and Operations.

To turn on the integration within Talent, follow these steps:

1.  On the **System Administration** page, click **Integration configuration.**

2.  Enter the **secure FTP endpoint** and **secure FTP folder path.**

3.  Enter the **user name** and **password** that will access the secure FTP
    endpoint and folder path.

4.  Test the connection if necessary and select **Yes** to **Enable payroll
    integration**.

When the integration is turned on, the data export package and files will be
created, and the frequency specified. You can change this frequency as needed.

For more information about Azure Storage Accounts and Azure Storage Connection
Strings, refer to the following Azure documentation:

[Azure Storage Accounts](https://docs.microsoft.com/en-us/azure/storage/common/storage-create-storage-account?toc=%2fazure%2fstorage%2ffiles%2ftoc.json)

[Azure Storage Connection Strings](https://docs.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string)

Configure your data 
====================

To process payroll, human resource data needs to be configured in Dynamics 365
for Talent. Organizational data such as jobs and positions, along with benefits
and compensation information, needs to be set up. This information provides the
employment, pay and deduction information required to generate employees’ pay.

Human resource data
-------------------

### Benefits 

Human resources provides tools to set up and maintain benefits, deductions, and
workers' compensation plans that an organization offers or processes for its
workers.

When creating benefits, keep in mind the following data and configurations used
within Dayforce.

#### Benefit plan

-   Plan (required)

-   Type (required)

-   Payroll impact (required)

-   Recover arrears

-   Deduction method

-   Deduction priority

-   Limit period

-   Limit amount

#### Benefit

-   Plan (required)

-   Type (required)

-   Option (required)

-   Benefit ID (required)

-   Frequency

-   Basis

-   Amount or rate

-   Earning code

#### Frequencies supported 

-   Weekly

-   Bi-weekly

-   Semi-monthly

-   Monthly

#### Basis supported 

-   Fixed amount

-   Percent of earnings

-   Productive hours

Dayforce creates the following deductions based on the payroll impact defined on
the benefit plan:

| **Selected in Talent**     | **Result in Dayforce**                       |
|----------------------------|----------------------------------------------|
| None                       | No deduction is created                      |
| Deduction only             | Employee deduction is created                |
| Contribution only          | Employer deduction is created                |
| Deduction and contribution | Employee and employer deductions are created |

Define and manage a benefits program

[Deliver an employee benefits program](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/deliver-employee-benefits-program)

[Create a new benefit](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/create-new-benefit)

[Define benefit eligibility and rules and policies](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-benefit-eligibility-rules-policies)

[Enroll and remove benefits from workers](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-remove-benefits-workers)

### Compensation 

Compensation management is used to control the delivery of base pay and awards.
An employee's fixed base pay and merit increases are controlled through fixed
compensation plans. The payment of incentive pay, such as bonus payments,
performance awards, stock options, and grants, as well as one-time awards, are
controlled through variable compensation plans.

Compensation information is used by Dayforce to calculate an employee’s hourly
or annual rate. Fixed compensation plans and pay rate conversions are required.
Employees must be associated with a fixed compensation plan.

Compensation plans

[Create fixed compensation plans](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/create-fixed-compensation-plans)

[Create variable compensation plans](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/create-variable-compensation-plans)

[Develop salary/compensation structure and plans](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/develop-salary-compensation-structure-plan)

[Process compensation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/process-compensation)

[Define compensation and process results](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-compensation-process-calculate-results)

[Enroll an employee in a fixed compensation plan](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-employee-fixed-compensation-plan)

[Enroll an employee in a variable compensation plan](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-employee-fixed-compensation-plan)

### Jobs 

A job is a collection of tasks and responsibilities that are required of a
person who performs a job.

[Setting up the components of a job](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/create-job)

[Define new jobs](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-new-jobs)

Positions

A position is an individual instance of a job. For example, the position, “Sales
manager (East),” is one of the positions that is associated with the job, “Sales
manager.” A position exists in a department and can have only one worker
associated with it.

Keep the following data and configuration in mind when setting up positions.

-   Position (required)

-   Description (required)

-   Job (required)

-   Department (required)

-   Position type (required)

-   Full-time equivalent

-   Annual regular hours (required)

-   Paid by legal entity (required)

-   Pay cycle (required)

-   Default financial dimension – Cost center (required)

-   Worker assignment – Worker, assignment start, assignment end, reason code

If multiple positions are in the same department and associated with the same
job, it will be consolidated into a single position in Dayforce.

[Organization your workforce using departments, jobs and positions](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/departments-jobs-positions#positions)

[Set up positions](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/set-up-positions)

### Departments

A department is an operating unit that represents a category or functional area
of an organization. A department is responsible for a specific area of the
organization, such as sales, accounting, or human resources. You can use
departments to report on functional areas. Departments might have profit and
loss responsibility.

[Create a department and associate it with the department hierarchy](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/create-department-add-department-hierarchy)

[Define new departments](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-new-departments)

### Pay cycles and pay periods

A pay cycle determines how often payroll is run and on what specific days
workers are paid. For example, a pay cycle might be monthly, and employees might
be paid on the last day of the month, or it might be weekly and employees might
be paid on the Tuesday following the end of the pay period. Pay cycles are
assigned to positions to control when workers in those positions are paid.

After you create pay cycles, you can generate pay periods for each cycle. Each
pay period includes a default payment date that is based on information that you
provide. However, you can modify the default payment date in a pay period to
allow for exceptions, such as when the payment date falls on a holiday.

The following information is used in Dayforce.

-   Pay cycle (required)

-   Pay cycle frequency (required)

-   Period start date (first pay period required)

-   Default payment date (first pay period required)

This information is integrated with Dayforce as pay groups and will be separated
by country for each pay cycle. At least one pay period is required to be
generated prior to integration. Dayforce will generate pay group calendars and
payment dates based on first pay period start date and default payment date
setup in Talent.

### Earning codes

Earning codes uniquely identify every type of earnings that workers receive. The
codes various parameters that relate to earnings, such as accounting rules, tax
laws, reporting requirements, and gross up capability.

The following information is used in Dayforce.

-   Earning Code (required)

-   Description

-   Unit of measure

-   Productive

Worker data
-----------

Records for your various types of workers are important to your human resources
and payroll systems. The information that you enter can be used to track workers
and personal information.

You can maintain the following information for workers:

Basic – Maintain basic worker information, such as contact information,
demographic information, identification information, family information,
military service status, expatriate information, and personal and emergency
contacts.

Employment – Maintain information about workers’ employment, such as company or
organization affiliation, position assignment, start and end dates, work
eligibility, terms of employment, pension, vacation, and relocation information.

Leave and absence – Maintain information about workers’ absences, such as
working calendars, absence transactions, and absence setup.

Compensation and payroll – Maintain information about workers’ compensation
plans and payroll information, such as plan enrollment, awards, performance,
commission, tax information, retirement, and salary deductions.

When entering worker information, the following data and configuration is used
within Dayforce.

### General information

-   Personnel number (required)

-   First name (required)

-   Last name (required)

-   Middle name

-   Seniority date

-   Known as

### Personal information

-   Marital status (required)

-   Birth date (required)

-   Gender (required)

-   Person with disabilities

-   Nationality country region (only for Mexico)

### Address information

-   Primary (required)

-   Country/region (required)

-   Postal code (required)

-   Street Number (required) (Only for Mexico)

-   Building Complement (Only for Mexico)

-   City (required)

-   State (required)

-   County (required)

### Contact information 

-   Primary (required)

-   Contact number (required)

-   Extension

### Payroll information and earning codes

Employees may be elected certain earnings at a given frequency of payment and
have a preferred payment method. Below are the fields used by Dayforce to ensure
those preferences and elections are met.

#### Earning codes

-   Position (required)

-   Earning Code (required)

-   Frequency (required)

-   Amount (required)

#### Payroll information

-   Payment Method

-   Economic Region (required)

-   Employee Benefits ID

-   National ID Number (required)

-   Military Service Number

-   Shift ID (required)

-   Tax Number (required)

-   Union ID (required)

-   Work Day ID (required)

-   Work Permit Number

> [!NOTE]
> For payment method, Mexico supports Cash, Check (company’s manual check), and Electronic Payment. If none is specified, it will default Check.

### Employment details

Employment detail history will be used as key information to derive employee’s
hire, termination and rehire status in Dayforce. Dayforce only supports one
active employment record at a given time.

-   Employment start date (required)
-   Employment end date
-   Start date
-   Adjusted start date
-   Termination date (required upon termination)
-   Termination reason (required upon termination)

Employee’s key dates are derived using the following:

| **Talent**            | **Dayforce**                                                                                        |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| Most recent hire date | Employment start of current non-terminated employment history record                                |
| Termination date      | Termination date of current non-terminated employment history record                                |
| Start date            | Adjusted start date, start date or employment start of current non-active employment history record |
| Original hire date    | Employment start of earliest employment history record                                              |

### Compensation

Each employee must have a fixed compensation plan associated with their primary
position throughout an employment period. This starts from the date they were
hired (or employment start date) until termination.

-   Effective Date (required)
-   Expiration date
-   Pay Rate (required)
-   Pay Rate Conversions (required)
-   Annual equivalent (required)
-   Hourly equivalent (required)

If an hourly employee has multiple positions, the primary position’s fixed
compensation is imported into Dayforce as the employee level base rate/salary.
For non-primary positions, the hourly rate is saved to its respective position
in Dayforce.

If a salaried employee has multiple positions, the cumulative hour rate and
annual salary across all active positions is derived and used as the employee
level base rate/salary.

### Identification numbers

#### Social security identifier 

Employees are required to have one primary identifier. This needs to be “SSN”
identification type which will be automatically derived as their Social Security
identifier in Dayforce required for hire.

-   Primary (required)
-   Identification Type = “SSN”
-   Issued Date
-   Expiration Date

Employees can declare multiple identification numbers with Identification Type
equivalent to “SSN”. Only the record marked as Primary will be integrated into
Dayforce, regardless of whether the number is active or expired.

### Bank accounts and disbursements

Employees choosing to be paid via bank account transfers need to have valid bank
account information entered.

| **Talent**                     | **Dayforce**                                                                                    |
|--------------------------------|-------------------------------------------------------------------------------------------------|
| Bank account number (required) |                                                                                                 |
| SWIFT code (required)          | Bank ID field of Mexico’s bank information                                                      |
| Branch number (required)       |                                                                                                 |
| Bank account type (required)   | Account type field of Mexico’s bank information. Supported values include Checking and Payroll. |

> [!NOTE]
> Employees who choose to be paid via bank account transfers will be required to provide a link to a remainder account under a Mexico Legal Entity and associated to a valid Mexico bank account. All other non-remainder accounts are ignored.

### Address information

Employees need to have one primary location which will be used to determine
their primary residence for tax purposes in Dayforce.

-   Primary (required)
-   Country/region (required)
-   Zip/postal code (required)
-   Street (required)
-   Street Number (required)
-   Building Complement
-   City (required)
-   State (required)
-   County (required)

Configure your data to generate payroll in United States and Canada
=================================================

If you’re generating a pay for employees in the United States and Canada, the following elements must
be configured.

-   Departments are required on positions
-   Cost centers need to be set as financial dimensions and need to be the first
    element in the Default Financial Dimension string

Job types
---------

Job types are used to group similar jobs into categories. Job types are required
for processing payroll in the United States and Canada. Examples of job types include full-time and
part-time, or salary and hourly pay. Job types are mapped to Dayforce as Pay
Types that determines and employee is Hourly or Salaried.

The following job types and descriptions are required:

| **Job Type\*** | **Description** |
|----------------|-----------------|
| Hourly         | Hourly       |
| Salaried       | Salaried     |

Position types 
---------------

You use position types to describe whether the position is full-time, part-time
or something else. Position types are mapped to Dayforce as Pay Classes that
indicate whether an employee is full-time or part-time.

The following position types and descriptions are required:

| **Position Type\*** | **Description**    |
|---------------------|--------------------|
| Full-time           | Full time employee |
| Part-time           | Part time employee |

Reason codes
------------

Reason codes provide information about the status of an employee. Reason codes
are mapped to Dayforce as Status Reasons that indicate the reason for changes in
an employee’s position or employment status.

The following reason codes and descriptions are required:

| **Reason Code\***      | **Description**                | **Applicable scenarios** |
|------------------------|--------------------------------|--------------------------|
| RESIGNATION            | Resignation                    | Terminate worker         |
| TERMINATION            | Termination                    | Terminate worker         |
| RETIREMENT             | Retirement                     | Terminate worker         |
| OTHER                  | Other Reasons                  | Terminate worker         |
| DEATH                  | Death                          | Terminate worker         |
| LEAVEOFABSENCE         | Leave of Absence               | Terminate worker         |
| CONTRACTEND            | End of Contract                | Terminate worker         |
| SALARYCHANGE           | Change of Salary               | Compensation             |

Marital status
--------------

Marital Status values are mapped to Dayforce and translated as appropriate to
the accepted values upon integration.

Marital status is mapped to Dayforce as follows:

| **Talent**             | **Dayforce**              |
|------------------------|---------------------------|
| Married                | Married                   |
| Single                 | Single                    |
| Widowed                | Widowed                   |
| Divorced               | Divorced                  |
| Registered Partnership | Domestic Partnership      |
| None                   | None |
| Cohabiting             | Cohabiting |

Gender
------

Gender values are mapped to Dayforce and translated as appropriate to the
accepted values upon integration.

Gender designation is mapped to Dayforce as follows:

| **Talent**   | **Dayforce**              |
|--------------|---------------------------|
| Male         | Male                      |
| Female       | Female                    |
| Non-specific | *Not supported* |

Earning codes
-------------

Earning codes uniquely identify every type of earnings that workers receive. The
codes cover a number of parameters that relate to earnings, such as accounting
rules, tax laws, reporting requirements, and gross-up capability. If a
non-supported frequency is used, it will default to being calculated based on
Every Pay.

Supported frequencies

-   All

-   EVERYPAY

-   EACHPAYPERIOD

-   EVRYOTHRPAYODD

-   EVRYOTHRPAYEVN

-   1OFMTH

-   LASTOFMTH

-   2OFMTH

-   3OFMTH

-   4OFMTH

-   5OFMTH

-   1N2OFMTH

-   3N4OFMTH

-   1N3OFMTH

-   1N4OFMTH

-   2N3OFMTH

-   2N4OFMTH

-   1N2N3OFMTH

-   1N2N4OFMTH

-   1N3N4OFMTH

-   2N3N4OFMTH

-   1N2N3N4OFMTH - 1N2N3N4OFMTH

-   2N3N4N5OFMth - 2N3N4N5OFMth

-   1OFQTR - 1OFQTR

-   LASTOFQTR – LASTOFQTR

-   LASTMTHOFQTR – LASTMTHOFQTR

-   1OFYEAR - 1OFYEAR

-   LASTOFYEAR – LASTOFYEAR

-   NOVNDECOFYEAR - NOVNDECOFYEAR

Addresses
---------

Identifying specific country, state, and county (municipality) codes requires
specific formats that Dayforce and in-country providers can recognize. While the
format for cities is flexible, each city must be associated with a state.

| **Talent**          | **Dayforce**          |
|---------------------|-----------------------|
| Country/Region      | Country Code          |
| Zip/Postal Code     | Postal Code           |
| State               | State Code            |
| City                | City                  |
| County              | County (Municipality) |
| Street              | Address Line 1        |

Tax regions
-------------

Tax regions are used to determine the appropriate tax to be applied during payroll generation. Tax regions are mapped to Dayforce as Location Addresses. The default tax region needs to be assoicated with the worker's active position. 


-   Tax region (required)

-   Country/Region (required)

-   State (required)

-   County 

-   City (required)

Configure your data to generate payroll in Mexico
=================================================

If you’re generating a pay for employees in Mexico, the following elements must
be configured.

-   Departments are required on positions
-   Cost centers need to be set as financial dimensions and need to be the first
    element in the Default Financial Dimension string

Job types
---------

Job types are used to group similar jobs into categories. Job types are required
for processing payroll in Mexico. Examples of job types include full-time and
part-time, or salary and hourly pay. Job types are mapped to Dayforce as Pay
Types that determines and employee is Hourly or Salaried.

The following job types and descriptions are required:

| **Job Type\*** | **Description** |
|----------------|-----------------|
| Hourly         | MX Hourly       |
| Salaried       | MX Salaried     |

Position types 
---------------

You use position types to describe whether the position is full-time, part-time
or something else. Position types are mapped to Dayforce as Pay Classes that
indicate whether an employee is full-time or part-time.

The following position types and descriptions are required:

| **Position Type\*** | **Description**    |
|---------------------|--------------------|
| Full-time           | Full time employee |
| Part-time           | Part time employee |

Reason codes
------------

Reason codes provide information about the status of an employee. Reason codes
are mapped to Dayforce as Status Reasons that indicate the reason for changes in
an employee’s position or employment status.

The following reason codes and descriptions are required:

| **Reason Code\***      | **Description**                | **Applicable scenarios** |
|------------------------|--------------------------------|--------------------------|
| DEPARTUREBEFOREPAYMENT | Departure before first payroll | Terminate worker         |
| RESIGNATION            | Resignation                    | Terminate worker         |
| PENSION                | Pension                        | Terminate worker         |
| TERMINATION            | Termination                    | Terminate worker         |
| RETIREMENT             | Retirement                     | Terminate worker         |
| ABSENTEE               | Absentee                       | Terminate worker         |
| OTHER                  | Other Reasons                  | Terminate worker         |
| CLOSURE                | Business Closure               | Terminate worker         |
| DEATH                  | Death                          | Terminate worker         |
| LEAVEOFABSENCE         | Leave of Absence               | Terminate worker         |
| CONTRACTEND            | End of Contract                | Terminate worker         |
| SALARYCHANGE           | Change of Salary               | Compensation             |

Terms of employment
-------------------

Terms of employment are used to create categories of employment terms. The terms
are mapped to Dayforce as Employment Indicator values.

The following terms of employment and descriptions are required:

| **Terms of Employment\*** | **Description** |
|---------------------------|-----------------|
| Regular                   | Regular         |
| Direct                    | Direct          |
| Internship                | Internship      |
| Permanent                 | Permanent       |

Marital status
--------------

Marital Status values are mapped to Dayforce and translated as appropriate to
the accepted values upon integration.

Marital status is mapped to Dayforce as follows:

| **Talent**             | **Dayforce**              |
|------------------------|---------------------------|
| Married                | Married                   |
| Single                 | Single                    |
| Widowed                | Widowed                   |
| Divorced               | Divorced                  |
| Registered Partnership | Domestic Partnership      |
| None                   | *Not supported by Mexico* |
| Cohabiting             | *Not supported by Mexico* |

Gender
------

Gender values are mapped to Dayforce and translated as appropriate to the
accepted values upon integration.

Gender designation is mapped to Dayforce as follows:

| **Talent**   | **Dayforce**              |
|--------------|---------------------------|
| Male         | Male                      |
| Female       | Female                    |
| Non-specific | *Not supported by Mexico* |

Payment method
--------------

Payment methods are used to provide the employee and the company a way to
describe how employees will be paid. Payment methods are mapped to Dayforce and
translated as appropriate to the accepted values upon integration.

The following describes how marital status is mapped to Dayforce:

| **Talent**         | **Dayforce**              |
|--------------------|---------------------------|
| Cash               | Cash                      |
| Electronic Payment | Transfer                  |
| Check              | Cheque                    |
| Bank Draft         | *Not supported by Mexico* |
| Other              | *Not supported by Mexico* |

Bank account type
-----------------

Bank account types are used for electronic payments to employees. Bank account
types are mapped to Dayforce as Transfer account information. The Bank account
types are translated as appropriate to the accepted values upon integration.

| **Talent**        | **Dayforce**              |
|-------------------|---------------------------|
| Checking Account  | CheckingAccount           |
| Payroll Account   | PayrollAccount            |
| Savings Account   | *Not supported by Mexico* |
| BankGirot account | *Not supported by Mexico* |
| PlusGirot account | *Not supported by Mexico* |

Earning codes
-------------

Earning codes uniquely identify every type of earnings that workers receive. The
codes cover a number of parameters that relate to earnings, such as accounting
rules, tax laws, reporting requirements, and gross-up capability. If a
non-supported frequency is used, it will default to being calculated based on
Every Pay.

Supported frequencies

-   All

-   EVERYPAY

-   EACHPAYPERIOD

-   EVRYOTHRPAYODD

-   EVRYOTHRPAYEVN

-   1OFMTH

-   LASTOFMTH

-   2OFMTH

-   3OFMTH

-   4OFMTH

-   5OFMTH

-   1N2OFMTH

-   3N4OFMTH

-   1N3OFMTH

-   1N4OFMTH

-   2N3OFMTH

-   2N4OFMTH

-   1N2N3OFMTH

-   1N2N4OFMTH

-   1N3N4OFMTH

-   2N3N4OFMTH

-   1N2N3N4OFMTH - 1N2N3N4OFMTH

-   2N3N4N5OFMth - 2N3N4N5OFMth

-   1OFQTR - 1OFQTR

-   LASTOFQTR – LASTOFQTR

-   LASTMTHOFQTR – LASTMTHOFQTR

-   1OFYEAR - 1OFYEAR

-   LASTOFYEAR – LASTOFYEAR

-   NOVNDECOFYEAR - NOVNDECOFYEAR

Addresses
---------

Identifying specific country, state, and county (municipality) codes requires
specific formats that Dayforce and in-country providers can recognize. While the
format for cities is flexible, each city must be associated with a state.

| **Talent**          | **Dayforce**          |
|---------------------|-----------------------|
| Country/Region      | Country Code          |
| Zip/Postal Code     | Postal Code           |
| State               | State Code            |
| City                | City                  |
| County              | County (Municipality) |
| Street              | Address Line 1        |
| Street Number       | Address Line 2        |
| Building Complement | Address Line 5        |


Passport number
---------

Employees may declare Passport information with identification type equivalent
to “Passport”. This information will be integrated to Dayforce as part of an
employee’s Mexico-specific information.

-   Identification Type = “Passport”
-   Issued Date
-   Expiration Date

Employees can declare multiple identification numbers with Identification Type
equivalent to “Passport”. In such case, only current active Passport will be
integrated to Dayforce. In cases where all Passport entries are expired, the
passport issued most recently will be integrated into Dayforce.
