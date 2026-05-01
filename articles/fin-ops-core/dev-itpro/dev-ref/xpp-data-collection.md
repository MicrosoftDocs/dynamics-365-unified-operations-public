---
title: X++ collection classes
description: Learn about collection classes in X++, which are used to store objects to let you create arrays, lists, sets, maps, and structures.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ collection classes

[!include [banner](../includes/banner.md)]

The X++ language syntax provides two composite types: arrays and containers. These composite types are useful for aggregating values of primitive types. However, you can't store class objects in arrays or containers. 

Use *collection classes* to store objects. They let you create arrays, lists, sets, maps, and structs that can hold any data type, even objects. For maximum performance, C++ implements these classes (they're system classes). Collection classes were previously known as *foundation classes*. The collection classes are **Array**, **List**, **Map**, **Set**, and **Struct**.

- [Array](/dotnet/api/microsoft.dynamics.ax.xpp.array) – This class resembles the **array** type in the X++ language, but it can hold values of any single type, even objects and records. You access objects in a specific order.
- [List](/dotnet/api/microsoft.dynamics.ax.xpp.list) – This class contains elements that you access sequentially. Unlike an array, the **List** class provides an **addStart** method. Like the **Set** class, the **List** class provides the **getEnumerator** and **getIterator** methods. You can use an iterator to insert and delete items from a **List** object.
- [Map](/dotnet/api/microsoft.dynamics.ax.xpp.map) – This class associates a key value with another value.
- [Set](/dotnet/api/microsoft.dynamics.ax.xpp.set) – This class holds values of any single type. Values aren't stored in the sequence in which you add them. Instead, the **Set** object stores the value in a manner that optimizes performance for the **in** method. A **Set** object ignores any attempt to add a value that the **Set** object is already storing. Unlike the **Array** class, the **Set** class provides the **in** and **remove** methods.
- [Struct](/dotnet/api/microsoft.dynamics.ax.xpp.struct) – This class can contain values of more than one type. It's used to group information about a specific entity.

The constructor for every collection class except **Struct** takes a type parameter that is an element of the **Types** system enum. The collection instance can store items of that type only. The **Types::AnyType** enum element is a special case that you can't use to construct a collection object, such as a **Set** object. The **null** value can't be stored as an element in a **Set** object. Additionally, **null** can't be a key in a **Map** object. You can iterate through a collection object by using an iterator or enumerator. Here are typical examples that show how you can obtain an iterator.

```xpp
new MapIterator(myMap)
myMap.getEnumerator()
```

For **Set** objects, if you add or remove any elements after an iterator is created, the iterator instance can no longer be used to read from or step through the collection. 

For **Map** objects, as for **Set** objects, if you remove any elements, the iterator is no longer valid. However, a **MapIterator** object remains valid even after a call to the **Map.insert** method, regardless of whether the key is new, or whether the key already exists and only the value is being updated in the **Map** element. Code that calls **Map.insert** and depends on the iterator object remaining valid might fail if it's run as .NET Framework CIL. 

Use the collection classes to form more complex classes. For example, you can easily implement a stack by using a list where you always add elements to the beginning of the list. The newest element then occupies the top of the stack. 

You can also extend the collection classes. For example, you can extend the **List** class to create a list of customer records where the operations are type-safe. In this case, the derived collection class accepts only customer records.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
