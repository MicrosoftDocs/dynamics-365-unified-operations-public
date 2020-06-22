---
title: Image class
description: This topic describes the Image class.
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

# Class Image

[!include [banner](../../includes/banner.md)]

```xpp
class Image extends BinData
```

Provides methods for loading, saving, and manipulating images. If you want to manipulate several images at the same time, use the Imagelist Class.

## Remarks

You can construct Image objects from the following file types:

-   Raster (bitmap) formats - .bmp, .gif, .jpg, .png, .tiff, and .exif
-   Vector formats - .emf and .wmf

If you want to work with several images at the same time, use the Imagelist class. You can construct the Image objects from the following file types:

-   Raster, which is a bitmap, formats - .bmp, .gif, .jpg, .png, .tiff, and .exif
-   Vector formats - .emf and .wmf

The Image class is bound to the client. The class can no longer be run from the server because of the security risks that are associated with file handling.

## Examples

The following example prints the height of Picture.jpg in pixels.

```xpp
Image img = new  Image(); 
img.loadFile(@'C:\MyPictures\Picture.jpg'); 
print img.height(); 
pause;
```

## Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public int captureScreen(int left, int top, int right, int bottom)                                          | Captures an image from the screen by using the coordinates that are supplied in the parameter list.                                           |
| public int captureWindow(int hWnd)                                                                          | Captures a window as an image, using the handle that is supplied as a parameter.                                                              |
| public int clipboardCopy()                                                                                  | Copies an image to the clipboard.                                                                                                             |
| public int clipboardPaste()                                                                                 | Overwrites an existing image with the content of the system clipboard.                                                                        |
| public int copyImage(Image image)                                                                           | Copies the current image object.                                                                                                              |
| public int createImage(int Width, int Height, int BitsPerPixel)                                             | Creates an empty bitmap image with the width, height, and color depth as specified by the parameters.                                         |
| public int crop(int x, int y, int w, int h)                                                                 | Crops the image.                                                                                                                              |
| public int displayImage(Int64 HDC, \[int Mode\], \[int Xpos\], \[int Ypos\], \[int Width\], \[int Height\]) | Draws an image with the device context specified by the HDC parameter.                                                                        |
| public Int64 exportBitmap()                                                                                 | Gets a handle for the image.                                                                                                                  |
| public int flip(FlipType FlipType)                                                                          | Rotates the image 180 degrees in a vertical or horizontal direction.                                                                          |
| public container getImageDimensionUnits()                                                                   |                                                                                                                                               |
| public int getPixel(int x, int y)                                                                           | Retrieves the ARGB color value of the pixel at the point that is specified by the parameters.                                                 |
| public int height()                                                                                         | Retrieves the height of the image in pixels.                                                                                                  |
| public container imageInfo()                                                                                | Retrieves the width, height, and color depth of the image.                                                                                    |
| public int imageSpotlight(int x, int y, int radius, int smoothing, int intensity)                           | Produces a spotlight effect within the circle that is defined by radius with center coordinates x and y.                                      |
| public int importBitmap(Int64 hBitmap)                                                                      | Clones a bitmap from the image that is specified by the hBitmap parameter.                                                                    |
| public int importFileIcon(str fileName)                                                                     | Creates an icon from the file specified by the fileName parameter by copying the icon that is used for the file.                              |
| public int importIcon(str fileName, int iconIdx)                                                            | Retrieves a handle to an icon from an executable file. The icon is specified by the fileName and iconIdx parameters. |
| public int loadImage(str fileName)                                                                          | Loads an image from the file specified by the fileName parameter.                                                                             |
| public int loadResource(int id)                                                                             | Loads a resource from Ax32.exe.                                                                                                               |
| public int promoteColor(int noOfColorBits)                                                                  | Increases the color depth of the image.                                                                                                       |
| public int reduceColorOctree(int maxColors)                                                                 | Reduces the color depth of an image.                                                                                                          |
| public int removeImage()                                                                                    | Removes the data about an image; the object still exists, but has no data.                                                                    |
| public int resize(int newWidth, int newHeight, InterpolationMode InterpolationMode)                         | Resizes the image to the size that is specified by the newWidth and newHeight parameters.                                                     |
| public int rotate(RotateType RotateType)                                                                    | Rotates the image.                                                                                                                            |
| public int saveImage(str fileName, \[ImageSaveType Type\])                                                  | Saves the image to the specified file name.                                                                                                   |
| public ImageSaveType saveType(\[ImageSaveType Type\])                                                       | Gets or sets the image decoder.                                                                                                               |
| public int setPixel(int x, int y, int pixel)                                                                | Sets the color for the pixel that is specified by the x and y parameters.                                                                     |
| public int transparent(\[boolean Set\], \[int RValue\], \[int GValue\], \[int BValue\])                     | Sets the transparent color for the image.                                                                                                     |
| public int width()                                                                                          | Retrieves the width of the image in pixels.                                                                                                   |
| ::public static int canLoad(str filename)                                                                   | Determines whether an image file exists and can be opened.                                                                                    |
| ::public static container loadExt(int idx)                                                                  | Retrieves a list of the extensions of the file formats that are supported by the Image class.                                                 |
| ::public static int resourceType(int resourceIdx)                                                           | Determines whether a particular resource is a bitmap or an icon.                                                                              |
| ::public static int rgb(int R, int G, int B)                                                                | Converts an RGB value to an ARGB value.                                                                                                       |
| ::public static int validResource(int id)                                                                   | Determines whether the resource specified by the id parameter is valid.                                                                       |
| public void new(\[AnyType image\], \[int width\], \[int height\])                                           | Creates a new image.                                                                                                                          |
| public void displayOrign(int Xpos, int Ypos)                                                                | Enables you to specify an offset (X, Y) from the original origin (0, 0).                                                                      |
| public void finalize()                                                                                      |                                                                                                                                               |

