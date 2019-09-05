---
# required metadata

title: Cookie Compliance
description: This topic reviews considerations for Cookie Compliance and the default policies included within Dynamics 365 e-Commerce tooling.
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Cookie Compliance

Applies to Dynamics 365 e-Commerce for online tracking technologies and adhering to GDPR standards.

Privacy is an important factor when working with any tracking technologies that would affect an e-Commerce consumer. With privacy compliance standards such as GDPR in the EU, e-Privacy guidelines must be considered for any site that is active today. Many e-Commerce sites are globally accessible by default. For this reason, it is important to review compliance standards for your e-Commerce site.



The EU GDPR regulations for cookies directs:

- Receive users' consent before you use any cookies **except** strictly necessary cookies.
- Provide accurate and specific information about the data each cookie tracks and its purpose in plain language before consent is received.
- Document and store consent received from users.
- Allow users to access your service even if they refuse to allow the use of certain cookies.
- Make it as easy for users to withdraw their consent as it was for them to give their consent in the first place.

  ​	(Source https://gdpr.eu/cookies/)

Dynamics 365 e-Commerce by default does not collect any customer cookies that are not strictly necessary. This ensures sites built directly in the e-Commerce Authoring Tools will not be published with non-essential cookies.

However, note that any customizations or extensibility added to your site which may add cookies or tracking technologies will need to take GDPR and cookie compliance into account as necessary.

Additional information regarding GDPR Privacy standards can be found at https://gdpr.eu

