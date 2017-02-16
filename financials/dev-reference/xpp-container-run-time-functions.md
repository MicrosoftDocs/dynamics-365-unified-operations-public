---
# required metadata

title: X++ container run-time functions
description: This wiki describes the container run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-04 22 - 11 - 54
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31301
ms.assetid: f52bec38-0791-485b-8fb4-02e6f547e494
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# X++ container run-time functions

This wiki describes the container run-time functions.

These functions manipulate the contents of containers.

## conDel
Removes the specified number of elements from a container.

### Syntax

    container conDel(container container, int start, int number)

### Parameters

| Parameter | Description                                                 |
|-----------|-------------------------------------------------------------|
| container | The container to remove elements from.                      |
| start     | The one-based position at which to start removing elements. |
| number    | The number of elements to delete.                           |

### Return value

A new container that doesn't include the removed elements.

### Example

    static void conDelExample(Args _args)
    {
            container c = ["Hello world", 1, 3.14];
            // Deletes the first two items from the container.
            c = conDel(c, 1, 2);
    }

## conFind
Locates the first occurrence of an element or a sequence of elements in a container.

### Syntax

    int conFind (container container, anytype element,... )

### Parameters

| Parameter | Description                                              |
|-----------|----------------------------------------------------------|
| container | The container to search.                                 |
| element   | One or more elements to search for, separated by commas. |

### Remarks

If several elements are specified in the sequence, they must be separated by commas and specified in the correct sequence. The elements can be of any data type.

### Return value

**0** if the item was not found; otherwise, the sequence number of the item.

### Example

    static void conFindExample(Args _args)
    {
            container c = ["item1", "item2", "item3"];
            int i;
            int j;
            i = conFind(c, "item2");
            j = conFind(c, "item4");
            print "Position of 'item2' in container is " + int2Str(i);
            print "Position of 'item4' in container is " + int2Str(j);
    }

## conIns
Inserts one or more elements into a container.

### Syntax

    container conIns (container container, int start, anytype element, ... )

### Parameters

| Parameter | Description                                          |
|-----------|------------------------------------------------------|
| container | The container to insert elements into.               |
| start     | The position to insert elements at.                  |
| element   | One or more elements to insert, separated by commas. |

### Return value

A new container that contains the inserted elements.

### Remarks

The first element of the container is specified by the number **1**. To insert after the n element, the *start* parameter should be n+1. You can also use the **+=** operator to add values of any type to a container. For example, to create a container that contains the squared values of the first 10 loop iterations, use the following code.

    int i;
    container c;

    for (i = 1; i < = 10; i++)
    {
            c += i*i;
    }

### Example

    static void conInsExample(Args _arg)
    {
            container c;
            int i;

            c = conIns(c,1,"item1");
            c = conIns(c,2,"item2");
            for (i = 1 ; i <= conLen(c) ; i++)
            {
                    // Prints the content of a container.
                    print conPeek(c, i);
            }
    }

## conLen
Retrieves the number of elements in a container.

### Syntax

    int conLen(container container)

### Parameters

| Parameter | Description                                       |
|-----------|---------------------------------------------------|
| container | The container to count the number of elements in. |

### Return value

The number of elements in the container.

### Example

    static void conLenExample(Args _arg)
    {
            container c;
            int i;

            c = conins(["item1", "item2"], 1);
            for (i = 1 ; i <= conLen(c) ; i++)
            {
                    print conPeek(c, i);
            }
    }

## conNull
Retrieves an empty container.

    container conNull()

### Remarks

Use this function to explicitly dispose of the contents of a container.

### Return value

An empty container.

### Example

    static void conNullExample(Args _arg)
    {
            container c = ["item1", "item2", "item3"];

            print "Size of container is " + int2str(conLen(c));
            // Set the container to null.
            c = conNull();
            print "Size of container after conNull() is " + int2Str(conLen(c));
    }

## conPeek
Retrieves a specific element from a container and converts it into another data type, if conversion is required.

### Syntax

    anytype conPeek(container container, int number)

### Parameters

| Parameter | Description                                                                                                                                                                                                                      |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| container | The container to return an element from.                                                                                                                                                                                         |
| number    | The position of the element to return. Specify **1** to get the first element. An invalid position number, such as **-3**, **0**, or a number that is higher than the length of the container, might cause unpredictable errors. |

### Return value

The element in the container at the position that is specified by the *number* parameter. The **conPeek** function automatically converts the peeked item into the expected return type. Strings can automatically be converted into integers and real numbers, and integers and real numbers can be converted into strings.

### Example

    static void main(Args _args)
    {
            container cnI, cnJ;
            int i, j;
            anytype aty;
            info("container cnI ...");
            cnI = ["itemBlue", "itemYellow"];
            for (i=1; i <= conLen(cnI); i++)
            {
                    aty = conPeek(cnI, i);
                    info(int2str(i) + " :  " + aty);
            }

            info("container cnJ ...");
            cnJ = conIns(cnI, 2, "ItemInserted");
            for (j=1; j <= conLen(cnJ); j++)
            {
                    aty = conPeek(cnJ, j);
                    info(int2str(j) + " :  " + aty);
            }
    }
    /***  Output pasted from InfoLog ...
    Message (10:20:03 am)
    container cnI ...
    1 :  itemBlue
    2 :  itemYellow
    container cnJ ...
    1 :  itemBlue
    2 :  ItemInserted
    3 :  itemYellow
    ***/

## conPoke
Modifies a container by replacing one or more of the existing elements.

### Syntax

    container conPoke(container container, int start, anytype element, ...)

### Parameters

| Parameter | Description                                           |
|-----------|-------------------------------------------------------|
| container | The container to modify.                              |
| start     | The position of the first element to replace.         |
| element   | One or more elements to replace, separated by commas. |

### Return value

A new container that includes the new elements.

### Remarks

The first element of the container is specified by the number **1**.

### Example

    static void conPokeExample(Args _arg)
    {
            container c1 = ["item1", "item2", "item3"];
            container c2;
            int i;
            void conPrint(container c)
            {
                    for (i = 1 ; i <= conLen(c) ; i++)
                    {
                            print conPeek(c, i);
                    }
            }

            conPrint(c1);
            c2 = conPoke(c1, 2, "PokedItem");
            print "";
            conPrint(c2);
    }