## Method captureScreen

Captures an image from the screen by using the coordinates that are supplied in the parameter list.

```xpp
public int captureScreen(int left, int top, int right, int bottom)
```

### Parameters - captureScreen

left  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

top  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

right  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

bottom  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

### Return Value - captureScreen

0 indicates success. Other values indicate failure.

### Examples - captureScreen

The following example captures a part of the screen and saves it to a file that is named test.bmp.

```xpp
Image img = new Image(); 
img.captureScreen(0, 0, 100, 100); 
img.saveFile(@'C:\test.bmp');
```

## Method captureWindow

Captures a window as an image, using the handle that is supplied as a parameter.

```xpp
public int captureWindow(int hWnd)
```

### Parameters - captureWindow

hWnd  
The handle to the window that you want to capture which must be supplied as an integer.

### Return Value - captureWindow

0 indicates success; otherwise, failure.

## Method clipboardCopy

Copies an image to the clipboard.

```xpp
public int clipboardCopy()
```

### Return Value - clipboardCopy

0 indicates success; otherwise, failure.

### Examples - clipboardCopy

The following example copies the content from a file that is named Test.bmp.

```xpp
Image img = new Image(); 
img.loadFile(@'C:\Test.bmp'); 
img.clipboardCopy(); 
// Image can now be pasted into an application.
```

## Method clipboardPaste

Overwrites an existing image with the content of the system clipboard.

```xpp
public int clipboardPaste()
```

### Return Value - clipboardPaste

0 indicates success; otherwise, failure.

### Remarks - clipboardPaste

For the method to be used successfully, the clipboard must have content.

### Examples - clipboardPaste

The following example creates a new image file by using contents previously copied to the clipboard.

```xpp
Image img = new Image();
// Copy an image to the clipboard before this test 
img.clipboardPaste(); 
img.saveFile(@'C:\test.jpg');
```

## Method copyImage

Copies the current image object.

```xpp
public int copyImage(Image image)
```

### Parameters - copyImage

image  
The image to be copied.

### Return Value - copyImage

0 indicates success; otherwise, failure.

### Examples - copyImage

The following example creates two new images and then overwrites the contents of one image with the contents of the other.

```xpp
Image img =  new Image(); 
Image img2 = new Image(); 
img.loadFile(@'C:\test.bmp'); 
img2.loadFile(@'C:\test2.bmp'); 
img2.copyImage(img); //img2 now the same as img
```

## Method createImage

Creates an empty bitmap image with the width, height, and color depth as specified by the parameters.

```xpp
public int createImage(int Width, int Height, int BitsPerPixel)
```

### Parameters - createImage

Width  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

<!-- -->

Height  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

<!-- -->

BitsPerPixel  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

### Return Value - createImage

0 indicates success; otherwise, failure.

### Examples - createImage

The following example creates an image with a height and width of 16 pixels, and a color depth of 32 bits per pixel.

