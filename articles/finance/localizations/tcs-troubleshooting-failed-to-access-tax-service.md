---
# required metadata 

title: Access tax calculation service
description: This topic explains how to access tax calculation service. 
author: hangwan
ms.date: 02/16/2022
ms.topic: business-process 
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxIntegrationTaxServiceParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: hangwan
ms.search.validFrom: 02/16/2022
ms.dyn365.ops.version: Version 10.0.21 
---
# Failed to access tax service

This topic explains how to resolve the error of Tax Calculation service: "Failed to access tax service."


## Symptoms

This section describes the symptom being experienced as a result of the error.

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax service parameter**
2. Open the **General** tab, enable the switch name **Enable tax calculation**, then select the dropdown list of **Feature setup name**.
3. An error message pop out as **Failed to access tax service**. 

## Cause

> The *Finance and Operation* cannot access **Tax Calculation Service**

## Troubleshooting

1. Go to customer's LCS environment page, go to **Environment add-ins** tab, check the **Tax Calclation** item.
2. Check the status, it should be either **Installing** or **Installed**
3. If tax calculation service add-in is not installed, you will face the error.

## Mitigation

1. Go to the *Finance and Operation* LCS page.
2. In the **Power platform integration** section, click **Install a new add-in**
3. Scorll down to the end of the form, and select add-in **Tax Calculation** to install.
4. Then go to *Finance and Operation* to try again.

## Note
1. Before doing install, you need to check the [Tax Caclualtion Service Prerequisites](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/add-ins-overview).
1. If **Power platform integration** section is not avaliable to install add-in, please refer to [Add-in overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/add-ins-overview).
2. If you still face the error after installing the Add-in, please contact your system administrator.

