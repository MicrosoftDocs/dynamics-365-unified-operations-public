---
# required metadata

title: Gender base enum extensibility
description: This article provides an overview of extensibility of the Gender base enumeration (enum).
author: twheeloc
ms.date: 05/23/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---
# Gender base enum extensibility

The **Gender** enumeration (enum) is now extensible. This article describes the changes that you must make in the code base if you plan to extend the **Gender** enum.

## Gender vs. HcmPersonGender

There are two enums for gender values:

- **Gender** (Application Platform)
- **HcmPersonGender** (PersonnelManagement)

The **Gender** enum is used throughout Microsoft Dynamics 365 Finance, whereas **HcmPersonGender** is specific to human capital management (HCM) functionality. If you're using HCM functionality, and you make any changes to the **Gender** enum, you should consider making the same changes to the **HcmPersonGender**. For example, if you add **Transgender** to the **Gender** enum, add **Transgender** to the **HcmPersonGender** enum too.

## HcmPersonGenderTranformUtil (Class)

A new **HcmPersonGenderTranformUtil** class was created to allow for translation between the two base enumerators. In this class, there are two methods: **convertGenderToHcmPersonGender** and **convertHcmPersonGenderToGender**. You should create an extension by using the **Chain of Command** class or **event handlers**, and extend both methods to map new values that are added to either base enum.

## PayrollStateWageTaxPrepDP (Class)

**PayrollStateWageTaxPrepDP** is the data provider class for the **Payroll State Wage Tax Prep** SQL Server Reporting Services (SSRS) report. For the United States, three values are available: **Male**, **Female**, and **Unspecified**. In the **populatePayrollStateWageTaxPrepTmp** method, there is a switch statement that is used to map the value of the **HcmPersonGender** enum to one of three fields: **IsMale**, **IsFemale**, or **IsUnspecifiedGender**. The default value for the switch statement is **IsUnspecifiedGender**. If you add any values to the **HcmPersonGender** enum to map differently, you must create an extension by using the **Chain of Command** class over the **populatePayrollStateWageTaxPrepTmp** method to change the value as needed.

## smmOutlookSync_Contact (Class)

The **smmOutlookSync_Contact** integration class links values to and from **Outlook** and **Contact persons**. **Outlook** supports three values: **Male**, **Female**, and **Unspecified**. The class has two methods to help you map **Genders** to **OutlookGenders**. The default method is **NonSpecific/UnSpecified**. If you create additional values for the **Gender** enum, you should create an extension by using the **Chain of Command** class over both methods and map as needed.
