---
title: ReportOutputUser class
description: This topic describes the ReportOutputUser class.
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

# Class ReportOutputUser

[!include [banner](../../includes/banner.md)]

```xpp
class ReportOutputUser extends ReportOutput
```

The ReportOutputUser class implements a user-defined target for report formatting.

## Remarks

By default, reports are printed to a screen, printer, file, or email address. The following API items support a user-defined target:

-   ReportOutputUserType system enumeration
-   ViewerClass value for the PrintMedium system enumeration
-   ClassFactory::createViewer method

When a report is run, the print method creates a reportOutputUser object if the target is PrintMedium::Viewer class. This object will be created by calling the createViewer method and giving reportOutputUserType as one of the arguments. The report will then be printed by calling methods on the object: startReport, startPage, startSection, writeField, and so on. In general, if the target is, for example, a printer, the reportRun::print method will create a reportOutput object and call its print method to print the report to a printer. If the target is viewerClass, it will instead call the createViewer method to get a ReportOutputUser object. Then it will call methods on the object: startReport, startPage, startSection, startField, outputStringField, and so on. When the report is run, the Text property of the text controls of the report will be written to the print window.

## Examples

## Methods

| Method                                                                                            | Description                                     |
|---------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public boolean pageCreated(int page)                                                              |                                                 |
| public str result()                                                                               |                                                 |
| public void writeAutoLabel(OutputAutoLabelField field, OuputSection section)                      |                                                 |
| public void endHeaderSection(OutputHeaderSection section)                                         |                                                 |
| public void writeString(OutputStringField field, OuputSection section)                            |                                                 |
| public void endPageHeaderSection(OutputPageHeaderSection section)                                 |                                                 |
| public void writeBitmap(OutputBitmapField field, OuputSection section)                            |                                                 |
| public void endBodySection(OutputBodySection section)                                             |                                                 |
| public void startPageHeaderSection(OutputPageHeaderSection section)                               |                                                 |
| public void printViaClass()                                                                       |                                                 |
| public void endPageFooterSection(OutputPageFooterSection section)                                 |                                                 |
| public void writeReal(OutputRealField field, OuputSection section)                                |                                                 |
| public void startColumnHeadingsSection(OutputColumnHeadingsSection section)                       |                                                 |
| public void writeShape(OutputShapeField field, OuputSection section)                              |                                                 |
| public void writeDateTime(OutputDateTimeField field, OuputSection section)                        |                                                 |
| public void writeStaticText(OutputStaticTextField field, OuputSection section)                    |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\], \[container settings\]) | Initializes a new instance of the Object class. |
| public void writeInteger(OutputIntegerField field, OuputSection section)                          |                                                 |
| public void startColumnSection()                                                                  |                                                 |
| public void startSection(OuputSection section)                                                    |                                                 |
| public void writeDate(OutputDateField field, OuputSection section)                                |                                                 |
| public void pagesTotal(int pagesTotal)                                                            |                                                 |
| public void writeInt64(OutputInt64Field field, OuputSection section)                              |                                                 |
| public void endReport(PrintJobStatus printJobStatus)                                              |                                                 |
| public void endColumnSection()                                                                    |                                                 |
| public void startReport(PrintJobSettings printJobSettings)                                        |                                                 |
| public void printPageViaClass(int page)                                                           |                                                 |
| public void endEpilogSection(OutputEpilogSection section)                                         |                                                 |
| public void endPrologSection(OutputPrologSection section)                                         |                                                 |
| public void endPage()                                                                             |                                                 |
| public void startFooterSection(OutputFooterSection section)                                       |                                                 |
| public void endProgrammableSection(OutputProgrammableSection section)                             |                                                 |
| public void startBodySection(OutputBodySection section)                                           |                                                 |
| public void endSection(OuputSection section)                                                      |                                                 |
| public void startProgrammableSection(OutputProgrammableSection section)                           |                                                 |
| public void startEpilogSection(OutputEpilogSection section)                                       |                                                 |
| public void startHeaderSection(OutputHeaderSection section)                                       |                                                 |
| public void endColumnHeadingsSection(OutputColumnHeadingsSection section)                         |                                                 |
| public void writeLabel(OutputLabelField field, OuputSection section)                              |                                                 |
| public void endFooterSection(OutputFooterSection section)                                         |                                                 |
| public void writeField(OutputField field, OuputSection section)                                   |                                                 |
| public void writeEnum(OutputEnumField field, OuputSection section)                                |                                                 |
| public void startPageFooterSection(OutputPageFooterSection section)                               |                                                 |
| public void writeSum(OutputSumField field, OuputSection section)                                  |                                                 |
| public void writeTime(OutputTimeField field, OuputSection section)                                |                                                 |
| public void startPage(OutputPage page)                                                            |                                                 |
| public void startPrologSection(OutputPrologSection section)                                       |                                                 |

## Method pageCreated

```xpp
public boolean pageCreated(int page)
```

### Parameters - pageCreated

page  

### Return Value - pageCreated

## Method result

```xpp
public str result()
```

### Return Value - result

## Method writeAutoLabel

```xpp
public void writeAutoLabel(OutputAutoLabelField field, OuputSection section)
```

### Parameters - writeAutoLabel

field  

<!-- -->

section  

## Method endHeaderSection

```xpp
public void endHeaderSection(OutputHeaderSection section)
```

### Parameters - endHeaderSection

section  

## Method writeString

```xpp
public void writeString(OutputStringField field, OuputSection section)
```

### Parameters - writeString

field  

<!-- -->

section  

## Method endPageHeaderSection

```xpp
public void endPageHeaderSection(OutputPageHeaderSection section)
```

