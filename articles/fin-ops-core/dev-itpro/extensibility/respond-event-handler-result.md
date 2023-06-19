---
title: Respond by using EventHandlerResult
description: This article describes how to subscribe to events that has a parameter of any type that implements the IEventHandlerResult interface.
author: MichaelFruergaardPontoppidan
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: mfp
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
ms.assetid: 
---

# Respond by using EventHandlerResult

[!include [banner](../includes/banner.md)]

Some delegate methods are implemented so that they can request a response from subscribing delegate handler methods. The delegate calling logic then uses the response from a potential subscriber when it continues execution after the response has been received. These delegate methods usually have a signature that has an **EventHandlerResult** parameter as the last parameter. However, because of the support for the **EventHandlerAcceptResult** and **EventHandlerRejectResult** types, the parameter can be of any type that implements the **IEventHandlerResult** interface.

+ In general, the logic that is implemented in the delegate handler method should contain a condition that verifies that the subscribing logic is responsible for providing a response. It should also include logic to provide the response in the form of a result.
+ When the delegate handler method must provide the response to an **EventHandlerResult** object parameter, the subscribing logic might also contain logic to calculate or retrieve the result.
+ When the condition and the response logic are implemented, the calculation of the result must occur only when the condition is evaluated to **true**.
+ All the subscribing delegate handler methods are run when a delegate is called. Therefore, you should make sure that the overhead of running your method is as low as possible when the method isn't responsible for providing a response. Therefore, make sure that the condition is evaluated to **false** as quickly as possible when your delegate handler method isn't responsible for providing a result.

## Examples
The following example shows a delegate handler that has a condition in the form of a **switch** statement. The delegate handler also has logic to provide a response in the form of the result. The responding logic is run only when the condition is evaluated to **true**.

```xpp
[SubscribesTo(tableStr(InventWarehouseEntity), delegateStr(InventWarehouseEntity, validateWarehouseTypeDelegate))]
public static void validateWarehouseTypeIsSupportedStandardDelegateHandler(InventLocationType _inventLocationType, EventHandlerResult _result)
{
    switch (_inventLocationType)
    {
        case InventLocationType::Standard:
        case InventLocationType::Quarantine:
        case InventLocationType::Transit:
            _result.result(true);
            break;
    }
}
```

When the delegate method requests a response by using an **EventHandlerAcceptResult** or an **EventHandlerRejectResult** object parameter, the subscriber is expected to respond only with an accept or a reject. The subscribing logic might also add messages to the Infolog.

The following example resembles the previous example. However, the delegate method now requests a response by using an **EventHandlerAcceptResult** object and by calling the **accept** method.
	
```xpp
[SubscribesTo(tableStr(InventWarehouseEntity), delegateStr(InventWarehouseEntity, validateWarehouseTypeDelegate))]
public static void validateWarehouseTypeIsSupportedStandardDelegateHandler(InventLocationType _inventLocationType, EventHandlerAcceptResult _result)
{
    switch (_inventLocationType)
    {
        case InventLocationType::Standard:
        case InventLocationType::Quarantine:
        case InventLocationType::Transit:
            _result.accept();
            break;
    }
}
```

The following example shows a delegate handler method that responds by using an **EventHandlerRejectResult** object. To respond by using an **EventHandlerRejectResult** object, you can call the **reject** method or the **checkFailed** extension method. If you use the **checkFailed** method, you can add a warning message to the Infolog. Internally, the **checkFailed** method calls the **reject** method.

```xpp
[SubscribesTo(classStr(ProdTableType), delegateStr(ProdTableType, validateWriteProdTableInventRefTypeDelegate))]
public static void validateWriteProdTableInventRefTypeDelegateHandler(ProdTable _prodTable, EventHandlerRejectResult _result)
{
    if (_prodTable.InventRefType == InventRefType::ProdLine)
    {
        if (! _prodTable.InventRefId || !_prodTable.InventRefTransId)
        {
            _result.checkFailed("@SYS19558");
        }
        ProdBOM prodBOM;
        select prodBOM
            where prodBOM.InventTransId  == _prodTable.InventRefTransId;
        if (! _prodTable.checkRefProdBOM(prodBOM))
        {
            _result.reject();
        }
    }
}
```

## Guidelines
In addition to the previously described practices, the following general guidelines apply:

- Respond only when the subscribing logic is responsible for responding. The delegate handler methods were implemented to provide a response when a specific condition is met. Therefore, the subscribing logic must provide a result when a specific condition is met. Before the subscribing logic responds, it should not evaluate whether the result object parameter already contains a result. For example, a delegate handler method should not contain logic that resembles the logic in the following example. This logic evaluates whether the **EventHandlerResult** object parameter already contains a result when the method is run.

    > [!WARNING]
    > This example is an example of code that you should **not** write.

    ```xpp
    [SubscribesTo(tableStr(InventWarehouseEntity), delegateStr(InventWarehouseEntity, validateWarehouseTypeDelegate))]
	public static void validateWarehouseTypeIsSupportedStandardDelegateHandler(InventLocationType _inventLocationType, EventHandlerResult _result)
	{
	    // this if statement is an example of the bad practice.
	    if (_result.hasResult())
	    {
	         return;
	    }
	    switch (_inventLocationType)
	    {
	        case InventLocationType::Standard:
	        case InventLocationType::Quarantine:
	        case InventLocationType::Transit:
	             _result.result(true);
	            break;
	    }
	}
    ```
    
- Don't provide a response on behalf of other subscribers. If the delegate handler method isn't responsible for providing a response, the method must not provide a response. If the method provides a response when the condition isn't met, it provides a response on behalf of other subscribers. The requesting logic must be responsible for handling situations where no subscribers have responded. The delegate handler method must not contain logic that resembles the logic in the following example. This logic which provides a result when the condition is evaluated to **false**.
    
    > [!WARNING]
    > This example is an example of code that you should **not** write.
    
    ```xpp
	[SubscribesTo(tableStr(InventWarehouseEntity), delegateStr(InventWarehouseEntity, validateWarehouseTypeDelegate))]
	public static void validateWarehouseTypeIsSupportedStandardDelegateHandler(InventLocationType _inventLocationType, EventHandlerResult _result)
	{
	    switch (_inventLocationType)
	    {
	        case InventLocationType::Standard:
	        case InventLocationType::Quarantine:
	        case InventLocationType::Transit:
	            _result.result(true);
	            break;
		    // this default block is an example of the bad practice
	        default:
	            _result.result(false);
	            break;
	    }
	}
    ```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
