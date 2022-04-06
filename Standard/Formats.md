# Formats

## Required

All formats below are required.

### string

Simply an unencoded string.

### number

A number, either a float or an integer.

#### int

Just the integer, ie `1`

#### float

The float encoded in the format `int.int` (ie `1.0`), **not** the German `1,0`

### nil, null, undefined

All 3 should return the language's equivalent of `null` when parsing, and an empty string for the value when encoding.

### `function`

This datatype should **warn**, both when encoding, and parsing.<br/>
It should return an empty string when encoding, and the language's equivalent of `null` when parsing. An empty function is also allowed.

### `userdata`

This datatype should be ignored; when parsing, return an empty table, when encoding, return an empty string.

### `udim`

This datatype should be encoded as `Scale+Offset`, where `+` is [U+0006](https://unicode-table.com/en/0006/), and `[Scale|Offset]` are the Scale and Offset properties of a [UDim](https://developer.roblox.com/en-us/api-reference/datatype/UDim).

### `udim2`

This datatype should be encoded as `X.Scale+X.Offset+Y.Scale+Y.Offset`, where `+` is [U+0006](https://unicode-table.com/en/0006/), and `[X|Y].[Scale|Offset]` are the scale/offsets for the individual dimensions.

### `vector2`

This datatype should be encoded as `X+Y`, where `+` is [U+0006](https://unicode-table.com/en/0006/), and `[X|Y|Z]` are the individual components of the vector.

### `vector3`

This datatype should be encoded as `X.Y.Z`, where `.` is [U+0006](https://unicode-table.com/en/0006/), and `[X|Y|Z]` are the individual components of the vector.

### `cframe`

This datatype should be encoded as `pX,pY,pZ/lvX,lvY,lvZ`, where `lvX/lvY/lvZ` are `CFrame`.`LookVector`.`X/Y/Z` respectively, and `pX/pY/pZ` are `CFrame`.`Position`.`X/Y/Z` respectively.

[Example](https://github.com/Conglomeration/Lua/blob/11496b17611c3fc40678020ab8429f16e120cec6/src/CFrameSerializer.lua) of parsing/serializing a CFrame.

## Optional

All formats below are optional, but recommended.

Encoders (Serializers) should assume these aren't available, and may should provide a table containing their contents above said value.
