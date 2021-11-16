---
title: View Party Data
description: This topic explains how to view party data using party form. 
author: RamaKrishnamoorthy 
ms.date: 11/16/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2021-11-16
---

# View Party Data

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Similar to accounts and contacts, party data can be accessed through a user interface. Dual-write party and global address book solution version 3.2.0.70 provides “Party” form to access party data. Party form provides the capability to view and manage party records along with all its associated customers, contacts and vendors and their postal addresses and electronic addresses as explained below.
Using party form, you can create a new party of type “Person” and “Organization”. 

          <image1>  
  
Once a party is created, you can use the customers tab to create one or more customers from this party for different companies and manage it. When the party type is “Organization”, you can create and manage accounts (Customer of type Organization). When the party type is “Person”, you can create and manage contacts (Customer of type Person). Similarly, the Vendors tab is used to create vendors of type Person and Organization.

          <image2>
    
Postal addresses tab allows you to create and manage 1 or more postal addresses for the party record. You can create as many postal addresses as necessary. These addresses appear on the quotation and sales order forms. 

          <image 3>
      
Similarly Electronic addresses tab allows you to create and manage 1 or more electronic addresses for the party record. You can create as many electronic addresses as necessary.
      
          <image 4>
        
You can create contact persons (Contact for party records)  and associate to the party by navigating to the Associated Contacts tab.
        
          <image 5>
          
You can add the “Party” form to your application using site maps.
1.	Navigate to “Model-driven Apps” node in your custom solution. Click ‘Add Existing’ and select the app of your choice you intend to customize and include the Party entity or any other entities created as part of dual write solutions. In this example we will update the Sales Team member app to include Party entity.
          <image 6>
            
2.	Open the app and click Entities on the Components section to include the Party 
         <image 7>
         <image 8>
                
     Click Save after selecting the msdyn_party entity.

3.	Edit the Site map of the app by clicking Edit.
         <image 9>
                   
4.	Add a new Subarea onto the section we need to customize by selecting and dragging ‘Subarea’ from the Components section.
        <image 10>
                     
    Click Edit and select ‘Entity’ as Type and’Party’ as the entity in the components section.
        <image 11>
                         
5. Click Save and Publish so that the Party entity  is available on the app.                     
        <image 12>
    
