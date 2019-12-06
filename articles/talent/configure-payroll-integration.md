---
# required metadata

title: Configure the payroll integration between Talent and Dayforce
description: This topic explains how to configure the integration between Microsoft Dynamics 365 Talent and Ceridian Dayforce so that you can process a pay run.
author: andreabichsel
manager: AnnBe
ms.date: 06/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Configure payroll integration between Talent and Dayforce

The integration between Microsoft Dynamics 365 Talent and Ceridian Dayforce relies on several configuration steps that are described in this topic. You must configure the integration in both Talent and Dayforce before you can process a pay run.

When you use a service such as Dayforce to complete pay runs, you must enable the integration in Talent. The integration requires specific data from Talent. Therefore, you must verify that data that is mapped to Dayforce is configured in Talent in a manner that supports the integration. The integration uses the following broad categories of data:

- Human resources data
- Compensation data
- Payroll data, such as pay cycles, pay periods, and earning codes
- Worker data

This topic describes the steps that you must follow to enable the integration. It also explains the types of data and the configuration details that the integration requires.

## Enable the integration

In Talent, you must turn on the integration and enter the configuration information to connect to Dayforce. If you want the general ledger transaction that is produced to be imported into Microsoft Dynamics 365 Finance, you must also set up a Microsoft Azure storage account and enter the Azure Storage connection string in Finance.

To turn on the integration in Talent, follow these steps.

1. On the **System administration** page, select **Integration configuration**.
2. Enter the secure File Transfer Protocol (FTP) endpoint and the secure FTP folder path.
3. Enter the user name and password of the user who will access the secure FTP endpoint and folder path.
4. Test the connection, as required, and set the **Enable payroll integration** option to **Yes**.

When the integration is turned on, the data export package and files are created, and the frequency is set. You can change this frequency as you require.

For more information about Azure storage accounts and Azure Storage connection strings, see the following Azure topics:

- [About Azure storage accounts](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account?toc=%2fazure%2fstorage%2ffiles%2ftoc.json)
- [Configure Azure Storage connection strings](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)

### Technical details when payroll integration is enabled

Turning on the payroll integration has two primary effects:

- A data export project named "Payroll integration export" is created. This project contains the entities and fields required for the payroll integration. To examine the project, go to **System administration**, select the **Data management** tile, and then open the data project from the list of projects.
- This batch job executes the data export project, encrypts the resulting data package, and transfers the data package file to the SFTP endpoint configured on the **Integration configuration** screen.

> [!NOTE]
> The data package transferred to the SFTP endpoint is encrypted using a key that is unique to the package. The key is in an Azure Key Vault that is accessible only by Ceridian. It is not possible to decrypt and examine the data package contents. If you need to examine the contents of the data package, you need to export the "Payroll integration export" data project manually, download it, and then open it. Manual export will not apply encryption or transfer the package.

## Configure your data 

To process payroll, you must configure human resource data in Talent. You must set up organizational data, such as jobs and positions, together with benefits and compensation information. This information provides the employment, pay, and deduction information that is required in order to generate employee pay.

### Human resource data

#### Benefits 

Human resources provides tools for the setup and maintenance of the benefits, deductions, and worker compensation plans that an organization offers or processes for its workers.

When you create benefits, keep in mind the following data and configurations that are used in Dayforce.

##### Benefit plans

- Plan (required)
- Type (required)
- Payroll impact (required)
- Recover arrears
- Deduction method
- Deduction priority
- Limit period
- Limit amount

##### Benefits

- Plan (required)
- Type (required)
- Option (required)
- Benefit ID (required)
- Frequency
- Basis
- Amount or rate
- Earning code

##### Supported frequencies 

- Weekly
- Bi-weekly
- Semi-monthly
- Monthly

##### Supported bases 

- Fixed amount
- Percent of earnings
- Productive hours

Dayforce creates the following deductions, based on the payroll impact that is defined on the benefit plan.

| Selection in Talent        | Result in Dayforce                            |
|----------------------------|-----------------------------------------------|
| None                       | No deduction is created.                      |
| Deduction only             | An employee deduction is created.             |
| Contribution only          | An employer deduction is created.             |
| Deduction and contribution | Employee and employer deductions are created. |

