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

---

# Profile Structure

A telemetry profile is defined as a JSON object.

Example:

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

---

# Root Properties

| Property | Type | Description |
|---|---|---|
| id | string | Unique profile identifier |
| packetSize | integer | Expected UDP packet size |
| endianness | string | little or big |
| fields | array | Telemetry field definitions |

---

# Endianness

Supported values:

| Value | Description |
|---|---|
| little | Little-endian byte order |
| big | Big-endian byte order |

Most racing games use:

    "little"

---

# Field Definition

Each telemetry field describes how DashForge should decode a value from the UDP packet.

Example:

{
  "target": "currentEngineRpm",
  "offset": 16,
  "type": "f32",
  "scale": 1.0
}

---

# Field Properties

| Property | Type | Required | Description |
|---|---|---|---|
| target | string | Yes | DashForge telemetry field |
| offset | integer | Yes | Byte offset in packet |
| type | string | Yes | Value type |
| scale | number | No | Multiplier applied after decoding |
| transform | string | No | Additional value transform |

---

# Supported Value Types

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

---

# Supported Transforms

Transforms are applied after scaling.

| Transform | Description |
|---|---|
| msToKmh | Converts meters/sec to km/h |
| wattsToKw | Converts watts to kilowatts |
| intToBool | Converts integer to boolean |

Example:

{
  "target": "speedKmh",
  "offset": 120,
  "type": "f32",
  "transform": "msToKmh"
}

---

# Supported Telemetry Targets

DashForge can currently map the following telemetry fields.

---

## Session

| Target |
|---|
| isRaceOn |
| timestampMS |

---

## Engine

| Target |
|---|
| engineMaxRpm |
| engineIdleRpm |
| currentEngineRpm |

---

## Speed & Power

| Target |
|---|
| speedMs |
| speedKmh |
| power |
| powerKw |
| torqueNm |
| boost |
| fuel |

---

## Vehicle Position

| Target |
|---|
| positionX |
| positionY |
| positionZ |

---

## Driver Inputs

| Target |
|---|
| accel |
| brake |
| clutch |
| handBrake |
| gear |
| steer |

---

# Scaling

The scale property allows modifying decoded values.

Example:

{
  "target": "boost",
  "offset": 88,
  "type": "u16",
  "scale": 0.1
}

Decoded value:

    rawValue * scale

---

# Full Example

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

---

# Validation Rules

DashForge validates:
- packet size
- offsets
- value bounds
- supported types
- telemetry mappings

Invalid fields are ignored automatically.

---

# Important Notes

## Packet Size

If the received UDP packet size does not match:

    packetSize

the packet is ignored.

---

## Offsets

Offsets are byte-based.

Example:

    offset: 120

means:
- start reading at byte 120

---

## Unsupported Fields

Unknown telemetry targets are ignored safely.

---

# Community Profiles

Profiles are stored in:

    /templates/game-profiles

Community contributions are welcome.

---

# Recommendations

When creating a new profile:

- start from an existing profile
- validate telemetry offsets carefully
- verify packet structure after game updates
- test all mapped fields live

Telemetry formats may change after game updates.
