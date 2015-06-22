# RawPacker

Simple binary packing/unpacking for `RawArray` in Godot.

## About

`RawPacker` allows `Variant` arrays to be packed into and unpacked from a `RawArray` using a format string. The approach was inspired by Python's `struct.pack` and `struct.unpack` functions.
Packing/unpacking `RawArray` is useful for sending and storing data in a compact form.

## Installation

Simply drop the `rawpacker` directory in your `godot/modules` directory and build for the platfom of your choice.

## Example

```python
var raw_packer = RawPacker.new()
var raw_array = raw_packer.pack("?iisfH", [false,1,2,"helloworld",3.14,-42])
var array = raw_packer.unpack("?iisfH", raw_array)
print(array)
```

**Output:**
```
False, 1, 2, helloworld, 3.14, 65494
```

## Format Strings

| Format | Serialized Type    | Godot Type | Size (bytes) |
|:------:|--------------------|------------|:------------:|
| c      | char               | integer    | 1            |
| b      | unsigned char      | integer    | 1            |
| ?      | unsigned char      | boolean    | 1            |
| h      | short              | integer    | 2            |
| H      | unsigned short     | integer    | 2            |
| i      | int                | integer    | 4            |
| I      | unsigned int       | integer    | 4            |
| q      | long long          | integer    | 8            |
| Q      | unsigned long long | integer    | 8            |
| f      | float              | real       | 4            |
| d      | double             | real       | 8            |
| s      | char[]             | string     | varying      |
| p      | char[]             | string     | varying      |

## License
Copyright (c) 2015 James McLean  
Licensed under the MIT license.
