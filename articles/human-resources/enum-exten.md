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

This topic provides an overview of extending the Gender Base Enum.

## Overview
With the change to making the Gender Base Enum extensible, there are some considerations that should be taken into consideration before creating an extension. 
This topic describes the needed changes you should make within the code base if you plan on extending **Gender**.

## Gender vs HcmPersonGender

There are 2 Base Enums in the system to handle gender values:
 - **Gender** (Application Platform)
 - **HcmPersonGender** (PersonnelManagement)
 
The **Gender Base Enum** is used throughout Dynamics 365 Finance and **HcmPersonGender** is specific to HCM functionality. If you are using HCM functionality, you will 
want to consider making any changes to the **HcmPersonGender** as well.
For example, if **Transgender** is added as a value to the **Gender Base Enum**, we would also add **Transgender** to the **HcmPersonGender Base Enum** as well.

## HcmPersonGenderTranformUtil (Class)
A new class was created to allow for translation between the two base enumerators. In this class there are 2 methods: convertGenderToHcmPersonGender and 
convertHcmPersonGenderToGender. You will want to create an **Extension** or **Chain of Command** class and extend both methods to map any new values that you add to 
either base enumeration.

## PayrollStateWageTaxPrepDP (Class)
This is the data provider class for the **Payroll State Wage Tax Prep** SSRS report. For the United States, there are only 3 values available:**Male**, **Female**,
and **Unspecified**. In the **populatePayrollStateWageTaxPrepTmp** method, there is a switch statement to map the value of the **HcmPersonGender Base Enum** to one of 
three fields: **IsMale**, **IsFemale**, **IsUnspecifiedGender**. The default value for the switch statement is **IsUnspecifiedGender**. If you add any values to the 
**HcmPersonGender** to map differently, you would need to create an Extension or Chain of Command extension over the **populatePayrollStateWageTaxPrepTmp** method to 
change the value as needed.

## smmOutlookSync_Contact (Class)
This integration class ties values to/from **Outlook** and **Contact persons**. **Outlook** supports three values: **Male**, **Female**, **Unspecified**. The class has 
two methods to help map Genders to OutlookGenders. The default is **NonSpecific/UnSpecified**. If you creat additional values to the **Gender Base Enum**, you will 
want to create an Extension or Chain of Command over both methods and do the mapping as needed. 
