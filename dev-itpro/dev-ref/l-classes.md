---
# required metadata

title: L Classes
description: System API classes that start with the letter L.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 52291
ms.assetid: 60d8c71b-6df4-4776-9642-ed89ab5ad46a
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# L Classes

System API classes that start with the letter L.

Class Label
-----------

    class Label extends Object

The Label class manages label IDs and label files.

### Remarks

The SysLabel class extends the Label class.

### Examples

### Methods

| Method                                                                | Description                                                                                         |
|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| public LabelBulkEditor bulkEditor(str module)                         | Creates an instance of the LabelBulkEditor class.                                                   |
| public boolean createLabelFile(str module, str language)              | Creates a label file for a specified label ID.                                                      |
| public boolean delete(str label)                                      | Deletes a specified label.                                                                          |
| public boolean exists(str label)                                      | Indicates whether a specified label ID exists.                                                      |
| public str extractComment(str label)                                  | Returns a comment that is associated with a specified label ID.                                     |
| public str extractString(str label)                                   | Returns the text that is associated with a specified label ID.                                      |
| public str getFirstLabelFile()                                        | Returns the first label file ID record.                                                             |
| public Date getLabelFileCreatedDate(str labelFile, str language)      | Returns the date that a specified label file was created.                                           |
| public int getLabelFileCreatedTime(str labelFile, str language)       | Returns the time that a specified label file was created.                                           |
| public Date getLabelFileModificationDate(str labelFile, str language) | Returns the date that a specified label file was modified.                                          |
| public int getLabelFileModificationTime(str labelFile, str language)  | Returns the time that a specified label file was modified.                                          |
| public str getNextLabelFile()                                         | Returns the next label file ID record.                                                              |
| public str insert(str text, str comment, str module)                  | Creates a label ID for a specified text string.                                                     |
| public int labelId(str label)                                         | Returns the number that is included in a specified label ID.                                        |
| public int maxLabelId(str module)                                     | Returns the ID for the last label in the specified label file.                                      |
| public boolean modify(str label, str text, \[str comment\])           | Modifies the text and comment that are associated with a specified label.                           |
| public str moduleId(str label)                                        | Returns the label file ID for a specified label ID.                                                 |
| public boolean moreLabelFiles()                                       | Indicates whether there are additional label files.                                                 |
| public str name(str module, int labelId)                              | Returns a label ID, based on a specified label file ID and label ID number.                         |
| public str searchFirst(str searchString)                              | Returns the first label ID that is found for a specified search term.                               |
| public str searchNext()                                               | Returns the next label ID that is found for a search term that is passed to the searchFirst method. |
| ::public static boolean flush(str labelFileId, str language)          | Flushes the label file buffers to disk.                                                             |
| public void new(\[str language\])                                     | Creates a new instance of the Label class.                                                          |
| public void finalize()                                                | Closes the current label file.                                                                      |

### Method bulkEditor

Creates an instance of the LabelBulkEditor class.

    public LabelBulkEditor bulkEditor(str module)

#### Parameters

module  
A string data type that specifies a three-letter label file ID.

#### Return Value

An instance of the LabelBulkEditor class.

#### Remarks

The LabelBulkEditor class is used to quickly modify a label file. This method returns nullNothingnullptrunita null reference (Nothing in Visual Basic) when it is invoked from the client tier.

### Method createLabelFile

Creates a label file for a specified label ID.

    public boolean createLabelFile(str module, str language)

#### Parameters

module  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

#### Return Value

true if a file is created; otherwise, false.

#### Remarks

The label file is created after the file buffers are flushed to disk, which occurs when the server closes.

### Method delete

Deletes a specified label.

    public boolean delete(str label)

#### Parameters

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

#### Return Value

true if the label ID is deleted; otherwise, false.

### Method exists

Indicates whether a specified label ID exists.

    public boolean exists(str label)

#### Parameters

label  
The output of the literalStr function from a label ID string that includes the at sign (@).

#### Return Value

true if the label ID exists; otherwise, false.

#### Remarks

The format of the label parameter value must resemble literalStr("@SYS24359").

### Method extractComment

Returns a comment that is associated with a specified label ID.

    public str extractComment(str label)

#### Parameters

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

#### Return Value

A string value that indicates the comment that is associated with the specified label ID.

#### Remarks

If you specify a label ID that does not exist, this method returns the specified ID as a string. If you do not include the @ in the label parameter value, the method returns the label ID.

### Method extractString

Returns the text that is associated with a specified label ID.

    public str extractString(str label)

#### Parameters

label  
A string data type that specifies a label ID. The string must include the at sign (@) followed by a label file ID and a number.

#### Return Value

A string data type value that indicates the text that is associated with the specified label ID.

#### Remarks

If you specify a label ID that does not exist, the method returns the specified ID as a string. If you do not include the @ in the label parameter value, the method returns the label ID.

### Method getFirstLabelFile

Returns the first label file ID record.

    public str getFirstLabelFile()

#### Return Value

A string data type value that indicates the label file ID.

#### Remarks

A label file ID is a three-letter identifier for a label file.

### Method getLabelFileCreatedDate

Returns the date that a specified label file was created.

    public Date getLabelFileCreatedDate(str labelFile, str language)

#### Parameters

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

#### Return Value

A Date data type value that indicates when a label file is created.

#### Remarks

You can use the date2str function to convert the date to a text string.

### Method getLabelFileCreatedTime

Returns the time that a specified label file was created.

    public int getLabelFileCreatedTime(str labelFile, str language)

#### Parameters

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

#### Return Value

An integer data type value that indicates the time that a label file is created.

