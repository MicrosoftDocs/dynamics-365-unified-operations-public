---
title: PrintJobSettings class
description: This topic describes the PrintJobSettings class.
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

# Class PrintJobSettings

[!include [banner](../../includes/banner.md)]

```xpp
class PrintJobSettings extends Object
```

The PrintJobSettings class lets users access printers and their device settings.

## Remarks

PrintJobSettings is used by the SysPrintForm form.

## Examples

The following example writes the name of the default printer and lists the available printers.

```xpp
void printerInfo() 
{    
    printJobSettings pjs; 
    int i; 
    pjs = new PrintJobSettings(); 
    print "The default printer is ", pjs.DeviceName(); 
    print "There are ", pjs.GetNumberOfPrinters(), " printers"; 
    i = 1; 
    while (i<=pjs.GetNumberOfPrinters())  
    { 
        print "Printer No. ", i, " is ", pjs.GetPrinter(i);  
        i++; 
    } 
    pause; 
}
```

## Methods

| Method                                                                                                  | Description                                                                                       |
|---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| public boolean allPages(\[boolean all\])                                                                | Controls whether the All or Pages option button should be selected when you run the sysPrintForm. |
| public boolean appendToTextFile(\[boolean append\])                                                     |                                                                                                   |
| public boolean banding()                                                                                |                                                                                                   |
| public PrintJobSettings clientPrintJobSettings()                                                        |                                                                                                   |
| public boolean collate(\[boolean collate\])                                                             |                                                                                                   |
| public int copies(\[int numberOfCopies\])                                                               |                                                                                                   |
| public str copyDescription(int number, \[str description\])                                             |                                                                                                   |
| public str deviceName(\[str device\], \[ClassRunMode runOn\])                                           | Selects a printer or retrieves the deviceName of the selected printer.                            |
| public boolean doNotOverwrite(\[boolean warn\])                                                         |                                                                                                   |
| public boolean enableCopies(\[boolean enable\])                                                         |                                                                                                   |
| public boolean enableDevice(\[boolean enable\])                                                         |                                                                                                   |
| public boolean enablePages(\[boolean enable\])                                                          |                                                                                                   |
| public boolean enableProperties(\[boolean enable\])                                                     |                                                                                                   |
| public boolean enableStoreInPrintArchive(\[boolean enable\])                                            |                                                                                                   |
| public boolean enableTarget(\[boolean enable\])                                                         |                                                                                                   |
| public int facename2number(\[str facename\])                                                            |                                                                                                   |
| public str fileName(\[str FileName\])                                                                   |                                                                                                   |
| public boolean fitToPage(\[boolean fit\])                                                               |                                                                                                   |
| public PrintFormat format(\[PrintFormat format\])                                                       |                                                                                                   |
| public int from(\[int fromPage\])                                                                       |                                                                                                   |
| public str getFacename(int number)                                                                      |                                                                                                   |
| public str getFacenameInfo(int number)                                                                  |                                                                                                   |
| public Struct getFontInfo(str fontName)                                                                 |                                                                                                   |
| public Array getGlyphWidthsArray(str fontName, int firstChar, int lastChar)                             |                                                                                                   |
| public int getNumberOfClientPrinters()                                                                  |                                                                                                   |
| public int getNumberOfFacenames()                                                                       |                                                                                                   |
| public int getNumberOfPrinters()                                                                        | Returns the number of printers that are set up on the computer.                                   |
| public int getNumberOfServerPrinters()                                                                  |                                                                                                   |
| public int getNumberOfTrays()                                                                           |                                                                                                   |
| public str getPrinter(int number)                                                                       | Gets the deviceName of a printer.                                                                 |
| public ClassRunMode getRunOn(int number)                                                                |                                                                                                   |
| public PrintMedium getTarget()                                                                          |                                                                                                   |
| public int getTray(int number)                                                                          |                                                                                                   |
| public str getTrayName(int number)                                                                      |                                                                                                   |
| public Int64 hDC()                                                                                      |                                                                                                   |
| public boolean lockDestinationProperties(\[boolean warn\])                                              |                                                                                                   |
| public str mailCc(\[str MailCc\])                                                                       |                                                                                                   |
| public str mailSubject(\[str MailSubject\])                                                             |                                                                                                   |
| public str mailTo(\[str MailTo\])                                                                       |                                                                                                   |
| public int numberOfCopyDescriptions(int number)                                                         |                                                                                                   |
| public boolean outputToClient(\[boolean toClient\])                                                     |                                                                                                   |
| public boolean outputToPrnFile(\[boolean writePrnFile\])                                                |                                                                                                   |
| public container packNamesAndPrinterData()                                                              |                                                                                                   |
| public container packPageSettings()                                                                     | Stores the data that is selected during page formatting in a container.                           |
| public container packPrinterSettings()                                                                  |                                                                                                   |
| public container packPrintJobSettings()                                                                 |                                                                                                   |
| public container packSubtotalSettings()                                                                 |                                                                                                   |
| public int pageCopy2Tray(int pageNumber, \[int copyNumber\])                                            |                                                                                                   |
| public boolean pageFormatting()                                                                         |                                                                                                   |
| public PrinterOrientation paperOrientation(\[PrinterOrientation orientation\])                          |                                                                                                   |
| public int paperTray(\[int tray\])                                                                      |                                                                                                   |
| public int paperTrayRaw(\[int tray\])                                                                   |                                                                                                   |
| public int performanceTest(\[int loops\])                                                               |                                                                                                   |
| public PrintFormat preferredFileFormat(\[PrintFormat format\])                                          |                                                                                                   |
| public PrintFormat preferredMailFormat(\[PrintFormat format\])                                          |                                                                                                   |
| public PrinterOrientation preferredOrientation(\[PrinterOrientation orientation\])                      |                                                                                                   |
| public PrintMedium preferredTarget(\[PrintMedium target\])                                              |                                                                                                   |
| public int printerAttributes()                                                                          |                                                                                                   |
| public int printerAveragePPM()                                                                          |                                                                                                   |
| public str printerComment()                                                                             |                                                                                                   |
| public str printerDatatype()                                                                            |                                                                                                   |
| public int printerDefaultPriority()                                                                     |                                                                                                   |
| public str printerDriverName()                                                                          |                                                                                                   |
| public str printerLocation()                                                                            |                                                                                                   |
| public int printerPageHeight()                                                                          |                                                                                                   |
| public int printerPageWidth()                                                                           |                                                                                                   |
| public int printerPaper()                                                                               |                                                                                                   |
| public str printerParameters()                                                                          |                                                                                                   |
| public str printerPortName()                                                                            |                                                                                                   |
| public str printerPrinterName()                                                                         |                                                                                                   |
| public str printerPrintProcessor()                                                                      |                                                                                                   |
| public int printerPriority()                                                                            |                                                                                                   |
| public int printerQueuedJobs()                                                                          |                                                                                                   |
| public ClassRunMode printerRunOn()                                                                      |                                                                                                   |
| public str printerSepFile()                                                                             |                                                                                                   |
| public str printerServerName()                                                                          |                                                                                                   |
| public boolean printerSettings(str formName, \[xArgs args\], \[ReportRun reportRun\], \[int showWhat\]) |                                                                                                   |
| public str printerShareName()                                                                           |                                                                                                   |
| public TimeOfDay printerStartTime()                                                                     |                                                                                                   |
| public int printerStatus()                                                                              |                                                                                                   |
| public TimeOfDay printerUntilTime()                                                                     |                                                                                                   |
| public ReportRun reportRun()                                                                            |                                                                                                   |
| public str requestedDeviceName()                                                                        |                                                                                                   |
| public ClassRunMode requestedRunOn()                                                                    |                                                                                                   |
| public boolean runClient()                                                                              |                                                                                                   |
| public boolean runServer()                                                                              |                                                                                                   |
| public int sectionsPerPage(\[int sectionsPerPage\])                                                     |                                                                                                   |
| public PrintMedium setTarget(PrintMedium target)                                                        | Sets the print medium.                                                                            |
| public boolean singleLargePage(\[boolean singleLargePage\])                                             |                                                                                                   |
| public boolean skipBitmapsInRTF(\[boolean skipBitmaps\])                                                | Controls whether bitmaps are included when reports are printed to an .rtf file.                   |
| public boolean storeInPrintArchive(\[boolean store\])                                                   |                                                                                                   |
| public boolean suppressScalingMessage(\[boolean suppress\])                                             |                                                                                                   |
| public int to(\[int toPage\])                                                                           |                                                                                                   |
| public str toString()                                                                                   | Returns a string that represents the current object.                                              |
| public boolean unpackPageSettings(container settings)                                                   | Sets the page settings, such as paper size and orientation.                                       |
| public boolean unpackPrinterSettings(container settings)                                                |                                                                                                   |
| public boolean unpackPrintJobSettings(container settings)                                               |                                                                                                   |
| public boolean unpackSubtotalSettings(container settings)                                               |                                                                                                   |
| public int unprintableBottom()                                                                          |                                                                                                   |
| public int unprintableLeft()                                                                            |                                                                                                   |
| public int unprintableRight()                                                                           |                                                                                                   |
| public int unprintableTop()                                                                             | Indicates the distance from the top of the paper to the printable area of the paper.              |
| public ReportOutputUserType viewerType(\[ReportOutputUserType type\])                                   |                                                                                                   |
| public int virtualPageHeight(\[int height\])                                                            |                                                                                                   |
| public boolean warnIfFileExists(\[boolean warn\])                                                       |                                                                                                   |
| public void enableBody(\[TableId tableId\])                                                             |                                                                                                   |
| public void new(\[container Settings\], \[boolean infoOnly\])                                           | Initializes a new instance of the Object class.                                                   |
| public void addTrayPageCopy(int tray, int pageNumber, \[int copyNumber\])                               |                                                                                                   |
| public void disableBody(\[TableId tableId\])                                                            |                                                                                                   |
| public void clearTrayPageCopy()                                                                         |                                                                                                   |
| public void rulerInch()                                                                                 |                                                                                                   |
| public void finalize()                                                                                  |                                                                                                   |
| public void rulerOff()                                                                                  |                                                                                                   |
| public void rulerMetric()                                                                               |                                                                                                   |

