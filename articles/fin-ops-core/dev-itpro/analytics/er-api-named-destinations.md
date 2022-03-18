---
# required metadata

title: Change code to enable users to configure and use named ER destinations
description: This topic describes how the Electronic reporting (ER) API can be used to enable users to configure and use named ER destinations.
author: NickSelin
ms.date: 08/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERFormatDestinationTable
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-08-01
ms.dyn365.ops.version: 10.0.21
---

# Change code to enable users to configure and use named ER destinations

[!include [banner](../includes/banner.md)]

To generate an [outbound document](general-electronic-reporting.md#configuring-data-model-mappings-for-outgoing-documents), you must run an ER format mapping. When the [initial](er-apis-app73.md#code-to-run-a-format-mapping-for-data-export) API of the ER framework is used to call an ER format mapping, all [destinations](electronic-reporting-destinations.md#applicability) that were configured for components of the format are always run. To review the sample code for a call of this type, see [Add a report service class](er-quick-start1-new-solution.md#ServiceClass).

You can also configure [action-dependent ER destinations](er-action-dependent-destinations.md) for the ER format. You can then use the [extended](er-apis-app10-0-17.md#er-api-run-format-with-action-code) API of the ER framework to call an ER format mapping that provides a user action code. The action code runs only the destinations that were configured for the action that was provided.

In some cases, you must configure [print management](document-reporting-services.md) and select the same ER format for different print management records, so that you can apply different ER destinations for generated documents when you run that format. For example, you might configure print management so that it runs the same ER format to email original documents and to print document copies to a network printer. You can use the new [API](er-apis-app10-0-21.md) of the ER framework in Microsoft Dynamics 365 Finance version 10.0.21 for this purpose.

## <a name="er-api-set-print-management-record-specific-destination"></a>API to enable users to configure ER destinations that are print management record specific

Currently, you can open the **Print management setup** page for every type of business document, to specify how the business document is generated and delivered. For every available record of the print management tree, you can perform the following actions:

- Use the **Report format** field to select either a SQL Server Reporting Services (SSRS) report or an ER format that will be run.
- Use the **Destination** button to open the **Print destination settings** dialog box, so that you can change the destination of the generated report.
- Review the **Destination** field, which shows the defined destination.

> [!IMPORTANT]
> If an ER format is selected in the **Report format** field, the configured SSRS destination won't be applied for a generated report.

You can change this behavior and configure ER destinations that are specific to a print management record. Unlike general ER destination, these destinations are named. A single named destination can be selected for several print management records. For more information, see [Configure print management record-specific ER destinations](er-named-destinations.md).

First, you must turn on the **Allow to set up ER destinations per print management item** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) workspace.

Next, you must enable users to configure print management record–specific ER destinations for a specific type of business document, if this functionality isn't enabled by default. In Finance version 10.0.21, the functionality isn't enabled for every type of business document, because the `isNamedDestinationEnabledByDocumentType` method of the `ERNamedDestinationReportEnabler` class returns *false* for any `PrintMgmtDocumentType` document type that is provided. 

```xpp
/// <summary>Class for enabling NamedDestinationFeature for current document type.</summary>
/// <remarks>To enable the document type you should wrap a <c>isNamedDestinationEnabledByDocumentType</c> method.</remarks>
public class ERNamedDestinationReportEnabler
{
    /// <summary>Checks that feature enabled for current document type. Make extension for this method.</summary>
    /// <param name = "_typeId">Print mgmt document type</param>
    /// <returns>True if feature enabled.</returns>
    [Wrappable(true), SuppressBPWarning('BPParameterNotUsed', 'Required by signature')]
    public static boolean isNamedDestinationEnabledByDocumentType(PrintMgmtDocumentType _typeId)
    {
        return false;
    }
}
```

You must wrap the `isNamedDestinationEnabledByDocumentType` method for a specific document type to enable users to configure print management record–specific ER destinations for documents of that type. The following example shows how to enable the functionality for free text invoices.

```xpp
[ExtensionOf(classStr(ERNamedDestinationReportEnabler))]
final class ERNamedDestinationReportEnablerContoso_Extension
{
    public static boolean isNamedDestinationEnabledByDocumentType(PrintMgmtDocumentType _typeId)
    {
        var ret = next isNamedDestinationEnabledByDocumentType(_typeid);
        if(_typeId == PrintMgmtDocumentType::SalesFreeTextInvoice)
        {
            return true;
        }
        else
        {
            return ret;
        }
    }
}
```

## <a name="er-api-pass-print-management-record-specific-destination"></a>API to run a format mapping where the destination that is provided is print management record specific

When you enable users to configure print management record–specific destinations, the expectation is that a named destination is configured for a print management record. When the print management record is used to run an ER format and generate an outbound document, you must pass that named destination to the ER framework to force ER to run only that destination, not any other destinations that might be configured for the ER format that is running. 

The following code for the `ERPrintMgmtReportFormatSubscriber` class shows how the ER framework is currently called to generate a free text invoice.

```xpp
/// <summary>
/// Runs a format mapping based on incoming arguments.
/// </summary>
/// <param name = "_args">Event arguments object.</param>
public static void runFreeTextInvoiceReport(NonSSRSPrintMgmtAdapterReportExecutedEventArgs _args)
{
    ERIFormatMappingRun formatMappingRun = ERPrintMgmtReportFormatSubscriber::buildFreeTextInvoiceReportMappingRun(_args);

    if (_args.parmArgs() && _args.parmArgs().parmEnumType() == enumNum(PrintCopyOriginal))
    {
        Args args = _args.parmArgs();
        boolean doUsePrintManagement = true;

        if (args.caller() is SalesFormLetter)
        {
            SalesFormLetter caller = args.caller();
            doUsePrintManagement = caller.usePrintManagement();
        }

        ERDestinationAction action;
        if (doUsePrintManagement || !isFlightEnabled(LocalizationFlights::ForcePrintJobSettings))
        {
            action = ReportDestinationContract::getPrintDestinationAction(args.parmEnum());
        }
        else
        {
            action = ERDestinationAction::View;
        }

        ERIFormatMappingRunWithDestinationAction mappingRunWithAction = formatMappingRun as ERIFormatMappingRunWithDestinationAction;

        if (mappingRunWithAction && action != ERDestinationAction::NoAction)
        {
            mappingRunWithAction.withDestinationAction(action);
        }
    }

    formatMappingRun.withCreatingObjectParameter(
        CustomersInvoicingModelName,
        classStr(PrintMgmtPrintSettingDetail),
        _args.parmSettingDetail());
    formatMappingRun.run();
}
```

The following example shows how you can change the sample code to use the new API to run an ER format and provide an ER named destination that is print management record specific.

```xpp
/// <summary>
/// Runs a format mapping based on incoming arguments.
/// </summary>
/// <param name = "_args">Event arguments object.</param>
public static void runFreeTextInvoiceReport(NonSSRSPrintMgmtAdapterReportExecutedEventArgs _args)
{
    ERIFormatMappingRun formatMappingRun = ERPrintMgmtReportFormatSubscriber::buildFreeTextInvoiceReportMappingRun(_args);

    if (_args.parmArgs() && _args.parmArgs().parmEnumType() == enumNum(PrintCopyOriginal))
    {
        Args args = _args.parmArgs();
        boolean doUsePrintManagement = true;

        if (args.caller() is SalesFormLetter)
        {
            SalesFormLetter caller = args.caller();
            doUsePrintManagement = caller.usePrintManagement();
        }

        ERDestinationAction action;
        if (doUsePrintManagement || !isFlightEnabled(LocalizationFlights::ForcePrintJobSettings))
        {
            action = ReportDestinationContract::getPrintDestinationAction(args.parmEnum());
        }
        else
        {
            action = ERDestinationAction::View;
        }

        ERIFormatMappingRunWithDestinationAction mappingRunWithAction = formatMappingRun as ERIFormatMappingRunWithDestinationAction;

        if (mappingRunWithAction && action != ERDestinationAction::NoAction)
        {
            mappingRunWithAction.withDestinationAction(action);
        }

        // Check whether a named destination is provided.
        // If so, pass it to ER to specify a single destination for a generated document

        RefRecId NamedDestination;
        if (doUsePrintManagement || !isFlightEnabled(LocalizationFlights::ForcePrintJobSettings))
        {
            NamedDestination = ReportDestinationContract::getNamedDestination(args.parmEnum());
        }
        else
        {
            NamedDestination = 0;
        }

        ERIFormatMappingRunWithNamedDestination RunWithNamedDestination = formatMappingRun as ERIFormatMappingRunWithNamedDestination;

        if (RunWithNamedDestination && NamedDestination)
        {
            RunWithNamedDestination.withDestinationNamed(NamedDestination);
        }
    }

    formatMappingRun.withCreatingObjectParameter(
        CustomersInvoicingModelName,
        classStr(PrintMgmtPrintSettingDetail),
         _args.parmSettingDetail());
    formatMappingRun.run();
}
```

The reference to a named destination is provided in the `NamedDestination` field of the `PrintMgmtSettings` table. You must pass this reference to the `runFreeTextInvoiceReport` method from the processed print management record that extends `ReportDestinationContract`.

## Applicability

To set up named destinations and force the ER framework to use the named destination that is provided, you must first turn on the **Allow to set up ER destinations per print management item** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) workspace.

The named ER destinations for all types of business documents that can be generated in Finance by using the ER framework are enabled. For more information, see the **Configurable business documents – specific destinations via printer management settings in the reports** feature in the "Globalization" section for the "Dynamics 365 Finance" application in the Dynamics 365 and industry clouds release plan for the [2021 release wave 2](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Configure action-dependent ER destinations](er-action-dependent-destinations.md)

[Configure print management record-specific ER destinations](er-named-destinations.md)

[Electronic reporting framework API changes for Application update 10.0.21](er-apis-app10-0-21.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
