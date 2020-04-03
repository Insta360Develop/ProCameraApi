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