## Method allPages

Controls whether the All or Pages option button should be selected when you run the sysPrintForm.

```xpp
public boolean allPages([boolean all])
```

### Parameters - allPages

all  
A boolean value that, if true, the All option button is selected; otherwise, the Pages option button is selected.

### Return Value - allPages

true if the All radio button should be selected; otherwise, false, and the Pages option button is selected.

### Remarks - allPages

The method is for internal use by sysPrintForm.

### Examples - allPages

The following example prints pages 2 to 4 and selects the Pages option button instead of the All option button.

```xpp
static void PrintingToPDF(Args _args) 
{ 
    Args                args; 
    ReportRun           rr; 
    str reportName = 'Cust'; 
    int i; 
    int numReports = 10; 
    args = new Args(reportName); 
    rr = new ReportRun(args,''); 
    rr.setTarget(Printmedium::File); 
    rr.printJobSettings().format(PrintFormat::RTF); 
    rr.printJobSettings().fileName("C:\\tmp\\Cust_ReportRange2.rtf"); 
    // Select the Pages option button rather than the All option button. 
    rr.printJobSettings().allPages(false); 
    rr.printJobSettings().from(2); 
    rr.printJobSettings().to(4); 
    rr.query().interactive(false); 
    rr.report().interactive(false); 
    rr.run(); 
}
```

