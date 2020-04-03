## Overview

Insta360 Pro series camera has 2 live mode, `normal` and `origin live`.  

For `normal` mode, the camera push a single stitched equirectangular/cube mapped stream. This is the most commonly used live mode, but with a maximum resolution of 3840x3840 due to on-board stitching limit.

For `origin live` mode, the camera push multiple fisheye stream(one for each lens). This mode is mainly used for out-camera stitching, and the resolution goes up to 8K, and even 11k for titan (requires the client hardware be able to do the stitching real-time).



## Request

`stiching` is only available in `normal` mode, do not pass `stiching` in `origin live` mode

```json
{
  "name": "camera._startLive",
  "parameters":{
    "origin":{
      "mime":string,
      "width":int,
      "height":int,
      "framerate":float,
      "bitrate":int,
      "logMode":int, 
      "liveUrl":string,//only available in origin live mode, pass rtmp url without stream name. eg. rtmp://127.0.0.1/live
      "saveOrigin":bool 
    },
    "stiching":{ //stitching is only needed in normal mode, do not pass this param for origin live mode
      "mode":sting,
      "mime":string,
      "width":int,
      "height":int,
      "framerate":int,
      "bitrate":int, 
      "map":string, 
      "_liveUrl":string, //rtmp url, like rtmp://127.0.0.1/live/test
      "liveOnHdmi":bool, 
      "fileSave":bool //save live stream on the camera.
    },
    "audio":{
      "mime":string,
      "sampleFormat":string,
      "channelLayout":string,
      "samplerate":int,
      "bitrate":int
    }
  },
  "autoConnect":{
    "enable":bool, 
    "interval":int, // retry delay in ms.
    "count":int //count = -1 means always try to reconnect
  }
  “stabilization”:bool
}
```



## Response

```json
{
  "name":"camera._startLive",
  “state”:"done",
  "results":{"_liveUrl":string}
}
```

For `origin live` mode, if the `liveUrl` you specified is rtmp://{host}/{app_name}, then you could access streams by the url rtmp://{host}/{app_name}/origin{i} where i=1,2,3,4,5,6,(7,8 for titan).