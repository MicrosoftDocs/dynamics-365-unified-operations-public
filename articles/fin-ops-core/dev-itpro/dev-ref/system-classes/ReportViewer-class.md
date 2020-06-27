---
title: ReportViewer class
description: This topic describes the ReportViewer class.
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

# Class ReportViewer

[!include [banner](../../includes/banner.md)]

```xpp
class ReportViewer extends ReportOutput
```

The ReportViewer class lets the user preview a report.

## Remarks

ReportViewer objects can exist only on the client, because a report preview can occur only on a client.

## Examples

The following code will print the job descriptions and the page numbers of jobs that are inserted in the printArchive on the current date, and it will show page 1 in the report viewer.

```xpp
static void aaaReportOutputExample(args a) 
{ 
    PrintJobHeader printJobHeader; 
    PrintJobPages printJobPages; 
    int myrecId; 
    reportViewer reportViewer; 
    while select printJobHeader where printJobHeader.CreatedDate >= 
            str2datetime("01/01/2011 12:00:00 am",123)
    { 
        myrecId = printJobHeader.recId; 
        print printJobHeader.jobDescription; 
        while select printJobPages  
            where printJobPages.pagesHeaderRecId == myRecId 
                print printJobPages.PageNo; 
        reportViewer = new reportViewer(printJobHeader); 
        reportViewer.showPage(1); 
    } 
}
```

## Methods

| Method                                                                                                          | Description                                     |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public boolean setNumberOfPages(int pageNo, \[boolean updataProgressForm\])                                     |                                                 |
| public void nextPage()                                                                                          |                                                 |
| public void lastPage()                                                                                          |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\], \[container packedPrintJobSettings\]) | Initializes a new instance of the Object class. |
| public void gotoPage(int pageNo)                                                                                |                                                 |
| public void pause()                                                                                             |                                                 |
| public void showPage(int pageNo)                                                                                |                                                 |
| public void firstPage()                                                                                         |                                                 |
| public void setAborted()                                                                                        |                                                 |
| public void close()                                                                                             |                                                 |
| public void prevPage()                                                                                          |                                                 |
| public void setCompleted()                                                                                      |                                                 |

## Method setNumberOfPages

```xpp
public boolean setNumberOfPages(int pageNo, [boolean updataProgressForm])
```

### Parameters - setNumberOfPages

pageNo  

<!-- -->

updataProgressForm  

### Return Value - setNumberOfPages

## Method nextPage

```xpp
public void nextPage()
```

## Method lastPage

```xpp
public void lastPage()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor], [container packedPrintJobSettings])
```

### Parameters - new

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

packedPrintJobSettings  

## Method gotoPage

```xpp
public void gotoPage(int pageNo)
```

### Parameters - gotoPage

pageNo  

## Method pause

```xpp
public void pause()
```

## Method showPage

```xpp
public void showPage(int pageNo)
```

### Parameters - showPage

pageNo  

## Method firstPage

```xpp
public void firstPage()
```

## Method setAborted

```xpp
public void setAborted()
```

## Method close

```xpp
public void close()
```

## Method prevPage

```xpp
public void prevPage()
```

## Method setCompleted

```xpp
public void setCompleted()
```

