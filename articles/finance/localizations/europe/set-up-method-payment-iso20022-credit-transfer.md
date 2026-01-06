--- 
title: Set up method of payment for ISO20022 credit transfer
description: Learn how to set up a vendor method of payment for a ISO20022 credit transfer or any other payment type using electronic reporting to generate a file in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak    
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: VendPaymMode
---

# Set up method of payment for ISO20022 credit transfer

[!include [banner](../../includes/banner.md)]

The following procedure explains how to set up a vendor method of payment for a ISO20022 credit transfer or any other payment type using electronic reporting to generate a file in Microsoft Dynamics 365 Finance.

Before you complete the procedure, you must first export format configurations and set up payment accounts.

The procedure was created using the DEMF demo data company.

To set up a vendor method of payment for a ISO20022 credit transfer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Methods of payment**.
1. Use the Quick Filter to find records. For example, filter on the **Method of payment** field with a value of "SEPA CT".
1. Select **Edit**.
1. In the **Period field**, select **Total**.
1. In the **Payment type** field, select **Electronic payment**.
1. Expand the **File formats** section.
1. In the **Generic electronic reporting** field, select **Yes**.
1. In the **Export format configuration** field, select **ISO20022 Credit transfer (DE)**. If the list is empty, the vendor payment export format configuration isn't imported and active.  
9. In the **Account type** field, select **Bank**.
1. In the **Payment account** field, enter "DEMF OPER".
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
