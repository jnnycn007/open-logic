<img src="../Logo.png" alt="Logo" width="400">

# olo_fix_from_real

[Back to **Entity List**](../EntityList.md)

## Status Information

![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/coverage/olo_fix_from_real.json?cacheSeconds=0)
![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/branches/olo_fix_from_real.json?cacheSeconds=0)
![Endpoint Badge](https://img.shields.io/endpoint?url=https://storage.googleapis.com/open-logic-badges/issues/olo_fix_from_real.json?cacheSeconds=0)

VHDL Source: [olo_fix_from_real](../../src/fix/vhdl/olo_fix_from_real.vhd)
Bit-true Model: [olo_fix_from_real](../../src/fix/python/olo_fix/olo_fix_from_real.py)

## Description

This entity converts a real (floating-point) number to fixed-point format.

Real numbers are not used for synthesis normally. The _olo_fix_from_real_ entity has the following use-case:

- Create fixed-point representation of constants
  - Example: Calculation of the gravitational force
  - A real constant with the value 9.81 is defined (good readability)
  - For fixed-point calculations, the constant is converted to fixed-point representation using _olo_fix_from_real_
  - In this case the input is static, therefore the generic interface (_Value_g_) is used

Note that this entity does not contain any pipeline registers. Real (floating-point) values do no exist in synthesized
netlists - so the conversion only is executed at compile-time or in simulations. Hence no registers are needed.

This entity does only allow to handle constant values. For the conversion of real values in simulation, use
[olo_fix_sim_from_real](./olo_fix_sim_from_real.md) instead.

For details about the fixed-point number format used in _Open Logic_, refer to the
[fixed point principles](./olo_fix_principles.md).

## Generics

| Name        | Type    | Default   | Description                                                  |
| :---------- | :------ | --------- | :----------------------------------------------------------- |
| ResultFmt_g | string  | -         | Format of the result<br />String representation of an _en_cl_fix Format_t_ (e.g. "(0,1,15)") |
| Saturate_g  | string  | "Sat_s"   | Saturation mode<br />String representation of an _en_cl_fix FixSaturate_t_. |
| Value_g     | real    | 0.0       | Generic to be used for compile-time static inputs. |

## Interfaces

### Input Data

None

### Output Data

| Name       | In/Out | Length               | Default | Description                               |
| :--------- | :----- | :------------------- | ------- | :---------------------------------------- |
| Out_Value  | out    | _width(ResultFmt_g)_ | N/A     | Output data  |

## Detail

No detailed description required. All details that could be mentioned here are already covered by
[fixed point principles](./olo_fix_principles.md).