### Parameters - endPageHeaderSection

section  

## Method writeBitmap

```xpp
public void writeBitmap(OutputBitmapField field, OuputSection section)
```

### Parameters - writeBitmap

field  

<!-- -->

section  

## Method endBodySection

```xpp
public void endBodySection(OutputBodySection section)
```

### Parameters - endBodySection

section  

## Method startPageHeaderSection

```xpp
public void startPageHeaderSection(OutputPageHeaderSection section)
```

### Parameters - startPageHeaderSection

section  

## Method printViaClass

```xpp
public void printViaClass()
```

## Method endPageFooterSection

```xpp
public void endPageFooterSection(OutputPageFooterSection section)
```

### Parameters - endPageFooterSection

section  

## Method writeReal

```xpp
public void writeReal(OutputRealField field, OuputSection section)
```

### Parameters - writeReal

field  

<!-- -->

section  

## Method startColumnHeadingsSection

```xpp
public void startColumnHeadingsSection(OutputColumnHeadingsSection section)
```

### Parameters - startColumnHeadingsSection

section  

## Method writeShape

```xpp
public void writeShape(OutputShapeField field, OuputSection section)
```

### Parameters - writeShape

field  

<!-- -->

section  

## Method writeDateTime

```xpp
public void writeDateTime(OutputDateTimeField field, OuputSection section)
```

### Parameters - writeDateTime

field  

<!-- -->

section  

## Method writeStaticText

```xpp
public void writeStaticText(OutputStaticTextField field, OuputSection section)
```

### Parameters - writeStaticText

field  

<!-- -->

section  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor], [container settings])
```

### Parameters - new

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

settings  

## Method writeInteger

```xpp
public void writeInteger(OutputIntegerField field, OuputSection section)
```

### Parameters - writeInteger

field  

<!-- -->

section  

## Method startColumnSection

```xpp
public void startColumnSection()
```

## Method startSection

```xpp
public void startSection(OuputSection section)
```

### Parameters - startSection

section  

## Method writeDate

```xpp
public void writeDate(OutputDateField field, OuputSection section)
```

### Parameters - writeDate

field  

<!-- -->

section  

## Method pagesTotal

```xpp
public void pagesTotal(int pagesTotal)
```

### Parameters - pagesTotal

pagesTotal  

## Method writeInt64

```xpp
public void writeInt64(OutputInt64Field field, OuputSection section)
```

### Parameters - writeInt64

field  

<!-- -->

section  

## Method endReport

```xpp
public void endReport(PrintJobStatus printJobStatus)
```

### Parameters - endReport

printJobStatus  

## Method endColumnSection

```xpp
public void endColumnSection()
```

## Method startReport

```xpp
public void startReport(PrintJobSettings printJobSettings)
```

### Parameters - startReport

printJobSettings  

## Method printPageViaClass

```xpp
public void printPageViaClass(int page)
```

### Parameters - printPageViaClass

page  

## Method endEpilogSection

```xpp
public void endEpilogSection(OutputEpilogSection section)
```

### Parameters - endEpilogSection

section  

## Method endPrologSection

```xpp
public void endPrologSection(OutputPrologSection section)
```

### Parameters - endPrologSection

section  

## Method endPage

```xpp
public void endPage()
```

## Method startFooterSection

```xpp
public void startFooterSection(OutputFooterSection section)
```

### Parameters - startFooterSection

section  

## Method endProgrammableSection

```xpp
public void endProgrammableSection(OutputProgrammableSection section)
```

### Parameters - endProgrammableSection

section  

## Method startBodySection

```xpp
public void startBodySection(OutputBodySection section)
```

### Parameters - startBodySection

section  

## Method endSection

```xpp
public void endSection(OuputSection section)
```

### Parameters - endSection

section  

## Method startProgrammableSection

```xpp
public void startProgrammableSection(OutputProgrammableSection section)
```

### Parameters - startProgrammableSection

section  

## Method startEpilogSection

```xpp
public void startEpilogSection(OutputEpilogSection section)
```

### Parameters - startEpilogSection

section  

## Method startHeaderSection

```xpp
public void startHeaderSection(OutputHeaderSection section)
```

### Parameters - startHeaderSection

section  

## Method endColumnHeadingsSection

```xpp
public void endColumnHeadingsSection(OutputColumnHeadingsSection section)
```

### Parameters - endColumnHeadingsSection

section  

## Method writeLabel

```xpp
public void writeLabel(OutputLabelField field, OuputSection section)
```

### Parameters - writeLabel

field  

<!-- -->

section  

## Method endFooterSection

```xpp
public void endFooterSection(OutputFooterSection section)
```

### Parameters - endFooterSection

section  

## Method writeField

```xpp
public void writeField(OutputField field, OuputSection section)
```

### Parameters - writeField

field  

<!-- -->

section  

## Method writeEnum

```xpp
public void writeEnum(OutputEnumField field, OuputSection section)
```

### Parameters - writeEnum

field  

<!-- -->

section  

## Method startPageFooterSection

```xpp
public void startPageFooterSection(OutputPageFooterSection section)
```

### Parameters - startPageFooterSection

section  

## Method writeSum

```xpp
public void writeSum(OutputSumField field, OuputSection section)
```

### Parameters - writeSum

field  

<!-- -->

section  

## Method writeTime

```xpp
public void writeTime(OutputTimeField field, OuputSection section)
```

### Parameters - writeTime

field  

<!-- -->

section  

## Method startPage

```xpp
public void startPage(OutputPage page)
```

### Parameters - startPage

page  

## Method startPrologSection

```xpp
public void startPrologSection(OutputPrologSection section)
```

### Parameters - startPrologSection

section  

