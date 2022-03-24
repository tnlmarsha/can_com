* [CAN communication using Python](#can-communication-using-python)
  * [Python Modules](#python-modules)
    * [Goals](#goals)
      * [Implement DBC File](#implement-dbc-file)
        * [Resources](#resources)
      * [Encode CAN data](#encode-can-data)
      * [Decode CAN data](#decode-can-data)
      * [Simulate BMS/VCS](#simulate-bmsvcs)


# CAN communication using Python
Note: The intent of this repository is to show easy, accessible methods of CAN communication using Python; Pythonic design choices shall not be of primary concern. Additionally, CAN communication protocol reference is of type J1939, where more details regarding this protocol can be found [here](https://www.kvaser.com/can-protocol-tutorial/). Finally, DBC file syntax differs from appliction to application, but just as with CAN, we will be discussing DBCs descibing J1939. 

## Python Modules
- [`cantools`](https://cantools.readthedocs.io/en/latest/#can-bus-tools)
  - [installation and tutorial](https://cantools.readthedocs.io/en/latest/#installation)
- [`python-can`](https://python-can.readthedocs.io/en/master/#python-can)
  - [installation and tutorial](https://python-can.readthedocs.io/en/master/installation.html#installation)

### Goals
#### Implement DBC File
DBC (CAN database) files use a special syntax in plain (ASCII) text to describe CAN (Controller Area Network) data. Commercially available and open source methods of reading, creating, modifying, and using DBC files are readily available. I'm partial to open source, so here is how you can be too!
- simple DBC creation using `cantools`
  - created DBC will be used to encode and decode CAN messages
##### Resources
- [DBC tutorial](https://docs.openvehicles.com/en/latest/components/vehicle_dbc/docs/dbc-primer.html#dbc-introduction)
- Python 3rd-party module, `cantools`

#### Encode CAN data
DBC created above shall serve as the translater allowing us to write data as if sending CAN messages, which is common when simulating VCS commands. 
- determine desired parameters based on previous DBC definition
- encode data from perspective of BMS or VCS
#### Decode CAN data
Data shall be received as encoded above. 
- capture and decode CAN messages per DBC specification
- keep track of data for futher use, if necessary
#### Simulate BMS/VCS
Send commands to receive desired data from BMS, and to command actions based on response from BMS. 
- determine desired data
- determine desired commanding actions and resonses
- define guidance with regard to defined DBC parameters