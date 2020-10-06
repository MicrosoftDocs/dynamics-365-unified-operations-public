---
title: ReportRun class
description: This topic describes the ReportRun class.
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

# Class ReportRun

[!include [banner](../../includes/banner.md)]

```xpp
class ReportRun extends ObjectRun
```

The ReportRun class generates and prints a report or previews a report on the screen.

## Remarks

As opposed to the , which defines the structure of a report, a ReportRun object contains the runtime characteristics of the report. A ReportRun object can be created by using one of the following arguments:

-   An Args object where the name and optionally designName parameters are specified.
-   A created container, by using the for example.
-   The report name and an optional design name.

The section template node type allows the sections to be defined once and reuse them many times in different reports. A typical example of this would be a check or a giro.

## Examples

The following example runs the Customer design of the existing Cust report:

```xpp
static void testReportRun(args a) 
{  
    reportRun rr; 
    args aa = new args("Cust"); 
    aa.designName("Customer"); 
    rr = new reportRun(aa); 
    rr.run(); 
}
```

## Methods

| Method                                                                                                                                                    | Description                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean allPages(\[boolean all\])                                                                                                                  |                                                                                                                                                   |
| public boolean callMenuFunction(xMenuFunction menuFunction)                                                                                               |                                                                                                                                                   |
| public str caption(str reportSpelling, str reportName, str designCaption, str designName)                                                                 | Creates a caption when previewing a report, or a document name when printing a report.                                                            |
| public boolean collate(\[boolean collate\])                                                                                                               |                                                                                                                                                   |
| public TableId columnHeadings(\[TableId tableId\])                                                                                                        | Provides control of column headings in a report.                                                                                                  |
| public ReportControl control()                                                                                                                            | Retrieves the control that is being executed.                                                                                                     |
| public int copies(\[int numberOfCopies\])                                                                                                                 |                                                                                                                                                   |
| public int copiesTotal()                                                                                                                                  | Enables marking copies of reports.                                                                                                                |
| public int copy()                                                                                                                                         | Returns the number of the copy of a report.                                                                                                       |
| public str copyDescription()                                                                                                                              |                                                                                                                                                   |
| public xFormRun createProgressForm()                                                                                                                      | Creates the form that contains progress information.                                                                                              |
| public int currentYmm100()                                                                                                                                |                                                                                                                                                   |
| public ReportDesign design(\[AnyType nameOrReportDesign\])                                                                                                | Gets or sets the name of the design.                                                                                                              |
| public str deviceName(\[str device\])                                                                                                                     |                                                                                                                                                   |
| public Object dialog(Object dialog)                                                                                                                       |                                                                                                                                                   |
| public str driverName()                                                                                                                                   | Returns the printer driver name.                                                                                                                  |
| public boolean enableAllBodies(\[boolean enable\])                                                                                                        |                                                                                                                                                   |
| public boolean execute(int number)                                                                                                                        | Prints the programmable sections of a report.                                                                                                     |
| public boolean executeBodyColumnHeadings(TableId tableId, \[FieldId fieldId\])                                                                            | Prints the column headings of a body section in a report.                                                                                         |
| public boolean executeColumnHeadings(ReportSection section)                                                                                               |                                                                                                                                                   |
| public boolean executeControlColumnHeadings(int number)                                                                                                   | Executes the column headings of a programmable section.                                                                                           |
| public boolean executeFooter(\[TableId tableId\], \[FieldId fieldId\])                                                                                    | Execute a footer section.                                                                                                                         |
| public boolean executeHeader(\[TableId tableId\], \[FieldId fieldId\])                                                                                    | Executes a header section.                                                                                                                        |
| public boolean executeSection(ReportSection section)                                                                                                      | Prints the specified section in the report.                                                                                                       |
| public boolean fetch()                                                                                                                                    | Executes the report query and calls the send method for the record that is found by the query.                                                    |
| public int from(\[int fromPage\])                                                                                                                         |                                                                                                                                                   |
| public int generateDesign(\[Query query\], \[int designNo\])                                                                                              |                                                                                                                                                   |
| public boolean getDeclineOverwrite()                                                                                                                      |                                                                                                                                                   |
| public int getNumberOfPrinters()                                                                                                                          |                                                                                                                                                   |
| public str getPrinter(int number)                                                                                                                         |                                                                                                                                                   |
| public str getRangeDescription(int number)                                                                                                                |                                                                                                                                                   |
| public ReportViewer getReportViewer()                                                                                                                     |                                                                                                                                                   |
| public PrintMedium getTarget()                                                                                                                            |                                                                                                                                                   |
| public boolean hasGeneratedDesign()                                                                                                                       |                                                                                                                                                   |
| public str headerDescription()                                                                                                                            |                                                                                                                                                   |
| public int heightOfPageFooters()                                                                                                                          |                                                                                                                                                   |
| public int indent()                                                                                                                                       |                                                                                                                                                   |
| public boolean isBodyEnabled(TableId tableId)                                                                                                             |                                                                                                                                                   |
| public Int64 jobId()                                                                                                                                      |                                                                                                                                                   |
| public Common last(TableId tableId)                                                                                                                       |                                                                                                                                                   |
| public int mm100Left()                                                                                                                                    |                                                                                                                                                   |
| public int mm100PageHeight()                                                                                                                              |                                                                                                                                                   |
| public str name(\[str name\])                                                                                                                             | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.                         |
| public container pack()                                                                                                                                   | Serializes the current instance of the ReportRun class.                                                                                           |
| public container packDesign()                                                                                                                             |                                                                                                                                                   |
| public container packPageSettings()                                                                                                                       |                                                                                                                                                   |
| public container packPrinterSettings()                                                                                                                    |                                                                                                                                                   |
| public container packPrintJobSettings()                                                                                                                   |                                                                                                                                                   |
| public container packSubtotalSettings()                                                                                                                   |                                                                                                                                                   |
| public int page(\[int number\])                                                                                                                           |                                                                                                                                                   |
| public boolean pageFormatting()                                                                                                                           | Displays the printer properties of the printer.                                                                                                   |
| public int pagesTotal()                                                                                                                                   |                                                                                                                                                   |
| public str passThrough(str str)                                                                                                                           |                                                                                                                                                   |
| public int pixelsLeft()                                                                                                                                   |                                                                                                                                                   |
| public int print()                                                                                                                                        | Sends the generated report to a print medium, such as a printer or the screen.                                                                    |
| public int printerAttributes()                                                                                                                            |                                                                                                                                                   |
| public int printerAveragePPM()                                                                                                                            |                                                                                                                                                   |
| public str printerComment()                                                                                                                               |                                                                                                                                                   |
| public str printerDatatype()                                                                                                                              |                                                                                                                                                   |
| public int printerDefaultPriority()                                                                                                                       |                                                                                                                                                   |
| public str printerDriverName()                                                                                                                            |                                                                                                                                                   |
| public str printerFontInfo()                                                                                                                              | Indicates which font is used to print the report.                                                                                                 |
| public str printerLocation()                                                                                                                              |                                                                                                                                                   |
| public int printerPageHeight()                                                                                                                            |                                                                                                                                                   |
| public int printerPageWidth()                                                                                                                             |                                                                                                                                                   |
| public int printerPaper()                                                                                                                                 |                                                                                                                                                   |
| public str printerParameters()                                                                                                                            |                                                                                                                                                   |
| public str printerPortName()                                                                                                                              |                                                                                                                                                   |
| public str printerPrinterName()                                                                                                                           |                                                                                                                                                   |
| public str printerPrintProcessor()                                                                                                                        |                                                                                                                                                   |
| public int printerPriority()                                                                                                                              |                                                                                                                                                   |
| public int printerQueuedJobs()                                                                                                                            |                                                                                                                                                   |
| public str printerSepFile()                                                                                                                               |                                                                                                                                                   |
| public str printerServerName()                                                                                                                            |                                                                                                                                                   |
| public boolean printerSettings(\[int showWhat\])                                                                                                          | Enables the user to select printer settings.                                                                                                      |
| public str printerShareName()                                                                                                                             |                                                                                                                                                   |
| public TimeOfDay printerStartTime()                                                                                                                       |                                                                                                                                                   |
| public int printerStatus()                                                                                                                                |                                                                                                                                                   |
| public TimeOfDay printerUntilTime()                                                                                                                       |                                                                                                                                                   |
| public PrintJobSettings printJobSettings(\[container packedPrintJobSettings\])                                                                            |                                                                                                                                                   |
| public int printSum()                                                                                                                                     |                                                                                                                                                   |
| public xFormRun progressForm(\[xFormRun form\])                                                                                                           |                                                                                                                                                   |
| public str progressInfo(int pageNo, int lineNo)                                                                                                           | Creates a string that describes how much of the report has been generated during the execution of a report every time that a section is executed. |
| public boolean prompt(\[boolean enableCopy\], \[boolean enablePages\], \[boolean enableDevice\], \[boolean enableProperties\], \[boolean enablePrintTo\]) | Prompts the user a report is run.                                                                                                                 |
| public Query query(\[Query query\])                                                                                                                       |                                                                                                                                                   |
| public QueryRun queryRun(\[QueryRun queryRun\])                                                                                                           |                                                                                                                                                   |
| public Report report()                                                                                                                                    |                                                                                                                                                   |
| public str reportUser(\[str user\])                                                                                                                       |                                                                                                                                                   |
| public int rulerCM()                                                                                                                                      |                                                                                                                                                   |
| public int rulerINCH()                                                                                                                                    |                                                                                                                                                   |
| public str screenFontInfo()                                                                                                                               |                                                                                                                                                   |
| public ReportSection section()                                                                                                                            |                                                                                                                                                   |
| public int sectionsLeft(ReportSection section)                                                                                                            |                                                                                                                                                   |
| public boolean send(Common cursor, \[int level\], \[boolean triggerOffBody\], \[boolean newPageBeforeBody\])                                              | Triggers the body sections that belong to a section group.                                                                                        |
| public PrintMedium setTarget(PrintMedium target)                                                                                                          |                                                                                                                                                   |
| public boolean showMenuFunction(xMenuFunction menuFunction)                                                                                               |                                                                                                                                                   |
| public boolean showMenuReference(WebMenu menuReference)                                                                                                   |                                                                                                                                                   |
| public str sortInfo(Common cursor)                                                                                                                        |                                                                                                                                                   |
| public Date startDate()                                                                                                                                   |                                                                                                                                                   |
| public DateTime startDateTime()                                                                                                                           |                                                                                                                                                   |
| public Date startMachineDate()                                                                                                                            |                                                                                                                                                   |
| public TimeOfDay startTime()                                                                                                                              |                                                                                                                                                   |
| public Real sum(TableId tableId, FieldId fieldId, \[int indent\])                                                                                         |                                                                                                                                                   |
| public Real sumControl(str fieldName, \[int indent\])                                                                                                     |                                                                                                                                                   |
| public Real sumControlNeg(str fieldName, \[int indent\])                                                                                                  |                                                                                                                                                   |
| public Real sumControlPos(str fieldName, \[int indent\])                                                                                                  |                                                                                                                                                   |
| public str sumDescription()                                                                                                                               |                                                                                                                                                   |
| public Real sumNeg(TableId tableId, FieldId fieldId, \[int indent\])                                                                                      |                                                                                                                                                   |
| public Real sumPos(TableId tableId, FieldId fieldId, \[int indent\])                                                                                      |                                                                                                                                                   |
| public boolean suppressReportIsEmptyMessage(\[boolean suppress\])                                                                                         |                                                                                                                                                   |
| public str title(\[str title\])                                                                                                                           | Gets or sets the print job description.                                                                                                           |
| public int to(\[int toPage\])                                                                                                                             |                                                                                                                                                   |
| public str toString()                                                                                                                                     | Returns a textual description of the class.                                                                                                       |
| public boolean unpackPageSettings(container packedPageSetup)                                                                                              |                                                                                                                                                   |
| public boolean unpackPrinterSettings(container packedPrinterSetup)                                                                                        |                                                                                                                                                   |
| public boolean unpackPrintJobSettings(container packedPrintJobSettings)                                                                                   |                                                                                                                                                   |
| public boolean unpackSubtotalSettings(container packedSubtotalSetup)                                                                                      |                                                                                                                                                   |
| public PrinterOrientation userSelectedOrientation()                                                                                                       |                                                                                                                                                   |
| public void disableBody(\[TableId tableId\])                                                                                                              |                                                                                                                                                   |
| public void attach()                                                                                                                                      |                                                                                                                                                   |
| public void new(AnyType argsOrReportOrContainer, \[str designName\], \[boolean isWebReport\])                                                             | Initializes an instance of the ReportRun class.                                                                                                   |
| public void disableSection(ReportSection section)                                                                                                         |                                                                                                                                                   |
| public void arrangeLevelGlobal()                                                                                                                          |                                                                                                                                                   |
| public void setEscapeSequence(str str)                                                                                                                    |                                                                                                                                                   |
| public void enableBody(\[TableId tableId\])                                                                                                               |                                                                                                                                                   |
| public void clearAllRangeDescriptions()                                                                                                                   |                                                                                                                                                   |
| public void header(ReportSection headerSection, TableId tableId, FieldId fieldId)                                                                         | Controls the header.                                                                                                                              |
| public void unpackDesign(container packedDesign)                                                                                                          |                                                                                                                                                   |
| public void newPage(\[boolean doPageFooter\])                                                                                                             |                                                                                                                                                   |
| public void footer(ReportSection footerSection, TableId tableId, FieldId fieldId)                                                                         | Controls the footer.                                                                                                                              |
| public void reset(\[boolean delayExceptions\])                                                                                                            | Enables a single instance of the ReportRun class to create multiple reports.                                                                      |
| public void arrangeLevelNone()                                                                                                                            |                                                                                                                                                   |
| public void run()                                                                                                                                         | Runs the report.                                                                                                                                  |
| public void gotoYmm100(\[int mm100\])                                                                                                                     |                                                                                                                                                   |
| public void disableColumnHeadings(\[TableId tableId\])                                                                                                    |                                                                                                                                                   |
| public void enablePageFooter()                                                                                                                            |                                                                                                                                                   |
| public void init()                                                                                                                                        |                                                                                                                                                   |
| public void arrangeLevelControl()                                                                                                                         |                                                                                                                                                   |
| public void disablePageFooter()                                                                                                                           |                                                                                                                                                   |
| public void addPendingSums()                                                                                                                              | Prints the relevant footers of the report.                                                                                                        |
| public void arrangeLevelSection()                                                                                                                         |                                                                                                                                                   |
| public void enableSection(ReportSection section)                                                                                                          |                                                                                                                                                   |
| public void detach()                                                                                                                                      |                                                                                                                                                   |
| public void addRangeDescription(int x, int y, str text, \[str fontName\], \[int fontSize\])                                                               |                                                                                                                                                   |
| public void finalize()                                                                                                                                    |                                                                                                                                                   |

