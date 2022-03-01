---
# required metadata 

title: Set up tax codes
description: This topic explains how to set up tax codes in Tax Calculation Service. 
author: wangchen
ms.date: 11/17/2021
ms.topic: business-process  
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxIntegrationTaxServiceParameters    
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-10-26 
ms.dyn365.ops.version: Version 10.0.21 
---

# Tax feature list is empty on tax calculation parameter

## Symptom

1. Publish my feature in RCS.
2. Go to *Finance and Operation > Tax > Setup > Tax configuration > Tax calculation parameters*.
3. Drop down the *Feture setup name*, list show empty.

## Rootcause
Usually, this is because user's *Finance and Operation* environment and *Regulatory Configuration Service* is not under the same tenant.

### *Regulatory Configuration Service* tenant

- Open browser with InPrivate mode
- Copy the full url of *Regulatory Configuration Service*, and enter it into the new Inprivate browser window, e.g. https://rcs-rts-sf-ed22b5aeea8-int-westus2.configure.global.int.dynamics.com/namespaces/817ff7a0-0d77-4aba-9360-3c9749e2c5de/?cmp=dat&mi=RCSFeatureDomainsWorkspace, and press **Enter**
- You will be navigate to login page, on the url, you can find the tenant ID of RCS, e.g. https://login.microsoftonline.com/d335a570-a05b-4bc5-8eb3-c42c65f9560d
- The tenant is following https://login.microsoftonline.com, so it's **d335a570-a05b-4bc5-8eb3-c42c65f9560d**


### *Finance and Operation* environment tenant ID
Same steps as to get *Regulatory Configuration Service* tenant, instead use the full url of *Finance and Operation* environment


If the two tenants Id are different, then it means you are running to issue described here, or else, please reach MS support. 

## Mitigate
### Solution 1
Make sure to sign in the *Regulatory Configuration Service* in the same tenant of *Finance and Operation* tenant, then create/publish tax feature.

### Solution 2
Share the tax feature to the tenant of *Finance and Operation* in *Regulatory Configuration Service*
1. Go to *Regulatory Configuration Service*
2. Globalization features > Tax Calculation.
3. Focus on the feature which you want to share. go to the tab **Organizations** which is after **Versions**.
![image.png](media/ShareTaxFeature.png)
4. Click Share with, and fill the **Organization domain name**, like **contoso.onmicrosoft.com**
