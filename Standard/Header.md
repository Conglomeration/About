# Headers

## Per-CGL

Each Conglomeration (CGL) must start with a simple `FORMAT_VERSION_BEGIN` followed by the format version, followed by `FORMAT_VERSION_END`

## Per-Entry

Each kv pair (entry) has a header, which is composed of the following:

- A `HEADER_BEGIN` marker, indicating that the header begins
- A `DATA_NAME` marker, followed by **base-64 encoded** the name of the chunk (aka the Key in the k,v pair)
- A `DATA_TYPE` marker, followed by the type of the chunk (such as `string`, `vector3`) - Parsers must treat this case-insensitively<br/>This is used to determine how to parse the data.<br/>This **must** be followed by a `END_HEADER_FIELD` marker, indicating that this is is the end of the `DATA_TYPE` marker.<br/>This field **cannot** contain the `END_HEADER_FIELD` marker within it\'s contents.<br/>Parsers should read up to said `END_HEADER_FIELD` marker.
- A `DATA_LENGTH` marker, followed by the length of the data (in bytes)
- A `DATA_LAST` marker, followed by `true` or `false`, indicating if this is the last chunk, or if we should read more.<br/>-> Parsers should error if this is false despite being the last chunk
- A `DATA_BEGIN` marker, followed by the data

### Parsing Headers

Parsers should ignore headers they don't understand. They can optionally, for returned tables/custom classes, add it as `__UNKNOWN_FIELD_<UPPERCASE_NAME>` to the returned object, however this is not required.<br/>
Parsers should consider everything until the `DATA_BEGIN` marker to be the header.<br/>
Parsers should consider exactly `DATA_LENGTH` Bytes after `DATA_BEGIN` to be the body. No more, No less.

> **Note**: Parsers should error if there are not `DATA_LENGTH` bytes after `DATA_BEGIN` available.

## Priorities

Values towards the end should overwrite ones towards the top, if their types can be found.<br/>
This is useful, if, for example, you have, say, `vector3` and `vector3-with-non-standard-data` types, one which adds extra data, and the other just contains the basic data.<br/>
Encoders may provide an option to encode in a way that takes advantage of this, however parsers **must** follow this while parsing.

## Markers

Here's a list of Header Markers and their corresponding unicode characters:
| Name | Character | Unicode |
| ---------------------- | --------- | --- |
| `HEADER_BEGIN` | `` | [U+0001](https://unicode-table.com/en/0001/) |
| `DATA_NAME` | `` | [U+0003](https://unicode-table.com/en/0003/) |
| `DATA_TYPE` | `` | [U+0004](https://unicode-table.com/en/0004/) |
| `END_HEADER_FIELD` | `` | [U+0007](https://unicode-table.com/en/0007/) |
| `DATA_LENGTH` | `` | [U+0005](https://unicode-table.com/en/0005/) |
| `DATA_LAST` | | [U+000B](https://unicode-table.com/en/000B/) |
| `DATA_BEGIN` | `` | [U+0006](https://unicode-table.com/en/0006/) |
| `FORMAT_VERSION_BEGIN` | `` | [U+0008](https://unicode-table.com/en/0008/) |
| `FORMAT_VERSION_END` | | [U+0009](https://unicode-table.com/en/0009/) |
