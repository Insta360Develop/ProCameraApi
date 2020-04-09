## Overview

`start_record` command start recording.

## Reqeust

```json
{
  "name": "camera._startRecording",
  "parameters":{
    "origin":	{
      "mime":string,
      "width":int,//single fisheye image width and height, eg. 3840 x 2160,3840x2880
      "height":int,
      "framerate":int,
      "bitrate":int,
      "logMode":int,
      "hdr":bool,
      "saveOrigin":bool,
      "storage_loc":int //0:save on TF card 1：save on main storage,default 0
    },
    "stiching":	{
      "mode":sting,
      "mime":string,
      "width":int,//stitched video size, no more than 4k, like 3840x1920.
      "height":int,
      "framerate":int,
      "bitrate":int,
    },
    "audio":{
      "mime":string,
      "sampleFormat":string,
      "channelLayout":string,
      "samplerate":int,
      "bitrate":int
    }
	}
}
```

