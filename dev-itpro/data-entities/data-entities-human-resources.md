---
# required metadata

title: Data entities - Human resources
description: This article provides a list of the data entities that are available for the Human resources functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 26 - 26
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96373
ms.assetid: be9e5713-994e-43a8-8dcc-16c6f25ee927
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Human resources

This article provides a list of the data entities that are available for the Human resources functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**05.1.001 HR - Foundation setup**

1

Language codes

Foundation setup

Setup

None

The list of language codes for Human resources

2

Accommodation type

Foundation setup

Setup

None

The setup for specific types of workplace accommodations that you provide to workers and applicants

3

Ethnic origins

Foundation setup

Setup

None

Ethnic origins values

4

Issuing agency

Foundation setup

Setup

None

Address and contact information about government or other entities that are authorized to issue Form I-9 employment eligibility verification documents

5

Identification type

Foundation setup

Setup

None

The list of identification types that you can select from to specify identifying information about a worker

6

I-9 document type

Foundation setup

Setup

Identification type, Issuing agencies

A list of the document types that you can use when you enter Form I-9 document information for workers. These types of documents are verification documents that workers provide to prove their work eligibility status.

7

Areas of responsibility

Foundation setup

Setup

None

Defines the general areas of responsibility within a company. Areas of responsibility are the work roles, processes, products, and actions a worker is responsible for in a job.

8

Screening type

Foundation setup

Setup

None

Set up one-time screenings or screenings that occur regularly.

9

Worker tasks

Foundation setup

Setup

None

Maintain the list of worker tasks that you can assign to workers for worker assignments.

10

Veteran status

Foundation setup

Setup

None

Veteran status values that can be selected for a worker or applicant

11

Injury and illness body parts

Foundation setup

Setup

None

The list of body parts that you can select from on the **Injury or illness incidents** page

12

Titles

Foundation setup

Setup

None

Set up and maintain contact person titles.

13

Compensation fixed action table

Foundation setup

Setup

None

Set up fixed compensation actions.

14

Injury and illness cost types

Foundation setup

Setup

None

The list of cost types that you can select from on the **Injury or illness incidents** page

15

Injury and illness outcome types

Foundation setup

Setup

None

Maintain the list of outcome types that you can select from on the **Injury or illness incidents** page.

16

Compensation job function

Foundation setup

Setup

None

17

Injury and illness severity levels

Foundation setup

Setup

None

The list of severity levels that you can select from on the **Injury or illness incidents** page. For example, you can use numbers to indicate severity, where 1 indicates the most severe injury or illness, such as death, and 10 indicates the least severe injury or illness, such as a minor cut.

18

Injury and illness treatment types

Foundation setup

Setup

None

Maintain the list of treatment types that you can select from on the **Injury or illness incidents** page. For example, you can enter **Ice pack** as a treatment type and then enter **Ice pack applied to injury** as the description.

19

Injury and illness types

Foundation setup

Setup

None

Maintain the list of injury or illness types that you can select from on the **Injury or illness incidents** page.

20

Reason codes

Foundation setup

Setup

None

Codes that users can select to record the reason for a change or transaction

21

Reporting agencies

Foundation setup

Setup

None

Maintain the list of reporting agencies that you can select from on the **Injury or illness incidents** page. For example, you can enter **OSHA** as a reporting agency and then enter **Occupational Safety and Health Administration** as the description.

22

Job tasks

Foundation setup

Setup

None

Specify tasks for jobs.

23

Compensation regions

Foundation setup

Setup

None

Set up compensation regions, which you use to specify the region of a position in the **Compensation region** field for the position.

24

Media types

Foundation setup

Setup

None

The types of media that you use to recruit new workers

25

Media

Foundation setup

Setup

Media type

Set up a list of advertising media that you use to recruit new workers.

26

Regulatory establishments

Foundation setup

Setup

None

The list of regulatory establishments that are used to submit required reports

27

Regulatory establishment details

Foundation setup

Setup

Regulatory establishments

Details for regulatory establishments

28

Levels

Foundation setup

Setup

None

The discrete levels for the three types of compensation plan

29

Terms of employment

Foundation setup

Setup

None

Categories of employment terms

30

Labor unions

Foundation setup

Setup

None

