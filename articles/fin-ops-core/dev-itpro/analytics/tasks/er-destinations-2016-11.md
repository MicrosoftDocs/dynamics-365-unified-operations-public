---
title: ER Configure destinations
description: This procedure demonstrates how to set up and use different destinations for Electronic reporting (ER) output components, such as a folder or a file.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERFormatDestinationTable, SysLookupPicklist, ERFormatDestinationSettings, ERFormatDestinationEmailSettings, ERExpressionDesignerFormula, SRSPrintDestinationTokens
---
# ER Configure destinations

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to set up and use different destinations for Electronic reporting (ER) output components, such as a folder or a file. The demo data company used to create this procedure is DEMF. Germany is the country\region of the legal entity's primary address, however you can use any legal entity for this procedure. 

The format used in this example is ISO20022 Credit transfer, but you can use any format that you have already imported. Note, this procedure is an example of a single file and a single destination setup. More information about Electronic reporting destination management can be found in the Dynamics 365 Finance Help.

1. Go to Organization administration > Electronic reporting > Electronic reporting destination.
2. Click New to create a new set of destinations for a format.
3. In the Reference field, select a format for which you want to configure destinations.
    * If you don't have a value to select, it means that you have not imported any Electronic reporting format configurations. You must import a format configuration before setting up destinations.  
4. Click New to create a new file destination.
    * Note, you can create one file destination for each output component of the same format, such as a folder or a file. You will be able to enable and disable destinations separately in the settings.  
5. In the Name field, enter the user-friendly name of output component.
    * We recommend that you use meaningful names, such as "Payment file" or "Control report". These names will be presented to users at configuration runtime along with the destination settings.  
6. In the File name, select a file or folder that is specific to the format.
7. Click Settings.
8. Select Yes in the Enabled field.
    * The Enabled check box on each tab enables and disables each destination separately. In this example, you'll enable sending an output file to a mail recipient when the file is generated.  
9. Click Edit, to set up email recipients.
10. Click Add.
11. Click Print Management email.
12. In the Email source  field, select an option.
    * You can select different email source types, such as a customer or a vendor type. This defines the type of argument that will be returned by the Email source account formula. The Email source account formula, described in a following step, is the place where you bind an email source. Select Vendor if your formula will return a vendor account. Use Vendor if you are using the ISO 20022 Credit Transfer configuration example.  
13. Click Email source bind button.
14. In the Formula, enter a document-specific reference to a party type that you selected earlier.
    * Instead of typing, you can find a data source node that represents the party account, and click the Add data source button to update the formula. For example, if you use the ISO 20022 Credit Transfer configuration, the node representing a vendor account is '$PaymentsForCoveringLetter'.Creditor.Identification.SourceID. Otherwise, enter any string value, such as "DE-001", to save a formula.  
15. Click Save.
16. Close the page.
17. Click Edit to configure contact details for the party.
18. Select Yes in the Primary contact field.
    * You may use different options to indicate what contact type of the party should be used as an email address for this destination. We use primary contact in this example.  
19. Click OK.
20. Click OK.
21. In the Subject field, type a value.
22. Click OK.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
