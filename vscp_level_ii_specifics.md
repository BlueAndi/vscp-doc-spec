# VSCP Level II Specifics

Also check VSCP over TCP/IP which have more Level II specifics for the lower levels.

Level II nodes are intended for media with higher bandwidth then Level I nodes and no nickname procedure is therefore implemented on Level II. As result of this the full GUID is sent in each packet.

## Level II events

The header for a level II event is defined as

```c++
typedef struct {
        uint16_t crc;           /* crc checksum (calculated from here to end) */
                                /* Used for UDP/Ethernet etc */

        uint32_t obid;          /* Used by driver for channel info etc. */

        /* Time block - Always UTC time */
        uint16_t year;
        uint8_t month;          /* 1-12 */
        uint8_t day;            /* 1-31 */
        uint8_t hour;           /* 0-23 */
        uint8_t minute;         /* 0-59 */
        uint8_t second;         /* 0-59 */

        uint32_t timestamp;     /* Relative time stamp for package in microseconds */
                                /* ~71 minutes before roll over */

        /* ----- CRC should be calculated from here to end + data block ----  */

        uint16_t head;          /* Bit 15   GUID is IP v.6 address. */
	                            /* Bit 14   This is a dumb node. No MDF, register, nothing. */
                                /* Bit 8-13 = Reserved */
                                /* bit 765  priority, Priority 0-7 where 0 is highest. */
                                /* bit 4 = hard coded, true for a hard coded device. */
                                /* bit 3 = Don't calculate CRC, false for CRC usage. */
                                /*          Just checked when CRC is used.                */
                                /*          If set the CRC should be set to 0xAA55 for    */
                                /*          the event to be accepted without a CRC check. */
                                /* bit 2 = Rolling index. */
                                /* bit 1 = Rolling index. */
                                /* bit 0 = Rolling index. */
        uint16_t vscp_class;    /* VSCP class */
        uint16_t vscp_type;     /* VSCP type */
        uint8_t GUID[ 16 ];     /* Node globally unique id MSB(0) -> LSB(15) */
        uint16_t sizeData;      /* Number of valid data bytes */

        uint8_t *pdata;         /* Pointer to data. Max 512 bytes */

    } vscpEvent;
```

The biggest differences is that the GUID is sent in each event and that both class and type has a 16-bit length.

The CRC is calculated using the CCITT polynomial

 The format in a stream is


## VSCP LEVEL II UDP datagram offsets

```c++
#define VSCP_MULTICAST_PACKET0_POS_PKTTYPE              0

#define VSCP_MULTICAST_PACKET0_POS_HEAD                 1
#define VSCP_MULTICAST_PACKET0_POS_HEAD_MSB             1

#define VSCP_MULTICAST_PACKET0_POS_HEAD_LSB             2
#define VSCP_MULTICAST_PACKET0_POS_TIMESTAMP            3

#define VSCP_MULTICAST_PACKET0_POS_YEAR                 7
#define VSCP_MULTICAST_PACKET0_POS_YEAR_MSB             7

#define VSCP_MULTICAST_PACKET0_POS_YEAR_LSB             8
#define VSCP_MULTICAST_PACKET0_POS_MONTH                9

#define VSCP_MULTICAST_PACKET0_POS_DAY                  10
#define VSCP_MULTICAST_PACKET0_POS_HOUR                 11

#define VSCP_MULTICAST_PACKET0_POS_MINUTE               12
#define VSCP_MULTICAST_PACKET0_POS_SECOND               13

#define VSCP_MULTICAST_PACKET0_POS_VSCP_CLASS           14
#define VSCP_MULTICAST_PACKET0_POS_VSCP_CLASS_MSB       14

#define VSCP_MULTICAST_PACKET0_POS_VSCP_CLASS_LSB       15
#define VSCP_MULTICAST_PACKET0_POS_VSCP_TYPE            16

#define VSCP_MULTICAST_PACKET0_POS_VSCP_TYPE_MSB        16
#define VSCP_MULTICAST_PACKET0_POS_VSCP_TYPE_LSB        17

#define VSCP_MULTICAST_PACKET0_POS_VSCP_GUID            18
#define VSCP_MULTICAST_PACKET0_POS_VSCP_SIZE            34

#define VSCP_MULTICAST_PACKET0_POS_VSCP_SIZE_MSB        34
#define VSCP_MULTICAST_PACKET0_POS_VSCP_SIZE_LSB        35

#define VSCP_MULTICAST_PACKET0_POS_VSCP_DATA            36
```

As is noted the obid and time-stamp is not present in the actual stream and is only inserted by the driver interface software.

Level I events can travel in the Level II world. This is because all Level I events are repleted in Class=1024. As nicknames are not available on Level II they are replaced in the events by the full GUID. This is an important possibility in larger installations.

A event from a node on a Level I that is transferred out on a Level II can have the nodes own GUID set or the GUID of the interface between the Level I and the Level II segment. Which method to choose is up to the implementer as long as the GUID's are unique.

