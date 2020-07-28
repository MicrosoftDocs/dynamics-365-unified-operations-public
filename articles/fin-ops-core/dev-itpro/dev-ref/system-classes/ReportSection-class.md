---
title: ReportSection class
description: This topic describes the ReportSection class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class ReportSection

[!include [banner](../../includes/banner.md)]

```xpp
class ReportSection extends TreeNode
```

The ReportSection class contains a collection of report controls.

## Remarks

A section is printed on the report when the query for the report is executed or when the methods of the report are executed. This class lets you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. A report section can be one of the following types: prologue, page header, header, footer, page footer, epilogue, programmable section, header, body, or footer. The section template node type lets you define sections one time and then reuse them many times in different reports. A typical example of this is a check or a giro.

## Examples

The following example adds a section to a report:

```xpp
static void test(args a) 
{  
    report r; 
    reportDesign rd; 
    reportSection rs; 
    reportRun rr; 
    // Create a simple report that is not present in  
    // the Application Object Tree. 
    r = new report(); 
    rd = r.addDesign("myDesign"); 
    rs = rd.addProgrammableSection(1);  
    // Add a section triggered by execute(1). 
    rs.addTextControl("Hello world"); 
    // Run the report. 
    rr = new reportRun(r); 
    if (rr.prompt()) // Run the sysPrintForm form. 
    { 
        rr.execute(1); // Execute the programmableSection. 
        rr.print();   // Print report to the target 
                      // (for example, printer or screen) 
                      // selected during the previous prompt call. 
    } 
}
```

## Methods

