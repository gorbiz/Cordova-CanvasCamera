# [CanvasCamera](http://github.com/daraosn/Cordova-CanvasCamera)
### for iOS PhoneGap / Cordova
***

Plugin to capture Camera streaming into a HTML5 Canvas or an IMG tag.

It uses *AVCaptureVideoDataOutput* to create a capture session. Each frame is base64 encoded and passed to the Cordova *UIWebView*. Please note this is mostly experimental and is slower than any native approach.

### How to Install
***
`cordova plugin add https://github.com/gorbiz/Cordova-CanvasCamera.git`

### How to Use
***

Configuration for ````<img>````:

    <img id="camera" width="352" height="288" />
    <script>
      CanvasCamera.capture = function(data) {
        document.getElementById('camera').src = data;
      }
    </script>

Configuration for ````<canvas>````: 

    <canvas id="camera" width="352" height="288"></canvas>
    <script>
        var context = document.getElementById('camera').getContext("2d");
        var camImage = new Image();
        camImage.onload = function() {
          context.drawImage(camImage, 0, 0);
        };
        CanvasCamera.capture = function(data) {
          camImage.src = data;
        };
    </script>

Start capture:

    <script>
      document.addEventListener("deviceready", function() {
        CanvasCamera.start();
      });
    </script>


### Known Issues & Roadmap/TODO
***

* Capture has some delay. This could be improved using another approach instead of base64 JPEG encoding.
* Capture runs at low quality (352x288), but this can be changed using a different *sessionPreset*.
* Missing configuration options for fps, quality, orientation, size, formats, etc.


### Author & Contributions
***

Diego Araos <d@wehack.it>

Feel free to fork & contribute!

### License
***

MIT