For interfaces the machine MAC address, if available, is a good base for a GUID which easily can map to real physical nodes that are handled by the interface. By using this method each MAC address gives 65536 unique GUID's.

Other methods to generate GUID's s also available form more information see Appendix A.

## XML Representation

VSCP level II events can be presented as XML data. Format is

```xml
`<?xml version = "1.0" encoding = "UTF-8" ?>`
`<!-- Version 0.0.1 2007-09-27 -->`
`<event>`
    `<head>`flags for event`</head>`
    `<class>`Eventclass is numerical form or CLASSx:numerical form`</class>`
    `<type>`Event type in numerical form.`</type>`
    `<!-- GUID of sending node -->`
    `<guid>`ff:ee:dd:cc:bb:aa:99:88:77:66:55:44:33:22:11:00`</guid>`
    `<timestamp>`Relative microsecond value.`</timestamp>`
    `<!-- UTC time -->`
    `<datetime>`2018-03-03T12:01:40`</datetime>`
    `<data>`
    Comma separated list with event data.
    Hex values (preceded with '0x')and decimal values allowed.
    `</data>`
    `<!-- Optional for use with measurements -->`
    `<unit>`Code for unit data is presented in`</unit>`
    `<sensorindex>`Index for sensor`</sensorindex>`
    `<coding>`How value is codes`</coding>`
    `<value>`Measurement value`</value>`
`</event>`
```

If timestamp and or datetime is absent it should be treated as 'now'.

timestamp is a sender relative value expressed in microseconds that can be used for more precise timing calculations

datetime is date + time in UTC

## JSON Representation

VSCP level II events can be presented as JSON data. Format is

```json
{
    “head”:0,
    “vscpclass”: 10,
    “vscptype”: 6,
    "guid": "ff:ee:dd:cc:bb:aa:99:88:77:66:55:44:33:22:11:00",
    "timestamp": 1234567,
    "datetime": "2018-03-03T12:01:40",
    "data":[1,2,3,4],
    “unit”: 0,        /* optional for measurements */
    “sensorindex”: 0, /* optional for measurements */
    “coding”: 0,      /* optional for measurements */
    “value”: 1.2345,  /* optional for measurements */
}
```

If timestamp and or datetime is absent it should be treated as 'now'.

timestamp is a sender relative value expressed in microseconds that can be used for more precise timing calculations

datetime is date + time in UTC

## Globally Unique Identifiers

To classify as a node in a VSCP net all nodes must be uniquely identified by a globally unique 16-byte (yes that is 16-byte (128 bits) not 16-bit) identifier. This number uniquely identifies all devices around the world and can be used as a means to obtain device descriptions as well as drivers for a specific platform and for a specific device.

The manufacturer of the device can also use the number as a serial number to track manufactured devices. In many other environments and protocols there is a high cost in getting a globally unique number for your equipment. This is not the case with VSCP. If you own an Ethernet card you also have what is needed to create your own GUID's.

The GUID address is not normally used during communication with a node. Instead an 8-bit address is used. This gives a low protocol overhead. A segment can have a maximum of 127 nodes even if the address gives the possibility for 256 nodes. The 8-bit address is received from a master node called the segment controller. The short address is also called the nodes nickname-ID or nickname address.

Besides the GUID it is recommended that all nodes should have a node description string in the firmware that points to a URL that can give full information about the node and its family of devices. As well as providing information about the node, this address can point at drivers for various operating systems or segment controller environments. Reserved GUID's

Some GUID's are reserved and unavailable for assignment. Appendix A list these and also assigned IDs.

The VSCP team controls the rest of the addresses and will allocate addresses to individuals or companies by them sending a request to [guid_request@vscp.org](guid_request@vscp.org). You can request a series of 32-bits making it possible for you to manufacture 4294967295 nodes. If you need more (!!!) you can ask for another series. There is no cost for reserving a series. Appendix A in this document contains a list of assigned addresses which will also be available at [https://www.vscp.org](https://www.vscp.org)

## Predefined VSCP GUID's

It is possible to create your own GUID without requesting a series and still have a valid global VSCP GUID. This is because GUID series has been constructed from Ethernet MAC addresses and other common id series. Full list is [here](./vscp_globally_unique_identifiers.md).



## Assigned VSCP GUID's

Current predefined GUID series is listed in [appendix A](./appendix_a.md). You can request your own series by writing [guid_request@vscp.org](guid_request@vscp.org)

## Shorthand GUID's

Note that there is a convenient shorthand notation :: used for IPV6 that can be used as a place holder for zeros. For example

    ::1

really means

    00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:01

and

    FF:21::22:32

is the same as

    FF:21:00:00:00:00:00:00:00:00:00:00:00:00:22:32

we use *: in the same way for FFs so that

*:1 really means

    FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:01

These short cut notations makes it much easier to write GUID's.

{% include "./bottom_copyright.md" %}
