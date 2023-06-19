---
title: Images on a page or in a grid
description: This article describes the steps for displaying images on a page or in a grid.
author: jasongre
ms.date: 07/09/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 58e6476b-c29f-46c4-8866-78ca4ab3c0bc
---

# Images on a page or in a grid

[!include [banner](../includes/banner.md)]

This article describes the steps for displaying images on a page or in a grid. The article also provides background about some of the ways that images can be used, and the APIs that are used.  

> [!NOTE]
> For accessibility, when you use an image to indicate status or show data, the image must be accompanied by a tooltip, enhanced preview, label, or other textual representation that describes the value or status that the image represents. 

Finance and Operation apps do not use embedded resources for images. Instead, it uses lightweight symbols. The coding pattern has changed slightly to support the new image control. 

For ImageList uses, the runtime accepts the old **ImageID** value and maps it to a symbol, so that existing code continues to work.

> [!NOTE]
> In some cases, there is no image even after runtime mapping, and this behavior is intentional. 

AX 2012 displays images in a grid column to indicate status. These images were sometimes retrieved from embedded resources that are no longer available. 

AX 2012 offers the following storage options for images:

-   An embedded resource where images are offered as part of the kernel itself
-   An Application Object Server (AOS) resource where developers or independent software vendors (ISVs) can add their own image resources
-   A file location where developers or ISVs can load images at run time
-   A database field that is stored as a bitmap

The following storage options are available for images:

-   An AOS resource where developers or ISVs can add their own image resources
-   A URL location where developers or ISVs can load images at run time
-   A database field that is stored as a container.
-   A symbol font, where images are rendered by name from the font

Images that are stored as AOS resources allow for the use of an image that isn't categorized as user data, and can be used with your application. 

> [!NOTE]
> If there are legacy embedded resource images that UX has approved for use, those embedded images can be manually transferred to an AOS resource and used. 

A typical web application maintains a collection of images on an Internet Information Services (IIS) server and just provides a URL to the image. Although this approach is supported, we don't expect that it will be used very much. Instead, we expect that the symbol font will be used as an image source. 

Of course, application logic will store an image in a database to allow for strong employee photos, product images, and so on, and this approach is a first-class experience. 

A symbol font is the most performant and scalable image format. We expect that characters from the symbol font will be used for most application use cases (grid row by row status, button images, and so on). 

For the list of symbols that are available in the symbol font, see [Symbol font](symbol-font.md).

## Image type: Symbol

| Pros | Cons |
|---|---|
| <ul><li>Usually, the symbol font is the smallest payload to send to the client.</li><li>You can easily customize the images by using Cascading Style Sheets (CSS).</li><li>The symbol font should already be cached on the user's computer. Therefore, no extra bandwidth is used, and there are no additional network requests that might slow down page loads.</li><li>Colors can be controlled by themes.</li><li>The images are automatically scaled on high-DPI displays.</li></ul>|A limited number of framework-defined symbols is available. |

### Design time
<strong>Image location:</strong> Symbol <strong>Typical image:</strong> &quot;Person&quot;

### Run time
Sometimes, you don't have an image for a particular record in a grid, but you don't want an empty space where the image should be. The following example shows how you can use a display method to check for an image value, and then substitute a placeholder image instead.

```xpp
public display container customerImage()
{
    container imageContainer = this.Image;
    if (imageContainer == connull())
    {
        // there is no image… the container is null
        // show a generic person outline image
        ImageReference imageReference = 
            ImageReference::constructForSymbol(ImageReferenceSymbol::Person);
        imageContainer = imageReference.pack();
    }
    return imageContainer;
}
```

## Image type: AOT Resource

| Pros | Cons |
|---|---|
| In addition to the pros of using URL images (see the next section), AOT resources are modeled and managed by the development tools. | A   limited number of framework-defined images is available. |

### Design time
| You just create a new resource and then save the image into the Application Object Tree (AOT) resource. When you model your image control on a page, you specify the resource name, not the image name. This approach is typically used for legacy images (icons) that don’t have equivalents in the symbol font. <strong>Image location:</strong> AOTResource <strong>Typical image:</strong> &quot;ResourceMicrosoft Dynamics AX&quot; (a .jpg is added to resources) |

### Run time

```xpp
public display container imageDataMethod()
{
    ImageReference imageReference =
        ImageReference::constructForAotResource(
            'ResourceMicrosoft Dynamics AX');
    return imageReference.pack();
}
```

## Image type: URL Image

