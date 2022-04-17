# Hangry Mobile Order API Docs

A collection of APIs gathered from reverse engineering and network traffic analysis of the Hangry Solutions Mobile Order app.

## General API Information

The base endpoint for `POST` requests for data is https://hangrybbapiprod-main.azurewebsites.net
The base endpoint for `GET` requests for media is https://hangrybbprod.blob.core.windows.net

## Get Campus Locations

```
POST /api_user/getcampuslocations
```

| Header      | Description  |
| ----------- | ------------ |
| api_key     | Required     |
| login_token | Required     |
| sessionid   | Not Required |

### Body

```json
{
  "campusid": "CAMPUS_ID"
}
```

### Response

```json
{
    "web_instanceid",
    "locations",
    "message",
    "user",
    "status"
    "cafeterias"
}
```

#### `web_instanceid`

64 character alpha-numeric string

For example, `2e99d0233fcdc9c5177744d92d997c4a0c2a58953be940932917af4af07a8486`

#### `locations`

Array of objects representing locations

#### `message`

| Condition                   | Message                                                               |
| --------------------------- | --------------------------------------------------------------------- |
| Invalid/Missing API Key     | `Invalid API Access Key`                                              |
| Invalid Login Token         | `Your session has expired. For your security, please log in again :)` |
| Missing Login Token         | `Login Token was not supplied.`                                       |
| Valid API Key & Login Token | `SUCCESS`                                                             |

#### `user`

Object representing user

#### `status`

`OK` or `ERROR`

#### `cafeterias`

Array of objects representing dining halls/cafeterias

## ...