```xpp
int i;
int j;
Image image;
image.createImage(
    Imagelist::smallIconWidth(),
    Imagelist::smallIconHeight(),
    32);
for (i=0; i < Imagelist::smallIconWidth(); i++)
{
    for (j=0; j < Imagelist::smallIconHeight(); j++)
    {
        if (i >= Imagelist::smallIconWidth()-2)
        {
            image.setPixel(i, j, WinAPI::RGB2int(0, 255, 255));
        }
        else
        {
            image.setPixel(i, j, WinAPI::imageTransparentColor());
        }
    }
}
```

## Method crop

Crops the image.

```xpp
public int crop(int x, int y, int w, int h)
```

### Parameters - crop

x  
The height of the region that you want to crop from the point (x, y).

<!-- -->

y  
The height of the region that you want to crop from the point (x, y).

<!-- -->

w  
The height of the region that you want to crop from the point (x, y).

<!-- -->

h  
The height of the region that you want to crop from the point (x, y).

### Return Value - crop

0 indicates success; otherwise, failure.

## Method displayImage

Draws an image with the device context specified by the HDC parameter.

```xpp
public int displayImage(Int64 HDC, [int Mode], [int Xpos], [int Ypos], [int Width], [int Height])
```

### Parameters - displayImage

HDC  
Optional parameter.

<!-- -->

Mode  
Optional parameter.

<!-- -->

Xpos  
Optional parameter.

<!-- -->

Ypos  
Optional parameter.

<!-- -->

Width  
Optional parameter.

<!-- -->

Height  
Optional parameter.

### Return Value - displayImage

0 indicates success; otherwise, failure.

## Method exportBitmap

Gets a handle for the image.

```xpp
public Int64 exportBitmap()
```

### Return Value - exportBitmap

An integer that represents the handle for the image.

### Examples - exportBitmap

The following example retrieves the handle for an image and then uses the handle to clone the image.

```xpp
{ 
    int hdlBitmap; 
    Image img = new Image(); 
    Image img2 = new Image(); 
    img.loadImage(@'C:\MyImage.bmp'); 
    //Set hdlBitmap to handle for MyImage.bmp 
    hdlBitmap = img.exportBitmap(); 
    //Load MyImage.bmp to img2 using image handle 
    if (hdlBitmap) 
    { 
        img2.importBitmap(hdlBitmap); 
    } 
}
```

## Method flip

Rotates the image 180 degrees in a vertical or horizontal direction.

```xpp
public int flip(FlipType FlipType)
```

### Parameters - flip

FlipType  
A FlipType enumeration that determines the way in which the image is flipped.

### Return Value - flip

0 indicates success; otherwise, failure.

### Remarks - flip

The possible values for the FlipType parameter are those available in the FlipType system enum:

|     |                    |                                                          |
|-----|--------------------|----------------------------------------------------------|
| 0   | RotateNoneFlipNone | No flip                                                  |
| 1   | RotateNoneFlipX    | Rotates the image 180 degrees in a horizontal direction. |
| 2   | RotateNoneFlipY    | Rotates the image 180 degrees in a vertical direction.   |

## Method getImageDimensionUnits

```xpp
public container getImageDimensionUnits()
```

### Return Value - getImageDimensionUnits

## Method getPixel

Retrieves the ARGB color value of the pixel at the point that is specified by the parameters.

```xpp
public int getPixel(int x, int y)
```

### Parameters - getPixel

x  
The vertical coordinate of the pixel.

<!-- -->

y  
The vertical coordinate of the pixel.

### Return Value - getPixel

An integer that is the ARGB value of the pixel (a 32-bit representation of an RGB color).

## Method height

Retrieves the height of the image in pixels.

```xpp
public int height()
```

### Return Value - height

An integer that represents the height of the image in pixels.

### Examples - height

The following example prints out the height of the image that is contained in test.bmp.

```xpp
Image img = new Image(); 
img.loadFile(@'C:\test.bmp'); 
print img.height(); 
pause;
```

## Method imageInfo

Retrieves the width, height, and color depth of the image.

```xpp
public container imageInfo()
```

### Return Value - imageInfo

A container that holds values that specify the width of the image, the height of the image, and the number of bits per pixel.

### Examples - imageInfo

The following example prints out the width and height of the image test.bmp, and specifies the color depth in bits per pixel.

```xpp
Image img = new Image(); 
container c; 
img.loadFile(@'C:\Test.bmp'); 
c = img.imageInfo(); 
print con2str(c); 
pause;
```

## Method imageSpotlight

Produces a spotlight effect within the circle that is defined by radius with center coordinates x and y.