#### Remarks

For more information, see How to: Create a Label File. You can use the time2str function to convert the integer to a text string.

### Method getLabelFileModificationDate

Returns the date that a specified label file was modified.

    public Date getLabelFileModificationDate(str labelFile, str language)

#### Parameters

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

#### Return Value

A Date data type value that indicates when a label file was modified.

#### Remarks

You can use the date2str function to convert the date to a text string.

### Method getLabelFileModificationTime

Returns the time that a specified label file was modified.

    public int getLabelFileModificationTime(str labelFile, str language)

#### Parameters

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

#### Return Value

An integer value that indicates the time that a label file was modified.

#### Remarks

You can use the time2str function to convert the integer to a text string.

### Method getNextLabelFile

Returns the next label file ID record.

    public str getNextLabelFile()

#### Return Value

A string data type value that indicates the label file ID.

#### Remarks

A label file ID is a three-letter identifier for a label file.

### Method insert

Creates a label ID for a specified text string.

    public str insert(str text, str comment, str module)

#### Parameters

text  
A string data type that specifies a three-letter label file ID.

<!-- -->

comment  
A string data type that specifies a three-letter label file ID.

<!-- -->

module  
A string data type that specifies a three-letter label file ID.

#### Return Value

A string data type value for the label ID that is created.

#### Remarks

This operation allocates a new label ID across all languages.

### Method labelId

Returns the number that is included in a specified label ID.

    public int labelId(str label)

#### Parameters

label  
A string data type that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

#### Return Value

An integer data type value that indicates the number that is included in a label ID.

#### Remarks

You must call the searchFirst or searchNext method, and then pass the return value as a parameter to this method.

### Method maxLabelId

Returns the ID for the last label in the specified label file.

    public int maxLabelId(str module)

#### Parameters

module  
A string that specifies a three-letter label file ID.

#### Return Value

An integer that indicates the maximum label ID for the specified label file.

### Method modify

Modifies the text and comment that are associated with a specified label.

    public boolean modify(str label, str text, [str comment])

#### Parameters

label  
A string that specifies the comment that is associated with a label ID.

<!-- -->

text  
A string that specifies the comment that is associated with a label ID.

<!-- -->

comment  
A string that specifies the comment that is associated with a label ID.

#### Return Value

true if the label ID is modified; otherwise, false.

### Method moduleId

Returns the label file ID for a specified label ID.

    public str moduleId(str label)

#### Parameters

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

#### Return Value

A string that indicates the label file ID for a specified label ID.

#### Remarks

You need to call the searchFirst or searchNext method, and then pass the return value as a parameter to the labelId method.

### Method moreLabelFiles

Indicates whether there are additional label files.

    public boolean moreLabelFiles()

#### Return Value

true if there are additional label files; otherwise, false.

### Method name

Returns a label ID, based on a specified label file ID and label ID number.

    public str name(str module, int labelId)

#### Parameters

module  
An integer that specifies the numeric part of a label ID.

<!-- -->

labelId  
An integer that specifies the numeric part of a label ID.

#### Return Value

A string value that indicates the label ID.

### Method searchFirst

Returns the first label ID that is found for a specified search term.

    public str searchFirst(str searchString)

#### Parameters

searchString  
A string that specifies the search term.

#### Return Value

A string value that indicates the label ID.

### Method searchNext

Returns the next label ID that is found for a search term that is passed to the searchFirst method.

    public str searchNext()

#### Return Value

A string value that indicates the label ID.

#### Remarks

You must call the searchFirst method before you call this method. Otherwise, this method returns a random label ID.

### Method flush

Flushes the label file buffers to disk.

    public static boolean flush(str labelFileId, str language)

#### Parameters

labelFileId  
A string that specifies a language by using a language prefix.

<!-- -->

language  
A string that specifies a language by using a language prefix.

#### Return Value

### Method new

Creates a new instance of the Label class.

    public void new([str language])

#### Parameters

language  
A string that specifies a language by using a language prefix.

### Method finalize

Closes the current label file.

    public void finalize()

## Class LabelBulkEditor
    class LabelBulkEditor extends Object

The LabelBulkEditor class is used to quickly modify label files.

### Remarks

The LabelBulkEditor class is instantiated through the Label.bulkEditor() method. The label file is opened for modification when the instance of the class is created, and the label file is closed when the instance has garbage collected.

### Examples

### Methods

| Method                                                      | Description                                                                  |
|-------------------------------------------------------------|------------------------------------------------------------------------------|
| public boolean delete(str label)                            | Deletes a specified label.                                                   |
| public boolean modify(str label, str text, \[str comment\]) | Modifies the text and comment that are associated with a specified label ID. |
| public void new()                                           | Initializes an instance of the LabelBulkEditor class.                        |

### Method delete

Deletes a specified label.

    public boolean delete(str label)

#### Parameters

label  
A string that specifies the label ID. The string must include an at sign (@) followed by a label file ID and a number.

#### Return Value

true if the label is deleted; otherwise, false.

### Method modify

Modifies the text and comment that are associated with a specified label ID.

    public boolean modify(str label, str text, [str comment])

#### Parameters

label  
A string that specifies the comment that is associated with the label ID.

<!-- -->

text  
A string that specifies the comment that is associated with the label ID.

<!-- -->

comment  
A string that specifies the comment that is associated with the label ID.

#### Return Value

true if the label is modified; otherwise, false.

### Method new

Initializes an instance of the LabelBulkEditor class.

    public void new()

## Class LastAotSelection
    class LastAotSelection extends Object

### Remarks

### Examples

### Methods

