# Class=89 (0x59) - Set value with zone

    CLASS1.SETVALUEZONEX4

## Description

This class mirrors the standard measurement events is [CLASS1.MEASUREMENT=14](./class1.measurement.md) but also have zone information and is intended for setting a value instead of providing a measurement.

 | Byte | Description                                                        |
 | ---- | -----------                                                        |
 | 0    | Index for sensor.                                                  |
 | 1    | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2    | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3    | Data coding.                                                       |
 | 4-7  | Data with format defined by byte 0.                                |

## Type=0 (0x00) - General event {#type0}
    VSCP_TYPE_MEASUREMENTX4_GENERALGeneral Event.




----

{% include "./bottom_copyright.md" %}