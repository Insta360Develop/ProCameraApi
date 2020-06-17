## Overview

`start_preview` command tells the camera to push an rtmp preview stream. 

## Request

For any capture command, `origin` , `stiching` and `audio` are three common params. 

`origin` describes the capture options of each lens. Generally, it looks like this:

```json
{
  "mime":string,//mime type of the output, might be "h264","h265" for video, "jpeg","raw" for image,
  "width":int,
  "height":int,
  "framerate":float,
  "bitrate":float, //bitrate in Kbps
  "saveOrigin":bool //whether to save the separated fisheye origin video/image.
}
```

`stiching` describes the output of on-board stitching

```json
{
  "mode":string,//stitching mode,"pano" for mono 360 video,"3d_top_left" for stereo 360 with top/bottom layout, left eye on top. "3d_top_right" for stereo 360 with top/bottom layout, right eye on top.
  "mime":string,//mime type of the output, "h264" for video,"jpeg" for image
  "width":int,
  "height":int,
  "framerate":float,
  "bitrate":float//bitrate in Kbps
}
```

**NOTE**: The name of the attribute is `stiching`, not `stitching`. I know it is a typo, for compatiblility consideration, we kept it.

`audio` describes the audio options

```json
{
  "mime":'aac', 
  "sampleFormat":'s16',
  "channelLayout":'stereo',
  "samplerate":48000,
  "bitrate":128
}
```

`stiching` for `start_preveiw` is required. Here is the sample of `start_preview` request

```json
{
  "name": "camera._startPreview",
	"parameters":{
    "origin":{
      "mime":"h264",
      "width":1920,
      "height":1440,
      "framerate":30,
      "bitrate":20480 //Kbps
	   },
    "stiching":{
      "mode":"pano",
      "mime":"h264",
      "width":3840,
      "height":1920,
      "framerate":30, //should be the same as origin.framerate
      "bitrate":10240 //Kbps
    },
	},
    "stabilization":true //whether apply stabilization on preview.
}
```



## Response

The response contains the absolute rtmp url for playnback. 

```json
{
	"name":"camera._startPreview",
	"state":"done",
	"results":{
    "_previewUrl":string 
  }
}
```

