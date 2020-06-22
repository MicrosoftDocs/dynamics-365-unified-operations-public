---
title: ReportDesign class
description: This topic describes the ReportDesign class.
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

# Class ReportDesign

[!include [banner](../../includes/banner.md)]

```xpp
class ReportDesign extends TreeNode
```

The ReportDesign class determines the contents of a report.

## Remarks

A ReportDesign object is a collection of ReportSection objects or SectionTemplate objects that determines the contents of a report. Each report contains a ReportDesign node in the Application Object Tree (AOT), below the Designs node. The ReportDesign node always contains a node that is named AutoDesignSpecs, and it can contain a node that is named Design, which is referred to as the generated design. A ReportDesign node should contain either one or more SectionTemplate nodes (below the AutoDesignSpecs node) or a generated design. If it contains both, only the generated design is used. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. A report that does not have a generated design offers more flexibility to the end user than a report that has a generated design. For example, a user who is running a report that does not have a generated design can decide in the query which sums to include in the report. A generated design is then created during the execution of the report, and it will contain footer sections that correspond to the user's choice. If a report has a generated design, the existence of footer sections in the generated design controls which sums are printed in the report.

## Examples

The following example creates a simple report that is not present in the AOT.

```xpp
static void test(args a) 
{  
    report r; 
    reportDesign rd; 
    reportSection rs; 
    reportRun rr; 
    r = new report(); 
    rd = r.addDesign("myDesign"); 
    // Add a section triggered by execute(1). 
    rs = rd.addProgrammableSection(1);  
    rs.addTextControl("Hello world"); 
    // Run the report. 
    rr = new reportRun(r); 
    // Run the sysPrintForm form. 
    if (rr.prompt())  
    { 
        // Execute the programmableSection. 
        rr.execute(1);  
        // Print the report to the target, such as printer or screen. 
        rr.print();    
    } 
}
```

## Methods

