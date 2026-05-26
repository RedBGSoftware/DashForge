# 🛠 Custom Game Profiles

DashForge supports fully customizable telemetry profiles using JSON configuration files.

Custom profiles allow the community to add support for additional racing games without modifying the application code.

A profile describes:
- packet size
- endianness
- telemetry fields
- memory offsets
- value types
- scaling
- transforms
- telemetry mapping

<br>

## Profile Structure

A telemetry profile is defined as a JSON object.

Example:

```json
{
  "id": "forza-horizon",
  "packetSize": 324,
  "endianness": "little",
  "fields": [
    {
      "target": "speedMs",
      "offset": 256,
      "type": "f32"
    }
  ]
}
```

<br>

### Root Properties

| Property | Type | Description |
|---|---|---|
| id | string | Unique profile identifier |
| packetSize | integer | Expected UDP packet size |
| endianness | string | little or big |
| fields | array | Telemetry field definitions |

<br>

### Endianness

Supported values:

| Value | Description |
|---|---|
| little | Little-endian byte order |
| big | Big-endian byte order |

Most racing games use:

    "little"

<br>

### Field Definition

Each telemetry field describes how DashForge should decode a value from the UDP packet.

Example:

```json
{
  "target": "currentEngineRpm",
  "offset": 16,
  "type": "f32",
  "scale": 1.0
}
```

<br>

### Field Properties

| Property | Type | Required | Description |
|---|---|---|---|
| target | string | Yes | DashForge telemetry field |
| offset | integer | Yes | Byte offset in packet |
| type | string | Yes | Value type |
| scale | number | No | Multiplier applied after decoding |
| transform | string | No | Additional value transform |

<br>

### Supported Value Types

DashForge currently supports:

| Type | Description | Size |
|---|---|---|
| u8 | Unsigned 8-bit integer | 1 byte |
| s8 | Signed 8-bit integer | 1 byte |
| u16 | Unsigned 16-bit integer | 2 bytes |
| s16 | Signed 16-bit integer | 2 bytes |
| u32 | Unsigned 32-bit integer | 4 bytes |
| s32 | Signed 32-bit integer | 4 bytes |
| f32 | 32-bit floating point | 4 bytes |

<br>

### Supported Transforms

Transforms are applied after scaling.

| Transform | Description |
|---|---|
| msToKmh | Converts meters/sec to km/h |
| wattsToKw | Converts watts to kilowatts |
| intToBool | Converts integer to boolean |

Example:

```json
{
  "target": "speedKmh",
  "offset": 120,
  "type": "f32",
  "transform": "msToKmh"
}
```

<br>

### Scaling

The scale property allows modifying decoded values.

Example:

```json
{
  "target": "boost",
  "offset": 88,
  "type": "u16",
  "scale": 0.1
}
```

Decoded value:

    rawValue * scale
    
<br>



## Supported Telemetry Targets

DashForge can currently map the following telemetry fields.

<br>

### Session

| Target |
|---|
| isRaceOn |
| timestampMS |

<br>

### Engine

| Target |
|---|
| engineMaxRpm |
| engineIdleRpm |
| currentEngineRpm |

<br>

### Speed & Power

| Target |
|---|
| speedMs |
| speedKmh |
| power |
| powerKw |
| torqueNm |
| boost |
| fuel |

<br>

### Vehicle Position

| Target |
|---|
| positionX |
| positionY |
| positionZ |

<br>

### Driver Inputs

| Target |
|---|
| accel |
| brake |
| clutch |
| handBrake |
| gear |
| steer |


<br>

## Full Example

```json
{
  "id": "example-racing-game",
  "packetSize": 256,
  "endianness": "little",
  "fields": [
    {
      "target": "speedMs",
      "offset": 120,
      "type": "f32"
    },
    {
      "target": "currentEngineRpm",
      "offset": 16,
      "type": "f32"
    },
    {
      "target": "gear",
      "offset": 44,
      "type": "s8"
    },
    {
      "target": "powerKw",
      "offset": 88,
      "type": "u32",
      "transform": "wattsToKw"
    }
  ]
}
```

<br>

## Validation Rules

DashForge validates:
- packet size
- offsets
- value bounds
- supported types
- telemetry mappings

Invalid fields are ignored automatically.

<br>

---

## Important Notes

### Packet Size

If the received UDP packet size does not match:

    packetSize

the packet is ignored.

<br>

## Offsets

Offsets are byte-based.

Example:

    offset: 120

means:
- start reading at byte 120

<br>

### Unsupported Fields

Unknown telemetry targets are ignored safely.

<br>

---

## Community Profiles

Profiles are stored in:

    /templates/game-profiles

Community contributions are welcome.

<br>

---


## Recommendations

When creating a new profile:

- start from an existing profile
- validate telemetry offsets carefully
- verify packet structure after game updates
- test all mapped fields live

Telemetry formats may change after game updates.