## Method appendToTextFile

```xpp
public boolean appendToTextFile([boolean append])
```

### Parameters - appendToTextFile

append  

### Return Value - appendToTextFile

## Method banding

```xpp
public boolean banding()
```

### Return Value - banding

## Method clientPrintJobSettings

```xpp
public PrintJobSettings clientPrintJobSettings()
```

### Return Value - clientPrintJobSettings

## Method collate

```xpp
public boolean collate([boolean collate])
```

### Parameters - collate

collate  

### Return Value - collate

## Method copies

```xpp
public int copies([int numberOfCopies])
```

### Parameters - copies

numberOfCopies  

### Return Value - copies

## Method copyDescription

```xpp
public str copyDescription(int number, [str description])
```

### Parameters - copyDescription

number  

<!-- -->

description  

### Return Value - copyDescription

## Method deviceName

Selects a printer or retrieves the deviceName of the selected printer.

```xpp
public str deviceName([str device], [ClassRunMode runOn])
```

### Parameters - deviceName

device  

<!-- -->

runOn  

### Return Value - deviceName

The deviceName of the selected printer.

### Remarks - deviceName

The deviceName of a printer to be selected could be found by using the getPrinter method.

### Examples - deviceName

This job lists the available printers and their nonprintable area.

```xpp
static void aaaKJ(args a) 
{ 
    printJobSettings pjs; 
    str printer; 
    int i; 
    pjs = new printJobSettings(); 
    for (i=1; i<=pjs.GetNumberOfPrinters(); i++) 
    { 
        printer = pjs.GetPrinter(i); 
        pjs.DeviceName(printer); 
        print "printer No. ",i, " has name ",  printer; 
        print "   left:  ", pjs.UnprintableLeft(),   "/100 mm"; 
        print "   right: ", pjs.UnprintableRight(),  "/100 mm"; 
        print "   top:   ", pjs.UnprintableTop(),    "/100 mm"; 
        print "   bottom:", pjs.UnprintableBottom(), "/100 mm"; 
    } 
    pause; 
}
```