| Method                                                                                                 | Description                                                                                                                               |
|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportSection addProgrammableSection(int number)                                                |                                                                                                                                           |
| public ReportSection addSection(ReportBlockType sectionType, \[TableId tableId\], \[FieldId fieldId\]) | Adds a report section to a design.                                                                                                        |
| public ReportSectionGroup addSectionGroup(TableId tableId, \[FieldId fieldId\])                        | Adds a section group to a design.                                                                                                         |
| public int arrange()                                                                                   |                                                                                                                                           |
| public int arrangeWhen(\[int value\])                                                                  |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                                      | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public ReportAutoDesignSpecs autoDesignSpecs()                                                         |                                                                                                                                           |
| public ReportSection autoSection(TableId tableId, \[int number\])                                      |                                                                                                                                           |
| public int autoSectionControlCount()                                                                   |                                                                                                                                           |
| public ReportControl autoSectionControlNumber(int number)                                              |                                                                                                                                           |
| public int autoSectionCount()                                                                          |                                                                                                                                           |
| public ReportSection autoSectionNumber(int number)                                                     |                                                                                                                                           |
| public int bold(\[int value\])                                                                         | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginMode(\[int value\])                                                             |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                                              |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                                                         |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                                                          |                                                                                                                                           |
| public str caption(\[str value\])                                                                      | Gets or set the caption of the control.                                                                                                   |
| public int characterSet(\[int value\])                                                                 | Gets or sets the character set of the font.                                                                                               |
| public boolean collate(\[boolean collate\])                                                            |                                                                                                                                           |
| public int colorScheme(\[int value\])                                                                  | Gets or sets the color scheme of the control.                                                                                             |
| public ReportControl control(TableId tableId, FieldId fieldId)                                         | Finds a control in the generated design, based on the control's table and dataField properties.                                           |
| public int controlCount()                                                                              |                                                                                                                                           |
| public ReportControl controlName(str name)                                                             | Finds a control in the generated design, based on the control's Name property.                                                            |
| public ReportControl controlNumber(int number)                                                         |                                                                                                                                           |
| public int copies(\[int numberOfCopies\])                                                              |                                                                                                                                           |
| public int delete()                                                                                    | Deletes the node from the AOT.                                                                                                            |
| public str description(\[str value\])                                                                  |                                                                                                                                           |
| public str deviceName(\[str device\])                                                                  |                                                                                                                                           |
| public str driverName()                                                                                |                                                                                                                                           |
| public boolean edit()                                                                                  |                                                                                                                                           |
| public str emptyReportPrompt(\[str value\])                                                            |                                                                                                                                           |
| public int fitToPage(\[int value\])                                                                    |                                                                                                                                           |
| public str font(\[str value\])                                                                         | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                     | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                                              | Gets or sets the text color for the control to use.                                                                                       |
| public int from(\[int fromPage\])                                                                      |                                                                                                                                           |
| public int generateDesign()                                                                            |                                                                                                                                           |
| public int getNumberOfPrinters()                                                                       |                                                                                                                                           |
| public str getPrinter(int number)                                                                      |                                                                                                                                           |
| public PrintMedium getTarget()                                                                         | Returns the print medium target for the report.                                                                                           |
| public boolean hideBorder(\[boolean value\])                                                           |                                                                                                                                           |
| public boolean italic(\[boolean value\])                                                               |                                                                                                                                           |
| public str jobType(\[str value\])                                                                      |                                                                                                                                           |
| public int language(\[int value\])                                                                     |                                                                                                                                           |
| public str languageID(\[str lan\])                                                                     |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                                               |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                                                |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                                                           |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                                                            |                                                                                                                                           |
| public container loadDiskSettings()                                                                    |                                                                                                                                           |
| public str localWebMenu(\[str value\])                                                                 |                                                                                                                                           |
| public str lookupCaption(\[str lan\])                                                                  |                                                                                                                                           |
| public str lookupLabel(str label, \[str lan\])                                                         |                                                                                                                                           |
| public int makeAutoSection(\[Query query\])                                                            |                                                                                                                                           |
| public str name(\[str value\])                                                                         | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int orientation(\[int value\])                                                                  |                                                                                                                                           |
| public container pack()                                                                                | Serializes the current instance of the ReportDesign class.                                                                                |
| public container packPageSettings()                                                                    |                                                                                                                                           |
| public container packPrinterSettings()                                                                 |                                                                                                                                           |
| public container packPrintJobSettings()                                                                |                                                                                                                                           |
| public boolean pageFormatting()                                                                        |                                                                                                                                           |
| public PrinterOrientation paperOrientation(\[PrinterOrientation orientation\])                         |                                                                                                                                           |
| public int paperTray(\[int tray\])                                                                     |                                                                                                                                           |
| public int printerAttributes()                                                                         |                                                                                                                                           |
| public int printerAveragePPM()                                                                         |                                                                                                                                           |
| public str printerComment()                                                                            |                                                                                                                                           |
| public str printerDatatype()                                                                           |                                                                                                                                           |
| public int printerDefaultPriority()                                                                    |                                                                                                                                           |
| public str printerDriverName()                                                                         |                                                                                                                                           |
| public str printerLocation()                                                                           |                                                                                                                                           |
| public int printerPageHeight()                                                                         |                                                                                                                                           |
| public int printerPageWidth()                                                                          |                                                                                                                                           |
| public int printerPaper()                                                                              |                                                                                                                                           |
| public str printerParameters()                                                                         |                                                                                                                                           |
| public str printerPortName()                                                                           |                                                                                                                                           |
| public str printerPrinterName()                                                                        |                                                                                                                                           |
| public str printerPrintProcessor()                                                                     |                                                                                                                                           |
| public int printerPriority()                                                                           |                                                                                                                                           |
| public int printerQueuedJobs()                                                                         |                                                                                                                                           |
| public str printerSepFile()                                                                            |                                                                                                                                           |
| public str printerServerName()                                                                         |                                                                                                                                           |
| public boolean printerSettings(\[ReportRun reportRun\], \[int showWhat\])                              |                                                                                                                                           |
| public str printerShareName()                                                                          |                                                                                                                                           |
| public int printerStartTime()                                                                          |                                                                                                                                           |
| public int printerStatus()                                                                             |                                                                                                                                           |
| public int printerUntilTime()                                                                          |                                                                                                                                           |
| public str printFormName(\[str value\])                                                                |                                                                                                                                           |
| public PrintJobSettings printJobSettings()                                                             |                                                                                                                                           |
| public boolean removeRedundantFooters(\[boolean value\])                                               |                                                                                                                                           |
| public boolean removeRepeatedFooters(\[boolean value\])                                                |                                                                                                                                           |
| public boolean removeRepeatedHeaders(\[boolean value\])                                                |                                                                                                                                           |
| public str reportTemplate(\[str value\])                                                               |                                                                                                                                           |
| public str resolutionX(\[str value\])                                                                  |                                                                                                                                           |
| public int resolutionXStr(str value)                                                                   |                                                                                                                                           |
| public Units resolutionXUnit(\[Units value\])                                                          |                                                                                                                                           |
| public str resolutionY(\[str value\])                                                                  |                                                                                                                                           |
| public int resolutionYStr(str value)                                                                   |                                                                                                                                           |
| public Units resolutionYUnit(\[Units value\])                                                          |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                                              |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                                               |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                                                          |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                                                           |                                                                                                                                           |
| public int ruler(\[int value\])                                                                        |                                                                                                                                           |
| public boolean saveDiskSettings(container buffer)                                                      |                                                                                                                                           |
| public ReportSection section(int number)                                                               | Finds a section below the generated design node.                                                                                          |
| public int sectionCount()                                                                              |                                                                                                                                           |
| public ReportSectionGroup sectionGroup(TableId tableId, \[FieldId fieldId\])                           | Finds a reportSectionGroup object below a reportDesign object.                                                                            |
| public ReportSection sectionName(str name)                                                             |                                                                                                                                           |
| public ReportSection sectionNumber(int number)                                                         |                                                                                                                                           |
| public PrintMedium setTarget(PrintMedium target)                                                       | Sets the print medium target for the report.                                                                                              |
| public int to(\[int toPage\])                                                                          |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                                                |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                                                 |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                                                            |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                                                             |                                                                                                                                           |
| public str toString()                                                                                  | Returns a string that contains the class handle and name.                                                                                 |
| public boolean underline(\[boolean value\])                                                            |                                                                                                                                           |
| public boolean unpackPageSettings(container packedPageSetup)                                           |                                                                                                                                           |
| public boolean unpackPrinterSettings(container packedPrintSetup)                                       |                                                                                                                                           |
| public boolean unpackPrintJobSettings(container packedPrintJobSettings)                                |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                                                         |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                                                       |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                                                        |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                                                          |                                                                                                                                           |
| public void deleteDiskSettings(\[boolean allUsers\])                                                   |                                                                                                                                           |

