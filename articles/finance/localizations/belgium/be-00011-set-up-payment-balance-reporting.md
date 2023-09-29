---
title: Set up payment balance reporting (Belgium)
description: Use this procedure to set up Belgisch Luxemburgs Wissel Instituut (BLWI) information for Belgium.
author: AdamTrukawka
ms.date: 07/12/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Belgium
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Set up payment balance reporting (Belgium)

[!include [banner](../../includes/banner.md)]

Use this procedure to set up Belgisch Luxemburgs Wissel Instituut (BLWI) information for Belgium. This procedure was created by using the USSI demo data company.

This functionality is available for legal entities that have their primary address in Belgium. Before you can complete this procedure, you must set up the registration ID for Belgium and enter the registration number that should be used to create the BLWI declaration.


## Set up a BLWI country/region group
1. Go to Tax > Setup > Foreign trade > BLWI country/region groups.
2. Click New.
3. In the Group ID field, type a value.
4. In the Description field, type a value.
5. Click Add.
6. In the Country/region field, enter or select a value.
7. In the Description field, type a value.
8. Click Translations.
9. In the Language field, enter or select a value.
10. Close the page.

## Set up BLWI currencies
1. Go to Tax > Setup > Foreign trade > BLWI currencies.
2. Click New.
3. In the Currency field, enter or select a value.
4. Select the Report in this currency check box.
5. In the Column number field, enter a number.

## Set up BLWI parameters
1. Go to Tax > Setup > Foreign trade > BLWI parameters.
2. Select Yes in the BLWI field.
    * This parameter should be activated before you post customer/vendor transactions, so that the transactions are transferred to the payment balance.  
3. In the Email field, type a value.
4. In the Name field, type a value.
5. In the Telephone field, type a value.
6. In the Fax field, type a value.
7. In the Check BLWI code on journals field, select an option.
    * In the Check BLWI code field, select the rule for checking that a payment purpose code is specified in documents. The available options are None, Warning, and Error. If a transaction has a customer/vendor that is located in a foreign country/region (that is, the country/region of the customer/vendor differs from the country/region of the legal entity), the transaction doesn't have an assigned payment purpose code, and the check is set to Warning or Error, either a warning or error message will be shown during posting. This validation is applied for all customer/vendor transactions except payment transactions.  
8. In the Format mapping field, enter or select a value.
    * Prerequisite: You should upload the BLWI format (BE) configuration for Electronic reporting (ER) from Microsoft Dynamics Lifecycle Services (LCS).  

## Set up payment survey codes
1. Go to Tax > Setup > Foreign trade > Payment survey codes.
2. Click New.
3. In the Survey code field, type a value.
4. In the Month/Quarter field, select an option.
5. In the Calculation type field, select an option.
    * If you select Turnover in the Calculation type field, the customer/vendor transactions that are posted during the reporting period are transferred to the payment balance, and the amount that is reported is the total amount of the posted transaction.  If you select Balance, the customer/vendor transactions that are open (not fully settled/closed) at the end of the reporting period are transferred to the payment balance, and the amount that is reported is the open (unsettled) amount of the posted transaction as of the end of the reporting period.  
6. In the Description field, type a value.
7. In the Summary country/region field, type a value.
8. Click Add.
9. In the Central bank purpose code field, enter or select a value.
10. Select the Include payment check box.
    * Note that payment transactions won't be transferred to the payment balance survey by default. The user must activate the Include payment field for purpose codes.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
