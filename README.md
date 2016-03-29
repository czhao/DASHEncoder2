# DASHEncoder2
Tool to generated DASH content using config file or command line, modified from itec's DASHEncoder which is not maintained by them any more. 一个可以生成DASH媒体内容和MPD的工具

This is not designed for production yet but a good alternative to explore the DASH encoding. 

# HOW TO
You can either use Visual Studio or Clion to work on the build. 

Assume you build the code on directory /bin. Copy the configuration file `DASHEncoder.config` to the same directory. 

```
./DASHEncoder
```

Check the output in the destination directory. 

# Test the MPD output

For simplicity, you can start a simple http server via

```
python -m SimpleHTTPServer
```

And then serve the file via browser with [Dash JS](https://github.com/Dash-Industry-Forum/dash.js/wiki) support library. A skeletion is shown below

```
<html>
  <body>
	<script src="http://cdn.dashjs.org/latest/dash.all.min.js"></script>
   <style>
    video {
       width: 640px;
       height: 360px;
    }
   </style>
<body>
  <div>
    <h3>Http Adaptive Video Streaming Demo</h3>
  </div>
   <div>
       <video data-dashjs-player autoplay src="test.mpd" controls></video>
   </div>
</body>
  </body>
</html>
```

Alternatively you can test with [ExoPlayer](https://github.com/google/ExoPlayer/tree/master/demo) demo on Android. 


# Dependencies:
MP4Box and FFmpeg

Install the mp4box via homebrew

```
brew install mp4box
```

Install the ffmpeg via homebrew

```
brew install ffmpeg
``` 

# Issues

- Frame dropping in the final output and the video quality is lower than expected. 
- As there is no actual work done via C++ implementation, a python-based implementation is entirely possible.