| Pros | Cons |
|---|---|
| <ul><li>This approach provides an easy way to reference any image anywhere on web.</li><li>This approach supports full-color images.</li><li>The web browser can cache the image, based on the settings of the server that hosts the image.</li></ul> | <ul><li>The transfer size isn’t as small as it is for symbols, but it's reasonable. The URL is sent as a string for each control that uses the image. The browser then downloads the image from the URL, and from that point, standard browser caching rules apply.</li><li>You can’t easily theme the images by using CSS.</li><li>Unless the URL points to a Scalable Vector Graphics (SVG) file, the image isn't automatically scaled on high-DPI displays.</li></ul> |

### Run time

The following example shows an image that uses a URL that is contained in a string.

```xpp
public display container imageDataMethod()
{
    ImageReference imageReference = 
        ImageReference::constructForUrl(this.ImageURL);
    return imageReference.pack();
}
```

This code sends a small JavaScript Object Notation (JSON) message to the control on the client. This message instructs the control to treat the image as a URL and let the browser do the work of downloading the image. No download occurs on the server. <strong>Storing an image URL in a database table</strong> You can also have a container field for the image column on your table. You can then use code that resembles the following example to store the <strong>ImageReference</strong> pack.

```xpp
CLIControls_ImageTable imageTable;
ttsbegin;
ImageReference imageReference = 
    ImageReference::constructForUrl(
        'http://dynamics/PublishingImages/ERPLogos/DynamicsLogo.jpg');
imageTable.ImageField = imageReference.pack();
imageTable.insert();
ttscommit;
```

This code causes the user’s browser to download the image from the specified URL. The use of ImageReference involves some overhead, but this approach lets you use a single application programming interface (API) to handle images that are created from binary data, URLs, AOT resources, or symbols. You can even mix and match image types between rows of data.


## Image type: Binary Image

| Pros | Cons |
|---|---|
| Usually, this approach offers the easiest migration if the <strong>Image</strong> class in X++ was already used, or if binary images were previously stored in the database. | <ul><li>This approach involves the largest transfer size, because the binary image is encoded as a string and sent to the client as part of the interaction.</li><li>The browser can't cache the images.</li><li>For a grid, the binary-encoded image is sent for every row, even if multiple rows use the same image. Therefore, this approach can lead to very large transfer sizes in the interactions.</li><li>You can't easily theme the images by using CSS.</li><li>The images aren't automatically scaled on high-DPI displays.</li></ul> |

| Design time | Run time |
|---|---|
| <strong>Using a database field</strong> This approach is typically used to display data, such as employee pictures and product images. You can bind directly to a field, or you can use a display method. Data Source Data Field Data Method | Typically, the images are loaded from database, and no additional code is required. For cases where the image is managed in a data method, see the data method examples. |

## Display methods and images (three return types)
When you use a display method for an image type to show an image in a grid, three return types are understood by the image control that works with the framework. All three return types can be used to display an image.

-   Int (imagelist array index)
-   Container (image instance)
-   ResID (which is mapped to a symbol)

> [!NOTE]
> ResID and Int are the same return types. If the **imageList** property of the image control instance has been assigned an instance value, the display method return value is considered an array index into the imagelist. If the **imageList** property is **null**, the return value is used to map a legacy ResID to a symbol.

## Images in a grid and the legacy ImageList collection
In AX 2012 and earlier versions, a common use pattern for displaying images is to store an image as a resource or use a kernel-supplied image resource, and then at run time, extract that image and place it in a reusable collection that is known as an ImageList. The guidance is to use lighter-weight symbol images. You should rewrite all legacy code so that it uses symbols directly. You should also replace all code that uses the ImageList collection. If you don't make these changes, the legacy ImageList collection won't display images, because use of this collection relies on embedded (kernel) resources that no longer exist. Therefore, to support legacy code until it can be updated, the ImageList collection maps the ResID for an embedded resource to a new font-based symbol to help guarantee that any code that uses the ImageList collection will continue to run and provide an image.

## Using the imageList property for backward compatibility
An image control has a property that is named **imageList**. You pass in an instance of the ImageList collection to this property. In this way, the image is an array of images that you select via the array number.

