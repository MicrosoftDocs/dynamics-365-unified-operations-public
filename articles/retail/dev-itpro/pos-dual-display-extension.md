---
# required metadata

title: POS Dual display extension
description: This topic explains how to extend POS dual display with custom information. 
author: mugunthanm
manager: AnnBe
ms.date: 05/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.search.region: Global 
ms.search.industry: retail
ms.author: mumani
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1
---

# POS Dual display extension

[!include[banner](../includes/banner.md)]

This topic explains how to extend POS dual display with custom information. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail 7.2 with KB 4091080 and higher versions.

POS Dual display can be extended by adding a custom control to the dual display view and within the custom control you can add any images, POS data list, labels etc. to show custom information.

> [!NOTE]
> Dual display can be extended only by adding custom control and it will override the standard content shown in the dual display.

## Steps required to customize POS dual display:

1.  Configure the hardware profile to enable dual display.

2.  Create a new folder in POS.Extensions project for dual display extension.

3.  Add new custom control with custom information.

4.  Update Manifest and extension.json with the dual display extension.

5.  Deploy the changes and validate.

## Scenario or Business problem

Let’s add custom control column in POS dual display view to show the cart detail, customer and store employee information.

### Configure Hardware profile to enable Dual display

1.  Login to Dynamics 365 for Retail or Finance and Operations.

2.  Navigate to Retail > Channel setup > POS setup > POS profiles > Hardware profiles

3.  Select the hardware profile linked to your register.

4.  Expand the dual display tab and Set Dual display in use to **Yes**.

5.  Navigate to Retail > Retail IT > Distribution schedule.

6.  Select the Registers (1090) job and click Run now.

> [!NOTE]
> You can find this same sample E2E in …\\RetailSDK\\POS\\Extensions\\DualDisplaySample

## Add new custom control for dual display extension

1.  Open visual studio 2015 in administrator mode.

2.  Open ModernPOS solution from …\\RetailSDK\\POS

3.  Under the POS.Extensions project create a new folder called DualDisplayExtension.

4.  Under DualDisplayExtension, create new folder called CustomControl.

5.  Under CustomControl folder, create a new html file and name it as DualDisplayCustomControl.html

    In the html file we will add data list control to show the cart details and text controls to show total amount, customer name, customer name, employee name and logon status.

6.  Copy paste the below code in the DualDisplayCustomControl.html file:

```typescript

<!DOCTYPE html>                                                                                                                                                         
                                                                                                                                                                                
 <html lang="en" xmlns="http://www.w3.org/1999/xhtml">                                                                                                                    
                                                                                                                                                                                
 <head>                                                                                                                                                                   
                                                                                                                                                                                
 <meta charset="utf-8" />                                                                                                                                                 
                                                                                                                                                                                
 <title></title>                                                                                                                                                    
                                                                                                                                                                                
 </head>                                                                                                                                                                  
                                                                                                                                                                                
 <body>                                                                                                                                                                   
                                                                                                                                                                                
 <!-- Note: The element id is different than the id generated by the POS extensibility framework. This 'template' id is not used by the POS extensibility framework. -->  
                                                                                                                                                                                
 <script id="Microsot_Pos_Extensibility_Samples_DualDisplay" type="text/html">                                                                                        
                                                                                                                                                                                
 <div class="height100Percent width100Percent">                                                                                                                                                                                                                                                                                        
     <div class="height700 width100Percent no-shrink col marginBottom20">                                                                                                                                                                                                                                                                 
 	<div class="col grow marginBottom48">                                                                                                                                                                                                                                                                             
 		<div id="dualDisplayDataListSample" data-bind="msPosDataList: cartLinesDataList">                                                                                                                                                                                                                           
		 </div>                                                                                                                                                                                                                                                                                                                                      
 	</div>                                                                                                                                                                                                                                                                                                                                       
    </div>                                                                                                                                                                   
                                                                                                                                                                                
	 <div class="marginBottom20">                                                                                                                                                                                                                                                                                                  
 		<h2 class="marginLeft8" data-bind="text: cartTotalAmountLabel">Total Amount:</h2>                                                                                                                                                                                                                              
		 <h2 class="marginLeft8" data-bind="text: cartTotalAmount"></h2>                                                                                                                                                                                                                                                       
		 <h2 class="marginLeft8" data-bind="text: customerNameLabel">Customer Name:</h2>                                                                                                                                                                                                                          
		 <h2 class="marginLeft8" data-bind="text: customerName"></h2>                                                                                                                                                                                                                                                        
		 <h2 class="marginLeft8" data-bind="text: customerAccountNumberLabel">Customer Account Number:</h2>                                                                                                                                                                                                             
 		<h2 class="marginLeft8" data-bind="text: customerAccountNumber"></h2>                                                                                                                                                                                                                                                  
 		<h2 class="marginLeft8" data-bind="text: isLoggedOn() ? 'logged in' : 'logged out'"></h2>                                                                                                                                                                                                                               
 		<h2 class="marginLeft8" data-bind="text: employeeNameLabel">Employee Name:</h2>                                                                                                                                                                                                                                          
		 <h2 class="marginLeft8" data-bind="text: employeeName"></h2>                                                                                                                                                                                                                                                                
 	</div>                                                                                                                                                                   
                                                                                                                                                                                
 </div>                                                                                                                                                                                                                                                                                                                                             
 </script>                                                                                                                                                                                                                                                                                                                                  
 </body>                                                                                                                                                                                                                                                                                                                                          
 </html>   
```                  

