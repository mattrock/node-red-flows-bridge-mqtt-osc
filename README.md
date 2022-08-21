# node-red-flows-bridge-mqtt-osc
Use Node-RED to bridge Open Sound Control (OSC) with MQTT

When the attached flows.json is imported to Node-RED, it can be used to connect to ETC's EOS/Element lighting console via OSC.
When the ETC EOS software is enabled to send OSC via UDP, Node-RED will convert the address and value to topic and payload for MQTT.
With the current config, any MQTT messages addressed for EOS user 2 (/eos/user/2/{command}) will be converted back to OSC and
sent to ETC EOS as UDP OSC messages.  The flow will also configure the eos fader bank controls in banks of 10.

This will enable any level of control of ETC EOS via MQTT messages, but what specifically works well is associating faders to a home 
automation system. In this case, Homeseer with the MCS MQTT extension is used.  Once a device is created in HomeSeer to represent the
EOS fader, the device can then be linked to physical devices on the HomeSeer network.

The current use scenario utilizes circular linking between a no-load Insteon wall dimmer switch and fader 2 in fader bank 1 in ETC EOS.
The EOS fader is loaded with a bright cue for all accent lights in the room. When the wall switch is turned up, the fader will increase
with the bright cue piling on any effects which may be curretnly running on the accent light.
