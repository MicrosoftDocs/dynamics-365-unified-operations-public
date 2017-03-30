# Use the EventHandlerResult class in request/response scenarios

Delegate methods and delegate handler methods can be declared to support a request/response scenario, where the delegate calling logic requests the subscribers to provide a response. To support this scenario the **EventHandlerResult** class is most often passed as a parameter, and the delegate handler methods provide their result using one of the result methods on the class. However, the **EventHandlerResult** class can only contain a single result, so if multiple subscribers provide their individual result, the last respondent wins, and the results from the previous subscribers are overwritten.

Before the functionality described in this topic was introduced (platform update 5), there was no mechanism to ensure that, at most, a single subscriber provided a result, and that no results were lost if there were multiple subscribers.

## Ensuring, at most, one response

In platform update 5, the **EventHandlerResult** class has an additional static constructor which ensures that the logic fails if more than one subscriber provides a result. The new constructor is named **newSingleResponse**. When instantiating an **EventHandlerResult** object using this method, the framework will throw an exception as soon as a second delegate handler method attempts to provide a result.

    EventHandlerResult result = EventHandlerResult::newSingleResponse();
    this.validateWarehouseTypeDelegate(this.WarehouseType, result);

## IEventHandlerResultValidator interface

The validation in the **EventHandlerResult** class is handled by injecting an object of a type that implements the **IEventHandlerResultValidator** interface. When instantiating the **EventHandlerResult** object using the **newSingleResponse** static constructor, an **EventHandlerSingleResponseValidator** object is instantiated and injected into the **EventHandlerResult** object, and the injected object becomes responsible for validating any result provided to the **EventhandlerResult** object. Other validation classes can be implemented by having the class implement the **IEventHandlerResultValidator **interface, and injecting it into the **EventHandlerResult** class by instantiating the **EventHandlerResult** object using another new static constructor named **newWithResultValidator**. The constructor takes an argument of type **IEventHandlerResultValidator**, which makes it possible to inject any validator object as long as it implements the **IEventHandlerResultValidator **interface**.**

For example, the <strong>newSingleResponse</strong> static constructor simply delegates the instantiation to the **newWithResultValidator** static constructor like this.

    return EventHandlerResult::newWithResultValidator(EventHandlerSingleResponseValidator::construct());
    
# Accept and reject request/response scenarios

In certain request/response scenarios, the subscriber is only expected to provide their acceptance or rejection. Using the **EventHandlerResult** class to request acceptance/rejection can be confusing, if the subscriber is only expected to respond with a Boolean value. In a validation scenario, for example, should the subscriber only respond with Boolean false, when validation fails, or should the subscriber also respond with Boolean true, if validation succeeds? If the response is gathered using an **EventHandlerResult** object, then the second subscriber that validates and replies with Boolean true, might overwrite the Boolean false from the first subscriber.

To mitigate this confusion, two new result type classes have been introduced in platform update 5: **EventHandlerAcceptResult** and **EventHandlerRejectResult**.

When using the **EventHandlerAcceptResult** class, the delegate handler method can only respond by calling the **accept** method. When using the **EventHandlerRejectResult** class, only the **reject** method can be called.

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

The two new classes also contain a **newSingleResponse** static constructor for use in scenarios where, at most, one subscriber is allowed to respond with their rejection or acceptance. Whether any subscriber has responded can still be answered by querying the <strong>hasResult</strong> method, and the acceptance/rejection is queried by calling either the **isAccepted** or **isRejected** methods for the **EventHandlerAcceptResult **and** EventHandlerRejectResult **classes, respectively.

    boolean ret = false;
    EventHandlerAcceptResult result = EventHandlerAcceptResult::newSingleResponse(); 
    this.validateWarehouseTypeDelegate(this.WarehouseType, result);
    if (result.hasResult())
    {
        ret = result.isAccepted();
    }
