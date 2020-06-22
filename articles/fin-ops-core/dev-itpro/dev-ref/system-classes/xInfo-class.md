---
title: xInfo class
description: This topic describes the xInfo class.
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

# Class xInfo

[!include [banner](../../includes/banner.md)]

```xpp
class xInfo extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                       | Description                                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int removeMessage(Int64 messageId)                                                                                                                                                                    |                                                                                                                                                                                         |
| public Int64 insertMessage(MessageSeverity type, str message)                                                                                                                                                |                                                                                                                                                                                         |
| public Exception add(Exception exceptionType, str string, \[str helpURL\], \[Object obj\], \[boolean buildprefix\])                                                                                          | Adds a string to the Infolog buffer.                                                                                                                                                    |
| public Exception addException(str string, str stackTrace)                                                                                                                                                    |                                                                                                                                                                                         |
| public container breakpoint(\[container breakpoint\])                                                                                                                                                        | Gets or sets information about breakpoints.                                                                                                                                             |
| public boolean canShowCreateRuleMenuItem(xFormRun caller)                                                                                                                                                    | Determines whether the menu item for the Create alert rule form should be displayed for a form.                                                                                         |
| public boolean canShutdown(boolean silent)                                                                                                                                                                   | Tests whether the system can be shut down. Do not use this method. Use the version that is overridden on the Info class instead.                                                        |
| public boolean canViewAlertInbox()                                                                                                                                                                           | Determines whether the current user has permission to view the View alerts form.                                                                                                        |
| public xCompilerOutput compilerOutput(\[Object compilerOut\])                                                                                                                                                | Gets or sets the compiler output object. The compiler output object is the Compiler output window by default.                                                                           |
| public container copy(int from, int to)                                                                                                                                                                      | Copies lines from the Infolog buffer.                                                                                                                                                   |
| public int createDevelopmentWorkspaceWindow()                                                                                                                                                                |                                                                                                                                                                                         |
| public int createWorkspaceWindow()                                                                                                                                                                           | Opens a new workspace window. For example, this enables you to open different sets of application objects in different windows, or to work with two different sets of company accounts. |
| public UtilEntryLevel currentAOLayer()                                                                                                                                                                       | Retrieves the current layer you are running in such as SYS, or USR.                                                                                                                     |
| public container cut(int from, int to)                                                                                                                                                                       | Cuts lines from the Infolog buffer.                                                                                                                                                     |
| public str documentationLanguage(\[str languageCode\])                                                                                                                                                       | Gets or sets the language that is used for the documentation.                                                                                                     |
| public container export()                                                                                                                                                                                    |                                                                                                                                                                                         |
| public TreeNode findNode(str nodePath)                                                                                                                                                                       | Retrieves the specified a tree node.                                                                                                                                                    |
| public TreeNode getDocNode(UtilFileType helpType, int UtilType, str Name, \[UtilElementId ParentId\], \[int Type\], \[UtilEntryLevel UtilLevel\], \[boolean ForceLevel\], \[int Mode\], \[boolean OldUtil\]) | Retrieves the specified documentation nodes from the AOT.                                                                                                                               |
| public TreeNode getImportedNode(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)                                                                                    | Creates an instance of a tree node from an XPO file but does not import it into the AOT. For example, this allows you to compare it with another version of the same tree node.         |
| public TreeNode getNode(UtilElementType UtilType, str Name, \[UtilElementId ParentId\], \[int Type\], \[UtilEntryLevel Utillevel\], \[boolean Forcelevel\], \[int Mode\], \[boolean OldUtil\])               | Retrieves a tree node that corresponds to a node in the AOT.                                                                                                                            |
| public int getNodeResid(UtilElementType nodeType)                                                                                                                                                            | Retrieves the resource ID for the icon that is used to display nodes of the specified type.                                                                                             |
| public Struct getTaskInfo(int taskNumber)                                                                                                                                                                    |                                                                                                                                                                                         |
| public UserSetup getUserSetup()                                                                                                                                                                              | Retrieves a UserSetup object that is used to set user parameters.                                                                                                                       |
| public container getWorkspaceList()                                                                                                                                                                          |                                                                                                                                                                                         |
| public int hWnd(\[int workspaceNum\])                                                                                                                                                                        | Retrieves a handle to the Navigation Pane window.                                                                                                                  |
| public boolean import(container infologContainer, \[boolean clearExistingInfolog\])                                                                                                                          |                                                                                                                                                                                         |
| public int importElement(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)                                                                                           | Specifies the object to be imported.                                                                                                                                                    |
| public int importString(str source, UtilElementType kind, str name)                                                                                                                                          | Imports an object from a file.                                                                                                                                                          |
| public int instance()                                                                                                                                                                                        | Retrieves a handle to the current instance of the application.                                                                                                                          |
| public str isoCurrencyCode(\[str code\])                                                                                                                                                                     | Gets or sets the currency code.                                                                                                                                                         |
| public boolean IsVisible()                                                                                                                                                                                   | Determines whether the client window is not minimized.                                                                                                                                  |
| public str language(\[str languageCode\])                                                                                                                                                                    | Gets or sets the language for the GUI.                                                                                                                                                  |
| public Exception level(int line)                                                                                                                                                                             | Retrieves the exception level of a line in the Infolog buffer.                                                                                                                          |
| public int line()                                                                                                                                                                                            | Retrieves the number of lines in the Infolog buffer.                                                                                                                                    |
| public MessageWin messageWin()                                                                                                                                                                               | Enables you to send output from the Infolog to the Message window.                                                                                                                      |
| public Real nationalCurrencyFactor(\[Real factor\])                                                                                                                                                          |                                                                                                                                                                                         |
| public str nationalCurrencyPostfix(\[str string\])                                                                                                                                                           |                                                                                                                                                                                         |
| public str nationalCurrencyPrefix(\[str string\])                                                                                                                                                            |                                                                                                                                                                                         |
| public xNavPane navPane()                                                                                                                                                                                    | Retrieves an xNavPane object, the primary navigation control class.                                                                                                                     |
| public int num(\[Exception exceptionType\])                                                                                                                                                                  | Retrieves the number of exceptions of the specified type in the Infolog buffer.                                                                                                         |
| public int prevInstance()                                                                                                                                                                                    | Retrieves a handle to the previous instance of the application.                                                                                                                         |
| public int processId()                                                                                                                                                                                       | Retrieves the ID for the process.                                                                                                                                 |
| public TreeNode projectRootNode()                                                                                                                                                                            | Returns the X++ Projects node.                                                                                                                                                          |
| public TreeNode rootNode()                                                                                                                                                                                   | Retrieves the root of the application object tree.                                                                                                                                      |
| public int startImport(str file, int flag, \[str labelSubstitutes\])                                                                                                                                         | Creates an import context.                                                                                                                                                              |
| public str text(\[int line\])                                                                                                                                                                                | Retrieves a line of text from the Infolog.                                                                                                                                              |
| public TreeNode userNode()                                                                                                                                                                                   |                                                                                                                                                                                         |
| public AnyType webSession(\[AnyType value\])                                                                                                                                                                 |                                                                                                                                                                                         |
| ::public static container activeXControls()                                                                                                                                                                  | Retrieves a list of the ActiveX controls.                                                                                                             |
| ::public static str AOTLogDirectory()                                                                                                                                                                        | Gets the path to the log directory for the current installation.                                                                                                                        |
| ::public static container automationObjects()                                                                                                                                                                | Retrieves the list of COM objects that are available.                                                                                                          |
| ::public static str buildNo()                                                                                                                                                                                | Retrieves the kernel build number of the current executable.                                                                                                      |
| ::public static str compilationDate()                                                                                                                                                                        | Retrieves the date on which the current version was last compiled.                                                                                             |
| ::public static str compilationTime()                                                                                                                                                                        | Retrieves the time at which the current version was last compiled.                                                                                             |
| ::public static str componentName()                                                                                                                                                                          | Retrieves the path to the component.                                                                                                                                                    |
| ::public static str configuration()                                                                                                                                                                          | Retrieves the current client configuration.                                                                                                                                             |
| ::public static int currentWorkspaceNum()                                                                                                                                                                    | Retrieves the application window ID of the current workspace.                                                                                                                           |
| ::public static str directory(DirectoryType type)                                                                                                                                                            | Retrieves the path to the directory where the client has been installed.                                                                                          |
| ::public static Date expireDate()                                                                                                                                                                            | Retrieves the date on which the license for the current installation expires.                                                                                                           |
| ::public static ApplicationObjectTreeWindow getApplicationObjectTreeWindow()                                                                                                                                 |                                                                                                                                                                                         |
| ::public static int getCurrentModelId()                                                                                                                                                                      |                                                                                                                                                                                         |
| ::public static int getNumberOfDecimals(Real number)                                                                                                                                                         | Retrieves the number of decimal places in the specified number.                                                                                                                         |
| ::public static PropertiesWindow getPropertiesWindow()                                                                                                                                                       |                                                                                                                                                                                         |
| ::public static int getSystemGeneratedModelId(UtilEntryLevel layer)                                                                                                                                          |                                                                                                                                                                                         |
| ::public static str licenseName()                                                                                                                                                                            | Retrieves the name of the current license.                                                                                                                        |
| ::public static str productName()                                                                                                                                                                            | Retrieves the name of the product.                                                                                                                                                      |
| ::public static str productRegisteredName()                                                                                                                                                                  |                                                                                                                                                                                         |
| ::public static str releaseVersion()                                                                                                                                                                         | Retrieves the version number of the current executable; for example: 3.0, or 4.0.                                                                                 |
| ::public static str releaseYear()                                                                                                                                                                            |                                                                                                                                                                                         |
| ::public static str serialNo()                                                                                                                                                                               | Retrieves the serial number of the current license.                                                                                                               |
| public void new()                                                                                                                                                                                            | Initializes a new xInfo object.                                                                                                                                                         |
| public void workspaceWindowDestroyed(int hWnd)                                                                                                                                                               | Executes when a workspace is closed.                                                                                                                                                    |
| public void writeCustomStatlineItem(str text)                                                                                                                                                                | Writes a line of text to the status bar.                                                                                                                                                |
| public void reloadRunningMode()                                                                                                                                                                              |                                                                                                                                                                                         |
| public void setWindowOrder(int window, \[int afterWindow\])                                                                                                                                                  | Sets the order in which windows should be displayed.                                                                                                                                    |
| public void shutDown(boolean force)                                                                                                                                                                          | Shuts down the client.                                                                                                                                                                  |
| public void xref(str path, xRef x)                                                                                                                                                                           | Executes when the cross-reference system is used.                                                                                                                                       |
| public void updateCurrentCompany()                                                                                                                                                                           |                                                                                                                                                                                         |
| public void redrawAllWindows()                                                                                                                                                                               | Redraws all windows.                                                                                                                                                                    |
| public void formNotify(xFormRun form, FormNotify notification, \[FormNotifyEventArgs formNotifyEventArgs\])                                                                                                  | Executes based on a particular type of change to a specific form, allowing custom code to run.                                                                                          |
| public void mayReloadMenu(boolean value)                                                                                                                                                                     | Prevents the UI from refreshing.                                                                                                                                                        |
| public void startLengthyOperation()                                                                                                                                                                          | Sets the mouse cursor to idle.                                                                                                                                                          |
| public void breakpointNotify(BreakpointNotify notification)                                                                                                                                                  | Implements a notification system when a breakpoint is changed.                                                                                                                          |
| public void initializeInfolog(int window)                                                                                                                                                                    |                                                                                                                                                                                         |
| public void startup(str startupCmd)                                                                                                                                                                          | Executes when the client starts.                                                                                                                                                        |
| public void endImport(int id, int elements)                                                                                                                                                                  | Completes an import process.                                                                                                                                                            |
| public void yield()                                                                                                                                                                                          |                                                                                                                                                                                         |
| public void viewAlertInbox(\[int selectedTab\])                                                                                                                                                              | Launches the View alerts form.                                                                                                                                                          |
| public void reportSendMailServer(PrintJobSettings settings)                                                                                                                                                  |                                                                                                                                                                                         |
| public void endLengthyOperation(\[boolean endAll\])                                                                                                                                                          | Sets the mouse cursor back to normal after a call to startLengthyOperation.                                                                                                             |
| public void setNumUnreadAlerts(\[int n\])                                                                                                                                                                    | Refreshes the status bar text when the number of unread Alert e-mails changes.                                                                                                          |
| public void truncate(str prefix)                                                                                                                                                                             | Removes the items with the specified prefix from the Infolog.                                                                                                                           |
| public void formNoteButton(boolean enable, boolean value)                                                                                                                                                    | Controls the Document handling button on the toolbar.                                                                                                                                   |
| public void viewCreateRuleDialog(xFormRun caller)                                                                                                                                                            | Launches the Create alert rule form.                                                                                                                                                    |
| public void view(\[container container\])                                                                                                                                                                    |                                                                                                                                                                                         |
| public void clear(\[int linesLeft\])                                                                                                                                                                         | Deletes lines from the Infolog buffer.                                                                                                                                                  |
| public void workspaceWindowCreated(int hWnd)                                                                                                                                                                 | Executes when a new workspace is created.                                                                                                                                               |
| ::public static void setCurrentModelId(int currentModelId)                                                                                                                                                   |                                                                                                                                                                                         |
| public void activateMenubarTask(int command)                                                                                                                                                                 |                                                                                                                                                                                         |
| public void finalize()                                                                                                                                                                                       |                                                                                                                                                                                         |
| public void insertXReferences()                                                                                                                                                                              |                                                                                                                                                                                         |
| public void activateButton(int command)                                                                                                                                                                      |                                                                                                                                                                                         |
| public void activateWindow(int window)                                                                                                                                                                       | Sets the focus on a form or Window.                                                                                                                                                     |
| public void reportSendMail(PrintJobSettings settings)                                                                                                                                                        | Generates the settings for sending a report by email.                                                                                                                                   |

## Method removeMessage

```xpp
public int removeMessage(Int64 messageId)
```

### Parameters - removeMessage

messageId  

### Return Value - removeMessage

## Method insertMessage

```xpp
public Int64 insertMessage(MessageSeverity type, str message)
```

### Parameters - insertMessage

type  

<!-- -->

message  

### Return Value - insertMessage

## Method add

Adds a string to the Infolog buffer.

```xpp
public Exception add(Exception exceptionType, str string, [str helpURL], [Object obj], [boolean buildprefix])
```

### Parameters - add

exceptionType  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

string  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

helpURL  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

obj  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

buildprefix  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

### Return Value - add

An Exception system enumeration value. For more information, see Exception Handling with try and catch Keywords.

### Remarks - add

An example value for the helpURL parameter is 'KernDoc:\\\\\\\\Functions\\\\substr'. This method should not be used directly. Instead, use the infolog.info, infolog.warning, infolog.error, or infolog.checkFailed method instead. For more information about the exceptionType parameter, see Exception Handling with try and catch Keywords.

## Method addException

```xpp
public Exception addException(str string, str stackTrace)
```

### Parameters - addException

string  

<!-- -->

stackTrace  

### Return Value - addException

## Method breakpoint

Gets or sets information about breakpoints.

```xpp
public container breakpoint([container breakpoint])
```

### Parameters - breakpoint

breakpoint  
A container that holds information about the current breakpoints.

### Return Value - breakpoint

A container holding information about the current breakpoints.

### Remarks - breakpoint

The container that holds information about breakpoints is of the format:

-   Item 1: Version number
-   Items 2 - 4, 5-7, � n - n+2: Information about each breakpoint, consisting of:

```xpp
-   the AOT path
-   the line number on which the breakpoint is set
-   whether the breakpoint is enabled or disabled
```

In the application, this method is used by the Breakpoints form. When the form is opened it calls the getBreakpoints method on the form. This calls the xInfo.breakpoint method, and uses a container with the breakpoint information as a parameter. When a breakpoint is disabled, enabled, or deleted from the form, the setBreakpoints method is called. This updates the information about the breakpoints and returns this as a container using the xInfo.breakpoint method without using the breakpoint parameter. The container is used to update the breakpoint information in the Code Editor window.

## Method canShowCreateRuleMenuItem

Determines whether the menu item for the Create alert rule form should be displayed for a form.

```xpp
public boolean canShowCreateRuleMenuItem(xFormRun caller)
```

### Parameters - canShowCreateRuleMenuItem

caller  
The current form: the form from which the Create alert rule menu item can be displayed.

### Return Value - canShowCreateRuleMenuItem

true if the current form supports the creation of alerts; otherwise false.

## Method canShutdown

Tests whether the system can be shut down. Do not use this method. Use the version that is overridden on the Info class instead.

```xpp
public boolean canShutdown(boolean silent)
```

### Parameters - canShutdown

silent  
A Boolean that determines whether users are asked if they want to exit the system.

### Return Value - canShutdown

true of the system can be shut down; otherwise false.

## Method canViewAlertInbox

Determines whether the current user has permission to view the View alerts form.

```xpp
public boolean canViewAlertInbox()
```

### Return Value - canViewAlertInbox

true if the user has permission to view the form; otherwise, false.

### Remarks - canViewAlertInbox

Call this method before calling xInfo.viewAlertInbox.

## Method compilerOutput

Gets or sets the compiler output object. The compiler output object is the Compiler output window by default.

```xpp
public xCompilerOutput compilerOutput([Object compilerOut])
```

### Parameters - compilerOutput

compilerOut  
A compiler output object; optional. Optional parameter.

### Return Value - compilerOutput

An xCompilerOutput object.

### Remarks - compilerOutput

The default value of the compilerOut parameter is the Compiler output window, but it can also be the Message window.

## Method copy

Copies lines from the Infolog buffer.

```xpp
public container copy(int from, int to)
```

### Parameters - copy

from  
The last line to copy.

<!-- -->

to  
The last line to copy.

### Return Value - copy

Container that contains the Infolog lines between from and to.

### Examples - copy

The following example uses the copy method to copy the content of the Infolog into a log.

```xpp
boolean validateRecord() 
{ 
    boolean     ok = true; 
    ok = intrastat.validateRecord(); 
    if (ok) 
        intrastat.log = ''; 
    else 
    { 
        intrastat.log = Info::infoCon2Str( 
            infolog.copy(infoLogCounter+1,infolog.num())); 
        infoLogCounter = infolog.num(); 
        errorFound = true; 
    } 
    intrastat.update(); 
    return ok; 
}
```

## Method createDevelopmentWorkspaceWindow

```xpp
public int createDevelopmentWorkspaceWindow()
```

### Return Value - createDevelopmentWorkspaceWindow

## Method createWorkspaceWindow

Opens a new workspace window. For example, this enables you to open different sets of application objects in different windows, or to work with two different sets of company accounts.

```xpp
public int createWorkspaceWindow()
```

### Return Value - createWorkspaceWindow

Returns a handle to the new window.

## Method currentAOLayer

Retrieves the current layer you are running in such as SYS, or USR.

```xpp
public UtilEntryLevel currentAOLayer()
```

### Return Value - currentAOLayer

A UtilEntryLevel system enumeration value that indicates the current layer you are working in.

### Remarks - currentAOLayer

For more information, see Layers.

## Method cut

Cuts lines from the Infolog buffer.

```xpp
public container cut(int from, int to)
```

### Parameters - cut

from  
The last line to cut.

<!-- -->

to  
The last line to cut.

### Return Value - cut

A container that contains the Infolog lines between the lines specified by the from and to parameters.

### Examples - cut

The following example cuts the lines in the Infolog from the line specified by the fromLine value, up to the last line.

```xpp
private void cutInfolog(int fromLine) 
{ 
    infolog.cut(fromLine+1, Global::infologLine()); 
}
```

## Method documentationLanguage

Gets or sets the language that is used for the documentation.

```xpp
public str documentationLanguage([str languageCode])
```

### Parameters - documentationLanguage

languageCode  
The ID of the language you want to set; optional.

### Return Value - documentationLanguage

The ID of the language that is currently used for the documentation.

### Remarks - documentationLanguage

Use the xInfo.language Method to set the language for the GUI. To set the documentation language for a particular session, use the xSession.documentationLanguage Method. An example value for the languageCode parameter is "en-us", which will set the language to US English.

## Method export

```xpp
public container export()
```

### Return Value - export

## Method findNode

Retrieves the specified a tree node.

```xpp
public TreeNode findNode(str nodePath)
```

### Parameters - findNode

nodePath  
A string that contains the path to the node.

### Return Value - findNode

Returns the tree node that is specified by the nodePath parameter.

### Remarks - findNode

This method is obsolete. Use the TreeNode::findNode Method instead.

## Method getDocNode

Retrieves the specified documentation nodes from the AOT.

```xpp
public TreeNode getDocNode(UtilFileType helpType, int UtilType, str Name, [UtilElementId ParentId], [int Type], [UtilEntryLevel UtilLevel], [boolean ForceLevel], [int Mode], [boolean OldUtil])
```

### Parameters - getDocNode

helpType  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

UtilType  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Name  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

ParentId  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Type  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

UtilLevel  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

ForceLevel  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Mode  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

OldUtil  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

### Return Value - getDocNode

A documentation node from the AOT.

### Remarks - getDocNode

The possible values for the helpType parameter are values of the UtilFileType system enumeration:

-   KernelHelp: the System Documentation node
-   ApplicationHelp: the Application Documentation node
-   ApplicationCodeDocumentation: the Application Developer Documentation node.

An example value of the utilType parameter is the Functions node within the System Documentation node. The default value of the ForceLevel parameter is false. If it is set to false, and there is no content in the layer specified, the node will be taken from the next layer below this that does have content. If it is set to true, and there is no content in the layer, the method will return nullNothingnullptrunita null reference (Nothing in Visual Basic).

## Method getImportedNode

Creates an instance of a tree node from an XPO file but does not import it into the AOT. For example, this allows you to compare it with another version of the same tree node.

```xpp
public TreeNode getImportedNode(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)
```

### Parameters - getImportedNode

id  

<!-- -->

utilfiletype  

<!-- -->

utiltype  

<!-- -->

name  

<!-- -->

fileposition  

<!-- -->

Flag  

### Return Value - getImportedNode

A tree node.

### Remarks - getImportedNode

The possible values for the utilfiletype parameter are those that are available in the UtilFileType Enumeration. The possible values for the utiltype parameter are those that are available in the UtilElementType Enumeration. For a list of the possible values for the Flag parameter, see the AOTExport macro. The values are listed under the System import flags comment.

### Examples - getImportedNode

The following example uses the getImportedNode method to create a virtual tree node.

```xpp
public TreeNode getVirtualTreenode( 
    Filename _filename = this.fileName()) 
{ 
    #AOT 
    #AotExport 
    TmpAotImport      tmpImportAot; 
    SysImportElements sysImportElements = new SysImportElements(); 
    TreeNode treeNodeImport  = null; 
    int      exportId; 
    int      flag = (#impGetCompareNode + #impKeepIds); 
    str      name; 
    ; 
    // Set the filename. 
    sysImportElements.newFile(_filename); 
    // Get info from the file 
    tmpImportAot = sysImportElements.getTmpImportAot(); 
    // Create an import context 
    exportId     = infolog.startImport(_filename, flag); 
    // Get the right name 
    // for doc nodes it is the path excl. the first part 
    switch (tmpImportAot.UtilFileType) 
    { 
        case UtilFileType::Application: 
            name = tmpImportAot.TreeNodeName; 
            break; 
        case UtilFileType::ApplicationCodeDocumentation: 
            name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#ApplicationDeveloperDocPath)); 
            break; 
        case UtilFileType::ApplicationHelp: 
            name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#ApplicationDocPath)); 
            break; 
        case UtilFileType::KernelHelp: 
            name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#SystemDocPath)); 
            break; 
        default: 
            name = tmpImportAot.TreeNodeName; 
            break; 
    } 
    // Import the node in memory 
    treeNodeImport  = infolog.getImportedNode( 
        exportId, 
        tmpImportAot.UtilFileType, 
        tmpImportAot.UtilElementType, 
        name, 
        tmpImportAot.FilePos, 
        flag); 
    // Close the import context 
    infolog.endImport(exportId, 1); 
    return treeNodeImport; 
}
```

## Method getNode

Retrieves a tree node that corresponds to a node in the AOT.

```xpp
public TreeNode getNode(UtilElementType UtilType, str Name, [UtilElementId ParentId], [int Type], [UtilEntryLevel Utillevel], [boolean Forcelevel], [int Mode], [boolean OldUtil])
```

### Parameters - getNode

UtilType  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Name  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

ParentId  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Type  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Utillevel  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Forcelevel  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Mode  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

OldUtil  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

### Return Value - getNode

The tree node that is specified by the UtilType and Name parameters.

### Remarks - getNode

The node returned is not linked into the AOT, so you cannot perform operations on the node. To perform operations on a node, use the findNode or rootNode method instead. The default value for the UtilLevel parameter is the current layer. The possible values for the Mode parameter are:

-   0x001: Load for run
-   0x002: Load for edit

The default value of the ForceLevel parameter is false. If it is set to false, and there is no content in the layer specified, the node will be taken from the next layer below this that does have content. If it is set to true, and there is no content in the layer, the method will return nullNothingnullptrunita null reference (Nothing in Visual Basic).

## Method getNodeResid

Retrieves the resource ID for the icon that is used to display nodes of the specified type.

```xpp
public int getNodeResid(UtilElementType nodeType)
```

### Parameters - getNodeResid

nodeType  
A UtilElementType system enumeration value that indicates the type of node to retrieve.

### Return Value - getNodeResid

An integer that represents the Resource ID for the node.

## Method getTaskInfo

```xpp
public Struct getTaskInfo(int taskNumber)
```

### Parameters - getTaskInfo

taskNumber  

### Return Value - getTaskInfo

## Method getUserSetup

Retrieves a UserSetup object that is used to set user parameters.

```xpp
public UserSetup getUserSetup()
```

### Return Value - getUserSetup

A UserSetup object.

### Remarks - getUserSetup

The UserSetup system class provides an interface for setting user parameters.

## Method getWorkspaceList

```xpp
public container getWorkspaceList()
```

### Return Value - getWorkspaceList

## Method hWnd

Retrieves a handle to the Navigation Pane window.

```xpp
public int hWnd([int workspaceNum])
```

### Parameters - hWnd

workspaceNum  
The handle to the workspace from which to get the Navigation Pane handle.

### Return Value - hWnd

An integer that represents the handle to the Navigation Pane window.

## Method import

```xpp
public boolean import(container infologContainer, [boolean clearExistingInfolog])
```

### Parameters - import

infologContainer  

<!-- -->

clearExistingInfolog  

### Return Value - import

## Method importElement

Specifies the object to be imported.

```xpp
public int importElement(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)
```

### Parameters - importElement

id  

<!-- -->

utilfiletype  

<!-- -->

utiltype  

<!-- -->

name  

<!-- -->

fileposition  

<!-- -->

Flag  

### Return Value - importElement

This method is obsolete. Use the SysImportElements class instead.

## Method importString

Imports an object from a file.

```xpp
public int importString(str source, UtilElementType kind, str name)
```

### Parameters - importString

source  
The name of the object.

<!-- -->

kind  
The name of the object.

<!-- -->

name  
The name of the object.

### Return Value - importString

## Method instance

Retrieves a handle to the current instance of the application.

```xpp
public int instance()
```

### Return Value - instance

The handle of the current instance of the application.

## Method isoCurrencyCode

Gets or sets the currency code.

```xpp
public str isoCurrencyCode([str code])
```

### Parameters - isoCurrencyCode

code  
A string that contains the ISO currency code to set.

### Return Value - isoCurrencyCode

A string that contains the currency code for the current application.

## Method IsVisible

Determines whether the client window is not minimized.

```xpp
public boolean IsVisible()
```

### Return Value - IsVisible

false if the client window is minimized; otherwise, true.

## Method language

Gets or sets the language for the GUI.

```xpp
public str language([str languageCode])
```

### Parameters - language

languageCode  
A string that contains the language code to set.

### Return Value - language

A string that contains the current language code.

### Remarks - language

To set the language for the documentation, use the xInfo.documentationLanguage Method. To set the GUI language for a particular session, use the xSession.interfaceLanguage Method.

### Examples - language

The following example prints the code for the language that is currently set. For example, if the interface was in US English, it would print "en-us".

```xpp
{ 
    print infolog.language(); 
    pause; 
}
```

## Method level

Retrieves the exception level of a line in the Infolog buffer.

```xpp
public Exception level(int line)
```

### Parameters - level

line  
The line in the Infolog for which to retrieve the exception level.

### Return Value - level

A Exception system enumeration value.

### Remarks - level

For more information, see Exception Handling with try and catch Keywords.

## Method line

Retrieves the number of lines in the Infolog buffer.

```xpp
public int line()
```

### Return Value - line

An integer that represents the number of lines in the Infolog buffer.

### Remarks - line

If you are running code on the server, use the xGlobal::infologLine method instead. It eliminates calls between the server and client. To get the number of exceptions of a specific type in the Infolog, use the xInfo.num Method.

## Method messageWin

Enables you to send output from the Infolog to the Message window.

```xpp
public MessageWin messageWin()
```

### Return Value - messageWin

A MessageWin object.

### Remarks - messageWin

You may want to send output to the Message window if you have a lengthy process. If you send output to the Infolog, nothing will be displayed until the process is completed. If you send output to the Message window, content is displayed as the operation proceeds.

## Method nationalCurrencyFactor

```xpp
public Real nationalCurrencyFactor([Real factor])
```

### Parameters - nationalCurrencyFactor

factor  

### Return Value - nationalCurrencyFactor

## Method nationalCurrencyPostfix

```xpp
public str nationalCurrencyPostfix([str string])
```

### Parameters - nationalCurrencyPostfix

string  

### Return Value - nationalCurrencyPostfix

## Method nationalCurrencyPrefix

```xpp
public str nationalCurrencyPrefix([str string])
```

### Parameters - nationalCurrencyPrefix

string  

### Return Value - nationalCurrencyPrefix

## Method navPane

Retrieves an xNavPane object, the primary navigation control class.

```xpp
public xNavPane navPane()
```

### Return Value - navPane

An instance of the xNavPane class.

### Remarks - navPane

You can only have one instance of this class per workspace.

## Method num

Retrieves the number of exceptions of the specified type in the Infolog buffer.

```xpp
public int num([Exception exceptionType])
```

### Parameters - num

exceptionType  
A Exception system enumeration value that indicates the exception type to count; optional.

### Return Value - num

An integer that represents the number of exceptions of the type specified by the exceptionType parameter, or the total number of lines in the Infolog if no parameter is specified.

### Remarks - num

For more information, see Exception Handling with try and catch Keywords.

### Examples - num

The following example returns the number of warnings in the Infolog.

```xpp
{ 
    print infolog.num(Exception::Warning); 
    pause; 
}
```

## Method prevInstance

Retrieves a handle to the previous instance of the application.

```xpp
public int prevInstance()
```

### Return Value - prevInstance

The handle of the previous instance of the application.

### Remarks - prevInstance

This method should not be used.

## Method processId

Retrieves the ID for the process.

```xpp
public int processId()
```

### Return Value - processId

The ID for the process.

## Method projectRootNode

Returns the X++ Projects node.

```xpp
public TreeNode projectRootNode()
```

### Return Value - projectRootNode

The tree node that contains the X++ projects.

### Examples - projectRootNode

The following example prints out the names of all the projects in the Shared projects folder.

```xpp
void ProjectNames() 
{ 
    Treenode treenode; 
    TreenodeIterator it; 
    treenode = infolog.projectRootNode(); 
    treenode = treenode.AOTfindChild("Shared"); 
    it = treenode.AOTiterator(); 
    while (treenode) 
    { 
       print treenode.treeNodeName(); 
       treenode = it.next(); 
    } 
    pause; 
}
```

## Method rootNode

Retrieves the root of the application object tree.

```xpp
public TreeNode rootNode()
```

### Return Value - rootNode

The root of the application object tree.

### Examples - rootNode

The following example prints out all the names of the methods in the AddressSelectForm class. The rootnode method is used to set the treenode object to the AOT root before selecting a child node.

```xpp
{ 
    Treenode treenode; 
    TreenodeIterator it; 
    treenode = infolog.rootNode(); 
    treenode = treenode.AOTfindChild("Classes"); 
    treenode = treenode.AOTfindChild("AddressSelectForm"); 
    it = treenode.AOTiterator(); 
    while (treenode) 
    { 
       print treenode.treeNodeName(); 
       treenode = it.next(); 
    } 
    pause; 
}
```

## Method startImport

Creates an import context.

```xpp
public int startImport(str file, int flag, [str labelSubstitutes])
```

### Parameters - startImport

file  

<!-- -->

flag  

<!-- -->

labelSubstitutes  

### Return Value - startImport

### Remarks - startImport

This method is obsolete. Use the SysImportElements class instead.

## Method text

Retrieves a line of text from the Infolog.

```xpp
public str text([int line])
```

### Parameters - text

line  
The line in the Infolog with the text to retrieve.

### Return Value - text

A string that contains the text from the Infolog.

## Method userNode

```xpp
public TreeNode userNode()
```

### Return Value - userNode

## Method webSession

```xpp
public AnyType webSession([AnyType value])
```

### Parameters - webSession

value  

### Return Value - webSession

## Method activeXControls

Retrieves a list of the ActiveX controls.

```xpp
public static container activeXControls()
```

### Return Value - activeXControls

A nested container that holds information about each of the ActiveX controls.

### Remarks - activeXControls

The returned container contains four containers. The first inner container contains the names of all the controls. The second inner container contains the ID for each control, which is a GUID. The third inner container contains the security setting for each control. The fourth inner container contains a description of each control.

### Examples - activeXControls

The following example prints a description of each of the ActiveX controls.

```xpp
static void activeXcontents(Args _args) 
{ 
    int       i; 
    str       strClsName, strTypeLibHelp, strClsId, strSafeForBits; 
    container c; 
    container clsName, clsId, safeForBits, typeLibHelp; 
    c = xinfo::activeXControls(); 
    clsName = conpeek(c, 1); 
    clsId = conpeek(c, 2); 
    safeForBits = conpeek(c, 3); 
    typeLibHelp = conpeek(c, 4); 
    for (i=1; i<conlen(clsName); i++) 
    { 
        strClsName = conpeek(clsName, i); 
        strClsId = conpeek(clsId, i); 
        strSafeForBits = conpeek(safeForBits, i); 
        strTypeLibHelp = conpeek(typeLibHelp, i); 
        print strClsName, " ", strClsId, " ", strSafeForBits, 
            " ", strTypeLibHelp; 
    } 
    pause; 
}
```

## Method AOTLogDirectory

Gets the path to the log directory for the current installation.

```xpp
public static str AOTLogDirectory()
```

### Return Value - AOTLogDirectory

A string that contains the path to the log directory for the current installation.

### Remarks - AOTLogDirectory

If you turn on the AOT Log option, information will be stored in the log directory each time you compile. To turn on this option:

1.  Open a developer workspace.
2.  Select Tools &gt; Options &gt; Development &gt; Compiler.
3.  Select the AOT log check box.

## Method automationObjects

Retrieves the list of COM objects that are available.

```xpp
public static container automationObjects()
```

### Return Value - automationObjects

A nested container that holds a description of each COM object.

### Examples - automationObjects

The following example unpacks the nested container that is returned from automationObjects to get a list of COM objects.

```xpp
void getAutomationObjects() 
{ 
    int idx; 
    FormListItem listItem; 
    int itemPos; 
    container clsGUID,clsDesc,clsVersion,clsPath; 
    [clsGUID,clsDesc,clsVersion,clsPath] = xInfo::automationObjects(); 
    for (idx = 1; idx < conlen(clsGUID); idx++) 
    { 
        itemPos = formListControl.add(conpeek(clsDesc,idx)); 
        listItem = formListControl.getItem(itemPos); 
        listItem.data(conpeek(clsPath,idx)); 
        formListControl.setItem(listItem); 
    } 
}
```

## Method buildNo

Retrieves the kernel build number of the current executable.

```xpp
public static str buildNo()
```

### Return Value - buildNo

A string that contains the kernel build number.

### Examples - buildNo

The following example uses this method to return the kernel build number as part of a string that contains version information.

```xpp
static client str axaptaReleaseID() 
{ 
    #define.versionPrefix('v') 
    #define.versionNumber('#') 
    #define.versionPartition('/') 
    return    #versionprefix+xInfo::releaseVersion()+ 
              #versionNumber+xInfo::buildNo()+ 
              #versionPartition+ApplicationVersion::buildNo(); 
}
```

## Method compilationDate

Retrieves the date on which the current version was last compiled.

```xpp
public static str compilationDate()
```

### Return Value - compilationDate

A string that contains the date on which the current version was last compiled.

### Examples - compilationDate

The following example returns system information, including the date on which the application was last compiled:

```xpp
str environment() 
{ 
    return xInfo::buildNo() + ' - '  
        + xInfo::compilationDate() + ' - '  
        + xInfo::dbName() + ' - '  
        + xInfo::osName() + ' - '  
        + xInfo::productName() + ' - '  
        + xInfo::releaseVersion(); 
}
```

## Method compilationTime

Retrieves the time at which the current version was last compiled.

```xpp
public static str compilationTime()
```

### Return Value - compilationTime

A string that contains the time at which the current version was last compiled.

## Method componentName

Retrieves the path to the component.

```xpp
public static str componentName()
```

### Return Value - componentName

A string that contains the path to the executable.

### Remarks - componentName

If this method is run on the client, it returns the path to the .exe file for the client. If it is run on the server, it returns the path to the .exe file for the AOS.

## Method configuration

Retrieves the current client configuration.

```xpp
public static str configuration()
```

### Return Value - configuration

A string that represents the current client configuration.

### Remarks - configuration

This is the configuration that is selected in the Configuration box in the Client Configuration Utility program. An example string that could be returned is "Original (installed configuration)".

## Method currentWorkspaceNum

Retrieves the application window ID of the current workspace.

```xpp
public static int currentWorkspaceNum()
```

### Return Value - currentWorkspaceNum

The application window ID of the current workspace.

### Remarks - currentWorkspaceNum

The createWorkspaceWindow method allows you to open additional workspaces in the application.

## Method directory

Retrieves the path to the directory where the client has been installed.

```xpp
public static str directory(DirectoryType type)
```

### Parameters - directory

type  
A DirectoryType enumeration value that indicates one of the subfolders of the client installation.

### Return Value - directory

A string that contains the path to the directory that is specified by the DirectoryType parameter.

### Examples - directory

The following example prints the path to the Bin directory for the current client installation.

```xpp
{ 
    print xInfo::directory(DirectoryType::Bin); 
    pause; 
}
```

## Method expireDate

Retrieves the date on which the license for the current installation expires.

```xpp
public static Date expireDate()
```

### Return Value - expireDate

A date that represents the date on which the license expires.

## Method getApplicationObjectTreeWindow

```xpp
public static ApplicationObjectTreeWindow getApplicationObjectTreeWindow()
```

### Return Value - getApplicationObjectTreeWindow

## Method getCurrentModelId

```xpp
public static int getCurrentModelId()
```

### Return Value - getCurrentModelId

## Method getNumberOfDecimals

Retrieves the number of decimal places in the specified number.

```xpp
public static int getNumberOfDecimals(Real number)
```

### Parameters - getNumberOfDecimals

number  
A real number.

### Return Value - getNumberOfDecimals

The number of decimal places in the number parameter.

## Method getPropertiesWindow

```xpp
public static PropertiesWindow getPropertiesWindow()
```

### Return Value - getPropertiesWindow

## Method getSystemGeneratedModelId

```xpp
public static int getSystemGeneratedModelId(UtilEntryLevel layer)
```

### Parameters - getSystemGeneratedModelId

layer  

### Return Value - getSystemGeneratedModelId

## Method licenseName

Retrieves the name of the current license.

```xpp
public static str licenseName()
```

### Return Value - licenseName

A string that contains the name of the license.

### Remarks - licenseName

The xInfo::expireDate Method returns the date on which the license expires. The xInfo::serialNo Method returns the serial number of the license.

## Method productName

Retrieves the name of the product.

```xpp
public static str productName()
```

### Return Value - productName

A string that contains the name of the product.

### Examples - productName

The following example returns system information, including the name of the product.

```xpp
str environment() 
{ 
    return xInfo::buildNo() + ' - '  
        + xInfo::compilationDate() + ' - '  
        + xInfo::dbName() + ' - '  
        + xInfo::osName() + ' - '  
        + xInfo::productName() + ' - '  
        + xInfo::releaseVersion(); 
}
```

## Method productRegisteredName

```xpp
public static str productRegisteredName()
```

### Return Value - productRegisteredName

## Method releaseVersion

Retrieves the version number of the current executable; for example: 3.0, or 4.0.

```xpp
public static str releaseVersion()
```

### Return Value - releaseVersion

A string containing the version number.

### Remarks - releaseVersion

Possible version numbers include 3.0 and 4.0.

### Examples - releaseVersion

The following example uses this return the version number as part of a string that contains version information.

```xpp
static client str axaptaReleaseID() 
{ 
    #define.versionPrefix('v') 
    #define.versionNumber('#') 
    #define.versionPartition('/') 
    return    #versionprefix+xInfo::releaseVersion()+ 
              #versionNumber+xInfo::buildNo()+ 
              #versionPartition+ApplicationVersion::buildNo(); 
}
```

## Method releaseYear

```xpp
public static str releaseYear()
```

### Return Value - releaseYear

## Method serialNo

Retrieves the serial number of the current license.

```xpp
public static str serialNo()
```

### Return Value - serialNo

A string that contains the serial number of the license.

## Method new

Initializes a new xInfo object.

```xpp
public void new()
```

### Remarks - new

Note: Do not use this method. You should use the global instance of the xInfo class, infolog, instead. For more information, see the xInfo class.

## Method workspaceWindowDestroyed

Executes when a workspace is closed.

```xpp
public void workspaceWindowDestroyed(int hWnd)
```

### Parameters - workspaceWindowDestroyed

hWnd  
The handle of the workspace.

### Remarks - workspaceWindowDestroyed

This method is called when a new workspace is closed. It allows you to perform an action when this occurs.

## Method writeCustomStatlineItem

Writes a line of text to the status bar.

```xpp
public void writeCustomStatlineItem(str text)
```

### Parameters - writeCustomStatlineItem

text  
The line of text to put on the status bar.

## Method reloadRunningMode

```xpp
public void reloadRunningMode()
```

## Method setWindowOrder

Sets the order in which windows should be displayed.

```xpp
public void setWindowOrder(int window, [int afterWindow])
```

### Parameters - setWindowOrder

window  
The handle to the window to place after the window specified by the window parameter; optional.

<!-- -->

afterWindow  
The handle to the window to place after the window specified by the window parameter; optional.

### Examples - setWindowOrder

The following example sets focus on a window and brings it to the front.

```xpp
void setFocus() 
{ 
    infolog.activateWindow(element.hWnd()); 
    infolog.setWindowOrder(element.hWnd()); 
}
```

## Method shutDown

Shuts down the client.

```xpp
public void shutDown(boolean force)
```

### Parameters - shutDown

force  
A Boolean value that indicates whether the user is given the option to prevent the shutdown.

## Method xref

Executes when the cross-reference system is used.

```xpp
public void xref(str path, xRef x)
```

### Parameters - xref

path  

<!-- -->

x  

### Remarks - xref

Do not use this method.

## Method updateCurrentCompany

```xpp
public void updateCurrentCompany()
```

## Method redrawAllWindows

Redraws all windows.

```xpp
public void redrawAllWindows()
```

### Remarks - redrawAllWindows

This method can be used to update the display during a long process.

## Method formNotify

Executes based on a particular type of change to a specific form, allowing custom code to run.

```xpp
public void formNotify(xFormRun form, FormNotify notification, [FormNotifyEventArgs formNotifyEventArgs])
```

### Parameters - formNotify

form  

<!-- -->

notification  

<!-- -->

formNotifyEventArgs  

### Remarks - formNotify

Possible values for the notification parameter are:

-   Activate
-   DeActivate
-   Open
-   Close
-   RecordChange
-   NoteClicked

For an example of the usage of this method, see the formNotify method of the Info class, where this method has been overridden.

## Method mayReloadMenu

Prevents the UI from refreshing.

```xpp
public void mayReloadMenu(boolean value)
```

### Parameters - mayReloadMenu

value  
A Boolean value that indicates whether to prevent the UI from refreshing.

### Remarks - mayReloadMenu

Set the value to false to prevent the UI from refreshing when a process is executing, and then set it to true after the process has finished. The mayReloadMenu method can be useful to prevent the UI from flickering, for example when many nodes in the AOT are being read.

## Method startLengthyOperation

Sets the mouse cursor to idle.

```xpp
public void startLengthyOperation()
```

### Remarks - startLengthyOperation

Use at the start of a lengthy operation to indicate that a process is in progress. When the operation has finished, the system automatically calls the endLengthyOperation method.

## Method breakpointNotify

Implements a notification system when a breakpoint is changed.

```xpp
public void breakpointNotify(BreakpointNotify notification)
```

### Parameters - breakpointNotify

notification  
A BreakpointNotify system enumeration value that specifies the type of change that has occurred to the breakpoints.

### Remarks - breakpointNotify

In the application, this method is used to update the Breakpoints form when a change is made to a breakpoint in the Code Editor window. The following values of the BreakpointNotify enumeration type are valid for the notification parameter:

-   BreakpointForm: Notifies the client that the breakpoint list should be reloaded.
-   BreakpointChange: Notifies the client and server that the status of a breakpoint has changed (enabled, disabled, or deleted).

## Method initializeInfolog

```xpp
public void initializeInfolog(int window)
```

### Parameters - initializeInfolog

window  

## Method startup

Executes when the client starts.

```xpp
public void startup(str startupCmd)
```

### Parameters - startup

startupCmd  

### Remarks - startup

Do not use this method. Use one following methods instead. Use the Info.startupPost Method to pass startup commands to the client. Use the Application.startupPost Method to pass startup commands to the server. Do not use the Application.startup or Info.startup methods. This might affect code in a new version, which could prevent the client or server from starting.

## Method endImport

Completes an import process.

```xpp
public void endImport(int id, int elements)
```

### Parameters - endImport

id  

<!-- -->

elements  

### Remarks - endImport

This method is obsolete. Use the SysImportElements class instead.

## Method yield

```xpp
public void yield()
```

## Method viewAlertInbox

Launches the View alerts form.

```xpp
public void viewAlertInbox([int selectedTab])
```

### Parameters - viewAlertInbox

selectedTab  
Determines which tab the View alerts form opens on; optional.

### Remarks - viewAlertInbox

The default value for the selectedTab parameter is Overview, the first tab. Call the xInfo.canViewAlertInbox Method to check whether the user has permission to view this form.

## Method reportSendMailServer

```xpp
public void reportSendMailServer(PrintJobSettings settings)
```

### Parameters - reportSendMailServer

settings  

## Method endLengthyOperation

Sets the mouse cursor back to normal after a call to startLengthyOperation.

```xpp
public void endLengthyOperation([boolean endAll])
```

### Parameters - endLengthyOperation

endAll  
Reserved.

### Remarks - endLengthyOperation

It is best practice not to call this method. It will be called automatically by the system when the operation has ended. If you call this method explicitly and there are other processes, or looping code, that use the method, it could lead to the mouse pointer flickering.

## Method setNumUnreadAlerts

Refreshes the status bar text when the number of unread Alert e-mails changes.

```xpp
public void setNumUnreadAlerts([int n])
```

### Parameters - setNumUnreadAlerts

n  
Allows you to set the number of unread e-mails to a specific number.

## Method truncate

Removes the items with the specified prefix from the Infolog.

```xpp
public void truncate(str prefix)
```

### Parameters - truncate

prefix  
The prefix for the items that you want to remove from the Infolog.

## Method formNoteButton

Controls the Document handling button on the toolbar.

```xpp
public void formNoteButton(boolean enable, boolean value)
```

### Parameters - formNoteButton

enable  
A Boolean data type that indicates the appearance of the icon.

<!-- -->

value  
A Boolean data type that indicates the appearance of the icon.

### Examples - formNoteButton

The following example shows how to disable the Document handling button.

```xpp
void disableNoteButton() 
    { 
        infolog.formNoteButton(false, false); 
    }
```

## Method viewCreateRuleDialog

Launches the Create alert rule form.

```xpp
public void viewCreateRuleDialog(xFormRun caller)
```

### Parameters - viewCreateRuleDialog

caller  
The current form.

### Remarks - viewCreateRuleDialog

The Create alert rule form will be launched from the current form, as specified by the caller parameter.

## Method view

```xpp
public void view([container container])
```

### Parameters - view

container  

## Method clear

Deletes lines from the Infolog buffer.

```xpp
public void clear([int linesLeft])
```

### Parameters - clear

linesLeft  
Number of lines to leave in the buffer; optional.

### Remarks - clear

Do not call this with method with the default value of zero unless another process has not put information into the Infolog.

### Examples - clear

Use this pattern to clear the Infolog cache:

```xpp
int line = Global::infologLine();
try 
{ 
    // 
} 
catch 
{ 
    infolog.clear(line); 
}
```

## Method workspaceWindowCreated

Executes when a new workspace is created.

```xpp
public void workspaceWindowCreated(int hWnd)
```

### Parameters - workspaceWindowCreated

hWnd  
The handle of the new workspace.

### Remarks - workspaceWindowCreated

This method is called when a new workspace is created. It allows you to perform an action when this occurs.

## Method setCurrentModelId

```xpp
public static void setCurrentModelId(int currentModelId)
```

### Parameters - setCurrentModelId

currentModelId  

## Method activateMenubarTask

```xpp
public void activateMenubarTask(int command)
```

### Parameters - activateMenubarTask

command  

## Method finalize

```xpp
public void finalize()
```

## Method insertXReferences

```xpp
public void insertXReferences()
```

## Method activateButton

```xpp
public void activateButton(int command)
```

### Parameters - activateButton

command  

## Method activateWindow

Sets the focus on a form or Window.

```xpp
public void activateWindow(int window)
```

### Parameters - activateWindow

window  
The handle to the form or window that you want to bring into focus.

## Method reportSendMail

Generates the settings for sending a report by email.

```xpp
public void reportSendMail(PrintJobSettings settings)
```

### Parameters - reportSendMail

settings  
The email settings for the user.

