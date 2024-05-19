# Air Sensor MQTT Schema

The base schema path is `emf/air_quality_sensors/<name>/device/` where `<name>` is the configured name of the sensor.

| Topic                                 | Contents                                                     | Example Values                                               |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `system/name`                         | Name of the sensor¹                                          | main-bar                                                     |
| `system/location`                     | Location of the sensor                                       | Main Bar                                                     |
| `system/version/hw`                   | Hardware version²                                            | 1 or 2                                                       |
| `system/version/fw`                   | Firmware version                                             | 2.1                                                          |
| `system/sensors/names`                | Comma separated string containing sensor names, indicating the sensors that are present in the device³ | co2<br />eco2<br />tvoc<br />temp<br />humidity<br />pm10<br />pm2.5<br />pm1.0<br />pc10<br />pc5.0<br />pc2.5<br />pc1.0<br />pc0.5<br />pc0.3<br />vin<br />5v |
| `system/sensors/co2_sensor_pn`        | Part number of the CO2 sensor                                | "MH-Z19D" or "SCD40"                                         |
| `system/sensors/eco2_sensor_pn`       | Part number of the eCO2 sensor                               | "SGP30" or "None"                                            |
| `system/sensors/tvoc_sensor_pn`       | Part number of the TVOC sensor                               | "SGP30" or "None"                                            |
| `system/sensors/temp_sensor_pn`       | Part number of the temperature sensor                        | "SHT32" or "SHT35"                                           |
| `system/sensors/humidity_sensor_pn`   | Part number of the humidity sensor                           | "SHT32" or "SHT35"                                           |
| `system/sensors/pm_sensor_pn`         | Part number of the particulate matter (PM) sensor            | "PMSA003" or "None"                                          |
| `system/wifi/last_update`             | The device timestamp in milliseconds when the WiFi state last changed |                                                              |
| `system/wifi/disconnect_events`       | The number of WiFi disconnect events since the last power cycle | 0                                                            |
| `system/wifi/dhcp_timeout_events`     | The number of DHCP timeout events since the last power cycle | 0                                                            |
| `system/wifi/rssi`                    | The WiFi RSSI in dBm                                         | -70                                                          |
| `system/wifi/ip`                      | The device's IP address                                      | 10.20.30.40                                                  |
| `settings/update_rate`                | The rate at which the sensor sends updates, in milliseconds  | 10000                                                        |
| `settings/fan_wait_time`              | The delay between air cycling operations, in seconds         | 3600                                                         |
| `settings/fan_on_time`                | The amount of time the fan operates during air cycling operations, in seconds | 10                                                           |
| `settings/fan_recovery_time`          | The amount of time after an air cycling operation before sensor measurements resume, in seconds | 30                                                           |
| `timings/last_loop_start`             | The device timestamp in milliseconds at the start of the last update loop |                                                              |
| `timings/last_loop_end`               | The device timestamp in milliseconds at the end of the last update loop |                                                              |
| `timings/last_sensor_update_duration` | The amount of time it took to update sensors in the last measurement cycle |                                                              |
| `alarms/co2/threshold`                | The configured CO2 alarm level, in parts per million (ppm); disabled if zero | 1000                                                         |
| `alarms/co2/triggered`                | 1 if the CO2 alarm is currently triggered, otherwise 0       | 0/1                                                          |
| `alarms/eco2/threshold`               | The configured eCO2 alarm level, in parts per million (ppm)  | 1000                                                         |
| `alarms/eco2/triggered`               | 1 if the eCO2 alarm is currently triggered, otherwise 0      | 0/1                                                          |
| `alarms/tvoc/threshold`               | The configured TVOC alarm level, in parts per billion (ppb)  | 500                                                          |
| `alarms/tvoc/triggered`               | 1 if the TVOC alarm is currently triggered, otherwise 0      | 0/1                                                          |
| `sensor/co2/valid`                    | 1 if the CO2 sensor reading is valid, otherwise 0            | 0/1                                                          |
| `sensor/co2/level`                    | The CO2 level in parts per million (ppm)                     | 350                                                          |
| `sensor/co2/level_raw`                | The raw reading from the CO2 sensor                          |                                                              |
| `sensor/co2/internal_temperature`     | The internal temperature reading from the CO2 sensor, in °C  | 21.3                                                         |
| `sensor/co2/internal_humidity`        | The internal humidity reading from the CO2 sensor, in %RH    | 30.5                                                         |
| `sensor/co2/last_update`              | The device timestamp in milliseconds when the CO2 sensor was last updated |                                                              |
| `sensor/co2/error_count`              | The number of errors reported by the CO2 sensor              | 0                                                            |
| `sensor/co2/last_error`               | The device timestamp in milliseconds when the CO2 sensor last reported an error |                                                              |
| `sensor/eco2/valid`                   | 1 if the eCO2 sensor reading is valid, otherwise 0           | 0/1                                                          |
| `sensor/eco2/level`                   | The eCO2 level in parts per million (ppm)                    | 350                                                          |
| `sensor/eco2/last_update`             | The device timestamp in milliseconds when the eCO2 sensor was last updated |                                                              |
| `sensor/eco2/error_count`             | The number of errors reported by the eCO2 sensor             | 0                                                            |
| `sensor/eco2/last_error`              | The device timestamp in milliseconds when the eCO2 sensor last reported an error |                                                              |
| `sensor/tvoc/valid`                   | 1 if the TVOC sensor reading is valid, otherwise 0           | 0/1                                                          |
| `sensor/tvoc/level`                   | The TVOC level in parts per billion (ppb)                    | 150                                                          |
| `sensor/tvoc/internal_raw_h2`         | The raw H2 reading from the TVOC sensor                      |                                                              |
| `sensor/tvoc/internal_raw_ethanol`    | The raw Ethanol reading from the TVOC sensor                 |                                                              |
| `sensor/tvoc/last_update`             | The device timestamp in milliseconds when the TVOC sensor was last updated |                                                              |
| `sensor/tvoc/error_count`             | The number of errors reported by the TVOC sensor             | 0                                                            |
| `sensor/tvoc/last_error`              | The device timestamp in milliseconds when the TVOC sensor last reported an error |                                                              |
| `sensor/temp/valid`                   | 1 if the temperature sensor reading is valid, otherwise 0    | 0/1                                                          |
| `sensor/temp/level`                   | The temperature sensor reading in °C                         | 21.3                                                         |
| `sensor/temp/last_update`             | The device timestamp in milliseconds when the temperature sensor was last updated |                                                              |
| `sensor/temp/error_count`             | The number of errors reported by the temperature sensor      | 0                                                            |
| `sensor/temp/last_error`              | The device timestamp in milliseconds when the temperature sensor last reported an error |                                                              |
| `sensor/humidity/valid`               | 1 if the temperature sensor reading is valid, otherwise 0    | 0/1                                                          |
| `sensor/humidity/level`               | The temperature sensor reading in %RH                        | 30.5                                                         |
| `sensor/humidity/last_update`         | The device timestamp in milliseconds when the humidity sensor was last updated |                                                              |
| `sensor/humidity/error_count`         | The number of errors reported by the humidity sensor         | 0                                                            |
| `sensor/humidity/last_error`          | The device timestamp in milliseconds when the humidity sensor last reported an error |                                                              |
| `sensor/pm10/valid`                   | 1 if the PM10 sensor reading is valid, otherwise 0           | 0/1                                                          |
| `sensor/pm10/level`                   | The PM10 sensor reading in μg/m³                             | 200                                                          |
| `sensor/pm10/last_update`             | The device timestamp in milliseconds when the PM10 sensor was last updated |                                                              |
| `sensor/pm10/error_count`             | The number of errors reported by the PM10 sensor             | 0                                                            |
| `sensor/pm10/last_error`              | The device timestamp in milliseconds when the PM10 sensor last reported an error |                                                              |
| `sensor/pm2.5/valid`                  | 1 if the PM2.5 sensor reading is valid, otherwise 0          | 0/1                                                          |
| `sensor/pm2.5/level`                  | The PM2.5 sensor reading in μg/m³                            | 200                                                          |
| `sensor/pm2.5/last_update`            | The device timestamp in milliseconds when the PM2.5 sensor was last updated |                                                              |
| `sensor/pm2.5/error_count`            | The number of errors reported by the PM2.5 sensor            | 0                                                            |
| `sensor/pm2.5/last_error`             | The device timestamp in milliseconds when the PM2.5 sensor last reported an error |                                                              |
| `sensor/pm1.0/valid`                  | 1 if the PM1.0 sensor reading is valid, otherwise 0          | 0/1                                                          |
| `sensor/pm1.0/level`                  | The PM1.0 sensor reading in μg/m³                            | 200                                                          |
| `sensor/pm1.0/last_update`            | The device timestamp in milliseconds when the PM1.0 sensor was last updated |                                                              |
| `sensor/pm1.0/error_count`            | The number of errors reported by the PM1.0 sensor            | 0                                                            |
| `sensor/pm1.0/last_error`             | The device timestamp in milliseconds when the PM1.0 sensor last reported an error |                                                              |
| `sensor/pc10/valid`                   | 1 if the >10μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc10/level`                   | The >10μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc10/last_update`             | The device timestamp in milliseconds when the >10μm particle count sensor was last updated |                                                              |
| `sensor/pc10/error_count`             | The number of errors reported by the >10μm particle count sensor | 0                                                            |
| `sensor/pc10/last_error`              | The device timestamp in milliseconds when the >10μm particle count sensor last reported an error |                                                              |
| `sensor/pc5.0/valid`                  | 1 if the >5.0μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc5.0/level`                  | The >5.0μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc5.0/last_update`            | The device timestamp in milliseconds when the >5.0μm particle count sensor was last updated |                                                              |
| `sensor/pc5.0/error_count`            | The number of errors reported by the >5.0μm particle count sensor | 0                                                            |
| `sensor/pc5.0/last_error`             | The device timestamp in milliseconds when the >5.0μm particle count sensor last reported an error |                                                              |
| `sensor/pc2.5/valid`                  | 1 if the >2.5μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc2.5/level`                  | The >2.5μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc2.5/last_update`            | The device timestamp in milliseconds when the >2.5μm particle count sensor was last updated |                                                              |
| `sensor/pc2.5/error_count`            | The number of errors reported by the >2.5μm particle count sensor | 0                                                            |
| `sensor/pc2.5/last_error`             | The device timestamp in milliseconds when the >2.5μm particle count sensor last reported an error |                                                              |
| `sensor/pc1.0/valid`                  | 1 if the >1.0μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc1.0/level`                  | The >1.0μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc1.0/last_update`            | The device timestamp in milliseconds when the >1.0μm particle count sensor was last updated |                                                              |
| `sensor/pc1.0/error_count`            | The number of errors reported by the >1.0μm particle count sensor | 0                                                            |
| `sensor/pc1.0/last_error`             | The device timestamp in milliseconds when the >1.0μm particle count sensor last reported an error |                                                              |
| `sensor/pc0.5/valid`                  | 1 if the >0.5μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc0.5/level`                  | The >0.5μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc0.5/last_update`            | The device timestamp in milliseconds when the >0.5μm particle count sensor was last updated |                                                              |
| `sensor/pc0.5/error_count`            | The number of errors reported by the >0.5μm particle count sensor | 0                                                            |
| `sensor/pc0.5/last_error`             | The device timestamp in milliseconds when the >0.5μm particle count sensor last reported an error |                                                              |
| `sensor/pc0.3/valid`                  | 1 if the >0.3μm particle count sensor reading is valid, otherwise 0 | 0/1                                                          |
| `sensor/pc0.3/level`                  | The >0.3μm particle count sensor reading in particles per 0.1L of air | 200                                                          |
| `sensor/pc0.3/last_update`            | The device timestamp in milliseconds when the >0.3μm particle count sensor was last updated |                                                              |
| `sensor/pc0.3/error_count`            | The number of errors reported by the >0.3μm particle count sensor | 0                                                            |
| `sensor/pc0.3/last_error`             | The device timestamp in milliseconds when the >0.3μm particle count sensor last reported an error |                                                              |
| `sensor/vin/valid`                    | 1 if the VIN voltage measurement is valid, if not 0          | 0/1                                                          |
| `sensor/vin/level`                    | The voltage of the VIN sensor board's supply rail, in volts  | 5.0                                                          |
| `sensor/vin/last_update`              | The device timestamp in milliseconds when the VIN voltage sensor was last updated |                                                              |
| `sensor/5v/valid`                     | 1 if the 5V0 voltage measurement is valid, if not 0          | 0/1                                                          |
| `sensor/5v/level`                     | The voltage of the sensor board's 5V0 rail, in volts         | 5.0                                                          |
| `sensor/5v/last_update`               | The device timestamp in milliseconds when the 5V voltage sensor was last updated |                                                              |