## Method addProgrammableSection

```xpp
public ReportSection addProgrammableSection(int number)
```

### Parameters - addProgrammableSection

number  

### Return Value - addProgrammableSection

## Method addSection

Adds a report section to a design.

```xpp
public ReportSection addSection(ReportBlockType sectionType, [TableId tableId], [FieldId fieldId])
```

### Parameters - addSection

sectionType  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

<!-- -->

tableId  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

<!-- -->

fieldId  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

### Return Value - addSection

The section that is created.

### Remarks - addSection

This method creates a generated design if it does not already exist. If the sectionType parameter is set to Header, Body, or Footer, this method creates a section group if it does not already exist.

## Method addSectionGroup

Adds a section group to a design.

```xpp
public ReportSectionGroup addSectionGroup(TableId tableId, [FieldId fieldId])
```

### Parameters - addSectionGroup

tableId  
The dataField property of the section group; optional.

<!-- -->

fieldId  
The dataField property of the section group; optional.

### Return Value - addSectionGroup

The section group that is created.

### Remarks - addSectionGroup

This method creates a generated design (if it does not already exist).

## Method arrange

```xpp
public int arrange()
```

### Return Value - arrange

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

## Method autoDesignSpecs

```xpp
public ReportAutoDesignSpecs autoDesignSpecs()
```

### Return Value - autoDesignSpecs