## Method allPages

```xpp
public boolean allPages([boolean all])
```

### Parameters - allPages

all  

### Return Value - allPages

## Method callMenuFunction

```xpp
public boolean callMenuFunction(xMenuFunction menuFunction)
```

### Parameters - callMenuFunction

menuFunction  

### Return Value - callMenuFunction

## Method caption

Creates a caption when previewing a report, or a document name when printing a report.

```xpp
public str caption(str reportSpelling, str reportName, str designCaption, str designName)
```

### Parameters - caption

reportSpelling  
The name of the design.

<!-- -->

reportName  
The name of the design.

<!-- -->

designCaption  
The name of the design.

<!-- -->

designName  
The name of the design.

### Return Value - caption

A string that contains "DesignLabel - ReportSpelling" if the DesignLabel is not empty. A string that contains "ReportName(DesignName) - ReportSpelling" if the DesignLabel is empty.

### Remarks - caption

The call to the super method in this method creates a string that is used as a caption when previewing a report and as the document name when printing a report. It is recommended that you always fill out the Caption property of the report design so that the caption that is used during the preview of the report is in the actual language.

## Method collate

```xpp
public boolean collate([boolean collate])
```

### Parameters - collate

collate  

### Return Value - collate

## Method columnHeadings

Provides control of column headings in a report.