## Method doNotOverwrite

```xpp
public boolean doNotOverwrite([boolean warn])
```

### Parameters - doNotOverwrite

warn  

### Return Value - doNotOverwrite

## Method enableCopies

```xpp
public boolean enableCopies([boolean enable])
```

### Parameters - enableCopies

enable  

### Return Value - enableCopies

## Method enableDevice

```xpp
public boolean enableDevice([boolean enable])
```

### Parameters - enableDevice

enable  

### Return Value - enableDevice

## Method enablePages

```xpp
public boolean enablePages([boolean enable])
```

### Parameters - enablePages

enable  

### Return Value - enablePages

## Method enableProperties

```xpp
public boolean enableProperties([boolean enable])
```

### Parameters - enableProperties

enable  

### Return Value - enableProperties

## Method enableStoreInPrintArchive

```xpp
public boolean enableStoreInPrintArchive([boolean enable])
```

### Parameters - enableStoreInPrintArchive

enable  

### Return Value - enableStoreInPrintArchive

## Method enableTarget

```xpp
public boolean enableTarget([boolean enable])
```

### Parameters - enableTarget

enable  

### Return Value - enableTarget

## Method facename2number

```xpp
public int facename2number([str facename])
```

### Parameters - facename2number

facename  

### Return Value - facename2number

## Method fileName

```xpp
public str fileName([str FileName])
```

### Parameters - fileName

FileName  

### Return Value - fileName

## Method fitToPage

```xpp
public boolean fitToPage([boolean fit])
```

### Parameters - fitToPage

fit  

### Return Value - fitToPage

## Method format

```xpp
public PrintFormat format([PrintFormat format])
```

### Parameters - format

format  

### Return Value - format

## Method from

```xpp
public int from([int fromPage])
```

### Parameters - from

fromPage  

### Return Value - from

## Method getFacename

```xpp
public str getFacename(int number)
```

### Parameters - getFacename

number  

### Return Value - getFacename

## Method getFacenameInfo

```xpp
public str getFacenameInfo(int number)
```

### Parameters - getFacenameInfo

number  

### Return Value - getFacenameInfo

## Method getFontInfo

```xpp
public Struct getFontInfo(str fontName)
```