| Method                                                                                       | Description                                                                                                                               |
|----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportBitmapControl addBitmapControl()                                                | Adds a bitmap control to a report section.                                                                                                |
| public ReportShapeControl addBoxControl(\[ShapeType type\])                                  | Adds a shape control to a report section.                                                                                                 |
| public ReportControl addControl(TableId tableId, FieldId fieldId, \[int arrayIndex\])        | Adds a report control to a report section.                                                                                                |
| public ReportDateControl addDateControl(TableId tableId, FieldId fieldId)                    | Adds a date control to a report section.                                                                                                  |
| public ReportDateControl addDateDisplayControl(str displayFunc, \[TableId tableId\])         | Adds a date control to a report section.                                                                                                  |
| public ReportDateTimeControl addDateTimeControl(TableId tableId, FieldId fieldId)            |                                                                                                                                           |
| public ReportDateTimeControl addDateTimeDisplayControl(str displayFunc, \[TableId tableId\]) |                                                                                                                                           |
| public ReportControl addDisplayControl(str displayFunc, \[TableId tableId\])                 |                                                                                                                                           |
| public ReportEnumControl addEnumControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportEnumControl addEnumDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportFieldGroup addFieldGroup(TableId tableId, str name)                             |                                                                                                                                           |
| public ReportGuidControl addGuidControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportGuidControl addGuidDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportInt64Control addInt64Control(TableId tableId, FieldId fieldId)                  |                                                                                                                                           |
| public ReportInt64Control addInt64DisplayControl(str displayFunc, \[TableId tableId\])       |                                                                                                                                           |
| public ReportIntegerControl addIntegerControl(TableId tableId, FieldId fieldId)              |                                                                                                                                           |
| public ReportIntegerControl addIntegerDisplayControl(str displayFunc, \[TableId tableId\])   |                                                                                                                                           |
| public ReportPromptControl addPromptControl(TableId tableId, \[FieldId fieldId\])            |                                                                                                                                           |
| public ReportRealControl addRealControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportRealControl addRealDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportSectionGroup addSection(TableId tableId, \[FieldId fieldId\])                   |                                                                                                                                           |
| public ReportShapeControl addShapeControl(\[ShapeType type\])                                |                                                                                                                                           |
| public ReportStringControl addStringControl(TableId tableId, FieldId fieldId)                |                                                                                                                                           |
| public ReportStringControl addStringDisplayControl(str displayFunc, \[TableId tableId\])     |                                                                                                                                           |
| public ReportSumControl addSumControl(TableId tableId, FieldId fieldId)                      |                                                                                                                                           |
| public ReportSumControl addSumNameControl(str name)                                          |                                                                                                                                           |
| public ReportTextControl addTextControl(str text)                                            |                                                                                                                                           |
| public ReportTimeControl addTimeControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportTimeControl addTimeDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public int arrange()                                                                         |                                                                                                                                           |
| public int arrangeMethod(\[int value\])                                                      |                                                                                                                                           |
| public int arrangeWhen(\[int value\])                                                        |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                            | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public boolean autoHeader(\[boolean value\])                                                 |                                                                                                                                           |
| public int bold(\[int value\])                                                               | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                                            |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                                                   |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                                    |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                                               |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                                                |                                                                                                                                           |
| public int bottomMode(\[int value\])                                                         |                                                                                                                                           |
| public str bottomStr(\[str value\])                                                          |                                                                                                                                           |
| public Units bottomUnit(\[Units value\])                                                     |                                                                                                                                           |
| public Real bottomValue(\[Real value\])                                                      |                                                                                                                                           |
| public int characterSet(\[int value\])                                                       | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                        | Gets or sets the color scheme of the control.                                                                                             |
| public int columnHeadingsStrategy(\[int value\])                                             |                                                                                                                                           |
| public int columns(\[int value\], \[ColumnsMode mode\])                                      |                                                                                                                                           |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                         |                                                                                                                                           |
| public int columnspaceMode(\[int value\])                                                    |                                                                                                                                           |
| public str columnspaceStr(\[str value\])                                                     |                                                                                                                                           |
| public Units columnspaceUnit(\[Units value\])                                                |                                                                                                                                           |
| public Real columnspaceValue(\[Real value\])                                                 |                                                                                                                                           |
| public int columnsValue(\[int value\])                                                       |                                                                                                                                           |
| public ReportControl control(FieldId fieldId, \[TableId tableId\])                           | Finds a control in the section, based on the control�s table and dataField properties.                                                    |
| public int controlCount()                                                                    |                                                                                                                                           |
| public ReportControl controlName(str name)                                                   | Finds a control in a section, based on the control's Name property.                                                                       |
| public ReportControl controlNo(int number)                                                   |                                                                                                                                           |
| public int controlNumber(\[int value\])                                                      |                                                                                                                                           |
| public int delete()                                                                          | Deletes the current node from the AOT.                                                                                                    |
| public str font(\[str value\])                                                               | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                           | Gets or sets the size of the font for the control to use.                                                                                 |
| public str footerText(\[str value\])                                                         |                                                                                                                                           |
| public int foregroundColor(\[int value\])                                                    | Gets or sets the text color for the control to use.                                                                                       |
| public boolean grandHeader(\[boolean value\])                                                |                                                                                                                                           |
| public boolean grandTotal(\[boolean value\])                                                 | Determines whether the FooterText property value can be displayed.                                                                        |
| public boolean hasButtons(\[boolean value\])                                                 |                                                                                                                                           |
| public int headerDetailLevel(\[int value\], \[AutoMode mode\])                               |                                                                                                                                           |
| public AutoMode headerDetailLevelMode(\[AutoMode mode\])                                     |                                                                                                                                           |
| public int headerDetailLevelValue(\[int value\])                                             |                                                                                                                                           |
| public str headerText(\[str value\])                                                         |                                                                                                                                           |
| public int height100mm(\[int height\])                                                       | Gets or sets the height of a section, excluding the height of the border and the top and bottom margins.                                  |
| public int heightmm100(\[int heightInclMargins\])                                            | Gets or sets the height of a section, including the height of the border and the top and bottom margins.                                  |
| public int heightMode(\[int value\])                                                         | Gets or sets a calculation mode for the height of the control.                                                                            |
| public str heightStr(\[str value\])                                                          |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                                     |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                                      | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                                     |                                                                                                                                           |
| public str label()                                                                           | Gets the description of the section node in the AOT.                                                                                      |
| public int labelBottomMarginMode(\[int value\])                                              |                                                                                                                                           |
| public str labelBottomMarginStr(\[str value\])                                               |                                                                                                                                           |
| public Units labelBottomMarginUnit(\[Units value\])                                          |                                                                                                                                           |
| public Real labelBottomMarginValue(\[Real value\])                                           |                                                                                                                                           |
| public int labelTopMarginMode(\[int value\])                                                 |                                                                                                                                           |
| public str labelTopMarginStr(\[str value\])                                                  |                                                                                                                                           |
| public Units labelTopMarginUnit(\[Units value\])                                             |                                                                                                                                           |
| public Real labelTopMarginValue(\[Real value\])                                              |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                                     |                                                                                                                                           |
| public int leftMarginsEtc()                                                                  |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                                      |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                                                 |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                                                  |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                                                |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                                                |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                                                 | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                                                |                                                                                                                                           |
| public TableId map(\[TableId value\])                                                        |                                                                                                                                           |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int noOfHeadingLines(\[int value\], \[AutoMode mode\])                                |                                                                                                                                           |
| public AutoMode noOfHeadingLinesMode(\[AutoMode mode\])                                      |                                                                                                                                           |
| public int noOfHeadingLinesValue(\[int value\])                                              |                                                                                                                                           |
| public str resolutionX(\[str value\])                                                        |                                                                                                                                           |
| public int resolutionXStr(str value)                                                         |                                                                                                                                           |
| public Units resolutionXUnit(\[Units value\])                                                |                                                                                                                                           |
| public str resolutionY(\[str value\])                                                        |                                                                                                                                           |
| public int resolutionYStr(str value)                                                         |                                                                                                                                           |
| public Units resolutionYUnit(\[Units value\])                                                |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                                    |                                                                                                                                           |
| public int rightMarginsEtc()                                                                 |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                                     |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                                                |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                                                 |                                                                                                                                           |
| public int ruler(\[int value\])                                                              |                                                                                                                                           |
| public ReportSectionGroup sectionGroup(TableId tableId, \[FieldId fieldId\])                 | Finds an existing section group in the generated design.                                                                                  |
| public ReportBlockType sectionType()                                                         | Retrieves the type of a given report section, such as ReportBlockType::Prolog, ReportBlockType::PageHeader, or ReportBlockType::Body.     |
| public int sumDetailLevel(\[int value\], \[AutoMode mode\])                                  |                                                                                                                                           |
| public AutoMode sumDetailLevelMode(\[AutoMode mode\])                                        |                                                                                                                                           |
| public int sumDetailLevelValue(\[int value\])                                                |                                                                                                                                           |
| public TableId table(\[TableId value\])                                                      | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                                      |                                                                                                                                           |
| public int topMarginAndFrame()                                                               |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                                      |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                                       |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                                                  |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                                                   |                                                                                                                                           |
| public int topMode(\[int value\])                                                            |                                                                                                                                           |
| public str topStr(\[str value\])                                                             |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                                        |                                                                                                                                           |
| public Real topValue(\[Real value\])                                                         |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                  |                                                                                                                                           |
| public void columnspace(Real value, Units unit)                                              |                                                                                                                                           |
| public void bottom(Real value, Units unit)                                                   |                                                                                                                                           |
| public void labelBottomMargin(Real value, Units unit)                                        |                                                                                                                                           |
| public void labelTopMargin(Real value, Units unit)                                           |                                                                                                                                           |
| public void executeColumnHeadings()                                                          |                                                                                                                                           |
| public void executeSection()                                                                 | Prints the section on the report.                                                                                                         |
| public void rightMargin(Real value, Units unit)                                              |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                                             |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                                                |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                                               |                                                                                                                                           |
| public void top(Real value, Units unit)                                                      |                                                                                                                                           |
| public void height(Real value, Units unit)                                                   | Gets or sets the height of the control.                                                                                                   |

