---
title: List module
description: A list is a control that contains any numbers of rows.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# List module

[!include [banner](../../../../includes/banner.md)]

A list is a control that contains any numbers of rows.
Each row follows a template for the layout of any number of controls.
Lists come in two styles: simple and card.

## Index

### Types

* [List](../interfaces/view-model-control-list-ilist-ilist.md)
* [ListDesign](../interfaces/view-model-control-list-ilist-ilistdesign.md)
* [ListMetadata](../interfaces/view-model-control-list-ilist-ilistmetadata.md)
* [Row](../interfaces/view-model-control-list-ilist-irow.md)

## Types


### List

#### Hierarchy

[ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ List <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [$accessibility](../interfaces/view-model-control-list-ilist-ilist.md#accessibility) |$accessibility: any <br>|  |
| [DefaultSearchColumn](../interfaces/view-model-control-list-ilist-ilist.md#defaultsearchcolumn) |DefaultSearchColumn: string <br>|  |
| [container](../interfaces/view-model-control-list-ilist-ilist.md#container) |container: boolean <br>|True if the control is a container.<br>  Inherited from [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md).[container](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#container) <br> Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [emptyListMessage](../interfaces/view-model-control-list-ilist-ilist.md#emptylistmessage) |emptyListMessage: string <br>|Settable property to override default empty list message.<br>  |
| [enableMultiSelect](../interfaces/view-model-control-list-ilist-ilist.md#enablemultiselect) |enableMultiSelect: boolean <br>|  |
| [generic](../interfaces/view-model-control-list-ilist-ilist.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-list-ilist-ilist.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [hidden](../interfaces/view-model-control-list-ilist-ilist.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |
| [hideEmptyListMessage](../interfaces/view-model-control-list-ilist-ilist.md#hideemptylistmessage) |hideEmptyListMessage: boolean <br>|If true, no message is shown if the list is empty. To set this property, update the corresponding metadata property via configureControl.<br>  |
| [imageFields](../interfaces/view-model-control-list-ilist-ilist.md#imagefields) |imageFields: any [ ] <br>|  |
| [performingRemoteSearch](../interfaces/view-model-control-list-ilist-ilist.md#performingremotesearch) |performingRemoteSearch: boolean <br>|  |
| [searchQuery](../interfaces/view-model-control-list-ilist-ilist.md#searchquery) |searchQuery: [value: string]: any <br>|  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [allowsNavigation](../interfaces/view-model-control-list-ilist-ilist.md#allowsnavigation) |allowsNavigation(): boolean|  |
| [applyDesign](../interfaces/view-model-control-list-ilist-ilist.md#applydesign) |applyDesign(IDesign: [ListDesign](../interfaces/view-model-control-list-ilist-ilistdesign.md)): void|Applies given design to the design on the control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [applySearch](../interfaces/view-model-control-list-ilist-ilist.md#applysearch) |applySearch(): void|  |
| [canPerformRemoteSearch](../interfaces/view-model-control-list-ilist-ilist.md#canperformremotesearch) |canPerformRemoteSearch(): boolean|  |
| [clearSearch](../interfaces/view-model-control-list-ilist-ilist.md#clearsearch) |clearSearch(): void|  |
| [dataContext](../interfaces/view-model-control-list-ilist-ilist.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getColumnLabel](../interfaces/view-model-control-list-ilist-ilist.md#getcolumnlabel) |getColumnLabel(id: string): string|  |
| [getControl](../interfaces/view-model-control-list-ilist-ilist.md#getcontrol) |getControl(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|Given the name of a control, returns the control instance.<br>  Inherited from [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md).[getControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrol) <br> |
| [getControlById](../interfaces/view-model-control-list-ilist-ilist.md#getcontrolbyid) |getControlById(id: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|Given the ID of a control, returns the control instance.<br>  Inherited from [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md).[getControlById](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrolbyid) <br> |
| [getControlMetadata](../interfaces/view-model-control-list-ilist-ilist.md#getcontrolmetadata) |getControlMetadata(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getControlMetadataById](../interfaces/view-model-control-list-ilist-ilist.md#getcontrolmetadatabyid) |getControlMetadataById(id: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getData](../interfaces/view-model-control-list-ilist-ilist.md#getdata) |getData(): any [ ]|  |
| [getDesign](../interfaces/view-model-control-list-ilist-ilist.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [getListData](../interfaces/view-model-control-list-ilist-ilist.md#getlistdata) |getListData(): any|  |
| [getRenderedRows](../interfaces/view-model-control-list-ilist-ilist.md#getrenderedrows) |getRenderedRows(): [Row](../interfaces/view-model-control-list-ilist-irow.md) [ ]|  |
| [getRowNavigation](../interfaces/view-model-control-list-ilist-ilist.md#getrownavigation) |getRowNavigation(row: [Row](../interfaces/view-model-control-list-ilist-irow.md)): Promise &lt;any&gt; &#124; any|  |
| [getRowSelectionCount](../interfaces/view-model-control-list-ilist-ilist.md#getrowselectioncount) |getRowSelectionCount(): number|  |
| [getRowSelections](../interfaces/view-model-control-list-ilist-ilist.md#getrowselections) |getRowSelections(): string [ ]|  |
| [getRowTracking](../interfaces/view-model-control-list-ilist-ilist.md#getrowtracking) |getRowTracking(row: any, index: string): string|  |
| [getSearchColumn](../interfaces/view-model-control-list-ilist-ilist.md#getsearchcolumn) |getSearchColumn(): string|  |
| [getSearchColumnLabel](../interfaces/view-model-control-list-ilist-ilist.md#getsearchcolumnlabel) |getSearchColumnLabel(): string|  |
| [getSearchableColumns](../interfaces/view-model-control-list-ilist-ilist.md#getsearchablecolumns) |getSearchableColumns(): any [ ]|  |
| [hideSearchBar](../interfaces/view-model-control-list-ilist-ilist.md#hidesearchbar) |hideSearchBar(): boolean|  |
| [isEditable](../interfaces/view-model-control-list-ilist-ilist.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [loadMetaData](../interfaces/view-model-control-list-ilist-ilist.md#loadmetadata) |loadMetaData(): void|  |
| [loadMore](../interfaces/view-model-control-list-ilist-ilist.md#loadmore) |loadMore(): void|  |
| [metadata](../interfaces/view-model-control-list-ilist-ilist.md#metadata) |metadata(): [ListMetadata](../interfaces/view-model-control-list-ilist-ilistmetadata.md)|Returns the metadata object of this control.<br>  Overrides [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md).[metadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-list-ilist-ilist.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [performRemoteSearch](../interfaces/view-model-control-list-ilist-ilist.md#performremotesearch) |performRemoteSearch(): void|  |
| [root](../interfaces/view-model-control-list-ilist-ilist.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |
| [selectSearchColumn](../interfaces/view-model-control-list-ilist-ilist.md#selectsearchcolumn) |selectSearchColumn(column: string): void|  |
| [setRowSections](../interfaces/view-model-control-list-ilist-ilist.md#setrowsections) |setRowSections(selections: string [ ]): void|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onRowCreate](../interfaces/view-model-control-list-ilist-ilist.md#onrowcreate) |onRowCreate: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;[Row](../interfaces/view-model-control-list-ilist-irow.md)&gt; <br>|  |
| [onRowSelect](../interfaces/view-model-control-list-ilist-ilist.md#onrowselect) |onRowSelect: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;[Row](../interfaces/view-model-control-list-ilist-irow.md)&gt; <br>|  |


### ListDesign

#### Hierarchy

[ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ ListDesign <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-list-ilist-ilistdesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-list-ilist-ilistdesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [allowScroll](../interfaces/view-model-control-list-ilist-ilistdesign.md#allowscroll) |allowScroll: string (optional)  <br>|True if the container will allow scrolling when its items do not fit into the container's available space. If a container has an item which may scroll, then set this property to false to prevent nested scrolling areas.<br>  Inherited from [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md).[allowScroll](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#allowscroll) <br> |
| [background](../interfaces/view-model-control-list-ilist-ilistdesign.md#background) |background: string (optional)  <br>|The background color of the container.<br>  Inherited from [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md).[background](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#background) <br> |
| [bindings](../interfaces/view-model-control-list-ilist-ilistdesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-list-ilist-ilistdesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-list-ilist-ilistdesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [design](../interfaces/view-model-control-list-ilist-ilistdesign.md#design) |design: [GroupDesign](../interfaces/view-model-control-group-igroup-igroupdesign.md) (optional)  <br>|The design object that will be applied to each row.<br>  |
| [flexFlow](../interfaces/view-model-control-list-ilist-ilistdesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-list-ilist-ilistdesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-list-ilist-ilistdesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-list-ilist-ilistdesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [hideArrow](../interfaces/view-model-control-list-ilist-ilistdesign.md#hidearrow) |hideArrow: boolean (optional)  <br>|Allows an arrow ( > ) on a default styled navigation control to be hidden.<br>  |
| [hideSearchBar](../interfaces/view-model-control-list-ilist-ilistdesign.md#hidesearchbar) |hideSearchBar: boolean (optional)  <br>|If true, the search bar will be hidden.<br>  |
| [itemBorder](../interfaces/view-model-control-list-ilist-ilistdesign.md#itemborder) |itemBorder: "solid" &#124; "none" (optional)  <br>|If true, a border will appear around each row in the list.<br>  Inherited from [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md).[itemBorder](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#itemborder) <br> |
| [items](../interfaces/view-model-control-list-ilist-ilistdesign.md#items) |items: string &#124; [Design](../interfaces/view-model-ipage-idesign.md) \[ \] (optional)  <br>|An array containing the components to place inside of the container.<br>  Inherited from [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md).[items](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#items) <br> |
| [justifyItems](../interfaces/view-model-control-list-ilist-ilistdesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-list-ilist-ilistdesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-list-ilist-ilistdesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-list-ilist-ilistdesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [padding](../interfaces/view-model-control-list-ilist-ilistdesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [type](../interfaces/view-model-control-list-ilist-ilistdesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### ListMetadata

#### Hierarchy

[ContainerControlMetadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ ListMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-list-ilist-ilistmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-list-ilist-ilistmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [Children](../interfaces/view-model-control-list-ilist-ilistmetadata.md#children) |Children: [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md) \[ \] (optional)  <br>|List of metadata for controls that will appear in each row of the list.<br>  |
| [Description](../interfaces/view-model-control-list-ilist-ilistmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [DetailsPageAppId](../interfaces/view-model-control-list-ilist-ilistmetadata.md#detailspageappid) |DetailsPageAppId: string (optional)  <br>|App ID of the page that each row in the list will navigate to.<br>  |
| [DetailsPageId](../interfaces/view-model-control-list-ilist-ilistmetadata.md#detailspageid) |DetailsPageId: string (optional)  <br>|The ID of the page to which each row will navigate.<br>  |
| [Editable](../interfaces/view-model-control-list-ilist-ilistmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [EmptyListMessage](../interfaces/view-model-control-list-ilist-ilistmetadata.md#emptylistmessage) |EmptyListMessage: string (optional)  <br>|If set, overrides the default message for empty lists.<br>  |
| [ExtType](../interfaces/view-model-control-list-ilist-ilistmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [HelpText](../interfaces/view-model-control-list-ilist-ilistmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-list-ilist-ilistmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [HideEmptyListMessage](../interfaces/view-model-control-list-ilist-ilistmetadata.md#hideemptylistmessage) |HideEmptyListMessage: boolean (optional)  <br>|If true, the empty list message will be hidden.<br>  |
| [HideSearchBar](../interfaces/view-model-control-list-ilist-ilistmetadata.md#hidesearchbar) |HideSearchBar: boolean (optional)  <br>|If true, the search bar will be hidden.<br>  |
| [Id](../interfaces/view-model-control-list-ilist-ilistmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [InfiniteScroll](../interfaces/view-model-control-list-ilist-ilistmetadata.md#infinitescroll) |InfiniteScroll: boolean (optional)  <br>|If set to true then the list will allow infinite scroll.<br>  |
| [InfiniteScrollPageSize](../interfaces/view-model-control-list-ilist-ilistmetadata.md#infinitescrollpagesize) |InfiniteScrollPageSize: number (optional)  <br>|Number of rows to load initially and the number of rows to load after the user reaches the end of the currently displayed rows.<br>  |
| [Label](../interfaces/view-model-control-list-ilist-ilistmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [ListStyle](../interfaces/view-model-control-list-ilist-ilistmetadata.md#liststyle) |ListStyle: string (optional)  <br>|Dictates the list template type.<br>  |
| [MultiSelect](../interfaces/view-model-control-list-ilist-ilistmetadata.md#multiselect) |MultiSelect: boolean (optional)  <br>|If true, then the list will be a multi-select list.<br>  |
| [Name](../interfaces/view-model-control-list-ilist-ilistmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [NonEntityProjection](../interfaces/view-model-control-list-ilist-ilistmetadata.md#nonentityprojection) |NonEntityProjection: boolean (optional)  <br>|  |
| [Order](../interfaces/view-model-control-list-ilist-ilistmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [Type](../interfaces/view-model-control-list-ilist-ilistmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [navigationHandler](../interfaces/view-model-control-list-ilist-ilistmetadata.md#navigationhandler) |Optional navigationHandler(row: [Row](../interfaces/view-model-control-list-ilist-irow.md)): Promise &lt;any&gt; &#124; [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)|A function that determines the navigation for a given row.<br>  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [OnNavigate](../interfaces/view-model-control-list-ilist-ilistmetadata.md#onnavigate) |OnNavigate: function(navigation: [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)): any (optional)  <br>|An event that is triggered when a pagelink control is selected.<br>  |
| [OnRowSelect](../interfaces/view-model-control-list-ilist-ilistmetadata.md#onrowselect) |OnRowSelect: function(row: [Row](../interfaces/view-model-control-list-ilist-irow.md)): void (optional)  <br>|An event that is triggered when a row is selected.<br>  |


### Row

#### Hierarchy

Row <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [fieldList](../interfaces/view-model-control-list-ilist-irow.md#fieldlist) |fieldList: [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) [ ] <br>|  |
| [headerField](../interfaces/view-model-control-list-ilist-irow.md#headerfield) |headerField: [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) <br>|  |
| [hidden](../interfaces/view-model-control-list-ilist-irow.md#hidden) |hidden: boolean <br>|If true then the row will be hidden.<br>  |
| [imageFields](../interfaces/view-model-control-list-ilist-irow.md#imagefields) |imageFields: [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) [ ] <br>|  |
| [isSelected](../interfaces/view-model-control-list-ilist-irow.md#isselected) |isSelected: boolean <br>|  |
| [item](../interfaces/view-model-control-list-ilist-irow.md#item) |item: any <br>|A container of rendered data.<br>  |
| [template](../interfaces/view-model-control-list-ilist-irow.md#template) |template: [Group](../interfaces/view-model-control-group-igroup-igroup.md) <br>|Group control that represents the template for a row.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [getControl](../interfaces/view-model-control-list-ilist-irow.md#getcontrol) |getControl(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getControlById](../interfaces/view-model-control-list-ilist-irow.md#getcontrolbyid) |getControlById(id: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getControlValueById](../interfaces/view-model-control-list-ilist-irow.md#getcontrolvaluebyid) |getControlValueById(id: string): string|  |
| [getRowHeader](../interfaces/view-model-control-list-ilist-irow.md#getrowheader) |getRowHeader(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getRowId](../interfaces/view-model-control-list-ilist-irow.md#getrowid) |getRowId(): string|  |
| [hasImageField](../interfaces/view-model-control-list-ilist-irow.md#hasimagefield) |hasImageField(): boolean|Returns true if the row has an image field.<br>  |
| [isEntityCreatedNew](../interfaces/view-model-control-list-ilist-irow.md#isentitycreatednew) |isEntityCreatedNew(): boolean|  |
| [isEntityDeleted](../interfaces/view-model-control-list-ilist-irow.md#isentitydeleted) |isEntityDeleted(): boolean|  |
| [isEntityModified](../interfaces/view-model-control-list-ilist-irow.md#isentitymodified) |isEntityModified(): boolean|  |
| [isEntitySyncPending](../interfaces/view-model-control-list-ilist-irow.md#isentitysyncpending) |isEntitySyncPending(): boolean|  |
| [select](../interfaces/view-model-control-list-ilist-irow.md#select) |select(): any|  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]