Set up labor unions that workers might be associated with.

31

Labor union agreement

Foundation setup

Setup

Labor unions

Establish relationships between positions and unions.

32

Compensation survey companies

Foundation setup

Setup

None

The list of survey companies that provide market pricing information to your company. You can use market pricing information to determine compensation for specific jobs.

33

Position hierarchy types

Foundation setup

Setup

None

Set up a matrix hierarchy or other custom hierarchies that your organization might use. Use this data entity only if the **Personnel actions** configuration key is selected.

34

Personnel action types

Foundation setup

Setup

Compensation fixed action table

Names for the personnel action type and a brief description of the action

35

Rating models

Foundation setup

Setup

None

Contain graduated scales that employees and managers can use to rate items, such as employee skills. Rating models help guarantee that that the same scale is used by everyone who rates an item.

36

Rating level

Foundation setup

Setup

Rating models

Rating levels on the rating models that are created. Factors can be a number 0–9, and each level must have a unique factor. Levels that have higher factor values carry more weight in a rating model.

37

Loan types

Foundation setup

Setup

None

Set up loan types that are used to categorize loaned items.

38

Position type

Foundation setup

Setup

None

Categories that you can assign positions to that are similar in function or purpose

39

Compensation job type

Foundation setup

Setup

None

The various compensation job types

**05.1.002 HR - Competencies**

40

Certificate type

Competencies

Setup

None

Certificates of achievement

41

Education Degree

Competencies

Setup

None

The educational degrees that workers in your organization or company might have

42

Institution

Competencies

Setup

None

A list of learning institutions, so that you can specify where workers received their education or attended courses

43

Test

Competencies

Setup

None

Create tests, set up the minimum requirements for test scores, and set up recurrence details for tests.

44

Skill types

Competencies

Setup

None

Types of skills

45

Skills

Competencies

Setup

None

The skills that a worker, applicant, or contact person might have

46

Education disciplines

Competencies

Setup

None

The levels of education that an employee must or should have acquired to be considered qualified for a position

47

Education discipline categories

Competencies

Setup

Education disciplines

The education discipline categories that are used to categorize education disciplines

48

Education and discipline category associations

Competencies

Setup

Education discipline categories

Bridge information between the association of education discipline category and education discipline.

49

Skill-mapping - main

Competencies

Setup

Rating models, Skill type

Can be used in searches to find workers, contacts, and applicants who have a specific set of competencies.

**05.1.003 HR - Jobs**

50

Jobs

Jobs

Setup

Job function, Job type, Titles, Survey company

Jobs that are available in the company

51

Job detail

Jobs

Setup

None

A description of the job

52

Job - areas of responsibility

Jobs

Setup

Areas of responsibility, Jobs

Define general areas of responsibility, such as products or processes, for jobs.

53

Job - certificates

Jobs

Setup

Certificate types, Jobs

The certification requirements for jobs

54

Job - education

Jobs

Setup

None

The specific education requirements for jobs

55

Job - screening

Jobs

Setup

Test, Jobs

The screening requirements for jobs

56

Job - skills

Jobs

Setup

Skills, Jobs

The skill requirements for jobs that use a job template

57

Job - work tasks

Jobs

Setup

Job tasks, Jobs

The specific task requirements for jobs

58

Job - ADA requirements

Jobs

Setup

ADA setup

The specific Americans with Disabilities Act (ADA) requirements for jobs

59

Active jobs **Note:** This entity will be renamed Job-tests during Application Update 1.

Jobs

Setup

Test, Jobs

Active jobs in the company

60

Job templates

Jobs

Setup

Job function, Job type, Titles

Used as the basis for jobs that you create, and that are similar in function or purpose.

61

Job template - areas of responsibility

Jobs

Setup

Job templates, Areas of responsibility

The general areas of responsibility, such as products or processes, for jobs that use a job template

62

Job template - certificates

Jobs

Setup

Job templates, Certificate types

The certification requirements for jobs that use a job template

63

Job template - education

Jobs

Setup

Job templates, Education disciplines

The specific education requirements for jobs that use a job template

64

Job template - screening

Jobs

Setup

Job templates, Screening type

The screening requirements for jobs that use a job template

65

Job template - skills

Jobs

Setup

Job templates, Skills