## Method addBitmapControl

Adds a bitmap control to a report section.

```xpp
public ReportBitmapControl addBitmapControl()
```

### Return Value - addBitmapControl

The bitmap control that is created.

## Method addBoxControl

Adds a shape control to a report section.

```xpp
public ReportShapeControl addBoxControl([ShapeType type])
```

### Parameters - addBoxControl

type  
The type of shape control to add; optional.

### Return Value - addBoxControl

The shape control that is created.

## Method addControl

Adds a report control to a report section.

```xpp
public ReportControl addControl(TableId tableId, FieldId fieldId, [int arrayIndex])
```

### Parameters - addControl

tableId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

### Return Value - addControl

The report control that is created.

### Remarks - addControl

This method adds the specified type of control, such as string, enumeration, integer, real, or date, depending on the type of the field that is specified by the arguments.

## Method addDateControl

Adds a date control to a report section.

```xpp
public ReportDateControl addDateControl(TableId tableId, FieldId fieldId)
```

### Parameters - addDateControl

tableId  
The field ID.

<!-- -->

fieldId  
The field ID.

### Return Value - addDateControl

The date control that is created.

### Examples - addDateControl

```xpp
static void test(args a) 
{ 
    reportRun rr; 
    inventTrans rec; 
    int i; 
    // Create a simple report that is not present in 
    // the Application Object Tree. 
    report r = new report(); 
    reportDesign rd = r.addDesign("myDesign"); 
    reportSection rs = rd.AddSection(reportBlockType::body,  
    tablenum(inventTrans)); 
    int t = tablenum(inventTrans); 
    int f; 
    f = fieldnum(inventTrans, datePhysical); 
    rs.addDateControl(t,f); 
    // run the report 
    rr = new reportRun(r); 
    // Run the sysPrintForm form. 
    if (rr.prompt())  
    { 
        while select rec 
            rr.send(rec); 
        // Print report to the target (e.g. printer or screen) selected during the  
        // prompt call above. 
        rr.print();  
    } 
}
```

