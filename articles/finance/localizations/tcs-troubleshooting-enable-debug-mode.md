---
# required metadata 

title: Enable debug mode in Tax Calculation service
description: This topic explains how to enable debug mode of Tax Calculation service to investigate issues. 
author: hangwan
ms.date: 03/23/2022
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
ms.search.validFrom: 03/23/2022
ms.dyn365.ops.version: Version 10.0.21 
---
# Enable debug mode

This topic explains how to enable debug mode of Tax Calculation service to investigate issues.

- Append **&debug=vs%2CconfirmExit&** to the URL of AOS, then refresh the page
- A `TXT` file named `TaxServiceTroubleshootingLog` will present when clicking `Sales tax` button to calculate tax
- The TaxServiceTroubleshootingLog.txt contains taxabledocument, calculation parameter, the result returned from tax service and exceptions information for troubleshooting.

## Sample

```json
===============================Tax service calculation input JSON:=====================================
{
    "TaxableDocument": {
    "Header": [
        {
        "Lines": [
            {
            "Transaction Line ID": "5816,68719677391",
            ...
            }
        ],
        "Transaction Header ID": "2022,68719506302",
        ...
        }
    ]
    },
    "Parameter": {
    "ContinueOnErrors": true,
    ...
    },
    "Adjustment": {
    "Lines": {}
    }
}
===========================Tax service calculation result JSON:=================================
{
    "taxDocument": {
    "Header": [
        {
        "Lines": [
            {
            "Tax Codes": {
                ...
            }
        ],
        "Measures": {
            "List Code": "EUTrade"
        },
        "Tax Registration ID": null,
        "Transaction Header ID": "2022,68719506302",
        "Errors": null
        }
    ]
    },
    "solutionId": "b51e0025-cbbe-4d37-bf0b-90d7be4f214d|1",
    "isPartialSuccess": false
}
=============================CorrelationId:==============================
"21f3a8a1-ee9a-477b-b44e-b8ec79e74d16"
```