```xpp
public int imageSpotlight(int x, int y, int radius, int smoothing, int intensity)
```

### Parameters - imageSpotlight

x  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

y  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

radius  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

smoothing  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

intensity  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

### Return Value - imageSpotlight

0 indicates success; otherwise, failure.

### Remarks - imageSpotlight

The pixels within the circle are unchanged, but the other pixels in the image are darkened by reducing their intensity.

## Method importBitmap

Clones a bitmap from the image that is specified by the hBitmap parameter.

```xpp
public int importBitmap(Int64 hBitmap)
```

### Parameters - importBitmap

hBitmap  
The handle to the image that you clone.

### Return Value - importBitmap

0 indicates success; otherwise, failure.

### Examples - importBitmap

The following example retrieves the handle for an image and then uses the importBitmap method to clone the image.

```xpp
{ 
    int hdlBitmap; 
    Image img = new Image(); 
    Image img2 = new Image(); 
    img.loadImage(@'C:\MyImage.bmp'); 
    //Set hdlBitmap to handle for MyImage.bmp 
    hdlBitmap = img.exportBitmap(); 
    //Load MyImage.bmp to img2 using image handle 
    if (hdlBitmap) 
    { 
        img2.importBitmap(hdlBitmap); 
    } 
}
```

## Method importFileIcon

Creates an icon from the file specified by the fileName parameter by copying the icon that is used for the file.

```xpp
public int importFileIcon(str fileName)
```

### Parameters - importFileIcon

fileName  
The name and the path of the file from which you create an icon.

### Return Value - importFileIcon

0 indicates success; otherwise, failure.

### Examples - importFileIcon

The following example copies the icon that is used for the file test.bmp.

```xpp
Image img = new Image(); 
img.importFileIcon(@'C:\test.bmp'); 
img.clipboardCopy(); 
// Icon used for test.bmp can now be pasted into an application.
```

## Method importIcon

Retrieves a handle to an icon from an executable file. The icon is specified by the fileName and iconIdx parameters.

```xpp
public int importIcon(str fileName, int iconIdx)
```

### Parameters - importIcon

fileName  
The resource within the specified file.

<!-- -->

iconIdx  
The resource within the specified file.

### Return Value - importIcon

0 indicates success; otherwise, failure.

## Method loadImage

Loads an image from the file specified by the fileName parameter.

```xpp
public int loadImage(str fileName)
```

### Parameters - loadImage

fileName  
The resource from which you want to load the image.

### Return Value - loadImage

0 indicates success; otherwise, failure.

## Method loadResource

Loads a resource from Ax32.exe.

```xpp
public int loadResource(int id)
```

### Parameters - loadResource

id  
The ID of the resource that you want to load. Values of resources can be found in the Resources macro.

### Return Value - loadResource

0 indicates success; otherwise, failure.

### Examples - loadResource

The following example adds two resources to an image list.

```xpp
Resource 
Image img; 
ImageList imageList; 
imageList = new Imagelist( 
    Imagelist::smallIconWidth(), 
    Imagelist::smallIconHeight()); 
img = new Image(); 
img.loadResource(#RES_NODE_CLOSED); 
imageList.add(img); 
img = new Image(); 
img.loadResource(#RES_NODE_OPEN); 
imageList.add(img);
```

## Method promoteColor

Increases the color depth of the image.

```xpp
public int promoteColor(int noOfColorBits)
```

### Parameters - promoteColor

noOfColorBits  
The number of bits that you want to promote the image to.

### Return Value - promoteColor

0 indicates success; otherwise, failure.

### Remarks - promoteColor

The method promotes:

-   8-bit images to 24 or 32 bits.
-   4-bit images to 8, 24, or 32 bits.
-   1-bit images to 4, 8, 24, or 32 bits.

### Examples - promoteColor

The following example increases the color depth of an image to 8 bits per pixel, unless it is already 8 or more.

```xpp
Image img = new Image(); 
img.loadFile(@'C:\test.bmp'); 
if (conpeek(img.imageInfo(),3) <8) 
{ 
    img.promoteColor(8); 
}
```

## Method reduceColorOctree

Reduces the color depth of an image.

```xpp
public int reduceColorOctree(int maxColors)
```

### Parameters - reduceColorOctree

maxColors  
The maximum number of colors.

### Return Value - reduceColorOctree

0 indicates success; otherwise, failure.

### Remarks - reduceColorOctree

