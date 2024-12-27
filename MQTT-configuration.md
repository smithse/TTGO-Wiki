# MQTT data feed configuration

`rdzTTGOsonde` supports reporting decoded radiosode measurements and receiver telemetry over MQTT as newline-delimited JSON messages. Each of these messages can be parsed into an object - with `json.loads` in python, or `jq` for example. In the samples below, the messages are pretty-printed; on the wire they are a single line.

## MQTT active

This is the main control for enabling MQTT reporting. Prior to `dev20241225` this was a binary switch: if set to a non-zero value, MQTT was enabled. Note that many MQTT reporting issues can be traced to ACLs on the broker; if the main screen reports that MQTT is connected but no messages seem to be published, there is almost certainly an ACL blocking the message.

Since commit [56f8fe9aac3ca47c62d234349ff867f3367d04f2](https://github.com/dl9rdz/rdz_ttgo_sonde/commit/56f8fe9aac3ca47c62d234349ff867f3367d04f2)
this has changed to a bitfield which enables different message topics.

Note that reported GPS and system time may differ from actual time by up to one second due to internal caching; this is different from the time reported by the radiosonde.

#### 0x01: packet
```
{
    "lat": 37.80481,
    "lon": -122.02071,
    "alt": 7087.3,
    "vs": 4.6,
    "hs": 36.9,
    "climb": 4.6,
    "speed": 36.9,
    "dir": 82.7,
    "type":"RS41",
    "id": "W3110601",
    "ser": "W3110601",
    "frame": 2331,
    "vframe": 2331,
    "time": 1732490972,
    "sats": 12,
    "freq": 404.00,
    "rssi": 217,
    "afc": 4333,
    "launchKT": 0,
    "burstKT": 0,
    "countKT": 0,
    "crefKT": 0,
    "launchsite": "Oakland",
    "res": 0,
    "batt": 2.9
}
```

Measurements as reported by the currently tracked radiosonde

#### 0x02: uptime
```
{
    "uptime": 51122.9,
    "user": "radiosonde",
    "time": 2024-12-26 20:11:41,
    "rxlat": 37.744502,
    "rxlon":  -122.223611,
    "SW": "rdzTTGOsonde",
    "VER": "dev20241225"
}
```

basic information about the device including uptime in seconds, MQTT username, current time, and if configured - the static location.

#### 0x04: pmu
```
{
    "I_Batt": 351.0,
    "V_Batt": 4.184,
    "I_Vbus": 417.0,
    "V_Vbus": 5.046,
    "T_sys": 55.3
}
```

Power management unit information. PMU temperature (C), and current (mA) and voltage (volts) of the battery and USB rails. Positive current indicates battery charging, negative current indicates discharging.

#### 0x08: gps

```
{
    "valid": 1,
    "systime": "2024-12-27 00:30:03",
    "gpstime": "2024-12-27 00:30:04",
    "lat": 37.744502,
    "lon": -122.223611,
    "alt": 6,
    "course":0,
    "speed":0.0,
    "sat": 10
}
```

#### 0x10: rf

Depending on the screen mode, this will publish either the current listening frequency to the `qrg` topic or the peak detected RF frequency to the `spectrum` topic. 

QRG replicates the information on the scanner screen, indicating which entry is currently being searched.
```
{
    "num": 2,
    "type": "RS41",
    "site": "Oakland",
    "freq": 404.000
}
```

Spectrum gives the frequency and RSSI of the peak detected energy. This is not necessarily a radiosonde; it could be a source of local interference.
```
{
    "time": "2024-12-17 23:31:25",
    "peak": 400.390,
    "rssi": -87.5
}
```

#### 0x80: debug

This message class can be used as a reporting channel for generally unimportant diagnostic messages. Developers are encouraged to add additional type bits for messages with longer lasting value, and document those bits here.

## MQTT client ID

A string (eg. `oakrdz`) used as the base of the MQTT client identifier. A random, internally-generated, four digit suffix will be added to the actual connection client (eg. `oakrdz1234`) to prevent collisions in case of network timeouts and reconnections.

## MQTT server hostname

Hostname or IP address of the MQTT broker, eg. `mqtt.example.com` or `192.0.2.83`.

## MQTT port

Port where the broker is listening. Defaults to `1883` and should probably be left that way since TLS connections are not yet supported.

## MQTT username

Username for the MQTT connection.

## MQTT password

Password for the MQTT connection.

## MQTT prefix

Topic prefix, used to establish some structure on the messages. The default is `rdz_sonde_server/` but you could use any other meaningful string, such as `sonde/sea/`, `sonde/sfo/` and `sonde/lax/` if you had three receiver in the Seattle, San Francisco, and Los Angeles areas.

## MQTT Report Interval

Number of milliseconds at which to publish uptime, gps, and pmu metrics. Default value is 60000 (60s, 1 minute). Increase or decrease as you see fit.