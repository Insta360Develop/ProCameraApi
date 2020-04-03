## Overview

State polling is used both for heartbeat and receiving notification from camera.

Camera will disconnect the client after 10s without receiving `state` command. Generally, we suggest sending `state` command every 1 second, do not send the next `state` command before the previous one respond.



Except [required headers](commands/overview.md),  `state` command do not needs any param.



## State Response

```json
{
  "_battery":{
    "battery_level":float,
    "battery_charge":bool
  },
  "_idRes": [int], // array of finished async command sequence
  "_external_dev":{
    "entries":[string],//array of filepath on camera main storage
    "save_path":string //default save_path
  },
  "_cam_state":int, //camera state mask
  "_gps_state":int, //0: no device; 1: no location, 2: 2d location; 3: 3d location
  "_tl_info":{//information for timelapse
    "tl_count":int //count of pictures taken
  },
  "_snd_state":{//microphone information
    "dev_name":string, //name of the microphone device
    "type":int, //mic type,0:none;1:built-in mic; 2: 3.5mm mic; 3: usb mic; -1: unknown
    "is_spatial":bool //whether it is a spatial mic
  },
  "_left_info":{//estimated storage information
    "_rec_left_sec":int, //left recording time in current recording mode, in seconds.
    "_live_rec_left_sec":int,//left recording time in live+recording mode, in seconds.
  },
  "fan_level":int //fan level of the camera
}
```





