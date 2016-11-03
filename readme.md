# CanvaWork.js #

### A tool for:
- Reading image files and converting to usable canvas element
- Applying a watermarks to your processed images
- Resize canvas by precentage
- Resize canvas to 3 images based of "Big", "Med" & "Thumb" option sizes

### Conversions:
- Converting 1 or mulitple canvas to base64
- Converting 1 or mulitple  canvas to blob
- Converting 1 or mulitple  base64 to canvas
- Converting 1 or mulitple  base64 to blob
- Converting 1 or mulitple  blob to canvas
- Converting 1 or mulitple  blob to base64

## Code ##

**Include before closing the body element**
```php
<script src="https://code.jquery.com/jquery-3.1.1.min.js" crossorigin="anonymous"></script>
<script src="../src/canvawork.min.js"></script>
```

**Initialize**
```php
var options = {
    file: "", // src to the file you would like to work with as main canvas
    watermark_file: "", // src to the watermark file, must be appropriately sized and have transparency already applied to image
    watermark: false, // To watermak or not to watermark
    sizes:{ // Your 3 image sizes, set these accordingly
        big:{
            width: 1200,
            height:400,
            watermark_decrease: 80
        },
        med:{
            width: 600,
            height:200,
            watermark_decrease: 50
        },
        thumb:{
            width: 300,
            height:100,
            watermark_decrease: 30
        }
    },
    file_type:"image/png", // Png, Jpeg, etccc
    file_quality:"1.0",
    debug: true
}
var CanvaWork = new CanvaWork(options);
```

**Load image to use as canvas**
```php
CanvaWork.loadImage("yourimage.png", function(obj){
    console.log(obj.canvas);  // The usable canvas
    console.log(obj.width);
    console.log(obj.height);
    console.log(obj.image); // Contains the image file
});
```

**Resize loaded canvas by precentage**
```php
CanvaWork.canvasResizePrecent(obj.canvas, 50, function(canvas){
    // "canvas" variable will now have a canvas reduced to 50% of the size
});
```

**Resize loaded canvas to all sizes**
```php
CanvaWork.canvasResizeAll(obj.canvas, function(canvases){
    // "canvases" will be an array containing 3 canvases with different sizes depending on initial options
});
```

**Apply watermark to loaded canvas from image**
```php
CanvaWork.canvasToBase64(obj.canvas, function(base64){
    CanvaWork.base64ToCanvas(base64, function(canvas){
        // By passing the canvas through the "base64ToCanvas" function will apply the watermark if active in options
    });
});

```

## Demos ##
The following demos should get you started:

- Load image and apply watermark [Demo1](https://github.com/vnbenny/canvawork.js/blob/master/demos/load-image-and-apply-watermark.html).
- Load image and convert multiple [Demo2](https://github.com/vnbenny/canvawork.js/blob/master/demos/load-image-and-convert-multiple.html).
- Load image and convert [Demo3](https://github.com/vnbenny/canvawork.js/blob/master/demos/load-image-and-convert.html).
- Load image and resize precentage [Demo4](https://github.com/vnbenny/canvawork.js/blob/master/demos/load-image-and-resize-precentage.html).
- Load image and resize all [Demo5](https://github.com/vnbenny/canvawork.js/blob/master/demos/load-image-and-resizeall.html).

## License
MIT
