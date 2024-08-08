---
title: Extend export control license functionality
description: Learn about what's useful for developers who are extending license functionality for implementing export controls with an outline on license evaluations.
author: t-benebo
ms.author: benebotg
ms.topic: overview
ms.date: 08/29/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Extend export control license functionality

This article provides information that's useful for developers who are extending license functionality for implementing export controls.

License information is stored in the `msdyn_exportcontrollicense` table. Tracking of licenses is provided only as it pertains to export control. It should not be considered a general-purpose license management subsystem.

## License evaluation

All license checks occur at the document line level. A single document can contain lines that reference multiple licenses. When the system evaluates a license, the same evaluation that's used for restriction and exception rules is performed. The evaluation considers any field that has a value in the license definition. It ignores fields that don't have a value. As is the case for rules, the license is considered valid only if the value matches the line that's being processed.

The document date is compared against the license's valid-from and valid-to dates, if they're provided. To perform the check based on the current date instead of the document date, either use a Power Fx rule or pass the current date in the document that's being analyzed. The **Expected export date** field of the license has no impact and is provided only for reference. However, it can be referenced from Power Fx rules.

A license can be provided at either the document level or the line level. The assumption is that a document-level license is by default on all lines. It's overridden if a license is provided on a specific line.

## License lines and consumption

The Export Control Classification Number (ECCN) from the license line must match the ECCN from the document line that references the license. If no line in the license has a matching ECCN, the check fails, and the license issues collection contains a reference to the missing license.

The following three properties on the export control check call control how license consumption is handled:

- `"msdyn_ExportControlSourceApplication": "Supply Chain"`
- `"msdyn_ExportControlSourceDocument": "SO1347134"`
- `"msdyn_DecrementLicenseQuantity": true`

Consumption is tracked in the `msdyn_exportcontrollicenselineconsumption` table. The `SourceApplication` and `SourceDocument` fields are used to reference which incoming document from an external system has consumed the quantity or value. If you specify *true* for `msdyn_DecrementLicenseQuantity`, rows are written in the `msdyn_exportcontrollicenselineconsumption` table, and future license checks will be blocked if no quantity or value remains for that line. If the same `SourceApplication` and `SourceDocument` values are passed in again with `DecrementLicenseQuantity`, all existing decrements for that document are deleted and then re-created with the updated quantities and values. Therefore, if a sales order is updated, and a different quantity (either larger or smaller) must be reserved, all the existing values can be updated just by sending in the sales order a second time.

The consumed quantity and value are calculated as rollup fields on the license line. If no total quantity or value is provided, export control checks aren't blocked for that license line. Instead, total consumed quantity and total consumed value continue to accrue. The line value is a standard Dataverse currency field. For more information about currency fields and exchange rates, see [Using currency columns](/power-apps/maker/data-platform/types-of-fields#using-currency-columns).

License consumption is automatically computed and updated based on checks when `msdyn_DecrementLicenseQuantity` is set to *True*. However, users who have the appropriate permissions can also create, edit, or delete consumption lines directly from the `msdyn_exportcontrollicenselineconsumption` table as required. Access to view and edit this and all other tables is based on standard [Dataverse role-based security](/power-platform/admin/wp-security-cds).

## Unit and currency conversion

If a unit or currency is specified on both a license line and a related incoming document, then the system converts the unit and currency automatically. If either the document being checked or the license line doesn't specify a unit or currency, then it's assumed that the amount provided is in the same unit or currency as the license line.

If the Dynamics 365 Supply Chain Extended and Dynamics 365 Finance Extended dual-write solutions are installed on your environment, then the system converts units and currencies using the `msdyn_unitofmeasureconversion` and `msdyn_currencyexchangerate` values, respectively. If the dual-write solutions aren't installed, then the system applies the default Dataverse conversions. If a conversion for the currency or unit isn't found in existing data, then a license issue is returned and the check is blocked.

