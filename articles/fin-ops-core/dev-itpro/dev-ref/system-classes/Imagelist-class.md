---
title: Imagelist class
description: This topic describes the Imagelist class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class Imagelist

[!include [banner](../../includes/banner.md)]

```xpp
class Imagelist extends BinData
```

The Imagelist class lets you work with a list of images.

## Remarks

To work with a single image, use the Image class.

## Examples

The following example creates an image list and adds the icons in the Shell32.dll file. It then deletes the fourth member of the list.

```xpp
Imagelist list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight() ); 
list.loadIcons('shell32.dll'); 
print list.count(); 
list.remove(4); 
print list.count(); 
pause;
```

## Methods

| Method                                                                         | Description                                                                                                                        |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| public int add(Image image)                                                    | Adds a new image to the image list.                                                                                                |
| public boolean autoResize(\[boolean value\])                                   | Sets the Boolean autoResize flag, which determines whether new images are automatically resized.                                   |
| public int clear()                                                             | Removes all images from the image list.                                                                                            |
| public int count()                                                             | Retrieves the number of images in an image list.                                                                                   |
| public boolean dragBegin(int imageIdx, int hotSpotX, int hotSpotY)             | Begins dragging an image.                                                                                                          |
| public boolean dragEnd()                                                       | Ends a drag operation.                                                                                                             |
| public boolean dragEnter(int hWnd, int x, int y)                               | Locks updates to the specified window during a drag operation and displays the drag image at the specified position in the window. |
| public boolean dragLeave(int hWnd)                                             | Unlocks the specified window and hides the drag image, so that the window to be updated.                                           |
| public boolean dragMove(int x, int y)                                          | Moves the image that is being dragged during a drag-and-drop operation.                                                            |
| public boolean dragShowImage(boolean show)                                     | Shows or hides the image that is being dragged.                                                                                    |
| public int height()                                                            | Retrieves the height, in pixels, of the images in the image list.                                                                  |
| public int loadIcons(str moduleName)                                           | Loads icons from the specified resource into the image list.                                                                       |
| public int remove(int imageIdx)                                                | Removes an image from an image list.                                                                                               |
| public int replace(int imageIdx, Image image)                                  | Replaces an existing image in the list.                                                                                            |
| public boolean setOverlayImage(int imageIdx, int overlayIdx)                   | Adds an image to the list of images to use as overlay masks.                                                                       |
| public int width()                                                             | Retrieves the width, in pixels, of the images in the image list.                                                                   |
| ::public static int iconHeight()                                               | Retrieves the system metrics for the height of a standard icon.                                                                    |
| ::public static int iconWidth()                                                | Retrieves the system metrics for the width of a standard icon.                                                                     |
| ::public static int smallIconHeight()                                          | Retrieves the system metrics for the height of a small icon.                                                                       |
| ::public static int smallIconWidth()                                           | Retrieves the system metrics for the width of a small icon.                                                                        |
| public void maskColor(int Color)                                               | Sets the masking color.                                                                                                            |
| public void draw(int HDC, int imageIdx, int x, int y, \[boolean transparent\]) | Draws an image list item in the specified device context.                                                                          |
| public void finalize()                                                         |                                                                                                                                    |
| public void new(int cx, int cy, \[boolean transparent\])                       | Creates a new empty list to hold images.                                                                                           |

## Method add

Adds a new image to the image list.

```xpp
public int add(Image image)
```

### Parameters - add

image  
The new image to add to the list.

### Return Value - add

0 if the method is successful.

### Remarks - add

You can use the autoResize method to automatically resize images when you add them to the list.

### Examples - add

The following example creates a new image list and adds three images to it.

```xpp
ImageList list = new Imagelist( 
    Imagelist::smallIconWidth(), 
    Imagelist::smallIconHeight()); 
list.add(new Image(3104)); 
list.add(new Image(1097)); 
list.add(new Image(1200)); 
// Prints 3 
print list.count(); 
pause;
```

## Method autoResize

Sets the Boolean autoResize flag, which determines whether new images are automatically resized.

```xpp
public boolean autoResize([boolean value])
```

### Parameters - autoResize

value  
A Boolean value that determines whether the autoResize flag is set; optional.

### Return Value - autoResize

### Remarks - autoResize

If the autoResize flag is set to true, any image that you add to the list is automatically resized to the dimensions that were specified when you created the image list.

