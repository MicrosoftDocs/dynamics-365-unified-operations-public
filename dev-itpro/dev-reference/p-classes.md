---
# required metadata

title: P Classes
description: System API classes that start with the letter P.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 14 - 22 - 52
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52231
ms.assetid: bab4be7a-314f-4605-8354-031b3e61fc82
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# P Classes

System API classes that start with the letter P.

Class Page
----------

    class Page extends Object

This Page class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                        | Description                                                              |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| public boolean actionPaneControlEnabled(str controlName, \[boolean enabled\]) | Sets or gets the enabled property value of a control on the Action Pane. |
| public boolean actionPaneControlVisible(str controlName, \[boolean visible\]) | Sets or gets the visible property value of a control on the Action Pane. |
| public Array activeActionPaneTabNames()                                       |                                                                          |
| public Common activeRecord(str dataSourceName)                                | Gets the active record for the given data source name.                   |
| public str name()                                                             | Gets the name of the page.                                               |
| public PageArgs pageArgs()                                                    | Gets the page arguments.                                                 |
| public xFormRun formRun()                                                     |                                                                          |

### Method actionPaneControlEnabled

Sets or gets the enabled property value of a control on the Action Pane.

    public boolean actionPaneControlEnabled(str controlName, [boolean enabled])

#### Parameters

controlName  
A value that specifies whether the Action Pane control is enabled; optional.

<!-- -->

enabled  
A value that specifies whether the Action Pane control is enabled; optional.

#### Return Value

A Boolean value that indicates whether the Action Pane control is enabled.

### Method actionPaneControlVisible

Sets or gets the visible property value of a control on the Action Pane.

    public boolean actionPaneControlVisible(str controlName, [boolean visible])

#### Parameters

controlName  
A value that specifies whether the Action Pane control is visible; optional.

<!-- -->

visible  
A value that specifies whether the Action Pane control is visible; optional.

#### Return Value

A Boolean value that indicates whether the Action Pane control is visible.

### Method activeActionPaneTabNames

    public Array activeActionPaneTabNames()

#### Return Value

### Method activeRecord

Gets the active record for the given data source name.

    public Common activeRecord(str dataSourceName)

#### Parameters

dataSourceName  
The name of the data source to search on.

#### Return Value

The active record for the given data source.

### Method name

Gets the name of the page.

    public str name()

#### Return Value

The page name.

### Method pageArgs

Gets the page arguments.

    public PageArgs pageArgs()

#### Return Value

The page arguments.

### Method formRun

    public xFormRun formRun()

#### Return Value

## Class PageArgs
    class PageArgs extends Object

The PageArgs class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                         | Description                                                                                                 |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public int enumParameter(\[int value\])        | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class. |
| public int enumTypeParameter(\[int value\])    | Gets or sets the enumTypeParameter property for the MenuFunction class.                                     |
| public Common externalRecord(\[Common value\]) |                                                                                                             |
| public str menuItemName(\[str value\])         |                                                                                                             |
| public str parameters(\[str value\])           | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.      |
| public void new()                              | Initializes a new instance of the PageArgs class.                                                           |

### Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

    public int enumParameter([int value])

#### Parameters

value  

#### Return Value

The enumParameter property that is passed to the object that is run by the MenuFunction class.

### Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

    public int enumTypeParameter([int value])

#### Parameters

value  

#### Return Value

The enumTypeParameter property for the MenuFunction class.

