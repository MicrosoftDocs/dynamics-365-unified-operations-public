---
# required metadata

title: Gender Base Enum extensibility
description: This topic provides an overview of extending the Gender Base Enum.
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
ms.custom: ["51941", "intro-internal"]
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---
# Gender Base Enum extensibility

This topic provides an overview of extending the **Gender** enum.

## Overview
The **Gender** enum is now extensible. This topic describes the changes to make within the code base if you plan on extending the **Gender** enum.

## Gender vs HcmPersonGender

There are two enums for gender values:
 - **Gender** (Application Platform)
 - **HcmPersonGender** (PersonnelManagement)
 
The **Gender** enum is used throughout Dynamics 365 Finance and **HcmPersonGender** is specific to HCM functionality. If you're using HCM functionality, you'll 
want to consider making any changes to the **HcmPersonGender** as well. For example, if **Transgender** is added to the **Gender** enum, add **Transgender** to the **HcmPersonGender** enum as well.

## HcmPersonGenderTranformUtil (Class)
A new class was created to allow for translation between the two base enumerators. In this class there are two methods: **convertGenderToHcmPersonGender** and 
**convertHcmPersonGenderToGender**. You'll want to **Create extension** or **Chain of Command** class and extend both methods to map new values that are added to 
either base enumeration.

## PayrollStateWageTaxPrepDP (Class)
The **PayrollStateWageTaxPrepDP** is the data provider class for the **Payroll State Wage Tax Prep** SSRS report. For the United States, there are three values available: **Male**, **Female**, and **Unspecified**. In the **populatePayrollStateWageTaxPrepTmp** method, there's a switch statement to map the value of the **HcmPersonGender** enum to one of three fields: **IsMale**, **IsFemale**, **IsUnspecifiedGender**. The default value for the switch statement is **IsUnspecifiedGender**. If you add any values to the **HcmPersonGender** to map differently, you would need to **Create extension** or **Chain of Command** extension over the **populatePayrollStateWageTaxPrepTmp** method to change the value as needed.

## smmOutlookSync_Contact (Class)
This integration class ties values to/from **Outlook** and **Contact persons**. **Outlook** supports three values: **Male**, **Female**, **Unspecified**. The class has 
two methods to help map **Genders** to **OutlookGenders**. The default is **NonSpecific/UnSpecified**. If you create additional values for the **Gender** enum, you'll 
want to **Create extension** or **Chain of Command** over both methods and map as needed. 
