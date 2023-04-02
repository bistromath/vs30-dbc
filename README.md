# vs30-dbc
DBC file for CAN B on the VS30 Sprinters

[DBC](https://docs.openvehicles.com/en/latest/components/vehicle_dbc/docs/dbc-primer.html) is the industry-standard file format to describe [CAN bus](https://en.wikipedia.org/wiki/CAN_bus) messages. This repo is a work in progress to decode CAN bus B of a 2020 Sprinter (VS30). Its applicability to other vehicles is unknown.
The CAN interface used to gather the data used to reverse-engineer the DBC was the CAN B interface on the PSM wiring harness under the driver's seat; I believe this interface is firewalled from the actual CAN B bus, but the messages should be the same wherever they are gathered.

## Usage

There are a bunch of tools out there to work with DBC files and parse CAN messages. Here's an example using the Python [cantools](https://pypi.org/project/cantools/) module.
```
  $ python3
  >>> import cantools
  >>> db = cantools.database.load_file('vs30_canb_psm.dbc')
  >>> db.decode_message(0x3a5, b"\x00\x10\x01\x00\x00\x00\x00\x00")
  {'SlidingDoorState': 'Closed'}
  >>>
```

As I figure out more messages they will be added to the DBC. Contributions are welcome!