| Method                           | Description                                               |
|----------------------------------|-----------------------------------------------------------|
| public TreeNode first()          |                                                           |
| public TreeNode next()           |                                                           |
| public ProjectNode projectRoot() |                                                           |
| public int selectionCount()      |                                                           |
| public void new()                | Initializes a new instance of the LastAotSelection class. |
| public void finalize()           |                                                           |

### Method first

    public TreeNode first()

#### Return Value

### Method next

    public TreeNode next()

#### Return Value

### Method projectRoot

    public ProjectNode projectRoot()

#### Return Value

### Method selectionCount

    public int selectionCount()

#### Return Value

### Method new

Initializes a new instance of the LastAotSelection class.

    public void new()

### Method finalize

    public void finalize()

## Class List
    class List extends Object

Contains any number of elements that are accessed sequentially. Lists are structures that can contain values of any X++ type. All the values in the list must be of the same type.

### Remarks

The type of the values in the list is specified when the list is created and cannot be changed afterwards. The implementation of lists makes traversal of the list elements very fast. Lists can be traversed by using the ListEnumerator class. To create a ListEnumerator object, use List.getEnumerator.

### Examples

The following example creates a list of integers and prints out a description of the list and the values that it contains.

    { 
        // Create a list of integers 
        List il = new List(Types::Integer); 
        // Add some elements to the list 
        il.addEnd(1); 
        il.addEnd(2); 
        il.addStart(3); 
        // Print a description of the list 
        print il.definitionString(); 
        print il.toString(); 
        pause; 
    }

### Methods

| Method                                                | Description                                                                           |
|-------------------------------------------------------|---------------------------------------------------------------------------------------|
| public AnyType addEnd(AnyType element)                | Adds a value to the end of the list.                                                  |
| public AnyType addStart(AnyType element)              | Adds a value to the start of the list.                                                |
| public str definitionString()                         | Returns a description of the type of the elements in the list.                        |
| public int elements()                                 | Specifies the number of elements in a list.                                           |
| public boolean empty()                                | Determines whether a list is empty.                                                   |
| public boolean equalTo(List l)                        | Determines whether a list is the same as the current list.                            |
| public ListEnumerator getEnumerator()                 | Creates an enumerator for a list which allows you to traverse the list.               |
| public container pack()                               | Serializes the current instance of the List class.                                    |
| public str toString()                                 | Returns a description of the values in the list.                                      |
| public Types typeId()                                 | Returns the type of the values in a list.                                             |
| public str xml(\[int indent\])                        | Returns an XML string that represents the current object.                             |
| ::public static List create(container container)      | Creates a list from the container obtained from a prior call to the List.pack method. |
| ::public static List createFromXML(Object xmlnode)    |                                                                                       |
| ::public static boolean equal(List list1, List list2) | Determines whether two lists are identical.                                           |
| ::public static List merge(List list1, List list2)    | Combines two lists to create a new list.                                              |
| public void appendList(List list)                     |                                                                                       |
| public void new(Types Type)                           | Creates a list.                                                                       |

### Method addEnd

Adds a value to the end of the list.

    public AnyType addEnd(AnyType element)

#### Parameters

element  
The value to add to the end of the list.

#### Return Value

The value that is added to the list.

### Method addStart

Adds a value to the start of the list.

    public AnyType addStart(AnyType element)

#### Parameters

element  
The value to add to the start of the list.

#### Return Value

The value added to the list.

#### Remarks

Elements can be added to the end of the list by using the List.addEnd method.

#### Examples

The following example creates a list of integers, adds the values 1 and 2 to the end of the list, and then adds the value 3 to the start of the list. The values that are returned by the List.toString method are {3, 1, 2}.

    { 
        // Create a list of integers 
        list il = new List(Types::Integer); 
        // Add some elements to the list 
        il.addEnd(1); 
        il.addEnd(2); 
        il.addStart(3); 
        // Print a description of the list. 
        print il.definitionString(); 
        print il.toString(); 
        pause; 
    }

### Method definitionString

Returns a description of the type of the elements in the list.

    public str definitionString()

#### Return Value

A string that contains a definition of the list.

#### Remarks

For example, this method could return "list of int". To print a list of the values within the list, use the List.toString method.

#### Examples

The following example creates a list of integers. The definitionString method is used to print a description of the list.

    { 
        // Create a list of integers 
        List il = new List(Types::Integer); 
        // Add some elements to the list 
        il.addEnd(1); 
        il.addEnd(2); 
        il.addStart(3); 
        // Print a description ofvthe list 
        print il.definitionString(); 
        print il.toString(); 
        pause; 
    }

### Method elements

Specifies the number of elements in a list.

    public int elements()

#### Return Value

The number of elements in the list.

#### Examples

The following example creates a list of integers and adds some elements to it. The elements method is used to test whether there are three elements in the list.

    { 
        List il = new List(Types::Integer); 
        il.addStart(1); 
        il.addStart(2); 
        il.addStart(3); 
        if (il.elements() != 3) 
        { 
            print "Something is wrong..."; 
        } 
    }

### Method empty

Determines whether a list is empty.

    public boolean empty()

#### Return Value

true if the list is empty; otherwise, false.

### Method equalTo

Determines whether a list is the same as the current list.

    public boolean equalTo(List l)

#### Parameters

l  
The list to be compared with the current list.

#### Return Value

true if the specified list is identical to the list on which the method is called; otherwise, false.

#### Remarks

A list is equal to another list if the two lists are the same type, contain the same number of elements, and the elements occur in the same order. The equalTo method is a shortcut for using the List.equal method: equal(this, l).

