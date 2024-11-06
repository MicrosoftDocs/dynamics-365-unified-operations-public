---
title: Personal information requests for Estonia
description: Learn about personal information requests for Estonia, including an outline on various reports that are available and additional resources.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Estonia
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Personal information requests for Estonia

[!include [banner](../../includes/banner.md)]

Estonia legally allows people to ask companies for reports that identify the personal information that the companies track. The reports also indicate who has viewed, created, updated, and deleted this information.

All companies must gather data about employees, customers, and vendors, and also other personal data. When the data is gathered about persons, most of the information is considered personal data and must be handled correctly according to the Estonian legislation. All information that comes from logging changes or inquiries on tables that are related to personal data is presented on three defined reports: **Personal chart**, **Access log**, and **Permission changes**.

Following tables are in scope of logging changes or inquiries that are related to personal data:

| Table	| Label |
|-------|-------|
| DirPerson |	People |
| ContactPerson |	Contacts |
| HcmEmployment |	Employment | 
| HcmEmploymentContractor |	Employment contractor |
| HcmEmploymentDetail |	Employment detail |
| HcmEmploymentEmployee |	Employeet detail |
| HcmEmploymentTerm |	Employment term |
| HcmEmploymentVacation |	Employment vacation |
| HcmPersonAccommodation |	Accommodations |
| HcmPersonDetails |	Person details |
| HcmPersonEducation |	Education competency |
| HcmPersonIdentificationNumber |	Identification |
| HcmPersonPrivateDetails |	Person private details |
| HcmPersonPrivateCitizenshipDetails |	Private citizenship details |
| HcmPersonProfessionalExperience |	Professional experience competency |
| HcmWorkerBankAccount |	Worker bank accounts |
| PayrollEarningStatement |	Earnings statements |
| HcmWorkerEnrolledBenefit |	Worker enrolled benefit |

To enable logging changes or inquiries that are related to personal data in the mentioned tables, go to **Organization administration** > **Organizations** > **Legal entities**, for your legal entity with primary address in Estonia expand the **Database read log** FastTab and mark the **Enable** checkbox.

## Reports that are available

- **Access log** – This report shows the fields and tables that are related to an employee's personal information, and that have been accessed within a specified period. To generate the report, go to **Human resources** \> **Workers** \> **Inquiries and reports** \> **Access log**.
- **Permission changes log** – This report shows changes to an employee's permissions to access information, the employee's security rights, or the employee's user role. You can view the permission changes either as an overall list for the employee, or as a breakdown of tables and fields. To generate and print the report, go to **Human resources** \> **Workers** \> **Inquiries and reports** \> **Permission changes log**.
- **Personal chart** – This report shows a selected employee's personal information. To generate the report, go to **Human resources** \> **Workers** \> **Inquiries and reports** \> **Personal chart**.

## Additional resources

- [Resources for responding to a personal data request](../../../fin-ops-core/dev-itpro/privacy/privacy-home-page.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