### Parameters - getFontInfo

fontName  

### Return Value - getFontInfo

## Method getGlyphWidthsArray

```xpp
public Array getGlyphWidthsArray(str fontName, int firstChar, int lastChar)
```

### Parameters - getGlyphWidthsArray

fontName  

<!-- -->

firstChar  

<!-- -->

lastChar  

### Return Value - getGlyphWidthsArray

## Method getNumberOfClientPrinters

```xpp
public int getNumberOfClientPrinters()
```

### Return Value - getNumberOfClientPrinters

## Method getNumberOfFacenames

```xpp
public int getNumberOfFacenames()
```

### Return Value - getNumberOfFacenames

## Method getNumberOfPrinters

Returns the number of printers that are set up on the computer.

```xpp
public int getNumberOfPrinters()
```

### Return Value - getNumberOfPrinters

The number of printers that are set up on the computer.

## Method getNumberOfServerPrinters

```xpp
public int getNumberOfServerPrinters()
```

### Return Value - getNumberOfServerPrinters

## Method getNumberOfTrays

```xpp
public int getNumberOfTrays()
```

### Return Value - getNumberOfTrays

## Method getPrinter

Gets the deviceName of a printer.

```xpp
public str getPrinter(int number)
```

### Parameters - getPrinter

number  
A value between 1 and the number of available printers.

### Return Value - getPrinter

The deviceName of the given printer number.

### Examples - getPrinter

```xpp
printJobSettings pjs; 
int i; 
pjs = new printJobSettings(); 
i = 1; 
while (i<=pjs.GetNumberOfPrinters()) 
{ 
    print "Printer No. ", i, " is ", pjs.GetPrinter(i); 
    i++; 
}
```

## Method getRunOn

```xpp
public ClassRunMode getRunOn(int number)
```

### Parameters - getRunOn

number  

### Return Value - getRunOn

## Method getTarget

```xpp
public PrintMedium getTarget()
```

### Return Value - getTarget

## Method getTray

```xpp
public int getTray(int number)
```

### Parameters - getTray

number  

### Return Value - getTray

## Method getTrayName

```xpp
public str getTrayName(int number)
```

### Parameters - getTrayName

number  

### Return Value - getTrayName

## Method hDC

```xpp
public Int64 hDC()
```

### Return Value - hDC

## Method lockDestinationProperties

```xpp
public boolean lockDestinationProperties([boolean warn])
```

### Parameters - lockDestinationProperties

warn  

### Return Value - lockDestinationProperties

## Method mailCc

```xpp
public str mailCc([str MailCc])
```

### Parameters - mailCc

MailCc  

### Return Value - mailCc

## Method mailSubject

```xpp
public str mailSubject([str MailSubject])
```

### Parameters - mailSubject

MailSubject  

### Return Value - mailSubject

## Method mailTo

```xpp
public str mailTo([str MailTo])
```

### Parameters - mailTo

MailTo  

### Return Value - mailTo

## Method numberOfCopyDescriptions

```xpp
public int numberOfCopyDescriptions(int number)
```

### Parameters - numberOfCopyDescriptions

number  

### Return Value - numberOfCopyDescriptions

## Method outputToClient

```xpp
public boolean outputToClient([boolean toClient])
```

### Parameters - outputToClient

toClient  

### Return Value - outputToClient

## Method outputToPrnFile

```xpp
public boolean outputToPrnFile([boolean writePrnFile])
```

### Parameters - outputToPrnFile

writePrnFile  

### Return Value - outputToPrnFile

## Method packNamesAndPrinterData

```xpp
public container packNamesAndPrinterData()
```

### Return Value - packNamesAndPrinterData

## Method packPageSettings

Stores the data that is selected during page formatting in a container.

```xpp
public container packPageSettings()
```

### Return Value - packPageSettings

A container that holds data that is selected during page formatting.

### Remarks - packPageSettings

The returned container can be used as input to the unpackPageSettings method.

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

## Method pageCopy2Tray