### Method getEnumerator

Creates an enumerator for a list which allows you to traverse the list.

    public ListEnumerator getEnumerator()

#### Return Value

A listEnumerator object for the current list.

### Method pack

Serializes the current instance of the List class.

    public container pack()

#### Return Value

A container that contains the current instance of the List class.

#### Remarks

The container created by this method contains 3 elements before the first element from the list:

-   A version number for the container
-   An integer that identifies the data type of the list elements
-   The number of elements in the list

If the elements in the list are objects, packing is performed by calling the pack method successively on each object to yield a subcontainer. The list can be retrieved from the packed container by using the List.create method.

#### Examples

The following example creates a list of records and passes in the packed list as a parameter for creating a new projReverseMarking object.

    public boolean canClose() 
    { 
        ProjReverseMarking      projReverseMarking; 
        boolean                 canClose; 
        List                    list; 
        canClose = super(); 
        if (element.closedOk() && canClose) 
        { 
            List = new List(Types::Record); 
            while select tmpFrmVirtualLines 
            { 
                list.addEnd(tmpFrmVirtualLines); 
            } 
            projReverseMarking = new ProjReverseMarking(list.pack()); 
            projReverseMarking.run(); 
        } 
        return canClose; 
    }

### Method toString

Returns a description of the values in the list.

    public str toString()

#### Return Value

A string that describes the values of the elements in the list.

#### Remarks

To print a description of the type of the elements in the list, use the List.definitionString method.

#### Examples

The following example creates a list of integers. The toString method is used to print a description of the values in the list.

    { 
        // Create a list of integers 
        List il = new List(Types::Integer); 
        // Add some elements to the list 
        il.addEnd(1); 
        il.addEnd(2); 
        il.addStart(3); 
        // Print a description of the list 
        print il.definitionString(); 
        print il.toString(); 
        pause; 
    }

### Method typeId

Returns the type of the values in a list.

    public Types typeId()

#### Return Value

The type of the list elements.

#### Remarks

The type of the list is specified when the list is created, and remains the same throughout the life of the list.

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method create

Creates a list from the container obtained from a prior call to the List.pack method.

    public static List create(container container)

#### Parameters

container  
The container that holds the packed list.

#### Return Value

A list identical to the one that was packed into the container.

#### Examples

The following example creates a list and packs it into a container. The create method is then used to unpack the container and create a list identical to the original one.

    { 
        List il = new List(Types::Integer); 
        List newList; 
        container packedList; 
        // Add some elements 
        il.addEnd(1); 
        il.addEnd(2); 
        il.addEnd(3); 
        // Pack the list into a container 
        packedList = il.pack(); 
        newList = list::create(packedList); 
        // Prints <1, 2, 3> 
        print newList.toString(); 
        pause; 
    }

### Method createFromXML

    public static List createFromXML(Object xmlnode)

#### Parameters

xmlnode  

#### Return Value

### Method equal

Determines whether two lists are identical.

    public static boolean equal(List list1, List list2)

#### Parameters

list1  
The second list to be compared.

<!-- -->

list2  
The second list to be compared.

#### Return Value

true if the two lists are identical; otherwise, false.

#### Remarks

A list is equal to another list if the two lists are the same type, contain the same number of elements, and the elements occur in the same order.

### Method merge

Combines two lists to create a new list.

    public static List merge(List list1, List list2)

#### Parameters

list1  
The list that will be added to the end of the first to create the new list.

<!-- -->

list2  
The list that will be added to the end of the first to create the new list.

#### Return Value

The new list.

#### Remarks

The types of the lists must be the same.

#### Examples

The following example creates two lists of integer values, merges them to create a new list, and then prints out the values in the new combined list.

    { 
        List list1  = new List(Types::Integer); 
        List list2  = new List(Types::Integer); 
        List combinedList  = new List(Types::Integer); 
        int  i; 
        for(i=1; i<6; i++) 
        { 
            List1.addEnd(i); 
        } 
         for(i=6; i<11; i++) 
        { 
            List2.addEnd(i); 
        } 
        combinedList = List::merge(list1, list2); 
        print combinedList.toString(); 
        pause; 
    }

### Method appendList

    public void appendList(List list)

#### Parameters

list  

### Method new

Creates a list.

    public void new(Types Type)

#### Parameters

Type  
The type that the elements in the list should have.

#### Remarks

The possible values for the Type parameter are supplied by the Types system enum. After you have created a list, you cannot change the type of the elements it contains.

#### Examples

The following example creates a list of strings.

    { 
        // Creates a list of integers. 
        List il = new List(Types::String); 
    }

## Class ListEnumerator
    class ListEnumerator extends Object

The ListEnumerator class lets you traverse the elements in a list.

### Remarks

List enumerators start before the first element in the list. You must call the ListEnumerator.moveNext method to make it point to the first element in the list. It is best practice to use the ListEnumerator class instead of the ListIterator class, because enumerators are automatically created on the same tier as the list (when the list.getEnumerator method is called). This avoids a potential problem in code that is marked as Called from, where the iterator and list can be on separate tiers. In addition, list enumerators require less code than list iterators and therefore perform slightly better. The only situation where you have to use a list iterator is if you want to delete items from a list (use the ListIterator.delete method).

### Examples