For more information about how to define and manage a benefits program, see the following topics:

- [Deliver an employee benefits program](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/deliver-employee-benefits-program)
- [Create a new benefit](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/create-new-benefit)
- [Define benefit eligibility rules and policies](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-benefit-eligibility-rules-policies)
- [Enroll and remove benefits from workers](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-remove-benefits-workers)

#### Compensation 

Compensation management is used to control the delivery of base pay and awards. An employee's fixed base pay and merit increases are controlled through fixed compensation plans. The payment of incentive pay, such as bonus payments, performance awards, stock options, and grants, and also one-time awards, are controlled through variable compensation plans.

Dayforce uses compensation information to calculate an employee's hourly or annual rate. Fixed compensation plans and pay rate conversions are required. Employees must be associated with a fixed compensation plan.

For more information about compensation plans, see the following topics:

- [Create fixed compensation plans](https://docs.microsoft.com/dynamics365/unified-operations/talent/create-fixed-compensation-plans)
- [Create variable compensation plans](https://docs.microsoft.com/dynamics365/unified-operations/talent/create-variable-compensation-plans)
- [Develop salary/compensation structure and plans](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/develop-salary-compensation-structure-plan)
- [Process compensation](https://docs.microsoft.com/dynamics365/unified-operations/talent/process-compensation)
- [Define compensation process and calculate results](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-compensation-process-calculate-results)
- [Enroll an employee in a fixed compensation plan](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-employee-fixed-compensation-plan)
- [Enroll an employee in a variable compensation plan](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/enroll-employee-variable-compensation-plan)

#### Jobs 

A job is a collection of the tasks and responsibilities that are required of a person who performs a job. For more information, see the following topics:

- [Setting up the components of a job](https://docs.microsoft.com/dynamics365/unified-operations/talent/create-job)
- [Define new jobs](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-new-jobs)

##### Positions

A position is an individual instance of a job. For example, the "Sales manager (East)" position is one of the positions that are associated with the "Sales manager" job. A position exists in a department. Only one worker can be associated with each position.

Keep the following data and configuration in mind when you set up positions:

- Position (required)
- Description (required)
- Job (required)
- Department (required)
- Position type (required)
- Full-time equivalent
- Annual regular hours (required)
- Paid by legal entity (required)
- Pay cycle (required)
- Default financial dimension – Cost center (required)
- Worker assignment – Worker, assignment start, assignment end, reason code

If multiple positions in the same department are associated with the same job, they are consolidated into a single position in Dayforce.

For more information, see the following topics:

- [Organize your workforce using departments, jobs, and positions](https://docs.microsoft.com/dynamics365/unified-operations/talent/departments-jobs-positions#positions)
- [Set up positions](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/set-up-positions)

#### Departments

A department is an operating unit that represents a category or functional area of an organization. A department is responsible for a specific area of the organization, such as sales, accounting, or human resources. You can use departments to report on functional areas. Departments might have profit and loss responsibility.

For more information, see the following topics:

- [Create a department and associate it with the department hierarchy](https://docs.microsoft.com/dynamics365/unified-operations/talent/create-department-add-department-hierarchy)
- [Define new departments](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/hr/tasks/define-new-departments)

#### Pay cycles and pay periods

A pay cycle determines how often payroll is run and the specific days when workers are paid. For example, a pay cycle might be monthly, and employees might be paid on the last day of the month. Alternatively, a pay cycle might be weekly, and employees might be paid on the Tuesday after the end of the pay period. Pay cycles are assigned to positions to control when workers in those positions are paid.

After you create pay cycles, you can generate pay periods for each cycle. Each pay period includes a default payment date that is based on information that you provide. However, you can modify the default payment date in a pay period to allow for exceptions, such as when the payment date falls on a holiday.

The following information is used in Dayforce:

- Pay cycle (required)
- Pay cycle frequency (required)
- Period start date (first pay period required)
- Default payment date (first pay period required)

This information is integrated with Dayforce as pay groups, and is separated by country or region for each pay cycle. At least one pay period must be generated before integration. Dayforce generates pay group calendars and payment dates, based on the start date of the first pay period and the default payment date that is set up in Talent.

#### Earning codes

Earning codes uniquely identify every type of earnings that workers receive. The codes have various parameters that are related to earnings, such as accounting rules, tax laws, reporting requirements, and gross-up capability.

The following information is used in Dayforce:

- Earning Code (required)
- Description
- Unit of measure
- Productive

### Worker data

Records for the various types of workers that you have are important to your human resources and payroll systems. The information that you enter can be used to track workers and personal information.

You can maintain the following information for workers:

- **Basic** – Maintain basic information about a worker, such as contact information, demographic information, identification information, family information, military service status, expatriate information, and personal and emergency contacts.
- **Employment** – Maintain information about a worker's employment, such as company or organization affiliation, position assignment, start and end dates, work eligibility, terms of employment, pension, vacation, and relocation information.
- **Leave and absence** – Maintain information about a worker's absences, such as working calendars, absence transactions, and absence setup.
- **Compensation and payroll** – Maintain information about a worker's compensation plans and payroll information, such as plan enrollment, awards, performance, commission, tax information, retirement, and salary deductions.

When you enter worker information, keep in mind the following data and configurations that are used in Dayforce.

#### General information

- Personnel number (required)
- First name (required)
- Last name (required)
- Middle name
- Seniority date
- Known as

#### Personal information

- Marital status (required)
- Birth date (required)
- Gender (required)
- Person with disabilities
- Nationality country region (only for Mexico)

#### Address information

- Primary (required)
- Country/region (required)
- Postal code (required)
- Street Number (required) (Only for Mexico)
- Building Complement (Only for Mexico)
- City (required)
- State (required)
- County (required)

#### Contact information 

- Primary (required)
- Contact number (required)
- Extension

#### Payroll information and earning codes

Employees may be assigned specific earnings at a given frequency of payment and have a preferred payment method. The following fields are used in Dayforce to help guarantee that those preferences and settings are used.

##### Earning codes

- Position (required)
- Earning Code (required)
- Frequency (required)
- Amount (required)

##### Payroll information

- Payment Method
- Economic Region (required)
- Employee Benefits ID
- National ID Number (required)
- Military Service Number
- Shift ID (required)
- Tax Number (required)
- Union ID (required)
- Work Day ID (required)
- Work Permit Number

> [!NOTE]
> For the payment method, Mexico supports **Cash**, **Check** (the company's physical check), and **Electronic Payment**. If np payment method is specified, **Check** is used by default.

#### Employment details

Employment detail history is used as key information to derive an employee's hire, termination, and rehire statuses in Dayforce. Dayforce supports only one active employment record at a time.

- Employment start date (required)
- Employment end date
- Start date
- Adjusted start date
- Termination date (required upon termination)
- Termination reason (required upon termination)

An employee's key dates are derived by using the following information.

| Talent                | Dayforce                                                                                             |
|-----------------------|------------------------------------------------------------------------------------------------------|
| Most recent hire date | Employment start of current non-terminated employment history record                                 |
| Termination date      | Termination date of current non-terminated employment history record                                 |
| Start date            | Adjusted start date, start date, or employment start of current non-active employment history record |
| Original hire date    | Employment start of earliest employment history record                                               |

#### Compensation

A fixed compensation plan must be associated with every employee's primary position throughout an employment period. This period starts on the date that the employee was hired (or the employment start date) and continues until termination.

- Effective Date (required)
- Expiration date
- Pay Rate (required)
- Pay Rate Conversions (required)
- Annual equivalent (required)
- Hourly equivalent (required)

If an hourly employee has multiple positions, the fixed compensation of the primary position is imported into Dayforce as the employee-level base rate/salary. For non-primary positions, the hourly rate is saved to the corresponding position in Dayforce.

If a salaried employee has multiple positions, the cumulative hour rate and annual salary across all active positions are derived and used as the employee-level base rate/salary.

#### Identification numbers

##### Social Security identifier 

Every employee must have one primary identifier. This identifier must be of **SSN** identification type. In Dayforce, it's automatically derived as the employee's Social Security identifier that is required for hire.

- Primary (required)
- Identification Type = "SSN"
- Issued Date
- Expiration Date

Employees can declare multiple identification numbers of the **SSN** identification type. However, only the record that is marked as **Primary** is integrated into Dayforce, regardless of whether the number is active or expired.

#### Bank accounts and disbursements

Valid bank account information must be entered for any employee who chooses to be paid via bank account transfers.

| Talent                         | Dayforce                                                                                                    |
|--------------------------------|-------------------------------------------------------------------------------------------------------------|
| Bank account number (required) |                                                                                                             |
| SWIFT code (required)          | **Bank ID** field used when processing payroll in Mexico.                                                             |
| Branch number (required)       |                                                                                                             |
| Bank account type (required)   | **Account type** field used when processing payroll in Mexico. Supported values include **Checking** and **Payroll**. |

> [!NOTE]
> Employees who choose to be paid via bank account transfers must provide a link to a remainder account that is under a legal entity that has its primary address in Mexico and associated with a valid bank account from a Mexican bank. All other non-remainder accounts are ignored.

#### Address information

Every employee must have one primary location. In Dayforce, this location is used to determine the employee's primary residence for tax purposes.

- Primary (required)
- Country/region (required)
- Zip/postal code (required)
- Street (required)
- Street Number (required)
- Building Complement
- City (required)
- State (required)
- County (required)

## Configure your data to generate payroll in United States and Canada

If you're generating pay for employees in the United States and Canada, the following elements must be configured:

- Departments are required on positions.
- Cost centers must be set as financial dimensions and must be the first element in the default financial dimension string.

> [!NOTE] 
> You can configure Talent to require that Positions specify a Department. To do this, go to **Human Resources Shared Positions > Positions > Require departments on positions**. We recommend that this setting be enforced for the integration.

### Job types

Job types are used to group similar jobs into categories. Job types are required in order to process payroll in the United States and Canada. Examples of job types include full-time and part-time, or salary and hourly pay. Job types are mapped to Dayforce as pay types that indicate whether an employee is hourly or salaried.

The following job types and descriptions are required.

| Job type   | Description |
|------------|-------------|
| Hourly     | Hourly      |
| Salaried   | Salaried    |

### Position types 

You use position types to describe whether the position is full-time, part-time, or something else. Position types are mapped to Dayforce as pay classes that indicate whether an employee is full-time or part-time.

The following position types and descriptions are required.

| Position type   | Description        |
|-----------------|--------------------|
| Full-time       | Full time employee |
| Part-time       | Part time employee |

### Reason codes

Reason codes provide information about the status of an employee. Reason codes are mapped to Dayforce as status reasons that indicate the reason for changes to an employee's position or employment status.

The following reason codes and descriptions are required.

| Reason code    | Description      | Applicable scenarios |
|----------------|------------------|----------------------|
| RESIGNATION    | Resignation      | Terminate worker     |
| TERMINATION    | Termination      | Terminate worker     |
| RETIREMENT     | Retirement       | Terminate worker     |
| OTHER          | Other Reasons    | Terminate worker     |
| DEATH          | Death            | Terminate worker     |
| LEAVEOFABSENCE | Leave of Absence | Terminate worker     |
| CONTRACTEND    | End of Contract  | Terminate worker     |
| SALARYCHANGE   | Change of Salary | Compensation         |

### Marital status

Marital status values are mapped to Dayforce and translated, as appropriate, to the accepted values upon integration.

The following table shows how marital status values are mapped to Dayforce.

| Talent                 | Dayforce             |
|------------------------|----------------------|
| Married                | Married              |
| Single                 | Single               |
| Widowed                | Widowed              |
| Divorced               | Divorced             |
| Registered Partnership | Domestic Partnership |
| None                   | None                 |
| Cohabiting             | Cohabiting           |

### Gender

Gender designations are mapped to Dayforce and translated, as appropriate, to the accepted values upon integration.

The following table shows how gender designations are mapped to Dayforce.

| Talent       | Dayforce        |
|--------------|-----------------|
| Male         | Male            |
| Female       | Female          |
| Non-specific | *Not supported* |

### Earning codes

Earning codes uniquely identify every type of earnings that workers receive. The codes cover several parameters that are related to earnings, such as accounting rules, tax laws, reporting requirements, and gross-up capability. If an unsupported frequency is used, the **Every Pay** frequency is used by default for the calculation.

#### Supported frequencies

- All
- EVERYPAY
- EACHPAYPERIOD
- EVRYOTHRPAYODD
- EVRYOTHRPAYEVN
- 1OFMTH
- LASTOFMTH
- 2OFMTH
- 3OFMTH
- 4OFMTH
- 5OFMTH
- 1N2OFMTH
- 3N4OFMTH
- 1N3OFMTH
- 1N4OFMTH
- 2N3OFMTH
- 2N4OFMTH
- 1N2N3OFMTH
- 1N2N4OFMTH
- 1N3N4OFMTH
- 2N3N4OFMTH
- 1N2N3N4OFMTH - 1N2N3N4OFMTH
- 2N3N4N5OFMth - 2N3N4N5OFMth
- 1OFQTR - 1OFQTR
- LASTOFQTR – LASTOFQTR
- LASTMTHOFQTR – LASTMTHOFQTR
- 1OFYEAR - 1OFYEAR
- LASTOFYEAR – LASTOFYEAR
- NOVNDECOFYEAR - NOVNDECOFYEAR

### Addresses

The identification of specific country or region, state, and county (municipality) codes requires specific formats that Dayforce and in-country/in-region providers can recognize. Although the format for cities is flexible, every city must be associated with a state.

| Talent          | Dayforce              |
|-----------------|-----------------------|
| Country/Region  | Country Code          |
| Zip/Postal Code | Postal Code           |
| State           | State Code            |
| City            | City                  |
| County          | County (Municipality) |
| Street          | Address Line 1        |

### Tax regions

Tax regions are used to determine the appropriate tax that should be applied during payroll generation. Tax regions are mapped to Dayforce as location addresses. The default tax region must be associated with the worker's active position. 

- Tax region (required)
- Country/Region (required)
- State (required)
- County 
- City (required)

## Configure your data to generate payroll in Mexico

If you're generating pay for employees in Mexico, the following elements must be configured:

- Departments are required on positions.
- Cost centers must be set as financial dimensions and must be the first element in the Default Financial Dimension string.

### Job types

Job types are used to group similar jobs into categories. Job types are required in order to process payroll in Mexico. Examples of job types include full-time and part-time, or salary and hourly pay. Job types are mapped to Dayforce as pay types that indicate whether an employee is hourly or salaried.

The following job types and descriptions are required.

| Job type   | Description |
|------------|-------------|
| Hourly     | MX Hourly   |
| Salaried   | MX Salaried |

### Position types 

You use position types to describe whether the position is full-time, part-time, or something else. Position types are mapped to Dayforce as pay classes that indicate whether an employee is full-time or part-time.

The following position types and descriptions are required.

| Position type   | Description        |
|-----------------|--------------------|
| Full-time       | Full time employee |
| Part-time       | Part time employee |

### Reason codes

Reason codes provide information about the status of an employee. Reason codes are mapped to Dayforce as status reasons that indicate the reason for changes to an employee's position or employment status.

The following reason codes and descriptions are required.

| Reason code            | Description                    | Applicable scenarios |
|------------------------|--------------------------------|----------------------|
| DEPARTUREBEFOREPAYMENT | Departure before first payroll | Terminate worker     |
| RESIGNATION            | Resignation                    | Terminate worker     |
| PENSION                | Pension                        | Terminate worker     |
| TERMINATION            | Termination                    | Terminate worker     |
| RETIREMENT             | Retirement                     | Terminate worker     |
| ABSENTEE               | Absentee                       | Terminate worker     |
| OTHER                  | Other Reasons                  | Terminate worker     |
| CLOSURE                | Business Closure               | Terminate worker     |
| DEATH                  | Death                          | Terminate worker     |
| LEAVEOFABSENCE         | Leave of Absence               | Terminate worker     |
| CONTRACTEND            | End of Contract                | Terminate worker     |
| SALARYCHANGE           | Change of Salary               | Compensation         |

### Terms of employment

Terms of employment are used to create categories of employment terms. The terms are mapped to Dayforce as employment indicator values.

The following terms of employment and descriptions are required.

| Terms of employment   | Description |
|-----------------------|-------------|
| Regular               | Regular     |
| Direct                | Direct      |
| Internship            | Internship  |
| Permanent             | Permanent   |

### Marital status

Marital status values are mapped to Dayforce and translated, as appropriate, to the accepted values upon integration.

The following table shows how marital status values are mapped to Dayforce.

| Talent                 | Dayforce                  |
|------------------------|---------------------------|
| Married                | Married                   |
| Single                 | Single                    |
| Widowed                | Widowed                   |
| Divorced               | Divorced                  |
| Registered Partnership | Domestic Partnership      |
| None                   | *Not supported by Mexico* |
| Cohabiting             | *Not supported by Mexico* |

### Gender

Gender designations are mapped to Dayforce and translated, as appropriate, to the accepted values upon integration.

The following table shows how gender designations are mapped to Dayforce.

| Talent       | Dayforce                  |
|--------------|---------------------------|
| Male         | Male                      |
| Female       | Female                    |
| Non-specific | *Not supported by Mexico* |

### Payment method

Payment methods give the employee and the company a way to describe how employees will be paid. Payment methods are mapped to Dayforce and translated, as appropriate, to the accepted values upon integration.

The following table shows how payment methods are mapped to Dayforce.

| Talent             | Dayforce                  |
|--------------------|---------------------------|
| Cash               | Cash                      |
| Electronic Payment | Transfer                  |
| Check              | Cheque                    |
| Bank Draft         | *Not supported by Mexico* |
| Other              | *Not supported by Mexico* |

### Bank account type

Bank account types are used for electronic payments to employees. Bank account types are mapped to Dayforce as transfer account information. The bank account types are translated, as appropriate, to the accepted values upon integration.

| Talent            | Dayforce                  |
|-------------------|---------------------------|
| Checking Account  | CheckingAccount           |
| Payroll Account   | PayrollAccount            |
| Savings Account   | *Not supported by Mexico* |
| BankGirot account | *Not supported by Mexico* |
| PlusGirot account | *Not supported by Mexico* |

### Earning codes

Earning codes uniquely identify every type of earnings that workers receive. The codes cover several parameters that are related to earnings, such as accounting rules, tax laws, reporting requirements, and gross-up capability. If an unsupported frequency is used, the **Every Pay** frequency is used by default for the calculation.

#### Supported frequencies

- All
- EVERYPAY
- EACHPAYPERIOD
- EVRYOTHRPAYODD
- EVRYOTHRPAYEVN
- 1OFMTH
- LASTOFMTH
- 2OFMTH
- 3OFMTH
- 4OFMTH
- 5OFMTH
- 1N2OFMTH
- 3N4OFMTH
- 1N3OFMTH
- 1N4OFMTH
- 2N3OFMTH
- 2N4OFMTH
- 1N2N3OFMTH
- 1N2N4OFMTH
- 1N3N4OFMTH
- 2N3N4OFMTH
- 1N2N3N4OFMTH - 1N2N3N4OFMTH
- 2N3N4N5OFMth - 2N3N4N5OFMth
- 1OFQTR - 1OFQTR
- LASTOFQTR – LASTOFQTR
- LASTMTHOFQTR – LASTMTHOFQTR
- 1OFYEAR - 1OFYEAR
- LASTOFYEAR – LASTOFYEAR
- NOVNDECOFYEAR - NOVNDECOFYEAR

### Addresses

The identification of specific country or region, state, and county (municipality) codes requires specific formats that Dayforce and in-country/in-region providers can recognize. Although the format for cities is flexible, every city must be associated with a state.

| Talent              | Dayforce              |
|---------------------|-----------------------|
| Country/Region      | Country Code          |
| Zip/Postal Code     | Postal Code           |
| State               | State Code            |
| City                | City                  |
| County              | County (Municipality) |
| Street              | Address Line 1        |
| Street Number       | Address Line 2        |
| Building Complement | Address Line 5        |

### Passport number

Employees can declare passport information. This information is of the **Passport** identification type and is integrated into Dayforce as part of an employee's Mexico-specific information.

- Identification Type = "Passport"
- Issued Date
- Expiration Date

Employees can declare multiple identification numbers of the **Passport** identification type. However, only the current active passport entry is integrated into Dayforce. If all passport entries are expired, the passport that was most recently issued is integrated into Dayforce.