The skill requirements for jobs that use a job template

66

Job template - work tasks

Jobs

Setup

Job templates, Job tasks

The specific task requirements for jobs that use a job template

67

Job template test

Jobs

Setup

Job templates, Test

The test requirements for jobs that use a job template

**05.1.004 HR - Pay**

If you’re using demo data to import the Pay period data entity, you will encounter errors on most records because inclusive dates are incorrectly defined. Import of child data entities for Pay period will also fail. Demo data will be fixed during Application Update 1 to address this issue.

68

Pay cycle

Pay

Setup

None

The frequency of pay periods and the pay dates for positions

69

Pay period

Pay

Setup

None

The number of pay periods per pay cycle

70

Pay types

Pay

Setup

None

Pay agreements that are used to calculate various kinds of pay for workers, based on their time and attendance registrations

**05.1.005 HR - Employees**

Before you import employees and contractors, make sure that the Organizational calendar data entity **for all legal entities** was imported. Otherwise, the import will fail on some of the employee records that don’t have an associated calendar per company. There is an existing issue where not all employee records can be exported by using data management. This issue occurs only when no worker calendar is associated with an employee. Therefore, before import, make sure that a worker calendar is associated with every employee. This issue will be fixed during Application Update 1. The steps under 05.1.006 and 05.1.007 will bring in current employees and contractors in the system, together with all associated child records. Your organization should decide how you want to bring in data, and you may use only one import method. For option 1, you use the Worker and Employment data entities. For option 2, you use Employee and Contractor data entities.

-   **Option 1:** If you’re bringing in past and current workers, which include employees and contractors, you can use Worker and then import Employment data entities to bring in data. However, if you use this option, be aware that you won’t be able to bring in data that is associated with workers, such as Employment employee, Employment contractor, Employment details, and Working calendars.
-   **Option 2:** This option will bring in current employees and contractors in the system. The import will bring in data that is associated with workers, such as Employment, Employment details, and Working calendars. However, if you use this option, be aware that you won’t be able to bring in past employees and contractors.

Before you import the Employee and Contractor data entities, make sure that the Calendar and Working times data entities are imported into all available legal entities. When you do data import for the Employee data entity, use the **Batch** option. Do **not** use the **Import Now** option. To use the **Batch** option, click **Import options** &gt; **Import in batch** while you're doing data import in Data management. **Import in batch** is a better option if you have to manage RAM consumption.

71

Employee

Employees

Master

Worker main setups

Employee records

**05.1.006 HR - Contractor**

72

Contractor

Contractors

Master

None

Contractor records

**05.1.007 HR - Positions**

Currently, the data entities for Position details, Position durations, and Position union agreement won’t bring in historical values. This issue will be addressed during Application Update 1.

73

Positions

Position

Setup

Job, Department, Title, Position type, Employee/Worker, Position hierarchy types, Pay cycle, work cycle, benefits, earning code, schedule, Union agreement, Labor union

Positions that are available in the company

74

Position details

Position

Setup

None

Details for the positions

75

Position durations

Position

Setup

None

The length of time that the position will be in your company. Many workers can be assigned to a position throughout the duration of a position. However, only one worker can be assigned to the position at a time.

76

Position union agreement

Position

Setup

None

The union agreement that governs the position

77

Position default dimensions **Note:** This data entity isn’t included in the data package that is available on Microsoft Dynamics Lifecycle Services (LCS). The parent entity will be made available during Application Update 1.

Position

Setup

None

Account structures and advanced rule structures that use the financial dimensions

78

Position hierarchies

Position

Setup

Position, Position hierarchy types

Types for each organizational hierarchy that your organization or company uses

**05.1.008 HR - Worker details**

Currently, the Worker title data entities for Position durations and Position union agreement won’t bring in historical values. This issue will be addressed during Application Update 1.

79

Person details

Worker details

Setup

None

Details for the worker

80

Worker bank accounts

Worker details

Setup

None

Worker bank account information

81

Bank account disbursements

Worker details

Setup

Bank account

Configure how funds are disbursed to worker bank accounts.

**05.1.009 HR - Compensation**

Some compensation fix plan records might fail during import, because a data entity is missing for Reference point line. This data entity will be made available during Application Update 1.

