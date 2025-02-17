# Class=527 (0x020F) - Class2 Level I Data

    CLASS2.LEVEL1.DATA

## Description

This class mirrors the [CLASS1.DATA](./class1.data.md) class but use a different data format with a GUID stored in the first 16 bytes of the data followed by the standard data thus offset with 16-bytes.

See [CLASS2.PROTOCOL1](./class2.protocol1.md) for more information on the data format.
## Type=0 (0x00) - General event {#type0}
    VSCP_TYPE_DATA_GENERALGeneral event.



----

## Type=1 (0x01) - I/O value {#type1}
    VSCP_TYPE_DATA_IOGeneral I/O value. First data byte defines format. 

 | Data byte | Description                         | 
 | :---------: | -----------                       | 
 | 0         | Data coding.                        | 
 | 1-7       | Data with format defined by byte 0. | 


----

## Type=2 (0x02) - A/D value {#type2}
    VSCP_TYPE_DATA_ADGeneral A/D value. First data byte defines format. 

 | Data byte | Description                         | 
 | :---------: | -----------                       | 
 | 0         | Data coding.                        | 
 | 1-7       | Data with format defined by byte 0. | 


----

## Type=3 (0x03) - D/A value {#type3}
    VSCP_TYPE_DATA_DAGeneral D/A value. First data byte defines format. 

 | Data byte | Description                         | 
 | :---------: | -----------                       | 
 | 0         | Data coding.                        | 
 | 1-7       | Data with format defined by byte 0. | 


----

## Type=4 (0x04) - Relative strength {#type4}
    VSCP_TYPE_DATA_RELATIVE_STRENGTHRelative strength.  

 | Data byte | Description                         | 
 | :---------: | -----------                       | 
 | 0         | Data coding.                        | 
 | 1-7       | Data with format defined by byte 0. | 

### Coding of units (Level I)

 | Code | Description  | 
 | :----: | ----------- | 
 | 0    | **Byte count = 2**: Min = 0, Max = 255 <br> **Byte count = 3**: Min = 0, Max = 65535 <br> and so on... | 
 | 1    | db (decibel) | 
 | 2    | dbV (decibel volts) | 
 | 3    | Undefined | 

Units for Level II are the same as for Level I for the first four units.


----

## Type=5 (0x05) - Signal Level {#type5}
    VSCP_TYPE_DATA_SIGNAL_LEVELSignal Level is a relative strength value that (as default) has its maximum at 100 and minimum at 0 interpreted as a percentage. For a digital transmission Signal Level it can be used to give an indication of the analogue signal and [CLASS1.DATA, Type = 6, Signal Quality](./class1.data.md#type6) can be used to give an indication of the quality of the digital part as BER (Bit Error Ratio) for example.

 | Data byte | Description                         | 
 | :---------: | -----------                         | 
 | 0         | Data coding.                        | 
 | 1-7       | Data with format defined by byte 0. | 

### Coding of units (Level I)
 | Code | Description                                                                                        | 
 | :----: | -----------                                                                                        | 
 | 0    | (0-100) percentage.                                                                               | 
 | 1    | **Byte count = 2**: Min = 0, Max = 255<br>**Byte count = 3**: Min = 0, Max = 65535<br>  and so on... | 


Units for Level II are the same as for Level I for the first four units.


----

## Type=6 (0x06) - Signal Quality {#type6}
    VSCP_TYPE_DATA_SIGNAL_QUALITYSignal Quality be used to give an indication of the quality of the digital part as BER (Bit Error Ratio) for example.

 | Data byte | Description                         |
 | :---------: | -----------                       |
 | 0         | Data coding.                        |
 | 1-7       | Data with format defined by byte 0. |

### Coding of units (Level I)

 | Code | Description                                                                                        |
 | :----: | -----------                                                                                        |
 | 0    | 0-100, Percent                                                                                     |
 | 1    | **Byte count = 2**: Min = 0, Max = 255  **Byte count = 3**: Min = 0, Max = 65535  and so on... |
 | 2    | dBm  |
 | 3    | To be defined |

Units for Level II are the same as for Level I for the first four units.


----

{% include "./bottom_copyright.md" %}