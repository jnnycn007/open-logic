<img src="../Logo.png" alt="Logo" width="400">

# olo_base_pkg_logic

[Back to **Entity List**](../EntityList.md)

## Status Information

![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/coverage/olo_base_pkg_logic.json?cacheSeconds=0)
![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/branches/olo_base_pkg_logic.json?cacheSeconds=0)
![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/issues/olo_base_pkg_logic.json?cacheSeconds=0)

VHDL Source: [olo_base_pkg_logic](../../src/base/vhdl/olo_base_pkg_logic.vhd)

## Description

This package contains different logic functions not defined in IEEE packages but used by _Open Logic_ internally or on
its interfaces to the user (e.g. for port-widths depending on generics). The package is written mainly for these
purposes and does not aim for completeness - nevertheless as a user you are free to use it for your code of course.

## Definitions

### Polynomial_Prbs\<N\>_c

Common LFSR polynomials. X^N positions are marked by a one:

x⁹ + x⁵ + 1 = "100010000"

## Functions

### zerosVector() / onesVector()

Returns a _std_logic_vector_ of a given length containing all zeros or all ones.

```vhdl
function zerosVector(size : in natural) return std_logic_vector;
function onesVector(size : in natural) return std_logic_vector;
```

### shiftLeft() / shiftRight()

Shift a _std_logic_vector_ an arbitrary number of bits to the right or left and shift in either '0' or '1'
(configurable).

```vhdl
function shiftLeft(     arg  : in std_logic_vector;
                        bits : in integer;
                        fill : in std_logic := '0') return std_logic_vector;
function shiftRight(    arg  : in std_logic_vector;
                        bits : in integer;
                        fill : in std_logic := '0') return std_logic_vector;
```

_bits_ is the number of bits to shift, _fill_ is the bit-value shifted in.

### binaryToGray() / grayToBinary()

Conversion between binary numbers and gray coded numbers.

```vhdl
binaryToGray(binary : in std_logic_vector) return std_logic_vector;
function grayToBinary(gray : in std_logic_vector) return std_logic_vector;
```

### ppcOr()

Computation of the OR parallel prefix, which is useful for implementing arbiters.

```vhdl
ppcOr(inp : in std_logic_vector) return std_logic_vector;
```

### to01X()

Convert a _std_logic_ resp all bits in a _std_logic_vector_ to '0', '1' or 'X'.

```vhdl
to01X(inp : in std_logic) return std_logic;
function to01X(inp : in std_logic_vector) return std_logic_vector;
```

'H' and 'L' are interpreted as '1' and '0', so this function can be used to convert weak signals from testbenches into
binary signals.

- '0', 'L' --> '0'
- '1', 'H' --> '1'
- all others --> 'X'

### to01()

Convert a _std_logic_ resp all bits in a _std_logic_vector_ to '0' or '1'.

```vhdl
to01(inp : in std_logic) return std_logic;
function to01(inp : in std_logic_vector) return std_logic_vector;
```

'H' and 'L' are interpreted as '1' and '0', so this function can be used to convert weak signals from testbenches into
binary signals.

- '0', 'L' --> '0'
- '1', 'H' --> '1'
- all others --> '0'

### invertBitOrder()

Invert bit-order in a _std_logic_vector_.

```vhdl
invertBitOrder(inp : in std_logic_vector) return std_logic_vector;
```

### invertByteOrder()

Invert the byte-order in a _std_logic_vector_.

This function is only allowed for number of bits being a multiple of 8, otherwise it asserts an error.

```vhdl
invertByteOrder(inp : in std_logic_vector) return std_logic_vector;
```
