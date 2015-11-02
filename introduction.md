# Introduction

***

Quartz 2D is **resolution-and-device-independent**; you don’t need to think about the final destination when you use the Quartz 2D application programming interface (API) for drawing.

# Overview of Quartz 2D

***

### Drawing Destinations:The Graphics Context

**A graphics context** is an opaque data type (CGContextRef) that encapsulates the information Quartz uses to draw images to an output device, such as a PDF file, a bitmap, or a window on a display. The information inside a graphics context includes graphics drawing parameters and a device-specific representation of the paint on the page.

<br>
These **graphics contexts** are available to your application:

* A bitmap graphics context
* A PDF graphics context
* A window graphics context
* A layer context(**CGLayerRef**)

### Quartz 2D Opaque Data Types

The **opaque data types** available in Quartz 2D include the following:

* **CGPathRef**, used for vector graphics to create paths that you fill or stroke;
* **CGImageRef**, used to represent bitmap images and bitmap image masks based on sample data that you supply;
* **CGLayerRef**, used to represent a drawing layer that can be used for repeated drawing (such as for backgrounds or patterns) and for offscreen drawing;
* **CGPatternRef**, used for repeated drawing;
* **CGShadingRef** and **CGGradientRef**,usedtopaintgradients;* **CGFunctionRef**, used to define callback functions that take an arbitrary number of floating-point arguments. You use this data type when you create gradients for a shading;
* **CGColorRef** and **CGColorSpaceRef**, used to inform Quartz how to interpret color;* **CGImageSourceRef** and **CGImageDestinationRef**, which you use to move data into and out of Quartz;* **CGFontRef**, used to draw text;* **CGPDFDictionaryRef**, **CGPDFObjectRef**, **CGPDFPageRef**, **CGPDFStream**, **CGPDFStringRef**, and **CGPDFArrayRef**, which provide access to PDF metadata;* **CGPDFScannerRef** and **CGPDFContentStreamRef**, which parse PDF metadata;* **CGPSConverterRef**, used to convert PostScript to PDF.
### Graphics StatesTo save the current graphics state, use the function **CGContextSaveGState** to push a copy of the current graphics state onto the stack. To restore a previously saved graphics state, use the function **CGContextRestoreGState** to replace the current graphics state with the graphics state that’s on top of the stack.

The graphics state parameters that are saved when you call this function are listed below:

* Current transformation matrix (CTM)
* Clipping area
* Line: width, join, cap, dash, miter limit
* Accuracy of curve estimation (flatness)
* Anti-aliasing setting
* Color: fill and stroke settings
* Alpha value (transparency)
* Rendering intent
* Color space: fill and stroke settings
* Text: font, font size, character spacing, text drawing mode
* Blend mode

### Quartz 2D Coordinate Systems

Quartz accomplishes device independence with a separate coordinate system—user space—mapping it to the coordinate system of the output device—device space—using the **current transformation matrix, or CTM**.

The current Quartz 2D Coordinate Systems transformation matrix is a particular type of matrix called an **affine transform**, which maps points from one coordinate space to another by applying **translation**, **rotation**, and **scaling** operations (calculations that move, rotate, and resize a coordinate system).

### Memory Management: Object Ownership

Quartz uses the Core Foundation memory management model, in which objects are reference counted.

There are a few simple rules to keep in mind:

* If you create or copy an object, you own it, and therefore you must release it. That is, in general, if you obtain an object from a function with the words “Create” or “Copy” in its name, you must release the object when you’re done with it. Otherwise, a memory leak results.
* If you obtain an object from a function that does not contain the words “Create” or “Copy” in its name, you do not own a reference to the object, and you must not release it. The object will be released by its owner at some point in the future.
* If you do not own an object and you need to keep it around, you must retain it and release it when you’re done with it. You use the Quartz 2D functions specific to an object to retain and release that object. For example, if you receive a reference to a **CGColorspace** object, you use the functions **CGColorSpaceRetain** and **CGColorSpaceRelease** to retain and release the object as needed. You can also use the Core Foundation functions **CFRetain** and **CFRelease**, but you must be careful not to pass **NULL** to these functions.






