## Overview

`get_options` command  let you retrieve options from camera. View supported options.

## Request

The only parameter needed is `property`, which is the name of the options

```json
{
  "name":"camera._getOptions",
  "parameters": {
    "property":string 
  }
}
```



## Response

The `value` may b `int`, `string`, `array`, `object`, depending on specific property.

```json
{
  "name":"camera._getOptions",
  "state":"done",
  "results":{
    "value": depends on property
  }
}
```