## Method clear

Removes all images from the image list.

```xpp
public int clear()
```

### Return Value - clear

0 if the method is successful.

## Method count

Retrieves the number of images in an image list.

```xpp
public int count()
```

### Return Value - count

An integer that represents the number of images in the list.

### Examples - count

The following example creates an image list, loads icons from the shell.dll file, and then prints the number of images in the list.

```xpp
Imagelist list; 
int       counter; 
list = new Imagelist( 
   Imagelist::iconWidth(), 
   Imagelist::iconHeight() ); 
list.loadIcons('shell32.dll'); 
print list.count(); 
pause;
```

## Method dragBegin

Begins dragging an image.

```xpp
public boolean dragBegin(int imageIdx, int hotSpotX, int hotSpotY)
```

### Parameters - dragBegin

imageIdx  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

<!-- -->

hotSpotX  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

<!-- -->

hotSpotY  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

### Return Value - dragBegin

1 if the method is successful.

### Remarks - dragBegin

The rest of the drag operation is specified by the dragEnter, dragMove, dragLeave, and dragEnd methods.

## Method dragEnd

Ends a drag operation.

```xpp
public boolean dragEnd()
```

### Return Value - dragEnd

1 if the method is successful; otherwise, 0.

### Remarks - dragEnd

The rest of the drag operation is specified by the dragBegin, dragEnter, dragMove, and dragLeave methods.

## Method dragEnter

Locks updates to the specified window during a drag operation and displays the drag image at the specified position in the window.

```xpp
public boolean dragEnter(int hWnd, int x, int y)
```

### Parameters - dragEnter

hWnd  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

x  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

y  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

### Return Value - dragEnter

1 if the method is successful; otherwise, 0.

### Remarks - dragEnter

To start the drag operation, call the dragBegin method. The rest of the drag operation is specified by the dragMove, dragLeave, and dragEnd methods.

## Method dragLeave

Unlocks the specified window and hides the drag image, so that the window to be updated.

```xpp
public boolean dragLeave(int hWnd)
```

### Parameters - dragLeave

hWnd  
The handle to the window that owns the drag image.

### Return Value - dragLeave

1 if the method is successful; otherwise, 0.

### Remarks - dragLeave

The rest of the drag operation is specified by the dragBegin, dragEnter, dragMove, and dragEnd methods.

## Method dragMove

Moves the image that is being dragged during a drag-and-drop operation.

```xpp
public boolean dragMove(int x, int y)
```

### Parameters - dragMove

x  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

y  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

### Return Value - dragMove

1 if the method is successful; otherwise, 0.

### Remarks - dragMove

To start the drag operation, call the dragBegin method and then the dragEnter method. The rest of the drag operation is specified by the dragLeave and dragEnd methods.

## Method dragShowImage

Shows or hides the image that is being dragged.

```xpp
public boolean dragShowImage(boolean show)
```

### Parameters - dragShowImage

show  
A value that specifies whether to show the image.

### Return Value - dragShowImage

## Method height

Retrieves the height, in pixels, of the images in the image list.

```xpp
public int height()
```

### Return Value - height

An integer that represents the height of the images in pixels.

### Remarks - height

The height of the images in the list is set when you instantiate the list.

### Examples - height

The following example creates an image list, and sets the height and width of the images to the dimensions that are specified by the iconWidth and iconHeight methods. It then prints the height of images in the list.

```xpp
Imagelist list; 
list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight()); 
print list.height();   
pause;
```

## Method loadIcons

Loads icons from the specified resource into the image list.

```xpp
public int loadIcons(str moduleName)
```

### Parameters - loadIcons

moduleName  
The name of the file from which to load images.

### Return Value - loadIcons

0 if the method is successful.

### Examples - loadIcons

The following example creates a list of images and then loads the images that are contained in the shell32.dll file.

```xpp
Imagelist list; 
list = new Imagelist(Imagelist::iconWidth(),Imagelist::iconHeight()); 
list.loadIcons('shell32.dll');
```

## Method remove

Removes an image from an image list.

```xpp
public int remove(int imageIdx)
```

### Parameters - remove

imageIdx  
The position of the image to remove from the list.

### Return Value - remove

0 if the method is successful.

### Examples - remove

The following example creates an image list, adds the icons in shell32.dll file, and then deletes the fourth member of the list.

