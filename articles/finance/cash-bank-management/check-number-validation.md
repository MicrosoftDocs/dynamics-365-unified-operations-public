---
# required metadata

title: Check number validation 
description: This article provides an overview of check number validation functionality in the Cash and bank management module.
author: wangchen
ms.date: 11/06/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-03-08
ms.dyn365.ops.version: 10.0.37

---
# Check number validation

You can use this feature to validate a check number when you generate a payment. When this feature is enabled, the system validates whether check number exceeds the defined interval with last check number. You can set up the check number interval. If the check number exceeds the defined interval with last check number, confirm before you proceed to avoid manually entering the wrong check number. Next, the system validates if there's a character in the check number.

## Set up validation parameters

1. Go to the **Feature management** workspace and in the list of features, find and select **Enable check number validation**.
2. Select **Enable now**.
3. Go to **Cash and bank management parameters** > **General** > **Check setup**.
4. On the **Check setup** page, enable the **Allow check number validation** parameter to validate the check number when you generate a payment document in the vendor payment journal. This parameter enables two validations:
  - Check number interval validation
  - Check number character validation
5. In the **Check number interval** field, select the interval to trigger the check number validation when the user-defined check number on the vendor payment journal exceeds the interval with last check number.

## Validating the check number

There are two scenarios that result in the system validating the check number.  

  -  Wrong check number: You inadvertently enter the wrong check number when you generate payment on a vendor payment journal and the method of payment is **Check**. 
  - Characters in the check number: You inadvertently add characters to the check number when you generate payment on a vendor payment journal and the method of payment is **Check**.

If either of these scenarios occur, a warning message will appear confirming your entry.  
