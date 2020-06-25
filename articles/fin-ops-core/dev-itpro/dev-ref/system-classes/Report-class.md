---
title: Report class
description: This topic describes the Report class.
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

# Class Report

[!include [banner](../../includes/banner.md)]

```xpp
class Report extends TreeNode
```

The Report class lets users use reports that are present in the Application Object Tree (AOT) and report creation by using code instead of the AOT.

## Remarks

A Report object contains a query and zero or more designs. Each design is a definition of the layout of a report that can be displayed on screen or printed. A Report object also has ReportRun methods that can be overridden. This class enables you to create, read, update, and delete X++ code and metadata.

## Examples

The following code example creates and runs a report that is not present in the AOT.

```xpp
static void test(args a) 
{ 
    report r; 
    reportDesign rd; 
    reportSection rs; 
    reportRun rr; 
    // Creates a simple report that is not present in  
    // the AOT. 
    r = new report(); 
    rd = r.addDesign("myDesign"); 
    // Adds a section that is triggered by execute(1). 
    rs = rd.addProgrammableSection(1);
    rs.addTextControl("Hello world"); 
    // Runs the report. 
    rr = new reportRun(r); 
    // Runs the SysPrintForm form. 
    if (rr.prompt())  
    { 
        // Executes the programmable section. 
        rr.execute(1);  
        // Prints the report to the target selected 
        // during the previous prompt call. 
        rr.print();    
    } 
}
```

## Methods

| Method                                                              | Description                                                                                                                               |
|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportDesign addDesign(\[str name\], \[container buffer\])   | Creates a reportDesign that belongs to a report.                                                                                          |
| public boolean allowCheck(\[boolean value\])                        |                                                                                                                                           |
| public boolean autoJoin(\[boolean value\])                          |                                                                                                                                           |
| public str changedBy(\[str value\])                                 | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                             | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                               | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                                 | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                            | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                              |                                                                                                                                           |
| public ReportDesign design(\[str name\])                            | Retrieves an existing design.                                                                                                             |
| public int designCount()                                            | Retrieves the number of designs in a given report.                                                                                        |
| public ReportDesign designNumber(\[int number\])                    | Gets an existing design.                                                                                                                  |
| public boolean interactive(\[boolean value\])                       |                                                                                                                                           |
| public str name(\[str value\])                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                                  |                                                                                                                                           |
| public container pack()                                             | Serializes the current instance of the Report class.                                                                                      |
| public Query query(\[Query query\])                                 |                                                                                                                                           |
| public boolean saved()                                              | Indicates whether the report has been saved to disk.                                                                                      |
| public void new(\[AnyType nameOrContainer\], \[AnyType container\]) | Initializes a new instance of the TreeNode class.                                                                                         |
| public void dump()                                                  | Writes an overview of the report's contents to the Infolog.                                                                               |

## Method addDesign

Creates a reportDesign that belongs to a report.

```xpp
public ReportDesign addDesign([str name], [container buffer])
```

### Parameters - addDesign

name  
Lets the design have the contents given by buffer.

<!-- -->

buffer  
Lets the design have the contents given by buffer.

### Return Value - addDesign

The created reportDesign.

### Remarks - addDesign

The buffer argument can be a container created by the pack method.

### Examples - addDesign

This job demonstrates how addDesign can be used to generate a design that is a copy of another design.

```xpp
static void demoAddDesign(args a) 
{  
    report r1; 
    report r2; 
    reportDesign rd; 
    reportSection rs; 
    reportRun rr; 
    container c; 
    // Create a simple report r1. 
    r1 = new report(); 
    rd = r1.addDesign("Design1"); 
    rs = rd.addProgrammableSection(1); 
    rs.addTextControl("Hello world"); 
    c = rd.Pack(); // make a container containing r1's design 
    // Create a report r2 having a design that is a copy of r1's design. 
    r2 = new report(); 
    r2.AddDesign("design2", c); 
    // Run the report. 
    rr = new reportRun(r2, "design2"); 
    // Run the sysPrintForm form. 
    if (rr.prompt()) 
    { 
        // Execute the programableSection. 
        rr.execute(1);  
        // Print report to the target, such as printer or screen. 
        rr.print();    
    } 
}
```

## Method allowCheck

```xpp
public boolean allowCheck([boolean value])
```

### Parameters - allowCheck

value  

### Return Value - allowCheck

## Method autoJoin

```xpp
public boolean autoJoin([boolean value])
```

