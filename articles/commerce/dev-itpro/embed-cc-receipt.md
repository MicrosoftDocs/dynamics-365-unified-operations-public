---
# required metadata

title: Embed processor credit card receipts in customer receipts
description: This topic describes how to embed receipts from payment processors into the customer's itemized transaction receipt.
author: rubendel
manager: annbe
ms.date: 04/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 04-31-2020
ms.dyn365.ops.version: AX 7.0.1

---

# Embed processor credit card receipts in customer receipts


[!include [banner](../includes/banner.md)]

This topic describes how to embed payment processor receipts in a customer receipt. This capability is available in Microsoft Dynamics 365 Commerce starting with the 10.0.8 release. 

## Key terms

| Term | Description |
|---|---|
| Customer's receipt | The receipt generated at the point of sale (POS) for a cash and carry transaction. |
| Customer's credit card receipt | The credit card receipt that prints as a record of the credit card or other electronic payment used in a transaction. |

## Overview

This topic describes the steps required to embed a credit card receipt from the payment processor directly into the customer's receipt. In Retail versions 10.0.7 and earlier, several elements from the customer's credit card receipt could be embedded in the customer's itemized transaction receipt, but the actual receipt coming from the processor could not be included. That solution was not acceptable for all retailers, because the configurable receipt fields in the customer's credit card receipt did not always include all of the details required by local statutory requirements. 

## Prerequisites

The following items are required to embed processor credit card receipts in customer receipts.

- **Payment connector**: A payment connector that is implemented in accordance with the payments SDK.
- **POS with printer**: A POS with a working printer.

## Set up receipts

1. In the POS, search for "receipt formats" to open the **Receipt formats** page. 
2. Select the receipt of type "customer's credit card receipt" that will be used at the POS. If you are using demo data, select receipt format **3_P** and set **Print Behavior** to **Do not print**.
3. Click **Designer** to launch the receipt designer. 
4. Remove all of the fields from the receipt format. To edit a section of the receipt, you must first select the section in the bottom-left side of the designer window, then select the targeted receipt variable within the selected section. Use the keystroke "ALT+D" to delete the selected variable.
5. Select the **Header** section of the receipt and drag the **EFT Message** variable into the header. 

![EFT Message variable on Cardholder's receipt](media/Cardholders.png)

6. Click **Save**
7. With the receipt designer still open, click **Select format** in the top-left corner. A receipt selector is launched in a separate window. 
8. In the receipt selector, select the receipt of type "receipt" that will be at the POS. If you are using demo data, select receipt format **1_p**. 
9. Select **Footer** in the lower-left section of the window and drag the **Card tender details** receipt variable into the footer.

![Card tender details on the customer's receipt](media/customersreceipt.png)

10. Click **Save**. 
11. Sync the changes to the POS using the **1090** distribution schedule.
12. Close the shift in POS and open a new shift. 
13. Perform a credit card transaction to confirm that the processor's credit card receipt is embedded in the customer's receipt. 

![Customer's receipt with credit card details](media/receipt_w_cc.png)