## Method autoSection

```xpp
public ReportSection autoSection(TableId tableId, [int number])
```

### Parameters - autoSection

tableId  

<!-- -->

number  

### Return Value - autoSection

## Method autoSectionControlCount

```xpp
public int autoSectionControlCount()
```

### Return Value - autoSectionControlCount

## Method autoSectionControlNumber

```xpp
public ReportControl autoSectionControlNumber(int number)
```

### Parameters - autoSectionControlNumber

number  

### Return Value - autoSectionControlNumber

## Method autoSectionCount

```xpp
public int autoSectionCount()
```

### Return Value - autoSectionCount

## Method autoSectionNumber

```xpp
public ReportSection autoSectionNumber(int number)
```

### Parameters - autoSectionNumber

number  

### Return Value - autoSectionNumber

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

## Method caption

Gets or set the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

The string that is used as the caption of the control.

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

The value in the following table is for the Korean language edition of Microsoft Windows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

## Method collate

```xpp
public boolean collate([boolean collate])
```

### Parameters - collate

collate  

### Return Value - collate

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

## Method control

Finds a control in the generated design, based on the control's table and dataField properties.

```xpp
public ReportControl control(TableId tableId, FieldId fieldId)
```

### Parameters - control

tableId  
The dataField property of the control.

<!-- -->

fieldId  
The dataField property of the control.

### Return Value - control

The control that is found.

### Examples - control

```xpp
reportDesign rd = ...; 
reportControl rc = rd.control(tablenum(CustGroup), 
    fieldnum(CustGroup, Name));
```

## Method controlCount

```xpp
public int controlCount()
```

### Return Value - controlCount

## Method controlName

Finds a control in the generated design, based on the control's Name property.

```xpp
public ReportControl controlName(str name)
```

### Parameters - controlName

name  
The Name property of the control, expressed as a string.

### Return Value - controlName

The control that is found.

## Method controlNumber

```xpp
public ReportControl controlNumber(int number)
```

### Parameters - controlNumber

number  

### Return Value - controlNumber

## Method copies

```xpp
public int copies([int numberOfCopies])
```

### Parameters - copies

numberOfCopies  

### Return Value - copies

## Method delete

Deletes the node from the AOT.

```xpp
public int delete()
```

### Return Value - delete

An integer.

## Method description

```xpp
public str description([str value])
```

### Parameters - description

value  

### Return Value - description

## Method deviceName

```xpp
public str deviceName([str device])
```

### Parameters - deviceName

device  

### Return Value - deviceName

## Method driverName

```xpp
public str driverName()
```

### Return Value - driverName

## Method edit

```xpp
public boolean edit()
```

### Return Value - edit

## Method emptyReportPrompt

```xpp
public str emptyReportPrompt([str value])
```

### Parameters - emptyReportPrompt

value  

### Return Value - emptyReportPrompt

## Method fitToPage

```xpp
public int fitToPage([int value])
```

### Parameters - fitToPage

value  

### Return Value - fitToPage

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

## Method from

```xpp
public int from([int fromPage])
```

### Parameters - from

fromPage  

### Return Value - from

## Method generateDesign

```xpp
public int generateDesign()
```

### Return Value - generateDesign

## Method getNumberOfPrinters

```xpp
public int getNumberOfPrinters()
```

### Return Value - getNumberOfPrinters

## Method getPrinter

```xpp
public str getPrinter(int number)
```

### Parameters - getPrinter

number  

### Return Value - getPrinter

## Method getTarget

Returns the print medium target for the report.

```xpp
public PrintMedium getTarget()
```

### Return Value - getTarget

The target for the report.

## Method hideBorder

```xpp
public boolean hideBorder([boolean value])
```

### Parameters - hideBorder

value  

### Return Value - hideBorder

## Method italic

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

## Method jobType

```xpp
public str jobType([str value])
```

### Parameters - jobType

value  

### Return Value - jobType

## Method language

```xpp
public int language([int value])
```

### Parameters - language

value  

### Return Value - language

## Method languageID

```xpp
public str languageID([str lan])
```

### Parameters - languageID