```xpp
public void init()
{
    int imgCnt;
        
    // create an imagelist instance
    Imagelist imageList = new ImageList(
        ImageList::smallIconWidth(), 
        Imagelist::smallIconHeight());
        
    super();
        
    // add images to the instance (return value is not needed)
    // Note that a legacy ResID is used in the new Image contstructor. 
    // This is a compatibility mapping of resource to symbol.
    imgCnt = imagelist.add(new Image(#ImageInfo));
    imgCnt = imagelist.add(new Image(#ImageWarning));
    imgCnt = imagelist.add(new Image(#ImageError));
        
    // pass the image list instance to the control
    ImageListDM.imageList(imageList);
}
    
// at runtime, select the image you want to show: when the control has an imagelist instance, 
// this int value is used to index into that array
public display int imageListDataMethod()
{
    int imgCnt = imageCnt mod 3;
    imageCnt++;
    return imgCnt;
}
    
/*
    Note: The legacy image resource ID's #ImageInfo, #ImageWarning, #ImageError are 
    mapped from the legacy resource id to a symbol name in the X++
    class ImageLoader
*/
```

## Display method that returns an ImageRes (legacy image resource ID)

```xpp
// this is an example of backward compatibility the use of ImageRes will become obsolete
display ImageRes checkIfError(HRMCompEventEmpl _hrmCompEventEmpl)
{
    if (!_hrmCompEventEmpl.RecId)
    {
        return 0;
    }       
    if (_hrmCompEventEmpl.Status == HRMCompEventEmplStatus::Ignore   ||
        _hrmCompEventEmpl.Status == HRMCompEventEmplStatus::Approved ||
        _hrmCompEventEmpl.Status == HRMCompEventEmplStatus::Loaded)
    {
        return 0;
    }
    else
    {
        if (_hrmCompEventEmpl.ErrorStatus == HRMCompEventErrorStatus::Error)
        {
            return #ImageError;
        }
        if (_hrmCompEventEmpl.ErrorStatus == HRMCompEventErrorStatus::Warning)
        {
            return #ImageWarning;
        }
        if (_hrmCompEventEmpl.ErrorStatus == HRMCompEventErrorStatus::Info)
        {
            return #ImageInfo;
        }
    }      
    return 0;
}
```

## Display method that returns a container

```xpp
public display container checkIfError(HRMCompEventEmpl _hrmCompEventEmpl)
{
    ImageReference  imageReference;
    container       imageContainer;
    if (_hrmCompEventEmpl.RecId && _hrmCompEventEmpl.Status == HRMCompEventEmplStatus::Created)
    {
        switch (_hrmCompEventEmpl.ErrorStatus)
        {
            case HRMCompEventErrorStatus::Error:
                imageReference = ImageReference::constructForSymbol('Error');
                break;
            case HRMCompEventErrorStatus::Warning:
                imageReference = ImageReference::constructForSymbol('Warning');
                break;
            case HRMCompEventErrorStatus::Info:
                imageReference = ImageReference::constructForSymbol('Info');
                break;
        }
    }
    if (imageReference)
    {
        imageContainer = imageReference.pack();
    }
    return imageContainer;
}
```

## Obtaining and displaying an image from the user by using file upload
Model a page that has an image control and a **FileUpload** button.

```xpp
// model a new FileUpload control (style=minimal)
// class declaration
FileUpload uploadControl;
    
// form init() create a callback event handler to be notified when upload is complete
public void init()
{
    //when uploading an image, this method is called upon completion.
    uploadControl = FileUpload1;
    uploadControl.notifyUploadCompleted +=  eventhandler(this.UploadCompleted);
}
    
// form close() release the callback event handler
public void close()
{
    // when the form closes, release the eventhandler for file upload callback
    //  FileUpload uploadControl;
    super();
    //  uploadControl = FileUpload1;
    uploadControl.notifyUploadCompleted -=  eventhandler(this.UploadCompleted);
}
    
// when the upload completes, grab the image and store it in the database
/// <summary> 
/// This method is called by the file upload mechanism, when the upload completes
/// </summary>
public void UploadCompleted()
{
    Binary binaryImage;
    System.Net.WebClient webClient;
    System.IO.MemoryStream stream;
    String255 myUrl;
    if(uploadControl.uploadSuccess())
    {
        InteropPermission perm = new InteropPermission(InteropKind::ClrInterop);
        perm.assert();
            
        // BP Deviation Documented
        webClient = new System.Net.WebClient();
            
        // BP Deviation Documented
        // if success, downloadURL contains the path to the Azure blob location for the file
        stream = new System.IO.MemoryStream(webClient.DownloadData(uploadControl.downloadUrl()));
            
        // grab the data and assign to the image field
        binaryImage = Binary::constructFromMemoryStream(stream);
            
        // assign to the database field (type=container)
        FMVehicleModel.Image = binaryImage.getContainer();
            
        CodeAccessPermission::revertAssert();
    }
}
```

