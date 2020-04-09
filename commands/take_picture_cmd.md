## Overview

`take_picture` command handles picture taking, including normal picture, burst, HDR, bracket.

## Request

```json
{
  "name": "camera._takePicture",
  "parameters":{
    "origin":{
      "mime":string, 
      "width":int, //single fisheye image width, eg. 4000
      "height":int,//single fisheye image height, eg. 3000
      "saveOrigin":bool,
      "storage_loc":int //works for Titan,0:save on TF card 1：save on Main storage
    },
    "stiching":{
      "mode":string, 
      "mime":string, 
      "width":int, //stitched image width, eg. 8000
      "height":int, //stitched image height, eg.4000
      "map":string, 
      "algorithm":string //on-board stitching algorithm, available values are "opticalFlow" and "normal",default "normal"
    },
    "burst":{"enable":bool, "count":int},//available for burst mode
    "hdr":{"enable":bool, "count":int, "min_ev":int, "max_ev":int}, // available for hdr mode, currently only support 3 pictures
    "bracket":{"enable":bool, "count":int, "min_ev":int, "max_ev":int}, //available for bracket mode
    "delay":int,//delay in second before the camera actually execute the take picture command
  }
}
```



## Response

`take_picture` is an async command. View [Async command handling](../async_command_handling.md) to learn how to handle the result.

```json
{
  "name": "camera._takePicture",
  "state": "done",
  "sequence":int //sequence id for async handling
}
```