The following example creates a list of integers and puts some values into it. It then creates an enumerator, and then sets the enumerator to the first element in the list and then the second element in the list.

    { 
        List list = new List(Types::Integer); 
        ListEnumerator enumerator; 
        // Add some elements to the list 
        list.addEnd(1); 
        list.addEnd(2); 
        list.addStart(3); 
        // Set the enumerator 
        enumerator = list.getEnumerator(); 
        // Print a description of the list 
        print enumerator.definitionString(); 
        // Go to beginning of enumerator 
        enumerator.reset(); 
        //Go to the first element in the List 
        enumerator.moveNext(); 
        // Print contents of first and second elements 
        // First element is 3 as this was added to start of list 
        print enumerator.toString(); 
        enumerator.moveNext(); 
        print enumerator.toString(); 
        pause; 
    }

### Methods

| Method                        | Description                                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------------------|
| public AnyType current()      | Retrieves the value that is pointed to by the enumerator.                                                     |
| public str definitionString() | Returns a description of the enumerator.                                                                      |
| public boolean moveNext()     | Determines whether the enumerator denotes a valid list element.                                               |
| public str toString()         | Returns a description of the content of the element in the list that the enumerator is currently pointing to. |
| public void reset()           | Moves the enumerator to the start of the list.                                                                |

### Method current

Retrieves the value that is pointed to by the enumerator.

    public AnyType current()

#### Return Value

The value that is currently pointed to in the list. The type of the return value is determined by the type of the items in the list.

#### Examples

The following example iterates through the list and sets the dimensionTopic variable to the value of the current list element.

    public DimensionTopic firstDimensionTopic() 
    { 
        DimensionTopic  dimensionTopic; 
        ListEnumerator  enumerator; 
        enumerator = this.getTopicsEnumerator(); 
        if (enumerator.moveNext()) 
        { 
            dimensionTopic = enumerator.current(); 
        } 
        return dimensionTopic; 
    }

### Method definitionString

Returns a description of the enumerator.

    public str definitionString()

#### Return Value

A string that contains a description of the enumerator.

#### Remarks

For example, an enumerator for a list of integers would return int list enumerator.

#### Examples

The following example creates a list and an enumerator for the list. It uses the definitionString method to print a description of the enumerator.

    { 
        List list = new List(Types::Integer); 
        ListEnumerator  enumerator; 
        ; 
        // Add some elements to the list 
        list.addEnd(1); 
        list.addEnd(2); 
        list.addStart(3); 
        // Set the enumerator 
        enumerator = list.getEnumerator(); 
        print enumerator.definitionString(); 
        pause; 
    }

### Method moveNext

Determines whether the enumerator denotes a valid list element.

    public boolean moveNext()

#### Return Value

true if the current position in the list holds a valid element; otherwise, false.

#### Remarks

List enumerators start before the first element in the list. You must call the moveNext method to make it point to the first element in the list.

#### Examples

The following example uses the moveNext method to check whether there is another element in the list and then sets the dimensionTopic variable to the value of the current list element.

    public DimensionTopic firstDimensionTopic() 
    { 
        DimensionTopic  dimensionTopic; 
        ListEnumerator  enumerator; 
        enumerator = this.getTopicsEnumerator(); 
        if (enumerator.moveNext()) 
        { 
            dimensionTopic = enumerator.current(); 
        } 
        return dimensionTopic; 
    }

### Method toString

Returns a description of the content of the element in the list that the enumerator is currently pointing to.

    public str toString()

#### Return Value

A string that contains a description of the current list element.

#### Examples

The following example creates a list, and then prints the content of the first and second elements in the list.

    { 
        List list = new List(Types::Integer); 
        ListEnumerator  enumerator; 
        // Add some elements to the list 
        list.addEnd(1); 
        list.addEnd(2); 
        list.addStart(3); 
        // Set the enumerator 
        enumerator = list.getEnumerator(); 
        // Go to beginning of enumerator 
        enumerator.reset(); 
        //Go to the first element in the List 
        enumerator.moveNext(); 
        // First element is 3 as this was added to start of list 
        print enumerator.toString(); 
        pause; 
        enumerator.moveNext(); 
        //Print second element in list (1) 
        print enumerator.toString(); 
        pause; 
    }

### Method reset

Moves the enumerator to the start of the list.

    public void reset()

#### Remarks

The reset method moves the enumerator to the start of the list, before the first element in the list. You must call the ListEnumerator.moveNext method to make it point to the first element in the list.

#### Examples

The following example creates a list and then an enumerator for the list. It uses the reset method to move to the start of the list and then uses the moveNext method to move to the first element in the list.

    { 
        List list = new List(Types::Integer); 
        ListEnumerator  enumerator; 
        // Add some elements to the list 
        list.addEnd(1); 
        list.addEnd(2); 
        list.addStart(3); 
        // Set the enumerator 
        enumerator = list.getEnumerator(); 
        // Go to beginning of enumerator 
        enumerator.reset(); 
        //Go to the first element in the List 
        enumerator.moveNext(); 
        // First element is 3 as this was added to start of list 
        print enumerator.toString(); 
        pause; 
    }

## Class ListIterator
    class ListIterator extends Object

The ListIterator class is used to iterate over the elements in a list.

### Remarks

List iterators can be viewed as pointers into the lists over which they iterate. Functionality is available to start the iteration, determine whether more elements are available, and fetch the element that is pointed to by the iterator. The order in which the elements occur during iteration is defined by the sequence in which the elements are inserted. Elements can be inserted by using the List.addStart, List.addEnd, or ListIterator.insert method. It is better to use the ListEnumerator class than the ListIterator class. List iterators and the maps over which they iterate must be on the same client/server side. If you use the ListIterator class, and code is marked as Called from, it is possible that the list and the iterator will be on different tiers. In this case, the code will fail. If you use the ListEnumerator class, the enumerator is automatically created on the same tier as the list. Additionally, to move to the next item in a list, you must explicitly call the more and next methods if you are using a list iterator. If you use the ListEnumerator class, you only have to call the moveNext method. The only situation where you cannot use a list enumerator is where you need to delete elements from a list. For more information, see the delete method.

