---
# required metadata

title: How to add a custom field on the POS totals panel
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: mugunthanm
manager: AnnBe
ms.date: 04/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: retail
ms.author: mumani
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# How to add a custom field on the POS totals panel

[!include[banner](../includes/banner.md)]

This topic explains how to add new custom field to totals panel in POS transaction page using the screen layout designer. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail 7.3 and higher versions.

You can add custom fields to the totals panel in POS transaction page using screen layout designer, the custom fields added in the custom field form for totals panel will show up in the designer and you can choose which one to show on left or right columns, the logic for the custom field should be coded in the POS extensions.

Scenario/business problem
-------------------------

<span id="_Toc446093285" class="anchor"></span>Let’s add custom field to totals panel in POS transaction page using the screen layout designer and code the business logic in POS Extensions.

Steps required:
---------------

**HQ:**

1.  Add the language text for the custom field in the language text form.

2.  In the custom field form, add the new custom field.

3.  Open the screen layout designer, under the totals panel add this new custom field.

4.  Run the Job.

**POS Extension:**

1.  In the POS extension project add the business logic for the custom field.

**Configure HQ:**

1.  Login to Dynamics 365 for Retail.

2.  Navigate to Retail > Channel setup > POS setup > POS profiles > Language text

3.  Select the POS tab and add new POS language text by clicking the **Add** button.

    Ex:

| Language ID | Text ID | Text   |
|-------------|---------|--------|
| en-US       | 1       | Sample |
| en-UK       | 1       | Demo   |

The text shown in the totals panel is localizable, so you can create multiple text for the same text ID in different languages.

1.  Click the Save button in the action bar to Save the changes.

2.  Navigate to Retail > Channel setup > POS setup > POS profiles > Custom fields

3.  Click the New button in the Action bar to add the new custom field.

    Ex:

| Name   | Type        | Caption text ID |
|--------|-------------|-----------------|
| Sample | Totals area | 1               |

In the Name field enter the name of the custom field, in the type field you must Select “***Totals area***” and in the Caption text ID field give the Text ID you used in the step 2.

1.  Click the Save button in the action bar to Save the changes.

2.  Navigate to Retail > Channel setup > POS setup > POS > Screen layouts text

3.  Select the F3MGR screen layout ID and click the Designer button in the action bar (You can choose any existing layout or create a new one). You will find the layout ID F3MGR only if you are using demo data.

4.  Select the 1440x960 – Full layout from the layout sizes and click the Layout designer button.

5.  If prompted click Open and follow the instruction to install the designer tool.

6.  After installing it will ask for AAD credentials, provide the details to launch the designer.

7.  From the designer drag totals panel to the designer page, if it’s already exists in the page then the totals panel control on the left tab will be disabled.

8.  Right click on the totals panel in the transaction page and click customize.

9.  You should see the custom field “**SAMPLE**” in the available field list.

10. Move it to the left or right column by clicking the arrow buttons.

11. You can move the custom field up or down using the **Up** and **Down** buttons.

12. Click OK to Save the changes and close the Customization- Totals panel form.

13. Click the X button in the designer to close the designer.

14. When prompted to Save changes, click Yes. If you click No the changes will not be saved.

15. Navigate to Retail > Retail IT > Distribution schedule

16. Select the Registers (1090) job and click Run now.

 **Add business logic to custom field:**

 You can find the similar sample code in Retail SDK (…\RetailSDK\POS\Extensions\SampleExtensions\ViewExtensions\Cart\TipsCustomField.ts)

1.  Open visual studio 2015 in administrator mode.

2.  Open ModernPOS solution from …\RetailSDK\POS

3.  Under the POS.Extensions project create a new folder called CustomFieldExtensions.

4.  Under CustomControlExtensions, create new folder called Cart.

5.  In the Cart folder, add a new ts (typescript) and name it has SampleCustomField.ts

6.  Add the below import statement to import the relevant entities and context.