## Example of in-memory bitmap manipulation
In this example, an image is created from scratch. However, developers can also load a bitmap from an alternative source and then manipulate the image as desired (for example, by cropping, stretching, or resizing, or by changing the opacity). After any manipulation is completed, the developers can display the image by using the image control, or they can assign it to a data source field.

```xpp
public void clicked()
{
    Binary binaryImage;
    Image  image;
    int x,y;
        
    super();
        
    InteropPermission perm = new InteropPermission(InteropKind::ClrInterop);
    perm.assert();
        
    /* 
    In this example, we’ll create a bitmap programmatically, we’ll use a memory
    Stream o’bytes to then convert to the container format the image control expects.
    */
    System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(100,100);
    System.IO.MemoryStream myStream = new System.IO.MemoryStream();
        
    // draw some stuff (or load a bitmap from an alternative source)
    for( x=0; x < bitmap.Height; ++x)
    {
        for( y=0; y< bitmap.Width; ++y)
        {
            bitmap.SetPixel(x,y,System.Drawing.Color::White);
        }
    }
        
    for(x=0; x < bitmap.Height; ++x)
    {
        bitmap.SetPixel(x,x, System.Drawing.Color::Red);
    }
        
    // move our bitmap to an in memory stream
    bitmap.Save(myStream, System.Drawing.Imaging.ImageFormat::Bmp);
        
    // stream goes to raw binary
    binaryImage = Binary::constructFromMemoryStream(myStream);
        
    // create a blank image and copy our binary data to the image format
    image = new Image();
    image.setData(binaryImage.getContainer());
        
    // copy the image data to the image control
    MyImage.image(image);
        
    // alternatively, skip the image conversion step and assign directly to the data field
    binaryImage = Binary::constructFromMemoryStream(myStream);
        
    // assign to the database field (type=container)
    datafield.Image = binaryImage.getContainer();
        
    CodeAccessPermission::revertAssert();
}
```

## Additional examples (URL, binary, and symbol)
The following table explains two concepts: Image Class and FormImageControl.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Image Class</td>
<td>This class is a run-time representation of an image.</td>
<td>Four constructors:
<ul>
<li>Image::ConstructBinary(INT64Encode);</li>
<li>Image::ConstructSymbol(SymbolName);</li>
<li>Image::ConstructURL(URL);</li>
<li>Image::Construct(ResourceName);</li>
</ul></td>
</tr>
<tr class="even">
<td>FormImageControl</td>
<td>This control is used to add an image at run time.</td>
<td>.image(new image());</td>
</tr>
</tbody>
</table>

## Using a display method to show an image from a URL string
In this example, a display method is used to translate a string that contains a URL to the format that the image control expects.

```xpp
public display container imageDataMethod()
{
    ImageReference imageReference = 
        ImageReference::constructForUrl(this.ImageURL);
    return imageReference.pack();
}
```

This code sends a small JSON message to the control on the client. This message instructs the control to treat the image as a URL and let the browser do the work of downloading the image. No download occurs on the server.

## Using a display method to show a blank image
There might be times when you have no image for a particular record in a grid, but you don't want an empty space where the image should be. This example shows how you can use a display method to check for an image value and then substitute a placeholder image instead.

```xpp
public display container customerImage()
{
    container imageContainer = this.Image;
    if (imageContainer == connull())  // there is no image… the container is null
    {
        ImageReference imageReference =
            ImageReference::constructForSymbol(ImageReferenceSymbol::Person);  // show a generic person outline image
        imageContainer = imageReference.pack();
    }
    return imageContainer;
}

public display container statusImageDataMethod()
{
    ImageReference statusImage;
    if (this.Status == NoYes::Yes)
    {
        statusImage = 
            ImageReference::constructForSymbol(ImageReferenceSymbol::Accept);
    }
    else
    {
        statusImage = 
            ImageReference::constructForSymbol(ImageReferenceSymbol::Cancel);
    }
    return statusImage.pack();
}
```

## Taking an image URL and storing the image in table
You can have a container field for the image column on your table. You can then use code that resembles the following example to store the <strong>ImageReference</strong> pack.

```xpp
CLIControls_ImageTable imageTable;
ttsbegin;
ImageReference imageReference = 
    ImageReference::constructForUrl(
        'http://dynamics/PublishingImages/ERPLogos/DynamicsLogo.jpg');
imageTable.ImageField = imageReference.pack();
imageTable.insert();
ttscommit;
```

Like the display method that is described in the "Using a display method to show an image from a URL string" section, this code causes the user's browser to download the image from the specified URL. Although this approach involves some overhead, you can use a single API to handle images that are created from binary data, URLs, AOT resources, or symbols. You can even mix and match image types between rows of data.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