### Examples

The following example creates a list and an iterator to point to it. It then uses various methods on the ListIterator class to print a description of the list, and the items in the list.

    { 
        List il = new List(types::Integer); 
        ListIterator it; 
        // Add some elements into the list. 
        il.addStart(1); 
        il.addStart(2); 
        il.addStart(4);  
        // Create a list iterator to traverse the values. 
        it = new ListIterator (il);  
        // Prints "int list iterator". 
        print it.definitionString();  
        // Prints "(begin)[4]". 
        print it.toString();  
        // Go on for as long as elements are found in the list. 
        // Prints 4, 2, 1. 
        while (it.more()) 
        { 
            print it.value(); 
            it.next(); 
        } 
        // Prints (end). 
        print it.toString(); 
        pause; 
    }

### Methods

| Method                               | Description                                                                                    |
|--------------------------------------|------------------------------------------------------------------------------------------------|
| public str definitionString()        | Returns a textual representation of the type of the iterator.                                  |
| public AnyType insert(AnyType value) | Inserts a new value at the position in the list that the iterator currently points to.         |
| public boolean more()                | Determines whether the list iterator points to a valid element.                                |
| public str toString()                | Returns a textual representation of the current list value that is pointed to by the iterator. |
| public AnyType value()               | Retrieves the value that is pointed to by the iterator.                                        |
| public void begin()                  | Moves the iterator to the start of the list.                                                   |
| public void next()                   | Moves the iterator to the next element in the list.                                            |
| public void end()                    | Moves the iterator past the last element in the list.                                          |
| public void delete()                 | Removes the element that is pointed to by the iterator from the list.                          |
| public void new(List list)           | Creates a new iterator for a particular list.                                                  |

### Method definitionString

Returns a textual representation of the type of the iterator.

    public str definitionString()

#### Return Value

A string that contains the type of the iterator.

#### Remarks

For example: int list iterator.

### Method insert

Inserts a new value at the position in the list that the iterator currently points to.

    public AnyType insert(AnyType value)

#### Parameters

value  
The value of the item to insert into the list.

#### Return Value

The value that was inserted into the list.

#### Remarks

The value parameter must be the same type as the list.

#### Examples

The following example creates a list that has ten items and then uses the ListIterator.insert method to insert a new value as the third item in the list.

    { 
        List il = new List(Types::Integer); 
        ListIterator it; 
        int i; 
        int j = 25; 
        // Insert values 1 to 10 into the list 
        for (i = 1; i <= 10; i++) 
        { 
            il.addEnd(i); 
        } 
        // Go to the 3rd element in the list 
        it = new ListIterator(il); 
        it.begin(); 
        it.next(); 
        it.next(); 
        // Insert a new value (25) 
        it.insert(j); 
      it.begin(); 
        // Print all values in the list. 
        // 25 is the third value in the list 
        while (it.more()) 
        { 
            print it.value(); 
            it.next();  
        } 
        pause; 
    }

### Method more

Determines whether the list iterator points to a valid element.

    public boolean more()

#### Return Value

true if the list iterator points to a valid element; otherwise, false.

#### Remarks

Attempting to access an element when this method returns false will cause an error.

#### Examples

The following example uses the ListIterator.more method to check whether there are more elements in the list and then runs through the while loop, which prints the values of all the elements in the list.

    { 
        List il = new List(Types::Integer); 
        ListIterator it; 
        int i; 
        // Add some elements 
        for (i = 1; i <= 10; i++) 
        { 
            il.addEnd(i); 
        } 
        // Traverse the list 
        it = new ListIterator(il); 
        while (it.more()) 
        { 
            print it.value(); 
            it.next(); // Skip to the next element 
        } 
        pause; 
    }

### Method toString

Returns a textual representation of the current list value that is pointed to by the iterator.

    public str toString()

#### Return Value

A string that contains a description of the current value.

#### Remarks

If the iterator points to the first element in the list, the string will contain an indication of this, in the form "(begin)\[value\]" If the iterator does not point to an element (that is, the more() method returns false), the following string returned is: (end). If the iterator points to a value, the string is "\[value\]", where value is a string representation of the element value.

#### Examples

The following example prints the following description of the values of the two values in a list:

1.  (begin) \[2\]
2.  \[1\]

<!-- -->

    { 
        List li = new List(Types::Integer); 
        ListIterator it = new ListIterator(li); 
        li.addStart(1); 
        li.addStart(2); // This is now the first value 
        it.begin(); 
        print it.toString(); 
        it.next(); 
        print it.toString(); 
        pause; 
    }

### Method value

Retrieves the value that is pointed to by the iterator.

    public AnyType value()

#### Return Value

The value that is pointed to by the iterator.

#### Remarks

Before you try to retrieve the value of a list element, use the ListIterator.more method to test whether an element exists.

### Method begin

Moves the iterator to the start of the list.

    public void begin()

### Method next

Moves the iterator to the next element in the list.

    public void next()

#### Remarks

Use the ListIterator.more method to determine whether the iterator points to a valid element.

#### Examples

The following example uses the ListIterator.next method to traverse a list as the value of each element is printed.

    { 
        List il = new List(Types::Integer); 
        ListIterator it; 
        int i; 
        // Add some elements 
        for (i = 1; i <= 10; i++) 
        { 
            il.addEnd(i); 
        } 
        // Traverse the list 
        it = new ListIterator(il); 
        while (it.more()) 
        { 
            print it.value(); 
            // Move to the next element 
            it.next();  
        } 
        pause; 
    }