lan  

### Return Value - languageID

## Method leftMarginMode

```xpp
public int leftMarginMode([int value])
```

### Parameters - leftMarginMode

value  

### Return Value - leftMarginMode

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

## Method loadDiskSettings

```xpp
public container loadDiskSettings()
```

### Return Value - loadDiskSettings

## Method localWebMenu

```xpp
public str localWebMenu([str value])
```

### Parameters - localWebMenu

value  

### Return Value - localWebMenu

## Method lookupCaption

```xpp
public str lookupCaption([str lan])
```

### Parameters - lookupCaption

lan  

### Return Value - lookupCaption

## Method lookupLabel

```xpp
public str lookupLabel(str label, [str lan])
```

### Parameters - lookupLabel

label  

<!-- -->

lan  

### Return Value - lookupLabel

## Method makeAutoSection

```xpp
public int makeAutoSection([Query query])
```

### Parameters - makeAutoSection

query  

### Return Value - makeAutoSection

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method orientation

```xpp
public int orientation([int value])
```

### Parameters - orientation

value  

### Return Value - orientation

## Method pack

Serializes the current instance of the ReportDesign class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the ReportDesign class.

## Method packPageSettings

```xpp
public container packPageSettings()
```

### Return Value - packPageSettings

## Method packPrinterSettings

```xpp
public container packPrinterSettings()
```

### Return Value - packPrinterSettings

## Method packPrintJobSettings

```xpp
public container packPrintJobSettings()
```

### Return Value - packPrintJobSettings

## Method pageFormatting

```xpp
public boolean pageFormatting()
```

### Return Value - pageFormatting

## Method paperOrientation

```xpp
public PrinterOrientation paperOrientation([PrinterOrientation orientation])
```

### Parameters - paperOrientation

orientation  

### Return Value - paperOrientation

## Method paperTray

```xpp
public int paperTray([int tray])
```

### Parameters - paperTray

tray  

### Return Value - paperTray

## Method printerAttributes

```xpp
public int printerAttributes()
```

### Return Value - printerAttributes

## Method printerAveragePPM

```xpp
public int printerAveragePPM()
```

### Return Value - printerAveragePPM

## Method printerComment

```xpp
public str printerComment()
```

### Return Value - printerComment

## Method printerDatatype

```xpp
public str printerDatatype()
```

### Return Value - printerDatatype

## Method printerDefaultPriority

```xpp
public int printerDefaultPriority()
```

### Return Value - printerDefaultPriority

## Method printerDriverName

```xpp
public str printerDriverName()
```

### Return Value - printerDriverName

## Method printerLocation

```xpp
public str printerLocation()
```

### Return Value - printerLocation

## Method printerPageHeight

```xpp
public int printerPageHeight()
```

### Return Value - printerPageHeight

## Method printerPageWidth

```xpp
public int printerPageWidth()
```

### Return Value - printerPageWidth

## Method printerPaper

```xpp
public int printerPaper()
```

### Return Value - printerPaper

## Method printerParameters

```xpp
public str printerParameters()
```

### Return Value - printerParameters

## Method printerPortName

```xpp
public str printerPortName()
```

### Return Value - printerPortName

## Method printerPrinterName

```xpp
public str printerPrinterName()
```

### Return Value - printerPrinterName

## Method printerPrintProcessor

```xpp
public str printerPrintProcessor()
```

### Return Value - printerPrintProcessor

## Method printerPriority

```xpp
public int printerPriority()
```

### Return Value - printerPriority

## Method printerQueuedJobs

```xpp
public int printerQueuedJobs()
```

### Return Value - printerQueuedJobs

## Method printerSepFile

```xpp
public str printerSepFile()
```

### Return Value - printerSepFile

## Method printerServerName

```xpp
public str printerServerName()
```

### Return Value - printerServerName

## Method printerSettings

```xpp
public boolean printerSettings([ReportRun reportRun], [int showWhat])
```

### Parameters - printerSettings

reportRun  

<!-- -->

showWhat  

### Return Value - printerSettings

## Method printerShareName

```xpp
public str printerShareName()
```

