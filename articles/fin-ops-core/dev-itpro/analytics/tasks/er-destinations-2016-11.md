---
title: ER Configure destinations
description: This procedure demonstrates how to set up and use different destinations for Electronic reporting (ER) output components, such as a folder or a file.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERFormatDestinationTable, SysLookupPicklist, ERFormatDestinationSettings, ERFormatDestinationEmailSettings, ERExpressionDesignerFormula, SRSPrintDestinationTokens
---

# ER Configure destinations

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up and use different destinations for Electronic reporting (ER) output components, such as a folder or a file. The demo data company used to create this procedure is DEMF. Germany is the country\region of the legal entity's primary address, but you can use any legal entity for this procedure. 

The format used in this example is ISO20022 Credit transfer, but you can use any format that you already imported. This procedure is an example of a single file and a single destination setup. For more information about Electronic reporting destination management, see Dynamics 365 Finance Help.

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting destination**.
1. Select **New** to create a new set of destinations for a format.
1. In the **Reference** field, select a format for which you want to configure destinations.
    * If you don't see a value to select, it means that you didn't import any Electronic reporting format configurations. You must import a format configuration before setting up destinations.  
1. Select **New** to create a new file destination.
    * You can create one file destination for each output component of the same format, such as a folder or a file. You can enable and disable destinations separately in the settings.  
1. In the **Name** field, enter the user-friendly name of output component.
    * Use meaningful names, such as "Payment file" or "Control report". Users see these names at configuration runtime along with the destination settings.  
1. In the **File name**, select a file or folder that is specific to the format.
1. Select **Settings**.
1. Select **Yes** in the **Enabled** field.
    * The **Enabled** check box on each tab enables and disables each destination separately. In this example, you enable sending an output file to a mail recipient when the file is generated.  
1. Select **Edit**, to set up email recipients.
1. Select **Add**.
1. Select **Print Management email**.
1. In the **Email source** field, select an option.
    * You can select different email source types, such as a customer or a vendor type. This option defines the type of argument that the **Email source account** formula returns. The **Email source account** formula, described in a following step, is the place where you bind an email source. Select **Vendor** if your formula returns a vendor account. Use **Vendor** if you're using the ISO 20022 Credit Transfer configuration example.  
1. Select **Email source** bind button.
1. In the **Formula**, enter a document-specific reference to a party type that you selected earlier.
    * Instead of typing, you can find a data source node that represents the party account, and select the **Add data source** button to update the formula. For example, if you use the ISO 20022 Credit Transfer configuration, the node representing a vendor account is `$PaymentsForCoveringLetter.Creditor.Identification.SourceID`. Otherwise, enter any string value, such as "DE-001", to save a formula.  
1. Select **Save**.
1. Close the page.
1. Select **Edit** to configure contact details for the party.
1. Select **Yes** in the **Primary contact** field.
    * You can use different options to indicate what contact type of the party should be used as an email address for this destination. This example uses primary contact.  
1. Select **OK**.
1. Select **OK**.
1. In the **Subject** field, type a value.
1. Select **OK**.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
