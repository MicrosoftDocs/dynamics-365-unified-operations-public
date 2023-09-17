---
title: Set up NF-e federal parameters (Brazil)
description: You can set up Nota Fiscal eletrônica (NF-e) web services, rejection codes, and schemas to generate an NF-e.
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
# Set up NF-e federal parameters (Brazil)

[!include [banner](../../includes/banner.md)]

You can set up Nota Fiscal eletrônica (NF-e) web services, rejection codes, and schemas to generate an NF-e. After you generate an NF-e, XML messages are generated and submitted to the Secretaria da Fazenda (SEFAZ). This task uses the BRMF demo company.



1. Go to Organization administration > Organizations > Electronic fiscal documents > NF-e federal parameters.
2. Click New.
    * One tax authority must be created per state.  
3. In the Authority field, type a value.
4. In the Name field, type a value.
5. Select the Ignore accents check box.
6. Select the Cancel as Event check box.
    * This option complies with the cancellation of NF-e through events instead of a specific XML cancellation file.  
7. Click Save.
8. Click New.
9. In the Environment field, select an option.
10. Select the web service for NF-e authorization.
11. In the Version field, type a value.
12. In the Internet address field, type a value.
13. Click New.
14. In the Environment field, select an option.
15. Select the web service for NF-e discard.
16. In the Version field, type a value.
17. In the Internet address field, type a value.
18. Click New.
19. In the Environment field, select an option.
20. Select the web service for NF-e inquiries.
21. In the Version field, type a value.
22. In the Internet address field, type a value.
23. Click New.
24. In the Environment field, select an option.
25. Select the web service for NF-e authorization returns.
26. In the Version field, type a value.
27. In the Internet address field, type a value.
28. Click New.
29. In the Environment field, select an option.
30. Select the web service for NF-e events.
31. In the Version field, type a value.
32. In the Internet address field, type a value.
33. Click New.
34. In the Environment field, select an option.
35. Select the web service for NF-e service status inquiries.
36. In the Version field, type a value.
37. In the Internet address field, type a value.
38. Click Save.
39. Click the Rejection codes tab.
40. Click New.
    * Enter the rejection codes that are listed in the official NF-e guide.  
41. In the NF-e rejection code field, enter the rejection code from the official NF-e guide.
42. In the Description field, type a value.
43. In the list, mark the selected row.
44. In the Message type field, select an option.
45. In the Fiscal document status field, select an option.
    * Enter the fiscal document status that must be set when the rejection code is entered.  
46. Click Save.
47. Click the Schemas tab.
48. Click New.
    * When applicable, enter the path of the XSD file that will be used to validate the NF-e XML.  
49. In the The version of the NF-e feature field, select an option.
50. In the Schema field, type a value.
51. Click New.
52. In the Schema type field, select an option.
53. In the The version of the NF-e feature field, select an option.
54. In the Schema field, type a value.
55. Click New.
56. In the Schema type field, select an option.
57. In the The version of the NF-e feature field, select an option.
58. In the Schema field, type a value.
59. Click New.
60. In the Schema type field, select an option.
61. In the The version of the NF-e feature field, select an option.
62. In the Schema field, type a value.
63. Click Save.
64. Close the page.
65. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
