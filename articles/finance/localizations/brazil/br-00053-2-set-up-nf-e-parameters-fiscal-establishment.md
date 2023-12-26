---
title: Set up NF-e parameters for a fiscal establishment (Brazil)
description: Use the following procedure to set up the parameters for a Nota Fiscal eletrônica (NF-e) for a fiscal establishment.
author: AdamTrukawka
ms.date: 06/26/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Set up NF-e parameters for a fiscal establishment (Brazil)

[!include [banner](../../includes/banner.md)]

Use the following procedure to set up the parameters for a Nota Fiscal eletrônica (NF-e) for a fiscal establishment. This task uses the BRMF demo company.

1. Go to Organization administration > Organizations > Fiscal establishments > Fiscal establishments.
2. Select a fiscal establishment to set up NF-e for.
3. Expand the NF-e and NFC-e federal section.
4. Click Edit.
5. Enter the digital certificate that authenticates the electronic fiscal documents that are issued by the fiscal establishment.
6. Select the NF-e environment type.
    * Select Testing to issue an NF-e to the testing environment. Select Production to issue a valid NF-e to the tax authority's production environment.  
7. Select the version of the NF-e XML schema.
8. Select the state tax authority for NF-e.
9. Select the default email template that should be used to notify the customer when the NF-e is authorized by the tax authority.
10. Select the default email template that should be used to notify the customer when the NF-e is canceled by the tax authority.
11. Select the default email template that should be used to notify the customer when the NF-e is updated by an electronic correction letter.
12. Select Yes in the Preprinted security form field.
    * Select this option when the fiscal establishment uses a preprinted security form to print DANFE in the security form contingency mode.  
13. Select Yes in the Attach the DANFE as PDF file to  email field.
    * Select this option to automatically attach the DANFE to the email that is sent to the customer after the NF-e has been authorized by the tax authority.  
14. Select Yes in the Print DANFE when NF-e is approved field.
    * Select this option to automatically print the DANFE after the NF-e has been authorized by the tax authority.  
15. Select Yes in the Validate XML schema on posting field.
    * Select this option to validate the NF-e XML against the official XML schema that is published by the tax authority before fiscal documents are posted.  
16. Select Yes in the Post only NF-e that have valid access keys field.
    * Select this option to validate the NF-e access key from an NF-e that is issued by a vendor before vendor fiscal documents are posted.  
17. Select Yes in the Block NF-e posting if XML does not match field.
    * Select this option if a vendor fiscal document should not be posted if the NF-e XML from the vendor doesn't match the order.  
18. Click Save.
19. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