### Parameters - autoJoin

value  

### Return Value - autoJoin

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

## Method creationDate

Gets or sets the date an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

The date an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method design

Retrieves an existing design.

```xpp
public ReportDesign design([str name])
```

### Parameters - design

name  
The name of the report to be returned; optional.

### Return Value - design

The design that has the specified name, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if it was not found.

### Remarks - design

If no argument is supplied and the report only contains one design, the method returns the one design.

### Examples - design

```xpp
static void testDesign(args a) 
{ 
    report r; 
    reportDesign rd; 
    r = new report("Cust"); 
    rd = r.Design(); 
    if (rd) 
        print "a) r.design() : ", rd.Name(); 
    rd = r.Design(""); 
    if (rd) 
        print "b) r.design(emptyString) : ", rd.Name(); 
    rd = r.Design('customer'); 
    if (rd) 
        print "c) r.design(customer) : ", rd.Name(); 
    pause; 
}
```

## Method designCount

Retrieves the number of designs in a given report.

```xpp
public int designCount()
```

### Return Value - designCount

The number of designs.

### Examples - designCount

```xpp
static void testDesign(args a) 
{ 
    report r = new report(); 
    print "A newly created report has ", r.DesignCount(), " designs"; 
    pause; 
}
```

## Method designNumber

Gets an existing design.

```xpp
public ReportDesign designNumber([int number])
```

### Parameters - designNumber

number  
An integer that specifies the desired design; optional.

### Return Value - designNumber

The specified reportDesign, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if the design did not exist.

### Remarks - designNumber

If number is &lt; 1, design 1 is returned.

### Examples - designNumber

```xpp
void testDesign(args a) 
{ 
    report r; 
    reportDesign rd; 
    int i; 
    r = new report("myReport"); 
    if (r.DesignCount() == 0) 
    { 
        print "The report has no designs"; pause; 
    } 
    for (i=1; i<=r.DesignCount();i++) 
    { 
        rd = r.DesignNumber(i); 
        print "Design No. ", i, " has name ", rd.Name(); 
    } 
    pause; 
}
```

## Method interactive

```xpp
public boolean interactive([boolean value])
```

### Parameters - interactive

value  

### Return Value - interactive

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

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method pack

Serializes the current instance of the Report class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the Report class.

### Remarks - pack

The returned container can be used as first argument to the report constructor.

### Examples - pack

The following example stores a report named "cust" in a container and runs the report in the container (not the container in the AOT).

```xpp
static void testReportPack(args a) 
{ 
    report r1; 
    report r2; 
    reportRun rr; 
    container c; 
    r1 = new report("cust"); 
    c = r1.Pack(); 
    r2 = new report(c); 
    rr = new reportrun(r2); 
    rr.Run(); 
}
```

## Method query

```xpp
public Query query([Query query])
```

### Parameters - query

query  

### Return Value - query

## Method saved

Indicates whether the report has been saved to disk.

```xpp
public boolean saved()
```

### Return Value - saved

true if the report has been saved to disc; otherwise false.

### Remarks - saved

A report in the AOT can only be run if it has been saved to disk.

### Examples - saved

```xpp
static void testReportSaved(args a) 
{ 
    report r; 
    reportRun rr; 
    r = new report(); 
    r.AddDesign(); 
    print "before save, saved : ", r.Saved(); pause; 
    r.saved(); 
    print "after save, saved : ", r.Saved(); pause; 
    rr = new reportrun(r); 
    rr.Run(); 
}
```

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new([AnyType nameOrContainer], [AnyType container])
```

### Parameters - new

nameOrContainer  

<!-- -->

container  

### Remarks - new

The parameter format is as follows:

-   () � Creates a report object that is not present in the AOT.
-   (c) � Creates a report object that is not present in the AOT, the contents of which are given by the container c.
-   ("existingReportName") � Retrieves a report object that is found in the AOT.
-   ("nonExistingReportName") � Creates a report object in the AOT.
-   ("nonExistingReportName", c) � Creates a report object in the AOT, the contents of which are given by the container c.

The container c should be created by the pack method.

## Method dump

Writes an overview of the report's contents to the Infolog.

```xpp
public void dump()
```

### Remarks - dump

The lines written to the Infolog are identical to the information shown when you expand the report in the AOT.

### Examples - dump

```xpp
static void testReportDump(args a) 
{ 
    report r = new report("cust"); 
    r.Dump(); 
}
```

