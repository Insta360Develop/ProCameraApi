## Commands Overview

### Request/Response structures

Commands are executed by HTTP POST requests. Required HTTP Headers are listed below.

| Name         | Value                                             | Description                                                |
| ------------ | ------------------------------------------------- | ---------------------------------------------------------- |
| Fingerprint  | A string value,empty string for `connect` command | Identification of the client,obtained by `connect` command |
| Content-Type | application/json                                  |                                                            |

Most commands has the similar structure of request body. The root JSON object has `name` and `parameters` attributes, `name` describes which command to execute. `parameters` differs among different commands.

eg.

```json
{
  "name": "camera._connect",
  "parameters":{
    "hw_time":"MMDDhhmm[[CC]YY][.ss]",
    "time_zone":"GMT+08:00/GMT-08:00"
}

```



Generally, the response contains `name` and `state`.  `state` indicates whether the request is successfully executed. The value is `done` on success, `exception` or `error` otherwise.

eg.

**On success**

```json
{
	"name":"camera._connect",
	"state":"done",
  "results":{ //results contains the data returned by the command.
   	... 
  }
}
```



**On failure**

```json
{
  "name":"camera._connect",
	"state":"exception",
	"error":{ //error object contains the detailed error
    "code":-1, //error code
    "description":"The camera has been taken by another client."  //error description
  }
}
```