```xpp
public TableId columnHeadings([TableId tableId])
```

### Parameters - columnHeadings

tableId  
A table ID; optional.

### Return Value - columnHeadings

The last tableId value for which columnHeading objects were printed.

## Method control

Retrieves the control that is being executed.

```xpp
public ReportControl control()
```

### Return Value - control

The control that is being executed.

### Remarks - control

This method is intended for internal use.

## Method copies

```xpp
public int copies([int numberOfCopies])
```

### Parameters - copies

numberOfCopies  

### Return Value - copies

## Method copiesTotal

Enables marking copies of reports.

```xpp
public int copiesTotal()
```

### Return Value - copiesTotal

The number of copies the user requested in the sysPrintForm form.

### Remarks - copiesTotal

Controls are typically evaluated during the execution of a report. A control that uses this method is evaluated when the report is printed.

## Method copy

Returns the number of the copy of a report.

```xpp
public int copy()
```

### Return Value - copy

The number of the copy.

### Remarks - copy

If the user prints three copies of a report a control that have a dataFunction method, this method will return one for the first copy, two for the second copy, and three for the last copy.

## Method copyDescription

```xpp
public str copyDescription()
```

### Return Value - copyDescription

## Method createProgressForm

Creates the form that contains progress information.

```xpp
public xFormRun createProgressForm()
```

