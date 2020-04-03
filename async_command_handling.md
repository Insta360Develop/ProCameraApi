## Async command handling

In most case, we could simply send a http request to execute command, and get result from the http response. However, this is not a good way for time-consuming command, such as `take_picture` , `stop_record` and so on.

Pro Camera API provide a way to execute command asynchronously. Take `take_picture` command as an example, the http response looks like this

```json
{
  "name":"camera._takePicture",
  "state":"done",
  "sequence":int
}
```

There is no result in the response. Instead, there is a `sequence` value. The `sequence` acts as an asynchronous task token, which identifis this `take_picture` command and could be used to get the actual result later.

In [State polling](state_polling.md), we introduced the response of `state` command, where there is a `_idRes` atrribute. The value of `_idRes` attributes is an array of such `sequence` whose corresponding async task has finished executing.  So once the `sequence` of `take_picture` command is listed in `_idRes` , we could then get the actual result of the command.

## `get_result` command

`get_result` command is designed to get actual result of async command.

### Request

```json
{
  "name":"camera._getResult",
  "parameters": {
    "list_ids":[int] //array of sequence you want to get result.
  }
}
```



### Response

```json
{
  "name":"camera._getResult",
  "results":{
    "res_array":[
      {
        "id":int, //the sequence id
        "name":string, //name of the async command
        "results":{ //the sync command results
          "state":"done",
          ...
        }
      }
    ]
  }
}
```



eg. If we send an `get_result` command  with a `take_picture` sequence id. The response looks like this

```json
{
  "name":"camera._getResult",
  "results":{//results of get_result command
    "res_array":[
      {
        "id":int, //the sequence stop_record command
        "name":"camera._stopRecording", //name of the async command
        "results":{ //the origin command response
          "state":"done",
          "results": {//the origin command results
            "_picUrl":string
          }
        }
      }
    ]
  }
}
```