82

Compensation pay frequency

Compensation

Setup

None

Define the frequency of employee payment. Pay frequencies are also used to set up conversion factors to convert compensation from monthly, weekly, biweekly and hourly pay frequencies to an annual pay frequency.

83

Compensation performance plan

Compensation

Setup

None

Used to associate performance with an allocation matrix, so that you can use the plan in a pay-for-performance strategy.

84

Compensation performance rating

Compensation

Setup

None

Used in compensation plans to determine the amount of a merit award or performance award.

85

Compensation performance allocation

Compensation

Setup

None

Joins together the performance plan and performance rating, so that you can create a matrix that specifies graded merit increases for each performance rating.

86

Compensation variable type

Compensation

Setup

None

Variable compensation types, such as stock awards or cash award bonuses, are set up in variable compensation plans.

87

Compensation vesting rules

Compensation

Setup

None

List the various vesting rules for variable long-term awards, such as stocks.

88

Reference point setups

Compensation

Setup

None

Includes a set of reference points that represent ranges in a matrix, and each range can be associated with a pay rate. A reference point setup is created for a specific fixed compensation plan type.

89

Compensation grids

Compensation

Setup

None

Companies that use external compensation systems can use grids to generate basic compensation plans and set up pay range guidelines for those plans.

90

Compensation fixed plan

Compensation

Setup

None

Create fixed compensation plans of the **Grade**, **Band**, and **Step** types.

91

Compensation plan eligibility rules

Compensation

Setup

None

Set up eligibility rules for compensation plans. Eligibility rules make it easier to select an appropriate compensation plan for an employee. You can use eligibility rules to identify employees in specific jobs, job functions, job types, departments, labor unions, or compensation regions that are covered by a specific compensation plan.

92

Compensation merit increase target

Compensation

Setup

None

The general fixed increase budget for departments

93

Compensation process table

Compensation

Setup

None

Set up work streams for recommendations.

94

Process results

Compensation

Setup

None

Update the compensation information, or transactions, for employees’ compensation records.

**05.1.010 HR - Absence**

95

Absence groups

Absence

Setup

None

Groups of absence codes

96

Absence codes

Absence

Setup

None

The list of absence codes that indicate the reason for an absence

97

Absence reason

Absence

Setup

Reason codes

The list of reason for absences

**05.1.011 HR - Benefits**

98

Calculation frequency

Benefits

Setup

None

Determine when you process various payroll elements.

99

Calculation frequency pay period

Benefits

Setup

Pay cycle, Pay period

Control when benefits and certain earnings are processed.

100

Policy source document rule type

Benefits

Setup

None

Policy rule types for the audit, benefit eligibility, premium earning, and vendor invoice policies that are defined for your organization

101

Benefit type

Benefits

Setup

None

A collection of plans for a specific benefit, such as medical or parking

102

Benefit option

Benefits

Setup

None

The coverage level, such as employee-only or employee and spouse

103

Benefit Plan

Benefits

Setup

None

A specific benefit that is contracted from a provider

104

Benefit

Benefits

Setup

None

Set up current and future benefits that workers and their dependents and beneficiaries can receive, and also specify how to maintain payroll information for benefits.

105

Benefit eligibility overrides

Benefits

Setup

None

Information that is used to assign eligibility overrides for workers who should be allowed to enroll in benefits, but who don’t meet the criteria in the eligibility rules

**05.1.012 HR - Performance**

106

Discussion types

Performance

Setup

None

Use to categorize discussions before you can create discussions for workers.

107

Goal headings

Performance

Setup

None

Use to categorize goals.

108

Goal types

Performance

Setup

None

Organize goals into manageable categories.

109

Goal type templates

Performance

Setup

None

Templates for goal types

110

Goals

Performance

Setup

None

Categories to organize worker goals

111

Discussions

Performance

Setup

None

Types of discussions, so that you can group similar discussions

**05.1.013 HR - Courses**

112

Classroom groups

Courses

Setup

None

Groups of course locations

113

Course groups

Courses

Setup

None

Organize course types into groups.

114

Course types

Courses

Setup

None

The course types that will be offered by the company or taken by workers

115

Course type - certificates

Courses

Setup

None

A list of the certificates that participants will earn when they complete a course of the course type