### Return Value - createProgressForm

The form to use to display the progress information.

### Remarks - createProgressForm

You can overload this method. The method is called when the first page is created. The default implementation will open the SysPrintProgress form. If you implement your own progress form, you must implement the setNames and setPagePercent methods because these methods are called within the kernel. This form is shown when the pages are created, not when the pages are printed.

## Method currentYmm100

```xpp
public int currentYmm100()
```

### Return Value - currentYmm100

## Method design

Gets or sets the name of the design.

```xpp
public ReportDesign design([AnyType nameOrReportDesign])
```

### Parameters - design

nameOrReportDesign  
The name of the design; optional.

### Return Value - design

The name of the design.

### Remarks - design

This method can be used to change from one design to another while the report is executed.

## Method deviceName

```xpp
public str deviceName([str device])
```

### Parameters - deviceName

device  

### Return Value - deviceName

## Method dialog

```xpp
public Object dialog(Object dialog)
```

### Parameters - dialog

dialog  

### Return Value - dialog

## Method driverName

Returns the printer driver name.

```xpp
public str driverName()
```

### Return Value - driverName

The printer driver name.

### Remarks - driverName

The method often returns the string "winspool". This is the printer driver name that is used when the printer device context is created. If no printers have been set up on the computer, the string "Screen" is returned.

