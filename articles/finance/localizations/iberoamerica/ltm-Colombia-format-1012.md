---
title: Format 1012 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing a Format 1012 file for Colombia. 
author: Fhernandez0088
ms.date: 11/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1012 file for Colombia issue configuration  
This article will explain the necessary configurations to be done to issue a format 1012 file.	
The format 1012 file shows the company investments to be informed to the tax authority.
## Prerequisites
To print the report, it is necessary to meet the following prerequisites: 
* The legal entity address must be set in Colombia.
* Have both the country specific LATAM globalization feature and the general LATAM feature enabled.
* Import the configurations needed from the **Global** repository: 
	* LTM Tax Report
	* File format 1012

See [Download ER Configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters.

See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.

## Configure application specific parameters for format 1012 file
Lookups and conditions are designed to allow you to choose the combination of documents classification ids. and ledger account numbers used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1012**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.
5. In the **Lookups** section select the first lookup referring to the main account group “MainAccountGroup”. 
6. In the **Conditions** section add a line and in the Lookup result field select one of the following: 
    * **1110**: national bank accounts.
    * **1115**: international bank accounts.
    * **1200**: treasury bonds.
    * **1201**: deposit certifies.
    * **1202**: shares value.
    * **1203**: fiduciary rights.
    * **1204**: other investments value.
    * **1205**: crypto investments value.

These are the different option that will represent different concepts for the format 1012 file.
Add as many lines as concepts should contain the format 1012 file.
7. For each condition added complete the **Label** field with the concept number and in the **Main account** field select the ledger account that represents that concept.

> [!NOTE]
> The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

9. In the **Lookups** section select the second lookup “COMP1012”, it refers to the payment method document class used to post transactions for each concept in the other lookup.
10. In the **Conditions** section add a line and in the **Lookup result** column select a concept from the following:
    * **DEP BCO**: bank deposits.
    * **EFE CAJA CLP**: cash national currency.
    * **EFE CAJA USD**: cash USD.
    * **EFECTIVO**:
    * **EFECTIVO MN**: 
    * **TRB**: wire transfers.

## Issue Format 1012 file
Once the setup is finished follow these steps to issue a file:
1. Go to **Tax > Inquiries and Reports > LATAM > Tax reporting**.
2. Select **Format 1012** and click on ok.
3. Select the date range of the transactions you want to consult by opening the calendar for the **From Date** and **To Date** fields. 
4. Select ok.
