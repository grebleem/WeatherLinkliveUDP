# WeatherLinkLiveUDP
Weewx Driver for The WeatherLink Live (WLL). It implements a HTTP interface for getting current weather data and can support continuous requests as often as every 10 seconds.
Also it collects a real-time 2.5 sec broadcast for wind speed and rain over UDP port 22222.

[See Davis weatherlink-live-local-api](https://weatherlink.github.io/weatherlink-live-local-api/)

### Installation

1) Download the driver

```
wget -O weatherlinkliveudp.zip https://github.com/grebleem/*************/archive/master.zip
```

2) Install the driver

```
sudo wee_extension --install weatherlinkliveudp.zip
```

3) Set the `station_type` to `WLL` and modify the `[WLL]` stanza in `weewx.conf`:
```
[Station]

    # Set the type of station.
    station_type = WeatherLinkLiveUDP
```
```
[WeatherLinkLiveUDP]
    wll_ip = 192.168.1.47
    poll_interval = 15    # number of seconds
    ISS_id = 1
    wind_id = 4
    driver = user.weatherlinkliveudp
```

4) Restart WeeWX

```
sudo /etc/init.d/weewx restart
```

Note: The driver requires the Python `requests` library. To install it:

```
sudo apt-get update 
sudo apt-get install python-requests
```
or
```
pip install requests
```