```typescript
    import { CartViewTotalsPanelCustomFieldBase } from "PosApi/Extend/Views/CartView";
    import { ProxyEntities } from "PosApi/Entities";
```
7.  Create a new class called SampleCustomField and extend it from CartViewTotalsPanelCustomFieldBase. We are extending from CartViewTotalsPanelCustomFieldBase to get the computeValue method form the base class to do any custom logic for the custom field.
```typescript
    export default class SampleCustomField extends CartViewTotalsPanelCustomFieldBase {

    }
```
8.  Inside the class lets implement the abstract computeValue method to set logic for our custom field.
```typescript
public computeValue(cart: ProxyEntities.Cart): string {

// Let’s show 10% of total amount in the custom field.

if (isNaN(cart.TotalAmount) || cart.TotalAmount <= 0) {
return "$0.00";
}
return "$" + (cart.TotalAmount \* 0.1).toFixed(2).toString();
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

 * NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU  TO DO SO.
*/

 import { CartViewTotalsPanelCustomFieldBase } from "PosApi/Extend/Views/CartView";
 import { ProxyEntities } from "PosApi/Entities";

 export default class SampleCustomField extends CartViewTotalsPanelCustomFieldBase {
 public computeValue(cart: ProxyEntities.Cart): string {

// Let’s show 10% of total amount in the custom field.
 if (isNaN(cart.TotalAmount) || cart.TotalAmount <= 0) {
 return "$0.00";
 }
 return "$" + (cart.TotalAmount * 0.1).toFixed(2).toString();
 }
}
```
1.  Create a new json file under the CustomFieldExtensions folder and name it as manifest.json.

2.  In the manifest.json file, copy and paste the below code:
```typescript
 {
 "$schema": "../manifestSchema.json",
 "name": "Pos_Extensibility_Samples",
 "publisher": "Contoso",
 "version": "7.3.0",
 "minimumPosVersion": "7.3.0.0",
 "components": {
 "extend": {
 "views": {
    "CartView": {
    "totalsPanel": {
    "customFields": [
{
        "fieldName": "Sample",
        "modulePath": "Cart/SampleCustomField"
}
]
 } }
 }  }
} }
```
 **Note:** The fieldname in the manifest under the customField section should match the Name you used in the custom field form. If you add multiple custom field, you should add multiple implementation file and update the info under custom field section in the manifest. Implementation file name is the name of the file you created in step 27.

 **Ex:** If you add two custom field say Sample1 and Sample2, then you should have two implementation files extending from the same base class CartViewTotalsPanelCustomFieldBase.

 Manifest should like something like below:
```typescript
 "customFields": [
{
    "fieldName": "Sample1",
    "modulePath": "Cart/SampleCustomField1"
},
{
    "fieldName": "Sample2",
    "modulePath": "Cart/SampleCustomField2"
}
 ]
```
 SampleCustomField1 and SampleCustomField1 is the name of the typescript file where you will do the business logic.

1.  Open the extensions.json file under POS.Extensions project and update it with CustomFieldExtensions samples, so that POS during runtime will load this extension.
```typescript
 {
 "extensionPackages": [
 { 
     "baseUrl": "SampleExtensions2" 
 }, 
 {
     "baseUrl": "CustomFieldExtensions"
 }
 ]
}
```
1.  Open the tsconfig.json to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list, if you want to include any extension part of the POS then you need add the extension folder name and comment the extension from the extension list like below.
```typescript

"exclude": [
"SampleExtensions",
//"SampleExtensions2",
//"CustomFieldExtensions"
],
```
1.  Compile and rebuild the project.

2.  Deploy the customized MPOS by clicking the Local Machine button and make sure the solution platform is x86 orr you can create Retail deployable package and install it the MPOS from it.

    For the document we used Modern POS but you can use either cloud POS or Modern POS.

 **Validate the customization:**

1.  Login to MPOS using 000160 as operator id and 123 as password.

2.  Click the current transaction button on the welcome screen

3.  Add any item (0005) to transaction.

4.  The custom field should be displayed in the totals panel.
