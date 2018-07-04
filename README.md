# Vault Dragon
Coding test by Lohit for Vault Dragon

## Instructions

The base URL for the API is `http://vaultdragon-87519.onmodulus.net/object` 

API methods include:
```
POST http://vaultdragon-87519.onmodulus.net/object
```
```
GET http://vaultdragon-87519.onmodulus.net/object/:key
```
```
GET http://vaultdragon-87519.onmodulus.net/object/:key?timestamp=##########
```

You are allowed to POST more than one key at a time, and all of them will be added to the database. The POST data has to be in proper JSON string format, for example:
```
{"key":"value"}
```
```
{"key1":"value1","key2":"value2"}
```
The POST result will be in form of 2 arrays -- `success` and `failed`, for keys that are successfully added and keys that failed to save, respectively.
```
{
  "data": {
    "success": [
      {
        "key": "key",
        "value": "value",
        "timestamp": 1471201848
      },
      {
        "key": "key2",
        "value": "value2",
        "timestamp": 1471201848
      }
    ],
    "failed": [
      {
        "error": "Product validation failed",
        "key": "",
        "value": "value3"
      }
    ]
  }
}
```

If the JSON format is invalid or the value is not a string, an error will occur. The keys should be unique. If duplicate keys exist, only the last value of the same key will be saved.

Searching by key will get the latest value of the same key.<br>
Searching by key with timestamp will get the latest value of the same key that is at or before the appointed timestamp.
```
{
  "data": "value"
}
```

## Running on local machine

This code will not run on local machine out of the box. Please rename `config/secrets.json.example` to `config/secrets.json` first in order to run
