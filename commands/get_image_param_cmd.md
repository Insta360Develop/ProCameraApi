## Overview

`get_image_param` command let you get all the image params at one time.

### Request

No parameter is need.

```json
{
  "name":"camera._getImageParam"
}
```



### Response

```json
{
"name":"camera._getImageParam",
"state":"done",
"results":{
	"aaa_mode":int,
	“wb”:int,
	"iso_value":int,
	"shutter_value":int,
	"brightness":int,
	"contrast":int,
	"saturation":int,
	"hue":int,
	"sharpness":int,
	"ev_bias":int,
	"ae_meter":int,
	"dig_effect":int,
	"flicker":int
	}
}
```

## Image Param

- `aaa_mode`, 3A mode of the camera, available values:

  + Auto Mode = 1
  + Manual Mode = 0
  + WDR Mode = 2
  + Shutter Priority Mode = 3
  + ISO Priority Mode = 4

- `wb`, white balance, available values:

  | White balance | param value |
  | ------------- | ----------- |
  | Auto          | 0           |
  | 2700K         | 1           |
  | 3200K         | 6           |
  | 4000K         | 2           |
  | 5000K         | 3           |
  | 6500K         | 4           |
  | 7500K         | 5           |

- `iso_value`, available values:

  | iso  | param value |
  | ---- | ----------- |
  | 100  | 1           |
  | 125  | 2           |
  | 160  | 3           |
  | 200  | 4           |
  | 250  | 5           |
  | 320  | 6           |
  | 400  | 7           |
  | 500  | 8           |
  | 640  | 9           |
  | 800  | 10          |
  | 1000 | 11          |
  | 1250 | 12          |
  | 1600 | 13          |
  | 2000 | 14          |
  | 2500 | 15          |
  | 3200 | 16          |
  | 4000 | 17          |
  | 5000 | 18          |
  | 6400 | 19          |

- `shutter_value`, value tables:

  | Shutter | Param value |
  | ------- | ----------- |
  | 2s      | 1           |
  | 1s      | 4           |
  | 1/2s    | 7           |
  | 1/3s    | 9           |
  | 1/4s    | 10          |
  | 1/5s    | 11          |
  | 1/8s    | 13          |
  | 1/10s   | 14          |
  | 1/15s   | 16          |
  | 1/20s   | 17          |
  | 1/25s   | 18          |
  | 1/30s   | 19          |
  | 1/40s   | 20          |
  | 1/50s   | 21          |
  | 1/60s   | 22          |
  | 1/80s   | 23          |
  | 1/100s  | 24          |
  | 1/120s  | 25          |
  | 1/160s  | 26          |
  | 1/200s  | 27          |
  | 1/240s  | 28          |
  | 1/320s  | 29          |
  | 1/400s  | 30          |
  | 1/500s  | 31          |
  | 1/640s  | 32          |
  | 1/800s  | 33          |
  | 1/1000s | 34          |
  | 1/1250s | 35          |
  | 1/1600s | 36          |
  | 1/2000s | 37          |
  | 1/2500s | 38          |
  | 1/3200s | 39          |
  | 1/4000s | 40          |
  | 1/5000s | 41          |
  | 1/6400s | 42          |
  | 1/8000s | 43          |

- `brightness`, -255~255, default 0.
- `contrast` ,  0~255, default 64.
- `saturation`, 0~255, default 64.
- `hue`, -15~15
- `sharpness`,0~6,default 3.
- `ev_bias`, -255~255, default 0.