### Return Value - printerShareName

## Method printerStartTime

```xpp
public int printerStartTime()
```

### Return Value - printerStartTime

## Method printerStatus

```xpp
public int printerStatus()
```

### Return Value - printerStatus

## Method printerUntilTime

```xpp
public int printerUntilTime()
```

### Return Value - printerUntilTime

## Method printFormName

```xpp
public str printFormName([str value])
```

### Parameters - printFormName

value  

### Return Value - printFormName

## Method printJobSettings

```xpp
public PrintJobSettings printJobSettings()
```

### Return Value - printJobSettings

## Method removeRedundantFooters

```xpp
public boolean removeRedundantFooters([boolean value])
```

### Parameters - removeRedundantFooters

value  

### Return Value - removeRedundantFooters

## Method removeRepeatedFooters

```xpp
public boolean removeRepeatedFooters([boolean value])
```

### Parameters - removeRepeatedFooters

value  

### Return Value - removeRepeatedFooters

## Method removeRepeatedHeaders

```xpp
public boolean removeRepeatedHeaders([boolean value])
```

### Parameters - removeRepeatedHeaders

value  

### Return Value - removeRepeatedHeaders

## Method reportTemplate

```xpp
public str reportTemplate([str value])
```

### Parameters - reportTemplate

value  

### Return Value - reportTemplate

## Method resolutionX

```xpp
public str resolutionX([str value])
```

### Parameters - resolutionX

value  

### Return Value - resolutionX

## Method resolutionXStr

```xpp
public int resolutionXStr(str value)
```

### Parameters - resolutionXStr

value  

### Return Value - resolutionXStr

## Method resolutionXUnit

```xpp
public Units resolutionXUnit([Units value])
```

### Parameters - resolutionXUnit

value  

### Return Value - resolutionXUnit

## Method resolutionY

```xpp
public str resolutionY([str value])
```

### Parameters - resolutionY

value  

### Return Value - resolutionY

## Method resolutionYStr

```xpp
public int resolutionYStr(str value)
```

### Parameters - resolutionYStr

value  

### Return Value - resolutionYStr

## Method resolutionYUnit

```xpp
public Units resolutionYUnit([Units value])
```

### Parameters - resolutionYUnit

value  

### Return Value - resolutionYUnit

## Method rightMarginMode

```xpp
public int rightMarginMode([int value])
```

### Parameters - rightMarginMode

value  

### Return Value - rightMarginMode

## Method rightMarginStr

```xpp
public str rightMarginStr([str value])
```

### Parameters - rightMarginStr

value  

### Return Value - rightMarginStr

## Method rightMarginUnit

```xpp
public Units rightMarginUnit([Units value])
```

### Parameters - rightMarginUnit

value  

### Return Value - rightMarginUnit

## Method rightMarginValue

```xpp
public Real rightMarginValue([Real value])
```

### Parameters - rightMarginValue

value  

### Return Value - rightMarginValue

## Method ruler

```xpp
public int ruler([int value])
```

### Parameters - ruler

value  

### Return Value - ruler

## Method saveDiskSettings

```xpp
public boolean saveDiskSettings(container buffer)
```

### Parameters - saveDiskSettings

buffer  

### Return Value - saveDiskSettings

## Method section

Finds a section below the generated design node.

```xpp
public ReportSection section(int number)
```

### Parameters - section

number  
The section number.

### Return Value - section

The report section that is found.

## Method sectionCount

```xpp
public int sectionCount()
```

### Return Value - sectionCount

## Method sectionGroup

Finds a reportSectionGroup object below a reportDesign object.

```xpp
public ReportSectionGroup sectionGroup(TableId tableId, [FieldId fieldId])
```

### Parameters - sectionGroup

tableId  
The field of the section group; optional.

<!-- -->

fieldId  
The field of the section group; optional.

### Return Value - sectionGroup

The section group that matches the arguments.

### Examples - sectionGroup

The following example finds the section group that is created by the addSection method:

```xpp
static void test(args a) 
{ 
    reportRun rr; 
    inventTrans rec; 
    int i; 
    int t = tablenum(inventTrans); 
    int f = fieldnum(inventTrans, datePhysical); 
    // Create a simple report that is not present in 
    // the Application Object Tree. 
    report r = new report(); 
    reportDesign rd = r.addDesign("myDesign"); 
    reportSectionGroup rsg; 
    reportSection rs = rd.AddSection(reportBlockType::body, t); 
    rs.addControl(t,f); 
    rsg = rd.SectionGroup(t); 
    if (rsg) 
    { 
        rs = rsg.AddSection(ReportBlockType::Header); 
        rs.AddTextControl("This is the groupHeader"); 
    } 
    // Run the report. 
    rr = new reportRun(r); 
    // Run the sysPrintForm form 
    if (rr.prompt()) 
    { 
        select rec; 
        rr.send(rec); 
        // Print the report to the target, such as printer or screen, that  
        // was selected during the prompt call above. 
        rr.print();  
    } 
}
```

## Method sectionName

```xpp
public ReportSection sectionName(str name)
```

### Parameters - sectionName

name  

### Return Value - sectionName

## Method sectionNumber

```xpp
public ReportSection sectionNumber(int number)
```

### Parameters - sectionNumber

number  

### Return Value - sectionNumber

## Method setTarget

Sets the print medium target for the report.

```xpp
public PrintMedium setTarget(PrintMedium target)
```

### Parameters - setTarget

target  
The print medium for the report.

### Return Value - setTarget

The print medium for the report.

### Remarks - setTarget

To select a specific printer as the target for the report, call the PrintJobSettings.deviceName method on the object that is returned by the ReportDesign.printJobSettings method.

## Method to

```xpp
public int to([int toPage])
```

### Parameters - to

toPage  

### Return Value - to

## Method topMarginMode

```xpp
public int topMarginMode([int value])
```

### Parameters - topMarginMode

value  

### Return Value - topMarginMode

## Method topMarginStr

```xpp
public str topMarginStr([str value])
```

### Parameters - topMarginStr

value  

### Return Value - topMarginStr

## Method topMarginUnit

```xpp
public Units topMarginUnit([Units value])
```

### Parameters - topMarginUnit

value  

### Return Value - topMarginUnit

## Method topMarginValue

```xpp
public Real topMarginValue([Real value])
```

### Parameters - topMarginValue

value  

### Return Value - topMarginValue

## Method toString

Returns a string that contains the class handle and name.

```xpp
public str toString()
```

### Return Value - toString

A textual description of the class.

### Remarks - toString

In some classes, additional information is returned in the string.

## Method underline

```xpp
public boolean underline([boolean value])
```

### Parameters - underline

value  

### Return Value - underline

## Method unpackPageSettings

```xpp
public boolean unpackPageSettings(container packedPageSetup)
```

### Parameters - unpackPageSettings

packedPageSetup  

### Return Value - unpackPageSettings

## Method unpackPrinterSettings

```xpp
public boolean unpackPrinterSettings(container packedPrintSetup)
```

### Parameters - unpackPrinterSettings

packedPrintSetup  

### Return Value - unpackPrinterSettings

## Method unpackPrintJobSettings

```xpp
public boolean unpackPrintJobSettings(container packedPrintJobSettings)
```

### Parameters - unpackPrintJobSettings

packedPrintJobSettings  

### Return Value - unpackPrintJobSettings

## Method leftMargin

```xpp
public void leftMargin(Real value, Units unit)
```

### Parameters - leftMargin

value  

<!-- -->

unit  

## Method bottomMargin

```xpp
public void bottomMargin(Real value, Units unit)
```

### Parameters - bottomMargin

value  

<!-- -->

unit  

## Method rightMargin

```xpp
public void rightMargin(Real value, Units unit)
```

### Parameters - rightMargin

value  

<!-- -->

unit  

## Method topMargin

```xpp
public void topMargin(Real value, Units unit)
```

### Parameters - topMargin

value  

<!-- -->

unit  

## Method deleteDiskSettings

```xpp
public void deleteDiskSettings([boolean allUsers])
```

### Parameters - deleteDiskSettings

allUsers  

