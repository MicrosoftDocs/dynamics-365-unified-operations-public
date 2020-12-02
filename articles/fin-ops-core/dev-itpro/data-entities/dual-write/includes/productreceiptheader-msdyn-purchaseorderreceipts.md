---
author: robinarh
ms.service: dynamics-ax-applications
ms.topic: include
ms.date: 11/17/2020
ms.author: rhaertle
---

### Product receipt header to msdyn_purchaseorderreceipts

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
RECORDID | >> | `msdyn_recordid` | 
PRODUCTRECEIPTDATE | >> | `msdyn_datereceived` | 
DELIVERYADDRESSLATITUDE | >> | `msdyn_deliveryaddresslatitude` | 
DELIVERYADDRESSLONGITUDE | >> | `msdyn_deliveryaddresslongitude` | 
PURCHASEORDERNUMBER | >> | `msdyn_purchaseorder.msdyn_name` | 
DELIVERYMODEID | >> | `msdyn_shipvia.msdyn_name` | 
DELIVERYTERMSID | >> | `msdyn_deliveryterm.msdyn_termscode` | 
ORDERVENDORACCOUNTNUMBER | >> | `msdyn_ordervendor.msdyn_vendoraccountnumber` | 
REQUESTERPERSONNELNUMBER | >> | `msdyn_requesterpersonnel.cdm_workernumber` | 
ISDELIVERYADDRESSPRIVATE | >> | `msdyn_isdeliveryaddressprivate` | 
DELIVERYADDRESSCOUNTRYREGIONID | >> | `msdyn_deliveryaddresscountryregionid` | 
DELIVERYADDRESSCOUNTYID | >> | `msdyn_deliveryaddresscountyid` | 
DELIVERYADDRESSSTATEID | >> | `msdyn_deliveryaddressstateid` | 
DELIVERYADDRESSZIPCODE | >> | `msdyn_deliveryaddresszipcode` | 
DELIVERYADDRESSNAME | >> | `msdyn_deliveryaddressname` | 
DELIVERYADDRESSTIMEZONE | >> | `msdyn_deliveryaddresstimezone` | 
DELIVERYADDRESSPOSTBOX | >> | `msdyn_deliveryaddresspostbox` | 
DELIVERYADDRESSSTREETNUMBER | >> | `msdyn_deliveryaddressstreetnumber` | 
DELIVERYADDRESSSTREET | >> | `msdyn_deliveryaddressstreet` | 
PRODUCTRECEIPTNUMBER | >> | `msdyn_name` | 
ATTENTIONINFORMATION | >> | `msdyn_note` | 
DELIVERYCITYINKANA | >> | `msdyn_deliverycityinkana` | 
DELIVERYSTREETINKANA | >> | `msdyn_deliverystreetinkana` | 
FORMATTEDDELIVERYADDRESS | >> | `msdyn_formatteddeliveryaddress` | 
DELIVERYADDRESSLOCATIONID | >> | `msdyn_deliveryaddresslocationid` | 
DELIVERYADDRESSCITY | >> | `msdyn_deliveryaddresscity` | 
DELIVERYADDRESSDESCRIPTION | >> | `msdyn_deliveryaddressdescription` | 
DELIVERYADDRESSDISTRICTNAME | >> | `msdyn_deliveryaddressdistrictname` | 
DELIVERYBUILDINGCOMPLIMENT | >> | `msdyn_deliverybuildingcompliment` | 
DELIVERYADDRESSDUNSNUMBER | >> | `msdyn_deliveryaddressdunsnumber` | 
