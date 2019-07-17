
## About the benchmark

The Web Latency Benchmark is a new kind of benchmark that tests your browser's responsiveness by directly measuring *latency* 

## How it works

The Web Latency Benchmark works by programmatically sending input events to a browser window, and using screenshot APIs to detect when the browser has finished drawing its response.

There are two main components: the latency-benchmark server (written in C/C++) and the HTML/JavaScript benchmark page. The HTML page draws a special pattern of pixels to the screen using WebGL or Canvas 2D, then makes an XMLHTTPRequest to the server to start the latency measurement. The server locates the browser window by searching a screenshot for the special pattern. Once the browser window is located, the server starts sending input events. Each time the HTML page receives an input event it encodes that information into pixels in the on-screen pattern, drawn using the canvas element. Meanwhile the server is taking screenshots every few milliseconds. By decoding the pixel pattern the server can determine to within a few milliseconds how long it takes the browser to respond to each input event.

The native reference test is special because it requires extra support from the server. Using the native APIs of each platform, the server creates a special benchmark window that draws the same pattern as the test webpage, and responds to keyboard input in the same way. To ensure fairness when compared with the browser, this window is opened in a separate process and uses OpenGL to draw the pattern on the screen. The benchmark window opens as a popup window, only 1 pixel tall and without a border or title bar, so it's almost unnoticeable.

## License and distribution

The Web Latency Benchmark is licensed under the Apache License version 2.0. This is an open source project; it is not an official Google product.