### Method externalRecord

    public Common externalRecord([Common value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method new

Initializes a new instance of the PageArgs class.

    public void new()

## Class PageInteraction
    class PageInteraction extends Object

The PageInteraction class provides functionality for interacting with a list page.

### Remarks

### Examples

### Methods

| Method                                           | Description                                                        |
|--------------------------------------------------|--------------------------------------------------------------------|
| public Page page()                               | Gets the ListPage instance.                                        |
| public void tabChanged(container activeTabNames) |                                                                    |
| public void new(Page page)                       | Creates a new PageInteraction object that operates on a list page. |

### Method page

Gets the ListPage instance.

    public Page page()

#### Return Value

Returns the ListPage instance for this PageInteraction instance.

### Method tabChanged

    public void tabChanged(container activeTabNames)

#### Parameters

activeTabNames  

### Method new

Creates a new PageInteraction object that operates on a list page.

    public void new(Page page)

#### Parameters

page  

## Class PartList
    class PartList extends Object

### Remarks

### Examples

### Methods

| Method                                        | Description                                     |
|-----------------------------------------------|-------------------------------------------------|
| public xFormRun getPartById(int id)           |                                                 |
| public FormControl getPartControlById(int id) |                                                 |
| public int partCount()                        |                                                 |
| public void new(xFormRun form)                | Initializes a new instance of the Object class. |
| public void finalize()                        |                                                 |

### Method getPartById

    public xFormRun getPartById(int id)

#### Parameters

id  

#### Return Value

### Method getPartControlById

    public FormControl getPartControlById(int id)

#### Parameters

id  

#### Return Value

### Method partCount

    public int partCount()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(xFormRun form)

#### Parameters

form  

### Method finalize

    public void finalize()

## Class Percentbar
    class Percentbar extends Object

### Remarks

### Examples

### Methods

| Method                                   | Description                                         |
|------------------------------------------|-----------------------------------------------------|
| public void new(int maxCount, str title) | Initializes a new instance of the Percentbar class. |
| public void set(int count)               |                                                     |
| public void finalize()                   |                                                     |

### Method new

Initializes a new instance of the Percentbar class.

    public void new(int maxCount, str title)

#### Parameters

maxCount  

<!-- -->

title  

### Method set

    public void set(int count)

#### Parameters

count  

### Method finalize

    public void finalize()

## Class PerformanceMonitor
    class PerformanceMonitor extends Object

The PerformanceMonitor class fetches data for processes that are running on the system.

### Remarks

You can take a snapshot of the system at any time and traverse the counters for any process that is running on the system.

### Examples

The following example prints the processId and workingset values for all the currently running processes.

    static void pvPerformanceMonitorTest(args a) 
    { 
        int i, j;  
        PerformanceMonitorInstance instance;  
        PerformanceMonitorCounter counter1, counter2;  
        PerformanceMonitor pm = new PerformanceMonitor();  
        // Take a current snapshot of the system. 
        pm.takeSnapshot ();  
        // Traverse all the running processes. 
        for (i= 1; i <= pm.instanceCount(); i++)  
        {  
            instance = pm.instance(i);  
            counter1 = instance.getCounter("ID Process");  
            counter2 = instance.getCounter("Working Set");  
            print instance.name(), " ",  
            counter1.intData(), " ",  
            counter2.intData();  
        } 
        pause;  
    }

### Methods

| Method                                                     | Description                                                                                    |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| public PerformanceMonitorInstance instance(int instanceNo) |                                                                                                |
| public int instanceCount()                                 | Returns the instance count, which is the number of processes in the current snapshot.          |
| public int processId()                                     | Returns the processId value of the process that is running this method.                        |
| public str systemName()                                    |                                                                                                |
| public boolean takeSnapshot(\[str processName\])           |                                                                                                |
| public str toString()                                      | Returns a string that contains the class handle and name, and possibly additional information. |
| public void new()                                          | Initializes a new instance of the PerformanceMonitor class.                                    |

### Method instance

    public PerformanceMonitorInstance instance(int instanceNo)

#### Parameters

instanceNo  

#### Return Value

### Method instanceCount

Returns the instance count, which is the number of processes in the current snapshot.

    public int instanceCount()

#### Return Value

The number of processes in the current snapshot.

#### Remarks

Use the takeSnapshot method to take a snapshot of the currently running processes.

#### Examples

    static void pvPerformanceMonitorTest(args a) 
    { 
        int i, j; 
        PerformanceMonitorInstance instance; 
        PerformanceMonitorCounter counter1, counter2; 
        PerformanceMonitor pm = new PerformanceMonitor(); 
        // Take a current snapshot of the system. 
        pm.takeSnapshot (); 
        // Traverse all the running processes. 
        for (i= 1; i <= pm.instanceCount(); i++) 
        { 
            instance = pm.instance(i); 
            counter1 = instance.getCounter("ID Process"); 
            counter2 = instance.getCounter("Working Set"); 
            print instance.name(), " ",  
                counter1.intData(), " ",  
                counter2.intData(); 
        } 
        pause; 
    }

### Method processId

Returns the processId value of the process that is running this method.

    public int processId()

#### Return Value

The processId value of the Microsoft Dynamics AX process that is running this method.

#### Examples

    static void processIdDemo(args a) 
    { 
        PerformanceMonitor pm = new PerformanceMonitor(); 
        print pm.processId(); 
        pause; 
    }

### Method systemName

    public str systemName()

#### Return Value

### Method takeSnapshot

    public boolean takeSnapshot([str processName])

#### Parameters

processName  

#### Return Value

### Method toString

Returns a string that contains the class handle and name, and possibly additional information.

    public str toString()

#### Return Value

A textual description of the class.

#### Remarks

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes, additional information is returned in the string.

### Method new

Initializes a new instance of the PerformanceMonitor class.

    public void new()

## Class PerformanceMonitorCounter
    class PerformanceMonitorCounter extends Object

The PerformanceMonitorCounter class identifies a counter that is assigned to a particular instance of a particular snapshot.

### Remarks

The data can be fetched by using the get methods.

### Examples

### Methods

| Method                 | Description                                                                                    |
|------------------------|------------------------------------------------------------------------------------------------|
| public int intData()   |                                                                                                |
| public str name()      |                                                                                                |
| public Time timeData() |                                                                                                |
| public str toString()  | Returns a string that contains the class handle and name, and possibly additional information. |

### Method intData

    public int intData()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method timeData

    public Time timeData()

#### Return Value

### Method toString

Returns a string that contains the class handle and name, and possibly additional information.

    public str toString()

#### Return Value

A textual description of the class.

#### Remarks

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes additional information is returned in the string.

## Class PerformanceMonitorInstance
    class PerformanceMonitorInstance extends Object

The PerformanceMonitorInstance class represents a process that is running on the machine on which the Process Monitor runs.

### Remarks

This class allows for queries of the process counters. You can use objects of this class to query the processes counters. Each counter represents a process parameter.

### Examples

### Methods

| Method                                                       | Description                                                                                    |
|--------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| public PerformanceMonitorCounter getCounter(str counterName) |                                                                                                |
| public str name()                                            |                                                                                                |
| public str toString()                                        | Returns a string that contains the class handle and name, and possibly additional information. |

### Method getCounter

    public PerformanceMonitorCounter getCounter(str counterName)

#### Parameters

counterName  

#### Return Value

### Method name

    public str name()

#### Return Value

### Method toString

Returns a string that contains the class handle and name, and possibly additional information.

    public str toString()

#### Return Value

Returns a textual description of the class.

#### Remarks

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes additional information is returned in the string.

## Class PipeClient
    class PipeClient extends Object

### Remarks

### Examples

### Methods

| Method                                                              | Description                                         |
|---------------------------------------------------------------------|-----------------------------------------------------|
| public boolean blockingMode(\[boolean block\])                      |                                                     |
| public int errorCode()                                              |                                                     |
| public str read()                                                   |                                                     |
| public boolean write(str buffer)                                    |                                                     |
| public void new(str servername, str pipename, \[boolean blocking\]) | Initializes a new instance of the PipeClient class. |

### Method blockingMode

    public boolean blockingMode([boolean block])

#### Parameters

block  

#### Return Value

### Method errorCode

    public int errorCode()

#### Return Value

### Method read

    public str read()

#### Return Value

### Method write

    public boolean write(str buffer)

#### Parameters

buffer  

#### Return Value

### Method new

Initializes a new instance of the PipeClient class.

    public void new(str servername, str pipename, [boolean blocking])

#### Parameters

servername  

<!-- -->

pipename  

<!-- -->

blocking  

## Class PipeServer
    class PipeServer extends Object

The PipeServer class supports the server side of a named pipe connection.

### Remarks

A named pipe is created when a PipeServer object is created by using the PipeServer.new method. The pipe that is created has read access and is in message mode. The name of the pipe is automatically prefixed with \\\\.\\pipe\\Dynamics. The current session SID is postfixed to the name. The support that is provided for pipe connections on the server is restricted for the following security reasons:

-   The pipe is supported only for the current logon session on the computer that the session was created on.
-   The user who creates the pipe is the only person who can communicate with that pipe.

### Examples

### Methods

| Method                                              | Description                                                                  |
|-----------------------------------------------------|------------------------------------------------------------------------------|
| public boolean blockingMode(\[boolean block\])      |                                                                              |
| public boolean connect()                            | Waits for a client to connect to the named pipe.                             |
| public boolean disconnect()                         | Disconnects the server end of the named pipe instance from a client process. |
| public int errorCode()                              |                                                                              |
| public str read()                                   | Reads data from the named pipe, as written by a pipe client.                 |
| public void new(str pipename, \[boolean blocking\]) | Creates a new instance of the PipeServer class.                              |

### Method blockingMode

    public boolean blockingMode([boolean block])

#### Parameters

block  

#### Return Value

### Method connect

Waits for a client to connect to the named pipe.

    public boolean connect()

#### Return Value

true if the method succeeds; otherwise, false.

#### Remarks

If you do not want to block the current thread if it is waiting for a client to connect, avoid using the PipeServer.connect method, and poll by using the PipeServer.read method instead.

### Method disconnect

Disconnects the server end of the named pipe instance from a client process.

    public boolean disconnect()

#### Return Value

true if the method succeeds; otherwise, false.

### Method errorCode

    public int errorCode()

#### Return Value

### Method read

Reads data from the named pipe, as written by a pipe client.

    public str read()

#### Return Value

The data that is read from the pipe, if any data is read.

#### Remarks

Data might not be available when this method is called, perhaps because no client has connected to the named pipe. If you want to wait for a client to connect, use the connect method. However, if you do not want to block the current thread that is waiting for a client to connect, poll by using the read method.

### Method new

Creates a new instance of the PipeServer class.

    public void new(str pipename, [boolean blocking])

#### Parameters

pipename  
A Boolean flag that indicates whether blocking behavior should be used. Non-blocking mode is supported for compatibility with Microsoft LAN Manager version 2.0 and should not be used to achieve asynchronous I/O with named pipes. Instead, a polling technique should be used. See the read method.

<!-- -->

blocking  
A Boolean flag that indicates whether blocking behavior should be used. Non-blocking mode is supported for compatibility with Microsoft LAN Manager version 2.0 and should not be used to achieve asynchronous I/O with named pipes. Instead, a polling technique should be used. See the read method.

#### Remarks

Some restrictions apply. See the example in the general description of the PipeServer class.

## Class PresenceInfo
    class PresenceInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                                | Description                                           |
|-----------------------------------------------------------------------|-------------------------------------------------------|
| public str contactName(\[str contactName\])                           |                                                       |
| public str emailAddress(int index)                                    |                                                       |
| public str emailAlias(int index)                                      |                                                       |
| public int emailCount()                                               |                                                       |
| public str phoneAlias(int index)                                      |                                                       |
| public int phoneCount()                                               |                                                       |
| public str phoneNumber(int index)                                     |                                                       |
| public str sipAddress(\[str sipAddress\])                             |                                                       |
| public void finalize()                                                |                                                       |
| public void new()                                                     | Initializes a new instance of the PresenceInfo class. |
| public void addEmailAddress(\[str emailAlias\], \[str emailAddress\]) |                                                       |
| public void addPhoneNumber(\[str phoneAlias\], \[str phoneNumber\])   |                                                       |

### Method contactName

    public str contactName([str contactName])

#### Parameters

contactName  

#### Return Value

### Method emailAddress

    public str emailAddress(int index)

#### Parameters

index  

#### Return Value

### Method emailAlias

    public str emailAlias(int index)

#### Parameters

index  

#### Return Value

### Method emailCount

    public int emailCount()

#### Return Value

### Method phoneAlias

    public str phoneAlias(int index)

#### Parameters

index  

#### Return Value

### Method phoneCount

    public int phoneCount()

#### Return Value

### Method phoneNumber

    public str phoneNumber(int index)

#### Parameters

index  

#### Return Value

### Method sipAddress

    public str sipAddress([str sipAddress])

#### Parameters

sipAddress  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the PresenceInfo class.

    public void new()

### Method addEmailAddress

    public void addEmailAddress([str emailAlias], [str emailAddress])

#### Parameters

emailAlias  

<!-- -->

emailAddress  

### Method addPhoneNumber

    public void addPhoneNumber([str phoneAlias], [str phoneNumber])

#### Parameters

phoneAlias  

<!-- -->

phoneNumber  

## Class PrintJobSettings
    class PrintJobSettings extends Object

The PrintJobSettings class lets users access printers and their device settings.

### Remarks

PrintJobSettings is used by the SysPrintForm form.

### Examples

The following example writes the name of the default printer and lists the available printers.

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

### Methods

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

### Method allPages

Controls whether the All or Pages option button should be selected when you run the sysPrintForm.

    public boolean allPages([boolean all])

#### Parameters

all  
A boolean value that, if true, the All option button is selected; otherwise, the Pages option button is selected.

#### Return Value

true if the All radio button should be selected; otherwise, false, and the Pages option button is selected.

#### Remarks

The method is for internal use by sysPrintForm.

#### Examples

The following example prints pages 2 to 4 and selects the Pages option button instead of the All option button.

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

### Method appendToTextFile

    public boolean appendToTextFile([boolean append])

#### Parameters

append  

#### Return Value

### Method banding

    public boolean banding()

#### Return Value

### Method clientPrintJobSettings

    public PrintJobSettings clientPrintJobSettings()

#### Return Value

### Method collate

    public boolean collate([boolean collate])

#### Parameters

collate  

#### Return Value

### Method copies

    public int copies([int numberOfCopies])

#### Parameters

numberOfCopies  

#### Return Value

### Method copyDescription

    public str copyDescription(int number, [str description])

#### Parameters

number  

<!-- -->

description  

#### Return Value

### Method deviceName

Selects a printer or retrieves the deviceName of the selected printer.

    public str deviceName([str device], [ClassRunMode runOn])

#### Parameters

device  

<!-- -->

runOn  

#### Return Value

The deviceName of the selected printer.

#### Remarks

The deviceName of a printer to be selected could be found by using the getPrinter method.

#### Examples

This job lists the available printers and their nonprintable area.

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

### Method doNotOverwrite

    public boolean doNotOverwrite([boolean warn])

#### Parameters

warn  

#### Return Value

### Method enableCopies

    public boolean enableCopies([boolean enable])

#### Parameters

enable  

#### Return Value

### Method enableDevice

    public boolean enableDevice([boolean enable])

#### Parameters

enable  

#### Return Value

### Method enablePages

    public boolean enablePages([boolean enable])

#### Parameters

enable  

#### Return Value

### Method enableProperties

    public boolean enableProperties([boolean enable])

#### Parameters

enable  

#### Return Value

### Method enableStoreInPrintArchive

    public boolean enableStoreInPrintArchive([boolean enable])

#### Parameters

enable  

#### Return Value

### Method enableTarget

    public boolean enableTarget([boolean enable])

#### Parameters

enable  

#### Return Value

### Method facename2number

    public int facename2number([str facename])

#### Parameters

facename  

#### Return Value

### Method fileName

    public str fileName([str FileName])

#### Parameters

FileName  

#### Return Value

### Method fitToPage

    public boolean fitToPage([boolean fit])

#### Parameters

fit  

#### Return Value

### Method format

    public PrintFormat format([PrintFormat format])

#### Parameters

format  

#### Return Value

### Method from

    public int from([int fromPage])

#### Parameters

fromPage  

#### Return Value

### Method getFacename

    public str getFacename(int number)

#### Parameters

number  

#### Return Value

### Method getFacenameInfo

    public str getFacenameInfo(int number)

#### Parameters

number  

#### Return Value

### Method getFontInfo

    public Struct getFontInfo(str fontName)

#### Parameters

fontName  

#### Return Value

### Method getGlyphWidthsArray

    public Array getGlyphWidthsArray(str fontName, int firstChar, int lastChar)

#### Parameters

fontName  

<!-- -->

firstChar  

<!-- -->

lastChar  

#### Return Value

### Method getNumberOfClientPrinters

    public int getNumberOfClientPrinters()

#### Return Value

### Method getNumberOfFacenames

    public int getNumberOfFacenames()

#### Return Value

### Method getNumberOfPrinters

Returns the number of printers that are set up on the computer.

    public int getNumberOfPrinters()

#### Return Value

The number of printers that are set up on the computer.

### Method getNumberOfServerPrinters

    public int getNumberOfServerPrinters()

#### Return Value

### Method getNumberOfTrays

    public int getNumberOfTrays()

#### Return Value

### Method getPrinter

Gets the deviceName of a printer.

    public str getPrinter(int number)

#### Parameters

number  
A value between 1 and the number of available printers.

#### Return Value

The deviceName of the given printer number.

#### Examples

    printJobSettings pjs; 
    int i; 
    pjs = new printJobSettings(); 
    i = 1; 
    while (i<=pjs.GetNumberOfPrinters()) 
    { 
        print "Printer No. ", i, " is ", pjs.GetPrinter(i); 
        i++; 
    }

### Method getRunOn

    public ClassRunMode getRunOn(int number)

#### Parameters

number  

#### Return Value

### Method getTarget

    public PrintMedium getTarget()

#### Return Value

### Method getTray

    public int getTray(int number)

#### Parameters

number  

#### Return Value

### Method getTrayName

    public str getTrayName(int number)

#### Parameters

number  

#### Return Value

### Method hDC

    public Int64 hDC()

#### Return Value

### Method lockDestinationProperties

    public boolean lockDestinationProperties([boolean warn])

#### Parameters

warn  

#### Return Value

### Method mailCc

    public str mailCc([str MailCc])

#### Parameters

MailCc  

#### Return Value

### Method mailSubject

    public str mailSubject([str MailSubject])

#### Parameters

MailSubject  

#### Return Value

### Method mailTo

    public str mailTo([str MailTo])

#### Parameters

MailTo  

#### Return Value

### Method numberOfCopyDescriptions

    public int numberOfCopyDescriptions(int number)

#### Parameters

number  

#### Return Value

### Method outputToClient

    public boolean outputToClient([boolean toClient])

#### Parameters

toClient  

#### Return Value

### Method outputToPrnFile

    public boolean outputToPrnFile([boolean writePrnFile])

#### Parameters

writePrnFile  

#### Return Value

### Method packNamesAndPrinterData

    public container packNamesAndPrinterData()

#### Return Value

### Method packPageSettings

Stores the data that is selected during page formatting in a container.

    public container packPageSettings()

#### Return Value

A container that holds data that is selected during page formatting.

#### Remarks

The returned container can be used as input to the unpackPageSettings method.

### Method packPrinterSettings

    public container packPrinterSettings()

#### Return Value

### Method packPrintJobSettings

    public container packPrintJobSettings()

#### Return Value

### Method packSubtotalSettings

    public container packSubtotalSettings()

#### Return Value

### Method pageCopy2Tray

    public int pageCopy2Tray(int pageNumber, [int copyNumber])

#### Parameters

pageNumber  

<!-- -->

copyNumber  

#### Return Value

### Method pageFormatting

    public boolean pageFormatting()

#### Return Value

### Method paperOrientation

    public PrinterOrientation paperOrientation([PrinterOrientation orientation])

#### Parameters

orientation  

#### Return Value

### Method paperTray

    public int paperTray([int tray])

#### Parameters

tray  

#### Return Value

### Method paperTrayRaw

    public int paperTrayRaw([int tray])

#### Parameters

tray  

#### Return Value

### Method performanceTest

    public int performanceTest([int loops])

#### Parameters

loops  

#### Return Value

### Method preferredFileFormat

    public PrintFormat preferredFileFormat([PrintFormat format])

#### Parameters

format  

#### Return Value

### Method preferredMailFormat

    public PrintFormat preferredMailFormat([PrintFormat format])

#### Parameters

format  

#### Return Value

### Method preferredOrientation

    public PrinterOrientation preferredOrientation([PrinterOrientation orientation])

#### Parameters

orientation  

#### Return Value

### Method preferredTarget

    public PrintMedium preferredTarget([PrintMedium target])

#### Parameters

target  

#### Return Value

### Method printerAttributes

    public int printerAttributes()

#### Return Value

### Method printerAveragePPM

    public int printerAveragePPM()

#### Return Value

### Method printerComment

    public str printerComment()

#### Return Value

### Method printerDatatype

    public str printerDatatype()

#### Return Value

### Method printerDefaultPriority

    public int printerDefaultPriority()

#### Return Value

### Method printerDriverName

    public str printerDriverName()

#### Return Value

### Method printerLocation

    public str printerLocation()

#### Return Value

### Method printerPageHeight

    public int printerPageHeight()

#### Return Value

### Method printerPageWidth

    public int printerPageWidth()

#### Return Value

### Method printerPaper

    public int printerPaper()

#### Return Value

### Method printerParameters

    public str printerParameters()

#### Return Value

### Method printerPortName

    public str printerPortName()

#### Return Value

### Method printerPrinterName

    public str printerPrinterName()

#### Return Value

### Method printerPrintProcessor

    public str printerPrintProcessor()

#### Return Value

### Method printerPriority

    public int printerPriority()

#### Return Value

### Method printerQueuedJobs

    public int printerQueuedJobs()

#### Return Value

### Method printerRunOn

    public ClassRunMode printerRunOn()

#### Return Value

### Method printerSepFile

    public str printerSepFile()

#### Return Value

### Method printerServerName

    public str printerServerName()

#### Return Value

### Method printerSettings

    public boolean printerSettings(str formName, [xArgs args], [ReportRun reportRun], [int showWhat])

#### Parameters

formName  

<!-- -->

args  

<!-- -->

reportRun  

<!-- -->

showWhat  

#### Return Value

### Method printerShareName

    public str printerShareName()

#### Return Value

### Method printerStartTime

    public TimeOfDay printerStartTime()

#### Return Value

### Method printerStatus

    public int printerStatus()

#### Return Value

### Method printerUntilTime

    public TimeOfDay printerUntilTime()

#### Return Value

### Method reportRun

    public ReportRun reportRun()

#### Return Value

### Method requestedDeviceName

    public str requestedDeviceName()

#### Return Value

### Method requestedRunOn

    public ClassRunMode requestedRunOn()

#### Return Value

### Method runClient

    public boolean runClient()

#### Return Value

### Method runServer

    public boolean runServer()

#### Return Value

### Method sectionsPerPage

    public int sectionsPerPage([int sectionsPerPage])

#### Parameters

sectionsPerPage  

#### Return Value

### Method setTarget

Sets the print medium.

    public PrintMedium setTarget(PrintMedium target)

#### Parameters

target  
The print medium.

#### Return Value

The print medium.

### Method singleLargePage

    public boolean singleLargePage([boolean singleLargePage])

#### Parameters

singleLargePage  

#### Return Value

### Method skipBitmapsInRTF

Controls whether bitmaps are included when reports are printed to an .rtf file.

    public boolean skipBitmapsInRTF([boolean skipBitmaps])

#### Parameters

skipBitmaps  
A boolean flag that determines whether bitmaps are included; optional.

#### Return Value

true if the bitmaps are included; otherwise, false.

### Method storeInPrintArchive

    public boolean storeInPrintArchive([boolean store])

#### Parameters

store  

#### Return Value

### Method suppressScalingMessage

    public boolean suppressScalingMessage([boolean suppress])

#### Parameters

suppress  

#### Return Value

### Method to

    public int to([int toPage])

#### Parameters

toPage  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type.For example, an instance of the class returns the method name and type of the method, such as instance or static.

### Method unpackPageSettings

Sets the page settings, such as paper size and orientation.

    public boolean unpackPageSettings(container settings)

#### Parameters

settings  
A container that is obtained by calling the packPageSettings method.

#### Return Value

true if the pageSettings were successfully changed; false if the pageSettings were set to the default values.

#### Remarks

The classes reportDesign and report have a method with the same name.

### Method unpackPrinterSettings

    public boolean unpackPrinterSettings(container settings)

#### Parameters

settings  

#### Return Value

### Method unpackPrintJobSettings

    public boolean unpackPrintJobSettings(container settings)

#### Parameters

settings  

#### Return Value

### Method unpackSubtotalSettings

    public boolean unpackSubtotalSettings(container settings)

#### Parameters

settings  

#### Return Value

### Method unprintableBottom

    public int unprintableBottom()

#### Return Value

### Method unprintableLeft

    public int unprintableLeft()

#### Return Value

### Method unprintableRight

    public int unprintableRight()

#### Return Value

### Method unprintableTop

Indicates the distance from the top of the paper to the printable area of the paper.

    public int unprintableTop()

#### Return Value

The size of nonprintable area, measured in hundredths of a millimeter.

#### Remarks

In reports, the topMargin of a reportDesign must not be less than unprintableTop.

#### Examples

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

### Method viewerType

    public ReportOutputUserType viewerType([ReportOutputUserType type])

#### Parameters

type  

#### Return Value

### Method virtualPageHeight

    public int virtualPageHeight([int height])

#### Parameters

height  

#### Return Value

### Method warnIfFileExists

    public boolean warnIfFileExists([boolean warn])

#### Parameters

warn  

#### Return Value

### Method enableBody

    public void enableBody([TableId tableId])

#### Parameters

tableId  

### Method new

Initializes a new instance of the Object class.

    public void new([container Settings], [boolean infoOnly])

#### Parameters

Settings  

<!-- -->

infoOnly  

### Method addTrayPageCopy

    public void addTrayPageCopy(int tray, int pageNumber, [int copyNumber])

#### Parameters

tray  

<!-- -->

pageNumber  

<!-- -->

copyNumber  

### Method disableBody

    public void disableBody([TableId tableId])

#### Parameters

tableId  

### Method clearTrayPageCopy

    public void clearTrayPageCopy()

### Method rulerInch

    public void rulerInch()

### Method finalize

    public void finalize()

### Method rulerOff

    public void rulerOff()

### Method rulerMetric

    public void rulerMetric()

## Class profiler
    class profiler extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Description                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| public int collected()                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                      |
| public int flushInterval(\[int interval\])                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                      |
| public AnyType profileOff()                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                      |
| public AnyType profileOn(str runId, \[int traceDepth\])                                                                                                                                                                                                                                                                                                                                                                                                         |                                                      |
| public str tempPath()                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                                      |
| public str toString()                                                                                                                                                                                                                                                                                                                                                                                                                                           | Returns a string that represents the current object. |
| ::public static AnyType profilerAlreadyOn()                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                      |
| public void flush()                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                      |
| public void new()                                                                                                                                                                                                                                                                                                                                                                                                                                               | Initializes a new instance of the profiler class.    |
| public void flushData(int lineNumber, str path, int microSecs, int sequenceNumber, int parentSequenceNumber, int selectCalls, int selectBytes, int selectRows, int sqlWaitTime, int aosWaitTime, int sqlInserts, int sqlUpdates, int sqlDeletes, int aosInCalls, int aosOutCalls, int aosInBytes, int aosOutBytes, \[int sqlInsertBytes\], \[int sqlInsertRows\], \[int sqlUpdateBytes\], \[int sqlUpdateRows\], \[int sqlDeleteBytes\], \[int sqlDeleteRows\]) |                                                      |

### Method collected

    public int collected()

#### Return Value

### Method flushInterval

    public int flushInterval([int interval])

#### Parameters

interval  

#### Return Value

### Method profileOff

    public AnyType profileOff()

#### Return Value

### Method profileOn

    public AnyType profileOn(str runId, [int traceDepth])

#### Parameters

runId  

<!-- -->

traceDepth  

#### Return Value

### Method tempPath

    public str tempPath()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type.For example, an instance of the class returns the method name and type of the method, such as instance or static.

### Method profilerAlreadyOn

    public static AnyType profilerAlreadyOn()

#### Return Value

### Method flush

    public void flush()

### Method new

Initializes a new instance of the profiler class.

    public void new()

### Method flushData

    public void flushData(int lineNumber, str path, int microSecs, int sequenceNumber, int parentSequenceNumber, int selectCalls, int selectBytes, int selectRows, int sqlWaitTime, int aosWaitTime, int sqlInserts, int sqlUpdates, int sqlDeletes, int aosInCalls, int aosOutCalls, int aosInBytes, int aosOutBytes, [int sqlInsertBytes], [int sqlInsertRows], [int sqlUpdateBytes], [int sqlUpdateRows], [int sqlDeleteBytes], [int sqlDeleteRows])

#### Parameters

lineNumber  

<!-- -->

path  

<!-- -->

microSecs  

<!-- -->

sequenceNumber  

<!-- -->

parentSequenceNumber  

<!-- -->

selectCalls  

<!-- -->

selectBytes  

<!-- -->

selectRows  

<!-- -->

sqlWaitTime  

<!-- -->

aosWaitTime  

<!-- -->

sqlInserts  

<!-- -->

sqlUpdates  

<!-- -->

sqlDeletes  

<!-- -->

aosInCalls  

<!-- -->

aosOutCalls  

<!-- -->

aosInBytes  

<!-- -->

aosOutBytes  

<!-- -->

sqlInsertBytes  

<!-- -->

sqlInsertRows  

<!-- -->

sqlUpdateBytes  

<!-- -->

sqlUpdateRows  

<!-- -->

sqlDeleteBytes  

<!-- -->

sqlDeleteRows  

## Class ProgressWindow
    class ProgressWindow extends Object

### Remarks

### Examples

### Methods

| Method                                                      | Description                                             |
|-------------------------------------------------------------|---------------------------------------------------------|
| public int addProgressControl(\[int progressControlCount\]) |                                                         |
| public void ProgressBarVisible(int index, int visible)      |                                                         |
| public void ProgressValue(int index, int progressValue)     |                                                         |
| public void ControlMinMax(int index, int min, int max)      |                                                         |
| public void ProgressTextVisible(int index, int visible)     |                                                         |
| public void Animation(str animation)                        |                                                         |
| public void ControlText(int index, str text)                |                                                         |
| public void FormCaption(str text)                           |                                                         |
| public void ControlTime(str text)                           |                                                         |
| public void finalize()                                      |                                                         |
| public void new()                                           | Initializes a new instance of the ProgressWindow class. |

### Method addProgressControl

    public int addProgressControl([int progressControlCount])

#### Parameters

progressControlCount  

#### Return Value

### Method ProgressBarVisible

    public void ProgressBarVisible(int index, int visible)

#### Parameters

index  

<!-- -->

visible  

### Method ProgressValue

    public void ProgressValue(int index, int progressValue)

#### Parameters

index  

<!-- -->

progressValue  

### Method ControlMinMax

    public void ControlMinMax(int index, int min, int max)

#### Parameters

index  

<!-- -->

min  

<!-- -->

max  

### Method ProgressTextVisible

    public void ProgressTextVisible(int index, int visible)

#### Parameters

index  

<!-- -->

visible  

### Method Animation

    public void Animation(str animation)

#### Parameters

animation  

### Method ControlText

    public void ControlText(int index, str text)

#### Parameters

index  

<!-- -->

text  

### Method FormCaption

    public void FormCaption(str text)

#### Parameters

text  

### Method ControlTime

    public void ControlTime(str text)

#### Parameters

text  

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the ProgressWindow class.

    public void new()

## Class ProjectGroupNode
    class ProjectGroupNode extends TreeNode

The ProjectGroupNode class represents a group node within a project.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

### Examples

### Methods

| Method                                                                                       | Description                                                                                                                                   |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode findGroupMember(str name, UtilElementType type, \[boolean searchSubgroups\]) | Searches the projectGroup for a specific element. It can be used to search a specific group or the whole project.                             |
| public str groupMask(\[str value\])                                                          |                                                                                                                                               |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public boolean preventEditProperties(\[boolean value\])                                      |                                                                                                                                               |
| public GroupNodeType projectGroupType(\[GroupNodeType value\])                               |                                                                                                                                               |
| public void addUtilNode(UtilElementType type, str name)                                      | Adds a node to the projectGroup.                                                                                                              |
| public void addNode(TreeNode node)                                                           | Adds an existing node to the projectGroup.                                                                                                    |

### Method findGroupMember

Searches the projectGroup for a specific element. It can be used to search a specific group or the whole project.

    public TreeNode findGroupMember(str name, UtilElementType type, [boolean searchSubgroups])

#### Parameters

name  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

<!-- -->

type  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

<!-- -->

searchSubgroups  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

#### Return Value

The first object that fits the criteria; returns nullNothingnullptrunita null reference (Nothing in Visual Basic) if no object is found.

#### Remarks

This method is also found on ProjectNode.

### Method groupMask

    public str groupMask([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method preventEditProperties

    public boolean preventEditProperties([boolean value])

#### Parameters

value  

#### Return Value

### Method projectGroupType

    public GroupNodeType projectGroupType([GroupNodeType value])

#### Parameters

value  

#### Return Value

### Method addUtilNode

Adds a node to the projectGroup.

    public void addUtilNode(UtilElementType type, str name)

#### Parameters

type  
The name of the node.

<!-- -->

name  
The name of the node.

#### Remarks

This method also is found on the ProjectNode class.

### Method addNode

Adds an existing node to the projectGroup.

    public void addNode(TreeNode node)

#### Parameters

node  
The node to add.

## Class ProjectListNode
    class ProjectListNode extends TreeNode

The ProjectListNode class corresponds to the Private and Shared lists of projects in the project overview window. Use the ProjectListNode.addProject method to add a new project from X++ code.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                                               | Description                     |
|----------------------------------------------------------------------|---------------------------------|
| public ProjectNode addProject(str projectName, \[str projectClass\]) | Adds a new project to the list. |

### Method addProject

Adds a new project to the list.

    public ProjectNode addProject(str projectName, [str projectClass])

#### Parameters

projectName  
The name of the projecttype; optional. This should be the name of a class associated with the project (see the setProjectClass method). If no value is supplied, the project becomes a standard project.

<!-- -->

projectClass  
The name of the projecttype; optional. This should be the name of a class associated with the project (see the setProjectClass method). If no value is supplied, the project becomes a standard project.

#### Return Value

The newly added projectNode.

## Class ProjectNode
    class ProjectNode extends TreeNode

The ProjectNode class controls the behavior of an AOT project.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Create a new, user-defined AOT project by extending from this class. Control the behavior of the project by overriding the methods of this class. Create both Web projects and Help projects by creating classes that extend the ProjectNode class.

### Examples

### Methods

| Method                                                                                       | Description                                                                                                                                   |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str addContextMenuItems()                                                             | Adds a list of items to the shortcut menu of the project node.                                                                                |
| public str changedBy(\[str value\])                                                          | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                                      | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                                        | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                                                          | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                                     | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                                       |                                                                                                                                               |
| public str export(str buffer)                                                                |                                                                                                                                               |
| public TreeNode findGroupMember(str name, UtilElementType type, \[boolean searchSubgroups\]) | Searches the project or group for a specific element.                                                                                         |
| public str getProjectClassName()                                                             | Returns the name of the class corresponding to the classid of the project.                                                                    |
| public ProjectNode getRunNode()                                                              | Opens the project window and returns the root projectNode of that window, for a particular projectNode found in the project overview window.  |
| public str import(str buffer)                                                                |                                                                                                                                               |
| public boolean isRunNode()                                                                   |                                                                                                                                               |
| public ProjectNode loadForInspection()                                                       | Returns a loaded version of a projectNode found in the project overview window.                                                               |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                                                           |                                                                                                                                               |
| public boolean removeFromProject(TreeNode node)                                              |                                                                                                                                               |
| public str tooltipText(TreeNode node)                                                        |                                                                                                                                               |
| ::public static str projectType()                                                            |                                                                                                                                               |
| public void lockUpdate()                                                                     | Prevents visual updates while a series of actions is being performed.                                                                         |
| public void addSpecialOverlayIcon(str path, int resId, \[int xOffset\], \[int yOffset\])     |                                                                                                                                               |
| public void created(str name)                                                                | Enables the ability to perform custom actions on a project when a new instance of the project is created.                                     |
| public void setSpecialIcon(int type, str name, int resId)                                    | Assigns a different icon to a specific node in the project.                                                                                   |
| public void loadProject(str buffer)                                                          | Enables storing and retrieving custom data in the project definition when a project is loaded.                                                |
| public void saveProject(str buffer)                                                          | Enables saving custom data together with the project in the application object database.                                                      |
| public void unlockUpdate()                                                                   | Enables a visual update after a series of actions started with lockUpdate.                                                                    |
| public void handleContextMenuItem(int id)                                                    | Handles a user selecting an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.                  |
| public void addNode(TreeNode node)                                                           | Adds an existing node to the project.                                                                                                         |
| public void addUtilNode(UtilElementType type, str name)                                      | Adds a node to the project.                                                                                                                   |
| public void clear()                                                                          | Removes the contents of a project.                                                                                                            |
| public void setProjectClass(int classid)                                                     | Assigns a class to the project, which gives the project the type that the class defines.                                                      |
| public void removeSpecialOverlayIcons(str path)                                              |                                                                                                                                               |
| public void new()                                                                            | Initializes a new instance of the ProjectNode class.                                                                                          |

### Method addContextMenuItems

Adds a list of items to the shortcut menu of the project node.

    public str addContextMenuItems()

#### Return Value

A comma-separated list of the menu items to be added.

#### Remarks

Override this method to add a list of items to the shortcut menu of the project node. When one of the added menu items is selected by a user, the handleContextMenuItem method is called. Override this method to perform the appropriate action.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method export

    public str export(str buffer)

#### Parameters

buffer  

#### Return Value

### Method findGroupMember

Searches the project or group for a specific element.

    public TreeNode findGroupMember(str name, UtilElementType type, [boolean searchSubgroups])

#### Parameters

name  
A Boolean flag to determine whether the search should be recursive; optional.

<!-- -->

type  
A Boolean flag to determine whether the search should be recursive; optional.

<!-- -->

searchSubgroups  
A Boolean flag to determine whether the search should be recursive; optional.

#### Return Value

The first object that fits the criteria, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if no object is found.

#### Remarks

This method is also found on ProjectGroupNode.

### Method getProjectClassName

Returns the name of the class corresponding to the classid of the project.

    public str getProjectClassName()

#### Return Value

The name of the class corresponding to the classid of the project.

#### Remarks

The setClassId method assigns a classid to the project.

### Method getRunNode

Opens the project window and returns the root projectNode of that window, for a particular projectNode found in the project overview window.

    public ProjectNode getRunNode()

#### Return Value

The running projectNode.

#### Remarks

To obtain a running projectNode without opening the project window, use the ProjectNode.loadForInspection Method.

### Method import

    public str import(str buffer)

#### Parameters

buffer  

#### Return Value

### Method isRunNode

    public boolean isRunNode()

#### Return Value

### Method loadForInspection

Returns a loaded version of a projectNode found in the project overview window.

    public ProjectNode loadForInspection()

#### Return Value

The loaded projectNode.

#### Remarks

To get a loaded projectNode while also opening the project window, use the method getRunNode.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method removeFromProject

    public boolean removeFromProject(TreeNode node)

#### Parameters

node  

#### Return Value

### Method tooltipText

    public str tooltipText(TreeNode node)

#### Parameters

node  

#### Return Value

### Method projectType

    public static str projectType()

#### Return Value

### Method lockUpdate

Prevents visual updates while a series of actions is being performed.

    public void lockUpdate()

#### Remarks

To perform visual updates after the series of actions, call unlockUpdate.

### Method addSpecialOverlayIcon

    public void addSpecialOverlayIcon(str path, int resId, [int xOffset], [int yOffset])

#### Parameters

path  

<!-- -->

resId  

<!-- -->

xOffset  

<!-- -->

yOffset  

### Method created

Enables the ability to perform custom actions on a project when a new instance of the project is created.

    public void created(str name)

#### Parameters

name  
The name of the project instance.

#### Remarks

This method is called when a new instance of the project is created. Override this method to perform custom actions on your project.

### Method setSpecialIcon

Assigns a different icon to a specific node in the project.

    public void setSpecialIcon(int type, str name, int resId)

#### Parameters

type  
The ID of the icon that must be used for the specified node.

<!-- -->

name  
The ID of the icon that must be used for the specified node.

<!-- -->

resId  
The ID of the icon that must be used for the specified node.

### Method loadProject

Enables storing and retrieving custom data in the project definition when a project is loaded.

    public void loadProject(str buffer)

#### Parameters

buffer  
A string that contains the custom data that was saved in the project by saveProject.

#### Remarks

This method is called when a project is loaded. By overriding saveProject and loadProject, a user can store and retrieve custom data in the project definition. You must call super() for the project to continue loading.

### Method saveProject

Enables saving custom data together with the project in the application object database.

    public void saveProject(str buffer)

#### Parameters

buffer  
A string buffer that must be used for packing the data. The buffer must then be passed on to super().

#### Remarks

By overriding this method, you can save custom data together with the project in the application object database. It is recommended that the data be formed as an XML string in the following form: "&lt;APPDATA&gt; ... &lt;/APPDATA&gt;" The data can be retrieved by overriding the loadProject method.

### Method unlockUpdate

Enables a visual update after a series of actions started with lockUpdate.

    public void unlockUpdate()

### Method handleContextMenuItem

Handles a user selecting an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.

    public void handleContextMenuItem(int id)

#### Parameters

id  
The ID of the menu items. This is the zero-based number in the list set by the addContextMenuItems method. If accContextMenuItems returns the string "item1,item2" and the user selects the item "item2" in the shortcut menu, this method uses the value 1.

#### Remarks

This method is called when a user selects an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.

### Method addNode

Adds an existing node to the project.

    public void addNode(TreeNode node)

#### Parameters

node  
The node to add.

### Method addUtilNode

Adds a node to the project.

    public void addUtilNode(UtilElementType type, str name)

#### Parameters

type  
The name of the node.

<!-- -->

name  
The name of the node.

#### Remarks

This function is also found on ProjectGroupNode.

### Method clear

Removes the contents of a project.

    public void clear()

#### Remarks

This method does not remove the project contents from the Application Object Tree (AOT)—only from the project itself. This method removes the project contents but does not remove the project folder. To delete a project and its contents in one method call, use the AOTdelete method. To delete objects from the AOT, use the AOTdelete method.

#### Examples

The following example removes any objects in the Project1 project in the Private folder.

    static void clearProjectObjects(Args _args) 
        { 
            ProjectNode privatePn; 
            ProjectNode pn; 
            // Navigate to the Private projects folder. 
            privatePn = infolog.projectRootNode().AOTfindChild("Private"); 
            // Get a reference to the project. 
            pn = privatePn.AOTfindChild("Project1"); 
            // Clear the project. 
            pn.clear(); 
        }

### Method setProjectClass

Assigns a class to the project, which gives the project the type that the class defines.

    public void setProjectClass(int classid)

#### Parameters

classid  
The ID of the class to assign to the project.

#### Remarks

The specified class must extend the projectNode class.

### Method removeSpecialOverlayIcons

    public void removeSpecialOverlayIcons(str path)

#### Parameters

path  

### Method new

Initializes a new instance of the ProjectNode class.

    public void new()

## Class PropertiesWindow
    class PropertiesWindow extends Object

### Remarks

### Examples

### Methods

| Method                                                   | Description |
|----------------------------------------------------------|-------------|
| public int Activate(PropWindowDisplayState displaystate) |             |
| public boolean DockFrame(PropWindowDockState dockstate)  |             |
| public str GetSelectedPropertyName()                     |             |
| public boolean IsVisible()                               |             |
| public boolean SelectPropertyByName(str propname)        |             |
| public boolean SelectTab(PropWindowSelectTab selecttab)  |             |

### Method Activate

    public int Activate(PropWindowDisplayState displaystate)

#### Parameters

displaystate  

#### Return Value

### Method DockFrame

    public boolean DockFrame(PropWindowDockState dockstate)

#### Parameters

dockstate  

#### Return Value

### Method GetSelectedPropertyName

    public str GetSelectedPropertyName()

#### Return Value

### Method IsVisible

    public boolean IsVisible()

#### Return Value

### Method SelectPropertyByName

    public boolean SelectPropertyByName(str propname)

#### Parameters

propname  

#### Return Value

### Method SelectTab

    public boolean SelectTab(PropWindowSelectTab selecttab)

#### Parameters

selecttab  

#### Return Value