### Method end

Moves the iterator past the last element in the list.

    public void end()

#### Remarks

After this method runs, the ListIterator.more method will return false.

### Method delete

Removes the element that is pointed to by the iterator from the list.

    public void delete()

#### Remarks

The iterator will point to the next element after the deletion.

#### Examples

The following example creates a list that contains three elements and prints a description of the elements in the list. It then deletes the first element in the list and prints a description of the remaining elements.

    { 
        List li = new List(Types::Integer); 
        ListIterator it; 
        li.addStart(1); 
        li.addStart(2); 
        li.addStart(3); 
        print li.toString(); 
        it = new ListIterator(li); 
        it.delete(); 
        print li.toString(); 
        pause; 
    }

### Method new

Creates a new iterator for a particular list.

    public void new(List list)

#### Parameters

list  
The list for which to create an iterator.

#### Remarks

The iterator is positioned at the first value in the list, if the list is not empty. Iterators and the lists that they iterate over must be on the same client/server side.

#### Examples

The following example creates an iterator for a list of integers.

    List il = new List(types::Integer); 
    ListIterator it; 
    it = new ListIterator (il);

## Class ListPage
    class ListPage extends Page

### Remarks

### Examples

### Methods

| Method                                                                      | Description                                       |
|-----------------------------------------------------------------------------|---------------------------------------------------|
| public str actionPaneControlParameters(str controlName, \[str parameters\]) |                                                   |
| public Array activeActionPaneTabNames()                                     | Gets the name of the specified active tab.        |
| public str caption(\[str value\])                                           |                                                   |
| public ListPageArgs listPageArgs()                                          |                                                   |
| public int listPageFieldDataField(str fieldName)                            |                                                   |
| public Array listPageFieldNames()                                           |                                                   |
| public int listPageFieldTableId(str fieldName)                              |                                                   |
| public boolean listPageFieldVisible(str fieldName, \[boolean visible\])     |                                                   |
| public str modeledQueryName(\[str value\])                                  |                                                   |
| public void new()                                                           | Initializes a new instance of the ListPage class. |

### Method actionPaneControlParameters

    public str actionPaneControlParameters(str controlName, [str parameters])

#### Parameters

controlName  

<!-- -->

parameters  

#### Return Value

### Method activeActionPaneTabNames

Gets the name of the specified active tab.

    public Array activeActionPaneTabNames()

#### Return Value

An array that contains the names of the active tabs.

### Method caption

    public str caption([str value])

#### Parameters

value  

#### Return Value

### Method listPageArgs

    public ListPageArgs listPageArgs()

#### Return Value