## Method enableAllBodies

```xpp
public boolean enableAllBodies([boolean enable])
```

### Parameters - enableAllBodies

enable  

### Return Value - enableAllBodies

## Method execute

Prints the programmable sections of a report.

```xpp
public boolean execute(int number)
```

### Parameters - execute

number  
The controlNumber value of the programmable section.

### Return Value - execute

false if the toPage object has been generated; otherwise, true.

## Method executeBodyColumnHeadings

Prints the column headings of a body section in a report.

```xpp
public boolean executeBodyColumnHeadings(TableId tableId, [FieldId fieldId])
```

### Parameters - executeBodyColumnHeadings

tableId  
The field ID of the DataField property of a section group; optional.

<!-- -->

fieldId  
The field ID of the DataField property of a section group; optional.

### Return Value - executeBodyColumnHeadings

true if any column headings were printed; otherwise, false.

### Remarks - executeBodyColumnHeadings

This method is useful when a report should contain more column headings than those automatically printed in the report.

## Method executeColumnHeadings

```xpp
public boolean executeColumnHeadings(ReportSection section)
```

### Parameters - executeColumnHeadings

section  

### Return Value - executeColumnHeadings

## Method executeControlColumnHeadings

Executes the column headings of a programmable section.

```xpp
public boolean executeControlColumnHeadings(int number)
```

### Parameters - executeControlColumnHeadings

number  
The controlNumber value of the programmable section.

### Return Value - executeControlColumnHeadings

true if any sections were printed; otherwise, false.

### Remarks - executeControlColumnHeadings

This method is useful if you want to add columnHeading objects to a programmable section. If a programmable section causes a page break, the columnHeadings objects of the section are repeated. Under these circumstances this method not have to be called.

## Method executeFooter

Execute a footer section.

```xpp
public boolean executeFooter([TableId tableId], [FieldId fieldId])
```

### Parameters - executeFooter

tableId  
The field ID of the dataField property of the footer section group; optional.

<!-- -->

fieldId  
The field ID of the dataField property of the footer section group; optional.

### Return Value - executeFooter

true if anything was printed; otherwise, false.

## Method executeHeader

Executes a header section.

```xpp
public boolean executeHeader([TableId tableId], [FieldId fieldId])
```

### Parameters - executeHeader

tableId  
The field ID of the dataField property of the header section group; optional.

<!-- -->

fieldId  
The field ID of the dataField property of the header section group; optional.

### Return Value - executeHeader

## Method executeSection

Prints the specified section in the report.

```xpp
public boolean executeSection(ReportSection section)
```

### Parameters - executeSection

section  
The section to print.

### Return Value - executeSection

## Method fetch

Executes the report query and calls the send method for the record that is found by the query.

```xpp
public boolean fetch()
```

### Return Value - fetch

true if execution of the report should continue; otherwise, false.

### Remarks - fetch

The fetch method is called from the super call in the run method.

## Method from

```xpp
public int from([int fromPage])
```

### Parameters - from

fromPage  

### Return Value - from

## Method generateDesign

```xpp
public int generateDesign([Query query], [int designNo])
```

### Parameters - generateDesign

query  

<!-- -->

designNo  

### Return Value - generateDesign

## Method getDeclineOverwrite

```xpp
public boolean getDeclineOverwrite()
```

### Return Value - getDeclineOverwrite

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

## Method getRangeDescription

```xpp
public str getRangeDescription(int number)
```

### Parameters - getRangeDescription

number  

### Return Value - getRangeDescription

## Method getReportViewer

```xpp
public ReportViewer getReportViewer()
```

### Return Value - getReportViewer

## Method getTarget

```xpp
public PrintMedium getTarget()
```

### Return Value - getTarget

## Method hasGeneratedDesign

```xpp
public boolean hasGeneratedDesign()
```

### Return Value - hasGeneratedDesign

## Method headerDescription

```xpp
public str headerDescription()
```

### Return Value - headerDescription

## Method heightOfPageFooters

```xpp
public int heightOfPageFooters()
```

### Return Value - heightOfPageFooters

## Method indent

```xpp
public int indent()
```

### Return Value - indent

## Method isBodyEnabled

```xpp
public boolean isBodyEnabled(TableId tableId)
```

### Parameters - isBodyEnabled

tableId  

### Return Value - isBodyEnabled

## Method jobId

```xpp
public Int64 jobId()
```

### Return Value - jobId

## Method last

```xpp
public Common last(TableId tableId)
```

### Parameters - last

tableId  

### Return Value - last

## Method mm100Left

```xpp
public int mm100Left()
```

### Return Value - mm100Left

## Method mm100PageHeight

```xpp
public int mm100PageHeight()
```

### Return Value - mm100PageHeight

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

