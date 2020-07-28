---
title: xFormRun class
description: This topic describes the xFormRun class.
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

# Class xFormRun

[!include [banner](../../includes/banner.md)]

```xpp
class xFormRun extends ObjectRun
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                                                                                                                                                                         | Description |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean allowPrimaryKeyPreview(\[boolean display\])                                                                                                                                                                                                                                                                                                     |             |
| public boolean canClose()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean canSubmitToWorkflow()                                                                                                                                                                                                                                                                                                                           |             |
| public boolean checkViewOption(int viewOption)                                                                                                                                                                                                                                                                                                                 |             |
| public boolean closed()                                                                                                                                                                                                                                                                                                                                        |             |
| public boolean closedCancel()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean closedOk()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean contains(FormControl control)                                                                                                                                                                                                                                                                                                                   |             |
| public FormControl control(int controlId)                                                                                                                                                                                                                                                                                                                      |             |
| public FormControl controlCallingMethod()                                                                                                                                                                                                                                                                                                                      |             |
| public int controlId(str controlName)                                                                                                                                                                                                                                                                                                                          |             |
| public boolean controlMethodOverload(\[boolean value\])                                                                                                                                                                                                                                                                                                        |             |
| public Object controlMethodOverloadObject(\[Object value\])                                                                                                                                                                                                                                                                                                    |             |
| public boolean copy()                                                                                                                                                                                                                                                                                                                                          |             |
| public boolean cut()                                                                                                                                                                                                                                                                                                                                           |             |
| public FormObjectSet dataSource(\[AnyType objectSet\])                                                                                                                                                                                                                                                                                                         |             |
| public int dataSourceCount()                                                                                                                                                                                                                                                                                                                                   |             |
| public FormObjectSet defaultDataSource(\[FormObjectSet value\])                                                                                                                                                                                                                                                                                                |             |
| public boolean defaultInitialQueryValuesOnCreate(\[boolean value\])                                                                                                                                                                                                                                                                                            |             |
| public FormDesign design(\[int reserved\])                                                                                                                                                                                                                                                                                                                     |             |
| public Common docCursor()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean enableCountryRegion(\[boolean flag\])                                                                                                                                                                                                                                                                                                           |             |
| public Form form()                                                                                                                                                                                                                                                                                                                                             |             |
| public Common getActiveWorkflowConfiguration()                                                                                                                                                                                                                                                                                                                 |             |
| public Common getActiveWorkflowTrackingStatus()                                                                                                                                                                                                                                                                                                                |             |
| public Common getActiveWorkflowWorkItem()                                                                                                                                                                                                                                                                                                                      |             |
| public container getAutoCompleteString(int startIdx, \[FormControl control\], \[str searchString\])                                                                                                                                                                                                                                                            |             |
| public str getFormHelpTopic()                                                                                                                                                                                                                                                                                                                                  |             |
| public FormControl getNextField(FormControl control, \[int flags\])                                                                                                                                                                                                                                                                                            |             |
| public FormControl getPrevField(FormControl control, \[int flags\])                                                                                                                                                                                                                                                                                            |             |
| public boolean hasExecutedInit()                                                                                                                                                                                                                                                                                                                               |             |
| public int hWnd()                                                                                                                                                                                                                                                                                                                                              |             |
| public int installMessageProc(int message, int handle, str method)                                                                                                                                                                                                                                                                                             |             |
| public boolean inViewMode()                                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isDataInteractionSupported()                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isPreloadedInstance()                                                                                                                                                                                                                                                                                                                           |             |
| public boolean isFormPart()                                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isFactBox()                                                                                                                                                                                                                                                                                                                                     |             |
| public boolean isLookupForm()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean isPartRemote()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean isPartLocal()                                                                                                                                                                                                                                                                                                                                   |             |
| public boolean isWorkflowEnabled()                                                                                                                                                                                                                                                                                                                             |             |
| public Common loadWorkflowConfiguration()                                                                                                                                                                                                                                                                                                                      |             |
| public boolean lockWindowUpdate(boolean lock)                                                                                                                                                                                                                                                                                                                  |             |
| public str name()                                                                                                                                                                                                                                                                                                                                              |             |
| public FormObjectSet objectSet(\[AnyType objectSet\])                                                                                                                                                                                                                                                                                                          |             |
| public boolean resetAsyncOperationsPendingState()                                                                                                                                                                                                                                                                                                              |             |
| public PageInteraction pageInteraction()                                                                                                                                                                                                                                                                                                                       |             |
| public boolean paste()                                                                                                                                                                                                                                                                                                                                         |             |
| public str recordingScopeId()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean removeMessageProc(int message, int handle)                                                                                                                                                                                                                                                                                                      |             |
| public List rootFormDataSources()                                                                                                                                                                                                                                                                                                                              |             |
| public boolean selectControl(FormControl control)                                                                                                                                                                                                                                                                                                              |             |
| public FormControl selectedControl()                                                                                                                                                                                                                                                                                                                           |             |
| public Common selectRecordModeSelectedRecord(\[Common selectedRecord\])                                                                                                                                                                                                                                                                                        |             |
| public FormControl selectTarget(\[FormControl target\])                                                                                                                                                                                                                                                                                                        |             |
| public Array tabOrder(\[Array newValue\])                                                                                                                                                                                                                                                                                                                      |             |
| public int task(int taskId)                                                                                                                                                                                                                                                                                                                                    |             |
| public str toString()                                                                                                                                                                                                                                                                                                                                          |             |
| public FormObjectSet workflowDataSource()                                                                                                                                                                                                                                                                                                                      |             |
| public str workflowType()                                                                                                                                                                                                                                                                                                                                      |             |
| public System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, \[System.Threading.CancellationToken cancellationToken\], \[str callbackFormMethodName\], \[container asyncState\], \[str userId\], \[str company\], \[str language\], \[str partitionKey\], \[System.Threading.Tasks.TaskCreationOptions options\]) |             |
| public System.Threading.Tasks.Task setTimeoutEx(\[str formMethodName\], \[container parms\], \[int delay\], \[System.Threading.CancellationToken cancellationToken\])                                                                                                                                                                                          |             |
| public void setParentHandle(int hwnd)                                                                                                                                                                                                                                                                                                                          |             |
| public void setFormHelpTopic(str formHelpTopic)                                                                                                                                                                                                                                                                                                                |             |
| public void setFactBoxEditable()                                                                                                                                                                                                                                                                                                                               |             |
| public void setAutoCompleteString(str string, AnyType control)                                                                                                                                                                                                                                                                                                 |             |
| public void RaiseOnClosing(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                                |             |
| public void inlineLoadingKey(FormControl parentControl)                                                                                                                                                                                                                                                                                                        |             |
| public void closeSelect(str selectString)                                                                                                                                                                                                                                                                                                                      |             |
| public void RaiseOnActivated(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                              |             |
| public void prevField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void send()                                                                                                                                                                                                                                                                                                                                             |             |
| public void RaiseOnInitializing(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                           |             |
| public void updateWorkflowControls()                                                                                                                                                                                                                                                                                                                           |             |
| public void closeCancel()                                                                                                                                                                                                                                                                                                                                      |             |
| public void lastField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void wait(\[boolean modal\])                                                                                                                                                                                                                                                                                                                            |             |
| public void unLock(\[boolean arrangeNow\])                                                                                                                                                                                                                                                                                                                     |             |
| private void OnInitialized(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                           |             |
| public void detach()                                                                                                                                                                                                                                                                                                                                           |             |
| public void resetStatusBarBackgroundColor()                                                                                                                                                                                                                                                                                                                    |             |
| private void OnClosing(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                               |             |
| public void addDisplayMethod(str name, int displayKind, int displayType, int displayXType, int displayRecord, \[str dataSourceName\], \[boolean isTableDisplayMethod\])                                                                                                                                                                                        |             |
| public void print()                                                                                                                                                                                                                                                                                                                                            |             |
| public void activate(boolean active)                                                                                                                                                                                                                                                                                                                           |             |
| public void resize(int width, int height)                                                                                                                                                                                                                                                                                                                      |             |
| public void reload(\[xArgs args\])                                                                                                                                                                                                                                                                                                                             |             |
| public void finalize()                                                                                                                                                                                                                                                                                                                                         |             |
| public void RaiseOnInitialized(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                            |             |
| public void resetSize()                                                                                                                                                                                                                                                                                                                                        |             |
| public void clientId(str clientId)                                                                                                                                                                                                                                                                                                                             |             |
| public void createRecord(str formDataSourceName, \[boolean append\])                                                                                                                                                                                                                                                                                           |             |
| public void firstField(\[int flags\])                                                                                                                                                                                                                                                                                                                          |             |
| public void savePersonalization(str controlName, str propertyKey, str propertyValue)                                                                                                                                                                                                                                                                           |             |
| public void expandFactBoxPaneAtStart()                                                                                                                                                                                                                                                                                                                         |             |
| public void redraw()                                                                                                                                                                                                                                                                                                                                           |             |
| public void arrange()                                                                                                                                                                                                                                                                                                                                          |             |
| public void blockPersonalization(boolean blockPersonalization)                                                                                                                                                                                                                                                                                                 |             |
| public void nextField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void nextGroup()                                                                                                                                                                                                                                                                                                                                        |             |
| public void prevGroup()                                                                                                                                                                                                                                                                                                                                        |             |
| public void setFormPartStyle(boolean isFactBox)                                                                                                                                                                                                                                                                                                                |             |
| public void run()                                                                                                                                                                                                                                                                                                                                              |             |
| public void setActive()                                                                                                                                                                                                                                                                                                                                        |             |
| public void closeSelectRecord(Common selectedRecord)                                                                                                                                                                                                                                                                                                           |             |
| public void registerFormSpecializedCustomControl(str customControlName)                                                                                                                                                                                                                                                                                        |             |
| public void setApply(Object object, \[Object parm\])                                                                                                                                                                                                                                                                                                           |             |
| public void new(xArgs args)                                                                                                                                                                                                                                                                                                                                    |             |
| public void RegisterXppILImplementation(str className)                                                                                                                                                                                                                                                                                                         |             |
| public void sysColorChanged()                                                                                                                                                                                                                                                                                                                                  |             |
| public void selectRecordMode(\[FormControl control\])                                                                                                                                                                                                                                                                                                          |             |
| private void OnPostRun(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                               |             |
| public void skipSaveUserSetting(boolean skip)                                                                                                                                                                                                                                                                                                                  |             |
| public void selectMode(\[FormControl control\])                                                                                                                                                                                                                                                                                                                |             |
| public void printPreview()                                                                                                                                                                                                                                                                                                                                     |             |
| private void OnActivated(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                             |             |
| public void collapseFactBoxPaneAtStart()                                                                                                                                                                                                                                                                                                                       |             |
| public void lock()                                                                                                                                                                                                                                                                                                                                             |             |
| public void init()                                                                                                                                                                                                                                                                                                                                             |             |
| public void formOnTop()                                                                                                                                                                                                                                                                                                                                        |             |
| public void close()                                                                                                                                                                                                                                                                                                                                            |             |
| public void delAutoCompleteString(\[AnyType control\])                                                                                                                                                                                                                                                                                                         |             |
| public void closeOk()                                                                                                                                                                                                                                                                                                                                          |             |
| public void modeledQueryName(str queryName)                                                                                                                                                                                                                                                                                                                    |             |
| public void initWorkflowControls()                                                                                                                                                                                                                                                                                                                             |             |
| public void setOrder(FormControl control, FormControl control1, \[boolean before\])                                                                                                                                                                                                                                                                            |             |
| public void allowCrossFormLinks(boolean allowCrossFormLinks)                                                                                                                                                                                                                                                                                                   |             |
| public void RaiseOnPostRun(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                                |             |
| public void setStatusBarBackgroundColor(int a, int r, int g, int b)                                                                                                                                                                                                                                                                                            |             |
| public void loadPersonalization()                                                                                                                                                                                                                                                                                                                              |             |
| public void doApply()                                                                                                                                                                                                                                                                                                                                          |             |
| private void OnInitializing(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                          |             |
| public void flushCountryRegionCodeCache()                                                                                                                                                                                                                                                                                                                      |             |
| public void localRefresh()                                                                                                                                                                                                                                                                                                                                     |             |

## Method allowPrimaryKeyPreview

```xpp
public boolean allowPrimaryKeyPreview([boolean display])
```

### Parameters - allowPrimaryKeyPreview

display  

### Return Value - allowPrimaryKeyPreview

## Method canClose

```xpp
public boolean canClose()
```

### Return Value - canClose

## Method canSubmitToWorkflow

```xpp
public boolean canSubmitToWorkflow()
```

### Return Value - canSubmitToWorkflow

## Method checkViewOption

```xpp
public boolean checkViewOption(int viewOption)
```

### Parameters - checkViewOption

viewOption  

### Return Value - checkViewOption

## Method closed

```xpp
public boolean closed()
```

### Return Value - closed

## Method closedCancel

```xpp
public boolean closedCancel()
```

### Return Value - closedCancel

## Method closedOk

```xpp
public boolean closedOk()
```

### Return Value - closedOk

## Method contains

```xpp
public boolean contains(FormControl control)
```

### Parameters - contains

control  

### Return Value - contains

## Method control

```xpp
public FormControl control(int controlId)
```

### Parameters - control

controlId  

### Return Value - control

## Method controlCallingMethod

```xpp
public FormControl controlCallingMethod()
```

### Return Value - controlCallingMethod

## Method controlId

```xpp
public int controlId(str controlName)
```

### Parameters - controlId

controlName  

### Return Value - controlId

## Method controlMethodOverload

```xpp
public boolean controlMethodOverload([boolean value])
```

### Parameters - controlMethodOverload

value  

### Return Value - controlMethodOverload

## Method controlMethodOverloadObject

```xpp
public Object controlMethodOverloadObject([Object value])
```

### Parameters - controlMethodOverloadObject

value  

### Return Value - controlMethodOverloadObject

## Method copy

```xpp
public boolean copy()
```

### Return Value - copy

## Method cut

```xpp
public boolean cut()
```

### Return Value - cut

## Method dataSource

```xpp
public FormObjectSet dataSource([AnyType objectSet])
```

### Parameters - dataSource

objectSet  

### Return Value - dataSource

## Method dataSourceCount

```xpp
public int dataSourceCount()
```

### Return Value - dataSourceCount

## Method defaultDataSource

```xpp
public FormObjectSet defaultDataSource([FormObjectSet value])
```

### Parameters - defaultDataSource

value  

### Return Value - defaultDataSource

## Method defaultInitialQueryValuesOnCreate

```xpp
public boolean defaultInitialQueryValuesOnCreate([boolean value])
```

### Parameters - defaultInitialQueryValuesOnCreate

value  

### Return Value - defaultInitialQueryValuesOnCreate

## Method design

```xpp
public FormDesign design([int reserved])
```

### Parameters - design

reserved  

### Return Value - design

## Method docCursor

```xpp
public Common docCursor()
```

### Return Value - docCursor

## Method enableCountryRegion

```xpp
public boolean enableCountryRegion([boolean flag])
```

### Parameters - enableCountryRegion

flag  

### Return Value - enableCountryRegion

## Method form

```xpp
public Form form()
```

### Return Value - form

## Method getActiveWorkflowConfiguration

```xpp
public Common getActiveWorkflowConfiguration()
```

### Return Value - getActiveWorkflowConfiguration

## Method getActiveWorkflowTrackingStatus

```xpp
public Common getActiveWorkflowTrackingStatus()
```

### Return Value - getActiveWorkflowTrackingStatus

## Method getActiveWorkflowWorkItem

```xpp
public Common getActiveWorkflowWorkItem()
```

### Return Value - getActiveWorkflowWorkItem

## Method getAutoCompleteString

```xpp
public container getAutoCompleteString(int startIdx, [FormControl control], [str searchString])
```

### Parameters - getAutoCompleteString

startIdx  

<!-- -->

control  

<!-- -->

searchString  

### Return Value - getAutoCompleteString

## Method getFormHelpTopic

```xpp
public str getFormHelpTopic()
```

### Return Value - getFormHelpTopic

## Method getNextField

```xpp
public FormControl getNextField(FormControl control, [int flags])
```

### Parameters - getNextField

control  

<!-- -->

flags  

### Return Value - getNextField

## Method getPrevField

```xpp
public FormControl getPrevField(FormControl control, [int flags])
```

### Parameters - getPrevField

control  

<!-- -->

flags  

### Return Value - getPrevField

## Method hasExecutedInit

```xpp
public boolean hasExecutedInit()
```

### Return Value - hasExecutedInit

## Method hWnd

```xpp
public int hWnd()
```

### Return Value - hWnd

## Method installMessageProc

```xpp
public int installMessageProc(int message, int handle, str method)
```

### Parameters - installMessageProc

message  

<!-- -->

handle  

<!-- -->

method  

### Return Value - installMessageProc

## Method inViewMode

```xpp
public boolean inViewMode()
```

### Return Value - inViewMode

## Method isDataInteractionSupported

```xpp
public boolean isDataInteractionSupported()
```

### Return Value - isDataInteractionSupported

## Method isPreloadedInstance

```xpp
public boolean isPreloadedInstance()
```

### Return Value - isPreloadedInstance

## Method isFormPart

```xpp
public boolean isFormPart()
```

### Return Value - isFormPart

## Method isFactBox

```xpp
public boolean isFactBox()
```

### Return Value - isFactBox

## Method isLookupForm

```xpp
public boolean isLookupForm()
```

### Return Value - isLookupForm

## Method isPartRemote

```xpp
public boolean isPartRemote()
```

### Return Value - isPartRemote

## Method isPartLocal

```xpp
public boolean isPartLocal()
```

### Return Value - isPartLocal

## Method isWorkflowEnabled

```xpp
public boolean isWorkflowEnabled()
```

### Return Value - isWorkflowEnabled

## Method loadWorkflowConfiguration

```xpp
public Common loadWorkflowConfiguration()
```

### Return Value - loadWorkflowConfiguration

## Method lockWindowUpdate

```xpp
public boolean lockWindowUpdate(boolean lock)
```

### Parameters - lockWindowUpdate

lock  

### Return Value - lockWindowUpdate

## Method name

```xpp
public str name()
```

### Return Value - name

## Method objectSet

```xpp
public FormObjectSet objectSet([AnyType objectSet])
```

### Parameters - objectSet

objectSet  

### Return Value - objectSet

## Method resetAsyncOperationsPendingState

```xpp
public boolean resetAsyncOperationsPendingState()
```

### Return Value - resetAsyncOperationsPendingState

## Method pageInteraction

```xpp
public PageInteraction pageInteraction()
```

### Return Value - pageInteraction

## Method paste

```xpp
public boolean paste()
```

### Return Value - paste

## Method recordingScopeId

```xpp
public str recordingScopeId()
```

### Return Value - recordingScopeId

## Method removeMessageProc

```xpp
public boolean removeMessageProc(int message, int handle)
```

### Parameters - removeMessageProc

message  

<!-- -->

handle  

### Return Value - removeMessageProc

## Method rootFormDataSources

```xpp
public List rootFormDataSources()
```

### Return Value - rootFormDataSources

## Method selectControl

```xpp
public boolean selectControl(FormControl control)
```

### Parameters - selectControl

control  

### Return Value - selectControl

## Method selectedControl

```xpp
public FormControl selectedControl()
```

### Return Value - selectedControl

## Method selectRecordModeSelectedRecord

```xpp
public Common selectRecordModeSelectedRecord([Common selectedRecord])
```

### Parameters - selectRecordModeSelectedRecord

selectedRecord  

### Return Value - selectRecordModeSelectedRecord

## Method selectTarget

```xpp
public FormControl selectTarget([FormControl target])
```

### Parameters - selectTarget

target  

### Return Value - selectTarget

## Method tabOrder

```xpp
public Array tabOrder([Array newValue])
```

### Parameters - tabOrder

newValue  

### Return Value - tabOrder

## Method task

```xpp
public int task(int taskId)
```

### Parameters - task

taskId  

### Return Value - task

## Method toString

```xpp
public str toString()
```

### Return Value - toString

## Method workflowDataSource

```xpp
public FormObjectSet workflowDataSource()
```

### Return Value - workflowDataSource

## Method workflowType

```xpp
public str workflowType()
```

### Return Value - workflowType

## Method runAsync

```xpp
public System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, [System.Threading.CancellationToken cancellationToken], [str callbackFormMethodName], [container asyncState], [str userId], [str company], [str language], [str partitionKey], [System.Threading.Tasks.TaskCreationOptions options])
```

### Parameters - runAsync

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

cancellationToken  

<!-- -->

callbackFormMethodName  

<!-- -->

asyncState  

<!-- -->

userId  

<!-- -->

company  

<!-- -->

language  

<!-- -->

partitionKey  

<!-- -->

options  

### Return Value - runAsync

## Method setTimeoutEx

```xpp
public System.Threading.Tasks.Task setTimeoutEx([str formMethodName], [container parms], [int delay], [System.Threading.CancellationToken cancellationToken])
```

### Parameters - setTimeoutEx

formMethodName  

<!-- -->

parms  

<!-- -->

delay  

<!-- -->

cancellationToken  

### Return Value - setTimeoutEx

## Method setParentHandle

```xpp
public void setParentHandle(int hwnd)
```

### Parameters - setParentHandle

hwnd  

## Method setFormHelpTopic

```xpp
public void setFormHelpTopic(str formHelpTopic)
```

### Parameters - setFormHelpTopic

formHelpTopic  

## Method setFactBoxEditable

```xpp
public void setFactBoxEditable()
```

## Method setAutoCompleteString

```xpp
public void setAutoCompleteString(str string, AnyType control)
```

### Parameters - setAutoCompleteString

string  

<!-- -->

control  

## Method RaiseOnClosing

```xpp
public void RaiseOnClosing([FormEventArgs e])
```

### Parameters - RaiseOnClosing

e  

## Method inlineLoadingKey

```xpp
public void inlineLoadingKey(FormControl parentControl)
```

### Parameters - inlineLoadingKey

parentControl  

## Method closeSelect

```xpp
public void closeSelect(str selectString)
```

### Parameters - closeSelect

selectString  

## Method RaiseOnActivated

```xpp
public void RaiseOnActivated([FormEventArgs e])
```

### Parameters - RaiseOnActivated

e  

## Method prevField

```xpp
public void prevField([int flags])
```

### Parameters - prevField

flags  

## Method send

```xpp
public void send()
```

## Method RaiseOnInitializing

```xpp
public void RaiseOnInitializing([FormEventArgs e])
```

### Parameters - RaiseOnInitializing

e  

## Method updateWorkflowControls

```xpp
public void updateWorkflowControls()
```

## Method closeCancel

```xpp
public void closeCancel()
```

## Method lastField

```xpp
public void lastField([int flags])
```

### Parameters - lastField

flags  

## Method wait

```xpp
public void wait([boolean modal])
```

### Parameters - wait

modal  

## Method unLock

```xpp
public void unLock([boolean arrangeNow])
```

### Parameters - unLock

arrangeNow  

## Method OnInitialized

```xpp
private void OnInitialized([xFormRun sender], [FormEventArgs e])
```

### Parameters - OnInitialized

sender  

<!-- -->

e  

## Method detach

```xpp
public void detach()
```

## Method resetStatusBarBackgroundColor

```xpp
public void resetStatusBarBackgroundColor()
```

## Method OnClosing

```xpp
private void OnClosing([xFormRun sender], [FormEventArgs e])
```

### Parameters - OnClosing

sender  

<!-- -->

e  

## Method addDisplayMethod

```xpp
public void addDisplayMethod(str name, int displayKind, int displayType, int displayXType, int displayRecord, [str dataSourceName], [boolean isTableDisplayMethod])
```

### Parameters - addDisplayMethod

name  

<!-- -->

displayKind  

<!-- -->

displayType  

<!-- -->

displayXType  

<!-- -->

displayRecord  

<!-- -->

dataSourceName  

<!-- -->

isTableDisplayMethod  

## Method print

```xpp
public void print()
```

## Method activate

```xpp
public void activate(boolean active)
```

### Parameters - activate

active  

## Method resize

```xpp
public void resize(int width, int height)
```

### Parameters - resize

width  

<!-- -->

height  

## Method reload

```xpp
public void reload([xArgs args])
```

### Parameters - reload

args  

## Method finalize

```xpp
public void finalize()
```

## Method RaiseOnInitialized

```xpp
public void RaiseOnInitialized([FormEventArgs e])
```

### Parameters - RaiseOnInitialized

e  

## Method resetSize

```xpp
public void resetSize()
```

## Method clientId

```xpp
public void clientId(str clientId)
```

### Parameters - clientId

clientId  

## Method createRecord

```xpp
public void createRecord(str formDataSourceName, [boolean append])
```

### Parameters - createRecord

formDataSourceName  

<!-- -->

append  

## Method firstField

```xpp
public void firstField([int flags])
```

### Parameters - firstField

flags  

## Method savePersonalization

```xpp
public void savePersonalization(str controlName, str propertyKey, str propertyValue)
```

### Parameters - savePersonalization

controlName  

<!-- -->

propertyKey  

<!-- -->

propertyValue  

## Method expandFactBoxPaneAtStart

```xpp
public void expandFactBoxPaneAtStart()
```

## Method redraw

```xpp
public void redraw()
```

## Method arrange

```xpp
public void arrange()
```

## Method blockPersonalization

```xpp
public void blockPersonalization(boolean blockPersonalization)
```

### Parameters - blockPersonalization

blockPersonalization  

## Method nextField

```xpp
public void nextField([int flags])
```

### Parameters - nextField

flags  

## Method nextGroup

```xpp
public void nextGroup()
```

## Method prevGroup

```xpp
public void prevGroup()
```

## Method setFormPartStyle

```xpp
public void setFormPartStyle(boolean isFactBox)
```

### Parameters - setFormPartStyle

isFactBox  

## Method run

```xpp
public void run()
```

## Method setActive

```xpp
public void setActive()
```

## Method closeSelectRecord

```xpp
public void closeSelectRecord(Common selectedRecord)
```

### Parameters - closeSelectRecord

selectedRecord  

## Method registerFormSpecializedCustomControl

```xpp
public void registerFormSpecializedCustomControl(str customControlName)
```

### Parameters - registerFormSpecializedCustomControl

customControlName  

## Method setApply

```xpp
public void setApply(Object object, [Object parm])
```

### Parameters - setApply

object  

<!-- -->

parm  

## Method new

```xpp
public void new(xArgs args)
```

### Parameters - new

args  

## Method RegisterXppILImplementation

```xpp
public void RegisterXppILImplementation(str className)
```

### Parameters - RegisterXppILImplementation

className  

## Method sysColorChanged

```xpp
public void sysColorChanged()
```

## Method selectRecordMode

```xpp
public void selectRecordMode([FormControl control])
```

### Parameters - selectRecordMode

control  

## Method OnPostRun

```xpp
private void OnPostRun([xFormRun sender], [FormEventArgs e])
```

### Parameters - OnPostRun

sender  

<!-- -->

e  

## Method skipSaveUserSetting

```xpp
public void skipSaveUserSetting(boolean skip)
```

### Parameters - skipSaveUserSetting

skip  

## Method selectMode

```xpp
public void selectMode([FormControl control])
```

### Parameters - selectMode

control  

## Method printPreview

```xpp
public void printPreview()
```

## Method OnActivated

```xpp
private void OnActivated([xFormRun sender], [FormEventArgs e])
```

### Parameters - OnActivated

sender  

<!-- -->

e  

## Method collapseFactBoxPaneAtStart

```xpp
public void collapseFactBoxPaneAtStart()
```

## Method lock

```xpp
public void lock()
```

## Method init

```xpp
public void init()
```

## Method formOnTop

```xpp
public void formOnTop()
```

## Method close

```xpp
public void close()
```

## Method delAutoCompleteString

```xpp
public void delAutoCompleteString([AnyType control])
```

### Parameters - delAutoCompleteString

control  

## Method closeOk

```xpp
public void closeOk()
```

## Method modeledQueryName

```xpp
public void modeledQueryName(str queryName)
```

### Parameters - modeledQueryName

queryName  

## Method initWorkflowControls

```xpp
public void initWorkflowControls()
```

## Method setOrder

```xpp
public void setOrder(FormControl control, FormControl control1, [boolean before])
```

### Parameters - setOrder

control  

<!-- -->

control1  

<!-- -->

before  

## Method allowCrossFormLinks

```xpp
public void allowCrossFormLinks(boolean allowCrossFormLinks)
```

### Parameters - allowCrossFormLinks

allowCrossFormLinks  

## Method RaiseOnPostRun

```xpp
public void RaiseOnPostRun([FormEventArgs e])
```

### Parameters - RaiseOnPostRun

e  

## Method setStatusBarBackgroundColor

```xpp
public void setStatusBarBackgroundColor(int a, int r, int g, int b)
```

### Parameters - setStatusBarBackgroundColor

a  

<!-- -->

r  

<!-- -->

g  

<!-- -->

b  

## Method loadPersonalization

```xpp
public void loadPersonalization()
```

## Method doApply

```xpp
public void doApply()
```

## Method OnInitializing

```xpp
private void OnInitializing([xFormRun sender], [FormEventArgs e])
```

### Parameters - OnInitializing

sender  

<!-- -->

e  

## Method flushCountryRegionCodeCache

```xpp
public void flushCountryRegionCodeCache()
```

## Method localRefresh

```xpp
public void localRefresh()
```