## Method addDateDisplayControl

Adds a date control to a report section.

```xpp
public ReportDateControl addDateDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addDateDisplayControl

displayFunc  
The name of the table on which the display method is declared; optional.

<!-- -->

tableId  
The name of the table on which the display method is declared; optional.

### Return Value - addDateDisplayControl

The date control that is created.

### Remarks - addDateDisplayControl

The data control shows the result when a display method returns a date.

## Method addDateTimeControl

```xpp
public ReportDateTimeControl addDateTimeControl(TableId tableId, FieldId fieldId)
```

### Parameters - addDateTimeControl

tableId  

<!-- -->

fieldId  

### Return Value - addDateTimeControl

## Method addDateTimeDisplayControl

```xpp
public ReportDateTimeControl addDateTimeDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addDateTimeDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addDateTimeDisplayControl

## Method addDisplayControl

```xpp
public ReportControl addDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addDisplayControl

## Method addEnumControl

```xpp
public ReportEnumControl addEnumControl(TableId tableId, FieldId fieldId)
```

### Parameters - addEnumControl

tableId  

<!-- -->

fieldId  

### Return Value - addEnumControl

## Method addEnumDisplayControl

```xpp
public ReportEnumControl addEnumDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addEnumDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addEnumDisplayControl

## Method addFieldGroup

```xpp
public ReportFieldGroup addFieldGroup(TableId tableId, str name)
```

### Parameters - addFieldGroup

tableId  

<!-- -->

name  

### Return Value - addFieldGroup

## Method addGuidControl

```xpp
public ReportGuidControl addGuidControl(TableId tableId, FieldId fieldId)
```

### Parameters - addGuidControl

tableId  

<!-- -->

fieldId  

### Return Value - addGuidControl

## Method addGuidDisplayControl

```xpp
public ReportGuidControl addGuidDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addGuidDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addGuidDisplayControl

## Method addInt64Control

```xpp
public ReportInt64Control addInt64Control(TableId tableId, FieldId fieldId)
```

### Parameters - addInt64Control

tableId  

<!-- -->

fieldId  

### Return Value - addInt64Control

## Method addInt64DisplayControl

```xpp
public ReportInt64Control addInt64DisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addInt64DisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addInt64DisplayControl

## Method addIntegerControl

```xpp
public ReportIntegerControl addIntegerControl(TableId tableId, FieldId fieldId)
```

### Parameters - addIntegerControl

tableId  

<!-- -->

fieldId  

### Return Value - addIntegerControl

## Method addIntegerDisplayControl

```xpp
public ReportIntegerControl addIntegerDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addIntegerDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addIntegerDisplayControl

## Method addPromptControl

```xpp
public ReportPromptControl addPromptControl(TableId tableId, [FieldId fieldId])
```

### Parameters - addPromptControl

tableId  

<!-- -->

fieldId  

### Return Value - addPromptControl

## Method addRealControl

```xpp
public ReportRealControl addRealControl(TableId tableId, FieldId fieldId)
```

### Parameters - addRealControl

tableId  

<!-- -->

fieldId  

### Return Value - addRealControl

## Method addRealDisplayControl

```xpp
public ReportRealControl addRealDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addRealDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addRealDisplayControl

## Method addSection

```xpp
public ReportSectionGroup addSection(TableId tableId, [FieldId fieldId])
```

### Parameters - addSection

tableId  

<!-- -->

fieldId  

### Return Value - addSection

## Method addShapeControl

```xpp
public ReportShapeControl addShapeControl([ShapeType type])
```

