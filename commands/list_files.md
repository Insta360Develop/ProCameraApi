## Overview

`listFiles` command let you get a file list on the camera. 

## Request 

```json
{
    "name":"camera._listFiles",
    "parameters":{
        "path":string // you could find the path of the storage in the response of state command
    } 
}
```

## Response

`listFiles` is an async command. View [Async command handling](../async_command_handling.md) to learn how to handle the result.

```json
{
  "name": "camera._listFiles",
  "state": "done",
  "sequence":int //sequence id for async handling
}
```