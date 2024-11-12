# Equipment

## P-p-p-power connectors

Try for panel mount or...  something mount.

XT30 or barrel.  Not sure where my barrels are.  Barrel might b perfable for a 90 degree adapter.

## Regulator

Probalo go for 5v; not sure how much current is truly necessary, mostly depends on Tom Servo.

Remember to double-endpin the smol ones.

## Servo

Prlly go with HS-55 again, maybe HS-45HB.  Helo lack of stamdards.

Spex say 450mah stall curretn?  My domt belieb it.

## LC Filter

Should prlly put this downstream of the regulator?

## 5.8Ghz Video RX

### FR632

#### I/O
* GND
* Vcc (6-28v)
* Video out (prlly unused unless sending to DVR)
* RSSI CH1
* RSSI CH2

### Fartshat Module

Alternate RX.

Hrd to get RSSI pins sometimes, also annoybols to actually use.  Not shaped rite.  Butt possibly moar availble.

#### I/O

* 5v
* Unknown (great job Fartshat)
* Audio_R
* Audio_L
* Video
* Channel select bit 2?
* Channel select bit 1?
* Channel select bit 0?

## Microcontroller

###  Lolin ESP32-C3

ADCs are 12-bit.

I've never seen RSSI go past like 1.0v, and if it does it's probably because src so close it doesn't matter.  ADC_ATTEN_DB_2_5 might be just fine.

ADC2 is used by WiFi.  Could disable WiFi tho...

Need to check how to do multichannel continuous sampling in Arduino.  Likely will be typically awful.

#### I/O

Todo:  check boot pins

* GND
* 5v
* RSSI CH1 (GPIO0 - ADC1_0)
* RSSI CH2 (GPIO1 - ADC1_1)
* Servo (PWM) out (GPIO5 - Use LEDC channel)
* Vcc (battery level monitor - need voltage divider - GPIO4 - ADC1_4)
* RX - possible control via another Expresslrs RX; disable telemetry - (GPIO21 - UART)
* RGB LED status indicator - builtin - GPIO7

#### Accessories

##### Protoboard

Prlly need to xpand pinout.

##### OLED display

Lolin no makes these anymoar for some reason, n the clones don't come with buttons because f the customer amirite?

##### ExpressLRS Receiver

Allow gnd control from TX.

###### I/O

* GND
* 5v
* TX
* RX

# Software

## Filesystem

## JSON

### Main program config

* P-value
* CH1 offset/scale
* CH2 offset/scale
* Center value
* Difference threshold
* Min/max servo travel
* Reverse/channel mapping?

### WiFi config

* SSID
* PSK
* Channel

## OneButton comtrol

Short press - start/stop tracker.
Long press - start/stop wifi.

## RGB LED

Red - tracking stopped
Green - tracking started

Mite do a flash sequence, not sure.  Want to reflect Wifi status.

## Web server

Prlly should disable WiFi when not in use.  Long press + debounce?

## OLED

## Crossfire

## PID controller

probably not necessary cuz errthang so sloooowww