```xpp
public int pageCopy2Tray(int pageNumber, [int copyNumber])
```

### Parameters - pageCopy2Tray

pageNumber  

<!-- -->

copyNumber  

### Return Value - pageCopy2Tray

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

## Method paperTrayRaw

```xpp
public int paperTrayRaw([int tray])
```

### Parameters - paperTrayRaw

tray  

### Return Value - paperTrayRaw

## Method performanceTest

```xpp
public int performanceTest([int loops])
```

### Parameters - performanceTest

loops  

### Return Value - performanceTest

## Method preferredFileFormat

```xpp
public PrintFormat preferredFileFormat([PrintFormat format])
```

### Parameters - preferredFileFormat

format  

### Return Value - preferredFileFormat

## Method preferredMailFormat

```xpp
public PrintFormat preferredMailFormat([PrintFormat format])
```

### Parameters - preferredMailFormat

format  

### Return Value - preferredMailFormat

## Method preferredOrientation

```xpp
public PrinterOrientation preferredOrientation([PrinterOrientation orientation])
```

### Parameters - preferredOrientation

orientation  

### Return Value - preferredOrientation

## Method preferredTarget

```xpp
public PrintMedium preferredTarget([PrintMedium target])
```

### Parameters - preferredTarget

target  

### Return Value - preferredTarget

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

## Method printerRunOn

```xpp
public ClassRunMode printerRunOn()
```