### Parameters - addShapeControl

type  

### Return Value - addShapeControl

## Method addStringControl

```xpp
public ReportStringControl addStringControl(TableId tableId, FieldId fieldId)
```

### Parameters - addStringControl

tableId  

<!-- -->

fieldId  

### Return Value - addStringControl

## Method addStringDisplayControl

```xpp
public ReportStringControl addStringDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addStringDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addStringDisplayControl

## Method addSumControl

```xpp
public ReportSumControl addSumControl(TableId tableId, FieldId fieldId)
```

### Parameters - addSumControl

tableId  

<!-- -->

fieldId  

### Return Value - addSumControl

## Method addSumNameControl

```xpp
public ReportSumControl addSumNameControl(str name)
```

### Parameters - addSumNameControl

name  

### Return Value - addSumNameControl

## Method addTextControl

```xpp
public ReportTextControl addTextControl(str text)
```

### Parameters - addTextControl

text  

### Return Value - addTextControl

## Method addTimeControl

```xpp
public ReportTimeControl addTimeControl(TableId tableId, FieldId fieldId)
```

### Parameters - addTimeControl

tableId  

<!-- -->

fieldId  

### Return Value - addTimeControl

## Method addTimeDisplayControl

```xpp
public ReportTimeControl addTimeDisplayControl(str displayFunc, [TableId tableId])
```

### Parameters - addTimeDisplayControl

displayFunc  

<!-- -->

tableId  

### Return Value - addTimeDisplayControl

## Method arrange

```xpp
public int arrange()
```

### Return Value - arrange

## Method arrangeMethod

```xpp
public int arrangeMethod([int value])
```

### Parameters - arrangeMethod

value  

### Return Value - arrangeMethod

## Method arrangeWhen

```xpp
public int arrangeWhen([int value])
```

### Parameters - arrangeWhen

value  

### Return Value - arrangeWhen

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

### Return Value - autoDeclaration

true if the member variable can be declared for this control; otherwise, false.

### Remarks - autoDeclaration

Controls cannot have identical names.

## Method autoHeader

```xpp
public boolean autoHeader([boolean value])
```

### Parameters - autoHeader

value  

### Return Value - autoHeader

## Method bold

Gets or sets the weight of font that is used to output text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  

### Return Value - bold

An integer value between zero and nine, inclusive.

### Remarks - bold

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

## Method bottomMarginAndFrame

```xpp
public int bottomMarginAndFrame()
```

### Return Value - bottomMarginAndFrame

## Method bottomMarginMode

```xpp
public int bottomMarginMode([int value])
```

### Parameters - bottomMarginMode

value  

### Return Value - bottomMarginMode

## Method bottomMarginStr

```xpp
public str bottomMarginStr([str value])
```

### Parameters - bottomMarginStr

value  

### Return Value - bottomMarginStr

## Method bottomMarginUnit

```xpp
public Units bottomMarginUnit([Units value])
```

### Parameters - bottomMarginUnit

value  

### Return Value - bottomMarginUnit

## Method bottomMarginValue

```xpp
public Real bottomMarginValue([Real value])
```

### Parameters - bottomMarginValue

value  

### Return Value - bottomMarginValue

## Method bottomMode

```xpp
public int bottomMode([int value])
```

### Parameters - bottomMode

value  

### Return Value - bottomMode

## Method bottomStr

```xpp
public str bottomStr([str value])
```

### Parameters - bottomStr

value  

### Return Value - bottomStr

## Method bottomUnit

```xpp
public Units bottomUnit([Units value])
```

### Parameters - bottomUnit

value  

### Return Value - bottomUnit

## Method bottomValue

```xpp
public Real bottomValue([Real value])
```

### Parameters - bottomValue

value  

### Return Value - bottomValue

## Method characterSet

Gets or sets the character set of the font.

```xpp
public int characterSet([int value])
```

### Parameters - characterSet

value  

### Return Value - characterSet

An integer value that indicates the character set of the font.

### Remarks - characterSet

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of Microsoft Windows:

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows:

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows:

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

## Method colorScheme

Gets or sets the color scheme of the control.

```xpp
public int colorScheme([int value])
```

### Parameters - colorScheme

value  

### Return Value - colorScheme

An integer between zero and two, inclusive.

### Remarks - colorScheme

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

## Method columnHeadingsStrategy

```xpp
public int columnHeadingsStrategy([int value])
```

### Parameters - columnHeadingsStrategy

value  

### Return Value - columnHeadingsStrategy

## Method columns

```xpp
public int columns([int value], [ColumnsMode mode])
```

### Parameters - columns

value  

<!-- -->

mode  

### Return Value - columns

## Method columnsMode

```xpp
public ColumnsMode columnsMode([ColumnsMode mode])
```

### Parameters - columnsMode

mode  

### Return Value - columnsMode

## Method columnspaceMode

```xpp
public int columnspaceMode([int value])
```

### Parameters - columnspaceMode

value  

### Return Value - columnspaceMode

## Method columnspaceStr

```xpp
public str columnspaceStr([str value])
```

### Parameters - columnspaceStr

value  

### Return Value - columnspaceStr

## Method columnspaceUnit

```xpp
public Units columnspaceUnit([Units value])
```

### Parameters - columnspaceUnit

value  

### Return Value - columnspaceUnit

## Method columnspaceValue

```xpp
public Real columnspaceValue([Real value])
```

### Parameters - columnspaceValue

value  

### Return Value - columnspaceValue

## Method columnsValue

```xpp
public int columnsValue([int value])
```

### Parameters - columnsValue

value  

### Return Value - columnsValue

## Method control

Finds a control in the section, based on the control�s table and dataField properties.

```xpp
public ReportControl control(FieldId fieldId, [TableId tableId])
```

### Parameters - control

fieldId  
The control's table property; optional.

<!-- -->

tableId  
The control's table property; optional.

### Return Value - control

The report control that is found.

### Remarks - control

If the table ID is not supplied, the table property from the section�s parent section group is used.

## Method controlCount

```xpp
public int controlCount()
```

### Return Value - controlCount

## Method controlName

Finds a control in a section, based on the control's Name property.

```xpp
public ReportControl controlName(str name)
```

### Parameters - controlName

name  
The Name property of the control.

### Return Value - controlName

The control that is found.

## Method controlNo

```xpp
public ReportControl controlNo(int number)
```

### Parameters - controlNo

number  

### Return Value - controlNo

## Method controlNumber

```xpp
public int controlNumber([int value])
```

### Parameters - controlNumber

value  

### Return Value - controlNumber

## Method delete

Deletes the current node from the AOT.

```xpp
public int delete()
```

### Return Value - delete

## Method font

Gets or sets the name of the font for the control to use.

```xpp
public str font([str value])
```

### Parameters - font

value  

### Return Value - font

The name of the font to use, such as Tahoma or Verdana.

## Method fontSize

Gets or sets the size of the font for the control to use.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  

### Return Value - fontSize

The height of the font in points.

## Method footerText

```xpp
public str footerText([str value])
```

### Parameters - footerText

value  

### Return Value - footerText

## Method foregroundColor

Gets or sets the text color for the control to use.

```xpp
public int foregroundColor([int value])
```

### Parameters - foregroundColor

value  

### Return Value - foregroundColor

An integer that contains a packed RGB color.

### Remarks - foregroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

## Method grandHeader

```xpp
public boolean grandHeader([boolean value])
```

### Parameters - grandHeader

value  

### Return Value - grandHeader

## Method grandTotal

Determines whether the FooterText property value can be displayed.

```xpp
public boolean grandTotal([boolean value])
```

### Parameters - grandTotal

value  

### Return Value - grandTotal

true if the FooterText property value is displayed; otherwise, false.

### Remarks - grandTotal

The grandTotal property is available only when a report has unnested, multiple data sources.

## Method hasButtons

```xpp
public boolean hasButtons([boolean value])
```

### Parameters - hasButtons

value  

### Return Value - hasButtons

## Method headerDetailLevel

```xpp
public int headerDetailLevel([int value], [AutoMode mode])
```

### Parameters - headerDetailLevel

value  

<!-- -->

mode  

### Return Value - headerDetailLevel

## Method headerDetailLevelMode

```xpp
public AutoMode headerDetailLevelMode([AutoMode mode])
```

### Parameters - headerDetailLevelMode

mode  

### Return Value - headerDetailLevelMode

## Method headerDetailLevelValue

```xpp
public int headerDetailLevelValue([int value])
```

### Parameters - headerDetailLevelValue

value  

### Return Value - headerDetailLevelValue

## Method headerText

```xpp
public str headerText([str value])
```

### Parameters - headerText

value  

### Return Value - headerText

## Method height100mm

Gets or sets the height of a section, excluding the height of the border and the top and bottom margins.

```xpp
public int height100mm([int height])
```

### Parameters - height100mm

height  
The new value in 1/100 mm; optional.

### Return Value - height100mm

The height in 1/100 mm.

### Remarks - height100mm

This method acts as a heightExclBorderAndMargins method. The height that is returned corresponds to the value of the height property. Before you use this function to set the height property, make sure that the height property is not set to AUTO. Otherwise, built-in logic might recalculate the value.

## Method heightmm100

Gets or sets the height of a section, including the height of the border and the top and bottom margins.

```xpp
public int heightmm100([int heightInclMargins])
```

### Parameters - heightmm100

heightInclMargins  
The new total height of the section in 1/100 mm; optional.

### Return Value - heightmm100

The height in 1/100 mm.

### Remarks - heightmm100

This method acts as a heightInclBorderAndMargins method. Before you use this function to set the height property, make sure that the height property is not set to AUTO. Otherwise, the built-in logic might set the height. If the heightmm100 method returns 1000, the total height of the section is 10 mm.

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

The calculation mode.

### Remarks - heightMode

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

## Method heightStr

```xpp
public str heightStr([str value])
```

### Parameters - heightStr

value  

### Return Value - heightStr

## Method heightUnit

```xpp
public Units heightUnit([Units value])
```

### Parameters - heightUnit

value  

### Return Value - heightUnit

## Method heightValue

Gets or sets the height of the control.

```xpp
public Real heightValue([Real value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the exact height calculation mode is used.

## Method italic

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

## Method label

Gets the description of the section node in the AOT.

```xpp
public str label()
```

### Return Value - label

A string that contains the description of the section node.

## Method labelBottomMarginMode

```xpp
public int labelBottomMarginMode([int value])
```

### Parameters - labelBottomMarginMode

value  

### Return Value - labelBottomMarginMode

## Method labelBottomMarginStr

```xpp
public str labelBottomMarginStr([str value])
```

### Parameters - labelBottomMarginStr

value  

### Return Value - labelBottomMarginStr

## Method labelBottomMarginUnit

```xpp
public Units labelBottomMarginUnit([Units value])
```

### Parameters - labelBottomMarginUnit

value  

### Return Value - labelBottomMarginUnit

## Method labelBottomMarginValue

```xpp
public Real labelBottomMarginValue([Real value])
```

### Parameters - labelBottomMarginValue

value  

### Return Value - labelBottomMarginValue

## Method labelTopMarginMode

```xpp
public int labelTopMarginMode([int value])
```

### Parameters - labelTopMarginMode

value  

### Return Value - labelTopMarginMode

## Method labelTopMarginStr

```xpp
public str labelTopMarginStr([str value])
```

### Parameters - labelTopMarginStr

value  

### Return Value - labelTopMarginStr

## Method labelTopMarginUnit

```xpp
public Units labelTopMarginUnit([Units value])
```

### Parameters - labelTopMarginUnit

value  

### Return Value - labelTopMarginUnit

## Method labelTopMarginValue

```xpp
public Real labelTopMarginValue([Real value])
```

### Parameters - labelTopMarginValue

value  

### Return Value - labelTopMarginValue

## Method leftMarginMode

```xpp
public int leftMarginMode([int value])
```

### Parameters - leftMarginMode

value  

### Return Value - leftMarginMode

## Method leftMarginsEtc

```xpp
public int leftMarginsEtc()
```

### Return Value - leftMarginsEtc

## Method leftMarginStr

```xpp
public str leftMarginStr([str value])
```

### Parameters - leftMarginStr

value  

### Return Value - leftMarginStr

## Method leftMarginUnit

```xpp
public Units leftMarginUnit([Units value])
```

### Parameters - leftMarginUnit

value  

### Return Value - leftMarginUnit

## Method leftMarginValue

```xpp
public Real leftMarginValue([Real value])
```

### Parameters - leftMarginValue

value  

### Return Value - leftMarginValue

## Method lineAbove

```xpp
public LineType lineAbove([LineType value])
```

### Parameters - lineAbove

value  

### Return Value - lineAbove

## Method lineBelow

```xpp
public LineType lineBelow([LineType value])
```

### Parameters - lineBelow

value  

### Return Valu