```xpp
public str name([str name])
```

### Parameters - name

name  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method pack

Serializes the current instance of the ReportRun class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the ReportRun class.

## Method packDesign

```xpp
public container packDesign()
```

### Return Value - packDesign

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

## Method packSubtotalSettings

```xpp
public container packSubtotalSettings()
```

### Return Value - packSubtotalSettings

## Method page

```xpp
public int page([int number])
```

### Parameters - page

number  

### Return Value - page

## Method pageFormatting

Displays the printer properties of the printer.

```xpp
public boolean pageFormatting()
```

### Return Value - pageFormatting

### Remarks - pageFormatting

This method on the Report object is never called by the kernel. It could be called by the sysPrintForm form when the user clicks the Properties button, but instead, the sysPrintForm form calls the directly.

## Method pagesTotal

```xpp
public int pagesTotal()
```

### Return Value - pagesTotal

## Method passThrough

```xpp
public str passThrough(str str)
```

### Parameters - passThrough

str  

### Return Value - passThrough

## Method pixelsLeft

```xpp
public int pixelsLeft()
```

### Return Value - pixelsLeft

## Method print

Sends the generated report to a print medium, such as a printer or the screen.

```xpp
public int print()
```

### Return Value - print

### Remarks - print

The call to the super method in this method directs the generated report to a printMedium object, such as printer or screen. If the target is a screen, the call to the super method will create a reportViewer object on the client and call the showPage method. If the target is a printer, the call to the super method will create a reportOutput object and call the print method on this object. If the outputToClient method of the PrintJobSettings class has been called with a parameter of true, a reportViewer object will be created and the print method of that object will be called. In in this manner, a report that is generated on the server can be output to a printer that is set up on the client.

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

## Method printerFontInfo

Indicates which font is used to print the report.

```xpp
public str printerFontInfo()
```

### Return Value - printerFontInfo

The name of the font.

### Remarks - printerFontInfo

The font to use to print the report is not necessarily the same as that set on the font property of the control as that font might not be available on the user system.

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

Enables the user to select printer settings.

```xpp
public boolean printerSettings([int showWhat])
```

### Parameters - printerSettings

showWhat  
This parameter is currently not functional.

### Return Value - printerSettings

true if execution of the report should continue; otherwise, false.

### Remarks - printerSettings

The call to the super method in this method runs the sysPrintForm form. The prompt method is called from the super method call in the prompt method. The PrintFormName property on the reportDesign object determines which form the call to the super method in the printerSettings object will run.

## Method printerShareName

```xpp
public str printerShareName()
```

### Return Value - printerShareName

## Method printerStartTime

```xpp
public TimeOfDay printerStartTime()
```

### Return Value - printerStartTime

## Method printerStatus

```xpp
public int printerStatus()
```

### Return Value - printerStatus

## Method printerUntilTime

```xpp
public TimeOfDay printerUntilTime()
```

### Return Value - printerUntilTime

## Method printJobSettings

```xpp
public PrintJobSettings printJobSettings([container packedPrintJobSettings])
```

### Parameters - printJobSettings

packedPrintJobSettings  

### Return Value - printJobSettings

## Method printSum

```xpp
public int printSum()
```

### Return Value - printSum

## Method progressForm

```xpp
public xFormRun progressForm([xFormRun form])
```

### Parameters - progressForm

form  

### Return Value - progressForm

## Method progressInfo

Creates a string that describes how much of the report has been generated during the execution of a report every time that a section is executed.

```xpp
public str progressInfo(int pageNo, int lineNo)
```

### Parameters - progressInfo

pageNo  
The section number of the page.

<!-- -->

lineNo  
The section number of the page.

### Return Value - progressInfo

A string that describes how much of the report has been generated.

## Method prompt

Prompts the user a report is run.

```xpp
public boolean prompt([boolean enableCopy], [boolean enablePages], [boolean enableDevice], [boolean enableProperties], [boolean enablePrintTo])
```

### Parameters - prompt

enableCopy  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enablePages  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enableDevice  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enableProperties  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enablePrintTo  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

### Return Value - prompt

true if execution of report should continue; otherwise, false.

### Remarks - prompt

The call to the super method in the prompt method runs the sysPrintForm form. This method is called from the run method.

## Method query

```xpp
public Query query([Query query])
```

### Parameters - query

query  

### Return Value - query

## Method queryRun

```xpp
public QueryRun queryRun([QueryRun queryRun])
```

### Parameters - queryRun

queryRun  

### Return Value - queryRun

## Method report

```xpp
public Report report()
```

### Return Value - report

## Method reportUser

```xpp
public str reportUser([str user])
```

### Parameters - reportUser

user  

### Return Value - reportUser

## Method rulerCM

```xpp
public int rulerCM()
```

