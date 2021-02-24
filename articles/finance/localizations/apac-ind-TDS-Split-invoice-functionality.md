---
# required metadata

title: Split invoice functionality
description: 
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---
# Split invoice functionality

[!include [banner](../includes/banner.md)]

Select the **Product receipt**, or **Invoice** check boxes in **Accounts payable parameters > General** tab to post and split a product receipt or invoice with different delivery addresses and Tax Account Numbers (TAN) in the **Purchase** **order** form. The posted invoice is split per delivery address per TAN. 

Select the **Confirmation**, **Picking** **list**, **Packing** **slip**, or **Invoice** check boxes in **Accounts receivable parameters > Summary update > Split based on > DELIVERY INFORMATION** tab to post and split a confirmation, picking list, packing slip, or invoice with different delivery addresses and Tax Account Numbers (TAN) defined for different invoice lines in the **Sales** **order** form. The invoice is split per delivery address per TAN.

### Important Points 

- If the **Split** **based** **on** **delivery** **information** parameter is not selected, the invoice is posted as a single invoice and there will be no split of invoice.

- The **Packing** **slip** check box must be selected in the **Split** **based** **on** **delivery** **information** parameter to split and post a packing slip with invoice lines having different delivery addresses and Tax Account Numbers (TAN).

- The **Invoice** check box must be selected in the **Split** **based** **on** **delivery** **information** parameter to split and post an invoice with invoice lines having different delivery addresses and Tax Account Numbers (TAN).

- An invoice with invoice lines having different delivery addresses but same Tax Account Numbers (TAN) can be posted if the **Invoice** check box is not selected in the **Split** **based** **on** **delivery** **information** parameter. The invoice will be split per delivery address. 


**Example**:

The **Split** **based** **on** **delivery** **information** parameter is selected for the **Invoice** option. A purchase invoice is posted with the following setup:

Item line 1, Delivery address 1, TAN-ABCD12345A

Item line 2, Delivery address 1, TAN-ABCD12345A

Item line 3, Delivery address 2, TAN-ABCE12345B

Item line 4, Delivery address 3, TAN-ABCD12345A

 

Invoice 1 is posted for item line 1 and item line 2 because both have common delivery addresses and TAN.

Invoice 2 is posted for item line 3 and Invoice 3 is posted for item line 4.
