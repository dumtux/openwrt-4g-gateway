# Connecting openWRT to Wifi

## 1: Enable Wifi interface
```
$ uci set wireless.@wifi-device[0].disabled="0"
$ uci commit wireless
$ wifi
```
## 2: Scan Wifi networks
```
$ iw dev wlan0 scan
```
## 3: Add the following lines to `/etc/config/network`
```
config interface 'wan'
    option proto 'dhcp'
```
## 4: Add the following lines to `/etc/config/wireless`, replace it with you information
```
config wifi-iface
    option network 'wan'
    option mode 'sta'
    option ssid 'YOUR_SSID'
    option encryption 'psk2'
    option device 'YOUR_WIFI_DEVICE'
    option key 'YOUR_PASSWORD'
```
## 5: Restart network service with
```
$ service network restart
```