7.  Let’s add the resource file for the field name localization: Create a new folder called Resources under DualDisplayExtension.

8.  Inside Resources folder add new folder called Strings and inside that create one more folder called en-US

```typescript
    //======================================================================================================

    //======================================= Sample comment. ==============================================

    //======================================================================================================
 {
 //======================== extensions strings. ========================

"string_0" : "ID",
"_string_0.comment" : "Item ID label text",

"string_1" : "Name",
"_string_1.comment" : "Item name label text",

"string_2" : "Quantity",
"_string_2.comment" : "Item cost label text",

"string_3" : "Discount",
"_string_3.comment" : "Total amount label text",

"string_4" : "Cost",
"_string_4.comment" : "Item cost label text",

"string_5" : "Total Amount:",
"_string_5.comment" : "Total amount label text",

"string_6" : "Customer Name:",
"_string_6.comment" : "Customer name label text",

"string_7" : "Customer Account Number:",
"_string_7.comment" : "Customer account number label text",

"string_8" : "Employee Name:",
"_string_8.comment" : "Employee name label text"

}
```
9.  Under CustomControl folder, create new typescript file (.ts) and name it as DualDisplayCustomControl.ts

10.  Open the DualDisplayCustomControl.ts file

11.  Add the below import statement to import the relevant entities and context.

```typescript
import {
DualDisplayCustomControlBase,
IDualDisplayCustomControlState,
IDualDisplayCustomControlContext,
CartChangedData,
CustomerChangedData,
LogOnStatusChangedData
 } from "PosApi/Extend/DualDisplay";

import { DataList, IDataListState, SelectionMode } from "PosUISdk/Controls/DataList";
import { ObjectExtensions, StringExtensions } from "PosApi/TypeExtensions";
import { ProxyEntities } from "PosApi/Entities";
```
12.  Create a new class inside the DualDisplayCustomControl.ts file called DualDisplayCustomControl and extend it from DualDisplayCustomControlBase. We are extending from DualDisplayCustomControlBase class to get all the events exposed for dual display.

```typescript
export default class DualDisplayCustomControl extends DualDisplayCustomControlBase { }
```
13.  Inside the class add the below variables to get the cart, customer and employee details:

```typescript

private static readonly TEMPLATE_ID: string = "Microsot_Pos_Extensibility_Samples_DualDisplay";                                  
                                                                                                                                       
  // The data list to bind against and display with cart line information.                                                             
                                                                                                                                       
  public readonly cartLinesDataList: DataList<ProxyEntities.CartLine>;                                                           
                                                                                                                                       
  // Computed values for binding against.                                                                                                                                                                                                                                
 public readonly cartTotalAmount: Computed<number>;                                                                                                                                                                                                      
 public readonly customerName: Computed<string>;                                                                                                                                                                                                                
 public readonly customerAccountNumber: Computed<string>;                                                                                                                                                                                                       
 public readonly isLoggedOn: Computed<boolean>;                                                                                                                                                                                                                 
  public readonly employeeName: Computed<string>;                                                                                
                                                                                                                                       
  // Labels for binding against.                                                                                                       
                                                                                                                                       
  public readonly cartTotalAmountLabel: string;                                                                                        
  public readonly customerNameLabel: string;                                                                    
  public readonly customerAccountNumberLabel: string;                                                                                                                                                                                                                
  public readonly employeeNameLabel: string;                                                                                           
                                                                                                                                       
  // Observable values used for keeping track of state.                                                                                
                                                                                                                                       
  private readonly_cart: Observable<ProxyEntities.Cart>;                                                                                                                                                                                                 
  private readonly_cartLinesObservable: ObservableArray<ProxyEntities.CartLine>;                                                                                                                                                                              
  private readonly_customer: Observable<ProxyEntities.Customer>;                                                               
  private readonly_loggedOn: Observable<boolean>;                                                                                                                                                                                                         
  private readonly_employee: Observable<ProxyEntities.Employee>; private_selectedTenderLines: ProxyEntities.TenderLine[];  |
```

14.  Create a class constructor method to initialize all the variables:

```typescript

constructor(id: string, context: IDualDisplayCustomControlContext) {                                                              
                                                                                                                                    
 super(id, context);                                                                                                                
                                                                                                                                    
 // Initializes labels.                                                                                                             
                                                                                                                                    
 this.cartTotalAmountLabel = this.context.resources.getString("string_5");                                                                                                                                                                                     
 this.customerNameLabel = this.context.resources.getString("string_6");                                                                                                                                                                                
 this.customerAccountNumberLabel = this.context.resources.getString("string_7");                                                                                                                                                                                
 this.employeeNameLabel = this.context.resources.getString("string_8");                                                                                                                                                                                     

 // Initializes observable and computed values.                                                                                     
                                                                                                                                    
 this._cart = ko.observable(null);                                                                                                                                                                                                                              
 this._cartLinesObservable = ko.observableArray([]);                                                                                                                                                                                                         
 this._customer = ko.observable(null);                                                                                                                                                                                                                           
 this._loggedOn = ko.observable(false);                                                                                                                                                                                                                          
 this._employee = ko.observable(null);                                                                                                                                                                                                                      
 this.cartTotalAmount = ko.computed(() => {                                                                                      
                                                                                                                                    
 return ObjectExtensions.isNullOrUndefined(this._cart()) ? 0.00 : this._cart().TotalAmount;                                       
                                                                                                                                    
 });                                                                                                                                
                                                                                                                                    
 this.customerName = ko.computed(() => {                                                                                                                                                                                                                  
 return ObjectExtensions.isNullOrUndefined(this._customer()) ? StringExtensions.EMPTY : this._customer().Name;                    
                                                                                                                                    
 });                                                                                                                                
                                                                                                                                    
 this.customerAccountNumber = ko.computed(() => {                                                                                                                                                                                                             
 return ObjectExtensions.isNullOrUndefined(this._customer()) ? StringExtensions.EMPTY : this._customer().AccountNumber;           
                                                                                                                                    
 });                                                                                                                                
                                                                                                                                    
 this.isLoggedOn = ko.computed(() => {                                                                                                                                                                                                                        
 return this._loggedOn();                                                                                                                                                                                                                                       
 });                                                                                                                                
                                                                                                                                    
 this.employeeName = ko.computed(() => {                                                                                                                                                                                                                      
 return ObjectExtensions.isNullOrUndefined(this._employee()) ? StringExtensions.EMPTY : this._employee().Name;                    
                                                                                                                                    
 });                                                                                                                                
                                                                                                                                    
 this.cartChangedHandler = (data: CartChangedData) => {                                                                                                                                                                                                        
 this._cart(data.cart);                                                                                                                                                                                                                                        
 this._cartLinesObservable(ObjectExtensions.isNullOrUndefined(data.cart) ?[] : data.cart.CartLines)                             
                                                                                                                                    
 };                                                                                                                                 
                                                                                                                                    
 this.customerChangedHandler = (data: CustomerChangedData) => {                                                                                                                                                                                                
 this._customer(data.customer);                                                                                                    
                                                                                                                                    
 };                                                                                                                                 
                                                                                                                                    
 this.logOnStatusChangedHandler = (data: LogOnStatusChangedData) => {                                                            
                                                                                                                                    
 // Displays the busy indicator here, even though it's not necessary, in order to showcase and test the scenario.                   
                                                                                                                                    
 this.isProcessing = true;                                                                                                                                                                                                                                     
 window.setTimeout(() => {                                                                                                                                                                                                                                 
 this.isProcessing = false;                                                                                                                                                                                                                                      
 }, 1000);                                                                                                                                                                                                                                                      
 this._loggedOn(data.loggedOn);                                                                                                                                                                                                                            
 this._employee(data.employee);                                                                                                                                                                                                                                 
 }                                                                                                                                  
                                                                                                                                    
 // Initializes the cart lines data list                                                                                                                                                                                                                           
 let cartLinesDataListOptions: IDataListState<ProxyEntities.CartLine> = {                                                                                                                                                                             
 selectionMode: SelectionMode.None,                                                                                                                                                                                                                             
 itemDataSource: this._cartLinesObservable,                                                                                        
 columns:[                                                                                                                        
                                                                                                                                    
 {                                                                                                                                                                                                                                                               
 title: context.resources.getString("string_0"), // ID                                                                                                                                                                                                       
 ratio: 20,                                                                                                                                                                                                                                                     
 collapseOrder: 2,                                                                                                                                                                                                                                       
 minWidth: 50,                                                                                                                                                                                                                                              
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                        
 return ObjectExtensions.isNullOrUndefined(cartLine.ItemId) ? StringExtensions.EMPTY : cartLine.ItemId;                             
 }                                                                                                                                  
 },                                                                                                                                 
                                                                                                                                    
 {                                                                                                                                  
 title: context.resources.getString("string_1"), // Name                                                                                                                                                                                                      
 ratio: 50,                                                                                                                                                                                                                                                     
 collapseOrder: 4,                                                                                                                                                                                                                                               
 minWidth: 100,                                                                                                                                                                                                                                                  
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                           
 return ObjectExtensions.isNullOrUndefined(cartLine.Description) ? StringExtensions.EMPTY : cartLine.Description;                   
                                                                                                                                    
 }                                                                                                                                                                                                                                                                 
 },                                                                                                                                 
                                                                                                                                    
 {                                                                                                                                  
                                                                                                                                    
 title: context.resources.getString("string_2"), // Quantity                                                                       
 ratio: 10,                                                                                                                                                                                                                                                        
 collapseOrder: 3,                                                                                                                                                                                                                                        
 minWidth: 50,                                                                                                                                                                                                                                             
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                                 
 return ObjectExtensions.isNullOrUndefined(cartLine.Quantity) ? StringExtensions.EMPTY : cartLine.Quantity.toString();              
                                                                                                                                    
 }                                                                                                                                                                                                                                                                
 },                                                                                                                                                                                                                                                                  
 {                                                                                                                                  
                                                                                                                                    
 title: context.resources.getString("string_3"), // Discount                                                                                                                                                                                                      
 ratio: 10,                                                                                                                                                                                                                                                  
 collapseOrder: 1,                                                                                                                                                                                                                                                 
 minWidth: 50,                                                                                                                                                                                                                                                    
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                                
 return ObjectExtensions.isNullOrUndefined(cartLine.DiscountAmount) ? StringExtensions.EMPTY : cartLine.DiscountAmount.toString();                                                                                                                                  
 }                                                                                                                                                                                                                                                                   
 },                                                                                                                                                                                                                                                                   
 {                                                                                                                                  
                                                                                                                                    
 title: context.resources.getString("string_4"), // Cost                                                                                                                                                                                                           
 ratio: 10,                                                                                                                                                                                                                                                      
 collapseOrder: 5,                                                                                                                                                                                                                                             
 minWidth: 50,                                                                                                                                                                                                                                                   
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                       
 return ObjectExtensions.isNullOrUndefined(cartLine.TotalAmount) ? StringExtensions.EMPTY : cartLine.TotalAmount.toString();                                                                                                                                    
 }                                                                                                                                  
                                                                                                                                    
 }                                                                                                                                  
                                                                                                                                    
]                                                                                                                                 
                                                                                                                                    
 };        
 
 this.cartLinesDataList = new DataList(cartLinesDataListOptions);                                                                                                                                                                                                
 // Logs the completion of constructing the DualDisplayCustomControl.                                                               
                                                                                                                                    
 this.context.logger.logInformational("DualDisplayCustomControl constructed", this.context.logger.getNewCorrelationId());                                                                                                                                           
 }                                           
```
15.  Add the onReady method to bind the control to the specified html element.
```typescript
/**                                                                             
                                                                                    
* Binds the control to the specified element.                                     
                                                                                    
* @param {HTMLElement} element The element to which the control should be bound.  
                                                                                    
*/                                                                                
                                                                                    
 public onReady(element: HTMLElement): void {                                       
ko.applyBindingsToNode(element, {                                                                                                                       
 template: {                                                                                                                                                   
 name: DualDisplayCustomControl.TEMPLATE_ID,                                                                                                                  
 data: this                                                                                                                                                   
 }                                                                                  
                                                                                    
 });                                                                                
                                                                                    
 }
```
16.  Add the init method to initializer all the controls.

