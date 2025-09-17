# fanatec-pedal-emulator-vrs

This is a modified version of fanatec-pedal-emulator by GeekyDeaks to read VRS DirectForce Pro Pedals instead of the HE Sprint pedals.

Small golang HID to UART proxy

Allows a set of USB pedals to be proxied to a Fanatec wheelbase and therefore
be used on console if the wheelbase supports it

# Setup

The Fanatec CSL Elite pedal control module uses a simple UART protocol to
communicate with the wheelbase. A 5v tolerant USB to RS232 TTL like the CP2102
can be used to interface with the pedal RJ12 port on the wheelbase.

# build/run proxy

    go run proxy.go [COMPORT]

e.g. `go run proxy.go COM3`. Find the name of your COM port in Device Manager

# Fanatec RJ12 pinouts on pedal control board

Looking from the top of the socket

|Socket / Pin | 1    | 2      | 3    | 4  | 5  | 6   |
|-------------|------|--------|------|----|----|-----|
|Gas          | 3.3v | Signal | NC   | NC | NC | GND |
|Brake        | 3.3v | S-     | S+   | NC | NC | GND |
|Clutch       | 3.3v | Signal | NC   | NC | NC | GND |
|WheelBase    | GND? | GND?   | GND? | RX | TX | Vcc |

Note RX / TX is from PoV of the control board

# Connecting PC to Fanatec CS DD+

Looking at the RJ12 port on the back of the wheelbase, I connected the pins in the following order (from left to right).

NC, TX, RX, NC, NC, GND

