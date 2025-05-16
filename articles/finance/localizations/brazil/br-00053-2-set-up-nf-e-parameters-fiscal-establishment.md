---
title: Set up NF-e parameters for a fiscal establishment (Brazil)
description: This article describes how to set up parameters for a Nota Fiscal eletrônica (NF-e) for a fiscal establishment in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Set up NF-e parameters for a fiscal establishment (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up parameters for a Nota Fiscal eletrônica (NF-e) for a fiscal establishment in Brazil with Microsoft Dynamics 365 Finance.

Use the following procedure to set up the parameters for an NF-e for a fiscal establishment. 

The procedure uses the BRMF demo company.

To set up the parameters for an NF-e for a fiscal establishment, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Select a fiscal establishment for which to set up NF-e.
1. Expand the **NF-e and NFC-e federal** section.
1. Select **Edit**.
1. Enter the digital certificate that authenticates the electronic fiscal documents that are issued by the fiscal establishment.
1. Select the NF-e environment type:    
    - Select **Testing** to issue an NF-e to the testing environment.
    - Select **Production** to issue a valid NF-e to the tax authority's production environment.
1. Select the version of the NF-e XML schema.
1. Select the state tax authority for NF-e.
1. Select the default email template to be used to notify customers when the NF-e is authorized by the tax authority.
1. Select the default email template to be used to notify customers when the NF-e is canceled by the tax authority.
1. Select the default email template to be used to notify customers when the NF-e is updated by an electronic correction letter.
1. In the **Preprinted security form** field, select **Yes** when the fiscal establishment uses a preprinted security form to print a Documento Auxiliar da Nota Fiscal Eletrônica (DANFE) in security form contingency mode.  
1. In the **Attach the DANFE as PDF file to email** field, select **Yes** to automatically attach the DANFE to the email sent to the customer after the NF-e is authorized by the tax authority.  
1. In the **Print DANFE when NF-e is approved** field, select **Yes** to automatically print the DANFE after the NF-e is authorized by the tax authority.  
1. In the **Validate XML schema on posting** field, select **Yes** to validate the NF-e XML against the official XML schema published by the tax authority before fiscal documents are posted.  
1. In the **Post only NF-e that have valid access keys** field, select **Yes** to validate the NF-e access key from an NF-e issued by a vendor before the vendor fiscal documents are posted.  
1. In the **Block NF-e posting if XML does not match** field, select **Yes** if a vendor fiscal document shouldn't be posted when the NF-e XML from the vendor doesn't match the order.  
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