**¹** See the locations table below for prospective locations.

**²** Hardware version 1 is the older design (SHT32 and MH-Z19D). Hardware version 2 is the newer design (SHT35, SCD40, SGP30, optionally an MH-Z19D for comparative measurement).

**³** The sensor names match the topic names in the `sensor` sub-topic. The order of the comma-separated values in the string matches the list of values shown in the example column.

## Locations (Prospective)

Everything here is **subject to change** once we get on site and discuss the details of where we're deploying things. I've specified twenty sensors (10x rev1, 10x rev2) but I don't know that we actually have ten of the rev1 boards.

| Location          | Name                | HW Version |
| ----------------- | ------------------- | ---------- |
| Arcade            | `arcade`            | 2          |
| Badge Tent        | `badge-tent`        | 2          |
| Bar               | `bar`               | 2          |
| Crew Tent         | `crew-tent`         | 2          |
| Family Lounge     | `family-lounge`     | 2          |
| First Aid         | `first-aid`         | 1          |
| Green Room        | `green-room`        | 1          |
| Lounge            | `lounge`            | 1          |
| Null Sector Cybar | `null-sector-cybar` | 2          |
| Null Sector Stage | `null-sector-stage` | 1          |
| Stage A           | `stage-a`           | 2          |
| Stage B           | `stage-b`           | 2          |
| Stage C           | `stage-c`           | 2          |
| Volunteer Tent    | `volunteer-tent`    | 2          |
| Workshop 1        | `workshop-1`        | 1          |
| Workshop 2        | `workshop-2`        | 1          |
| Workshop 3        | `workshop-3`        | 1          |
| Workshop 4        | `workshop-4`        | 1          |
| Workshop 5        | `workshop-5`        | 1          |
| Workshop 6        | `workshop-6`        | 1          |