### Return Value - printerRunOn

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
public boolean printerSettings(str formName, [xArgs args], [ReportRun reportRun], [int showWhat])
```

### Parameters - printerSettings

formName  

<!-- -->

args  

<!-- -->

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

## Method reportRun

```xpp
public ReportRun reportRun()
```

### Return Value - reportRun

## Method requestedDeviceName

```xpp
public str requestedDeviceName()
```

### Return Value - requestedDeviceName

## Method requestedRunOn

```xpp
public ClassRunMode requestedRunOn()
```

### Return Value - requestedRunOn

## Method runClient

```xpp
public boolean runClient()
```

### Return Value - runClient

## Method runServer

```xpp
public boolean runServer()
```

### Return Value - runServer

## Method sectionsPerPage

```xpp
public int sectionsPerPage([int sectionsPerPage])
```

### Parameters - sectionsPerPage

sectionsPerPage  

### Return Value - sectionsPerPage

## Method setTarget

Sets the print medium.

```xpp
public PrintMedium setTarget(PrintMedium target)
```

### Parameters - setTarget

target  
The print medium.

### Return Value - setTarget

The print medium.

## Method singleLargePage

```xpp
public boolean singleLargePage([boolean singleLargePage])
```

### Parameters - singleLargePage

singleLargePage  

### Return Value - singleLargePage

## Method skipBitmapsInRTF

Controls whether bitmaps are included when reports are printed to an .rtf file.

```xpp
public boolean skipBitmapsInRTF([boolean skipBitmaps])
```

### Parameters - skipBitmapsInRTF

skipBitmaps  
A boolean flag that determines whether bitmaps are included; optional.

### Return Value - skipBitmapsInRTF

true if the bitmaps are included; otherwise, false.

## Method storeInPrintArchive

```xpp
public boolean storeInPrintArchive([boolean store])
```

### Parameters - storeInPrintArchive

store  

### Return Value - storeInPrintArchive

## Method suppressScalingMessage

```xpp
public boolean suppressScalingMessage([boolean suppress])
```

### Parameters - suppressScalingMessage

suppress  

### Return Value - suppressScalingMessage

## Method to

```xpp
public int to([int toPage])
```

### Parameters - to

toPage  

### Return Value - to

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the class returns the method name and type of the method, such as instance or static.

## Method unpackPageSettings

Sets the page settings, such as paper size and orientation.

```xpp
public boolean unpackPageSettings(container settings)
```

### Parameters - unpackPageSettings

settings  
A container that is obtained by calling the packPageSettings method.

### Return Value - unpackPageSettings

true if the pageSettings were successfully changed; false if the pageSettings were set to the default values.

### Remarks - unpackPageSettings

The classes reportDesign and report have a method with the same name.

## Method unpackPrinterSettings

```xpp
public boolean unpackPrinterSettings(container settings)
```

### Parameters - unpackPrinterSettings

settings  

### Return Value - unpackPrinterSettings

## Method unpackPrintJobSettings

```xpp
public boolean unpackPrintJobSettings(container settings)
```

### Parameters - unpackPrintJobSettings

settings  

### Return Value - unpackPrintJobSettings

## Method unpackSubtotalSettings

```xpp
public boolean unpackSubtotalSettings(container settings)
```

### Parameters - unpackSubtotalSettings

settings  

### Return Value - unpackSubtotalSettings

## Method unprintableBottom

```xpp
public int unprintableBottom()
```

### Return Value - unprintableBottom

## Method unprintableLeft

```xpp
public int unprintableLeft()
```

### Return Value - unprintableLeft

## Method unprintableRight

```xpp
public int unprintableRight()
```

### Return Value - unprintableRight

## Method unprintableTop

Indicates the distance from the top of the paper to the printable area of the paper.

```xpp
public int unprintableTop()
```

### Return Value - unprintableTop

The size of nonprintable area, measured in hundredths of a millimeter.

### Remarks - unprintableTop

In reports, the topMargin of a reportDesign must not be less than unprintableTop.

### Examples - unprintableTop

```xpp
static void printerInfo(args a) 
{ 
    printJobSettings pjs; 
    str printer; 
    int i; 
    pjs = new printJobSettings(); 
    for (i=1; i<=pjs.GetNumberOfPrinters(); i++) 
    { 
        printer = pjs.GetPrinter(i); 
        pjs.DeviceName(printer); 
        print "printer No. ",i, " has name ",  printer; 
        print "   left:   ", pjs.UnprintableLeft(),   "/100 mm"; 
        print "   right:  ", pjs.UnprintableRight(),  "/100 mm"; 
        print "   totalWidth: ", pjs.UnprintableLeft() +  
            pjs.PrinterPageWidth() + pjs.UnprintableRight(); 
        print "   top:    ", pjs.UnprintableTop(),    "/100 mm"; 
        print "   bottom: ", pjs.UnprintableBottom(), "/100 mm"; 
        print "   totalHeight: ", pjs.UnprintableTop() +  
            pjs.PrinterPageHeight() + pjs.UnprintableBottom(); 
    } 
    pause; 
}
```

## Method viewerType

```xpp
public ReportOutputUserType viewerType([ReportOutputUserType type])
```

### Parameters - viewerType

type  

### Return Value - viewerType

## Method virtualPageHeight

```xpp
public int virtualPageHeight([int height])
```

### Parameters - virtualPageHeight

height  

### Return Value - virtualPageHeight

## Method warnIfFileExists

```xpp
public boolean warnIfFileExists([boolean warn])
```

### Parameters - warnIfFileExists

warn  

### Return Value - warnIfFileExists

## Method enableBody

```xpp
public void enableBody([TableId tableId])
```

### Parameters - enableBody

tableId  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([container Settings], [boolean infoOnly])
```

### Parameters - new

Settings  

<!-- -->

infoOnly  

## Method addTrayPageCopy

```xpp
public void addTrayPageCopy(int tray, int pageNumber, [int copyNumber])
```

### Parameters - addTrayPageCopy

tray  

<!-- -->

pageNumber  

<!-- -->

copyNumber  

## Method disableBody

```xpp
public void disableBody([TableId tableId])
```

### Parameters - disableBody

tableId  

## Method clearTrayPageCopy

```xpp
public void clearTrayPageCopy()
```

## Method rulerInch

```xpp
public void rulerInch()
```

## Method finalize

```xpp
public void finalize()
```

## Method rulerOff

```xpp
public void rulerOff()
```

## Method rulerMetric

```xpp
public void rulerMetric()
```

