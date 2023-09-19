---

# required metadata

title: API based Payroll integration with Ceridian Dayforce
description: This article describes the API based Payroll integration API
Author: Tulsi
ms.author: tulsijhaveri
ms.date: 09/19/2023
ms.topic: how-to
ms.custom: 
---

# API based Payroll integration with Ceridian Dayforce

The API based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce relies on several configuration steps that are described in this article. You must configure the integration in both Human Resources and Dayforce before you can process a pay run. 

## Environment Settings

Before using the Dynamics 365 Human Resources Payroll integration, you must set up the parameters described in this article. 

•	Human Resources shared parameter > Positions, click Yes to enable Require departments on positions.

•	Human Resources shared parameter > Payroll integration, enable Use payroll address purposes.
•	Human Resources parameter > Payroll Integrations Enable , use identification Types in payroll integrations > identifications type=SSN.

Note: Human Resources parameters are unique to each legal entity. When using multiple legal entities, To expose the identification type ID in the payroll employee entity, you must configure human resources parameters for each company.  

•	Human Resources shared parameter > Financial dimensions, enable default financial dimensions.

Note: Collaborate with your Ceridian point of contact to determine which Financial dimensions should be enabled to align with the Dayforce Site (location).

•	Financial dimension configuration for integrating applications > Data entities.

Ensure that the financial dimension item(s) in the Selected list are in the correct order. The Connector will look at the financial dimension position that has been provided from the selected list in the Myintegration Portal.

For more information, see Configure Human Resources Parameters.

  



## API Setup
