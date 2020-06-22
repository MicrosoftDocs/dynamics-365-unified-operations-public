---
title: ReportOutput class
description: This topic describes the ReportOutput class.
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

# Class ReportOutput

[!include [banner](../../includes/banner.md)]

```xpp
class ReportOutput extends Object
```

The ReportOutput class handles the output of a report to a printer or file.

## Remarks

This class serves as the base class for the ReportViewer class, which handles preview of reports, and for the ReportOutputUser class, which handles output of reports to a user-defined target in a user-defined format. In general, if a report is printed to the printer, the print method creates a ReportOutput object and calls its print method. If the call printJobSettings::outputToClient(TRUE) has been made, a ReportViewer object is created instead. The call to the print method prints the report on a printer that is set up on the client, because a ReportViewer object can only exist on the client, not on the server.

## Examples

The following example prints the job descriptions and page numbers of jobs that have been inserted into the printArchive table on the current date, and prints page 1 on the default printer.

```xpp
static void aaaReportOutputExample(args a) 
{ 
    printJobHeader printJobHeader; 
    printJobPages printJobPages; 
    int myrecId; 
    reportViewer reportViewer; 
    while select printJobHeader where printJobHeader.createdDateTime >=
        str2datetime("01/01/2011 12:00:00", 123) 
    { 
        myrecId = printJobHeader.recId; 
        print printJobHeader.jobDescription; 
        while select printJobPages  
            where printJobPages.pagesHeaderRecId == myRecId 
        print printJobPages.PageNo; 
        reportViewer = new reportOutput(printJobHeader); 
        reportViewer.print(); 
    } 
}
```

## Methods

| Method                                                                    | Description                                     |
|---------------------------------------------------------------------------|-------------------------------------------------|
| public str description(\[str description\])                               |                                                 |
| public int getCopyNo()                                                    |                                                 |
| public boolean getDeclineOverwrite()                                      |                                                 |
| public int getLastCopyNo()                                                |                                                 |
| public int getLastPageNo()                                                |                                                 |
| public int getPageNo()                                                    |                                                 |
| public str getTempFileName(str prefix)                                    |                                                 |
| public PrintJobStatus jobStatus()                                         |                                                 |
| public PrintJobSettings printJobSettings()                                |                                                 |
| public boolean setNumberOfPages(int pageNo)                               |                                                 |
| public str type(\[str type\])                                             |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\]) | Initializes a new instance of the Object class. |
| public void printAscii(str filename)                                      |                                                 |
| public void printTextUTF8(str filename)                                   | Prints a report to a UTF-8 format.              |
| public void printRTF(str filename)                                        |                                                 |
| public void print()                                                       |                                                 |
| public void printPDF(str filename, \[boolean embedFonts\])                |                                                 |
| public void printHTML(str filename)                                       |                                                 |
| public void abort()                                                       |                                                 |
| public void dialogAndPrint()                                              |                                                 |
| public void printToTarget()                                               |                                                 |

## Method description

```xpp
public str description([str description])
```

### Parameters - description

description  

### Return Value - description

## Method getCopyNo

```xpp
public int getCopyNo()
```

### Return Value - getCopyNo

## Method getDeclineOverwrite

```xpp
public boolean getDeclineOverwrite()
```

### Return Value - getDeclineOverwrite

## Method getLastCopyNo

```xpp
public int getLastCopyNo()
```

### Return Value - getLastCopyNo

## Method getLastPageNo

```xpp
public int getLastPageNo()
```

### Return Value - getLastPageNo

## Method getPageNo

```xpp
public int getPageNo()
```

### Return Value - getPageNo

## Method getTempFileName

```xpp
public str getTempFileName(str prefix)
```

### Parameters - getTempFileName

prefix  

### Return Value - getTempFileName

## Method jobStatus

```xpp
public PrintJobStatus jobStatus()
```

### Return Value - jobStatus

## Method printJobSettings

```xpp
public PrintJobSettings printJobSettings()
```

### Return Value - printJobSettings

## Method setNumberOfPages

```xpp
public boolean setNumberOfPages(int pageNo)
```

### Parameters - setNumberOfPages

pageNo  

### Return Value - setNumberOfPages

## Method type

```xpp
public str type([str type])
```

### Parameters - type

type  

### Return Value - type

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor])
```

### Parameters - new

jobsCursor  

<!-- -->

pagesCursor  

## Method printAscii

```xpp
public void printAscii(str filename)
```

### Parameters - printAscii

filename  

## Method printTextUTF8

Prints a report to a UTF-8 format.

```xpp
public void printTextUTF8(str filename)
```

### Parameters - printTextUTF8

filename  
A string that specifies the name of the file that the report is printed to.

### Remarks - printTextUTF8

UTF-8 is a method of character encoding that allows for both single and multibyte characters in one string.

### Examples - printTextUTF8

The following example shows a call to the printTextUTF8 method.

```xpp
void printTextUTF8() 
{ 
    ReportOutput reportOutput; 
    printJobHeader printJobHeader; 
    while select printJobHeader where printJobHeader.createdDateTime >= 
        str2datetime("01/01/2011 12:00:00", 123)
    { 
        print printJobHeader.jobDescription; 
        reportOutput = new ReportOutput(printJobHeader); 
        reportOutput.printTextUTF8("c:\\report.txt"); 
    } 
}
```

## Method printRTF

```xpp
public void printRTF(str filename)
```

### Parameters - printRTF

filename  

## Method print

```xpp
public void print()
```

## Method printPDF

```xpp
public void printPDF(str filename, [boolean embedFonts])
```

### Parameters - printPDF

filename  

<!-- -->

embedFonts  

## Method printHTML

```xpp
public void printHTML(str filename)
```

### Parameters - printHTML

filename  

## Method abort

```xpp
public void abort()
```

## Method dialogAndPrint

```xpp
public void dialogAndPrint()
```

## Method printToTarget

```xpp
public void printToTarget()
```

