---
title: Fiscal establishment tax attributes (Brazil)
description: Use this procedure to create one or more fiscal establishments for a legal entity.
author: AdamTrukawka
ms.date: 06/24/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Manufacturing;Distribution;Service industries
---
# Fiscal establishment tax attributes (Brazil)

[!include [banner](../../includes/banner.md)]

Use this procedure to create one or more fiscal establishments for a legal entity. A fiscal establishment requires a Cadastro Nacional da Pessoa Jurídica (CNPJ) or Inscrição Estadual (IE) tax registration number. You can group fiscal establishments and set up tax groups for each fiscal establishment group in the Taxes matrix page. This task uses the BRMF demo company.

1. Go to Organization administration > Organizations > Legal entities.
2. Click to follow the link in the Name field.
3. Expand the Addresses section.
4. Click Add.
5. In the Name or description field, type a value.
6. In the Purpose field, enter or select a value.
7. In the Country/region field, type a value.
8. Click Yes.
9. In the ZIP/postal code field, type a value.
10. In the Street number field, type a value.
11. Click OK.
12. Close the page.
13. Close the page.
14. Go to Organization administration > Organizations > Fiscal establishments > Fiscal establishment groups.
15. Create new fiscal establishment group.
16. In the Fiscal establishment group field, type a value.
17. In the Description field, type a value.
18. Click Save.
19. Close the page.
20. Go to Organization administration > Organizations > Fiscal establishments > Fiscal establishments.
21. Create new fiscal establishment.
22. In the Fiscal establishment ID field, type a value.
23. In the Fiscal establishment group field, enter or select a value.
24. In the CNPJ field, enter the CNPJ of the new fiscal establishment.
25. Expand the Address section.
26. In the Name field, enter or select a value.
27. In the IE field, enter the IE of the fiscal establishment based on the state in the address.
28. Click Save.
29. Close the page.
30. Go to Inventory management > Setup > Inventory breakdown > Sites.
31. Click New.
32. In the Site field, type a value.
33. In the Name field, type a value.
34. In the Fiscal establishment ID field, enter or select a value.
35. Expand the Financial dimensions section.
36. Click to follow the link in the Filial field.
37. Click New.
38. In the Dimension value field, type a value.
39. In the Description field, type a value.
40. Click Add to open the drop dialog.
41. Click Add.
42. Click Save.
43. Close the page.
44. In the Filial field, enter or select a value.
45. Click Save.
46. Close the page.
47. Go to Organization administration > Organizations > Fiscal establishments > Fiscal establishments.
48. Open the advanced row selection dialog
49. Apply the following filters: Enter a filter value of "NovaFilial" on the "Fiscal establishment ID" field using the "is exactly" filter operator
50. Click Fiscal document types.
51. Click New.
52. In the Fiscal document type field, type a value.
53. In the Name field, type a value.
54. In the Series field, type a value.
55. In the Fiscal document number sequence field, enter or select a value.
56. In the Document model field, enter or select a value.
57. Click Save.
58. Close the page.
59. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
