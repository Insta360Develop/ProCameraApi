## Overview

`start_record` command start recording.

## Reqeust

```json
{
  "name": "camera._startRecording",
  "parameters":{
    "origin":	{
      "mime":string,
      "width":int,
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
      "width":int,
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