The method reduces a 24-bit image to 8 bits, or an 8-bit image to 4 bits, unless other instructions are specified in the maxColors parameter. If the maxColors parameter is less than or equal to 16, a 4-bit image is produced. If maxColors is more than 16, an 8-bit image is produced.

## Method removeImage

Removes the data about an image; the object still exists, but has no data.

```xpp
public int removeImage()
```

### Return Value - removeImage

0 indicates success; otherwise, failure.

## Method resize

Resizes the image to the size that is specified by the newWidth and newHeight parameters.

```xpp
public int resize(int newWidth, int newHeight, InterpolationMode InterpolationMode)
```

### Parameters - resize

newWidth  
The resizing method.

<!-- -->

newHeight  
The resizing method.

<!-- -->

InterpolationMode  
The resizing method.

### Return Value - resize

0 indicates success; otherwise, failure.

### Remarks - resize

The possible values for the InterpolationMode parameter are those available in the InterpolationMode system enum:

|     |                                      |                                                                                                                                                                        |
|-----|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0   | InterpolationModeDefault             | Specifies the default interpolation mode.                                                                                                                              |
| 1   | InterpolationModeLowQuality          | Specifies a low-quality mode.                                                                                                                                          |
| 2   | InterpolationModeHighQuality         | Specifies a high-quality mode.                                                                                                                                         |
| 3   | InterpolationModeBilinear            | Specifies bilinear interpolation. No pre-filtering is done. This method is not suitable for shrinking an image below 50% of its original size.                         |
| 4   | InterpolationModeBicubic             | Specifies bicubic interpolation. No pre-filtering is done. This method is not suitable for shrinking an image below 25% of its original size.                          |
| 5   | InterpolationModeNearestNeighbor     | Specifies nearest-neighbor interpolation.                                                                                                                              |
| 6   | InterpolationModeHighQualityBilinear | Specifies high-quality, bilinear interpolation. Pre-filtering is performed to ensure high-quality shrinking.                                                           |
| 7   | InterpolationModeHighQualityBicubic  | Specifies high-quality, bicubic interpolation. Pre-filtering is performed to ensure high-quality shrinking. This mode produces the highest quality transformed images. |

## Method rotate

Rotates the image.

```xpp
public int rotate(RotateType RotateType)
```

### Parameters - rotate

RotateType  
The amount to rotate the image by.

### Return Value - rotate

0 indicates success; otherwise, failure.

### Remarks - rotate

The possible values for the RotateType parameter are those available in the RotateType system enum:

|     |                    |                          |
|-----|--------------------|--------------------------|
| 0   | RotateNoneFlipNone | No rotation.             |
| 1   | Rotate90FlipNone   | Rotation by 90 degrees.  |
| 2   | Rotate180FlipNone  | Rotation by 180 degrees. |
| 3   | Rotate270FlipNone  | Rotation by 270 degrees. |

## Method saveImage

Saves the image to the specified file name.

```xpp
public int saveImage(str fileName, [ImageSaveType Type])
```

### Parameters - saveImage

fileName  
An ImageSaveType that enables you to specify that the file should be saved as a different format from that specified by the file extension; optional.

<!-- -->

Type  
An ImageSaveType that enables you to specify that the file should be saved as a different format from that specified by the file extension; optional.

### Return Value - saveImage

0 if the method was successful.

### Remarks - saveImage

The possible values for the Type parameter are those available in the ImageSaveType system enum. For example, you could save test.bmp as a .jpg file.

|     |                |
|-----|----------------|
| 0   | Use\_Extension |
| 1   | BMP            |
| 2   | GIF            |
| 3   | JPG            |
| 4   | PNG            |
| 5   | TIFF           |
| 6   | BMP\_UNCOMP    |
| 7   | TIF\_UNCOMP    |

### Examples - saveImage

The following example captures part of the screen to a file, and then loads that image.

```xpp
Image img = new Image(); 
img.captureScreen(0, 0, 100, 100); 
img.saveImage(@'C:\test.bmp'); 
img.loadFile(@'C:\test.bmp');
```

## Method saveType

Gets or sets the image decoder.

```xpp
public ImageSaveType saveType([ImageSaveType Type])
```

### Parameters - saveType

Type  
The type of decoder that you want to set; optional.

### Return Value - saveType

### Remarks - saveType

The possible values for the Type parameter are those available in the ImageSaveType system enum:

|     |                |
|-----|----------------|
| 0   | Use\_Extension |
| 1   | BMP            |
| 2   | GIF            |
| 3   | JPG            |
| 4   | PNG            |
| 5   | TIFF           |
| 6   | BMP\_UNCOMP    |
| 7   | TIF\_UNCOMP    |

