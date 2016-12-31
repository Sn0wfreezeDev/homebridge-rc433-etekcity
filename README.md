# Homebridge RC433 Etekcity Plugin

This Homebridge plugin enables you to control 433mhz Etekcity switchs by a Raspberry Pi. (https://www.amazon.de/dp/B016I3TZ58/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=3NEM5I6QUP4AR&coliid=I166WF1IKFO0FK)
The plugin is based on the idea of FWeinb's rcswitch plugin (https://github.com/FWeinb/homebridge-rcswitch).
The Etekcity switches require a pulse length beside its controlling code given, therefore a basic rc433mhz
implementation does not work.

## Setup

1) Wire a 433Mhz RF transmitter and receiver kit to your Raspberry Pi. You can find several instructions on the
web (e.g. (German) http://tutorials-raspberrypi.de/raspberry-pi-funksteckdosen-433-mhz-steuern/).

2) Use wiring-pi and its rf sniffer to record the codes for your switches by launching the programm on your
Raspberry Pi und controlling the switches by the remote control. Be aware of the fact that there a several
implementations of the 433mhz protocol. The Etekcity switches require those which handle the pulse lenght.

3) Follow the intstructions to install Homebridge on your Raspberry Pi (https://github.com/nfarina/homebridge/wiki/Running-HomeBridge-on-a-Raspberry-Pi)

4) Install this plugin

```bash
npm i -g homebridge-rc433-etekcity
```

5) Rename the sample-config.json to config.json and integrate your switches in the accessories array. The pins
of the Raspberry Pi require root rights to control them. Therefore you have to save your config file not
in your users directory. Put it under `/root/.homebridge/config.json`.
If you are already running homekit with other apps integrate the accessories switches into your config.json
and move your config file to the path above.

6) If you want to start homebrige as a service atomaticlly when the Raspberry is turned on copy over
the file homebridge to `/etc/init.d/` on your Raspberry. The file homebridge assumes that