```xpp
Imagelist list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight() ); 
list.loadIcons('shell32.dll'); 
print list.count(); 
list.remove(4); 
print list.count(); 
pause;
```

## Method replace

Replaces an existing image in the list.

```xpp
public int replace(int imageIdx, Image image)
```

### Parameters - replace

imageIdx  
The image to use to replace the existing image.

<!-- -->

image  
The image to use to replace the existing image.

### Return Value - replace

0 if the method is successful.

## Method setOverlayImage

Adds an image to the list of images to use as overlay masks.

```xpp
public boolean setOverlayImage(int imageIdx, int overlayIdx)
```

### Parameters - setOverlayImage

imageIdx  
The one-based index of the overlay mask.

<!-- -->

overlayIdx  
The one-based index of the overlay mask.

### Return Value - setOverlayImage

1 if the method is successful.

### Examples - setOverlayImage

The following example creates an image list that has three images and then sets the last image as an overlay mask.

```xpp
Imagelist list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight() ); 
list.add(new Image(824)); // Image 0 
list.add(new Image(815)); // Image 1 
list.add(new Image(936)); //Image 2 
list.setOverlayImage (2,1);
```

## Method width

Retrieves the width, in pixels, of the images in the image list.

```xpp
public int width()
```

### Return Value - width

An integer that represents the width of the images in pixels.

### Remarks - width

The width of the images in the list is set when you instantiate the list.

### Examples - width

The following example creates an image list that has the standard height and width for icons, and then prints the width of images in the list.

```xpp
Imagelist list; 
list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight()); 
print list.width();   
pause;
```

## Method iconHeight

Retrieves the system metrics for the height of a standard icon.

```xpp
public static int iconHeight()
```

### Return Value - iconHeight

An integer that represents the height of a standard icon.

### Examples - iconHeight

The following example creates a list of images, and then sets them to the standard icon width and height.

```xpp
ImageList list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight());
```

## Method iconWidth

Retrieves the system metrics for the width of a standard icon.

```xpp
public static int iconWidth()
```

### Return Value - iconWidth

An integer that represents the width of a standard icon.

### Examples - iconWidth

The following example creates a list of images, and then sets them to the standard icon width and height.

```xpp
ImageList list = new Imagelist( 
    Imagelist::iconWidth(), 
    Imagelist::iconHeight());
```

## Method smallIconHeight

Retrieves the system metrics for the height of a small icon.

```xpp
public static int smallIconHeight()
```

### Return Value - smallIconHeight

An integer that represents the height of a small icon.

### Examples - smallIconHeight

The following example creates an image list that has the standard height and width for small icons, and then prints the height of images in the list.

```xpp
Imagelist list = new Imagelist( 
    Imagelist::smallIconWidth(), 
    Imagelist::smallIconHeight()); 
print list.height();   
pause;
```

## Method smallIconWidth

Retrieves the system metrics for the width of a small icon.

```xpp
public static int smallIconWidth()
```

### Return Value - smallIconWidth

An integer that represents the width of a small icon.

### Examples - smallIconWidth

The following example creates an image list that has the standard height and width for small icons, and then prints the width of images in the list.

```xpp
Imagelist list = new Imagelist( 
   Imagelist::smallIconWidth(), 
   Imagelist::smallIconHeight()); 
print list.width();   
pause;
```

## Method maskColor

Sets the masking color.

```xpp
public void maskColor(int Color)
```

### Parameters - maskColor

Color  
The color as an ARGB value.

## Method draw

Draws an image list item in the specified device context.

```xpp
public void draw(int HDC, int imageIdx, int x, int y, [boolean transparent])
```

### Parameters - draw

HDC  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

imageIdx  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

x  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

y  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

transparent  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

## Method finalize

```xpp
public void finalize()
```

## Method new

Creates a new empty list to hold images.

```xpp
public void new(int cx, int cy, [boolean transparent])
```

### Parameters - new

cx  

<!-- -->

cy  

<!-- -->

transparent  

### Remarks - new

You can use the autoResize method to automatically resize images when you add them to the list.

### Examples - new

The following example creates an image list to hold items of the standard icon width and height.

```xpp
Imagelist list; 
list = new Imagelist( 
   Imagelist::iconWidth(), 
   Imagelist::iconHeight());
```

