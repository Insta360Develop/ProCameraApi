## Overview

`take_picture` command handles picture taking, including normal picture, burst, HDR, bracket.

## Request

```json
{
  "name": "camera._takePicture",
  "parameters":{
    "origin":{
      "mime":string, 
      "width":int, 
      "height":int,
      "saveOrigin":bool,
      "storage_loc":int //works for Titan,0:save on TF card 1：save on Main storage
    },
    "stiching":{
      "mode":string, 
      "mime":string, 
      "width":int, 
      "height":int, 
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

`take_picture` is an async command. View [async command handling]() to learn how to handle the result.

```json
{
  "name": "camera._takePicture",
  "state": "done",
  "sequence":int //sequence id for async handling
}
```

