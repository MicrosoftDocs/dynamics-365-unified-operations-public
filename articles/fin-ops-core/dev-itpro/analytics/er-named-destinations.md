---
# required metadata

title: Configure print management record specific ER destinations 
description: This topic explains how to configure print management record specific destinations for an Electronic reporting (ER) format that is configured to generate outbound documents.
author: NickSelin
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERFormatDestinationTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-08-01
ms.dyn365.ops.version: 10.0.21

---

# Configure print management record specific ER destinations

[!include [banner](../includes/banner.md)]

The procedures in this topic explain how a user in the System Administrator or Accounts Receivable Clerk role can perform these tasks:

- Configure named [Electronic reporting (ER)](general-electronic-reporting.md) destinations for the provided ER solution using to generate free text invoices
- Assign a named ER destination to a single [print management (PM)](document-reporting-services.md) record

All the following procedures can be done in the USMF company. No coding is required.

## Introduction

You can configure [destinations](electronic-reporting-destinations.md) for each output component (folder or file) of an ER [format](general-electronic-reporting.md#FormatComponentOutbound) [configuration](general-electronic-reporting.md#Configuration) that is used to generate an outbound document. Users who run an ER format of this type, and who have appropriate access rights, can also change the configured destination settings at runtime.

In Microsoft Dynamics 365 Finance **version 10.0.17 and later**, an ER format can be run by [provisioning](er-apis-app10-0-17.md) an action code that the user performs by running that ER format. For example, in the **Accounts receivable** module, in the PM settings, you can select an ER format that generates a specific business document, such as a free text invoice. You can then select **View** to preview the invoice or **Print** to send it to a printer. If a user action is passed for the running ER format at runtime, you can [configure different ER destinations for different user actions](er-action-dependent-destinations.md).

In Microsoft Dynamics 365 Finance **version 10.0.21 and later**, an ER format can be run by [provisioning](er-apis-app10-0-21.md) a named destination that is configured for the processed PM record. For example, in the **Accounts receivable** module, in the PM settings, you want to configure the **Original** record to run an ER format and email a generated invoice to customer and to configure the **Copy** record to run the same format and print out a copy of invoice to a network printer. So, you must configure different ER destinations for the running ER format and select them for different PM records. This topic explains how to configure named ER destinations and assign a named ER destination for a particular PM record. The free text invoice document type is used in this topic. 

## Prerequisites

It is assumed that the **Allow to set up ER destinations per print management item** feature was enabled in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) workspace in advance and source code has been changed to allow configuring named ER destinations in the current Finance instance and to enable the [new](er-apis-app10-0-21.md) ER API.

It is assumed that the **Free text invoice (Excel)** ER configuration has been [imported](er-download-configurations-global-repo.md) in advance to Finance instance.

## Configure a new named ER destination

1.  Go to **Accounts receivable \> Invoices \> All free text invoices**.
2.  Select an invoice with the **US-001** customer account.
3.  On the **Free text invoice** page, on the **Invoice** tab, in the **Print management** group, select **Print management**.
4.  On the **Print management setup** page, select the **Module - accounts receivable \> Documents \> Free text invoice \> Original** record.

    1.  In the **Report format** field, instead of **FreeTextInvoice.Report** select **Free text invoice (Excel)**.
    2.  Select the **Destination** button.
    3.  On the **Electronic reporting named destination** page, in the **Name** field, enter **Main destination**.
    4.  Select **Save**.
    5.  In the **File destination** Fast tab, [configure](er-destination-type-email.md) the **Email** destination for the **Report** component.
    6.  Close the **Electronic reporting named destination** page.
    7.  On the **Print management setup** page, in the **Destination name** field, select the **Main destination** named destination.

    ![Print management setup page that is used to configure named ER destinations for the selected ER format and to assign a named detination for the configured print management record.](./media/er-named-destinations-01.gif)

    > You configured the named ER destination **Main destination** for the **Free text invoice (Excel)** format and assign this destination to the **Module - accounts receivable \> Documents \> Free text invoice \> Original** PM record.

5. On the **Print management setup** page, select the **Module - accounts receivable \> Account - US-001 \> Free text invoice \> Original** record.

    1.  Do right mouse click and select **Override**.
    2.  Select the **Destination** button.
    3.  Select the **Destination** button.
    4.  On the **Electronic reporting named destination** page, on the Action Pane, select **New**.
    5.  In the **Name** field, enter **US-001 destination**.
    6.  In the **File destination** Fast tab, [configure](er-destination-type-print.md) the **Printer** destination for the **Report** component.
    7.  Close the **Electronic reporting named destination** page.
    8.  On the **Print management setup** page, in the **Destination name** field, select the **US-001 destination** named destination.

    > You configured the named ER destination **US-001 destination** for the **Free text invoice (Excel)** format and assign this destination to the **Module - accounts receivable \> Account - US-001 \> Free text invoice \> Original** PM record.

    ![Print management setup page that is used to configure named ER destinations for the selected ER format and to assign a named detination for the configured print management record.](./media/er-named-destinations-02.gif)

With this setting, the following will happen when a free text invoice is generated:

- When a free text invoice of other than US-001 customer is processed, the **Free text invoice (Excel)** ER format is executed and a generated document is sent out via email.
- Otherwise, the same **Free text invoice (Excel)** ER format is executed but a generated document is printed out.

> [!NOTE]
> When the named destination has not been defined for a print management record that is processed at runtime, the default ER destinations are used when thay are available for the running ER format.

> [!IMPORTANT]
> When you go to **Organization administration \> Electronic reporting \> Electronic reporting destination** to open the **Electronic reporting destination** page and select an ER format for which at least one named destination was configured, you will be notified about presence of named destinations. Please, note that when you delete this default destination, all named destinations will be also deleted. If those named destinations were selected for some PM records, this selection will be revoked.
>
> ![Electronic reporting destination page that informs user that some named destinations were configured for an ER format that is currently selected on this page](./media/er-named-destinations-03.png)

## Copy an existing ER destination as a new named one

When the default ER destination is available for an ER format, it can be used as a template for newly created named ER destination. To create a new nemed ER destination based on the default one, select the **Copy from default** button on the **Electronic reporting named destination** page - a new named destination with the name **Default** is added. You can repeat this step many times if needed.

You can select any of existing named destination as a template for making a new named destination. To create a new nemed ER destination based on the selected named one, select the **Copy** button on the **Electronic reporting named destination** page - a new named destination that is named as the selected one with added suffix **Copy** is added. You can repeat this step many times if needed.

## Applicability

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Electronic reporting framework API changes for Application update 10.0.17](er-apis-app10-0-17.md)

[Electronic reporting framework API changes for Application update 10.0.21](er-apis-app10-0-21.md)

[Change code to enable users to configure and use named ER destinations](er-api-named-destinations.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