## Method setPixel

Sets the color for the pixel that is specified by the x and y parameters.

```xpp
public int setPixel(int x, int y, int pixel)
```

### Parameters - setPixel

x  
The ARGB value of the color that you want to use.

<!-- -->

y  
The ARGB value of the color that you want to use.

<!-- -->

pixel  
The ARGB value of the color that you want to use.

### Return Value - setPixel

0 indicates success; otherwise, failure.

### Remarks - setPixel

To convert an RGB color value to an ARGB value, use the Image::rgb Method.

## Method transparent

Sets the transparent color for the image.

```xpp
public int transparent([boolean Set], [int RValue], [int GValue], [int BValue])
```

### Parameters - transparent

Set  
Blue value of the color that you want to set; optional.

<!-- -->

RValue  
Blue value of the color that you want to set; optional.

<!-- -->

GValue  
Blue value of the color that you want to set; optional.

<!-- -->

BValue  
Blue value of the color that you want to set; optional.

### Return Value - transparent

0 to indicate success; otherwise, failure.

### Remarks - transparent

If any of the input parameters are missing, the color at the point (0,0) in the image is used. If you want to specify a color, this is expressed as an RGB color by using parameters 2 to 4.

## Method width

Retrieves the width of the image in pixels.

```xpp
public int width()
```

### Return Value - width

An integer that represents the width of the image in pixels.

### Examples - width

The following example prints out the width of the image in the test.bmp file.

```xpp
Image img = new Image(); 
img.loadFile(@'C:\test.bmp'); 
print img.width(); 
pause;
```

## Method canLoad

Determines whether an image file exists and can be opened.

```xpp
public static int canLoad(str filename)
```

### Parameters - canLoad

filename  
The name and path of the file to check.

### Return Value - canLoad

1 if the image is found and can be opened; otherwise, 0.

## Method loadExt

Retrieves a list of the extensions of the file formats that are supported by the Image class.

```xpp
public static container loadExt(int idx)
```

### Parameters - loadExt

idx  

### Return Value - loadExt

A container that holds a list of the supported file formats.

## Method resourceType

Determines whether a particular resource is a bitmap or an icon.

```xpp
public static int resourceType(int resourceIdx)
```

### Parameters - resourceType

resourceIdx  
The ID of the resource that you want to load.

### Return Value - resourceType

0 if the image is a bitmap; 1 if it is an icon.

### Remarks - resourceType

The values of resources can be found in the Resources macro.

### Examples - resourceType

The following example tests whether resource 3020 is an icon or a bitmap.

```xpp
Resource 
print Image::resourceType(3020); 
pause;
```

## Method rgb

Converts an RGB value to an ARGB value.

```xpp
public static int rgb(int R, int G, int B)
```

### Parameters - rgb

R  
The blue value of the color.

<!-- -->

G  
The blue value of the color.

<!-- -->

B  
The blue value of the color.

### Return Value - rgb

An integer that represents the ARGB value of the color that is specified by the parameters.

## Method validResource

Determines whether the resource specified by the id parameter is valid.

```xpp
public static int validResource(int id)
```

### Parameters - validResource

id  
The ID of the resource that you want to check.

### Return Value - validResource

0 if the ID is valid.

## Method new

Creates a new image.

```xpp
public void new([AnyType image], [int width], [int height])
```

### Parameters - new

image  
The height of the image in pixels; optional.

<!-- -->

width  
The height of the image in pixels; optional.

<!-- -->

height  
The height of the image in pixels; optional.

### Remarks - new

You do not need to specify any parameters, but it is possible to specify the image contents and size. For the image parameter, you can specify a file name and location, a resource, a particular image in an array, or another Image object.

### Examples - new

The following examples illustrate how you can optionally specify the existing content for the new image object.

```xpp
Image img1 = new Image(@"C:\MyPicture.jpg", 100, 100); 
Image img2 = new Image(121,100, 100); // Uses resource 121 in Ax32.exe 
Image img4 = new Image(img1, 200, 200);
```

## Method displayOrign

Enables you to specify an offset (X, Y) from the original origin (0, 0).

```xpp
public void displayOrign(int Xpos, int Ypos)
```

### Parameters - displayOrign

Xpos  
New Y (vertical) coordinate for the origin.

<!-- -->

Ypos  
New Y (vertical) coordinate for the origin.

## Method finalize

```xpp
public void finalize()
```