116

Course type - education

Courses

Setup

None

A list of the education disciplines that participants will learn when they complete a course of the course type

117

Course type - skills

Courses

Setup

None

The list of skills that participants will gain when they complete a course of the course type

118

Course type default dimensions

Courses

Setup

None

Information about financial dimensions, such as the default dimensions, and where the dimensions are used in account structures and advanced rule structures

119

Course locations

Courses

Setup

None

The list of locations where courses are held

120

Classrooms

Courses

Setup

None

Record the rooms that you use at course locations.

121

Course instructors

Courses

Setup

None

List course instructors, and assign them to specific course locations.

122

Courses

Courses

Setup

None

Information about the courses that you offer to your workers

**05.1.014 HR - Recruitment**

123

Application bookmarks

Recruitment

Setup

None

Information that you make available for use in the templates for application email messages and application documents

124

Application e-mail templates

Recruitment

Setup

None

Information that can include bookmarks, so that each email that uses the template can include specific information about the applicant and the job that the applicant applied for

125

Recruitment projects

Recruitment

Setup

None

Set up information, such as the job that you’re recruiting for, the name of the recruiter, the status of the project, and the department that the job will be in.

126

Recruitment media

Recruitment

Setup

None

List the media that are used for a recruitment project.

127

Applicants

Recruitment

Master

None

Information about people who seek employment in your company or organization, or people that you’ve contacted to fill a position

128

Application basket

Recruitment

Setup

None

Applications that are received through Employee-self service

129

Applicant position of trust competency

Recruitment

Setup

None

Positions of trust that the selected applicant has held or currently holds

130

Applications

Recruitment

Master

None

Employment application information

**05.1.015 HR - Employee related associations**

Some records for the Course participants data entity might fail, because a data entity is missing for Questionnaire records. Some records for the Employee fixed compensation data entity might fail, because a data entity is missing for Compensation Reference point line.

131

Position worker assignments

Employee related association

Setup

None

Position assignments for workers. When you create a position assignment for a worker, you indicate that the worker will fill a specific position for a period of time.

132

Worker enrolled benefit

Employee related association

Setup

None

The list of enrolled workers and enrollment dates for a specific benefit

133

Injury or illness incidents

Employee related association

Setup

None

Track injury or illness of a worker. The data includes general case information, such as when the incident occurred, and when and who reported it.

134

Skill mapping

Employee related association

Setup

None

The results of a skill mapping

135

Course participants

Employee related association

Setup

None

The list of participants in courses that are offered

136

Loan items

Employee related association

Setup

Employee, Loan type

Records that help you keep track of the physical items that your company lends to workers

137

Loan

Employee related association

Setup

None

The list of company equipment that workers have borrowed or returned

138

Certificate competency

Employee related association

Setup

None

The list of certificates that the selected person has earned

139

Course competency

Employee related association

Setup

None

The list of courses that a person has completed

140

Education competency

Employee related association

Setup

None

The list of education that a person has

141

Worker position of trust competency

Employee related association

Setup

None

Positions of trust that the selected person has held or currently holds

142

Person exam

Employee related association

Setup

None

143

Professional experience competency

Employee related association

Setup

None

The list of professional experience for the selected person

144

Worker project experience competency

Employee related association

Setup

None

The list of project experience for a person

145

Skill competency

Employee related association

Setup

None

The list of skills for a person

146

Employee variable compensation enrollment overrides

Employee related association

Setup

None

The employee who is enrolled in the variable compensation plan

147

Employee fixed compensation

Employee related association

Setup

None

The base pay of an employee

**05.1.016 HR - Human resources parameters**

When you import the Human resources parameters data entity, you might receive the following error message: “Document type Note cannot be used for application email templates.” The message likely indicates that the **Note** document type had a group of **file** and a class of **Attach file** on your export file. We allow document types only for the erroring field of class **simple note** and **group note**. If you fix the document types on the export file before import, the import into the company should work.

148

Human resources parameters

Parameters

Setup

None

The default setup of the **Human resources** module for the current legal entity

**05.1.017 HR - Shared human resources parameters**

149

Shared human resources parameters

Parameters

Setup

Identification types, Issuing agencies

Set up Human resources parameters that are shared across all legal entities.

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

