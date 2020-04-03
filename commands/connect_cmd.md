## Overview

`connect` is the first command to execute. On success,  a session between camera and the client is established, during which  any other client is not able to connect to this camera.

## Request

`connect` needs the client to sync time with the camera. 

```json
{
  "name":"camera._connect",
  "parameters":{
    "hw_time":"MMDDhhmm[[CC]YY][.ss]",// utc time
    "time_zone":"GTM time zone str"
	}
}	
```

### Response

In the response, the camera returns basic information like `machine`(model name), `sys_info`(mostly version info), and information of current camera action, like recording options,stitching options, preview options, audio options and etc.

```json
{
  "name":"camera._connect",
  "state":"done",
  "machine":"pro2",//indicates camera model. this attribute is not presented in Pro, possible value are "pro2" and "titan"
  "results":{
    "Fingerprint":string, //identification of the session, should be passed in header in the following commands
    "_cam_state":int,
    "url_list":{
      "_liveUrl": string,
      "_previewUrl": string, 
      "_recordUrl": string
    },
    "last_info":{ //last_info contains basic camera information and information of current camera action, like preview/recording/living.
      "state":string, 
      "version":string,
      "moduleVersion":string,
      "origin":{ //options of unstitched origin fisheye
        "width":int, 
        "height":int, 
        "framerate":int, 
        "bitrate":int, 
        "mime":string, 
        "saveOrigin":bool
    	},
			"preview":{ //options of stitched preview stream
        "width":int, 
        "height":int, 
        "framerate":int, 
        "bitrate":int, 
        "mime":string
      },
			"live":{ //options of stitched live stream
        "width":int,
        "height":int,
        "framerate":int,
        "bitrate":int,
        "mime":string,
        "url":string,
        “timePast”:int,
        "timeLeft":int,
        "liveOnHdmi":bool
      },
			"record":{ //options of stitched record stream
        "width":int, 
        "height":int, 
        "framerate":int, 
        "bitrate":int, 
        "mime":string, 
        “url”:string,
        “timePast”:int, 
        "timeLeft":int
      },
			“audio”:{// options for audio
			  "mime":string,
        "sampleFormat":string,
        "channelLayout":string,
        "samplerate":int,
        "bitrate":int
      },
			"sys_info":{ //basic camera information
        "k_v": "6.0", //kernel version
        "r_v":"'000",  //rom version
        "p_v":"'1.00May 192017",
        "sn":"'xxxxxx"，//serial number
        "h_v":"V0.9.0_2017.5.16" //http service version
      }
		}
	}
}
```



