# Device Registry Service

## Usage
Response data will have the following format:

```json
{
  "data": "Mixed content",
  "message": "Description of what happened"
}
```

### List all devices

**Definition**
`GET /devices`

**Response**
- `200 OK` on success

```json
[
  {
    "identifier": "ceiling-lamp",
    "name": "Ceiling Lamp 1",
    "device_type": "switch",
    "controller_gateway": "192.168.1.17"
  },
  {
    "identifier": "raspberry-pi",
    "name": "Raspberry PI 1",
    "device_type": "raspi",
    "controller_gateway": "192.168.1.21"
  }
]
```

### Registering a new device

**Definition**
`POST /devices`

**Arguments**
- `"identifier": string` a globally unique identifier for device
- `"name": string` a user-friendly name for device
- `"device_type": string` the type of device as understood by the client
- `"controller_gateway": string` the IP address of the device's controller

**Response**
`201 Created` on success

```json
{
  "identifier": "raspberry-pi",
  "name": "Raspberry PI 1",
  "device_type": "raspi",
  "controller_gateway": "192.168.1.21"
}
```

### Lookup device details

**Definition**
`GET /device/<identifier>`

**Response**
- `404 Not Found` if the device does not exist
- `200 OK` on success

```json
{
  "identifier": "raspberry-pi",
  "name": "Raspberry PI 1",
  "device_type": "raspi",
  "controller_gateway": "192.168.1.21"
}
```

### Delete a device

**Definition**
`DELETE /devices/<identifier>`

**Response**
- `404 Not Found` if device does not exist
- `204 No Content` on success