```typescript
 /**                                                                                                          
                                                                                                                 
* Initializes the control.                                                                                                                   
* @param {IDualDisplayCustomControlState} state The initial state of the page used to initialize the control.                                                                                                              
*/                                                                                                             
                                                                                                                 
 public init(state: IDualDisplayCustomControlState): void {                                                                                                                
 this._cart(state.cart);                                                                                                                                                                                              
 this._customer(state.customer);                                                                                                                                                                                         
 this._loggedOn(state.loggedOn);                                                                                
 this._employee(state.employee)                                                                                 
                                                                                                                 
 }
```
The overall class should look like below:
```typescript
 /**                                                                                                                                              
                                                                                                                                                     
* SAMPLE CODE NOTICE                                                                                                                                                                                                                                                                                
*                                                                                                                                                                                                                                                                                                
* THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,                                                                                                                                                                                       
* OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.                                                                                                                                                                    
* THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.                                                                                                                                                                                           
* NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.                                                                                                                                                  
*/                                                                                                                                                 
                                                                                                                                                     
 import {                                                                                                                                            
                                                                                                                                                     
 DualDisplayCustomControlBase,                                                                                                                                                                                                                                                                        
 IDualDisplayCustomControlState,                                                                                                                                                                                                                                                                     
 IDualDisplayCustomControlContext,                                                                                                                                                                                                                                                                
 CartChangedData,                                                                                                                                    
 CustomerChangedData,                                                                                                                                
 LogOnStatusChangedData                                                                                                                                                                                                                                                                                
 } from "PosApi/Extend/DualDisplay";                                                                                                                 
                                                                                                                                                     
 import { DataList, IDataListState, SelectionMode } from "PosUISdk/Controls/DataList";                                                               
 import { ObjectExtensions, StringExtensions } from "PosApi/TypeExtensions";                                                                                                                                                                                                                   
 import { ProxyEntities } from "PosApi/Entities";                                                                                                    
                                                                                                                                                     
 export default class DualDisplayCustomControl extends DualDisplayCustomControlBase {                                                                                                                                                                                                      
 private static readonly TEMPLATE_ID: string = "Microsot_Pos_Extensibility_Samples_DualDisplay";                                                
                                                                                                                                                     
 // The data list to bind against and display with cart line information.                                                                            
                                                                                                                                          
 public readonly cartLinesDataList: DataList<ProxyEntities.CartLine>;                                                                          
                                                                                                                                                     
 // Computed values for binding against.                                                                                                             
                                                                                                                                                     
 public readonly cartTotalAmount: Computed<number>;                                                                                                                                                                                                                                 
 public readonly customerName: Computed<string>;                                                                                                                                                                                                                                     
 public readonly customerAccountNumber: Computed<string>;                                                                                                                                                                                                                                  
 public readonly isLoggedOn: Computed<boolean>;                                                                                                                                                                                                                                             
 public readonly employeeName: Computed<string>;                                                                                               
                                                                                                                                                     
 // Labels for binding against.                                                                                                                      
                                                                                                                                                     
 public readonly cartTotalAmountLabel: string;                                                                                                                                                                                                                                             
 public readonly customerNameLabel: string;                                                                                                                                                                                                                                                        
 public readonly customerAccountNumberLabel: string;                                                                                                                                                                                                                                               
 public readonly employeeNameLabel: string;                                                                                                                                                                                                                                                      
 // Observable values used for keeping track of state.                                                                                               
                                                                                                                                                     
 private readonly_cart: Observable<ProxyEntities.Cart>;                                                                                      
 private readonly_cartLinesObservable: ObservableArray<ProxyEntities.CartLine>;                                                                                                                                                                                                   
 private readonly_customer: Observable<ProxyEntities.Customer>;                                                                                                                                                                                                                        
 private readonly_loggedOn: Observable<boolean>;                                                                                                                                                                                                                                        
 private readonly_employee: Observable<ProxyEntities.Employee>;                                                                                                                                                                                                                           
 constructor(id: string, context: IDualDisplayCustomControlContext) {                                                                                                                                                                                                                      
 super(id, context);                                                                                                                                 
                                                                                                                                                     
 // Initializes labels.                                                                                                                              
                                                                                                                                                     
 this.cartTotalAmountLabel = this.context.resources.getString("string_5");                                                                                                                                                                                                                    
 this.customerNameLabel = this.context.resources.getString("string_6");                                                                                                                                                                                                                           
 this.customerAccountNumberLabel = this.context.resources.getString("string_7");                                                                                                                                                                                                                   
 this.employeeNameLabel = this.context.resources.getString("string_8");                                                                                                                                                                                                                        
 // Initializes observable and computed values.                                                                                                                                                                                                                                                  
 this._cart = ko.observable(null);                                                                                                                                                                                                                                                           
 this._cartLinesObservable = ko.observableArray([]);                                                                                                                                                                                                                                           
 this._customer = ko.observable(null);                                                                                                                                                                                                                                         
 this._loggedOn = ko.observable(false);                                                                                                                                                                                                                                                         
 this._employee = ko.observable(null);                                                                                                                                                                                                                                                          
 this.cartTotalAmount = ko.computed(() => {                                                                                                                                                                                                                                                    
 return ObjectExtensions.isNullOrUndefined(this._cart()) ? 0.00 : this._cart().TotalAmount;                                                                                                                                                                                                    
 });                                                                                                                                                 
                                                                                                                                                     
 this.customerName = ko.computed(() => {                                                                                                          
  return ObjectExtensions.isNullOrUndefined(this._customer()) ? StringExtensions.EMPTY : this._customer().Name;                                                                                                                                                                              
 });                                                                                                                                                 
                                                                                                                                                     
 this.customerAccountNumber = ko.computed(() => {                                                                                                                                                                                                                                               
 return ObjectExtensions.isNullOrUndefined(this._customer()) ? StringExtensions.EMPTY : this._customer().AccountNumber;                            
                                                                                                                                                     
 });                                                                                                                                                 
                                                                                                                                                     
 this.isLoggedOn = ko.computed(() => {                                                                                                                                                                                                                                                          
 return this._loggedOn();                                                                                                                           
                                                                                                                                                     
 });                                                                                                                                                 
                                                                                                                                                     
 this.employeeName = ko.computed(() => {                                                                                                                                                                                                                                                         
 return ObjectExtensions.isNullOrUndefined(this._employee()) ? StringExtensions.EMPTY : this._employee().Name;                                     
                                                                                                                                                     
 });                                                                                                                                                                                                                                                                                                
 this.cartChangedHandler = (data: CartChangedData) => {                                                                                                                                                                                                                                            
 this._cart(data.cart);                                                                                                                             
 this._cartLinesObservable(ObjectExtensions.isNullOrUndefined(data.cart) ?[] : data.cart.CartLines)                                                                                                                                                                                            
 };                                                                                                                                                                                                                                                                                              
 this.customerChangedHandler = (data: CustomerChangedData) => {                                                                                                                                                                                                                                   
 this._customer(data.customer);                                                                                                                     
                                                                                                                                                     
 };                                                                                                                                                  
                                                                                                                                                     
 this.logOnStatusChangedHandler = (data: LogOnStatusChangedData) => {                                                                                                                                                                                                                      
 // Displays the busy indicator here, even though it's not necessary, in order to showcase and test the scenario.                                    
 this.isProcessing = true;                                                                                                                                                                                                                                                                      
 window.setTimeout(() => {                                                                                                                                                                                                                                                                  
 this.isProcessing = false;                                                                                                                          
                                                                                                                                                     
 }, 1000);                                                                                                                                           
                                                                                                                                                     
 this._loggedOn(data.loggedOn);                                                                                                                                                                                                                                                                
 this._employee(data.employee);                                                                                                                     
                                                                                                                                                     
 }                                                                                                                                                   
                                                                                                                                                     
 // Initializes the cart lines data list                                                                                                                                                                                                                                                       
 let cartLinesDataListOptions: IDataListState<ProxyEntities.CartLine> = {                                                                                                                                                                                                                   
 selectionMode: SelectionMode.None,                                                                                                                                                                                                                                                        
 itemDataSource: this._cartLinesObservable,                                                                                                                                                                                                                                                  
 columns:[                                                                                                                                                                                                                                                                                  
 {                                                                                                                                                                                                                                                                                                
 title: context.resources.getString("string_0"), // ID                                                                                              
 ratio: 20,                                                                                                                                          
 collapseOrder: 2,                                                                                                                                   
 minWidth: 50,                                                                                                                                       
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                    
 return ObjectExtensions.isNullOrUndefined(cartLine.ItemId) ? StringExtensions.EMPTY : cartLine.ItemId;                                              
 }                                                                                                                                                   
 },                                                                                                                                                  
 {                                                                                                                                                   
                                                                                                                                                     
 title: context.resources.getString("string_1"), // Name                                                                                            
 ratio: 50,                                                                                                                                          
 collapseOrder: 4,                                                                                                                                   
 minWidth: 100,                                                                                                                                      
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                    
 return ObjectExtensions.isNullOrUndefined(cartLine.Description) ? StringExtensions.EMPTY : cartLine.Description;                                    
 }                                                                                                                                                   
 },                                                                                                                                                  
                                                                                                                                                     
 {                                                                                                                                                   
                                                                                                                                                     
 title: context.resources.getString("string_2"), // Quantity                                                                                        
 ratio: 10,                                                                                                                                          
 collapseOrder: 3,                                                                                                                                   
 minWidth: 50,                                                                                                                                       
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                    
 return ObjectExtensions.isNullOrUndefined(cartLine.Quantity) ? StringExtensions.EMPTY : cartLine.Quantity.toString();                               
 }                                                                                                                                                   
 },                                                                                                                                                  
                                                                                                                                                     
 {                                                                                                                                                   
 title: context.resources.getString("string_3"), // Discount                                                                                                                                                                                                                                  
 ratio: 10,                                                                                                                                                                                                                                                                               
 collapseOrder: 1,                                                                                                                                                                                                                                                                        
 minWidth: 50,                                                                                                                                       
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                                           
 return ObjectExtensions.isNullOrUndefined(cartLine.DiscountAmount) ? StringExtensions.EMPTY : cartLine.DiscountAmount.toString();                                                                                                                                                    
 }                                                                                                                                                   
 },                                                                                                                                                  
                                                                                                                                                     
 {                                                                                                                                                   
                                                                                                                                                     
 title: context.resources.getString("string_4"), // Cost                                                                                            
 ratio: 10,                                                                                                                                          
 collapseOrder: 5,                                                                                                                                                                                                                                                                         
 minWidth: 50,                                                                                                                                                                                                                                                                                   
 computeValue: (cartLine: ProxyEntities.CartLine): string => {                                                                                                                                                                                                                          
 return ObjectExtensions.isNullOrUndefined(cartLine.TotalAmount) ? StringExtensions.EMPTY : cartLine.TotalAmount.toString();                                                                                                                                                                   
 }                                                                                                                                                                                                                                                                                              
 }                                                                                                                                                                                                                                                                                                 
]                                                                                                                                                                                                                                                                                           
 };                                                                                                                                                  
                                                                                                                                                     
 this.cartLinesDataList = new DataList(cartLinesDataListOptions);                                                                                    
                                                                                                                                                     
 // Logs the completion of constructing the DualDisplayCustomControl.                                                                                                                                                                                                                            
 this.context.logger.logInformational("DualDisplayCustomControl constructed", this.context.logger.getNewCorrelationId());                                                                                                                                                                      
 }                                                                                                                                                   
                                                                                                                                                     
 /**                                                                                                                                               
                                                                                                                                                     
* Binds the control to the specified element.                                                                                                                                                                                                                                                  
* @param {HTMLElement} element The element to which the control should be bound.                                                                                                                                                                                                                    
*/                                                                                                                                                                                                                                                                                                 
 public onReady(element: HTMLElement): void {                                                                                                                                                                                                                                                  
 ko.applyBindingsToNode(element, {                                                                                                                                                                                                                                                                
 template: {                                                                                                                                                                                                                                                                                     
 name: DualDisplayCustomControl.TEMPLATE_ID,                                                                                                                                                                                                                                                      
 data: this                                                                                                                                                                                                                                                                                         
 }                                                                                                                                                                                                                                                                                                  
 });                                                                                                                                                                                                                                                                                              
 }                                                                                                                                                                                                                                                                                                 
 /**                                                                                                                                                                                                                                                                                          
 * Initializes the control.                                                                                                                                                                                                                                                                    
 * @param {IDualDisplayCustomControlState} state The initial state of the page used to initialize the control.                                                                                                                                                                                 
 */                                                                                                                                                                                                                                                                                  
 public init(state: IDualDisplayCustomControlState): void {                                                                         
 this._cart(state.cart);                                                                                                                
 this._customer(state.customer);                                                                                          
 this._loggedOn(state.loggedOn);                                                                                                        
 this._employee(state.employee)                                                                                                                   
 }                                                                                                                                           
 }                                                                                                                                        ``` 

