## Overview

Insta360 Pro Camera API defines a set of commands to control Insat360 Pro series cameras, supported cameras are listed below.

| Model          | Link                                        |
| :------------- | ------------------------------------------- |
| Insta360 Pro   | http://insta360.com/product/insta360-pro/   |
| Insta360 Pro 2  | http://insta360.com/product/insta360-pro2/  |
| Insta360 Titan | http://insta360.com/product/insta360-titan/ |

The commands are transferred via http request/response, the data is encoded in JSON format.

### About Built-in Http Server

Camera supporting Insta360 Pro Camera API has a built-in http server.  You could get ip address from the screen of the camera. Here are url routers. 

| Name | URL Pattern                                   | Function                                                |
| --------------------------------------------- | ------------------------------------------------------- | --------------------------------------------- |
| `command` | http://{camera_ip}:20000/osc/commands/execute | Execute commands                                       |
| `state` | http://{camera_ip}:20000/osc/state            | Poll state, also for notification from camera to client |
| `file` | http://{camera_ip}:8000/{fileuri} | Access Image/Video file from camera |
| `preview` | rtmp://{camera_ip}:1935/live/preview | rtmp stream of preview |



## Documentations

+ [State Polling](state_polling.md)

+ [Async Command Handling](async_command_handling.md) 

+ [Commands](commands/overview.md)

  + [camera._connect](commands/connect_cmd.md)

  + [camera._setOptions](commands/set_options_cmd.md)

  + [camera._getOptions](commands/get_options_cmd.md)

  + [camera._getImageParam](commands/get_image_param_cmd.md)

  + [camera._startPreview](commands/start_preview_cmd.md)

  + [camera._stopPreview](commands/stop_preview_cmd.md)

  + [camera._takePicture](commands/take_picture_cmd.md)

  + [camera._startRecording](commands/start_record_cmd.md)

  + [camera._stopRecording](commands/stop_record_cmd.md)

  + [camera._startLive](commands/start_live_cmd.md)

  + [camera._stopLive](commands/stop_live_cmd.md)

  + [camera._listFiles](commands/list_files.md)
+ [Capabilities](capabilities.md)