### Return Value - rulerCM

## Method rulerINCH

```xpp
public int rulerINCH()
```

### Return Value - rulerINCH

## Method screenFontInfo

```xpp
public str screenFontInfo()
```

### Return Value - screenFontInfo

## Method section

```xpp
public ReportSection section()
```

### Return Value - section

## Method sectionsLeft

```xpp
public int sectionsLeft(ReportSection section)
```

### Parameters - sectionsLeft

section  

### Return Value - sectionsLeft

## Method send

Triggers the body sections that belong to a section group.

```xpp
public boolean send(Common cursor, [int level], [boolean triggerOffBody], [boolean newPageBeforeBody])
```

### Parameters - send

cursor  

<!-- -->

level  

<!-- -->

triggerOffBody  

<!-- -->

newPageBeforeBody  

### Return Value - send

false if the toPage object has been generated; otherwise true.

### Remarks - send

The executeSection method of the ReportSection class is called on each triggered section. By default in a master-detail report, the records from the master table have level of one, and the records from the details table have level of two.

## Method setTarget

```xpp
public PrintMedium setTarget(PrintMedium target)
```

### Parameters - setTarget

target  

### Return Value - setTarget

## Method showMenuFunction

```xpp
public boolean showMenuFunction(xMenuFunction menuFunction)
```

### Parameters - showMenuFunction

menuFunction  

### Return Value - showMenuFunction

## Method showMenuReference

```xpp
public boolean showMenuReference(WebMenu menuReference)
```

### Parameters - showMenuReference

menuReference  

### Return Value - showMenuReference

## Method sortInfo

```xpp
public str sortInfo(Common cursor)
```

### Parameters - sortInfo

cursor  

### Return Value - sortInfo

## Method startDate

```xpp
public Date startDate()
```

### Return Value - startDate

## Method startDateTime

```xpp
public DateTime startDateTime()
```

### Return Value - startDateTime

## Method startMachineDate

```xpp
public Date startMachineDate()
```

### Return Value - startMachineDate

## Method startTime

```xpp
public TimeOfDay startTime()
```

### Return Value - startTime

## Method sum

```xpp
public Real sum(TableId tableId, FieldId fieldId, [int indent])
```

### Parameters - sum

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

### Return Value - sum

## Method sumControl

```xpp
public Real sumControl(str fieldName, [int indent])
```

### Parameters - sumControl

fieldName  

<!-- -->

indent  

### Return Value - sumControl

## Method sumControlNeg

```xpp
public Real sumControlNeg(str fieldName, [int indent])
```

### Parameters - sumControlNeg

fieldName  

<!-- -->

indent  

### Return Value - sumControlNeg

## Method sumControlPos

```xpp
public Real sumControlPos(str fieldName, [int indent])
```

### Parameters - sumControlPos

fieldName  

<!-- -->

indent  

### Return Value - sumControlPos

## Method sumDescription

```xpp
public str sumDescription()
```

### Return Value - sumDescription

## Method sumNeg

```xpp
public Real sumNeg(TableId tableId, FieldId fieldId, [int indent])
```

### Parameters - sumNeg

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

### Return Value - sumNeg

## Method sumPos

```xpp
public Real sumPos(TableId tableId, FieldId fieldId, [int indent])
```

### Parameters - sumPos

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

### Return Value - sumPos

## Method suppressReportIsEmptyMessage

```xpp
public boolean suppressReportIsEmptyMessage([boolean suppress])
```

### Parameters - suppressReportIsEmptyMessage

suppress  

### Return Value - suppressReportIsEmptyMessage

## Method title

Gets or sets the print job description.

```xpp
public str title([str title])
```

### Parameters - title

title  
The new printJobDescription value; optional.

### Return Value - title

A string that contains the job description.

### Remarks - title

If reports are written to the printArchive object, the print job description is stored in the jobDescription field of the printJobHeader table. If the report is previewed, the print job description is used as the caption. This method is not called by the kernel during the execution of a report. Therefore, overriding the method will have no effect.

## Method to

```xpp
public int to([int toPage])
```

### Parameters - to

toPage  

### Return Value - to

## Method toString

Returns a textual description of the class.

```xpp
public str toString()
```

### Return Value - toString

A string that describes the class.

### Remarks - toString

For most classes the toString method returns a string that contains the class handle and name, but for some classes more information is returned in the string.

## Method unpackPageSettings

```xpp
public boolean unpackPageSettings(container packedPageSetup)
```

### Parameters - unpackPageSettings

packedPageSetup  

### Return Value - unpackPageSettings

## Method unpackPrinterSettings

```xpp
public boolean unpackPrinterSettings(container packedPrinterSetup)
```

### Parameters - unpackPrinterSettings

packedPrinterSetup  

### Return Value - unpackPrinterSettings

