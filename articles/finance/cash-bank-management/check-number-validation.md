---
title: Check number validation 
description: Learn about check number validation functionality in the Cash and bank management module, including a step-by-step process for setting up validation parameters.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 11/06/2023
ms.custom: 
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-03-08
ms.search.form:
ms.dyn365.ops.version: 10.0.37
---

# Check number validation

You can use this feature to validate a check number when you generate a payment. When this feature is enabled, the system validates whether the interval between the current check number and the last check number exceeds the value that you defined. If it does, you must confirm your entry before you proceed, to avoid manually entering the wrong check number. The system then validates whether there's an uexpected character type in the check number.

## Set up validation parameters

1. Open the **Feature management** workspace, and then, in the list of features, find and select **Enable check number validation**.
2. Select **Enable now**.
3. Go to **Cash and bank management parameters** \> **General** \> **Check setup**.
4. On the **Check setup** page, enable the **Allow check number validation** parameter to validate the check number when you generate a payment document in the vendor payment journal. This parameter enables two validations:

    - Check number interval validation
    - Check number character validation

5. In the **Check number interval** field, select a value. Check number validation is then triggered if the interval between the user-defined check number in the vendor payment journal and the last check number exceeds this value.

## Validation scenarios

Two scenarios cause the system to validate the check number:

- **Incorrect check number** – You inadvertently enter the wrong check number when you generate a payment in a vendor payment journal, and the method of payment is **Check**. 
- **Characters in the check number** – You inadvertently add characters to the check number when you generate a payment in a vendor payment journal, and the method of payment is **Check**.

If either scenario occurs, you receive a warning message that prompts you to confirm your entry.