17.  Create a new json file and under the DualDisplayExtension folder and name it as manifest.json.

18.  In the manifest.json file, copy and paste the below code, delete the default generated code before copying the below code:
```typescript
{                                                          
                                                             
 "$schema": "../manifestSchema.json",                                                                                  
 "name": "Pos_Extensibility_DualDisplaySample",                                                                     
 "publisher": "Microsoft",                                                                                             
 "version": "7.2.0",                                         
 "minimumPosVersion": "7.2.0.0",                                                                                    
 "components": {                                                                                                     
 "resources": {                                              
  "supportedUICultures": [ "en-US" ],                                                                               
 "fallbackUICulture": "en-US",                                                                                       
 "culturesDirectoryPath": "Resources/Strings",                                                                       
 "stringResourcesFileName": "resources.resjson"              
                                                             
 },                                                          
                                                             
 "dualDisplay": {                                                                                                  
 "customControl": {                                                                                                
 "controlName": "DualDisplayCustomControl",                                                                       
 "htmlPath": "CustomControl/DualDisplayCustomControl.html",                                                       
 "modulePath": "CustomControl/DualDisplayCustomControl"                                                               
 }                                                                                                                   
 }                                                                                                                   
 }                                                                                                                    
 }
```
19.  Open the extensions.json file under POS.Extensions project and update it with DualDisplayExtension samples, so that POS during runtime will include this extension.
```typescript
 {
 "extensionPackages": [
 {
 "baseUrl": "SampleExtensions"
 },
 {
 "baseUrl": " SampleExtensions2"
 },
{
"baseUrl": " DualDisplayExtension"
 }
 ]
}
```
20. Open the tsconfig.json to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list, if you want to include any extension part of the POS then you need add the extension folder name and comment the extension from the extension list like below.
```typescript
 "exclude": [
 "AuditEventExtensionSample",
"B2BSample",
"CustomerSearchWithAttributesSample",
 "FiscalRegisterSample",
 "PaymentSample",
 "PromotionsSample",
 "SalesTransactionSignatureSample",
 //"SampleExtensions2",
 "SampleExtensions",
 "StoreHoursSample",
 "SuspendTransactionReceiptSample"
 //"SampleExtensions",
 //"DualDisplayExtension"
],
```
21. Compile and rebuild the project.

## Validate the customization

1.  Login to MPOS using 000160 as operator id and 123 as password.

2.  Click the current transaction button on the welcome screen.

3.  Add any item (0005) to transaction.

4.  Add any customer to transaction ("Karen Berg").

5.  The dual display should display the cart, total, employee and customer details.
