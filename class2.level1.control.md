# Class=542 (0x021E) - Class2 Level I Control

    CLASS2.LEVEL1.CONTROL

## Description

This class mirrors the [CLASS1.CONTROL](./class1.control.md) class but use a different data format with a GUID stored in the first 16 bytes of the data followed by the standard data thus offset with 16-bytes.

See [CLASS2.PROTOCOL1](./class2.protocol1.md) for more information on the data format.
## Type=0 (0x00) - General event {#type0}
    VSCP_TYPE_CONTROL_GENERALGeneral Event.

----

## Type=1 (0x01) - Mute on/off {#type1}
    VSCP_TYPE_CONTROL_MUTEMute/Un-mute all sound generating nodes in a zone 

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | If equal to zero no mute else mute.                                | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=2 (0x02) - (All) Lamp(s) on/off {#type2}
    VSCP_TYPE_CONTROL_ALL_LAMPSTurn on/off lamps on nodes in zone.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | If equal to zero off else on.                                      | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 

See also [CLASS1.CONTROL, Type=40](./class1.control.md#type40) and [CLASS1.CONTROL, Type=42](./class1.control.md#type41) which don't use byte 0 but instead are separated in two distinct events.


----

## Type=3 (0x03) - Open {#type3}
    VSCP_TYPE_CONTROL_OPENPerform open on all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=4 (0x04) - Close {#type4}
    VSCP_TYPE_CONTROL_CLOSEPerform close on all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=5 (0x05) - TurnOn {#type5}
    VSCP_TYPE_CONTROL_TURNONTurn On a nodes in a zone/subzone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=6 (0x06) - TurnOff {#type6}
    VSCP_TYPE_CONTROL_TURNOFFTurn Off a nodes in a zone/subzone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=7 (0x07) - Start {#type7}
    VSCP_TYPE_CONTROL_STARTStart all nodes in a zone.

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 


----

## Type=8 (0x08) - Stop {#type8}
    VSCP_TYPE_CONTROL_STOPStop all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=9 (0x09) - Reset {#type9}
    VSCP_TYPE_CONTROL_RESETPerform Reset on all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=10 (0x0A) - Interrupt {#type10}
    VSCP_TYPE_CONTROL_INTERRUPTPerform Interrupt on all nodes in zone. 

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Interrupt level. (0 – 255 , zero is lowest interrupt level. ).   | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 



----

## Type=11 (0x0B) - Sleep {#type11}
    VSCP_TYPE_CONTROL_SLEEPPerform Sleep on all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=12 (0x0C) - Wakeup {#type12}
    VSCP_TYPE_CONTROL_WAKEUPWakeup all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=13 (0x0D) - Resume {#type13}
    VSCP_TYPE_CONTROL_RESUMEResume all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=14 (0x0E) - Pause {#type14}
    VSCP_TYPE_CONTROL_PAUSEPause all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=15 (0x0F) - Activate {#type15}
    VSCP_TYPE_CONTROL_ACTIVATEActivate all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=16 (0x10) - Deactivate {#type16}
    VSCP_TYPE_CONTROL_DEACTIVATEDeactivate all nodes in zone. 

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 



----

## Type=17 (0x11) - Reserved for future use {#type17}
    VSCP_TYPE_CONTROL_RESERVED17Reserved. 

----

## Type=18 (0x12) - Reserved for future use {#type18}
    VSCP_TYPE_CONTROL_RESERVED18Reserved. 

----

## Type=19 (0x13) - Reserved for future use {#type19}
    VSCP_TYPE_CONTROL_RESERVED19Reserved.

----

## Type=20 (0x14) - Dim lamp(s) {#type20}
    VSCP_TYPE_CONTROL_DIM_LAMPSDim all dimmer devices on a segment to a specified dim value. 

 | Data byte | Description                                                                             | 
 | :---------: | -----------                                                                             | 
 | 0         | Value (0 – 100) . 0 = off, 100 = full on. 254 dim down one step. 255 dim up one step. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                              | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.                      | 


----

## Type=21 (0x15) - Change Channel {#type21}
    VSCP_TYPE_CONTROL_CHANGE_CHANNELThis is typical for changing TV channels or for changing AV amp input source etc. 

 | Data byte | Description                                                                                                                                                                                                                                                                                                                                               | 
 | :---------: | -----------                                                                                                                                                                                                                                                                                                                                               | 
 | 0         | A value between 0 and 127 indicates the channel number. A value between 128 to 157 is change down by the specified number of channels. A value between 160 to 191 is change up by the specified number of channels. A value of 255 means that this is an extended change channel event and that the channel number is sent in byte 3 and after if needed. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                                                                                                                                                                                                                                                                                                | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.                                                                                                                                                                                                                                                                                        | 


----

## Type=22 (0x16) - Change Level {#type22}
    VSCP_TYPE_CONTROL_CHANGE_LEVELChange an absolute level. 

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Absolute level.                                                    | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=23 (0x17) - Relative Change Level {#type23}
    VSCP_TYPE_CONTROL_RELATIVE_CHANGE_LEVEL
 Relative Change Level request
 
 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Relative level.                                                    | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=24 (0x18) - Measurement Request {#type24}
    VSCP_TYPE_CONTROL_MEASUREMENT_REQUESTMeasurement Request

| Data byte | Description                                                                                                                                                           | 
 | :---------: | -----------                                                                                                                                                           | 
 | 0         | Zero indicates all measurements supported by node should be sent (as separate events). Non-zero indicates a node specific index specifying which measurement to send. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                                                                                                            | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.                                                                                                    | 


----

## Type=25 (0x19) - Stream Data {#type25}
    VSCP_TYPE_CONTROL_STREAM_DATARequest to stream data

 | Data byte | Description                                                               | 
 | :---------: | -----------                                                               | 
 | 0         | Sequence number which is increase by one for each stream data event sent. | 
 | 1-7       | Stream data.                                                              | 

Use this event for streamed data out from a node. The source is then given by the nickname. If a specific received is needed use Zoned Stream. 


----

## Type=26 (0x1A) - Sync {#type26}
    VSCP_TYPE_CONTROL_SYNCSynchronize events on a segment. 

 | Data byte | Description                                                                                                                                  | 
 | :---------: | -----------                                                                                                                                  | 
 | 0         | Sensor index for a sensor within a module (see [data coding](./data_coding.md). 255 is all sensors. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                                                                                   | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.                                                                           | 

The sensor index can be used to index units within a module also or used as some other indexing schema. 


----

## Type=27 (0x1B) - Zoned Stream Data {#type27}
    VSCP_TYPE_CONTROL_ZONED_STREAM_DATARequest streamed data from nodes identified by zone/subzone.

 | Data byte | Description                                                               | 
 | :---------: | -----------                                                               | 
 | 0         | Sequence number which is increase by one for each stream data event sent. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.        | 
 | 3-7       | Stream data.                                                              | 


----

## Type=28 (0x1C) - Set Pre-set {#type28}
    VSCP_TYPE_CONTROL_SET_PRESETSome nodes may have pre-set configurations to choose from. With this event a pre-set can be set for a zone/sub-zone.

A node that receive and act on this event send CLASS1.INFORMATION, 

Type=48 as a response event. 

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Code for pre-set to set.                                           | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=29 (0x1D) - Toggle state {#type29}
    VSCP_TYPE_CONTROL_TOGGLE_STATEToggle the state of a node.

Note: This may be a bad design option as it often demands that the state should be known for the node on beforehand.

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 


----

## Type=30 (0x1E) - Timed pulse on {#type30}
    VSCP_TYPE_CONTROL_TIMED_PULSE_ONWith this event it is possible to generate a timed pulse that is on for a specified time.

 | Data byte | Description                                                         |
 | :---------: | ----------- |
 | 0         | Optional byte that have a meaning given by the issuer of the event. |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.      |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  |
 | 3         | Control byte.                                                       |
 | 4-7       | Set time as a long with MSB in the first byte.                      |

##### Control Byte

The control byte have the following bits defined

 | Bit | Description                                                          |
 | :---: | -----------                                                          |
 | 0-3 | Time code (see table below)                                          |
 | 4   | Reserved                                                             |
 | 5   | Reserved                                                             |
 | 6   | Send on event ( Class=20 Type = 3 (0x03) On ) when pulse goes on.    |
 | 7   | Send off event ( Class=20 Type = 4 (0x04) Off ) when pulse goes off. |

##### Time code

 | Code | Description                     |
 | :----: | -----------                     |
 | 0    | Time specified in microseconds. |
 | 1    | Time specified in milliseconds. |
 | 2    | Time specified in seconds.      |
 | 3    | Time specified in minutes.      |
 | 4    | Time specified in hours.        |
 | 5    | Time specified in days.         |


----

## Type=31 (0x1F) - Timed pulse off {#type31}
    VSCP_TYPE_CONTROL_TIMED_PULSE_OFFWith this event it is possible to generate a timed pulse that is off for a specified time.

 | Data byte | Description                                                         | 
 | :---------: | -----------                                                         | 
 | 0         | Optional byte that have a meaning given by the issuer of the event. | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.          | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  | 
 | 3         | Control byte.                                                       | 
 | 4-7       | Set time as a long with MSB in the first byte.                      | 

##### Control Byte

The control byte have the following bits defined

 | Bit | Description                                                          | 
 | :---: | -----------                                                          | 
 | 0-3 | Time code (see table below)                                          | 
 | 4   | Reserved                                                             | 
 | 5   | Reserved                                                             | 
 | 6   | Send on event ( Class=20 Type = 3 (0x03) On ) when pulse goes on.    | 
 | 7   | Send off event ( Class=20 Type = 4 (0x04) Off ) when pulse goes off. | 

##### Time code

 | Code | Description                     | 
 | :----: | -----------                     | 
 | 0    | Time specified in microseconds. | 
 | 1    | Time specified in milliseconds. | 
 | 2    | Time specified in seconds.      | 
 | 3    | Time specified in minutes.      | 
 | 4    | Time specified in hours.        | 
 | 5    | Time specified in days.         | 



----

## Type=32 (0x20) - Set country/language {#type32}
    VSCP_TYPE_CONTROL_SET_COUNTRY_LANGUAGESet country and language.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Country/Language code.                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 
 | 3-7       | Country/Language code specific                                     | 

 | Language code | Description          | Example                                           | 
 | :---------: | -----------          | -------                                           | 
 | 0             | Custom coded system  | Byte 3 = 0 English, Byte 3 = 1 German or similar. | 
 | 1             | ISO 639-1            | nl for Dutch, en for English.                     | 
 | 2             | ISO 639-2/T          | nid for Dutch, eng for English.                   | 
 | 3             | ISO 639-2/B          | dut for Dutch, eng for English.                   | 
 | 4             | ISO 639-3            | nid for Dutch, eng for English.                   | 
 | 5             | IETF (RFC-5646/4647) | en-US for American English. en-GB British.        | 


ISO codes can be found [here](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)


----

## Type=33 (0x21) - Big Change level {#type33}
    VSCP_TYPE_CONTROL_BIG_CHANGE_LEVELBig Change level can be used in situations when the one byte level of CLASS1.CONTROL, Type=22 is not enough.

 | Data byte | Description                                                                                               | 
 | :---------: | -----------                                                                                               | 
 | 0         | Index                                                                                                     | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.                                                | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.                                        | 
 | 3-7       | Level as signed Integer. The range can be adjusted by the user by sending the needed number of bytes 1-5. | 


----

## Type=34 (0x22) - Move shutter up {#type34}
    VSCP_TYPE_CONTROL_SHUTTER_UPMove shutter up.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=35 (0x23) - Move shutter down {#type35}
    VSCP_TYPE_CONTROL_SHUTTER_DOWNMove shutter down.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=36 (0x24) - Move shutter left {#type36}
    VSCP_TYPE_CONTROL_SHUTTER_LEFTMove shutter left.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 



----

## Type=37 (0x25) - Move shutter right {#type37}
    VSCP_TYPE_CONTROL_SHUTTER_RIGHTMove shutter right.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=38 (0x26) - Move shutter to middle position {#type38}
    VSCP_TYPE_CONTROL_SHUTTER_MIDDLEMove shutter to middle position.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 


----

## Type=39 (0x27) - Move shutter to preset position {#type39}
    VSCP_TYPE_CONTROL_SHUTTER_PRESETMove shutter to preset position.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Index.                                                             | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 
 | 3         | Position 0-100.                                                    | 


----

## Type=40 (0x28) - (All) Lamp(s) on {#type40}
    VSCP_TYPE_CONTROL_ALL_LAMPS_ONTurn on all lamps in a zone.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Not used.                                                          | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 

See also [CLASS1.CONTROL, Type=2](./class1.control.md#type2)


----

## Type=41 (0x29) - (All) Lamp(s) off {#type41}
    VSCP_TYPE_CONTROL_ALL_LAMPS_OFFTurn off all lamps in a zone.

 | Data byte | Description                                                        | 
 | :---------: | -----------                                                        | 
 | 0         | Not used.                                                          | 
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         | 
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. | 

See also [CLASS1.CONTROL, Type=2](./class1.control.md#type2)


----

## Type=42 (0x2A) - Lock {#type42}
    VSCP_TYPE_CONTROL_LOCKLock devices in a zone.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |


----

## Type=43 (0x2B) - Unlock {#type43}
    VSCP_TYPE_CONTROL_UNLOCKUnlock devices in a zone.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                        |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |


----

## Type=44 (0x2C) - PWM set {#type44}
    VSCP_TYPE_CONTROL_PWMWith this event it is possible to set duty cycle output such as PWM.

 | Data byte | Description   |
 | :---------: | ----------- |
 | 0         | Repeat/counter: 0=repeat forever, >0 number of repeats |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.      |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones.  |
 | 3         | Control byte.  |
 | 4         | Time-On MSB |
 | 5         | Time-On LSB |
 | 6         | Time-Off MSB |
 | 7         | Time-Off LSB |

##### Control Byte

The control byte have the following bits defined

 | Bit | Description |
 | :---: | ----------- |
 | 0-3 | Time code (see table below) |
 | 4   | Reserved  |
 | 5   | Reserved  |
 | 6   | Reserved  |
 | 7   | Reserved  |

##### Time code

 | Code | Description                     |
 | :----: | -----------                   |
 | 0    | Time specified in microseconds. |
 | 1    | Time specified in milliseconds. |
 | 2    | Time specified in seconds.      |
 | 3    | Time specified in minutes.      |
 | 4    | Time specified in hours.        |
 | 5    | Time specified in days.         |


----

## Type=45 (0x2D) - Lock with token {#type45}
    VSCP_TYPE_CONTROL_TOKEN_LOCKLock devices with token.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3-4 | Token. This token can be 1-5 bytes and length of event is set accordingly. It should be interpreted as an unsigned integer in the range 0-1099511627775. MSB byte is stored in first byte. |

----

## Type=46 (0x2E) - Unlock with token {#type46}
    VSCP_TYPE_CONTROL_TOKEN_UNLOCKUnlock devices with token.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3-4 | Token. This token can be 1-5 bytes and length of event is set accordingly. It should be interpreted as an unsigned integer in the range 0-1099511627775. MSB byte is stored in first byte. |

----

## Type=47 (0x2F) - Set security level {#type47}
    VSCP_TYPE_CONTROL_SET_SECURITY_LEVELSet security level.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Security level to set. 0-255 (Higher value is higher security level).  |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |


----

## Type=48 (0x30) - Set security pin {#type48}
    VSCP_TYPE_CONTROL_SET_SECURITY_PINSet security pin.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3-4 | Security pin. This pin can be 1-5 bytes and length of event is set accordingly. It should be interpreted as an unsigned integer in the range 0-1099511627775. MSB byte is stored in first byte. |

----

## Type=49 (0x31) - Set security password {#type49}
    VSCP_TYPE_CONTROL_SET_SECURITY_PASSWORDSet security password.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3-4 | Security password. This password can be 1-5 bytes and length of event is set accordingly. It should be interpreted as an UTF-8 string with a length set bt event data length - 3 |

----

## Type=50 (0x32) - Set security token {#type50}
    VSCP_TYPE_CONTROL_SET_SECURITY_TOKENSet security token.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 | 3-4 | Token. This token can be 1-5 bytes and length of event is set accordingly. It should be interpreted as an unsigned integer in the range 0-1099511627775. MSB byte is stored in first byte. |

----

## Type=51 (0x33) - Request new security token {#type51}
    VSCP_TYPE_CONTROL_REQUEST_SECURITY_TOKENRequest new security token.

 | Data byte | Description                                                        |
 | :---------: | -----------                                                      |
 | 0         | Not used.                                                          |
 | 1         | Zone for which event applies to (0-255). 255 is all zones.         |
 | 2         | Sub-zone for which event applies to (0-255). 255 is all sub-zones. |
 

----

{% include "./bottom_copyright.md" %}