## Method unpackPrintJobSettings

```xpp
public boolean unpackPrintJobSettings(container packedPrintJobSettings)
```

### Parameters - unpackPrintJobSettings

packedPrintJobSettings  

### Return Value - unpackPrintJobSettings

## Method unpackSubtotalSettings

```xpp
public boolean unpackSubtotalSettings(container packedSubtotalSetup)
```

### Parameters - unpackSubtotalSettings

packedSubtotalSetup  

### Return Value - unpackSubtotalSettings

## Method userSelectedOrientation

```xpp
public PrinterOrientation userSelectedOrientation()
```

### Return Value - userSelectedOrientation

## Method disableBody

```xpp
public void disableBody([TableId tableId])
```

### Parameters - disableBody

tableId  

## Method attach

```xpp
public void attach()
```

## Method new

Initializes an instance of the ReportRun class.

```xpp
public void new(AnyType argsOrReportOrContainer, [str designName], [boolean isWebReport])
```

### Parameters - new

argsOrReportOrContainer  

<!-- -->

designName  

<!-- -->

isWebReport  

## Method disableSection

```xpp
public void disableSection(ReportSection section)
```

### Parameters - disableSection

section  

## Method arrangeLevelGlobal

```xpp
public void arrangeLevelGlobal()
```

## Method setEscapeSequence

```xpp
public void setEscapeSequence(str str)
```

### Parameters - setEscapeSequence

str  

## Method enableBody

```xpp
public void enableBody([TableId tableId])
```

### Parameters - enableBody

tableId  

## Method clearAllRangeDescriptions

```xpp
public void clearAllRangeDescriptions()
```

## Method header

Controls the header.

```xpp
public void header(ReportSection headerSection, TableId tableId, FieldId fieldId)
```

### Parameters - header

headerSection  
The ID of the field that contains the changed value.

<!-- -->

tableId  
The ID of the field that contains the changed value.

<!-- -->

fieldId  
The ID of the field that contains the changed value.

### Remarks - header

This method works just like the footer method, except it is called before a group of records, whereas the footer method is called after a group of records.

## Method unpackDesign

```xpp
public void unpackDesign(container packedDesign)
```

### Parameters - unpackDesign

packedDesign  

## Method newPage

```xpp
public void newPage([boolean doPageFooter])
```

### Parameters - newPage

doPageFooter  

## Method footer

Controls the footer.

```xpp
public void footer(ReportSection footerSection, TableId tableId, FieldId fieldId)
```

### Parameters - footer

footerSection  
The ID of the field that contains the changed value.

<!-- -->

tableId  
The ID of the field that contains the changed value.

<!-- -->

fieldId  
The ID of the field that contains the changed value.

### Remarks - footer

This method is called when a field is sorted after it changes value, even if the user has chosen not to print headers or footers. One call of the send method can trigger the printing of multiple footer sections and header sections before the body sections. The header and footer methods allow the user to execute code before or after printing the header or footer.

## Method reset

Enables a single instance of the ReportRun class to create multiple reports.

```xpp
public void reset([boolean delayExceptions])
```

### Parameters - reset

delayExceptions  

## Method arrangeLevelNone

```xpp
public void arrangeLevelNone()
```

## Method run

Runs the report.

```xpp
public void run()
```

### Remarks - run

The call to the super method in this method calls the following methods:

-   prompt - Lets the user select the printer in the sysPrintForm form
-   fetch - Runs the report query
-   print - Directs the report to the printer or display.

## Method gotoYmm100

```xpp
public void gotoYmm100([int mm100])
```

### Parameters - gotoYmm100

mm100  

## Method disableColumnHeadings

```xpp
public void disableColumnHeadings([TableId tableId])
```

### Parameters - disableColumnHeadings

tableId  

## Method enablePageFooter

```xpp
public void enablePageFooter()
```

## Method init

```xpp
public void init()
```

## Method arrangeLevelControl

```xpp
public void arrangeLevelControl()
```

## Method disablePageFooter

```xpp
public void disablePageFooter()
```

## Method addPendingSums

Prints the relevant footers of the report.

```xpp
public void addPendingSums()
```

### Remarks - addPendingSums

This method should only be called in reports where the fetch method is called more than once.

## Method arrangeLevelSection

```xpp
public void arrangeLevelSection()
```

## Method enableSection

```xpp
public void enableSection(ReportSection section)
```

### Parameters - enableSection

section  

## Method detach

```xpp
public void detach()
```

## Method addRangeDescription

```xpp
public void addRangeDescription(int x, int y, str text, [str fontName], [int fontSize])
```

### Parameters - addRangeDescription

x  

<!-- -->

y  

<!-- -->

text  

<!-- -->

fontName  

<!-- -->

fontSize  

## Method finalize

```xpp
public void finalize()
```

