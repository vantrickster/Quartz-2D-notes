# Graphics Contexts

***

### Drawing to a View Graphics Context in IOS

To draw to the screen in an iOS application, you set up a **UIView** object and implement its `drawRect:` method to perform drawing. The view’s `drawRect:` method is called when the view is visible onscreen and its contents need updating. You obtain this graphics context in your `drawRect:` method by calling the **UIKit** function `UIGraphicsGetCurrentContext`.

### Creating a PDF Graphics Context

The Quartz 2D API provides two functions that create a PDF graphics context:

* `CGPDFContextCreateWithURL`, which you use when you want to specify the location for the PDF output as a Core Foundation URL.
* `CGPDFContextCreate`, which you use when you want the PDF output sent to a data consumer.

A PDF graphics context in iOS uses the default coordinate system provided by Quartz, without applying a transform to match the UIKit coordinate system.

### Creating a Bitmap Graphics Context

A bitmap graphics context accepts a pointer to a memory buffer that contains storage space for the bitmap. When you paint into the bitmap graphics context, the buffer is updated. After you release the graphics context, you have a fully updated bitmap in the pixel format you specify.

You use the function `CGBitmapContextCreate` to create a bitmap graphics context.This function takes the following parameters:

* **data**. Supply a pointer to the destination in memory where you want the drawing rendered. The size of this memory block should be at least (bytesPerRow*height) bytes.
* **width**. Specify the width, in pixels, of the bitmap.
* **height**. Specify the height, in pixels, of the bitmap.
* **bitsPerComponent**. Specify the number of bits to use for each component of a pixel in memory. For example, for a 32-bit pixel format and an RGB color space, you would specify a value of 8 bits per component.
* **bytesPerRow**. Specify the number of bytes of memory to use per row of the bitmap.
* **colorspace**. The color space to use for the bitmap context. You can provide a Gray, RGB, CMYK, or NULL color space when you create a bitmap graphics context.
* **bitmapInfo**. Bitmap layout information, expressed as a CGBitmapInfo constant, that specifies whether the bitmap should contain an alpha component, the relative location of the alpha component (if there is one) in a pixel, whether the alpha component is premultiplied, and whether the color components are integer or floating-point values.

##### Supported Pixel Formats(IOS)

The pixel format is specified as bits per pixel (bpp) and bits per component (bpc).

Color Space | Pixel format and bitmap information constatn | 
:---: | :----------------------------: |
Null  | 8 bpp, 8 bpc, kCGImageAlphaOnly|
Gray  | 8 bpp, 8 bpc,kCGImageAlphaNone |
Gray  | 8 bpp, 8 bpc,kCGImageAlphaOnly |
RGB   | 16 bpp, 5 bpc, kCGImageAlphaNoneSkipFirst |
RGB   | 32 bpp, 8 bpc, kCGImageAlphaNoneSkipFirst |
RGB   | 32 bpp, 8 bpc, kCGImageAlphaNoneSkipLast  |
RGB   | 32 bpp, 8 bpc, kCGImageAlphaPremultipliedFirst |
RGB   | 32 bpp, 8 bpc, kCGImageAlphaPremultipliedLast  |

##### Anti-Aliasing

Bitmap graphics contexts support **anti-aliasing**, which is the process of artificially correcting the jagged (or aliased) edges you sometimes see in bitmap images when text or shapes are drawn.

You can turn anti-aliasing off for a particular bitmap graphics context by calling the function `CGContextSetShouldAntialias`. The anti-aliasing setting is part of the graphics state.

You can control whether to allow anti-aliasing for a particular graphics context by using the function `CGContextSetAllowsAntialiasing`.

### Obtaining a Graphics Context for Printing

(nothing :] )