### Method listPageFieldDataField

    public int listPageFieldDataField(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method listPageFieldNames

    public Array listPageFieldNames()

#### Return Value

### Method listPageFieldTableId

    public int listPageFieldTableId(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method listPageFieldVisible

    public boolean listPageFieldVisible(str fieldName, [boolean visible])

#### Parameters

fieldName  

<!-- -->

visible  

#### Return Value

### Method modeledQueryName

    public str modeledQueryName([str value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the ListPage class.

    public void new()

## Class ListPageArgs
    class ListPageArgs extends PageArgs

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class ListPageInteraction
    class ListPageInteraction extends PageInteraction

### Remarks

### Examples

### Methods

| Method                                           | Description                                                   |
|--------------------------------------------------|---------------------------------------------------------------|
| public ListPage listPage()                       |                                                               |
| public void tabChanged(container activeTabNames) | Called when the active tab is changed.                        |
| public void initializing()                       |                                                               |
| public void initialized()                        |                                                               |
| public void selectionChanged()                   |                                                               |
| public void initializeQuery(Query query)         |                                                               |
| public void new(ListPage listPage)               | Creates a new PageInteraction object operating on a listPage. |

### Method listPage

    public ListPage listPage()

#### Return Value

### Method tabChanged

Called when the active tab is changed.

    public void tabChanged(container activeTabNames)

#### Parameters

activeTabNames  
A container containing the names of the active tabs.

### Method initializing

    public void initializing()

### Method initialized

    public void initialized()

### Method selectionChanged

    public void selectionChanged()

### Method initializeQuery

    public void initializeQuery(Query query)

#### Parameters

query  

### Method new

Creates a new PageInteraction object operating on a listPage.

    public void new(ListPage listPage)

#### Parameters

listPage  
The specified ListPage object.

## Class LoadAutoCompleteDataEventArgs
    class LoadAutoCompleteDataEventArgs extends Object

### Remarks

### Examples

### Methods

| Method                                                                                          | Description |
|-------------------------------------------------------------------------------------------------|-------------|
| public AutoCompleteDataMode autoCompleteDataMode(\[AutoCompleteDataMode autoCompleteDataMode\]) |             |
| public boolean canPage(\[boolean canPage\])                                                     |             |
| public str filterValue()                                                                        |             |
| public AnyType lastPagedTag()                                                                   |             |
| public FormSegment segment()                                                                    |             |
| public void addAutoCompleteData(str value, str description, AnyType tag)                        |             |

### Method autoCompleteDataMode

    public AutoCompleteDataMode autoCompleteDataMode([AutoCompleteDataMode autoCompleteDataMode])

#### Parameters

autoCompleteDataMode  

#### Return Value

### Method canPage

    public boolean canPage([boolean canPage])

#### Parameters

canPage  

#### Return Value

### Method filterValue

    public str filterValue()

#### Return Value

### Method lastPagedTag

    public AnyType lastPagedTag()

#### Return Value

### Method segment

    public FormSegment segment()

#### Return Value

### Method addAutoCompleteData

    public void addAutoCompleteData(str value, str description, AnyType tag)

#### Parameters

value  

<!-- -->

description  

<!-- -->

tag  

## Class LoginProperty
    class LoginProperty extends Object

The LoginProperty class enables logon information to be passed to an instance of the OdbcConnection class.

### Remarks

### Examples

### Methods

| Method                                                | Description                                                                                                                                                                                            |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public str getDatabase()                              | Retrieves the name of the database, as stored in the LoginProperty class.                                                                                                                              |
| public str getDSN()                                   | Retrieves the data source name (DSN) that is stored in the LoginProperty class.                                                                                                                        |
| public str getOciServiceName()                        | Retrieves the Oracle service name that is stored in the LoginProperty class.                                                                                                                           |
| public str getOther()                                 | Retrieves the additional logon parameters that are stored in the LoginProperty class.                                                                                                                  |
| public str getServer()                                | Retrieves the server name that is stored in the LoginProperty class.                                                                                                                                   |
| public str getTcpIpPort()                             | Retrieves the TCP/IP port that is stored in the LoginProperty class.                                                                                                                                   |
| public boolean getUsePredefinedService()              | Returns whether the loginProperty class is set to use a predefined Oracle service instead of specifying the server and database information on the loginProperty class.                                |
| public void setTcpIpPort(str tcpipPort)               | Specifies which TCP/IP port is used to connect to Oracle.                                                                                                                                              |
| public void setDatabase(str database)                 | Sets the name of the database to log on to.                                                                                                                                                            |
| public void setDSN(str datasourceName)                | Sets the DSN that is used to access the data source.                                                                                                                                                   |
| public void new()                                     | Initializes a new instance of the LoginProperty class.                                                                                                                                                 |
| public void setOciServiceName(str ociServiceName)     | Specifies an Oracle service name.                                                                                                                                                                      |
| public void setOther(str otherOdbcParameters)         | Sets additional nonstandard logon parameters that are stored in the LoginProperty class.                                                                                                               |
| public void setServer(str serverName)                 | Sets the name of the server on which the database resides.                                                                                                                                             |
| public void setUsePredefinedService(boolean newValue) | Specifies whether to use a predefined Oracle service (created by using Oracle network configuration tools) for the connection information, or whether it will be specified in the loginProperty class. |

### Method getDatabase

Retrieves the name of the database, as stored in the LoginProperty class.

    public str getDatabase()

#### Return Value

The name of the database.

### Method getDSN

Retrieves the data source name (DSN) that is stored in the LoginProperty class.

    public str getDSN()

#### Return Value

The DSN.

### Method getOciServiceName

Retrieves the Oracle service name that is stored in the LoginProperty class.

    public str getOciServiceName()

#### Return Value

The Oracle service name.

### Method getOther

Retrieves the additional logon parameters that are stored in the LoginProperty class.

    public str getOther()

#### Return Value

The additional logon parameters as a string.

### Method getServer

Retrieves the server name that is stored in the LoginProperty class.

    public str getServer()

#### Return Value

The name of the server.

### Method getTcpIpPort

Retrieves the TCP/IP port that is stored in the LoginProperty class.

    public str getTcpIpPort()

#### Return Value

The TCP/IP port.

### Method getUsePredefinedService

Returns whether the loginProperty class is set to use a predefined Oracle service instead of specifying the server and database information on the loginProperty class.

    public boolean getUsePredefinedService()

#### Return Value

true if a predefined Oracle service is used to connect; otherwise, false.

### Method setTcpIpPort

Specifies which TCP/IP port is used to connect to Oracle.

    public void setTcpIpPort(str tcpipPort)

#### Parameters

tcpipPort  
The TCP/IP port to use.

#### Remarks

The default port is 1521.

### Method setDatabase

Sets the name of the database to log on to.

    public void setDatabase(str database)

#### Parameters

database  
The name of the database.

### Method setDSN

Sets the DSN that is used to access the data source.

    public void setDSN(str datasourceName)

#### Parameters

datasourceName  
The name of the data source.

### Method new

Initializes a new instance of the LoginProperty class.

    public void new()

### Method setOciServiceName

Specifies an Oracle service name.

    public void setOciServiceName(str ociServiceName)

#### Parameters

ociServiceName  
The name of the service.

#### Remarks

This method is used when the loginProperty class is not set to use a predefined Oracle service.

### Method setOther

Sets additional nonstandard logon parameters that are stored in the LoginProperty class.

    public void setOther(str otherOdbcParameters)

#### Parameters

otherOdbcParameters  
The additional ODBC-formatted parameters.

#### Remarks

This method should be used only if the data source that you want to use requires some additional, nonstandard parameters. The parameters must be applied in the standard ODBC format: &lt;parm1&gt;=&lt;value1&gt;;&lt;parm2&gt;=&lt;value2&gt;,... For example: MODE=1;PATCH=32

### Method setServer

Sets the name of the server on which the database resides.

    public void setServer(str serverName)

#### Parameters

serverName  
The name of the server where the database is located.

### Method setUsePredefinedService

Specifies whether to use a predefined Oracle service (created by using Oracle network configuration tools) for the connection information, or whether it will be specified in the loginProperty class.

    public void setUsePredefinedService(boolean newValue)

#### Parameters

newValue  
A Boolean value that indicates whether to use a predefined Oracle service.

#### Remarks

By default, a predefined service is not used.

