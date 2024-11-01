---
title: Extend export control sales order functionality
description: Learn about what's useful for developers who are extending sales order functionality for implementing export controls with an outline on extended properties.
author: sgmsft
ms.author: shwgarg
ms.topic: overview
ms.date: 08/29/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Extend export control sales order functionality

This article provides information that's useful for developers who are extending sales order functionality for implementing export controls.

During confirmation and similar posting steps, the system tracks the history of export control checks. You can view this history from the sales order header by selecting **Result**. The details of the check that was performed are shown. This data is available for reference from reports and other processes in the `COOExportControlSalesTableHistory` table. This table also provides helper methods for accessing common information.

The document-level *de minimis* threshold value is **not** computed. By default, it's always *0* (zero). To provide a computation of the document-level *de minimis* threshold value, extend the `COOValidateSalesTable::createRequest()` API.

The `SalesLine.QtyOrdered` field is passed for the quantity, and the `SalesLine.LineAmount` field is passed for the value. No currency conversion is performed on these values. To override and pass different values, extend the `COOValidateSalesTable::createRequest()` method to update the values. The *de minimis* percentage from the associated item is passed for the line, without calculation.

## Extended properties

Additional properties can be added to requests from Supply Chain Management to the advanced export management solution. These properties can then be referenced in Power Fx rules on both restrictions and exceptions.

To add additional properties, create a chain of command extension of the `COOValidateSalesTable` class and override the appropriate method for your property.

- **Document properties:** `getExtendedProperties()`
- **Line properties:** `getExtendedLineProperties()`
- **Line code properties:** `getExtendedLineCodeProperties()`

Each of these methods contains a map named `_extendedProperties`. Add the physical name of the property and the value. For a given document part and property name, you must always use the same value type. For example, the property `TestProp` can't be of type `string` on one call and type `int` on the next call. Here is an example that adds properties to the document, line, and line code:

```xpp
[ExtensionOf(classStr(COOValidateSalesTable))]
final class COOValidateSalesTable_SampleModel_Extension
{
    public void getExtendedProperties(Map _extendedProperties)
    {
        _extendedProperties.add("TestDocString", strFmt("SalesId = %1", this.parmSalesTable().SalesId));
        _extendedProperties.add("TestDocInt", 42);
        _extendedProperties.add("TestDocReal", 3.14159);
        _extendedProperties.add("TestDocDate", today());
        _extendedProperties.add("TestDocUtcDateTime", DateTimeUtil::utcNow());
        next getExtendedProperties(_extendedProperties);
    }
    public void getExtendedLineProperties(Map _extendedProperties, COOValidationRequestLineContract _line)
    {
        _extendedProperties.add("TestLineString", strFmt("LineRecId = %1", _line.parmRecordId()));
        _extendedProperties.add("TestLineInt", 43);
        _extendedProperties.add("TestLineReal", 3.14159);
        _extendedProperties.add("TestLineDate", today());
        _extendedProperties.add("TestLineUtcDateTime", DateTimeUtil::utcNow());
        next getExtendedLineProperties(_extendedProperties, _line);
    }
    public void getExtendedLineCodeProperties(Map _extendedProperties, COOValidationRequestLineContract _line, COOValidationRequestCodeContract _code)
    {
        _extendedProperties.add("TestLineCodeString", strFmt("Code = %1", _code.parmCode()));
        _extendedProperties.add("TestLineCodeInt", 44);
        _extendedProperties.add("TestLineCodeReal", 3.14159);
        _extendedProperties.add("TestLineCodeDate", today());
        _extendedProperties.add("TestLineCodeUtcDateTime", DateTimeUtil::utcNow());
        next getExtendedLineCodeProperties(_extendedProperties, _line, _code);
    }
}
```

The first time a new property is used in an export control check, that property is added to the `msdyn_ExportControlExtendedProperty` table in the export control solution. After that, the property may be referenced in Power Fx rules. Properties can also be pre-added to this table prior to performing any checks. Here is an example of a Power Fx rule that makes use of the mentioned extension properties:

`And(And(Document.TestDocInt=42, Line.TestLineInt=43), LineCode.TestLineCodeInt=44`
