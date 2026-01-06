

# Apple's mobile processors

Dezső Sima

Vers. 1.4

December 2018

© Sima Dezső, 2018

## Preface

Apple does not reveal any details about their mobile devices.

There are however **two valuable sources** of information relating to Apple's SOC's.

1. A few companies **teardown** electronic devices, such as smartphones, tablets, etc., i.e. they disassemble these products, identify components and functionality, and publish their results either free of charge or for fees, like Chipworks, Techinsights, Ifixit.
2. In a few cases **even Apple reveals data for optimizing compiler operation**, as in case of the Cyclone core used in their A7/A8/A8X processors.

The information included in this chapter originates in most parts from these sources.

### Remark

Throughout this chapter the designations of **application processor, processor and SOC** are used as synonyms.

## Contents -1

- 1. Overview of Apple's mobile processors
- 2. Apple's original iPhone
- 3. Apple A4
- 4. Apple A6 with dual Swift cores
- 5. Apple A7 with dual Cyclone cores
- 6. Apple A8 with dual Typhoon cores
- 7. Apple A8X with triple Typhoon cores
- 8. Apple A9 with dual Twister cores
- 9. Apple A9X with dual Twister cores

## Contents -2

- 10. Apple A10 with dual big and dual LITTLE cores
- 11. Apple A10X with 3 dual and 3 LITTLE cores
- 12. Apple A11 with dual big and quad LITTLE cores
- 13. Apple A12 with dual big and quad LITTLE cores
- 14. Apple A12X with quad big and quad LITTLE cores
- 15. References

## 1. Overview of Apple's mobile processors

## 1. Overview of Apple's mobile processors (1)

## 1. Overview of Apple's mobile processors Main features of Apple's early iPhones-1 [4]

|                | 2007                                      | 2008                                | 2009                                 | 2010                               |
|----------------|-------------------------------------------|-------------------------------------|--------------------------------------|------------------------------------|
|                | <img alt="Image of the original iPhone"/> | <img alt="Image of the iPhone 3G"/> | <img alt="Image of the iPhone 3GS"/> | <img alt="Image of the iPhone 4"/> |
| Code Name      | iPhone M68                                | iPhone 3G N82                       | iPhone 3GS N88                       | iPhone 4 N90                       |
| Model Name     | iPhone 1,1                                | iPhone 1,2                          | iPhone 2,1                           | iPhone 3,1                         |
| OS             | iPhone OS 1.0                             | iPhone OS 2.0                       | iPhone OS 3.0                        | iOS 4                              |
| Screen Size    | 3.5-inch 480x320 at 163ppi                | 3.5-inch 480x320 at 163ppi          | 3.5-inch 480x320 at 163ppi           | 3.5-inch IPS 960x640 at 326ppi     |
| System-on-chip | Samsung S5L8900                           | Samsung S5L8900                     | Samsung APL0298C05                   | Apple A4                           |
| CPU            | ARM 1176JZ(F)-S                           | ARM 1176JZ(F)-S                     | 600MHz ARM Cortex A8                 | 800MHz ARM Cortex A8               |
| GPU            | Power VR MBX Lite 3D                      | Power VR MBX Lite 3D                | PowerVR SGX535                       | PowerVR SGX535                     |
| RAM            | 128MB                                     | 128MB                               | 256MB                                | 512MB                              |
| Storage        | 4GB/8GB (16GB later)                      | 8GB/16GB                            | 16GB/32GB                            | 16GB/32GB                          |
| Rear Camera    | 2MP                                       | 2MP                                 | 3MP/480p                             | 5MP/720p, f2.8, 1.75µ              |
| Front Camera   | None                                      | None                                | None                                 | VGA                                |

## 1. Overview of Apple's mobile processors (2)

### Main features of Apple's early iPhones-2 [4]

|                       | 2011                            | 2012                                      | 2013                                      | 2013                                      |
|-----------------------|---------------------------------|-------------------------------------------|-------------------------------------------|-------------------------------------------|
|                       | <img alt="Image of iPhone 4S"/> | <img alt="Image of iPhone 5"/>            | <img alt="Image of iPhone 5c"/>           | <img alt="Image of iPhone 5s"/>           |
| <b>Code Name</b>      | iPhone 4S                       | iPhone 5                                  | iPhone 5c                                 | iPhone 5s                                 |
| <b>Model Name</b>     | N94<br>iPhone 4,1               | N41<br>iPhone 5,1                         | N48<br>iPhone 5,3                         | N51<br>iPhone 6,1                         |
| <b>OS</b>             | iOS 5                           | iOS 6                                     | iOS 7                                     | iOS 7                                     |
| <b>Screen Size</b>    | 3.5-inch IPS 960x640 at 326ppi  | 4-inch 1136x640 in-cell IPS LCD at 326ppi | 4-inch 1136x640 in-cell IPS LCD at 326ppi | 4-inch 1136x640 in-cell IPS LCD at 326ppi |
| <b>System-on-chip</b> | Apple A5                        | Apple A6                                  | Apple A6                                  | 64-bit Apple A7, M7 motion co-processor   |
| <b>CPU</b>            | 800MHz dual-core ARM Cortex A9  | 1.2GHz dual-core Swift (ARM v7s)          | 1.2GHz dual-core Swift (ARM v7s)          | Swift (ARM v8)                            |
| <b>GPU</b>            | PowerVR dual-core SGX543MP4     | PowerVR triple-core SGX543MP3             | PowerVR triple-core SGX543MP3             | PowerVR Series 6                          |
| <b>RAM</b>            | 512MB                           | 1GB                                       | 1GB                                       | TBD                                       |
| <b>Storage</b>        | 16GB/32GB/64GB                  | 16GB/32GB/64GB                            | 16GB/32GB                                 | 16GB/32GB/64GB                            |
| <b>Rear Camera</b>    | 8MP/1080p, f2.4, BSI, 1.4 $\mu$ | 8MP/1080p, f2.4, BSI, 1.4 $\mu$           | 8MP/1080p, f2.4, BSI, 1.4 $\mu$           | 8MP/1080p, f2.2, BSI, 1.5 $\mu$           |
| <b>Front Camera</b>   | VGA                             | 1.2MP/720p, BSI                           | 1.2MP/720p, BSI                           | 1.2MP/720p, BSI                           |

## 1. Overview of Apple's mobile processors (3)

### Main features of Apple's early iPads -1 [5]

|                | iPad                                                   | iPad 2                                                 | iPad 3                                                 | iPad mini                                              | iPad 4                                                 | iPad mini Retina                                                           | iPad Air                                                                  |
|----------------|--------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|----------------------------------------------------------------------------|---------------------------------------------------------------------------|
| Code Name      | K48                                                    | K94                                                    | J1, J2                                                 | J65                                                    |                                                        | J85                                                                        | J72                                                                       |
| Model Name     | iPad 1,1                                               | iPad 2,1                                               | iPad 3,1                                               | iPad 2,5                                               | iPad 3,4                                               |                                                                            | iPad 4,1                                                                  |
| OS             | iPhone OS 3,2                                          | iOS OS 4,3                                             | iOS 5,1                                                | iOS 6                                                  | iOS 6                                                  | iOS 7                                                                      | iOS 7                                                                     |
| Screen Size    | 9.7-inch IPS LED<br>1024x768 @ 132 ppi                 | 9.7-inch IPS LED<br>1024x768 @ 132 ppi                 | 9.7-inch IPS LED<br>2048x1536 @ 264 ppi                | 7.9-inch IPS LED<br>1024x768 @ 163 ppi                 | 9.7-inch IPS LED<br>2048x1536 @ 264 ppi                | 7.9-inch IPS LED<br>2048x1536 @ 326 ppi                                    | 9.7-inch IPS LED<br>2048x1536 @ 264 ppi                                   |
| System-on-chip | Apple A4                                               | Apple A5                                               | Apple A5X                                              | Apple A5                                               | Apple A6X                                              | 64-bit Apple A7, M7<br>motion c-processor                                  | 64-bit Apple A7, M7<br>motion c-processor                                 |
| CPU            | 800MHz ARM Cortex A8                                   | 1GHz dual-core ARM<br>Cortex A9                        | 1GHz dual-core ARM<br>Cortex A9                        | 1GHz dual-core ARM<br>Cortex A9                        | 1.4GHz dual-core Swift<br>ARM v7s                      | Dual-core Cyclone<br>(ARM v8)                                              | Dual-core Cyclone<br>(ARM v8)                                             |
| GPU            | PowerVR SGX535                                         | PowerVR dual-core<br>SGX543MP2                         | PowerVR quad-core<br>SGX543MP4                         | PowerVR dual-core<br>SGX543MP2                         | PowerVR quad-core<br>SGX554MP4                         | PowerVR Series 6                                                           | PowerVR Series 6                                                          |
| Coprocessor    | None                                                   | None                                                   | None                                                   | None                                                   | None                                                   | M7 Motion                                                                  | M7 Motion                                                                 |
| RAM            | 256MB                                                  | 512MB                                                  | 1GB                                                    | 512MB                                                  | 1GB                                                    | TBD                                                                        | TBD                                                                       |
| Storage        | 16GB/32GB/64GB                                         | 16GB/32GB/64GB                                         | 16GB/32GB/64GB                                         | 16GB/32GB/64GB                                         | 16GB/32GB/64GB/<br>128GB                               | 16GB/32GB/64GB/<br>128GB                                                   | 16GB/32GB/64GB/<br>128GB                                                  |
| Top Data Speed | HSPA                                                   | HSPA                                                   | LTE                                                    | LTE                                                    | LTE                                                    | LTE                                                                        | LTE                                                                       |
| SIM            | Micro                                                  | Micro                                                  | Micro                                                  | Nano                                                   | Micro                                                  | Nano                                                                       | Nano                                                                      |
| Rear Camera    | None                                                   | 1.3mo/720p                                             | 5mp, 1080p                                             | 5mp, 1080p                                             | 5mp, 1080p                                             | 5mp, 1080p                                                                 | 5mp, 1080p                                                                |
| Front Camera   | None                                                   | 0.3mp/VGA                                              | 0.3mp/VGA                                              | 1.2mp, 720p                                            | 1.2mp, 720p                                            | 1.2mp, 720p                                                                | 1.2mp, 720p                                                               |
| Bluetooth      | Bluetooth 2.1 + EDR                                    | Bluetooth 2.1 + EDR                                    | Bluetooth 4.0                                          | Bluetooth 4.0                                          | Bluetooth 4.0                                          | Bluetooth 4.0                                                              | Bluetooth 4.0                                                             |
| WiFi           | 802.11 a/b/g/n                                         | 802.11 a/b/g/n                                         | 802.11 a/b/g/n                                         | 802.11 a/b/g/n                                         | 802.11 a/b/g/n                                         | 802.11 a/b/g/n MIMO                                                        | 802.11 a/b/g/n MIMO                                                       |
| GPS            | aGPS                                                   | aGPS                                                   | aGPS, GLONASS                                          | aGPS, GLONASS                                          | aGPS, GLONASS                                          | aGPS, GLONASS                                                              | aGPS, GLONASS                                                             |
| Sensors        | Accelerometer, proximity,<br>compass                   | Accelerometer,<br>proximity, compass,<br>gyroscope     | Accelerometer,<br>proximity, compass,<br>gyroscope     | Accelerometer,<br>proximity, compass,<br>gyroscope     | Accelerometer,<br>proximity, compass,<br>gyroscope     | Accelerometer,<br>proximity, compass,<br>gyroscope                         | Accelerometer,<br>proximity, compass,<br>gyroscope                        |
| Speakers       | Mono                                                   | Mono                                                   | Mono                                                   | Stereo                                                 | Mono                                                   | Stereo                                                                     | Stereo                                                                    |
| Connector      | 30-pin Dock                                            | 30-pin Dock                                            | 30-pin Dock                                            | Lightning                                              | Lightning                                              | Lightning                                                                  | Lightning                                                                 |
| Size           | 9.56x7.47x0.53                                         | 9.5x7.31x0.34 inches                                   | 9.5x7.31x0.37 inches                                   | 7.87x5.3x0.28 inches                                   | 9.5x7.31x0.37 inches                                   | 7.87x5.3x0.29 inches                                                       | 9.4x6.6x0.29 inches                                                       |
| Weight         | 1.5 lbs                                                | 1.33 lbs                                               | 1.44 lbs                                               | 0.68 lbs                                               | 1.44 lbs                                               | 0.73 lbs                                                                   | 1 lbs                                                                     |
| Battery        | 25 watt hour                                           | 25 watt hour                                           | 42.5 watt hour                                         | 16.3 watt hour                                         | 42.5 watt hour                                         | 23.8 watt hour                                                             | 32.4 watt hour                                                            |
| Colors         | Black                                                  | Black/White                                            | Black/White                                            | Slate/Silver                                           | Black/White                                            | Space gray/Silver                                                          | Space gray/Silver                                                         |
| Price          | Wi-Fi \$499, \$599, \$699,<br>Data \$629, \$729, \$829 | Wi-Fi \$499, \$599, \$699,<br>Data \$629, \$729, \$829 | Wi-Fi \$499, \$599, \$699,<br>Data \$629, \$729, \$829 | Wi-Fi \$329, \$429, \$529,<br>Data \$459, \$559, \$659 | Wi-Fi \$499, \$599, \$699,<br>Data \$629, \$729, \$829 | Wi-Fi \$399, \$499,<br>\$599, \$699, Data<br>\$529, \$629, \$729,<br>\$829 | Wi-Fi \$499, \$599,<br>\$699, \$799 Data<br>\$629, \$729, \$829,<br>\$929 |
| Release Date   | 2010-04-03                                             | 2011-03-11                                             | 2012-03-16                                             | 2012-11-02                                             | 2012-11-02                                             | 2013-11                                                                    | 2013-11-01                                                                |

## 1. Overview of Apple's mobile processors (4)

### Main features of Apple's early iPads -2 [6]

![Images of five different Apple iPad models: Air, Air 2, Mini, Mini 2, and Mini 3.](349ca0a6a9c2e2651a4deeeaf8be6da1_img.jpg)

Images of five different Apple iPad models: Air, Air 2, Mini, Mini 2, and Mini 3.

|                           | Air                                                         | Air 2                                                       | Mini                                                        | Mini 2                                                      | Mini 3                                                      |
|---------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|
| Price                     | Starts at £319 (Wi-Fi)<br>Starts at £419 (Wi-Fi + Cellular) | Starts at £399 (Wi-Fi)<br>Starts at £499 (Wi-Fi + Cellular) | Starts at £199 (Wi-Fi)<br>Starts at £299 (Wi-Fi + Cellular) | Starts at £239 (Wi-Fi)<br>Starts at £339 (Wi-Fi + Cellular) | Starts at £319 (Wi-Fi)<br>Starts at £419 (Wi-Fi + Cellular) |
| Display                   | 9.7-inch Retina<br>2048x1536 res<br>264 ppi                 | 9.7-inch Retina<br>2048x1536 res<br>264 ppi                 | 7.9-inch<br>1024x768 res<br>163 ppi                         | 7.9-inch Retina<br>2048x1536 res<br>326 ppi                 | 7.9-inch Retina<br>2048x1536 res<br>326 ppi                 |
| Wi-Fi Capacity            | 16GB, 32GB                                                  | 16GB, 64GB, 128GB                                           | 16GB                                                        | 16GB, 32GB                                                  | 16GB, 64GB, 128GB                                           |
| Wi-Fi + Cellular Capacity | 16GB, 32GB                                                  | 16GB, 64GB, 128GB                                           | 16GB                                                        | 16GB, 32GB                                                  | 16GB, 64GB, 128GB                                           |
| Preinstalled Apple SIM    | No                                                          | Yes (Wi-Fi + Cellular)                                      | No                                                          | No                                                          | Yes (Wi-Fi + Cellular)                                      |
| Processor                 | A7 chip with 64-bit architecture, M7 motion coprocessor     | A8X chip with 64-bit architecture, M8 motion coprocessor    | A5 Chip                                                     | A7 chip with 64-bit architecture, M7 motion coprocessor     | A7 chip with 64-bit architecture, M7 motion coprocessor     |

## 1. Overview of Apple's mobile processors (5)

### Main features of Apple's 32-bit application processors used in their mobiles (1)

| Appl. proc. | Model no. | Image    | Node  | Die size             | CPU                      | CPU ISA | CPU cache                              | GPU                                           | Memory (up to)                                                                   | Intro.           | Utilizing devices                                                                   |
|-------------|-----------|----------|-------|----------------------|--------------------------|---------|----------------------------------------|-----------------------------------------------|----------------------------------------------------------------------------------|------------------|-------------------------------------------------------------------------------------|
| S5L8900X    | S5L8900X  | S5L8900X | 90 nm | 72 mm <sup>2</sup>   | 1x ARM1176 412 MHz       | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103 MHz                    | 128 MB<br>16-bit SCh<br>LPDDR-266<br>(532 MB/sec)                                | 6/2007<br>6/2008 | • iPhone (2G)<br>• iPod Touch (1st gen.)<br>• iPhone 3G                             |
|             |           |          | 65 nm | 36 mm <sup>2</sup>   | 1x ARM1176 412-533 MHz   | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103-133 MHz                | 32/128 MB<br>32-bit SCh<br>LPDDR-133                                             | 9/2008           | • iPod Touch (2nd gen.)<br>• iPod Nano (4th gen.)                                   |
| A4          | A4        | A4       | 65 nm | 71.8 mm <sup>2</sup> | 1x Cortex-A8 600 MHz     | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150 MHz (1.2 GFLOPS)         | 256 MB<br>32-bit SCh<br>LPDDR-400<br>(1.6 GB/sec)                                | 6/2009           | • iPhone 3GS                                                                        |
|             |           |          | 45 nm | 41.6 mm <sup>2</sup> | 1x Cortex-A8 600-800 MHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150-200 MHz (1.2-1.6 GFLOPS) | 256 MB<br>32-bit SCh<br>LPDDR-400<br>(1.6 GB/sec)                                | 9/2009           | • iPod Touch (3rd gen.)                                                             |
| A4          | A4        | A4       | 45 nm | 53.3 mm <sup>2</sup> | 1x Cortex-A8 0.8-1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 512 KB | PowerVR SGX535 @ 200-250 MHz (1.6-2 GFLOPS)   | 256 MB (iPad)<br>512 MB<br>(iPhone 4)<br>32-bit DCh<br>LPDDR-400<br>(3.2 GB/sec) | 3/2010           | • iPad (1st gen.)<br>• iPhone 4<br>• iPod Touch (4th gen.)<br>• Apple TV (2nd gen.) |
|             |           |          | 45 nm | 53.3 mm <sup>2</sup> | 1x Cortex-A8 0.8-1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 512 KB | PowerVR SGX535 @ 200-250 MHz (1.6-2 GFLOPS)   | 256 MB (iPad)<br>512 MB<br>(iPhone 4)<br>32-bit DCh<br>LPDDR-400<br>(3.2 GB/sec) | 3/2010           | • iPad (1st gen.)<br>• iPhone 4<br>• iPod Touch (4th gen.)<br>• Apple TV (2nd gen.) |

## 1. Overview of Apple's mobile processors (6)

### Main features of Apple's 32-bit application processors used in their mobiles (2)

| Appl. proc. | Model no.          | Image                      | Node          | Die size              | CPU                         | CPU ISA | CPU cache                            | GPU                                                            | Memory (up to)                                      | Intro.  | Utilizing devices                                                   |
|-------------|--------------------|----------------------------|---------------|-----------------------|-----------------------------|---------|--------------------------------------|----------------------------------------------------------------|-----------------------------------------------------|---------|---------------------------------------------------------------------|
| A5          | APL0498 or S5L8940 | <img alt="A5 Die Image"/>  | 45 nm         | 122.2 mm <sup>2</sup> | 2x Cortex-A9<br>0.8–1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2011  | • iPad 2<br>• iPhone 4S                                             |
|             | APL2498 or S5L8942 | <img alt="A5 Die Image"/>  | 32 nm<br>HKMG | 69.6 mm <sup>2</sup>  | 2x Cortex-A9<br>0.8–1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2012  | • iPad 2<br>(iPad 2,4)<br>• iPod Touch<br>(5th gen.)<br>• iPad Mini |
|             | APL7498 or S5L8947 | <img alt="A5 Die Image"/>  | 32 nm<br>HKMG | 37.8 mm <sup>2</sup>  | 1x Cortex-A9<br>1.0 GHz     | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2013  | • AppleTV 3<br>(AppleTV3,2)                                         |
| A5X         | APL5498 or S5L8945 | <img alt="A5X Die Image"/> | 45 nm         | 165 mm <sup>2</sup>   | 2x Cortex-A9<br>1.0 GHz     | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP4 (4C)<br>@ 250 MHz<br>(32 GFLOPS)          | 1 GB<br>32-bit 4Ch<br>LPDDR2-800<br>(12.8 GB/sec)   | 3/2012  | • iPad<br>(3rd gen.)                                                |
| A6          | APL0598 or S5L8950 | <img alt="A6 Die Image"/>  | 32 nm<br>HKMG | 96.7 mm <sup>2</sup>  | 2x Swift<br>1.3 GHz         | ARMv7s  | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP3 (3C)<br>@ 266 MHz<br>(25.5 GFLOPS)        | 1 GB<br>32-bit DCh<br>LPDDR2-1066<br>(8.528 GB/sec) | 9/2012  | • iPhone 5<br>• iPhone 5C                                           |
| A6X         | APL5598 or S5L8955 | <img alt="A6X Die Image"/> | 32 nm<br>HKMG | 123 mm <sup>2</sup>   | 2x Swift<br>1.4 GHz         | ARMv7s  | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX554MP4 (4C)<br>@ 266 MHz<br>(68.1 GFLOPS)        | 1 GB<br>32-bit 4Ch<br>LPDDR2-1066<br>(17.1 GB/sec)  | 10/2012 | • iPad<br>(4th gen.)                                                |

## 1. Overview of Apple's mobile processors (7)

### Main features of Apple's 64-bit application processors used in their mobiles (1)

| Appl. proc. | Model no.                           | Image                       | Node                         | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.  | Utilizing devices                        |
|-------------|-------------------------------------|-----------------------------|------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|---------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | <img alt="A7 chip image"/>  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>LS: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013  | iPhone 5S<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | <img alt="A7 chip image"/>  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>LS: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013 | iPad Air 9.7"                            |
| A8          | APL1011                             | <img alt="A8 chip image"/>  | 20 nm HKMG                   | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>LS: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014  | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | <img alt="A8X chip image"/> | 20 nm HKMG                   | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>LS: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR3-1600 (25.6 GB/sec)      | 10/2014 | iPad Air 2 9.7"                          |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | <img alt="A9 chip image"/>  | 16 nm FinFET<br>14 nm FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015  | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | <img alt="A9X chip image"/> | 16 nm FinFET                 | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015 | iPad Pro 9.7"<br>iPad Pro 12.9"          |

LS: System cache, it services the entire SoC

## 1. Overview of Apple's mobile processors (8)

### Main features of Apple's 64-bit application processors used in their mobiles (2)

| Appl. proc.S  | Model no.      | Image                           | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                               | Memory (up to)     | Intro.  | Utilizing devices                                 |
|---------------|----------------|---------------------------------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|-------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)  | APL1W24        | <img alt="Image of A10 chip"/>  | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz (>250 GFLOPS) (redesigned) | 2 GB/3 GB LPDDR4   | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion) | APL1071 (TSMC) | <img alt="Image of A10X chip"/> | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                         | 3 GB/4 GB LPDDR4   | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic    | APL1W72 (TSMC) | <img alt="Image of A11 chip"/>  | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.39 GHz) + 4x Mistral (1.42 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                             | 2 GB/3 GB? LPDDR4X | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic    | APL1W82 (TSMC) | <img alt="Image of A12 chip"/>  | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                             | 3 GB/4 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic   | APL1083 (TSMC) | <img alt="Image of A12X chip"/> | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                             | 6 GB LPDDR4X       | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

## 1. Overview of Apple's mobile processors (9)

**Note** that the X-tagged processors, like A6X, A8X, A9X are primarily targeting tablets, whereas those without the X tag are primarily smartphones.

## 1. Overview of Apple's mobile processors (10)

### Evolution of CPU architectures in Apple's mobiles

![](b3df5964338063224492c01f09e4fed6_img.jpg)

Diagram illustrating the CPU architecture of mobile processors:

- Single CPU core
- Multiple CPU cores
  - Symmetrical multicores
  - big.LITTLE core clusters
    - Exclusive cluster allocation
    - Inclusive core allocation (GTS)
  - DynamIQ core clusters

![](cbc4516eb885829fe8c9dabc0946dcbe_img.jpg)

| Apple               | ARM1176 (2007) until A4 (2010) | → | A5 (2011) (2C)                       | → | A10 (2016) (2+2)                     | → | A11 (2017) (2+4)  |   |                   |
|---------------------|--------------------------------|---|--------------------------------------|---|--------------------------------------|---|-------------------|---|-------------------|
| Samsung Exynos      | 3110 (2010)                    | → | 3250 2C (2011)<br>4412 4C (2012)     | → | 5410 (2013) (4+4)                    | → | 5420 (2013) (4+4) | → | 9810 (2018) (4+4) |
| Qualcomm Snapdragon | MSM 7225 (2007)                | → | 8260 2C (2013)<br>400 4C (2013)      | → | 808 (2+4) (2014)<br>810 (4+4) (2015) | → | 845 (2018) (4+4)  |   |                   |
| Huawei Kirin        | (K3V1) (2009)                  | → | (K3V2 (2012))                        | → | 920 (4+4) (2014)                     |   |                   |   |                   |
| MediaTek            | MT6218B (2003)                 | → | MT6582 4C (2013)<br>MT6592 8C (2013) | → | MT6595 8C (2014)                     |   |                   |   |                   |

## 1. Overview of Apple's mobile processors (11)

Key features of Apple's 32-bit application processors (based on [2]) -1

| 2012 | Apple Swift (A6)   | 3-wide (32-bit) | 3 decode | 15+ Stages<br>Out-of-Order Scheduler<br>Pipeline<br>Pipeline<br>Pipeline | 2 cores | 1.3 GHz      |
|------|--------------------|-----------------|----------|--------------------------------------------------------------------------|---------|--------------|
| 2011 | ARM Cortex-A9 (A5) | 2-wide (32-bit) | 2 decode | 13 Stages<br>In-Order<br>Pipeline<br>Pipeline                            | 2 cores | 0.8-1.0 GHz  |
| 2009 | ARM Cortex-A8 (A4) | 2-wide (32-bit) | 2 decode | 13 Stages<br>In-Order<br>Pipeline<br>Pipeline                            | 1 core  | 600-1000 MHz |
| 2007 | ARM 1176           | 1-wide (32-bit) | 1 decode | 8 Stages<br>In-Order<br>Pipeline                                         | 1 core  | 412-533 MHz  |

## 1. Overview of Apple's mobile processors (12)

### Key features of Apple's 64-bit application processors (based on [2]) -1

| 2017 | Bionic (A11)           | 6-wide (64-bit) | 6 decode | Monsoon<br>Out-of-Order Scheduler<br>Stages<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline   | 2 big cores (Monsoon)<br>+ 4 LITTLE cores (Mistral)      | 2.39 GHz/<br>1.42 GHz |
|------|------------------------|-----------------|----------|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------|-----------------------|
| 2016 | Fusion (A10/A10X)      | 6-wide (64-bit) | 6 decode | Hurricane<br>Out-of-Order Scheduler<br>Stages<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline | 2-3 big cores (Hurricane)<br>+ 2-3 LITTLE cores (Zephyr) | 2.33 GHz/<br>1.1 GHz  |
| 2015 | Apple Twister (A9/A9X) | 6-wide (64-bit) | 6 decode | Stages<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline                                        | 2 cores                                                  | 1.85-<br>2.26 GHz     |
| 2014 | Apple Typhoon (A8/A8X) | 6-wide (64-bit) | 6 decode | Stages<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline                                        | 2-3 cores                                                | 1.4-1.5 GHz           |
| 2013 | Apple Cyclone (A7)     | 6-wide (64-bit) | 6 decode | Stages<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline<br>Pipeline                                        | 2 cores                                                  | 1.3-1.4 GHz           |

## 1. Overview of Apple's mobile processors (13)

### Width of mobile cores

![](7bed2d7c96d86bf922295a1252da52a5_img.jpg)

Width of mobile cores  
(or of big cores of big.LITTLE or dynamiQ core clusters)

|          | 2-wide                                                                          | 3-wide                                                                   | 4-wide                                   | 6-wide                                      |
|----------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------|------------------------------------------|---------------------------------------------|
| ARM      | v7 ISA based<br>(32-bit) Cortex-A cores<br>except the Cortex-A15<br>(2005-2009) | v7 ISA based<br>(32-bit) Cortex-A15<br>(2010)                            |                                          |                                             |
|          | v8 ISA-based<br>Cortex-A73 (2016)                                               | v8 ISA-based<br>(64-bit) Cortex-A line,<br>except the Cortex-A73 (2012-) |                                          |                                             |
| Intel    | Atom family<br>(2008-2016)                                                      |                                                                          |                                          |                                             |
| AMD      | Cat family<br>(2011-2015)                                                       |                                                                          |                                          |                                             |
| Apple    | Cortex-A8 (2009)                                                                | A6 (Swift (2012))                                                        |                                          | A7 (Cyclone (2013))<br>and subsequent cores |
| Qualcomm | Scorpion v7 ISA<br>(S1-S3) (2007-2010)                                          | Krait v7 ISA<br>(S4/S400/S60x/S80x)<br>(2012-2014)                       |                                          |                                             |
|          |                                                                                 | Kryo/Kryo 280 v8 ISA<br>(S820/S821/S835)<br>(2015/2016/2017)             |                                          |                                             |
|          |                                                                                 | Kryo 385 v8.2 ISA<br>(S845) (2018)                                       |                                          |                                             |
| Samsung  |                                                                                 | Exynos 5 v7 ISA<br>(2013-2014)                                           | M1 core v8 ISA (2016)<br>(Exynos 8 Octa) | M3 core v8.2 ISA<br>(2018)<br>(Exynos 9810) |
|          |                                                                                 | /Exynos 7 v8 ISA<br>(2016)                                               | M2 core v8 ISA (2017)<br>(Exynos 9 Octa) |                                             |

## 1. Overview of Apple's mobile processors (14)

### Remark

Certain early mobile processors are only 1-wide, like

- ARM's 1176 used in Apple's iPhone (2007) or
- ARM's Cortex-A5 (2009)

nevertheless, in the previous slide these processors are **not indicated for better visibility** of the entire Figure.

## 1. Overview of Apple's mobile processors (15)

For comparison: Width of Intel's and AMD's basic microarchitectures

![](2a77eb32ef4c4d8a5c1758a53a908336_img.jpg)

**Width of Intel's and AMD's basic microarchitectures**

|       | 2-wide         | 3-wide                                                                                                                                                     | 4-wide                                                                  | 5-wide                                 |
|-------|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|----------------------------------------|
| Intel | Pentium (1993) | Pentium II (Pentium Pro) 1996<br>Pentium III (1999)<br>Pentium 4 (2000)                                                                                    | Core 2 (2006) until<br>Broadwell (2014)                                 | Skylake (2015)<br>and subsequent lines |
| AMD   |                | K5 (1996)<br>K7 Athlon (1998)<br>K8 (Hammer)-based designs (2003)<br>K10 (Barcelona/Phenom) based lines (2007)<br>K10.5 (Shanghai etc.) based lines (2008) | K6 (1997)<br>K15 Bulldozer-based lines (2011)<br>Zen-based lines (2017) |                                        |

## 1. Overview of Apple's mobile processors (16)

For comparison: Width of IBMs POWER microarchitectures

![](9a19da4f7fccb96a934411c0bb5a386d_img.jpg)

Width of IBM's POWER microarchitectures

|     | 5-wide                                  | 6-wide                         | 8-wide        |
|-----|-----------------------------------------|--------------------------------|---------------|
| IBM | POWER4 (2001)<br>until<br>POWER6 (2007) | POWER7 (2010)<br>POWER9 (2018) | POWER8 (2010) |

## 1. Overview of Apple's mobile processors (17)

Increasing the clock frequency in Apple's mobiles [40]

![](9b5411fa2d169b66f6185fbf67b49766_img.jpg)

Graph showing the increasing clock frequency ( $f_c$  [Ghz]) of Apple's mobile processors (A4 to A11) over time (Year), alongside a dashed line indicating a theoretical  $\sim 6\times/10$  years scaling trend.

Y-axis:  $f_c$  [Ghz] (Up to 2.4)

X-axis: Year (2006 to 2018)

| Processor | Year | $f_c$ [Ghz] | Process Node |
|-----------|------|-------------|--------------|
| A4        | 2010 | 1.0         | 45 nm        |
| A5        | 2011 | 1.0         | 45 nm        |
| A6        | 2012 | 1.4         | 32 nm        |
| A7        | 2013 | 1.4         | 28 nm        |
| A8        | 2014 | 1.4         | 20 nm        |
| A9        | 2015 | 1.8         | 16 nm        |
| A10       | 2016 | 2.2         | 16 nm        |
| A11       | 2017 | 2.4         | 10 nm        |

Associated devices: iPhone 3GS (2009, 65 nm), iPhone 3G (2007, 90 nm).

## 1. Overview of Apple's mobile processors (18)

### New features and accelerators in Apple's processors [48]

![](485c57a6add7e0bd7898009db1179ee6_img.jpg)

**System on a Chip (SoC)**  
Combines all components on a single piece of silicon; designed by Samsung for iPhones before 2010.

**Secure Element**  
A secure vault that stores your payment and biometric data.

**Motion Co-Processor**  
A chip that measures your movements.

**Graphics Processor Unit (GPU)**  
The engine that powers graphics for gaming and other intensive tasks.

**Neural Engine**  
A processor for improving AI and machine learning apps.

**Apple HomePod**  
Includes a revamped storage chip for faster data processing.

**Apple TV**  
First dual-core Apple SoC. Introduces Apple-designed chip (the ISP) for improving photos.

**Apple TV (4th generation)**  
First Apple SoC.

**Apple TV**  
First chips optimized to support higher resolution iPad screen.

**Apple TV**  
Optimized for larger iPhone screens.

**Apple TV**  
Includes a revamped storage chip for faster data processing.

**Apple TV**  
First Apple chip with two high-performance and two energy-efficient components.

**Apple TV**  
First Apple chip with two high-performance and four energy-efficient components.

**Apple TV**  
Adds support for Face ID data for the iPhone X.

**Apple TV**  
First Apple custom designed graphics chip. Previously designed by Imagination Technologies.

**Apple TV**  
First Apple AI chip.

**Apple TV**  
First chip to store Touch ID and payment data.

**Apple TV**  
First motion-tracking iPhone chip to track steps.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV**  
First to measure elevation.

**Apple TV</**

## 1. Overview of Apple's mobile processors (19)

Die sizes of Apple's A5 to A9 mobile SoCs [40]

![](5500ab73cf84ccc0055eecf28889b4db_img.jpg)

Line chart titled "Apple SoC Die Size" showing the die size in  $\text{mm}^2$  for Apple's mobile System-on-Chip (SoC) processors from A5 to A9 (TSMC).

The Y-axis represents Die Size in  $\text{mm}^2$ , ranging from 0 to 140. The X-axis represents the SoC model (A5, A6, A7, A8, A9 (TSMC)).

| SoC Model | Die Size in $\text{mm}^2$ |
|-----------|---------------------------|
| A5        | 122                       |
| A6        | 97                        |
| A7        | 102                       |
| A8        | 89                        |
| A9 (TSMC) | 104.5                     |

## 1. Overview of Apple's mobile processors (20)

Die sizes of Apple's A5X to A10X tablet SoCs [49]

![](2a25e8bc21554c0efceda1a8ccf57db3_img.jpg)

Line chart titled "Apple Tablet SoC Die Size" showing the Die Size in  $\text{mm}^2$  versus the Apple processor model (A5X, A6X, A8X, A9X, A10X).

| Processor | Die Size in $\text{mm}^2$ | Process Node (nm) |
|-----------|---------------------------|-------------------|
| A5X       | 165                       | 45 nm             |
| A6X       | 123                       | 32 nm             |
| A8X       | 128                       | 20 nm             |
| A9X       | 147                       | 16 nm             |
| A10X      | 96                        | 10 nm             |

## 1. Overview of Apple's mobile processors (21)

### Overview of flash memory sizes in Apple's iPhones [3]

![](391ab9e5616ba6311161af4d7a93422b_img.jpg)

Horizontal bar chart illustrating the flash memory sizes available for various Apple iPhone models over time (2008 to 2015).

Legend:

- Original iPhone
- iPhone 3G
- iPhone 3GS
- iPhone 4
- iPhone 4S
- iPhone 5
- iPhone 5C
- iPhone 5S
- iPhone 6
- iPhone 6 Plus
- Still produced

Approximate Data:

| Model           | Year | Memory Sizes (GB) |
|-----------------|------|-------------------|
| Original iPhone | 2007 | 4GB               |
| iPhone 3G       | 2009 | 8GB, 16GB         |
| iPhone 3GS      | 2010 | 8GB, 16GB         |
| iPhone 4        | 2010 | 8GB, 16GB         |
| iPhone 4S       | 2011 | 8GB, 16GB         |
| iPhone 4        | 2011 | 8GB, 16GB         |
| iPhone 5        | 2012 | 16GB, 32GB        |
| iPhone 5C       | 2013 | 16GB, 32GB        |
| iPhone 5S       | 2013 | 16GB, 32GB, 64GB  |
| iPhone 5S       | 2014 | 16GB, 32GB, 64GB  |
| iPhone 6        | 2014 | 16GB, 64GB, 128GB |
| iPhone 6 Plus   | 2014 | 16GB, 64GB, 128GB |
| Still produced  | 2015 | 128GB             |

## 1. Overview of Apple's mobile processors (22)

### Overview of flash memory sizes in Apple's iPads [46]

![](abc0eb594f9d2c0daa0e60df05f2a666_img.jpg)

Horizontal bar chart illustrating the flash memory sizes available for various Apple iPad models over time (2011 to 2017).

| Model/Year | Memory Size | Color  | Approx. Year |
|------------|-------------|--------|--------------|
| iPad (1st) | 16GB        | Purple | 2010         |
| iPad 2     | 16GB        | Purple | 2011         |
| iPad 2     | 32GB        | Purple | 2011         |
| iPad 2     | 64GB        | Purple | 2011         |
| iPad 3     | 16GB        | Orange | 2012         |
| iPad 3     | 32GB        | Orange | 2012         |
| iPad 3     | 64GB        | Orange | 2012         |
| iPad 4th   | 16GB        | Orange | 2013         |
| iPad 4th   | 32GB        | Orange | 2013         |
| iPad 4th   | 64GB        | Orange | 2013         |
| iPad 4th   | 128GB       | Orange | 2013         |
| iPad Air   | 16GB        | Orange | 2013         |
| iPad Air   | 32GB        | Orange | 2013         |
| iPad Air   | 64GB        | Orange | 2013         |
| iPad Air   | 128GB       | Orange | 2013         |
| iPad Air 2 | 16GB        | Orange | 2014         |
| iPad Air 2 | 32GB        | Orange | 2014         |
| iPad Air 2 | 64GB        | Orange | 2014         |
| iPad Air 2 | 128GB       | Orange | 2014         |
| iPad Pro   | 32GB        | Gray   | 2015         |
| iPad Pro   | 128GB       | Gray   | 2015         |
| iPad Pro   | 256GB       | Gray   | 2016         |
| iPad Pro   | 128GB       | Gray   | 2017         |
| iPad Pro   | 256GB       | Gray   | 2017         |

## 1. Overview of Apple's mobile processors (23)

### Performance increase of Apple's iPhones (Up to the iPhone 6) [7]

![](20727e57890be6da5692a02d13c0a8ec_img.jpg)

UP TO  
**50x**  
FASTER

iPhone 3G, 3GS, 4, 4s, 5, 5s, iPhone 6

CPU PERFORMANCE

![](1b1bb497e39fcc025a3fc8bd4fc78d9a_img.jpg)

UP TO  
**84x**  
FASTER

iPhone 3G, 3GS, 4, 4s, 5, 5s, iPhone 6

GPU PERFORMANCE

iPhone 6 A8 SoC CPU and GPU performance graph (Apple's own figures)

## 1. Overview of Apple's mobile processors (24)

### Main components of a smartphone or tablet [9]

![](7119b28e39fa3784606bf8b8f44e4f9d_img.jpg)

Diagram illustrating the main components of a smartphone or tablet circuit board, labeled as follows:

- A 3G/4G **RF Transceiver**
- Front End Module ICs
- A high performance **ARM** based **Application Processor**
- A high Speed (LTE) **Baseband Processor (Modem)**
- A low cost **combo connectivity Chip (WiFi/Bluetooth/FM Radio)**

#### Note

**Processor memory** (usually implemented as stacked memory on the processor) and **flash memory** (usually implemented as an individual chip) **not indicated** in the Figure.

## 1. Overview of Apple's mobile processors (25)

### Apple's patent asset [10]

- A quick look at Apple's 13,000 patents broken down by issue date and type/origin – shows a healthy purchasing of legacy patents, and aggressive pursuit of design patents which they have used successfully in litigations
- Major recent increase in total # of patents issued yearly indicates Apple's strategic decision to pursue many patents regarding their product releases since 2003

![Map showing the distribution of granted Apple patents sorted by technology. Key areas labeled include MULTIMEDIA, SIRI, RADIO, GUI, TOUCH, MOBILE, SOFTWARE, DESIGN, HARDWARE, and CLOUD.](4dfe30ac5a87d018364a0ac42ea533fe_img.jpg)

Map showing the distribution of granted Apple patents sorted by technology. Key areas labeled include MULTIMEDIA, SIRI, RADIO, GUI, TOUCH, MOBILE, SOFTWARE, DESIGN, HARDWARE, and CLOUD.

Figure: Granted Apple patents sorted by technology [10]

## 1. Overview of Apple's mobile processors (26)

Evolution of cellular standards – until 2010 [8]

![](6f10f5cbc920e8c4340d869aae0f1f58_img.jpg)

Timeline of cellular standards evolution:

| 1G   | 2G              | 3G (Data)                  | Beyond 3G (Mobile broadband)          | Future          |
|------|-----------------|----------------------------|---------------------------------------|-----------------|
| AMPS | GSM, GPRS, Edge | WCDMA, HSDPA, HSUPA, HSPA+ | EVDO REV. 0, EVDO REV. A, EVDO REV. B | LTE, 4G (LTE-A) |
|      | CDMA            | RTT                        | TD-SCDMA                              |                 |

Years: 1983, 1993, 1995, 2005, 2010

## 2. Apple's original iPhone

## 2. Apple's original iPhone (1)

## 2. Apple's original iPhone

Designated also as the **iPhone 2G**.

Introduced in **1/2007** by Steve Jobs at the McWorld Expo.

![Steve Jobs holding the original iPhone (iPhone 2G) during the MacWorld Expo in 2007.](483c43eac5aa582dfcb6e0aa8cee163f_img.jpg)

Steve Jobs holding the original iPhone (iPhone 2G) during the MacWorld Expo in 2007.

Figure: Steve Jobs introducing the iPhone at MacWorld Expo in 1/2007 [11]

The iPhone became available in 6/2007 in the US and later elsewhere.

## 2. Apple's original iPhone (2)

### Main features of the original iPhone

| Appl. proc. | Model no.          | Image                                         | Node  | Die size             | CPU                      | CPU ISA | CPU cache                              | GPU                                           | Memory (up to)                                                             | Intro.           | Utilizing devices                                                                   |
|-------------|--------------------|-----------------------------------------------|-------|----------------------|--------------------------|---------|----------------------------------------|-----------------------------------------------|----------------------------------------------------------------------------|------------------|-------------------------------------------------------------------------------------|
|             | S5L8900X           | <img alt="Image of S5L8900X chip"/>           | 90 nm | 72 mm <sup>2</sup>   | 1x ARM1176 412 MHz       | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103 MHz                    | 128 MB<br>16-bit SCh<br>LPDDR-266<br>(532 MB/sec)                          | 6/2007<br>6/2007 | • iPhone (2G)<br>• iPod Touch (1st gen.)<br>• iPhone 3G                             |
|             | APL0278 or S5L8720 | <img alt="Image of APL0278 or S5L8720 chip"/> | 65 nm | 36 mm <sup>2</sup>   | 1x ARM1176 412–533 MHz   | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103–133 MHz                | 32/128 MB<br>32-bit SCh<br>LPDDR-133                                       | 9/2008           | • iPod Touch (2nd gen.)<br>• iPod Nano (4th gen.)                                   |
|             | APL0298 or S5L8920 | <img alt="Image of APL0298 or S5L8920 chip"/> | 65 nm | 71.8 mm <sup>2</sup> | 1x Cortex-A8 600 MHz     | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150 MHz (1.2 GFLOPS)         | 256 MB<br>32-bit SCh<br>LPDDR-400 (1.6 GB/sec)                             | 6/2009           | • iPhone 3GS                                                                        |
|             | APL2298 or S5L8922 | <img alt="Image of APL2298 or S5L8922 chip"/> | 45 nm | 41.6 mm <sup>2</sup> | 1x Cortex-A8 600–800 MHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150–200 MHz (1.2–1.6 GFLOPS) | 256 MB<br>32-bit SCh<br>LPDDR-400 (1.6 GB/sec)                             | 9/2009           | • iPod Touch (3rd gen.)                                                             |
| A4          | APL0398 or S5L8930 | <img alt="Image of A4 chip"/>                 | 45 nm | 53.3 mm <sup>2</sup> | 1x Cortex-A8 0.8–1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 512 KB | PowerVR SGX535 @ 200–250 MHz (1.6–2 GFLOPS)   | 256 MB (iPad)<br>512 MB (iPhone 4)<br>32-bit DCh<br>LPDDR-400 (3.2 GB/sec) | 3/2010           | • iPad (1st gen.)<br>• iPhone 4<br>• iPod Touch (4th gen.)<br>• Apple TV (2nd gen.) |

## 2. Apple's original iPhone (3)

### Implementation of the iPhone (termed also as the iPhone 2)

The original iPhone was based on a **PoP package** (Package on Package), designated as S5L8900B01, that included **3 dies**:

- the **SOC die** with the **ARM1176ZF-S 32-bit processor** (executing the ARMv6 ISA) and Imagination Technologies' **PowerVR MBX Lite 3D graphics accelerator**, and
- **two 512 Mb LPDDR-266 SDRAM dies** (providing 128 MB stacked memory), as illustrated below.

![](3fe839e8110987c60318d18e542f4a10_img.jpg)

Diagram illustrating the cross-section of the S5L8900B01 PoP package, showing the three dies stacked vertically:

- **Top Die:** 2x512 Mbit DDR SDRAM Stacked memory die.
- **Middle Die:** Single or multiple ASIC logic die (ARM1176ZF(F)-S + Power VR MBX Lite 3D).
- **Bottom Die:** Laminated substrate (essentially a mini PCB).

Connections shown:

- Gold or copper wirebonds connect the stacked memory die to the logic die.
- High density I/O BGA ball count (0.5mm pitch or less) connects the ASIC logic die to the motherboard.
- Lower density I/O BGA ball count (0.65mm pitch and more) connects the memory die to landing pads on the top of the bottom package. Memory die typically require less I/O than logic die.

Figure: iPhone's heart, the S5L8900B01 PoP, fabricated by Samsung (90 nm) [4]

## 2. Apple's original iPhone (4)

### Cross section of the iPhone [12]

![Cross section of the Apple original iPhone (4) showing the internal components.](9612f08d343bcc2a11b174db64ba7b3a_img.jpg)

This image is a cross-section view of the Apple original iPhone (4) showing the internal components. The layers, from top to bottom, are labeled:

- DRAM dies
- SOC die
- Solder balls
- Mini PCB

Cross section of the Apple original iPhone (4) showing the internal components.

DRAM dies

SOC die

Solder balls

Mini PCB

## 2. Apple's original iPhone (5)

### Remarks

- PoPs are fabricated as Multi-Chip Packages (MCPs).
- MCP became standardized by JEDEC about 2006 (JC-63).
- First PoPs emerged in cell phones around 2004 [13].
- First generation PoP technology typically integrates the baseband or application processor with one or two memory dies, as indicated in the next Figure.

![Diagram illustrating a Possible PoP (Package-on-Package) structure. It shows two stacked layers of circuitry (substrates) connected by vertical conductive paths (likely flex circuits or vias). The top layer contains a large rectangular die (likely the application processor or baseband processor). The bottom layer contains two smaller rectangular dies (memory dies). The structure is supported by multiple spherical connectors (ball grid array style) at the bottom.](0baabed74e5fce9eaf1cac18837415d8_img.jpg)

Diagram illustrating a Possible PoP (Package-on-Package) structure. It shows two stacked layers of circuitry (substrates) connected by vertical conductive paths (likely flex circuits or vias). The top layer contains a large rectangular die (likely the application processor or baseband processor). The bottom layer contains two smaller rectangular dies (memory dies). The structure is supported by multiple spherical connectors (ball grid array style) at the bottom.

Figure: Possible PoP structure for implementing a baseband or application processor and two memory dies [13]

- According to this, using PoP packaging for integrating the application processor and the memory in Apple's original iPhone was an early advanced packaging solution.

## 2. Apple's original iPhone (6)

### The ARM1176JZF-S CPU [14]

- The 32-bit CPU runs at a lower clock rate (412 MHz) than possible (667 MHz) to save power.
- It supports the ARMv6 ISA.
- It is a single issue processor.
- It has 16 kB instruction and 16 kB data caches, but no L2 cache.
- It has a Vector FP Processing Unit (VFP).

![](673e9e5873f9a4b71bbe7bac2cf6b758_img.jpg)

Diagram illustrating the ARM1176JZF-S CPU architecture. The central component is the ARMv6 TrustZone™ enabled ARM11™ core, which is connected to the Instruction Cache (TCRAM 0, TCRAM 1) and Data Cache (TCRAM 0, TCRAM 1). The core is also connected to the Debug Interface, Optional VFP, and Coprocessor Controller. Above the core, the ARMv6 TrustZone™ enabled ARM11™ core is shown. Below the core, the Memory Management unit is present. The bottom section shows the AMBA AXI Interface, which connects to the Instruction Interface, Data Interface, DMA, and Peripheral Port. The overall chip is labeled ARM1176JZF-S.

Figure: The ARM1176JZF-S CPU [14]

## 2. Apple's original iPhone (7)

### The PowerVR MBX Lite 3D graphics accelerator

| PowerVR branding | Architecture Generation | Example Application                     | Approximate date of introduction |
|------------------|-------------------------|-----------------------------------------|----------------------------------|
| PowerVR1         | Series1                 | Matrox m3D, Compaq Presario video cards | 1998                             |
| PowerVR2         | Series2                 | Sega Dreamcast, Neon250 PC video cards  | 1998                             |
| PowerVR3         | Series3                 | KYRO PC video cards                     | 2001                             |
| PowerVR4         | Series4                 | STM STG5000 chip for PC video cards     | Unreleased                       |
| PowerVR MBX      |                         | iPhone, iPhone 3G, iPod touch           | 2004                             |
| PowerVR SGX      | Series5                 | Palm Pre, iPhone 3GS                    | 2009                             |

Figure: Generations of PowerVR graphics IPs (from Imagination Technologies) [15]

## 2. Apple's original iPhone (8)

### The iPhone board (one side) [16]

![](1316cc5a3c69067473f110271212db3b_img.jpg)

**Philips**  
02992  
Touchscreen controller

**Wolfson**  
WM8758  
stereo audio codec

**Samsung**  
S5L8900B01  
ARM1176Z(F)-S +  
128 MB of stacked, POP DDR  
SDRAM

**Linear Technologies**  
4066  
Battery charger

## 2. Apple's original iPhone (9)

### The iPhone board (the other side) [16]

![](1c2028183a35357e7238438a4af9cab7_img.jpg)

Labels pointing to components on the iPhone board:

- **Samsung** K9MCG08U5M 64Gbit NAND Flash (8 GB)
- **Intel** PF38F1030W0YTQ2 Wireless Flash Memory
- **Infineon** M1817A11 RF transceiver
- **Infineon** PMB8876 5-Gold 2 Baseband modem
- **CSR** 41B14 BlueCore4ROM Bluetooth
- **Marvell** W8686 WLAN
- **Skyworks** SKY77340-13 GSM/EDGE quad-band amp
- **Apple branded** 33850297
- **EDGE MCP** MCP: Multi Chip Package

## 2. Apple's original iPhone (10)

Apple iPhone 3GS board [47]

![](db267ff9c1b97bbae0cb0856be1d8734_img.jpg)

Diagram of the Apple iPhone 3GS board showing various components:

- SIM slot
- App Processor/DDR SDRAM
- Accelerometer
- Power Amps
- Transceiver
- Power Amp
- NAND Flash
- GPS
- PMIC
- BB-PMIC
- BaseBand Processor
- SRAM

## 3. Apple A4

## 3. Apple A4 (1)

## 3. Apple A4

- Introduced in particular in the
  - iPad (2010) and
  - iPhone 4 (2010).
- The **A4** processor is [Apple's first in-house design](#) done in cooperation with Intrinsicity (a fabless semiconductor company, acquired by Apple in 2010).
- With Intrinsicity an experienced team of chip designers, specialized in high speed physical design joined Apple.
- Intrinsicity just finalized tuning Samsung's Hummingbird CPU for high speed and low power, in cooperation with Samsung.
- Apple's A4 is allegedly based on the Hummingbird core.

## 3. Apple A4 (2)

### Main features of the A4

| Appl. proc. | Model no.         | Image                                        | Node  | Die size             | CPU                      | CPU ISA | CPU cache                              | GPU                                           | Memory (up to)                                                             | Intro.           | Utilizing devices                                                           |
|-------------|-------------------|----------------------------------------------|-------|----------------------|--------------------------|---------|----------------------------------------|-----------------------------------------------|----------------------------------------------------------------------------|------------------|-----------------------------------------------------------------------------|
|             | S5L8900X          | <img alt="Image of S5L8900X chip"/>          | 90 nm | 72 mm <sup>2</sup>   | 1x ARM1176 412 MHz       | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103 MHz                    | 128 MB<br>16-bit SCh<br>LPDDR-266<br>(532 MB/sec)                          | 6/2007<br>6/2007 | iPhone (2G)<br>iPod Touch (1st gen.)<br>iPhone 3G                           |
|             | APO278 or S5L8720 | <img alt="Image of APO278 or S5L8720 chip"/> | 65 nm | 36 mm <sup>2</sup>   | 1x ARM1176 412-533 MHz   | ARMv6   | L1i: 16 KB<br>L1d: 16 KB               | PowerVR MBX Lite @ 103-133 MHz                | 32/128 MB<br>32-bit SCh<br>LPDDR-133                                       | 9/2008           | iPod Touch (2nd gen.)<br>iPod Nano (4th gen.)                               |
|             | APO298 or S5L8920 | <img alt="Image of APO298 or S5L8920 chip"/> | 65 nm | 71.8 mm <sup>2</sup> | 1x Cortex-A8 600 MHz     | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150 MHz (1.2 GFLOPS)         | 256 MB<br>32-bit SCh<br>LPDDR-400 (1.6 GB/sec)                             | 6/2009           | iPhone 3GS                                                                  |
| A4          | APO298 or S5L8922 | <img alt="Image of APO298 or S5L8922 chip"/> | 45 nm | 41.6 mm <sup>2</sup> | 1x Cortex-A8 600-800 MHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 256 KB | PowerVR SGX535 @ 150-200 MHz (1.2-1.6 GFLOPS) | 256 MB<br>32-bit SCh<br>LPDDR-400 (1.6 GB/sec)                             | 9/2009           | iPod Touch (3rd gen.)                                                       |
|             | APO398 or S5L8930 | <img alt="Image of APO398 or S5L8930 chip"/> | 45 nm | 53.3 mm <sup>2</sup> | 1x Cortex-A8 0.8-1.0 GHz | ARMv7   | L1i: 32 KB<br>L1d: 32 KB<br>L2: 512 KB | PowerVR SGX535 @ 200-250 MHz (1.6-2 GFLOPS)   | 256 MB (iPad)<br>512 MB (iPhone 4)<br>32-bit DCh<br>LPDDR-400 (3.2 GB/sec) | 3/2010           | iPad (1st gen.)<br>iPhone 4<br>iPod Touch (4th gen.)<br>Apple TV (2nd gen.) |

## 3. Apple A4 (3)

### Main features of the A4 PoP [17]

- The **A4 PoP** incorporates
  - the **A4 SOC** and
  - and **128 MB** later **512MB** **LPDDR 400 SDRAM stacked** memory (via 2x32-bit memory channels).
- The **A4 SOC** includes among others
  - a **single core ARM Cortex A8 CPU** supporting the ARMv7 ISA, it is a **dual-issue in order design**, clocked at 800 MHz and including 512 kB L2,
  - **dual core PowerVR SGX 535 GPU**, clocked at 200 MHz,
- The internal designation of the A4 PoP is S5L8930X.
- The Pop was fabricated by Samsung on a **45 nm** process.
- The die size is 53 mm<sup>2</sup>.

![Die plot of the Apple A4 PoP. The image shows the layout of the integrated circuit. A large rectangular area, highlighted by a red box and labeled 'ARM Core', represents the central processing unit. The surrounding area contains other components and memory blocks. The image includes a scale bar indicating 1000 µm.](f8d416442307a485296b835751a3f5a2_img.jpg)

Die plot of the Apple A4 PoP. The image shows the layout of the integrated circuit. A large rectangular area, highlighted by a red box and labeled 'ARM Core', represents the central processing unit. The surrounding area contains other components and memory blocks. The image includes a scale bar indicating 1000 µm.

Figure: Die plot of the A4 [17]

## 3. Apple A4 (4)

Key features of the microarchitecture of ARM's 32-bit Cortex-A8 core [2]

![](9857175bc98d86591d24a161fe615f12_img.jpg)

| ARM Cortex-A Family Architecture                   |                                                                                                    | 32-bit                                     |  |
|----------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------|--|
| 2010                                               | Cortex-A15<br>3 decode<br>Out-of-Order Scheduler<br>15+ Stages<br>Pipeline<br>Pipeline<br>Pipeline | -2.5GHz@28nm<br>3.5 DMIPS/MHz<br>1-32 Core |  |
| 2007                                               | Cortex-A9<br>2 decode<br>Out-of-Order Scheduler<br>9-12 Stages<br>Pipeline<br>Pipeline             | -2GHz@40nm<br>2.5 DMIPS/MHz<br>1-4 Core    |  |
| 2005                                               | Cortex-A8<br>2 decode<br>In-Order<br>13 Stages<br>Pipeline<br>Pipeline                             | -1GHz@65nm<br>2 DMIPS/MHz<br>1 Core        |  |
| 2009<br>(A9 replacement<br>for low-end<br>devices) | Cortex-A5<br>1 decode<br>In-Order<br>9 Stages<br>Pipeline                                          | -1GHz<br>1.6 DMIPS/MHz<br>1-4 Core         |  |

## 3. Apple A4 (5)

The iPad board-1 [12]

![A photograph of the main logic board (motherboard) of an early iPad, showing the Apple A4 processor chip prominently in the center. The board features several Samsung KFCC101-LC80 chips and various connectors and components.](c436e079f79bca972b79ed4b3e4613ea_img.jpg)

A photograph of the main logic board (motherboard) of an early iPad, showing the Apple A4 processor chip prominently in the center. The board features several Samsung KFCC101-LC80 chips and various connectors and components.

## 3. Apple A4 (6)

### The iPad board-2 [18]

![](7e2465b81aed11b2e58575a811424b75_img.jpg)

BROADCOM  
BCM5973  
Touch Screen  
Controller

SAMSUNG  
K9PFG08U5M  
MLC NAND Flash  
Memory-32 GB

APPLE  
A4/APL03898  
ARM Applications  
Processor w/SRAM

CIRRUS  
338S0589 / CLI1495B0  
Audio Codec

STMICRO  
M24128A  
Serial EEPROM - 16KB

SAMSUNG  
S6T2MLCX01  
Display Driver/Controller

STMICRO  
LIS331DLH  
3-Axis  
Accelerometer

ATMEL  
AT25DF08  
Serial Flash  
Memory - 1MB

LINEAR TECHNOLOGY  
LTC3442  
Buck-Boost  
DC/DC Converter

TI  
CD3040A1  
Touch Screen  
Line Drive

BROADCOM  
BCM5974  
Touch Screen  
Controller

NXP  
CBTL06141  
Display Port  
Multiplexer

TI  
TS3USB221  
USB Mux/De-mux

O2 MICRO  
APP\_1A/GOSHAWK6P-AO  
White LED Driver

TI  
TCA6408A  
I/O Expander

DIALOG  
SEMICONDUCTOR  
338S0805/D1815A  
Power Management Unit

LINEAR TECHNOLOGY  
LTC4099  
USB Battery Charge  
Management

## 4. Apple A6 with dual Swift cores

## 4. Apple A6 with dual Swift cores (1)

## 4. Apple A6 with dual Swift cores

### Introduction of the A6

- It debuted in the iPhone5 (2012).
- The **A6** is **Apple's first own in-house design**, it implements the **ARMv7S ISA**.  
  The S tag indicates an ISA extension implemented for the A6 (Swift) processor.

## 4. Apple A6 with dual Swift cores (2)

### Main features of the A6

| Appl. proc. | Model no.          | Image     | Node          | Die size              | CPU ISA | CPU                         | CPU cache                            | GPU                                                            | Memory (up to)                                      | Intro.  | Utilizing devices                                                  |
|-------------|--------------------|-----------|---------------|-----------------------|---------|-----------------------------|--------------------------------------|----------------------------------------------------------------|-----------------------------------------------------|---------|--------------------------------------------------------------------|
| A5          | APL0498 or S5L8940 | Apple A5  | 45 nm         | 122.2 mm <sup>2</sup> | ARMv7   | 0.8–1.0 GHz<br>2C Cortex-A9 | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2011  | • iPad 2<br>• iPhone 4S                                            |
|             | APL2498 or S5L8942 | Apple A5  | 32 nm<br>HKMG | 69.6 mm <sup>2</sup>  | ARMv7   | 0.8–1.0 GHz<br>2C Cortex-A9 | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2012  | • iPad 2<br>(iPad2,4)<br>• iPod Touch<br>(5th gen.)<br>• iPad Mini |
|             | APL7498 or S5L8947 | Apple A5  | 32 nm<br>HKMG | 37.8 mm <sup>2</sup>  | ARMv7   | SC Cortex-A9                | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP2 (2C)<br>@ 200–250 MHz<br>(12.8–16 GFLOPS) | 512 MB<br>32-bit DCh<br>LPDDR2-800<br>(6.4 GB/sec)  | 3/2013  | • AppleTV 3<br>(AppleTV3,2)                                        |
| A5X         | APL5498 or S5L8945 | Apple A5X | 45 nm         | 165 mm <sup>2</sup>   | ARMv7   | 1.0 GHz 2C<br>Cortex-A9     | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP4 (4C)<br>@ 250 MHz<br>(32 GFLOPS)          | 1 GB<br>32-bit 4Ch<br>LPDDR2-800<br>(12.8 GB/sec)   | 3/2012  | • iPad<br>(3rd gen.)                                               |
| A6          | APL0598 or S5L8950 | Apple A6  | 32 nm<br>HKMG | 96.71 mm <sup>2</sup> | ARMv7s  | 1.3 GHz 2C<br>Swift         | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX543MP3 (3C)<br>@ 266 MHz<br>(25.5 GFLOPS)        | 1 GB<br>32-bit DCh<br>LPDDR2-1066<br>(8.528 GB/sec) | 9/2012  | • iPhone 5<br>• iPhone 5C                                          |
| A6X         | APL5598 or S5L8955 | Apple A6X | 32 nm<br>HKMG | 123 m <sup>2</sup>    | ARMv7s  | 1.4 GHz 2C<br>Swift         | L1i: 32 KB<br>L1d: 32 KB<br>L2: 1 MB | PowerVR<br>SGX554MP4 (4C)<br>@ 266 MHz<br>(68.1 GFLOPS)        | 1 GB<br>32-bit 4Ch<br>LPDDR2-1066<br>(17.1 GB/sec)  | 10/2012 | • iPad<br>(4th gen.)                                               |

## 4. Apple A6 with dual Swift cores (3)

### Remarks to the development of the A6 [19]

- In 4/2008 Apple acquired PA Semi, a CPU design firm that had experience in developing high performance PowerPC processors.

Previously, some of the team even took part also in the design of the low-power StrongArm processor, at Digital Equipment Corporation.

- About this time Apple also signed a licensing agreement with ARM to be able to implement ARM compatible processors.
- One group of the PA Semi employees set to work on the Apple A4, based on the ARM Cortex A8 core whereas the other group began to define the microarchitecture of the **A6 core**, designated as **Swift**.
- In early 2010 the team completed the logical design of the microarchitecture of the A6 core and started with the physical design phase.

## 4. Apple A6 with dual Swift cores (4)

### Main features of the A6 (Swift) PoP [17]

- The **A6 PoP** incorporates
  - the **A6 SOC** and
  - **1GB LPDDR2-1066 SDRAM**  
    (via 2x32-bit memory channels).
- the **A6 SOC** includes among others
  - **dual Swift CPU cores**  
    supporting the ARMv7s ISA  
    (enhanced ARMv7 for Swift),  
    it is a **3-wide out-of-order design**,  
    clocked at **1.3 GHz** and  
    including **1 1MB L2**,
  - **three core PowerVR SGX 545 GPU**,  
    clocked at **333 MHz**.
- The internal designation of the A6 PoP is S5L8930X.
- The PoP was fabricated by Samsung on a **32 nm** process.
- The die size is **97 mm<sup>2</sup>**.

![Die shot of the Apple A6 System-on-Chip (SOC). The image highlights the ARM Cores (dual Swift CPU cores) and the three GPU Cores (PowerVR SGX 545). Other components like PELs (Power Efficient Logic) and the Interface are also visible.](9e3dccfc3a1dfa5759408d1269137ed0_img.jpg)

Die shot of the Apple A6 System-on-Chip (SOC). The image highlights the ARM Cores (dual Swift CPU cores) and the three GPU Cores (PowerVR SGX 545). Other components like PELs (Power Efficient Logic) and the Interface are also visible.

Figure: The A6 SOC [17]

## 4. Apple A6 with dual Swift cores (5)

Main features of the A6 SOC compared with previous Apple processors [20]

|                       | Apple A4                  | Apple A5                  | Apple A5r2                | Apple A5X          | Apple A6              |
|-----------------------|---------------------------|---------------------------|---------------------------|--------------------|-----------------------|
| Intro Date            | 2010                      | 2011                      | 2012                      | 2012               | 2012                  |
| Intro Product         | iPad                      | iPad 2                    | iPad 2                    | iPad 3             | iPhone 5              |
| Product Targets       | iPad/iPhone 4             | iPad 2/iPhone 4S          | iPad 2/iPhone 4S          | iPad 3             | ?                     |
| CPU                   | ARM Cortex A8             | 2 x ARM Cortex A9         | 2 x ARM Cortex A9         | 2 x ARM Cortex A9  | 2 x Apple Swift       |
| CPU Frequency         | 1GHz/800MHz (iPad/iPhone) | 1GHz/800MHz (iPad/iPhone) | 1GHz/800MHz (iPad/iPhone) | 1GHz               | 1.3GHz                |
| GPU                   | PowerVR SGX 535           | PowerVR SGX 543MP2        | PowerVR SGX 543MP2        | PowerVR SGX 543MP4 | PowerVR SGX 543MP3    |
| Memory Interface      | 32-bit LPDDR2             | 2 x 32-bit LPDDR2         | 2 x 32-bit LPDDR2         | 4 x 32-bit LPDDR2  | 2 x 32-bit LPDDR2     |
| Manufacturing Process | Samsung 45nm LP           | Samsung 45nm LP           | Samsung 32nm LP HK+MG     | Samsung 45nm LP    | Samsung 32nm LP HK+MG |

## 4. Apple A6 with dual Swift cores (6)

### Microarchitecture of the Swift core

- The A6 is Apple's (first and single) **3-issue out-of-order superscalar** with a **dispatch rate of 4**, as indicated in the next Figure.

## 4. Apple A6 with dual Swift cores (7)

### Width of mobile cores

#### Width of mobile cores (or of big cores of big.LITTLE or dynamiQ core clusters)

![](3881b390d52f27a35faedfc170916c86_img.jpg)

|          | 2-wide                                                                          | 3-wide                                                                   | 4-wide                                   | 6-wide                                      |
|----------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------|------------------------------------------|---------------------------------------------|
| ARM      | v7 ISA based<br>(32-bit) Cortex-A cores<br>except the Cortex-A15<br>(2005-2009) | v7 ISA based<br>(32-bit) Cortex-A15<br>(2010)                            |                                          |                                             |
|          | v8 ISA-based<br>Cortex-A73 (2016)                                               | v8 ISA-based<br>(64-bit) Cortex-A line,<br>except the Cortex-A73 (2012-) |                                          |                                             |
| Intel    | Atom family<br>(2008-2016)                                                      |                                                                          |                                          |                                             |
| AMD      | Cat family<br>(2011-2015)                                                       |                                                                          |                                          |                                             |
| Apple    | Cortex-A8 (2009)                                                                | A6 (Swift (2012))                                                        |                                          | A7 (Cyclone (2013))<br>and subsequent cores |
| Qualcomm | Scorpion v7 ISA<br>(S1-S3) (2007-2010)                                          | Krait v7 ISA<br>(S4/S400/S60x/S80x)<br>(2012-2014)                       |                                          |                                             |
|          |                                                                                 | Kryo/Kryo 280 v8 ISA<br>(S820/821/835)<br>(2015/2016/2017)               |                                          |                                             |
|          |                                                                                 | Kryo 385 v8.2 ISA<br>(S845) (2018)                                       |                                          |                                             |
| Samsung  |                                                                                 | Exynos 5 v7 ISA<br>(2013-2014)                                           | M1 core v8 ISA (2016)<br>(Exynos 8 Octa) | M3 core v8.2 ISA<br>(2018)<br>(Exynos 9810) |
|          |                                                                                 | /Exynos 7 v8 ISA<br>(2016)                                               | M2 core v8 ISA (2017)<br>(Exynos 9 Octa) |                                             |

## 4. Apple A6 with dual Swift cores (8)

Assumed block diagram of the Swift core [21]

![](4c547ec1af44f8fcdc8b1d67662ac30a_img.jpg)

Block diagram illustrating the assumed architecture of the Swift core (A6 dual-core). The core features a 16 KB L1-Data cache, an Instr. Queue, and a 4-stage Decode pipeline feeding into a Renaming / Scheduling unit. The execution units include Load, Store, Integer-ALU (x2), FP MAC (x2), and Neon, all connected to register files (Integer-Register file and FP and Neon-Register file). The core communicates with the AXI-Bus-IF and includes a Data-TLB.

Key components and data paths:

- **Branch prediction** feeds into **Instr. fetch**.
- **Instr. fetch** feeds into **Instr. complete** (4 Instr. path) and **Instr. Queue** (4 Instr. path).
- **Instr. Queue** feeds into **Decode** (3 Instr. path).
- **Decode** feeds into **Renaming / Scheduling**.
- **Renaming / Scheduling** feeds into the execution units (Load, Store, Integer-ALU, FP MAC, Neon).
- **Load** and **Store** units interact with the **Integer-Register file** (32-bit data paths).
- **Integer-ALU** units interact with the **Integer-Register file** (32-bit data paths).
- **FP MAC** and **Neon** units interact with the **FP and Neon-Register file** (128-bit data paths).
- The **Integer-Register file** feeds into **Data-TLB** (32-bit data path).
- The **FP and Neon-Register file** feeds into **Data-TLB** (128-bit data path).
- **Data-TLB** feeds into the **16 KB L1-Data cache**.
- The **16 KB L1-Data cache** feeds into the **AXI-Bus-IF**.

## 5. Apple A7 with dual Cyclone cores

## 5. Apple A7 with dual Cyclone cores (1)

## 5. Apple A7 with dual Cyclone cores

- The **A7** emerged in the mobile devices
  - iPhone 5S
  - iPad Mini 2
  - iPad Mini 3 and
  - iPad Airin 2013.
- It is **Apple's second own in-house design**, it implements the **ARMv8-A ISA**, that is the **64-bit ARMv8 ISA with custom Apple extensions**.

## 5. Apple A7 with dual Cyclone cores (2)

### Main features of the A7 -1

| Appl. proc. | Model no.                           | Image                             | Node                            | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.                                 | Utilizing devices                        |
|-------------|-------------------------------------|-----------------------------------|---------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|----------------------------------------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                      | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013                                 | iPhone 5S<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                      | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013                                | iPad Air 9.7"                            |
| A8          | APL1011                             | <img alt="Apple A8 chip image"/>  | 20 nm HKMG                      | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014                                 | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | <img alt="Apple A8X chip image"/> | 20 nm HKMG                      | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>L3: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR4-1600 (25.6 GB/sec)      | 10/2014                                | iPad Air 2 9.7"                          |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | <img alt="Apple A9 chip image"/>  | 16 nm FinFET<br>14 nm<br>FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015                                 | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | <img alt="Apple A9X chip image"/> | 16 nm FinFET                    | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015<br>(12.9")<br>3/2016<br>(9.7") | iPad Pro 9.7"<br>iPad Pro 12.9"          |

## 5. Apple A7 with dual Cyclone cores (3)

### Main features of the A7 -2 [10]

- It has **dual CPU cores**, called **Cyclone cores**.
- The out-of-order cores are **6-wide**.
- The clock rate is 1.3 GHz.
- The cores have a shared 1 MB L2 and a shared 4 MB L3 (first in the A line).
- The GPU is a PowerVR 6430 with four cores, clocked at 1.3 GHz.
- The **A7 PoP** includes also a 1 GB **stacked SDRAM** (LPDDR3-1600 SDRAM (attached via 2x32-bit memory channels)).

![Diagram of the Apple A7 System-on-Chip (SOC) layout. The chip features two CPU cores (Cyclone cores) connected to a shared L2 cache (1MB) and a shared L3 cache (4MB). The CPU cores are connected to DRAM interfaces and PLLs. The GPU core (PowerVR 6430) is shown with four cores and GPU shared digital logic. Other interfaces include USB, LCD interface, Camera interface, and DRAM interface. The chip is labeled 'chipworks'.](7b96fce298a23fd76a01ff6c176c1059_img.jpg)

Diagram of the Apple A7 System-on-Chip (SOC) layout. The chip features two CPU cores (Cyclone cores) connected to a shared L2 cache (1MB) and a shared L3 cache (4MB). The CPU cores are connected to DRAM interfaces and PLLs. The GPU core (PowerVR 6430) is shown with four cores and GPU shared digital logic. Other interfaces include USB, LCD interface, Camera interface, and DRAM interface. The chip is labeled 'chipworks'.

Figure: The A7 SOC [10]

## 5. Apple A7 with dual Cyclone cores (4)

### Main features of the A7 -3 [10]

- The internal designation of the A7 PoP is S5L8960X.
- The PoP was fabricated by Samsung on a **28 nm** process.
- The die size is  $102 \text{ mm}^2$ .
- The **transistor count** is  $\sim 1 \text{ billion}$ .

![Diagram of the Apple A7 System-on-Chip (SOC) layout. The chip features a CPU core with L1 and L2 caches (1MB), connected to the DRAM interface. The CPU is surrounded by four GPU cores. The GPU cores are connected to GPU shared digital logic. The chip also includes PLLs, DRAM interfaces, USB, LCD interface, and Camera interface. The chip is labeled 'chipworks'.](c742b64169a38a7f3f990172019878c8_img.jpg)

Diagram of the Apple A7 System-on-Chip (SOC) layout. The chip features a CPU core with L1 and L2 caches (1MB), connected to the DRAM interface. The CPU is surrounded by four GPU cores. The GPU cores are connected to GPU shared digital logic. The chip also includes PLLs, DRAM interfaces, USB, LCD interface, and Camera interface. The chip is labeled 'chipworks'.

Figure: The A7 SOC [10]

## 5. Apple A7 with dual Cyclone cores (5)

Using a motion coprocessor (designated as M7) to reduce the load on the A7 [22], [23]

- The iPhone 5S, iPad mini 2, 3 or the iPad Air A7 also include a **motion coprocessor**, designated as **M7**.
- It is actually an **ARM Cortex-M3** microcontroller running at 180 MHz.
- The chip **collects information from sensors**, such as the accelerometer, gyroscope or magnetometer, **processes these data and forwards workable data to the A7**. Health and fitness **apps can then make use of these data** e.g. for distinguishing the type or speed of the motion currently taking place etc..
- The low power M7 **reduces the load on the A7** chip and greatly improves in this way battery life.
- Subsequent implementations of Apple's mobile devices continue to make use of motion coprocessors (designated as the M8 for the A8 and A8X SOCs).

## 5. Apple A7 with dual Cyclone cores (6)

### Microarchitecture of the Cyclone core-1

- Apple does not reveal any details of their processor microarchitectures.
- Nevertheless, in order to support LLVM compiler optimization [Apple revealed the machine model of the Cyclone core](#) as follows.

## 5. Apple A7 with dual Cyclone cores (7)

Part of the machine model of the Cyclone core as revealed by Apple [24]

```
//====================================================================
//
// This file defines the machine model for ARM64 Cyclone to support
// instruction scheduling and other instruction cost heuristics.
//
//====================================================================

def CycloneModel : SchedMachineModel {
  let IssueWidth = 6; // 6 micro-ops are dispatched per cycle.
  let MicroOpBufferSize = 192; // Based on the reorder buffer.
  let LoadLatency = 4; // Optimistic load latency.
  let MispredictPenalty = 16; // 14-19 cycles are typical.
}

//====================================================================
// Define each kind of processor resource and number available on Cyclone.

// 4 integer pipes
def CyUnitI : ProcResource<4> {
  let BufferSize = 48;
}

// 2 branch units: I[0..1]
def CyUnitB : ProcResource<2> {
  let Super = CyUnitI;
  let BufferSize = 24;
}

```

## 5. Apple A7 with dual Cyclone cores (8)

### Microarchitecture of the Cyclone core-2

Based on the above compiler specifications, Cyclone's microarchitecture was guessed in two publications, as shown next.

## 5. Apple A7 with dual Cyclone cores (9)

Assumed block diagram of the Cyclone core, based on [25]

![](57e7a913a27e03b719a102d02c6bf985_img.jpg)

Block diagram illustrating the assumed structure of the Cyclone core, based on [25]. The diagram shows six Decoders feeding into a central 192-entry Reorder Buffer. The Reorder Buffer distributes instructions to three execution units:

- 48 entries unit, which includes four Integer ALUs, two Branch units, one Shift unit, and one Indirect Branch unit.
- 28 entries unit, which includes two Load/Store units and one FP/NEON ALU/MUL unit.
- 48 entries unit, which includes two FP/NEON ALU/MUL units, one FP Compare unit, and two CyUnitFlo atDiv units.

Additional functional units shown below the main execution units include an Integer DIV unit and an Integer MUL unit.

## 5. Apple A7 with dual Cyclone cores (10)

Assumed block diagram of the Cyclone core, based on [26]

![](14294c70b5a0effb6bdaf09c46bbdc9f_img.jpg)

Block diagram of the Cyclone core, based on [26].

The core fetches instructions from the **64 KB L1 I Cache** (128 bit width). The fetch path includes **Instr. Prefetch** and **L1 Instr. TLB**. The fetched instructions are stored in the **Prefetch-Buffer** (128 bit width).

The **Prefetch-Buffer** feeds into the **Microcode** unit, which performs **Decode** operations (5 stages shown). The output of the decoder feeds into the **Instr. Buffer**.

The **Instr. Buffer** output feeds into the **Branch prediction** unit and the **Reorder-Buffer** (192 entries).

The **Reorder-Buffer** output feeds into the **Integer Rename / Schedule** (48 entries), **Load-Queue / Schedule** (28 entries), and **FP Rename / Schedule** (48 entries).

The **Integer Rename / Schedule** unit feeds into the **Integer-Register File**. The **Integer-Register File** outputs to **FX ALU / Shift** (64 bit width), **FX ALU / Branch / FX Div / Shift** (64 bit width), **FX ALU / Indir. Branch** (64 bit width), and **FX ALU / FX Mul / Indir. Branch** (64 bit width).

The **Load-Queue / Schedule** unit feeds into the **64-bit AGU** (64 bit width) and the **Reissuance Queue** (64 bit width).

The **FP Rename / Schedule** unit feeds into **FP / NEON ALU / Mul.** (128 bit width), **FP / NEON ALU / Div.** (128 bit width), and **FP / NEON ALU / Mul. / FP Comp.** (128 bit width).

The **64-bit AGU** and **Reissuance Queue** output to the **FP-and NEON-Register File** (128 bit width).

The **FP-and NEON-Register File** outputs to **L2 Data TLB** (128 bit width) and **L1 Data TLB** (128 bit width).

The **L1 Data TLB** feeds into the **64 KB L1 D Cache** (128 bit width).

The **64 KB L1 D Cache** feeds into the **1 MB shared L2 Cache**.

All caches and the **AXI-Bus-IF** are connected to the **1 MB shared L2 Cache**.

## 5. Apple A7 with dual Cyclone cores (11)

### Microarchitecture of the Cyclone core-3

- As seen, the Cyclone core is an extremely wide - **6-wide** - **out-of-order superscalar** with an **issue rate of 9**.
- In contrast, **even Intel's and AMD's recent performance/Watt oriented processors** such as Haswell, Broadwell, Bulldozer or Piledriver are **only 4-wide designs**, as indicated in the next Figures.

## 5. Apple A7 with dual Cyclone cores (12)

### Width of mobile cores

![](6b26e27af9601d90852f430c44907bad_img.jpg)

Width of mobile cores  
(or of big cores of big.LITTLE or dynamiQ core clusters)

|          | 2-wide                                                                          | 3-wide                                                                                                                                                 | 4-wide                                                                               | 6-wide                                             |
|----------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------|
| ARM      | v7 ISA based<br>(32-bit) Cortex-A cores<br>except the Cortex-A15<br>(2005-2009) | v7 ISA based<br>(32-bit) Cortex-A15<br>(2010)                                                                                                          |                                                                                      |                                                    |
|          | v8 ISA-based<br>Cortex-A73 (2016)                                               | v8 ISA-based<br>(64-bit) Cortex-A line,<br>except the Cortex-A73 (2012-)                                                                               |                                                                                      |                                                    |
| Intel    | Atom family<br>(2008-2016)                                                      |                                                                                                                                                        |                                                                                      |                                                    |
| AMD      | Cat family<br>(2011-2015)                                                       |                                                                                                                                                        |                                                                                      |                                                    |
| Apple    | A5 (2011)                                                                       | A6 (Swift (2012))                                                                                                                                      |                                                                                      | A7 (Cyclone (2013)<br>and all subsequent<br>cores) |
| Qualcomm | Scorpion v7 ISA<br>(S1-S3) (2007-2010)                                          | Krait v7 ISA<br>(S4/S400/S60x/S80x)<br>(2012-2014)<br>Kryo/Kryo 280 v8 ISA<br>(S820/821/835)<br>(2015/2016/2017)<br>Kryo 385 v8.2 ISA<br>(S845) (2018) |                                                                                      |                                                    |
| Samsung  |                                                                                 | Exynos 5 v7 ISA<br>(2013-2014)<br>/Exynos 7 v8 ISA<br>(2016)                                                                                           | M1 core v8 ISA (2016)<br>(Exynos 8 Octa)<br>M2 core v8 ISA (2017)<br>(Exynos 9 Octa) | M3 core v8.2 ISA<br>(2018)<br>(Exynos 9810)        |

## 5. Apple A7 with dual Cyclone cores (13)

### Width of Intel's and AMD's basic microarchitectures

![](a4cabfec798f5330bf8cc750d4d518ee_img.jpg)

**Width of Intel's and AMD's basic microarchitectures**

|       | 2-wide         | 3-wide                                                                                                                                                     | 4-wide                                                                  | 5-wide                                 |
|-------|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|----------------------------------------|
| Intel | Pentium (1993) | Pentium II (Pentium Pro) 1996<br>Pentium III (1999)<br>Pentium 4 (2000)                                                                                    | Core 2 (2006) until<br>Broadwell (2014)                                 | Skylake (2015)<br>and subsequent lines |
| AMD   |                | K5 (1996)<br>K7 Athlon (1998)<br>K8 (Hammer)-based designs (2003)<br>K10 (Barcelona/Phenom) based lines (2007)<br>K10.5 (Shanghai etc.) based lines (2008) | K6 (1997)<br>K15 Bulldozer-based lines (2011)<br>Zen-based lines (2017) |                                        |

## 5. Apple A7 with dual Cyclone cores (14)

### Width of IBMs POWER microarchitectures

![](4af0349328e735d480210fe9a3e595cb_img.jpg)

Width of IBM's POWER microarchitectures

|     | 5-wide                                  | 6-wide                         | 8-wide        |
|-----|-----------------------------------------|--------------------------------|---------------|
| IBM | POWER4 (2001)<br>until<br>POWER6 (2007) | POWER7 (2010)<br>POWER9 (2018) | POWER8 (2010) |

## 5. Apple A7 with dual Cyclone cores (15)

### Contrasting key features of the A6 and A7 microarchitectures [25]

|                           | Apple A6            | Apple A7            |
|---------------------------|---------------------|---------------------|
| CPU Codename              | Swift               | Cyclone             |
| ARM ISA                   | ARMv7-A (32-bit)    | ARMv8-A (32/64-bit) |
| Issue Width               | 3 micro-ops         | 6 micro-ops         |
| Reorder Buffer Size       | 45 micro-ops        | 192 micro-ops       |
| Branch Mispredict Penalty | 14 cycles           | 16 cycles (14 - 19) |
| Integer ALUs              | 2                   | 4                   |
| Load/Store Units          | 1                   | 2                   |
| Load Latency              | 3 cycles            | 4 cycles            |
| Branch Units              | 1                   | 2                   |
| Indirect Branch Units     | 0                   | 1                   |
| FP/NEON ALUs              | ?                   | 3                   |
| L1 Cache                  | 32KB I\$ + 32KB D\$ | 64KB I\$ + 64KB D\$ |
| L2 Cache                  | 1MB                 | 1MB                 |
| L3 Cache                  | -                   | 4MB                 |

## 5. Apple A7 with dual Cyclone cores (16)

### Performance comparison of Apple processors [27]

|            |     |    | Geekbench 3 Scores |              |
|------------|-----|----|--------------------|--------------|
|            |     |    | Single-Thread      | Multi-Thread |
| iPad Air 2 | A8X | 3C | 1798               | 4468         |
| iPhone 6   | A8  | 2C | 1610               | 2881         |
| iPad Air   | A7  | 2C | 1472               | 2663         |
| iPad 4     | A6X | 2C | 770                | 1401         |

The benchmark scores for Geekbench 3 show that the 6-wide A7 has approximately twice the performance of the 3-wide A6X.

## 5. Apple A7 with dual Cyclone cores (17)

Example: Apple's iPhone 5s xxx and its constituents [10]

Apple iPhone 5s

![Image of the back of an Apple iPhone 5s, showing the camera and speaker grille.](6a634b478b14451f92bc705f0941bee3_img.jpg)

Image of the back of an Apple iPhone 5s, showing the camera and speaker grille.

![Image of the back of an Apple iPhone 5s, showing the Apple logo and the word 'iPhone'.](9525ab7edaab8eb7b55357f3e9d5a733_img.jpg)

Image of the back of an Apple iPhone 5s, showing the Apple logo and the word 'iPhone'.

![Disassembled components of an Apple iPhone 5s, including the screen, battery, and internal circuit boards.](b8b30b7a99aa84e981f8b6ab7de49e15_img.jpg)

Disassembled components of an Apple iPhone 5s, including the screen, battery, and internal circuit boards.

![Disassembled components of an Apple iPhone 5s, including the screen, battery, and internal circuit boards.](5d08409a2364adb2331af3333fcedbbe_img.jpg)

Disassembled components of an Apple iPhone 5s, including the screen, battery, and internal circuit boards.

## 5. Apple A7 with dual Cyclone cores (18)

### Assumed block diagram of the Apple iPhone 5s [10]

![](4aa5a040cd7f031e935bff34790ea96f_img.jpg)

Assumed block diagram of the Apple iPhone 5s [10].

The diagram illustrates the connectivity of various components, including the main processor (APP A7), memory (Flash Memory and DRAM), connectivity modules (LTE, WCDMA, GSM), sensors, and external interfaces.

**Key Components and Connections:**

- **Antenna SW (RF1112 (Murata))** connects to Power Amps (TQF6414 (TriQuint), TQF6414 (TriQuint), SKY77493 (Skyworks)) and LTE/WCDMA/GSM modems (WTR1605L (Qualcomm)).
- **Power Amps** connect to the Antenna SW and the LTE/WCDMA/GSM modems.
- **Modems (WTR1605L (Qualcomm))** connect to ABB (MDM9615M (Qualcomm)) and DBB (MDM9615M (Qualcomm)).
- **Memory:** Flash Memory (THGBX2G7B2JLA01 (Toshiba)) and DRAM (H9CKNNN8KTMKR (SK Hynix)) connect to the ABB, DBB, and APP A7.
- **Power Mgmt (PM8018 (Qualcomm), 338S1216 (Dialog))** connects to the Battery and Vibrator.
- **APP A7 (Samsung)** is the central processing unit, connected to ABB, DBB, DRAM, Flash Memory, and various external components.
- **External Components:**
  - **Digital TV** (Orange box with a crossed-out symbol) connects to the APP A7.
  - **T/P Controller (BCM5976 (Broadcom), 343S0645 (TI))** connects to the APP A7.
  - **Audio (338S1201 (Cirrus Logic))** connects to the Speaker, Headphone, and Microphone.
  - **Display Controller A7 (Samsung)** connects to the LCD/OLED.
  - **Camera ISP A7 (Samsung)** connects to the Camera.
  - **Sensors** (Keypad, MicroSD, SIM) connect to the APP A7.
  - **Bluetooth (338S0209 (Murata))** connects to the APP A7.
  - **GPS (WTR10051 (Qualcomm))** connects to the APP A7.
  - **WLAN (338S0208 (TI))** connects to the APP A7.
  - **RF/GPS (Red box with a crossed-out symbol)** connects to the APP A7.

## 5. Apple A7 with dual Cyclone cores (19)

Display side of the PCB#1 in Apple's iPhone 5s [10]

A7 Application Processor (Samsung)  
+ 8 Gb LPDDR3 SDRAM (SK Hynix)  
H9CKNNN8KTMKR

M7 Co-Processor (NXP)  
LPC18A1

Digital Compass  
(Asahi Kasei)  
AKM8963

LTE/WCDMA/CDMA/GSM Transceiver  
+ GPS (Qualcomm) WTR1605L

Duplexer Banks (Murata)

Diversity Down-conversion Mixer  
(Skyworks) SKY73614

Baseband Processor (Qualcomm)  
MDM9615M

Filter (Murata)

## 5. Apple A7 with dual Cyclone cores (20)

### Battery side of the PCB#2 in Apple's iPhone 5s [10]

![](fce2a4a923b40ec0421e00ecb8e809c9_img.jpg)

128 Gb NAND Flash Memory (Toshiba) THGBX2G7B2JLA01

Class D Audio Amplifier (Cirrus Logic) 338S1202

Display Interface (NXP) NXP1610A1

LTE/WCDMA/CDMA PA (Avago) AFEM-7925

LTE/CDMA PA (Skyworks) SKY77572

GSM PA (Skyworks) SKY77493

LTE/WCDMA PA (RFMD) RF3763

LTE PA (Skyworks) SKY77496

Power Management (Dialog) 338S1216

Accelerometer (Bosch) 1ED LP

Gyroscope (STM) B352

Antenna Switch (RFMD) RF1112

Touch Panel Controller (TI) 343S0645

WLAN + Bluetooth (TDK) 339S0209

TI 65730A0P

Touch Panel Controller (Broadcom) BCM5976

Audio Codec (Cirrus Logic) 338S1201

Power Management (Qualcomm) PM8018

LTE/WCDMA/CDMA PA (TriQuint) TQF6414

## 5. Apple A7 with dual Cyclone cores (21)

### Apple's A7 Package-on-Package in the iPhone 5s [10]

![](a0c08a47826f10d19f53bdae6664ca5b_img.jpg)

Cross-section through iPhone 5s motherboard

Apple A7 PoP

Hynix 16GB NAND flash

SDRAM

A7

Hynix 16 GB NAND flash

## 5. Apple A7 with dual Cyclone cores (22)

Introduction of Apple's own low-level graphics and compute API termed Metal

- According to Apple, the existing **OpenGL ES** framework has interposed **too much overhead between the GPU and the software running on it**, leading to inefficiencies and performance loss.
- In order resolve this problem Apple designed their **own C++-based low-level graphics framework** called **Metal** that was introduced in connection with **iOS 8** in **6/2014**.

## 5. Apple A7 with dual Cyclone cores (23)

### Apple's Metal graphics and compute API -1

- It can be used for **writing GPU code** for graphics and general-purpose data-parallel computations in order **to reduce the programming overhead** vs. Open GL or Open GL ES (Open GL for Embedded Systems like mobiles).

![Diagram illustrating the software stack when using the Open GL graphics API. The stack consists of three layers: Apps (top, yellow), Core Animation and Core Graphics (middle, red), and Open GL (bottom, blue).](b7f02e2da7b10a7c4333fe561867900c_img.jpg)

Diagram illustrating the software stack when using the Open GL graphics API. The stack consists of three layers: Apps (top, yellow), Core Animation and Core Graphics (middle, red), and Open GL (bottom, blue).

Figure: Using the Open GL graphics API

![Diagram illustrating the software stack when using the Metal graphics API. The stack consists of two layers: Game (top, red) and Metal (bottom, blue).](9950599fa0b5cbb4f429bc282082235a_img.jpg)

Diagram illustrating the software stack when using the Metal graphics API. The stack consists of two layers: Game (top, red) and Metal (bottom, blue).

Figure: Using the Metal graphics API

## 5. Apple A7 with dual Cyclone cores (24)

### Low-level graphics and compute APIs

![](366613102f1e34db1de83df8d2115642_img.jpg)

| (OpenGL for Embedded Systems)<br>For Android/Symbian (Chronos, since 2003) | OpenGL/ES             | → | Metal      | For Apple iOS 8/<br>MacOS 10.11<br>(since 2015)                            |
|----------------------------------------------------------------------------|-----------------------|---|------------|----------------------------------------------------------------------------|
| Cross platform API (originally Silicon Graphics, (since 2006 Chronos))     | OpenGL                | → | Metal 2    | For Apple iOS 11/<br>MacOS 10.13<br>(since 2017)                           |
| For Windows (Microsoft, since 1994)                                        | Microsoft® DirectX 11 | → | Vulkan     | Cross platform API (Chronos)<br>Replaces OpenGL/<br>OpenGL/ES (since 2016) |
|                                                                            |                       | → | DirectX 12 | For Windows 10 (Microsoft, 2015)                                           |

## 6. Apple A8 with dual Typhoon cores

## 6. Apple A8 with dual Typhoon cores (1)

## 6. The Apple A8 with dual Typhoon cores [28]

- The **A8** emerged in the mobile devices
  - iPhone 6 and
  - iPhone 6 Plusin **2014**.

  Its microarchitecture is **6-wide**, like that of the A7.
- It is a **20 nm shrink of the A7** (fabricated by TSMC rather than Samsung, as previously) with an **improved GPU**.
- It contains **2 billion transistors**, roughly twice than the A7.
- The die size has been reduced by about 13 % to 89 mm<sup>2</sup>.
- The A8 has **approximately the same clock speed as the A7** (1.38 GHz).
- The Typhoon core is **about 10 % faster** than its predecessor (the A7), as indicated in the subsequent Figure for the Geekbench 3 benchmark.

## 6. Apple A8 with dual Typhoon cores (2)

### Main features of the A8

| Appl. proc. | Model no.                           | Image     | Node                         | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.                                 | Utilizing devices                        |
|-------------|-------------------------------------|-----------|------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|----------------------------------------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | Apple A7  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013                                 | iPhone 5S<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | Apple A7  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013                                | iPad Air 9.7"                            |
| A8          | APL1011                             | Apple A8  | 20 nm HKMG                   | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014                                 | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | Apple A8X | 20 nm HKMG                   | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>L3: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR3-1600 (25.6 GB/sec)      | 10/2014                                | iPad Air 2 9.7"                          |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | Apple A9  | 16 nm FinFET<br>14 nm FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015                                 | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | Apple A9X | 16 nm FinFET                 | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015<br>(12.9")<br>3/2016<br>(9.7") | iPad Pro 9.7"<br>iPad Pro 12.9"          |

## 6. Apple A8 with dual Typhoon cores (3)

### Contrasting key features of the A8 vs. the A7 [39]

|                       | Apple A8 (2014)                                  | Apple A7 (2013)                         |
|-----------------------|--------------------------------------------------|-----------------------------------------|
| Manufacturing Process | TSMC 20nm HKMG                                   | Samsung 28nm HKMG                       |
| Die Size              | 89mm <sup>2</sup>                                | 102mm <sup>2</sup>                      |
| Transistor Count      | ~2B                                              | "Over 1B"                               |
| CPU                   | 2 x Apple Enhanced Cyclone<br>ARMv8 64-bit cores | 2 x Apple Cyclone<br>ARMv8 64-bit cores |
| GPU                   | IMG PowerVR GX6450                               | IMG PowerVR G6430                       |

## 6. Apple A8 with dual Typhoon cores (4)

Performance comparison of Apple processors from the A6X to A8X [27]

|            |     |    | Geekbench 3 Scores |              |
|------------|-----|----|--------------------|--------------|
|            |     |    | Single-Thread      | Multi-Thread |
| iPad Air 2 | A8X | 3C | 1798               | 4468         |
| iPhone 6   | A8  | 2C | 1610               | 2881         |
| iPad Air   | A7  | 2C | 1472               | 2663         |
| iPad 4     | A6X | 2C | 770                | 1401         |

The benchmark scores for Geekbench 3 show that the A8, i.e. the 20 nm shrink of the 28 nm A7, has approximately 10% performance improvement over the A7.

## 6. Apple A8 with dual Typhoon cores (5)

Comparing the die plots of A8 and A7 [29]

![](34cfb1835fdf0d248bc2c4d58956a896_img.jpg)

The figure displays die plots comparing the Apple A7 (left) and Apple A8 (right) processors.

**A7 Die Plot:**

- Dimensions: 9.83 x 10.45 mm
- Components include: CPU (with L1, L2 caches), GPU core (x4), GPU shared digital logic, SRAM, DRAM interface, PLL, and Camera interface.

**A8 Die Plot:**

- Dimensions: 8.47 x 10.50 mm
- Components include: CPU (with L1, L2 caches), GPU core (x4), SRAM, DRAM interface, and various memory blocks (DRAM, SRAM, DRAM Cache, SRAM Cache).

## 6. Apple A8 with dual Typhoon cores (6)

The assumed microarchitecture of the Typhoon core of the A8 [29]

A8's Typhoon core has basically the same microarchitecture as A7's Cyclone core, as indicated by a comparison vs. the A7 (see next Table).

## 6. Apple A8 with dual Typhoon cores (7)

Contrasting key features of the microarchitectures of the A8 and A7 [39]

|                              | Apple A7            | Apple A8            |
|------------------------------|---------------------|---------------------|
| CPU Codename                 | Cyclone             | Typhoon             |
| ARM ISA                      | ARMv8-A (32/64-bit) | ARMv8-A (32/64-bit) |
| Issue Width                  | 6 micro-ops         | 6 micro-ops         |
| Reorder Buffer Size          | 192 micro-ops       | 192 micro-ops?      |
| Branch Mispredict Penalty    | 16 cycles (14 - 19) | 16 (14 - 19)?       |
| Integer ALUs                 | 4                   | 4                   |
| Load/Store Units             | 2                   | 2                   |
| Addition (FP) Latency        | 5 cycles            | 4 cycles            |
| Multiplication (INT) Latency | 4 cycles            | 3 cycles            |
| Branch Units                 | 2                   | 2                   |
| Indirect Branch Units        | 1                   | 1                   |
| FP/NEON ALUs                 | 3                   | 3                   |
| L1 Cache per core            | 64KB I\$ + 64KB D\$ | 64KB I\$ + 64KB D\$ |
| L2 Cache per core            | 1MB                 | 1MB                 |
| L3 Cache (shared)            | 4MB                 | 4MB                 |

## 6. Apple A8 with dual Typhoon cores (8)

### Layout of the Typhoon core of the A8

- Despite the fact that A8's Typhoon core has basically the same microarchitecture as A7's Cyclone core, **its transistor count is raised from about 1 billion to about 2 billion.**
- This astonishing doubling of the transistor count may result from the fact that **the A8 is a complete redesign of the A7 on a new process technology of TSMC** while focusing on raising the energy efficiency.
- Actually, Apple declared that **the A8 is up to 50 % more energy efficient than the A7.**

## 6. Apple A8 with dual Typhoon cores (9)

Exploded assembly drawing of the iPhone 6+ [30]

![Exploded assembly drawing of the iPhone 6+ showing internal components. The main logic board is highlighted by a red dashed box and labeled 'Logic board'. Other components include the screen assembly, battery, and various connectors.](8f9a74669c6529fd53f721e1180895a0_img.jpg)

Exploded assembly drawing of the iPhone 6+ showing internal components. The main logic board is highlighted by a red dashed box and labeled 'Logic board'. Other components include the screen assembly, battery, and various connectors.

## 6. Apple A8 with dual Typhoon cores (10)

The front side of the logic board of the iPhone 6+ [31]-1

- Apple A8 APL1011 SoC + Elpida 1 GB LPDDR3 RAM (as denoted by the markings EDF8164A3PM-GD-F)
- Qualcomm MDM9625M LTE Modem
- Skyworks 77802-23 Low Band LTE PAD  
  PAD: Integrated Power Amplifier-Duplexer
- Avago A8020 High Band PAD
- Avago A8010 Ultra High Band PA + FBARS
- TriQuint TQF6410 3G EDGE Power Amplifier Module
- InvenSense MP67B 6-axis Gyroscope and Accelerometer Combo

![Front side of the logic board of the iPhone 6+ showing various components. The large central chip is the Apple A8 SoC. Other components include the LPDDR3 RAM, LTE Modem, and various RF and sensor chips.](5756bd999073356743c1ffb96784832d_img.jpg)

Front side of the logic board of the iPhone 6+ showing various components. The large central chip is the Apple A8 SoC. Other components include the LPDDR3 RAM, LTE Modem, and various RF and sensor chips.

## 6. Apple A8 with dual Typhoon cores (11)

The front side of the logic board of the iPhone 6+ [31]-2

- Qualcomm QFE1000 Envelope Tracking IC
- RF Micro Devices RF5159 Antenna Switch Module
- SkyWorks 77356-8 Mid Band PAD
- Bosch Sensortec BMA280

![Front side of the logic board of the iPhone 6+ showing various components. The image highlights four specific components with colored boxes: a black component (Qualcomm QFE1000 Envelope Tracking IC), an orange component (RF Micro Devices RF5159 Antenna Switch Module), a yellow component (SkyWorks 77356-8 Mid Band PAD), and a black component (Bosch Sensortec BMA280).](1736860af0cbb10c18a7ae6ae12b4332_img.jpg)

Front side of the logic board of the iPhone 6+ showing various components. The image highlights four specific components with colored boxes: a black component (Qualcomm QFE1000 Envelope Tracking IC), an orange component (RF Micro Devices RF5159 Antenna Switch Module), a yellow component (SkyWorks 77356-8 Mid Band PAD), and a black component (Bosch Sensortec BMA280).

## 6. Apple A8 with dual Typhoon cores (12)

The back side of the logic board of the iPhone 6+ [31]-1

![](a0ca2e895d28cff7c1bbb8e7bad3b0a1_img.jpg)

SK Hynix H2JTDG8UD1BMS 128 Gb (16 GB)  
NAND Flash

Murata 339S0228 Wi-Fi Module

Apple/Dialog 338S1251-AZ Power Management IC

Broadcom BCM5976 Touchscreen Controller

NXP LPC18B1UK ARM Cortex-M3  
Microcontroller (also known as the M8 motion  
coprocessor)

NXP 65V10 NFC module + Secure Element  
(likely contains an NXP PN544 NFC controller  
inside)

Qualcomm WTR1625L RF Transceiver

## 6. Apple A8 with dual Typhoon cores (13)

### The back side of the logic board of the iPhone 6+ [31]-2

- Qualcomm WFR1620 receive-only companion chip. Qualcomm states that the WFR1620 is "required for implementation of carrier aggregation with WTR1625L."
- Qualcomm PM8019 Power Management IC
- Texas Instruments 34350694 Touch Transmitter
- AMS AS3923 NFC Booster IC
- Cirrus Logic 338S1201 Audio Codec
- Bosch Sensortec BMP280

![A photograph of the back side of the logic board of an iPhone 6+ (A8 chip). The board features several chips, including the main processor (A8) and various peripheral chips. Specific components are highlighted with colored squares (red, orange, yellow, green) corresponding to the list items: WFR1620 (red), PM8019 (orange), 34350694 (yellow), AS3923 (green), 338S1201 (blue), and BMP280 (black).](829dd33300a024ceec1e3451220752a1_img.jpg)

A photograph of the back side of the logic board of an iPhone 6+ (A8 chip). The board features several chips, including the main processor (A8) and various peripheral chips. Specific components are highlighted with colored squares (red, orange, yellow, green) corresponding to the list items: WFR1620 (red), PM8019 (orange), 34350694 (yellow), AS3923 (green), 338S1201 (blue), and BMP280 (black).

## 7. Apple A8X with triple Typhoon cores

## 7. Apple A8X with triple Typhoon cores (1)

## 7. Apple A8X with triple Typhoon cores

- The **A8X** emerged along with the iPad Air 2 in 10/2014.
- It has **three Typhoon cores** rather than two as in the A8 SoC.
- Furthermore, it has an enhanced GPU in comparison to the A8.

## 7. Apple A8X with triple Typhoon cores (2)

### Main features of the A8X

| Appl. proc. | Model no.                           | Image                             | Node                            | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.                                 | Utilizing devices                        |
|-------------|-------------------------------------|-----------------------------------|---------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|----------------------------------------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                      | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013                                 | iPhone 5S<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                      | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013                                | iPad Air 9.7"                            |
| A8          | APL1011                             | <img alt="Apple A8 chip image"/>  | 20 nm HKMG                      | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014                                 | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | <img alt="Apple A8X chip image"/> | 20 nm HKMG                      | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>L3: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR4-1600 (25.6 GB/sec)      | 10/2014                                | iPad Air 2 9.7"                          |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | <img alt="Apple A9 chip image"/>  | 16 nm FinFET<br>14 nm<br>FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015                                 | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | <img alt="Apple A9X chip image"/> | 16 nm FinFET                    | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015<br>(12.9")<br>3/2016<br>(9.7") | iPad Pro 9.7"<br>iPad Pro 12.9"          |

## 7. Apple A8X with triple Typhoon cores (3)

### Main features of the A8X compared to the Apple A8 [32]

| Apple SoC Comparison  |                       |                       |               |                |
|-----------------------|-----------------------|-----------------------|---------------|----------------|
|                       | A8X                   | A8                    | A7            | A6X            |
| CPU                   | 3x "Enhanced Cyclone" | 2x "Enhanced Cyclone" | 2x Cyclone    | 2x Swift       |
| CPU Clockspeed        | 1.5GHz                | 1.4GHz                | 1.4GHz (iPad) | 1.3GHz         |
| GPU                   | Apple/PVR GX6850      | PVR GX6450            | PVR G6430     | PVR SGX554 MP4 |
| RAM                   | 2GB                   | 1GB                   | 1GB           | 1GB            |
| Memory Bus Width      | 128-bit               | 64-bit                | 64-bit        | 128-bit        |
| Memory Bandwidth      | 25.6GB/sec            | 12.8GB/sec            | 12.8GB/sec    | 17.1GB/sec     |
| L2 Cache              | 2MB                   | 1MB                   | 1MB           | 1MB            |
| L3 Cache              | 4MB                   | 4MB                   | 4MB           | N/A            |
| Transistor Count      | ~3B                   | ~2B                   | >1B           | N/A            |
| Manufacturing Process | TSMC(?) 20nm          | TSMC 20nm             | Samsung 28nm  | Samsung 32nm   |

## 7. Apple A8X with triple Typhoon cores (4)

- Further enhancement of the A8X vs. the A8 SOC, not mentioned in the above Table [32]
- The **GXA6850 GPU of the A8X has 8 cores** rather than only 4, as in case of the GX6450 GPU of the A8 (see next Figure).

## 7. Apple A8X with triple Typhoon cores (5)

### The GXA6850 GPU of the AX8-1 [32]

![](58084970bdd0e711a061181d8e1ea328_img.jpg)

Diagram illustrating the architecture of the GXA6850 GPU, which is part of the Apple A8X processor and features triple Typhoon cores.

The GPU is connected to the Host CPU Bus via the Host CPU Interface. The Host CPU Bus also connects to the System Memory Bus via the System Memory Interface.

The GPU core includes the following components:

- Vertex Data Master
- Pixel Data Master
- Compute Data Master
- Coarse Grain Scheduler
- Core Management Unit
- Multi-level Memory Cache Unit (MCU)
- Unified Shading Cluster Array (containing 16 USC blocks and 4 Shared Texture Units)
- Tiling Co-Processor
- Pixel Co-Processor
- 2D Core (TLA)

Control and Register Bus connects the Host CPU Interface, Coarse Grain Scheduler, Core Management Unit, and the Unified Shading Cluster Array.

System Memory Bus connects the System Memory Interface, Core Management Unit, and Multi-level Memory Cache Unit (MCU).

## 7. Apple A8X with triple Typhoon cores (6)

### The GXA6850 GPU of the AX8 -2 [33]

- Each of the 8 graphics cores of the GXA6850 (called USC in the above Figure) includes 32 FP32 ALUs.
- Consequently, the 8 graphics cores have altogether 256 FP32 ALUs.
- Each ALU can perform 2 operations per cycle, thus the GXA6850 can execute  $256 \times 2 = 512$  operations/cycle.
- At an assumed clock rate of 450 MHz this results in 230 GFLOPS, a value that exceeds by a small margin the FP performance of NVIDIA's K1.

## 7. Apple A8X with triple Typhoon cores (7)

Implementing the DRAM memory in form of two external chips [27]

Apple implemented the larger (2 GB) DRAM memory of the A8X in form of two external memory chips mounted onto the PC board on both sides of the A8X chip, rather than as stacked memory as in previous designs, as seen below.

![Close-up image of the Apple A8X chip mounted on a circuit board, flanked by two external ELPIDA DRAM chips. The A8X chip is centered, and the DRAM chips are mounted on both sides.](687907d817ed6f8fa73f5fbf3d159e88_img.jpg)

Close-up image of the Apple A8X chip mounted on a circuit board, flanked by two external ELPIDA DRAM chips. The A8X chip is centered, and the DRAM chips are mounted on both sides.

Figure: ELPIDA DRAM chips mounted onto the PC board on both sides of the A8X [27]

## 7. Apple A8X with triple Typhoon cores (8)

Die plot of the A8X [32]

![](ee9b6704de74d58f8d805dfc0e22a2d3_img.jpg)

Die plot of the Apple A8X chip showing the layout of its components:

- 8-Core GPU (Large area on the left)
- 3-Core CPU (Area below the GPU)
- L3 cache SRAM 4 MB (Rectangular area near the CPU)
- SDRAM Interface (Two interfaces, one near the top and one near the bottom)
- SDRAM Interface (Area near the top right, adjacent to the L3 cache)
- SDRAM (Area adjacent to the top right SDRAM Interface)

Source: chipworks

## 7. Apple A8X with triple Typhoon cores (9)

Performance of the iPad Air 2 vs. previous iPad models measured using the Geekbench 3.2 benchmark [34]

#### GECKBENCH 3.2: MULTI-CORE (Higher is better)

![](2303c01c42eb5b45539e6b0324701ee1_img.jpg)

Horizontal bar chart showing Geekbench 3.2 Multi-Core scores (Higher is better) for various iPad models. The chart compares Overall, Floating point, Integer, and Memory performance across four models: iPad Air 2 (speculated), iPad Air, iPad 4, and iPad 2/Mini.

| Model                   | Overall | Floating point | Integer | Memory |
|-------------------------|---------|----------------|---------|--------|
| iPad Air 2 (speculated) | 4,477   | 4,829          | 5,015   | 2,698  |
| iPad Air                | 2,683   | 3,049          | 2,823   | 1,675  |
| iPad 4                  | 1,428   | 1,557          | 1,242   | 1,543  |
| iPad 2/Mini             | 498     | 674            | 445     | 253    |

## 7. Apple A8X with triple Typhoon cores (10)

Performance of the iPad Air 2 vs. competing models measured using the Geekbench 3.2 benchmark [35]

![](282053518e4b8043f41b60fab17713bb_img.jpg)

| Geekbench     | 2013         |               |                   |                   | 2014              |              |               |               |
|---------------|--------------|---------------|-------------------|-------------------|-------------------|--------------|---------------|---------------|
|               | Nexus 7      | Nexus 9       | Kindle Fire HDX 7 | Galaxy Tab S 10.5 | Nvidia Shield Tab | iPad 4       | iPad Air      | iPad Air 2    |
| Single core   | Score<br>587 | Score<br>1807 | Score<br>881      | Score<br>888      | Score<br>1079     | Score<br>770 | Score<br>1472 | Score<br>1812 |
| Multiple core | 1844         | 3220          | 2646              | 2642              | 3202              | 1402         | 2664          | 4477          |
| Processor     | S4 Pro       | 64-bit K1     | Snapdragon 800    | Exynos 5 Octa     | Tegra K1          | A6X          | 64-bit A7     | 64-bit A8X    |
| CPU clock     | 1.4 GHz      | 2.2 GHz       | 2.2GHz            | 1.9 GHz           | 2.2 GHz           | 1.4 GHz      | 1.4 GHz       | 1.9 GHz       |
| RAM (Drive)   | 1GB          | 2GB           | 2GB               | 3GB               | 2GB               | 1GB          | 1GB           | 2GB           |

Horizontal bar chart comparing Geekbench scores (Single Core and Multiple Core) for various devices in 2013 and 2014. The X-axis represents scores, ranging from 0 to 4500.

Legend: Single Core (Blue), Multiple Core (Green).

Annotations:

- 2 Cyclone cores (pointing to Nexus 9)
- 3 Typhoon cores (pointing to iPad Air 2)

Scores are recorded by Primate Lab's Geekbench, relative to a PowerMac G5 1.6 GHz, which represents 1000. iPad increase over previous generation. Nexus 9 scores reported by GSMarena.com

## 7. Apple A8X with triple Typhoon cores (11)

Implications of the extremely high performance of Apple's A8X-based iPad Air 2 (including 3 Typhoon cores) [50] -1

- Intel lost Apple as a perspective buyer of their chips for the iPad line, and the iPad Air 2 also severely hit the perspective of their not so successful Atom line.
- Intel tried to raise their market share on the mobile market by paying subsidies to OEMs who were buying Atom processors, but due to their high losses suffered Intel first stopped paying subsidies and then in 4/2016 the firm announced their withdrawal from the mobile market.
- NVIDIA's Tegra 4 chips were not successful as well, so the firm announced in 05/2014 that they will abandon the phone market.

Apple's iPad Air 2 with its A8X processor and its GPU with 256 EUs became a very powerful rival to NVIDIA's subsequent 64-bit K1 chip including a GPU with 192 EUs.

As a consequence, NVIDIA also gave up their tablet interests.

## 7. Apple A8X with triple Typhoon cores (12)

Implications of the extremely high performance of Apple's A8X-based iPad Air 2 (including 3 Typhoon cores) -2

- **NVIDIA's** Tegra 4 chips were not successful as well, so **the firm announced in 05/2014 that they will abandon the phone market**.
- Apple's iPad Air 2 with its A8X processor and its GPU with 256 EUs became a very powerful rival to NVIDIA's subsequent 64-bit K1 chip including a GPU with 192 EUs.
- As a consequence, in 6/2016 (at Computex) NVIDIA's CEO declared the firm's leaving both the smartphone and tablet market by saying [61]:  
  "We are no longer interested in that market". He adds, "Anybody can build smartphones, and we're happy to enjoy these devices, but we'll let someone else build them".
- Instead NVIDIA became interested in designing in-car computers and car infotainment systems.

## 7. Apple A8X with triple Typhoon cores (13)

Implications of the extremely high performance of Apple's A8X-based iPad Air 2 (including 3 Typhoon cores) [36] -3

- Texas Instruments (TI) OMAP family is used in Kindle Fire and a variety of Samsung's Galaxy Tab models.
- TI however failed to compete successfully against Apple so was forced to announce a major shift in its business strategy in 9/2012, by leaving the consumer application processor business entirely and focusing on embedded applications, such as using processors in cars.

## 7. Apple A8X with triple Typhoon cores (14)

### iPad Air 2 board with main components [37]

- Apple APL1012 A8X 64-bit Processor
- Elpida/Micron Technology F8164A3MD 8 Gb (1 GB) RAM (1 GB x 2 = 2 GB total)
- SK Hynix H2]TDG8UD1BMR 128 Gb (16 GB) NAND Flash
- NXP 65V10 NFC Controller (as found in the iPhone 6 and 6 Plus)
- Apple (Cirrus Logic) 338S1213 Audio Codec
- NXP Semiconductors LPC18B1UK ARM Cortex-M3 Microcontroller (Apple M8 Motion Coprocessor)
- Murata 339S02541 Wi-Fi Module

![Diagram of the iPad Air 2 main board showing the locations of the main components. The components are highlighted with colored boxes corresponding to the list: Apple APL1012 A8X 64-bit Processor (Red), Elpida/Micron Technology F8164A3MD 8 Gb (1 GB) RAM (Orange), SK Hynix H2]TDG8UD1BMR 128 Gb (16 GB) NAND Flash (Yellow), NXP 65V10 NFC Controller (Green), Apple (Cirrus Logic) 338S1213 Audio Codec (Blue), NXP Semiconductors LPC18B1UK ARM Cortex-M3 Microcontroller (Pink), and Murata 339S02541 Wi-Fi Module (Black).](fc5604242afd229d6a030bd57dfee1b5_img.jpg)

Diagram of the iPad Air 2 main board showing the locations of the main components. The components are highlighted with colored boxes corresponding to the list: Apple APL1012 A8X 64-bit Processor (Red), Elpida/Micron Technology F8164A3MD 8 Gb (1 GB) RAM (Orange), SK Hynix H2]TDG8UD1BMR 128 Gb (16 GB) NAND Flash (Yellow), NXP 65V10 NFC Controller (Green), Apple (Cirrus Logic) 338S1213 Audio Codec (Blue), NXP Semiconductors LPC18B1UK ARM Cortex-M3 Microcontroller (Pink), and Murata 339S02541 Wi-Fi Module (Black).

## 8. Apple A9 with dual Twister cores

## 8. Apple A9 with dual Twister cores (1)

## 8. Apple A9 with dual Twister cores [42]

- The A9 emerged in the mobile devices
  - iPhone 6s and
  - iPhone 6s Plusin 9/2015.
- It is dual sourced, Samsung fabricates the A8 in the **16 nm FinFET** technology whereas TSMC in the **14 nm technology**.
- Apple did not reveal a transistor count for the A9.
- The **clock rate** of the A9 has considerable increased vs. the A8, from 1.4 GHz to **1.85 GHz**.
- Apple states that the A9 has **70% higher CPU performance** and **90% more graphics performance** than its predecessor, the A8 [42].

## 8. Apple A9 with dual Twister cores (2)

### Contrasting key components of the A9 vs. the A8 [40]

|                       | Apple A9 (2015)                           | Apple A8 (2014)                         |
|-----------------------|-------------------------------------------|-----------------------------------------|
| Manufacturing Process | TSMC 16nm FinFET /<br>Samsung 14nm FinFET | TSMC 20nm HKMG                          |
| Die Size              | 104.5mm <sup>2</sup> /96mm <sup>2</sup>   | 89mm <sup>2</sup>                       |
| CPU                   | 2 x Apple Twister<br>ARMv8 64-bit cores   | 2 x Apple Typhoon<br>ARMv8 64-bit cores |
| GPU                   | IMG PowerVR GT7600                        | IMG PowerVR GX6450                      |

## 8. Apple A9 with dual Twister cores (3)

### Main features of the A9

| Appl. proc. | Model no.                           | Image     | Node                         | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.                           | Utilizing devices                        |
|-------------|-------------------------------------|-----------|------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|----------------------------------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | Image A7  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013                           | iPhone 5s<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | Image A7  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013                          | iPad Air                                 |
| A8          | APL1011                             | Image A8  | 20 nm HKMG                   | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014                           | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | Image A8X | 20 nm HKMG                   | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>L3: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR3-1600 (25.6 GB/sec)      | 10/2014                          | iPad Air 2                               |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | Image A9  | 16 nm FinFET<br>14 nm FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015                           | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | Image A9X | 16 nm FinFET                 | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015 (12.9")<br>3/2016 (9.7") | iPad Pro 9.7"<br>iPad Pro 12.9"          |

## 8. Apple A9 with dual Twister cores (4)

Contrasting the alternative implementations of A9 [40]

![Die shot of the Apple A9 processor (APL1022) manufactured by TSMC using 16 nm FinFET technology. The die is large and features a complex layout with various functional blocks.](8eb40c780942191d9da9a0851328b462_img.jpg)

Die shot of the Apple A9 processor (APL1022) manufactured by TSMC using 16 nm FinFET technology. The die is large and features a complex layout with various functional blocks.

APL1022 – TSMC 16 nm FinFET

![Die shot of the Apple A9 processor (APL0898) manufactured by Samsung using 14 nm FinFET technology. The die is smaller and features a more compact layout compared to the TSMC version.](3a9f5f9c35b60ac892ab42fd077101d1_img.jpg)

Die shot of the Apple A9 processor (APL0898) manufactured by Samsung using 14 nm FinFET technology. The die is smaller and features a more compact layout compared to the TSMC version.

APL0898 – Samsung 14 nm FinFET

## 8. Apple A9 with dual Twister cores (5)

### Evolution of the microarchitectures of the A line from the A7 to A9X [41]

|                       | A9X                    | A9                       | A8              | A7              |
|-----------------------|------------------------|--------------------------|-----------------|-----------------|
| CPU                   | 2x Twister             | 2x Twister               | 2x Typhoon      | 2x Cyclone      |
| CPU Clockspeed        | 2.26GHz                | 1.85GHz                  | 1.4GHz          | 1.3GHz          |
| GPU                   | PVR 12 Cluster Series7 | PVR GT7600               | PVR GX6450      | PVR G6430       |
| RAM                   | 4GB LPDDR4             | 2GB LPDDR4               | 1GB LPDDR3      | 1GB LPDDR3      |
| Memory Bus Width      | 128-bit                | 64-bit                   | 64-bit          | 64-bit          |
| Memory Bandwidth      | 51.2GB/sec             | 25.6GB/sec               | 12.8GB/sec      | 12.8GB/sec      |
| L2 Cache              | 3MB (shared)           | 3MB (shared)             | 1MB (shared)    | 1MB (shared)    |
| L3 Cache              | None                   | 4MB (Victim)             | 4MB (Inclusive) | 4MB (Inclusive) |
| Manufacturing Process | TSMC 16nm FinFET       | TSMC 16nm & Samsung 14nm | TSMC 20nm       | Samsung 28nm    |

## 8. Apple A9 with dual Twister cores (6)

Die plot of the A9 including dual Twister cores [41]

![](69a2adeb3e48dbd7e9e1af814a9fbb03_img.jpg)

Die plot of the Apple A9 processor showing the layout of its components. The plot highlights several key areas:

- GPU Core Pair 1&2
- GPU Core Pair 3&4
- GPU Shared Logic
- GPU Core Pair 5&6
- L3 Cache
- Dual Core Twister CPU

## 8. Apple A9 with dual Twister cores (7)

Contrasting key features of the microarchitectures of the A8 and A7 [40]

|                               | Apple A8            | Apple A9            |
|-------------------------------|---------------------|---------------------|
| CPU Codename                  | Typhoon             | Twister             |
| ARM ISA                       | ARMv8-A (32/64-bit) | ARMv8-A (32/64-bit) |
| Issue Width                   | 6 micro-ops         | 6 micro-ops         |
| Reorder Buffer Size           | 192 micro-ops       | 192 micro-ops       |
| Branch Mispredict Penalty     | 16 (14 - 19)        | 9                   |
| Integer ALUs                  | 4                   | 4                   |
| Shifter ALUs                  | 2                   | 4                   |
| Load/Store Units              | 2                   | 2                   |
| Addition (FP32) Latency       | 4 cycles            | 3 cycles            |
| Multiplication (FP32) Latency | 5 cycles            | 4 cycles            |
| Addition (INT) Latency        | 1 cycle             | 1 cycle             |
| Multiplication (INT) Latency  | 3 cycles            | 3 cycles            |
| Branch Units                  | 2                   | 2                   |
| Indirect Branch Units         | 1                   | 1                   |
| FP/NEON ALUs                  | 3 (3 Add or 2 Mult) | 3 (3 Add or 3 Mult) |
| L1 Cache                      | 64KB I\$ + 64KB D\$ | 64KB I\$ + 64KB D\$ |
| L2 Cache                      | 1MB (per core?)     | 3MB (shared)        |
| L3 Cache                      | 4MB (inclusive)     | 4MB (exclusive)     |

## 8. Apple A9 with dual Twister cores (8)

### Key differences between the microarchitectures of the A9 and the A8

- The A9 has
  - two more shifter ALUs
  - faster 32-bit FP units and
  - a redesigned L2 - L3 cache architecture.
- The **new cache architecture** means that in the A9
  - the **L2** cache became **shared** rather per core (as supposed to be in the A7) and
  - the **L3** cache became a **victim cache** rather than an inclusive cache, as in the A7.
  - Further on the L2 and L3 caches provide in the **A9 shorter access times**, as seen in the next Figure.

## 8. Apple A9 with dual Twister cores (9)

Memory latency (ns) vs. transfer size (KB) of the A8 and A9 memory [41]

![](44229cd77a85081f3968b4bf05d232d3_img.jpg)

Memory Latency

Latency in ns (lower is better)

Transfer Size in KB

iPhone 6 (A8) iPhone 6s (A9)

## 8. Apple A9 with dual Twister cores (10)

- **Note** that the L3 cache of the A8 became a victim cache (exclusive cache).  
  This means that recently used data that do not fit into the L2 cache and became evicted will be kept in the L3 cache, i.e. they remain still on-chip.  
  This improves performance and reduces power consumption.
- By reorganizing the L3 cache to a victim cache the 4 MB L3 cache of the A9 becomes more useful than an inclusive L3 that would hold the entire content of the 3 MB L2 cache and would leave only 1 MB space for other data [41].

## 8. Apple A9 with dual Twister cores (11)

Die micrograph of the dual core Twister CPU [40]

![Die micrograph of the dual core Twister CPU. The image shows a large, rectangular die structure, predominantly brown/orange, with a large, dense, black grid pattern covering the central and lower portions, likely representing the core logic or memory array. Smaller, pink/red rectangular blocks are visible around the edges and near the top center, possibly representing I/O pads or peripheral components.](7e480a409b0a47faddefda8fc99dcf85_img.jpg)

Die micrograph of the dual core Twister CPU. The image shows a large, rectangular die structure, predominantly brown/orange, with a large, dense, black grid pattern covering the central and lower portions, likely representing the core logic or memory array. Smaller, pink/red rectangular blocks are visible around the edges and near the top center, possibly representing I/O pads or peripheral components.

## 8. Apple A9 with dual Twister cores (12)

Integer performance increase (SPECint2000) of A9 vs. A8 [40]

| SPECint2000 - Estimated Scores |      |      |             |                          |
|--------------------------------|------|------|-------------|--------------------------|
|                                | A9   | A8   | % Advantage | % Architecture Advantage |
| 164.gzip                       | 1191 | 842  | 41%         | 9%                       |
| 175.vpr                        | 2017 | 1228 | 64%         | 32%                      |
| 176.gcc                        | 3148 | 1810 | 74%         | 42%                      |
| 181.mcf                        | 3124 | 1420 | 120%        | 88%                      |
| 186.crafty                     | 3411 | 2021 | 69%         | 37%                      |
| 197.parser                     | 1892 | 1129 | 68%         | 35%                      |
| 252.eon                        | 3926 | 1933 | 103%        | 71%                      |
| 253.perlbmk                    | 2768 | 1666 | 66%         | 34%                      |
| 254.gap                        | 2857 | 1821 | 57%         | 25%                      |
| 255.vortex                     | 3177 | 1716 | 85%         | 53%                      |
| 256.bzip2                      | 1944 | 1234 | 58%         | 25%                      |
| 300.twolf                      | 2020 | 1633 | 24%         | -8                       |

## 8. Apple A9 with dual Twister cores (13)

FP performance increase (Geekbench3) of A9 vs. A8 [40]

| Geekbench 3 - Floating Point Performance |               |                |             |                          |
|------------------------------------------|---------------|----------------|-------------|--------------------------|
|                                          | A9            | A8             | % Advantage | % Architecture Advantage |
| <b>BlackScholes ST</b>                   | 11.9 Mnodes/s | 7.85 Mnodes/s  | 52%         | 19%                      |
| <b>BlackScholes MT</b>                   | 23.3 Mnodes/s | 15.5 Mnodes/s  | 50%         | 18%                      |
| <b>Mandelbrot ST</b>                     | 1.83 GFLOPS   | 1.18 GFLOPS    | 55%         | 23%                      |
| <b>Mandelbrot MT</b>                     | 3.56 GFLOPS   | 2.34 GFLOPS    | 52%         | 20%                      |
| <b>Sharpn Filter ST</b>                  | 1.69 MFLOPS   | 0.98 GFLOPS    | 72%         | 40%                      |
| <b>Sharpn Filter MT</b>                  | 3.32 MFLOPS   | 1.94 MFLOPS    | 71%         | 39%                      |
| <b>Blur Filter ST</b>                    | 2.22 GFLOPS   | 1.41 GFLOPS    | 57%         | 25%                      |
| <b>Blur Filter MT</b>                    | 4.33 GFLOPS   | 2.78 GFLOPS    | 56%         | 24%                      |
| <b>SGEMM ST</b>                          | 5.64 GFLOPS   | 3.83 GFLOPS    | 47%         | 15%                      |
| <b>SGEMM MT</b>                          | 10.8 GFLOPS   | 7.48 GFLOPS    | 44%         | 12%                      |
| <b>DGEMM ST</b>                          | 2.76 GFLOPS   | 1.87 GFLOPS    | 48%         | 15%                      |
| <b>DGEMM MT</b>                          | 5.24 GFLOPS   | 3.61 GFLOPS    | 45%         | 13%                      |
| <b>SFFT ST</b>                           | 2.83 GFLOPS   | 1.77 GFLOPS    | 60%         | 28%                      |
| <b>SFFT MT</b>                           | 5.68 GFLOPS   | 3.47 GFLOPS    | 64%         | 32%                      |
| <b>DFFT ST</b>                           | 2.64 GFLOPS   | 1.68 GFLOPS    | 57%         | 25%                      |
| <b>DFFT MT</b>                           | 4.98 GFLOPS   | 3.29 GFLOPS    | 51%         | 19%                      |
| <b>N-Body ST</b>                         | 1150 Kpairs/s | 735.8 Kpairs/s | 56%         | 24%                      |
| <b>N-Body MT</b>                         | 2.27 Mpairs/s | 1.46 Mpairs/s  | 55%         | 23%                      |
| <b>Ray Trace ST</b>                      | 4.16 MP/s     | 2.76 MP/s      | 51%         | 19%                      |
| <b>Ray Trace MT</b>                      | 8.15 MP/s     | 5.45 MP/s      | 50%         | 17%                      |

## 8. Apple A9 with dual Twister cores (14)

Graphics performance (3DMark 1.2 Unlimited) of A9 vs. the competition [40]

![](b54038322f35f7200081ccfdd4a8bfbd_img.jpg)

3DMark 1.2 Unlimited - Overall  
Score - Higher is Better

Horizontal bar chart showing 3DMark 1.2 Unlimited graphics performance scores for various devices. The Apple A9 (dual Twister cores) is represented by the orange bars.

| Device                 | Score  |
|------------------------|--------|
| Apple iPhone 6s Plus   | 27,833 |
| Apple iPhone 6s        | 27,646 |
| Xiaomi Mi Note Pro     | 26,705 |
| Samsung Galaxy Note 5  | 25,316 |
| Google Nexus 6         | 23,236 |
| HTC One (M9)           | 23,019 |
| Samsung Galaxy S6      | 22,476 |
| Samsung Galaxy S6 edge | 22,476 |
| Samsung Galaxy Note 4  | 20,717 |
| Xiaomi Mi Note         | 20,455 |
| Motorola Moto X (2014) | 19,758 |
| HTC One (M8)           | 19,631 |
| OnePlus One            | 19,568 |
| LG G4                  | 18,529 |
| Apple iPhone 6 Plus    | 17,788 |
| Google Nexus 5         | 17,529 |
| Apple iPhone 6         | 17,222 |
| Meizu MX4Pro           | 16,104 |
| Apple iPhone 5s        | 15,102 |
| Huawei Ascend Mate 7   | 12,381 |

## 9. Apple A9X with dual Twister cores

## 9. Apple A9X with dual Twister cores (1)

## 9. Apple A9X with dual Twister cores

- The **A9X** appeared in the 12.9" iPad Pro (released in 11/2015) and then in the 9.7" iPad Pro version (released in 3/2016).

These models are designated as the **1. generation iPad Pro** models.

- **Key modifications vs. the A8X:**
  - **Two Twister cores** vs. three Typhoon cores
  - **Much higher clock frequency** (up to 2.26 GHz vs. 1.5 GHz)
  - **Much higher memory speed** (DDR4 with 3200 MT/s vs. DDR3 with 1600 MT/s)
  - **3 MB L2 without L3** vs. 2 MB L2 and 4 MB L3, and
  - **higher performance graphics** (12 graphics cores vs. 5).

## 9. Apple A9X with dual Twister cores (2)

### 9. Main features of the A9X

| Appl. proc. | Model no.                           | Image                             | Node                         | Die size              | CPU                     | CPU ISA | CPU cache                                        | GPU                                                | Memory (up to)                                       | Intro.  | Utilizing devices                        |
|-------------|-------------------------------------|-----------------------------------|------------------------------|-----------------------|-------------------------|---------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|---------|------------------------------------------|
| A7          | APL0698 or S5L8960                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.3 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 9/2013  | iPhone 5S<br>iPad Mini 2<br>iPad Mini 3  |
|             | APL5698 or S5L8965                  | <img alt="Apple A7 chip image"/>  | 28 nm HKMG                   | 102 mm <sup>2</sup>   | 2x Cyclone 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR G6430 (4C) @ 450 MHz (115.2 GFLOPS)        | 1 GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)      | 10/2013 | iPad Air                                 |
| A8          | APL1011                             | <img alt="Apple A8 chip image"/>  | 20 nm HKMG                   | 89 mm <sup>2</sup>    | 2x Typhoon 1.4 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 1 MB<br>L3: 4 MB | PowerVR GX6450 (4C) @ 450 MHz (115.2 GFLOPS)       | 1GB<br>64-bit SCh<br>LPDDR3-1600 (12.8 GB/sec)       | 9/2014  | iPhone 6<br>iPhone 6 Plus                |
| A8X         | APL1012                             | <img alt="Apple A8X chip image"/> | 20 nm HKMG                   | 128 mm <sup>2</sup>   | 3xTyphoon 1.5 GHz       | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 2 MB<br>L3: 4 MB | PowerVR GXA6850 (5C) @ 450 MHz (230.4 GFLOPS)      | 2 GB<br>64-bit DCh<br>LPDDR3-1600 (25.6 GB/sec)      | 10/2014 | iPad Air 2                               |
| A9          | APL1022 (TSMC)<br>APL0898 (Samsung) | <img alt="Apple A9 chip image"/>  | 16 nm FinFET<br>14 nm FinFET | 104.5 mm <sup>2</sup> | 2xTwister 1.85 GHz      | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: 4 MB | PowerVR GT7600 (6C) @ 450 MHz (172.8 GFLOPS)       | 2 GB<br>64-bit SCh<br>LPDDR4-3200 (25.6 GB/sec)      | 9/2015  | iPhone 6s<br>iPhone 6s Plus<br>iPhone SE |
| A9X         | APL1021 (TSMC)                      | <img alt="Apple A9X chip image"/> | 16 nm FinFET                 | 147 mm <sup>2</sup>   | 2xTwister 2.16-2.26 GHz | ARMv8-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>L3: none | PowerVR 7XT series (12C) @ n.a. MHz (345.6 GFLOPS) | 2 GB/4 GB<br>64-bit DCh<br>LPDDR4-3200 (51.2 GB/sec) | 11/2015 | iPad Pro 9.7"<br>iPad Pro 12.9"          |

## 9. Apple A9X with dual Twister cores (3)

Die plot of the A9X including 12 graphics cores [43]

![](f8788dcd19850c3a526698d4a147dab6_img.jpg)

Die plot of the Apple A9X chip showing the layout of the 12 graphics cores and the dual Twister CPU.

The graphics cores are arranged in a 3x4 grid:

- GPU Core Pair 1&2
- GPU Core Pair 3&4
- GPU Core Pair 5&6
- GPU Core Pair 7&8
- GPU Core Pair 9&10
- GPU Core Pair 11&12

Shared GPU Logic is located centrally, connecting the core pairs.

The Dual Core Twister CPU is located in the bottom right corner.

## 9. Apple A9X with dual Twister cores (4)

Memory latency (ns) vs. transfer size (KB) of the A9X and A9 memory [41]

![](3ebaedbd0913c29c9bce534bccbe419e_img.jpg)

Memory Latency In Nanoseconds

Latency in ns (Lower is Better)

Transfer Size in KB

Legend: iPad Pro (A9X), iPhone 6s (A9)

The impact of the missing L3

10. Apple A10 with quad big.LITTLE cores

## 10. Apple A10 with quad big.LITTLE cores (1)

## 10. Apple A10 with quad big.LITTLE cores -1

- The A10 was released along with the iPhone 7 and iPhone 7s in 9/2016.
- It includes Apple's **first quad core CPU (in big.LITTLE configuration)** replacing symmetrical multicores used in prior A-series processors.
  - There are two performance cores, called **Hurricane**, clocked up to 2.34 GHz
  - and two high efficiency cores, called **Zephyr**, clocked up to 1.1 GHz (?).

The high performance cores are 40 percent faster than those of the A9 chip and the high-efficiency cores consume only 20 % of the high performance cores.

- The CPU makes use of Apple's **first gen. performance controller** that allows to utilize simultaneously either the big or the LITTLE cores (called **cluster migration**).

## 10. Apple A10 with quad big.LITTLE cores (2)

Apple's A10 position within the evolution of mobile CPU cores

![](b385220379a59067a173d244d6fd0d9f_img.jpg)

Diagram illustrating the CPU architecture of mobile processors, showing the evolution of core configurations:

- Single CPU core
- Multiple CPU cores
  - Symmetrical multicores
  - big.LITTLE core clusters
    - Exclusive cluster allocation
    - Inclusive core allocation (GTS)
  - DynamIQ core clusters

Evolution timeline of mobile CPU cores:

| Vendor              | Processor                            | Core Count | Year | Notes                |
|---------------------|--------------------------------------|------------|------|----------------------|
| Apple               | ARM1176 (2007) until A4 (2010)       |            |      |                      |
|                     | A5 (2011) (2C)                       |            |      |                      |
|                     | A10 (2016) (2+2)                     |            |      | Highlighted in green |
|                     | A11 (2017) (2+4)                     |            |      |                      |
| Samsung Exynos      | 3110 (2010)                          |            |      |                      |
|                     | 3250 2C (2011)<br>4412 4C (2012)     |            |      |                      |
|                     | 5410 (2013) (4+4)                    |            |      |                      |
|                     | 5420 (2013) (4+4)                    |            |      |                      |
|                     | 9810 (2018) (4+4)                    |            |      |                      |
| Qualcomm Snapdragon | MSM 7225 (2007)                      |            |      |                      |
|                     | 8260 2C (2013)<br>400 4C (2013)      |            |      |                      |
|                     | 808 (2+4) (2014)<br>810 (4+4) (2015) |            |      |                      |
|                     | 845 (2018) (4+4)                     |            |      |                      |
| Huawei Kirin        | (K3V1) (2009)                        |            |      |                      |
|                     | (K3V2 (2012))                        |            |      |                      |
|                     | 920 (4+4) (2014)                     |            |      |                      |
| MediaTek            | MT6218B (2003)                       |            |      |                      |
|                     | MT6582 4C (2013)<br>MT6592 8C (2013) |            |      |                      |
|                     | MT6595 8C (2014)                     |            |      |                      |

## 10. Apple A10 with quad big.LITTLE cores (3)

## 10. Apple A10 quad big.LITTLE cores -2

- Apple utilizes the **same GPU** as the A9 (Imagination Technology's GT7600) but **parts of the original design were replaced** to achieve 50 % speed-up and 66 % less power consumption vs. the original design.
- The A10 is manufactured by TSMC's **16 nm FinFET** process and includes **3.3 billion transistors on a Si area of 125 mm<sup>2</sup>**.

## 10. Apple A10 with quad big.LITTLE cores (4)

Core areas of different mobile processors [50]

![](f5cc4e774bc925c8fb27327ea133563f_img.jpg)

Diagram illustrating the core areas of different mobile processors, comparing Apple Zephyr, Cortex-A53, and Cortex-A72 cores, alongside the Broadwell and Qualcomm Kryo and Samsung M1 processors.

| Processor       | Core Area             |
|-----------------|-----------------------|
| Apple Zephyr    | 0.78mm <sup>2</sup>   |
| Cortex-A53      | 0.45mm <sup>2</sup> * |
| Cortex-A72      | 1.54mm <sup>2</sup>   |
| Broadwell       | 11.6mm <sup>2</sup> * |
| Apple Hurricane | 4.18mm <sup>2</sup>   |
| Qualcomm Kryo   | 2.79mm <sup>2</sup> * |
| Samsung M1      | 2.06mm <sup>2</sup> * |

## 10. Apple A10 with quad big.LITTLE cores (5)

### Main features of the A10 Fusion SoC

| Appl. proc.S  | Model no.      | Image | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                                  | Memory (up to)     | Intro.  | Utilizing devices                                 |
|---------------|----------------|-------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|----------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)  | APL1W24        | A10   | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz<br>(>250 GFLOPS) (redesigned) | 2 GB/3 GB LPDDR4   | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion) | APL1071 (TSMC) | A10X  | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                            | 3 GB/4 GB LPDDR4   | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic    | APL1W72 (TSMC) | A11   | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.38 GHz) + 4x Mistral (1.69 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                                | 2 GB/3 GB? LPDDR4X | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic    | APL1W82 (TSMC) | A12   | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                                | 3 GB/4 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic   | APL1083 (TSMC) | A12X  | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (7C)                                                | 4 GB/6 GB LPDDR4X  | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

## 10. Apple A10 with quad big.LITTLE cores (6)

Die plot of the A10 as revealed from Chipworks [45]

![](47e45f7287d5a0669d20fdcbc353eb2f_img.jpg)

Die plot of the Apple A10 processor, showing the layout of the CPU and GPU cores, SRAM, and SDRAM interfaces.

Key components labeled:

- GPU core (x2)
- 6-core GPU
- SDRAM interface (x4)
- big core (x2)
- small
- L2 Quad-core CPU arb
- L2
- SRAM L3 (x2)
- L3 Arb
- Dual-core CPU (little)? (x2)

## 10. Apple A10 with quad big.LITTLE cores (7)

### Main features of Apple's iPhone7 and iPhone7 Plus mobiles [51]

| Apple iPhone 7 and 7 Plus |                                                                  |                                                                                                                                                                            |                                                  |                                                    |
|---------------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|----------------------------------------------------|
|                           | Apple iPhone 7                                                   | Apple iPhone 7 Plus                                                                                                                                                        | Apple iPhone 6s                                  | Apple iPhone 6s Plus                               |
| SoC                       | Apple A10 Fusion<br>2 x 2.34 GHz Hurricane<br>2x 1.1 GHz? Zephyr |                                                                                                                                                                            | Apple A9<br>2 x 1.85GHz Apple Twister            |                                                    |
| GPU                       | 6 Core PowerVR Plus GPU                                          |                                                                                                                                                                            | PowerVR GT7600                                   |                                                    |
| Display                   | 4.7-inch 1334 x 750 IPS<br>LCD, DCI-P3                           | 5.5-inch 1920 x 1080 IPS<br>LCD, DCI-P3                                                                                                                                    | 4.7-inch 1334 x 750 IPS<br>LCD, sRGB             | 5.5-inch 1920 x 1080 IPS<br>LCD, sRGB              |
| Size / Mass               | 138.3 x 67.1 x 7.1 mm,<br>138 grams                              | 158.2 x 77.9 x 7.3 mm,<br>188 grams                                                                                                                                        | 138.3 x 67.1 x 7.1 mm,<br>143 grams              | 158.2 x 77.9 x 7.3mm,<br>192 grams                 |
| Battery                   | 1960 mAh<br>(7.55Whr)                                            | 2900 mAh<br>(11.17Whr)                                                                                                                                                     | 1715 mAh<br>(6.6Whr)                             | 2750 mAh<br>(10.59Whr)                             |
| Rear Cameras              | 12MP f/1.8<br>OIS, Wide Color Gamut,<br>Quad LED True Tone Flash | 12MP f/1.8 wide angle,<br>OIS, Wide Color Gamut,<br>Quad LED True Tone Flash<br>12MP f/2.8 telephoto,<br>2x optical zoom, Wide Color<br>Gamut, Quad LED True<br>Tone Flash | 12MP with 1.22µm pixels +<br>True Tone Flash     | 12MP with 1.22µm pixels +<br>True Tone Flash + OIS |
| Front Camera              | 7MP f/2.2, Wide Color<br>Gamut, Retina Flash                     | 7MP f/2.2, Wide Color<br>Gamut, Retina Flash                                                                                                                               | 5MP F/2.2 +<br>Retina Flash                      | 5MP F/2.2 +<br>Retina Flash                        |
| Storage                   | 32GB/128GB/256GB                                                 |                                                                                                                                                                            | 16GB/64GB/128GB (Launch)<br>32GB/128GB (Refresh) |                                                    |
| I/O                       | Apple Lightning connector                                        |                                                                                                                                                                            | Apple Lightning connector, 3.5mm headset         |                                                    |
| WiFi                      | 2.4/5GHz 2x2 802.11a/b/g/n/ac, BT 4.2, NFC                       |                                                                                                                                                                            | 2.4/5GHz 2x2 802.11a/b/g/n/ac, BT 4.2, NFC       |                                                    |
| Launch Price              | \$649/749/849 32/128/256GB                                       | \$769/869/969 32/128/256GB                                                                                                                                                 | \$649/749/849 16/64/128GB                        | \$749/849/949<br>16GB/64/128GB                     |

## 10. Apple A10 with quad big.LITTLE cores (8)

Geekbench 4 and AnTuTu benchmark results of high-end mobiles [52]

| Geekbench 4 | OnePlus 3T                   | LG G6    | Google Pixel | Galaxy S8 | iPhone SE | iPhone 6s | iPhone 6s Plus | iPhone 7 | iPhone 7 Plus |  |
|-------------|------------------------------|----------|--------------|-----------|-----------|-----------|----------------|----------|---------------|--|
| Single Core | 1912                         | 1856     | 1806         | 1838      | 2410      | 2374      | 2399           | 3406     | 3538          |  |
| Multicore   | 4314                         | 4261     | 4377         | 6202      | 4043      | 3982      | 4019           | 5394     | 5953          |  |
| AnTuTu 3D   | 152376                       | 140374   | 145469       | 165521    | no score  | no score  | 141813         | 173642   | 175606        |  |
| Processor   | Qualcomm SD 821 (Adreno 530) |          | SD 835/AS40  |           | A9        |           | A9             |          | A10 Fusion    |  |
| Peak CPU    | 2.35 GHz                     | 2.35 GHz | 2.15 GHz     | 2.35 GHz  | 1.8 GHz   | 1.85 GHz  | 1.85 GHz       | 2.34 GHz | 2.34 GHz      |  |
| RAM         | 6 GB                         | 4 GB     | 4 GB         | 4 GB      | 1 GB      | 2 GB      | 2 GB           | 2 GB     | 3 GB          |  |

![](45e7a4af10dbd8d97adcb607391dc4cc_img.jpg)

Single Core

Multicore

OnePlus 3T

LG G6

Google Pixel

Galaxy S8

iPhone SE

iPhone 6s

iPhone 6s Plus

iPhone 7

iPhone 7 Plus

Ref. value of 4000

0 650 1300 1950 2600 3250 3900 4550 5200 5850 6500

Scores are recorded by Primate Lab's Geekbench 4 relative to an Intel Core i7-6600U, which represents 4000.

OnePlus 3T

LG G6

Google Pixel

Galaxy S8

iPhone 6s Plus

iPhone 7

iPhone 7 Plus

0 18000 36000 54000 72000 90000 108000 126000 144000 162000 180000

Scores are recorded by AnTuTu CPU, UI & 3D benchmark

## 10. Apple A10 with quad big.LITTLE cores (9)

**Remark:** Geekbench 4 benchmarks are measured using a Microsoft Surface Book with an Intel Core i7-6600U (Skylake) processor as a baseline with a score of 4000 points [62].

Main features of the reference system:

- # of Cores: 2
- # of Threads: 4
- Processor Base Frequency: 2.60 GHz
- Max Turbo Frequency: 3.40 GHz
- Cache: 4 MB
- TDP: 15 W
- Graphics: Intel HD Graphics 520

11. Apple A10X with hexa big.LITTLE cores

## 11. Apple A10X with hexa big.LITTLE cores (1)

## 11. Apple A10X with hexa big.LITTLE cores

- Introduced in 6/2017.
- Fabricated on TSMCs 10nm FinFET process on 96 mm<sup>2</sup> Si area.
- It includes
  - 3 Hurricane and 3 Zephyr cores instead of 2+2 cores as the A10 does and
  - 3 to 4 GB LPDDR4 RAM rather than 2 to 3 GB as the A10.
- It appeared in the 10.5" iPad Pro and 12.9" iPad Pro tablet models, called also as the 2. generation iPad Pro models.

## 11. Apple A10X with hexa big.LITTLE cores (2)

### Main features of the A10X Fusion SoC

| Appl. proc.S  | Model no.      | Image                        | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                                  | Memory (up to)     | Intro.  | Utilizing devices                                 |
|---------------|----------------|------------------------------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|----------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)  | APL1W24        | <img alt="A10 chip image"/>  | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz<br>(>250 GFLOPS) (redesigned) | 2 GB/3 GB LPDDR4   | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion) | APL1071 (TSMC) | <img alt="A10X chip image"/> | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                            | 3 GB/4 GB LPDDR4   | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic    | APL1W72 (TSMC) | <img alt="A11 chip image"/>  | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.38 GHz) + 4x Mistral (1.69 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                                | 2 GB/3 GB? LPDDR4X | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic    | APL1W82 (TSMC) | <img alt="A12 chip image"/>  | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                                | 3 GB/4 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic   | APL1083 (TSMC) | <img alt="A12X chip image"/> | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (7C)                                                | 4 GB/6 GB LPDDR4X  | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

**Note** that the A10X Fusion SoC has

- 3 Hurricane and 3 Zephyr cores rather than only 2+2 cores as the A10 SoC and
- 3 to 4 GB LPDDR4 RAM rather than 2 to 3 GB as the A10 SoC.

## 11. Apple A10X with hexa big.LITTLE cores (3)

### Main features of Apple's A6X to A10X tablet SoCs [49]

| Apple SoC Comparison  |                          |                        |                   |                |
|-----------------------|--------------------------|------------------------|-------------------|----------------|
|                       | A10X                     | A9X                    | A8X               | A6X            |
| CPU                   | 3x Hurricane + 3x Zephyr | 2x Twister             | 3x Typhoon        | 2x Swift       |
| CPU Clockspeed        | ~2.36GHz                 | 2.26GHz                | 1.5GHz            | 1.3GHz         |
| GPU                   | 12 Cluster GPU           | PVR 12 Cluster Series7 | Apple/PVR GXA6850 | PVR SGX554 MP4 |
| Typical RAM           | 4GB LPDDR4               | 4GB LPDDR4             | 2GB LPDDR3        | 1GB LPDDR2     |
| Memory Bus Width      | 128-bit                  | 128-bit                | 128-bit           | 128-bit        |
| Memory Bandwidth      | TBD                      | 51.2GB/sec             | 25.6GB/sec        | 17.1GB/sec     |
| L2 Cache              | 8MB                      | 3MB                    | 2MB               | 1MB            |
| L3 Cache              | None                     | None                   | 4MB               | N/A            |
| Manufacturing Process | TSMC 10nm FinFET         | TSMC 16nm FinFET       | TSMC 20nm         | Samsung 32nm   |

## 11. Apple A10X with hexa big.LITTLE cores (4)

Die size of Apple's A5X to A10X tablet SoCs [49]

![](877cc2db8b4859a851aebf179fc3b868_img.jpg)

Line chart titled "Apple Tablet SoC Die Size" showing the die size in  $\text{mm}^2$  versus the SoC generation (A5X, A6X, A8X, A9X, A10X).

| SoC  | Die Size in $\text{mm}^2$ | Process Node |
|------|---------------------------|--------------|
| A5X  | 165                       | 45 nm        |
| A6X  | 123                       | 32 nm        |
| A8X  | 128                       | 20 nm        |
| A9X  | 147                       | 16 nm        |
| A10X | 96                        | 10 nm        |

## 11. Apple A10X with hexa big.LITTLE cores (5)

### Main features of Apple's A9X and A10X based tablets [60]

|                   | iPad Pro 10.5" (2017)                                                                                        | iPad Pro 12.9" (2017)                                  | iPad Pro 9.7" (2016)                                                    | iPad Pro 12.9" (2015)                                     |
|-------------------|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------|-----------------------------------------------------------|
| SoC               | Apple A10X Fusion<br>3x Apple Hurricane performance cores<br>3x Apple Zephyr efficiency cores<br>12 core GPU |                                                        | Apple A9X<br>2x Apple Twister @ ~2.2GHz<br>PowerVR 12 Cluster Series7XT |                                                           |
| Display           | 10.5-inch 2224x1668 IPS<br>LCD<br>DCI-P3, 120Hz                                                              | 12.9-inch 2732x2048 IPS<br>LCD<br>DCI-P3, 120Hz        | 9.7-inch 2048x1536 IPS<br>LCD<br>DCI-P3                                 | 12.9-inch 2732x2048 IPS<br>LCD<br>sRGB                    |
| Dimensions        | 250.6 x 174.1 x 6.1 mm<br>469 / 477 grams (WiFi / LTE)                                                       | 305.7 x 220.6 x 6.9 mm<br>677 / 692 grams (WiFi / LTE) | 240.0 x 169.5 x 6.1 mm<br>437 / 444 grams (WiFi / LTE)                  | 305.7 x 220.6 x 6.9 mm<br>713 / 723 grams (WiFi / LTE)    |
| RAM               | ?                                                                                                            | 4GB LPDDR4                                             | 2GB LPDDR4                                                              | 4GB LPDDR4<br>WiFi:                                       |
| NAND              | All: 64GB / 256GB / 512 GB                                                                                   |                                                        | All:<br>32GB / 128GB / 256GB                                            | 32GB / 128GB / 256GB<br>WiFi + Cellular:<br>128GB / 256GB |
| Battery           | 30.4 Wh                                                                                                      | 41.0 Wh                                                | 27.5 Wh                                                                 | 38.5 Wh                                                   |
| Front Camera      | 7MP, f/2.2, Auto HDR, Wide Color Gamut, Retina Flash                                                         |                                                        | 5MP, f/2.2                                                              | 1.2MP, f/2.2                                              |
| Rear Camera       | 12MP, 1.22µm pixels, f/1.8, PDAF, OIS, Auto HDR, Wide Color Gamut, True Tone Quad-LED flash                  |                                                        | 12MP, 1.22µm pixels, f/2.2, True Tone LED flash                         | 8MP, 1.1µm pixels, f/2.4                                  |
| Cellular SIM Size | 2G / 3G / 4G LTE (Category 9)<br>NanoSIM                                                                     |                                                        | 2G / 3G / 4G LTE (Category 4)<br>NanoSIM                                |                                                           |
| Wireless          | 802.11a/b/g/n/ac 2x2 MIMO, BT 4.2 LE, GPS/GLONASS<br>Wi-Fi/Wi-Fi+LTE                                         |                                                        | 802.11a/b/g/n/ac 2x2 MIMO, BT 4.2 LE, GPS/GLONASS<br>Wi-Fi              |                                                           |
| Connectivity      |                                                                                                              |                                                        |                                                                         |                                                           |
| Launch OS         | iOS 10                                                                                                       |                                                        | iOS 9                                                                   |                                                           |
| Launch Price      | 649-1229 \$                                                                                                  |                                                        | 599-1079 \$                                                             |                                                           |

12. Apple A11 with dual big and quad LITTLE cores

## 12. Apple A11 with dual big and quad LITTLE cores (1)

## 12. Apple A11 with dual big and quad LITTLE cores

- Introduced in 9/2017 along with the iPhone 8, iPhone 8 Pro and iPhone X.
- It is Apple's **first 10 nm** SoC, manufactured by TSMC as a PoP package with 2GB LPDDR4X memory in the iPhone 8 and 3 GB LPDDR4 memory in the iPhone 8 Plus and iPhone X.
- It is based on the **ARMv8.2-A ISA** (supporting therefore e.g. FP16 processing).
- Transistor count: **4.3 billion**.

## 12. Apple A11 with dual big and quad LITTLE cores (2)

### Main features of the A11 Bionic SoC

| Appl. proc.S69 696 | Model no.      | Image                        | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                                     | Memory (up to)     | Intro.  | Utilizing devices                                 |
|--------------------|----------------|------------------------------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|-------------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)       | APL1W24        | <img alt="A10 chip image"/>  | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz<br>(>250 GFLOPS)<br>(redesigned) | 2 GB/3 GB LPDDR4   | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion)      | APL1071 (TSMC) | <img alt="A10X chip image"/> | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                               | 3 GB/4 GB LPDDR4   | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic         | APL1W72 (TSMC) | <img alt="A11 chip image"/>  | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.38 GHz) + 4x Mistral (1.69 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                                   | 2 GB/3 GB? LPDDR4X | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic         | APL1W82 (TSMC) | <img alt="A12 chip image"/>  | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                                   | 3 GB/4 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic        | APL1083 (TSMC) | <img alt="A12X chip image"/> | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (7C)                                                   | 4 GB/6 GB LPDDR4X  | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

## 12. Apple A11 with dual big and quad LITTLE cores (3)

### Main features of the Apple A11 Bionic SoC [53]

| Model        | Apple iPhone7                                 | Apple iPhone8 256 GB                          | Apple iPhone8 Plus | Apple iPhone X |
|--------------|-----------------------------------------------|-----------------------------------------------|--------------------|----------------|
| Launched     | 10/2016                                       | 09/2017                                       | 09/2017            | 11/2017        |
| SoC          | Apple A10 Fusion APL1024                      | Apple A11 Bionic                              |                    |                |
| CPU          | DC Hurricane (2.34 GHz) + DC Zephyr (1.1 GHz) | DC Monsoon (2.39 GHz) + QC Mistral (1.42 GHz) |                    |                |
| GPU          | PowerVR GT7600 Plus                           | In-house 3 cores                              |                    |                |
| NPU          | --                                            | Dual core                                     |                    |                |
| ISP          | Yes                                           | In-house                                      |                    |                |
| Coprocessor  | M10 motion                                    | M11 Motion                                    |                    |                |
| RAM          | 2 GB                                          | 2 GB                                          | 3 GB               | 3 GB           |
| Flash memory | 32 GB                                         | 256 GB                                        | 64 /256 GB         | 64/256 GB      |
| Technology   | 16 nm                                         | 10 nm                                         |                    |                |

## 12. Apple A11 with dual big and quad LITTLE cores (4)

### 12. A11 Bionic

- The A11 Bionic SoC has
  - two performance cores called **Monsoon**, clocked at 3.39 GHz and
  - four high efficiency cores, called **Mistral**, clocked at 1.42 GHz.
- The performance cores are 25 percent faster than those of the A10 chip, and the high-efficiency cores are 70 percent faster those of the A10 chip.
- It makes use of a new, **2. gen. performance controller** that allows to utilize **up to all six cores simultaneously**, if needed (in contrast to the prior controller that activated either the big or the LITTLE cores).

## 12. Apple A11 with dual big and quad LITTLE cores (5)

Apple's A11 position within the evolution of mobile CPU cores

![](cdf78577d07f3375edf8d981fc288d6b_img.jpg)

Diagram illustrating the CPU architecture of mobile processors, showing the evolution of core configurations:

- Single CPU core
- Multiple CPU cores
  - Symmetrical multicores
  - big.LITTLE core clusters
    - Exclusive cluster allocation
    - Inclusive core allocation (GTS)
  - DynamIQ core clusters

Evolution timeline of mobile CPU cores:

| Vendor              | Processor                      | Core Count | Year      | Notes |
|---------------------|--------------------------------|------------|-----------|-------|
| Apple               | ARM1176 (2007) until A4 (2010) | 1C         | 2007-2010 |       |
| Apple               | A5 (2011)                      | 2C         | 2011      |       |
| Apple               | A10 (2016)                     | (2+2)      | 2016      |       |
| Apple               | A11 (2017)                     | (2+4)      | 2017      | (GTS) |
| Samsung Exynos      | 3110 (2010)                    | 2C         | 2010      |       |
| Samsung Exynos      | 3250 2C (2011)                 | 2C         | 2011      |       |
| Samsung Exynos      | 4412 4C (2012)                 | 4C         | 2012      |       |
| Samsung Exynos      | 5410 (2013)                    | (4+4)      | 2013      |       |
| Samsung Exynos      | 5420 (2013)                    | (4+4)      | 2013      |       |
| Samsung Exynos      | 9810 (2018)                    | (4+4)      | 2018      |       |
| Qualcomm Snapdragon | MSM 7225 (2007)                | 1C         | 2007      |       |
| Qualcomm Snapdragon | 8260 2C (2013)                 | 2C         | 2013      |       |
| Qualcomm Snapdragon | 400 4C (2013)                  | 4C         | 2013      |       |
| Qualcomm Snapdragon | 808 (2+4) (2014)               | (2+4)      | 2014      |       |
| Qualcomm Snapdragon | 810 (4+4) (2015)               | (4+4)      | 2015      |       |
| Qualcomm Snapdragon | 845 (2018)                     | (4+4)      | 2018      |       |
| Huawei Kirin        | (K3V1) (2009)                  | 1C         | 2009      |       |
| Huawei Kirin        | (K3V2 (2012))                  | 2C         | 2012      |       |
| Huawei Kirin        | 920 (4+4) (2014)               | (4+4)      | 2014      |       |
| MediaTek            | MT6218B (2003)                 | 1C         | 2003      |       |
| MediaTek            | MT6582 4C (2013)               | 4C         | 2013      |       |
| MediaTek            | MT6592 8C (2013)               | 8C         | 2013      |       |
| MediaTek            | MT6595 8C (2014)               | 8C         | 2014      |       |

## 12. Apple A11 with dual big and quad LITTLE cores (6)

### 12. A11 Bionic -2

- It is Apple's first SoC with an **in-house designed GPU (including 3 cores)** that has about the same performance as the prior PowerVR GT7600 from Imagination Technologies, used in the A10 but has 50 % less power consumption.
- It is also Apple's first SoC with a **Neural Engine Unit (NPU)** in order to give higher level support for **AI applications**.
- The A11 Bionic includes **4.3 billion transistors**, much more than Qualcomm's Snapdragon (3 billion) or Intel's desktop quad-core Skylake chip (1.75 billion) [54], on a Si area of **88 mm<sup>2</sup>** (that is 30 % less than that of the A10).

## 12. Apple A11 with dual big and quad LITTLE cores (6b)

Support of FP16 [63]

![](b9dc3e3a1dafbc5bcd30435478addb9d_img.jpg)

16-Bit Floating Point

ARM v8.2

| Precision                       | Core | 1  | 2 | 3  | 4  | 5  | 6  | 7  | 8  |
|---------------------------------|------|----|---|----|----|----|----|----|----|
| Double Precision<br>(Apple A10) | 1    | 64 |   |    |    |    |    |    |    |
|                                 | 2    |    |   | 64 |    |    |    |    |    |
| Single Precision<br>(Apple A10) | 1    | 32 |   | 32 |    | 32 |    | 32 |    |
|                                 | 2    |    |   |    |    |    |    |    |    |
| Half Precision<br>(Apple A11)   | 1    | 16 |   | 16 |    | 16 |    | 16 |    |
|                                 | 2    |    |   |    | 16 |    | 16 |    | 16 |
|                                 | 3    |    |   |    |    | 16 |    | 16 |    |
|                                 | 4    |    |   |    |    |    | 16 |    | 16 |
|                                 | 5    |    |   |    |    |    |    | 16 |    |
|                                 | 6    |    |   |    |    |    |    |    | 16 |
|                                 | 7    |    |   |    |    |    |    |    |    |
|                                 | 8    |    |   |    |    |    |    |    |    |

## 12. Apple A11 with dual big and quad LITTLE cores (7)

### A11 Bionic floor plane [55]

![](3678debce2fab7d3d0144c70a6a162c9_img.jpg)

Diagram of the Apple A11 Bionic floor plane showing major components:

- GPU (x2)
- GPU shared logic
- PLLS
- DDR (x2)
- A3
- CDI
- FS
- DDR
- HDMI
- PLL
- NPU
- SRAM (x2)
- CPU 2 (x2)
- CPU 1 (x2)
- TxRx
- A1
- USB
- FS

## 12. Apple A11 with dual big and quad LITTLE cores (8)

### The Neural Processing Unit (NPU) [56]

- It is a dedicated **two core hardware unit** to speed up machine learning tasks, including face identification, image enhancements etc.
- The NPU is capable to perform **600 billion operations per second**.
- The NPU allows to perform **AI applications faster and more energy-efficient** than while using the CPU with GPU support.

## 12. Apple A11 with dual big and quad LITTLE cores (9)

Main components as seen on the motherboard of the iPhone 8 -1 [55]

![](2c386c2f9fce92d900564b43725760dd_img.jpg)

Diagram illustrating the main components of the iPhone 8 -1 motherboard:

- Skyworks SKY13764-15 RF Switch
- Skyworks SKY13767 RF Switch
- Avago PA Duplexer (likely)
- Bosch Inertial Measurement Unit
- NXP Display Port Multiplexer 1612A1
- Wireless Charging BCM59355
- 338S00295 Audio Amp
- 338S00295 Audio Amp
- TI SN2501 Battery Charger
- TI LM 3539 Backlight LED Driver
- TI TPS65730 Display Power Management
- EPICOS D5341 RF Switch
- Intel PMB 5757 RF Transceiver
- Cypress CYPD2104 USB Type-C Controller
- Intel PMIC PMB6848
- PMIC 338500309
- 338S00295 Audio Amp
- SK Hynix 3D NAND
- 338S00248 Audio Codec
- USI Wi-Fi Module 339S00397

Tech Insights

## 12. Apple A11 with dual big and quad LITTLE cores (10)

Main components as seen on the motherboard of the iPhone 8 -2 [55]

![](ecaf55d564250830bf6c4165f2feeacc_img.jpg)

ALPS e-Compass

A11 APL1W72  
With Micron 3GB LPDDR4X SDRAM

Intel PMB9948 Baseband Processor

Apple/Dialog  
338S00306 PMIC

Qorvo QM81004  
Envelope Tracking

Avago 8066LC PAM

Avago 8056LE PAM

Qorvo QM76041 PAM

NXP NFC 80V18

## 12. Apple A11 with dual big and quad LITTLE cores (11)

Apple's Metal 2 graphics API introduced along with the iOS11 and A11 [57]

- Metal is a low-level graphics computing framework that has a number of successive releases with more and more enhancements targeting subsequent iOS and MacOS releases.
- From these releases Apple renamed the one introduced along with the iOS11 and the A11 Bionic processor as **Metal 2** in 06/2017.
- Metal 2 targets first of all VR and deep learning.

### Remark

Metal 2 introduces among others a **new memory model** that adopts and extends the C++11 memory consistency model and atomic functions for **thread synchronization** between threads within or across thread groups.

## 12. Apple A11 with dual big and quad LITTLE cores (12)

**Remark:** Low-level graphics and compute APIs

Metal API  
for Apple's iOS

(OpenGL for  
Embedded Systems)  
For Android/Symbian  
(Chronos, since 2003)

Cross platform API  
(originally Silicon Graphics,  
(since 2006 Chronos)

For Windows  
(Microsoft, since 1994)

![OpenGL ES logo](58edf2adae9816fe9931e55db37c287f_img.jpg)

OpenGL ES logo

![OpenGL logo](5ab01c5de59b6eb800c2b9b133bb7583_img.jpg)

OpenGL logo

![Microsoft DirectX 11 logo](8356cf9d5002eb22ee4a55562f107ee1_img.jpg)

Microsoft DirectX 11 logo

![Metal API logo (gray M)](a29b6e1a1b079703f4e9ad0266ae1977_img.jpg)

Metal API logo (gray M)

![Metal 2 API logo (green M)](acc1692d4dbfc70a0efc8448ca011e7c_img.jpg)

Metal 2 API logo (green M)

Metal  
For Apple iOS 8/  
MacOS 10.11  
(since 2014)

Metal 2  
For Apple iOS 11/  
MacOS 10.13  
(since 2017)

![Vulkan logo](7a6c70846723dc86f899bbb8584aaa83_img.jpg)

Vulkan logo

Cross platform API  
(Chronos)  
Replaces OpenGL/  
OpenGL/ES  
(since 2016)

![DirectX 12 logo](825bd003c52e5a8b5c692d29213bdacb_img.jpg)

DirectX 12 logo

For Windows 10  
(Microsoft, 2015)

## 12. Apple A11 with dual big and quad LITTLE cores (13)

#### Single core Geekbench 4 scores of Apple's iPhones [58]

| iPhone 8<br>Apple A11 Bionic @ 2.4 GHz      | 4217 |
|---------------------------------------------|------|
| iPhone 8 Plus<br>Apple A11 Bionic @ 2.4 GHz | 4216 |
| iPhone X<br>Apple A11 Bionic @ 2.4 GHz      | 4205 |
| iPhone 7 Plus<br>Apple A10 Fusion @ 2.3 GHz | 3437 |
| iPhone 7<br>Apple A10 Fusion @ 2.3 GHz      | 3388 |
| iPhone 6s Plus<br>Apple A9 @ 1.8 GHz        | 2389 |
| iPhone SE<br>Apple A9 @ 1.8 GHz             | 2371 |
| iPhone 6s<br>Apple A9 @ 1.8 GHz             | 2213 |
| iPhone 6 Plus<br>Apple A8 @ 1.4 GHz         | 1404 |
| iPhone 6<br>Apple A8 @ 1.4 GHz              | 1360 |
| iPhone 5s<br>Apple A7 @ 1.3 GHz             | 1267 |
| iPhone 5<br>Apple A6 @ 1.3 GHz              | 754  |
| iPhone 5c<br>Apple A6 @ 1.3 GHz             | 743  |
| iPhone 4S<br>Apple A5 @ 800 MHz             | 284  |

## 12. Apple A11 with dual big and quad LITTLE cores (14)

Geekbench 4 single core and multi core scores of high-end mobiles [59]

| Geekbench 4 | MacBook Pro 13" 2017 | Huawei P10          | Xiaomi Mi 6         | Samsung Galaxy S8   | iPhone SE | iPhone 7   | iPhone 7 Plus | iPhone 8   | iPhone 8 Plus | iPhone X   |
|-------------|----------------------|---------------------|---------------------|---------------------|-----------|------------|---------------|------------|---------------|------------|
| Single Core | 4229                 | 1886                | 1900                | 1965                | 2410      | 3328       | 3332          | 4189       | 4142          | 4017       |
| Multicore   | 8959                 | 5763                | 5996                | 6495                | 4043      | 5545       | 5558          | 9983       | 9883          | 9286       |
| Processor   | Intel Core i5 7267U  | Hisilicon Kirin 960 | Qualcomm Snapd. 835 | Samsung Exynos 8895 | A9        | A10 Fusion | A10 Fusion    | A11 Bionic | A11 Bionic    | A11 Bionic |
| CPU clock   | 3.5 GHz              | 2.25 GHz            | 1.9 GHz             | 1.6 GHz             | 1.8 GHz   | 2.34 GHz   | 2.34 GHz      | ?          | ?             | ?          |
| RAM         | 8 GB                 | 4 GB                | 6 GB                | 4 GB                | 1 GB      | 2 GB       | 3 GB          | 2 GB       | 3 GB          | 3 GB       |
| Display     | 2560x1600            | 1080x1920           | 1080x1920           | 1440x2960           | 640x1136  | 750x1334   | 1080x1920     | 750x1334   | 1080x1920     | 1125x2436  |

![](1d648bacf7b4f1d0c2fbd884f070e151_img.jpg)

Single Core

Multicore

MacBook Pro

Huawei P10

Xiaomi Mi 6

Galaxy S8

iPhone SE

iPhone 7

iPhone 7 Plus

iPhone 8

iPhone 8 Plus

iPhone X

Ref. value of 4000

Scores are recorded by Primate Lab's Geekbench 4 relative to an Intel Core i7-6600U, which represents 4000.

## 12. Apple A11 with dual big and quad LITTLE cores (15)

**Remark:** Geekbench 4 benchmarks are measured using a Microsoft Surface Book with an Intel Core i7-6600U (Skylake) processor (9/2015) as a baseline with a score of 4000 points [62].

Main features of the reference system:

- # of Cores: 2
- # of Threads: 4
- Processor Base Frequency: 2.60 GHz
- Max Turbo Frequency: 3.40 GHz
- Cache: 4 MB
- TDP: 15 W
- Graphics: Intel HD Graphics 520

13. Apple A12 with dual big and quad LITTLE cores

## 13. Apple A12 with dual big and quad LITTLE cores (1)

## 13. Apple A12 with dual big and quad LITTLE cores

- Introduced in 9/2017 along with the iPhone 8, iPhone 8 Pro and iPhone X.
- It is the **first 7 nm commercial SoC**, manufactured by TSMC as a PoP package with 4GB LPDDR4x memory in the iPhone XS and XS Max as well as 3 GB LPDDR4x memory in the iPhone XR.
- The A12 incorporates **dual Vortex cores** (2.50 GHz) and **quad Tempest cores** (1.59 GHz).

All six cores may run in parallel operated by the 2. gen. Power Controller, introduced along with the A11.

- It executes the **ARMv8.3-A ISA**.
- Transistor count: **6.9 billion**.

## 13. Apple A12 with dual big and quad LITTLE cores (2)

### Main features of the A12 Bionic SoC

| Appl. proc.S6 | Model no.      | Image                        | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                               | Memory (up to)     | Intro.  | Utilizing devices                                 |
|---------------|----------------|------------------------------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|-------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)  | APL1W24        | <img alt="A10 chip image"/>  | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz (>250 GFLOPS) (redesigned) | 2 GB/3 GB LPDDR4   | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion) | APL1071 (TSMC) | <img alt="A10X chip image"/> | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                         | 3 GB/4 GB LPDDR4   | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic    | APL1W72 (TSMC) | <img alt="A11 chip image"/>  | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.38 GHz) + 4x Mistral (1.69 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                             | 2 GB/3 GB? LPDDR4X | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic    | APL1W82 (TSMC) | <img alt="A12 chip image"/>  | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                             | 4 GB/3 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic   | APL1083 (TSMC) | <img alt="A12X chip image"/> | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (7C)                                             | 4 GB/6 GB LPDDR4X  | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

## 13. Apple A12 with dual big and quad LITTLE cores (3)

Max. clock frequency vs. core loading of the A12 [64]

| Maximum Frequency vs Loaded Threads<br>Per-Core Maximum MHz |      |      |      |      |      |      |
|-------------------------------------------------------------|------|------|------|------|------|------|
| Apple A11                                                   | 1    | 2    | 3    | 4    | 5    | 6    |
| Big 1                                                       | 2380 | 2325 | 2083 | 2083 | 2083 | 2083 |
| Big 2                                                       |      | 2325 | 2083 | 2083 | 2083 | 2083 |
| Little 1                                                    |      |      | 1694 | 1587 | 1587 | 1587 |
| Little 2                                                    |      |      |      | 1587 | 1587 | 1587 |
| Little 3                                                    |      |      |      |      | 1587 | 1587 |
| Little 4                                                    |      |      |      |      |      | 1587 |
| Apple A12                                                   | 1    | 2    | 3    | 4    | 5    | 6    |
| Big 1                                                       | 2500 | 2380 | 2380 | 2380 | 2380 | 2380 |
| Big 2                                                       |      | 2380 | 2380 | 2380 | 2380 | 2380 |
| Little 1                                                    |      |      | 1587 | 1562 | 1562 | 1538 |
| Little 2                                                    |      |      |      | 1562 | 1562 | 1538 |
| Little 3                                                    |      |      |      |      | 1562 | 1538 |
| Little 4                                                    |      |      |      |      |      | 1538 |

## 13. Apple A12 with dual big and quad LITTLE cores (4)

Main functional units of the A12 Bionic SoC [65]

![](5fb91e7895e390abec542d9328a870ef_img.jpg)

Diagram illustrating the main functional units of the Apple A12 Bionic SoC.

The SoC features a dual big and quad LITTLE core architecture, connected by a CC Fabric.

**Big Core Units (Left):**

- GPU Core0
- GPU Core1
- GPU Core2
- GPU Core3

**LITTLE Core Units (Right):**

- Tempest CPU (x2)
- Vortex CPU (x2)

**Central Units:**

- ISP
- Video Processor
- Depth Engine
- HEVC En/Decoder
- Control MCU
- Secure Enclave (SEP)
- NPU
- CC Fabric
- Sys Cache
- Always-on MCU
- Storage Controller

**Peripheral Units:**

- L2
- Audio Subsys
- IMC
- Display Engine

## 13. Apple A12 with dual big and quad LITTLE cores (5)

Floor plan of the A12 Bionic SoC [64]

![](a6a33dd8d6fd64d81e4fd9652f0c86bd_img.jpg)

Floor plan of the Apple A12 Bionic SoC. The chip is divided into several major functional blocks:

- DDR Logic (located in the top left and bottom left corners).
- Big Cores (located in the bottom left quadrant).
- NPU (Neural Processing Unit) (located below the Big Cores).
- System Cache (4x Slices) (located centrally, connected to the CPU Complex).
- CPU Complex (L2 4x Banks) (located centrally, connected to the System Cache).
- Small L2 (x2 Banks) (located near the CPU Complex).
- Small Cores (located in the bottom right quadrant).
- GPU (Graphics Processing Unit) (located in the top right quadrant).
- GPU Core (located near the GPU block).

The image is credited to Tech Insights and Floor Plan By AnkitTech.

## 13. Apple A12 with dual big and quad LITTLE cores (6)

### Major enhancements

1. Enhanced cache architecture
2. Improved neural engine
3. Improved GPU

## 13. Apple A12 with dual big and quad LITTLE cores (7)

#### a) Enhanced cache architecture

##### Cache sizes of the A12 vs. the preceding A11 [64]

| Measured and Estimated Cache Sizes |                                                                               |                                                                                      |
|------------------------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| SoC                                | Apple A12                                                                     | Apple A11                                                                            |
| Big L1\$                           | 128KB                                                                         | 64KB                                                                                 |
| Big L2\$                           | 128 instances<br><b>6MB</b> per core/thread<br><b>8MB total</b> at 64KB/inst  | 128 instances<br><b>6MB</b> per core/thread<br><b>8MB total</b> at 64KB/inst         |
| Small L1\$                         | 32KB                                                                          | 32KB                                                                                 |
| Small L2\$                         | 32 instances<br><b>1.5MB</b> per core/thread<br><b>2MB total</b> at 64KB/inst | 16 + 2(?) instances<br><b>512KB</b> per core/thread<br><b>1MB total</b> at 64KB/inst |
| System Cache                       | 4x 16 instances<br>(double size)<br><b>8MB</b> at 128KB/inst                  | 2x 32 instances<br><b>4MB</b> at 64KB/inst                                           |

Note that typically, cache sizes were doubled, except of the L2 caches of the big cores.

## 13. Apple A12 with dual big and quad LITTLE cores (8)

Full random latency of A12 caches vs. A11 caches (linear scale) [64]

![](d24d2a6c29ed7ac1827b2985ab9dac34_img.jpg)

Line graph showing Full random latency (ns) versus Test Depth (KB) for A12 and A11 caches. The Y-axis (Latency) ranges from 0 to 200 ns. The X-axis (Test Depth) ranges from 16 KB to 65536 KB.

Legend:

- A12 Big 2500 MHz
- A12 Little 1587 MHz
- A11 Big 2380 MHz
- A11 Little 1587 MHz

The graph illustrates that the A12 caches exhibit significantly lower latency than the A11 caches across all tested depths, particularly for the Big caches. The A12 Big cache (2500 MHz) shows the lowest latency, followed by the A12 Little cache (1587 MHz). The A11 caches show much higher latency, with the A11 Big cache (2380 MHz) having the highest latency among the Big caches, and the A11 Little cache (1587 MHz) having the highest latency among the Little caches.

ANANDTECH

## 13. Apple A12 with dual big and quad LITTLE cores (9)

Full random latency of A12 caches vs. A11 caches (log scale) [64]

![](bbc8eeb04f24c460b4f58a8f5bd63076_img.jpg)

Line graph showing Full random latency (in KB) versus Test Depth (in KB) on a logarithmic scale for A12 and A11 caches.

Legend:

- A12 Big 2500 MHz
- A12 Little 1587 MHz
- A11 Big 2380 MHz
- A11 Little 1587 MHz
- A11 Little
- A12 Little
- A11 Big
- A12 Big

Approximate Latency Data Points:

| Cache/Configuration | Latency (KB) |
|---------------------|--------------|
| A12 Big 2500 MHz    | 2656         |
| A12 Little 1587 MHz | 5632         |
| A11 Big 2380 MHz    | 10880        |
| A11 Little 1587 MHz | 16256        |

ANANDTECH

## 13. Apple A12 with dual big and quad LITTLE cores (10)

#### b) Improved Neural Engine

As long as the Neural Engine of the A11 is a dual-core design with up to 600 billion operation per sec., the advanced Neural Engine of the A12 is an eight-core design with up to 5 trillion operations per sec.

## 13. Apple A12 with dual big and quad LITTLE cores (11)

#### The Core ML machine learning framework of Apple [66]

- It is used on Apple's devices (macOS, iOS, watchOS, and tvOS) to convert trained ML models, created with third-party ML tools, like XGBoost, Keras, LibSVM, scikit-learn or Facebook's Caffe and Caffe2, to the Core ML model format and let perform fast prediction or inference on the Apple device.
- Apple introduced Core ML in 06/2017.
- In 12/2017 Google released a tool that converts AI models produced using TensorFlow Lite into a file type compatible with Apple's Core ML.

## 13. Apple A12 with dual big and quad LITTLE cores (12)

Programming frameworks used to create ML models [67]

![](11507ee926131d3a2a57f05ba47a2770_img.jpg)

TensorFlow  
Keras  
Chainer  
Microsoft  
CNTK  
Marvin  
neon  
tiny-dnn  
Caffe  
USI/SUPS/ID SIA  
DL4J  
CoreML  
Torch  
Paddle  
BigDL APACHE Spark  
Caffe2  
dy/net  
ONNX  
PYTORCH  
theano  
mxnet

## 13. Apple A12 with dual big and quad LITTLE cores (13)

### Remarks

- Neon: Intel (originally from Nervana Systems, Python based), released: 05/2015
- TensorFlow: Google, released 11/2015
- Caffe: Facebook, originally developed at U. of California, Berkeley, release vo: 12/2013
- Caffe2: Facebook, 04/2017
- Caffe2 Go: Facebook, 10/2017
- MXNet (originated at the Carnegie Mellon U. and U. of Washington.  
  It is now developed in cooperation by multiple universities and companies, including Amazon, Baidu, Intel, Microsoft and Nvidia.  
  Supports building and training models in Python, R, Scala, Julia, and C++).

## 13. Apple A12 with dual big and quad LITTLE cores (14)

#### c) Improved GPU [64]

- The **3-core GPU of the A11** was Apple's first in-house design, it resembles to the previous Imagination design.
- **A12's GPU has 4 cores** and still looks similar to the Imagination design.

## 13. Apple A12 with dual big and quad LITTLE cores (15)

Contrasting the floor plans of the GPUs of A11 and A12 [64]

![Floor plan diagram of the A11 GPU Core, showing a 3-core design.](bc0c14231cc599a42b1d566960c73ca9_img.jpg)

Floor plan diagram of the A11 GPU Core, showing a 3-core design.

3-core  
design

![Floor plan diagram of the A12 GPU Core, showing a 4-core design.](96ce8caa36e741e52c970425a015935f_img.jpg)

Floor plan diagram of the A12 GPU Core, showing a 4-core design.

4-core  
design

## 13. Apple A12 with dual big and quad LITTLE cores (16)

Major innovation: Lossless memory compression of data transfers between the frame buffer and main memory

- **Frame buffer compression** is a **widely used** technique in GPUs **to reduce bandwidth and power consumption** while transferring data between the frame buffer and the main memory for years.
- It is utilized both in discrete GPUs of desktop processors and integrated GPUs of desktops or mobiles by vendors like Nvidia, AMD, Qualcomm or Imagination Technologies.
- In order to give a glimpse into this technique subsequently we briefly describe **ARM's AFBC (ARM Frame Buffer Compression)** method.

## 13. Apple A12 with dual big and quad LITTLE cores (17)

#### Principle of operation [68]

If a portion, portions or the whole image frame is detected as being relatively static (i.e. unchanged or changeless regarding to a threshold) for a period of time larger than a given threshold, AFBC will be applied.

## 13. Apple A12 with dual big and quad LITTLE cores (18)

First implementation of ARM's AFBC technique (2013) [69]

![](35c01f0273e1800cbbf6efa659126360_img.jpg)

Diagram illustrating the ARM AFBC (Adaptive Frame Buffer Compression) technique flow between three processing units:

- **Video Processor (Mali-V500):** Contains an AFBC Encode block.
- **GPU (Mali-T760):** Contains two blocks: AFBC Decode and AFBC Encode.
- **Display Processor (Mali-DP500):** Contains an AFBC Decode block.

The data flow is as follows:

1. The AFBC Encode block in the Video Processor outputs to the AFBC Decode block in the GPU.
2. The AFBC Decode block in the GPU outputs to the AFBC Encode block in the GPU.
3. The AFBC Encode block in the GPU outputs to the AFBC Decode block in the Display Processor.

Both the AFBC Decode block in the GPU and the AFBC Decode block in the Display Processor interact with the **Frame Buffer Objects**, which are shared resources.

## 13. Apple A12 with dual big and quad LITTLE cores (19)

Implementation of ARM's AFBC technique in the Mali T800 GPUs (2015) [70]

#### AFBC integration with media system

![](c3d8104dc13f901e55235041c000a837_img.jpg)

Diagram illustrating AFBC integration with the media system, showing the flow between Video Processor, GPU, and Display Processor, utilizing Mali-V550, Mali-T880, and Mali-DP550 components.

The components are:

- Video Processor (Mali-V550)
- GPU (Mali-T880)
- Display Processor (Mali-DP550)

AFBC operations are performed within these components:

- Mali-V550: AFBC Encode
- Mali-T880: AFBC Decode, AFBC Encode
- Mali-DP550: AFBC Decode

Data flow is shown by arrows:

- AFBC Encode (Mali-V550) feeds into AFBC Decode (Mali-T880).
- AFBC Decode (Mali-T880) feeds into AFBC Encode (Mali-T880).
- AFBC Encode (Mali-T880) feeds into AFBC Decode (Mali-DP550).
- AFBC Decode (Mali-T880) and AFBC Decode (Mali-DP550) interact with Frame Buffer Objects.

The ARM logo is visible in the bottom right corner.

## 13. Apple A12 with dual big and quad LITTLE cores (20)

Bandwidth reduction by AFBC while decoding a 4K H.264 video stream [69]

![](19bac22169d425eceeb7d3a496efdc77_img.jpg)

Graph showing Bandwidth (MB/pts) versus Frame number (0 to 2500) for three scenarios: No AFBC (Blue), AFBC internal reference frame compression only (Green), and AFBC compression used for the output frame as well (Red). The graph illustrates significant bandwidth reduction achieved by AFBC, especially in the output frame compression scenario, where bandwidth drops from approximately 1200 MB/pts to 100 MB/pts.

No AFBC

AFBC is used for internal reference frame compression only

AFBC compression is used for the output frame as well

## 13. Apple A12 with dual big and quad LITTLE cores (21)

System bandwidth reduction achieved by ARM's AFBC technique [70]

![](da045bf643ae60761acebc6bd5a8a13a_img.jpg)

System bandwidth reduction with AFBC

| Workload        | Reduction |
|-----------------|-----------|
| User Interface  | 50%       |
| Video           | 60%       |
| High-End Gaming | 46%       |
| Angry Birds     | 33%       |

## 13. Apple A12 with dual big and quad LITTLE cores (22)

### Remarks

ARM enhanced their AFBC to **AFBC 1.2** by introducing some optimizations in **2016** (first implemented in the Mali G51 GPU).

Apple introduced **frame buffer compression** relatively late, in **2018** along with the **A12** processor.

## 13. Apple A12 with dual big and quad LITTLE cores (23)

Load ramping (tracking frequency over time in a workload from idle to full performance in the A12 [64])

![](1eba201f682d15a30b207c0d68cfb6d5_img.jpg)

Apple A12 Frequency Ramp

Frequency of resident core (MHz)

Time (ms)

Vortex core

Tempest core

ANANDTECH

A12 / iOS12

## 13. Apple A12 with dual big and quad LITTLE cores (24)

#### SPEC2006 energy efficiency estimate [64]

![](6a0edaeb8af1f2308513a8f98ce9aaa0_img.jpg)

Average Power (W), Energy Usage (Joules) --- Performance (SPECspeed)

Chart series order in same order as legend order

| Processor | Apple A12 Vortex | Apple A12 Tempest | Apple A11 Monsoon | Exynos 9810 / 2704 MHz | Exynos 9810 / 2314 MHz | Exynos 8895 | Exynos 8895 | Exynos 835 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 | Exynos 8895 | Exynos 835 |
|-----------|------------------|-------------------|-------------------|------------------------|------------------------|-------------|-------------|------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|
|-----------|------------------|-------------------|-------------------|------------------------|------------------------|-------------|-------------|------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|-------------|------------|

## 13. Apple A12 with dual big and quad LITTLE cores (25)

-Single-core GeekBench 4 scores of select processors [71]

![](0d89e7c97e2ededa96322ffc8b59c0d5_img.jpg)

| Huawei Mate 20 Pro    | Kirin 980        | 3333    |
|-----------------------|------------------|---------|
| Apple iPhone XS Max   | A12              | 4821    |
| Apple iPhone X        | A12              | 4244    |
| Samsung Galaxy Note 9 | Exynos 9810 (M3) | 3612    |
| Google Pixel 3 XL     | Snapdragon 845   | 2260    |
| LG V40 ThinQ          | Snapdragon 845   | 2007    |
| Sony Xperia XZ3       | Snapdragon 845   | 2385    |
| OnePlus 6             | Snapdragon 845   | 2413.66 |

Note the outstanding single core performance of the A12.

## 13. Apple A12 with dual big and quad LITTLE cores (26)

Multi-core GeekBench 4 scores of select processors [71]

![](4c4a5bb88d303bdd784fcae1ddb08539_img.jpg)

| Huawei Mate 20 Pro    | Kirin 980 (4xA76+4xA55)             | 9807  |
|-----------------------|-------------------------------------|-------|
| Apple iPhone XS Max   | A12 (2xVortex+4xTempest)            | 11299 |
| Apple iPhone X        | A12 ((2xVortex+4xTempest)           | 10401 |
| Samsung Galaxy Note 9 | Exynos 9810 (4xM3+4xA55)            | 8927  |
| Google Pixel 3 XL     | Samsung Snapdragon 845 (8xKryo 385) | 7623  |
| LG V40 ThinQ          | Snapdragon 845 (8xKryo 385)         | 8310  |
| Sony Xperia XZ3       | Snapdragon 845 (8xKryo 385)         | 8577  |
| OnePlus 6             | Snapdragon 845 (8xKryo 385)         | 8929  |

Note again the outstanding multi-core performance of the dual-core A12 processors vs. processors with 4 big cores (the Snapdragon 845 has 4 high-performance Kryo 385 cores running at up to 2.8 GHz and 4 efficient Kryo 385 cores running at up to 1.8 GHz).

14. Apple A12X with quad big and quad LITTLE cores

## 14. Apple A12X with quad big and quad LITTLE cores (1)

## 14. Apple A12X with quad big and quad LITTLE cores [72]

- Released in 10/2018 in the 11" iPad Pro 11" and the 12.9" iPad Pro.
- These tablet models are also called the 3. generation iPad Pro models.
- The A12X is manufactured by 7 nm technology by TSMC as a PoP package with up to 6 GB LPDDR4x memory.
- Transistor count: 10 billion.
- The A12 provides about 30 % more single core performance and about 90 % more multi-core performance compared to the A10X, as GeekBench 4 data presented subsequently, show.

## 14. Apple A12X with quad big and quad LITTLE cores (2)

### Main features of the A12X Bionic SoC

| Appl. proc. S6 | Model no.      | Image                        | Node         | Die size             | CPU                                           | CPU ISA    | CPU cache (big core)                                    | GPU                                                                  | Memory (Up to)     | Intro.  | Utilizing devices                                 |
|----------------|----------------|------------------------------|--------------|----------------------|-----------------------------------------------|------------|---------------------------------------------------------|----------------------------------------------------------------------|--------------------|---------|---------------------------------------------------|
| A10 (Fusion)   | APL1W24        | <img alt="A10 chip image"/>  | 16 nm FinFET | 125 mm <sup>2</sup>  | 2xHurricane (2.34 GHz) + 2x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 3 MB<br>LS: 4 MB        | PowerVR GT7600 Plus (6C)<br>@ >650 MHz<br>(>250 GFLOPS) (redesigned) | 2 GB/3 GB LPDDR4x  | 9/2016  | iPhone 7<br>iPhone 7 Plus                         |
| A10X (Fusion)  | APL1071 (TSMC) | <img alt="A10X chip image"/> | 10 nm FinFET | 96.4 mm <sup>2</sup> | 3xHurricane (2.38 GHz) + 3x Zephyr (1.1 GHz?) | ARM v8-A   | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: none        | PowerVR GT7600 Plus (12C)                                            | 3 GB/4 GB LPDDR4x  | 6/2017  | iPad Pro 10.5"<br>iPad Pro 12.9"<br>Apple TV 4K   |
| A11 Bionic     | APL1W72 (TSMC) | <img alt="A11 chip image"/>  | 10 nm FinFET | 88 mm <sup>2</sup>   | 2x Monsoon (2.38 GHz) + 4x Mistral (1.69 GHz) | ARM V8.2-A | L1i: 64 KB<br>L1d: 64 KB<br>L2: 8 MB<br>LS: 4 MB        | Apple Custom GPU (3C)                                                | 2 GB/3 GB? LPDDR4x | 9/2017  | iPhone 8<br>iPhone 8 Plus<br>iPhone X             |
| A12 Bionic     | APL1W82 (TSMC) | <img alt="A12 chip image"/>  | 7 nm FinFET  | 83 mm <sup>2</sup>   | 2x Vortex (2.50 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (4C)                                                | 3 GB/4 GB LPDDR4X  | 9/2018  | iPhone XS 5.8"<br>iPhone XS Max<br>iPhone XR 6.1" |
| A12X Bionic    | APL1083 (TSMC) | <img alt="A12X chip image"/> | 7 nm FinFET  | 122 mm <sup>2</sup>  | 4x Vortex (2.48 GHz) + 4x Tempest (1.59 GHz)  | ARM V8.3-A | L1i: 128 KB<br>L1d: 128 KB<br>L2: 6 MB/core<br>LS: 8 MB | Apple Custom GPU (7C)                                                | 6 GB LPDDR4X       | 10/2018 | iPad Pro 11"<br>iPad Pro 12.9"                    |

LS: System cache, it services the entire SoC

## 14. Apple A12X with quad big and quad LITTLE cores (3)

### Main enhancements of the A12X versus the A12 [72]

- The A12X has a **7-core GPU vs. 4 cores** implemented in the A12.

This graphics performance is claimed to be equivalent to that of the Xbox One S.

- In the A12X the new task scheduler (called performance controller) allows **all CPU cores to run simultaneously (inclusive core allocation)** rather than the big and little cores exclusively.

This new performance controller is used also along with the A12.

## 14. Apple A12X with quad big and quad LITTLE cores (4)

### Contrasting GeekBench 4 scores of Intel processor-based MacBook DTs with A12X-based iPad Pro tablets -1

- Recent MacBooks are based on Intel's high performance i9 or i7 processors, like the 15" MacBook Pro on the i9-8950HK processor.
- Even so, the performance of Apple's in-house developed A12X, used in the iPad Pro tablets, approaches more and more the performance of Intel's advanced DT processors, used in Apple's MacBooks, as indicated in the next Figures.

## 14. Apple A12X with quad big and quad LITTLE cores (5)

#### GeekBench 4 Single-core scores for MacBook Pro (15") DTs [73]

| System                                                                          |      | Geekbench 4 Single-Core Score |
|---------------------------------------------------------------------------------|------|-------------------------------|
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i9-8950HK (6 cores, up to 4.8 GHz) | 5317 |                               |
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i7-8850H (6 cores, up to 4.3 GHz)  | 4991 |                               |
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i7-8750H (6 cores, up to 4.1 GHz)  | 4927 |                               |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7920HQ (4 cores, up to 4.1 GHz) | 4625 |                               |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7820HQ (4 cores, up to 3.9 GHz) | 4479 |                               |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7700HQ (4 cores, up to 3.8 GHz) | 4343 |                               |

Source: Geekbench 4 <http://www.geekbench.com/>

## 14. Apple A12X with quad big and quad LITTLE cores (6)

GeekBench 4 Single-core scores for iPad Pro tablets and iPhone mobiles [74]

| Device                                                             | Score |
|--------------------------------------------------------------------|-------|
| iPad Pro (11-inch)<br>Apple A12X Bionic @ 2.5 GHz                  | 5005  |
| iPad Pro (12.9-inch 3rd Generation)<br>Apple A12X Bionic @ 2.5 GHz | 5005  |
| iPhone XS Max<br>Apple A12 Bionic @ 2.5 GHz                        | 4797  |
| iPhone XS<br>Apple A12 Bionic @ 2.5 GHz                            | 4796  |
| iPhone XR<br>Apple A12 Bionic @ 2.5 GHz                            | 4795  |
| iPhone 8<br>Apple A11 Bionic @ 2.4 GHz                             | 4224  |
| iPhone 8 Plus<br>Apple A11 Bionic @ 2.4 GHz                        | 4222  |
| iPhone X<br>Apple A11 Bionic @ 2.4 GHz                             | 4213  |
| iPad Pro (10.5-inch)<br>Apple A10X Fusion @ 2.3 GHz                | 3915  |
| iPad Pro (12.9-inch 2nd Generation)<br>Apple A10X Fusion @ 2.3 GHz | 3911  |

## 14. Apple A12X with quad big and quad LITTLE cores (7)

#### GeekBench 4 Multi-core scores for MacBook Pro (15") DTs [73]

| System                                                                          | Geekbench 4 Multi-Core Score |
|---------------------------------------------------------------------------------|------------------------------|
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i9-8950HK (6 cores, up to 4.8 GHz) | 22439                        |
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i7-8850H (6 cores, up to 4.3 GHz)  | 21190                        |
| MacBook Pro (15-inch Mid 2018)<br>Intel Core i7-8750H (6 cores, up to 4.1 GHz)  | 21042                        |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7920HQ (4 cores, up to 4.1 GHz) | 15548                        |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7820HQ (4 cores, up to 3.9 GHz) | 15251                        |
| MacBook Pro (15-inch Mid 2017)<br>Intel Core i7-7700HQ (4 cores, up to 3.8 GHz) | 14375                        |

Source: Geekbench 4 <http://www.geekbench.com/>

## 14. Apple A12X with quad big and quad LITTLE cores (8)

GeekBench 4 Multi-core scores for iPad Pro tablets and iPhone mobiles [74]

| Device                                                             | Score |
|--------------------------------------------------------------------|-------|
| iPad Pro (12.9-inch 3rd Generation)<br>Apple A12X Bionic @ 2.5 GHz | 17920 |
| iPad Pro (11-inch)<br>Apple A12X Bionic @ 2.5 GHz                  | 17879 |
| iPhone XS<br>Apple A12 Bionic @ 2.5 GHz                            | 11258 |
| iPhone XR<br>Apple A12 Bionic @ 2.5 GHz                            | 11208 |
| iPhone XS Max<br>Apple A12 Bionic @ 2.5 GHz                        | 11203 |
| iPhone 8 Plus<br>Apple A11 Bionic @ 2.4 GHz                        | 10185 |
| iPhone X<br>Apple A11 Bionic @ 2.4 GHz                             | 10145 |
| iPhone 8<br>Apple A11 Bionic @ 2.4 GHz                             | 10140 |
| iPad Pro (10.5-inch)<br>Apple A10X Fusion @ 2.3 GHz                | 9338  |
| iPad Pro (12.9-inch 2nd Generation)<br>Apple A10X Fusion @ 2.3 GHz | 9321  |

## 14. Apple A12X with quad big and quad LITTLE cores (9)

Geekbench 4 scores of Intel's 15 W i7-xxxxU processors [75]

| Model    | CPU cores | Launched | GB 4 SC max | GB 4 MC max | Family      | Techn. |
|----------|-----------|----------|-------------|-------------|-------------|--------|
| i7-4500U | 2C        | 6/2013   | 3854        | 6854        | Haswell     | 22 nm  |
| i7-4600U | 2C        | 9/2013   | 4202        | 7592        | Haswell     | 22 nm  |
| i7-5600U | 2C        | 1/2015   | 4217        | 8018        | Broadwell   | 14 nm  |
| i7-6600U | 2C        | 9/2015   | 4775        | 9010        | Skylake     | 14 nm  |
| i7-7560U | 2C        | 8/2016   | 5000        | 10182       | Kaby Lake   | 14 nm  |
| i7-7660U | 2C        | 1/2017   | 5128        | 10389       | Kaby Lake   | 14 nm  |
| i7-8565U | 4C        | 8/2018   | 5576        | 17813       | Coffee Lake | 14 nm  |

## 14. Apple A12X with quad big and quad LITTLE cores (10)

### Geekbench 4 scores of Apple's A series processors [74]

| Model | CPU cores | Launched | GB 4 SC max | GB 4 MC max | Techn.   |
|-------|-----------|----------|-------------|-------------|----------|
| A8    | 2C        | 9/2014   | 1663        | 2855        | 20 nm    |
| A8X   | 3C        | 10/2014  | 1798        | 4214        | 20 nm    |
| A9    | 2C        | 9/2015   | 2524        | 4391        | 14/16 nm |
| A9X   | 2C        | 11/2015  | 3057        | 5114        | 16 nm    |
| A10   | 2+2C      | 9/2016   | 3480        | 5928        | 16 nm    |
| A10X  | 3+3C      | 6/2017   | 3915        | 9339        | 10 nm    |
| A11   | 2+4C      | 9/2017   | 4224        | 10185       | 10 nm    |
| A12   | 2+4C      | 9/2018   | 4797        | 11260       | 7 nm     |
| A12X  | 4+4C      | 10/2018  | 5006        | 17925       | 7 nm     |

## 14. Apple A12X with quad big and quad LITTLE cores (11)

#### Geekbench 4 scores of Qualcomm's Snapdragon processors [76]

| Model | CPU cores | Launched | GB 4 SC max | GB 4 MC max | Techn. |
|-------|-----------|----------|-------------|-------------|--------|
| 808   | 2+4C      | Q3/2014  | 1152        | 2813        | 20 nm  |
| 810   | 4+4C      | Q3/2014  | 1351        | 3446        | 20 nm  |
| 820   | 4+4C      | Q4/2015  | 1702        | 3955        | 14 nm  |
| 821   | 4+4C      | Q3/2016  | 1880        | 4430        | 14 nm  |
| 835   | 4+4C      | Q2/2017  | 1947        | 6624        | 10 nm  |
| 845   | 4+4C      | Q1/2018  | 2415        | 8689        | 10 nm  |
| 850   | 4+4C      | Q3/2018  |             |             | 10 nm  |
| 855   | 1+3+4C    | Q1/2019  |             |             | 7 nm   |

## 14. Apple A12X with quad big and quad LITTLE cores (12)

Geekbench 4 SC scores of Intel's, Apple's and Qualcomm's processors

![](ef80a724391c296fb66b77244ffb0f9f_img.jpg)

Scatter plot showing Geekbench 4 Single Core (SC) scores over time (Year) for various processors. The Y-axis ranges from 500 to 6000, and the X-axis ranges from 2013 to 2018.

Legend:

- Intel (Blue line): I7-4500U 2C, I7-4600U, I7-5600U, I7-6600U, I7-7560U, I7-7660U 2C, I7-8565U 4C.
- Apple (Red line): A8X 3C, A9X 2C, A10X 3+3C, A12X 4+4C.
- Qualcomm (Black line): 810, 820, 821, 835, 845, 4C+4C.

## 14. Apple A12X with quad big and quad LITTLE cores (13)

Geekbench 4 MC scores of Intel's, Apple's and Qualcomm's processors

![](da29bcd4ce1277e82e278506d03fec24_img.jpg)

Line chart showing Geekbench 4 Multi-Core (MC) scores for Intel, Apple, and Qualcomm processors from 2013 to 2018.

The Y-axis represents Geekbench 4 MC scores, ranging from 2000 to 20000. The X-axis represents the Year.

Legend:

- Intel (Blue dotted line): I7-4500U 2C, I7-4600U, I7-5600U, I7-6600U, I7-7560U, I7-7660U 2C, I7-8565U 4C.
- Apple (Red dotted line): A8X 3C, A9X 2C, A10X 3+3C, A12X 4+4C.
- Qualcomm (Black dotted line): 810, 820, 835, 845.

## 14. Apple A12X with quad big and quad LITTLE cores (14)

### Contrasting GeekBench 4 scores of Intel processor-based MacBook DTs with A12X-based iPad Pro tablets -2

- A comparison of the A10X and A12X performance scores indicates a massive evolution of the GeekBench 4 scores of Apple's Axxx processors.

This fast improvement in performance figures lets suggest that **Apple is expected to replace soon Intel's processors by in-house developed Axxx processors in their MacBooks.**

## 15. References

## 15. References (1)

[1]: Goto H., The migration of semiconductor process that was hidden in the back of the iPad mini and fourth generation iPad announcement, PC Watch, Oct. 24 2012,  
[http://pc.watch.impress.co.jp/docs/column/kaigai/20121024\\_568188.html](http://pc.watch.impress.co.jp/docs/column/kaigai/20121024_568188.html)

[2]: Goto H., ARM Cortex – A Family Architecture, 2010,  
<http://pc.watch.impress.co.jp/video/pcw/docs/423/409/p1.pdf>

[3]: Wikipedia, iPhone (1st generation),  
[http://en.wikipedia.org/wiki/IPhone\\_%281st\\_generation%29](http://en.wikipedia.org/wiki/IPhone_%281st_generation%29)

[4]: Microsystems Integration, Aug. 28-Sept. 2 2014,  
[http://www.colorado.edu/engineering/MCEN/MCEN5166/Lectures/MI\\_2\\_iPhone2\\_1st2ndPKG\\_2014\\_Aug28.pdf](http://www.colorado.edu/engineering/MCEN/MCEN5166/Lectures/MI_2_iPhone2_1st2ndPKG_2014_Aug28.pdf)

[5]: Ritchie R., Evolution of iPad: Specs over history, iMore, Oct. 22 2013,  
<http://www.imore.com/evolution-ipad>

[6]: Betters E., Apple iPad showdown: Which tablet is best for you?, Pocket-lint, Oct. 16 2014,  
<http://www.pocket-lint.com/news/131406-apple-ipad-showdown-which-tablet-is-best-for-you>

[7]: Anthony S., Apple's A8 SoC analyzed: The iPhone 6 chip is a 2-billion-transistor 20nm monster  
ExtremeTech, Sept. 10 2014, <http://www.extremetech.com/computing/189787-apples-a8-soc-analyzed-the-iphone-6-chip-is-a-2-billion-transistor-20nm-monster>

[8]: The Five Pitfalls of 4G Baseband SOC Design, Tensilica White Paper, Jan. 19 2010,  
[http://iteportal.com/Files/MarketSpace/Download/187\\_DownloadTheFivePitfallsWhitePaper.pdf?PHPSESSID=3da81bf2f67dee99ff2117f3a8376439](http://iteportal.com/Files/MarketSpace/Download/187_DownloadTheFivePitfallsWhitePaper.pdf?PHPSESSID=3da81bf2f67dee99ff2117f3a8376439)

## 15. References (2)

[9]: Gianesello F., Analog and RF Requirements for Advanced CMOS Nodes: The SOI Perspective, Lund Circuit Design Workshop, Oct. 3 2012,  
<http://cdworkshop.eit.lth.se/fileadmin/cdworkshop/2012/STM-Gianesello.pdf>

[10]: James D., Inside Today's Systems & Chips: A Survey of the Past Year, Chipworks, 2013,  
[http://theconfab.com/wp-content/uploads/2014/dick\\_james\\_confab14.pdf](http://theconfab.com/wp-content/uploads/2014/dick_james_confab14.pdf)

[11]: Apple iPhone megateszt - a búnbeesés almája, Mobilarena, July 23 2007,  
[http://mobilarena.hu/teszt/apple\\_iphone\\_megateszt\\_a\\_bunbeeses\\_almaja/bevezeto.html](http://mobilarena.hu/teszt/apple_iphone_megateszt_a_bunbeeses_almaja/bevezeto.html)

[12]: Apple A4 Teardown. iFixit,  
<https://www.ifixit.com/Teardown/Apple+A4+Teardown/2204>

[13]: Dreiza M., Kim J.S., Smith L., Campos D., Saugier E. Jarvinen P., Joint Project for Mechanical Qualification of Next Generation High Density Package-on-Package (PoP) with Through Mold Via Technology, EMPC2009 – 17th European Microelectronics & Packaging Conference, June 16 2009, Rimini, Italy

[14]: ARM1176 Processor, ARM Ltd.,  
<http://www.arm.com/products/processors/classic/arm11/arm1176.php>

[15]: Apple iPhone 3GS - agyra gyúrt, Mobilarena, July 22 2009,  
[http://mobilarena.hu/teszt/apple\\_iphone\\_3gs\\_agyra\\_gyurt/hardveres\\_valtozasok.html](http://mobilarena.hu/teszt/apple_iphone_3gs_agyra_gyurt/hardveres_valtozasok.html)

[16]: Mannion P., Under the Hood : Inside the Apple iPhone, EE Times, July 1 2007,  
[http://www.eetimes.com/document.asp?doc\\_id=1281295](http://www.eetimes.com/document.asp?doc_id=1281295)

## 15. References (3)

[17]: The History of Apple SoCs, MacRumors, Aug. 31 2014,  
http://forums.macrumors.com/showthread.php?t=1770411

[18]: Morrissey S., iOS Forensic Analysis for iPhone, iPad and iPod touch, APress, 2010,  
http://sensperiodit.files.wordpress.com/2011/04/ios-forensic-analysis-for-iphone-ipad-and-ipod-touch.pdf

[19]: Gwennap L., How Apple Designed Own CPU For A6, The Linley Group, Sept. 15 2012,  
http://www.linleygroup.com/newsletters/newsletter\_detail.php?num=4881

[20]: Shimpi A.L, Klug B., Gowri V., The iPhone 5 Review, AnandTech, Oct. 16 2012,  
http://www.anandtech.com/print/6330/the-iphone-5-review

[21]: Riemenschneider F., Der Krieg um die Smartphones: Die ARM-Armada gegen Intel – eine Analyse, Presentation in „Konferenz für ARM-Systementwicklung“, July 9 2013, München

[22]: Devine R., Strava Run updates to use the M7 motion coprocessor in the iPhone 5s, iMore, Sept. 25 2013, http://www.imore.com/strava-run-updates-use-m7-motion-coprocessor-iphone-5s

[23]: Slivka E., Inside Apple's A7 Chip, M7 Motion Coprocessor, and More from the iPhone 5s MacRumors, Sept. 24 2013, http://www.macrumors.com/2013/09/24/inside-apples-a7-chip-m7-motion-coprocessor-and-more-from-the-iphone-5s/

[24]: Anthony S., Apple's A7 Cyclone CPU detailed: A desktop class chip that has more in common with Haswell than Krait, ExtremeTech, March 31 2014,  
http://www.extremetech.com/computing/179473-apples-a7-cyclone-cpu-detailed-a-desktop-class-chip-that-has-more-in-common-with-haswell-than-krait

## 15. References (4)

[25]: Shimpi A.L., Apple's Cyclone Microarchitecture Detailed, AnandTech, March 31 2014, <http://www.anandtech.com/show/7910/apples-cyclone-microarchitecture-detailed>

[26]: Riemenschneider F., Apples »Cyclone«-CPU-Architektur enthüllt, Elektroniknet, March 31 2014, <http://www.elektroniknet.de/halbleiter/prozessoren/artikel/107338/>

[27]: Ho J., The Apple iPad Air 2 Review, AnandTech, Nov. 7 2014, <http://www.anandtech.com/print/8666/the-apple-ipad-air-2-review>

[28]: Wikipedia, Apple A8, [http://en.wikipedia.org/wiki/Apple\\_A8](http://en.wikipedia.org/wiki/Apple_A8)

[29]: Smith R., Chipworks Disassembles Apple's A8 SoC: GX6450, 4MB L3 Cache & More, AnandTech, Sept. 23 2014, <http://www.anandtech.com/show/8562/chipworks-a8>

[30]: Hessedahl A., Teardown Shows Apple's iPhone 6 Cost at Least \$200 to Build, Recode, Sept. 23 2014, <http://recode.net/2014/09/23/teardown-shows-apples-iphone-6-cost-at-least-200-to-build/>

[31]: iPhone 6 Plus Teardown, iFixit, <https://www.ifixit.com/Teardown/iPhone+6+Plus+Teardown/29206>

[32]: Smith R., Apple A8X's GPU - GXA6850, Even Better Than I Thought, AnandTech, Nov. 11 2014, <http://www.anandtech.com/show/8716/apple-a8xs-gpu-gxa6850-even-better-than-i-thought>

[33]: Hinum K., Apple A8X, Notebook Check, Oct. 17 2014, <http://www.notebookcheck.net/Apple-A8X-iPad-SoC.128403.0.html>

## 15. References (5)

[34]: Anthony S., The iPad Air 2, with a tri-core CPU, is almost as fast as a modern PC, ExtremeTech, Oct. 22 2014, <http://www.extremetech.com/computing/192628-the-ipad-air-2-with-a-tri-core-cpu-is-almost-as-fast-as-a-modern-pc>

[35]: Dilger D.E., Apple's new A8X powered iPad Air 2 smokes new Android tablets, including Nvidia's Tegra K1 Shield Tablet [u], Apple Insider, Oct. 21 2014, <http://appleinsider.com/articles/14/10/21/apples-new-a8x-powered-ipad-air-2-smokes-new-android-tablets-including-nvidias-tegra-k1>

[36]: Goddard L., Texas Instruments admits defeat, moves focus away from smartphone processors, The Verge, Sept. 26 2012, <http://www.theverge.com/2012/9/26/3411212/texas-instruments-omap-smartphone-shift>

[37]: iPad Air 2 Teardown, iFixit, <https://www.ifixit.com/Teardown/iPad+Air+2+Teardown/30592>

[38]: Dilger D.E., Apple Inc. A8X iPad chip causing big problems for Intel, Qualcomm, Samsung and Nvidia, Apple Insider, Nov. 14 2014, <http://appleinsider.com/articles/14/11/15/apple-inc-a8x-ipad-chip-causing-big-problems-for-intel-qualcomm-samsung-and-nvidia>

[39]: Ho J., Chester B., Heinonen C., Smith R., The iPhone 6 Review, AnandTech, Sep. 30, 2014, <http://www.anandtech.com/show/8554/the-iphone-6-review>

[40]: Smith R. & Ho J., The Apple iPhone 6s and iPhone 6s Plus Review, AnandTech, Nov. 2, 2015, <http://www.anandtech.com/show/9686/the-apple-iphone-6s-and-iphone-6s-plus-review>

## 15. References (6)

[41]: Smith R., Correcting Apple's A9 SoC L3 Cache Size: A 4MB Victim Cache, Nov. 30 2015, <http://www.anandtech.com/show/9825/correcting-a9s-l3-cache>

[42]: Apple Introduces iPhone 6s & iPhone 6s Plus, Press info, Apple, Sept. 9, 2015, <http://www.apple.com/pr/library/2015/09/09Apple-Introduces-iPhone-6s-iPhone-6s-Plus.html>

[43]: Cunningham A., Apple's A9X has a 12-core GPU and is made by TSMC, arsTECHNICA, 11/30/2015, <http://arstechnica.com/apple/2015/11/apples-a9x-has-a-12-core-gpu-and-is-made-by-tsmc/>

[44]: Smith R., More on Apple's A9X SoC: 147mm2@TSMC, 12 GPU Cores, No L3 Cache, AnandTech, Nov. 30 2015, <http://www.anandtech.com/show/9824/more-on-apples-a9x-soc>

[45]: Apple iPhone 7 Teardown, chipworks, Sept. 15 2016, <http://www.chipworks.com/about-chipworks/overview/blog/apple-iphone-7-teardown>

[46]: iPad Pro, Wikipedia, [https://en.wikipedia.org/wiki/iPad\\_Pro](https://en.wikipedia.org/wiki/iPad_Pro)

[47]: Hanrahan P., Why are Graphics Systems so Fast? Stanford University PACT Keynote Sept. 14 2009, <http://www.graphics.stanford.edu/~hanrahan/talks/pact/why.pdf>

[48]: Zibreg C., New iPad due this fall may feature custom AI chip & Apple-designed graphics, iDB, Jan. 29 2018, <http://www.idownloadblog.com/2018/01/29/new-ipads-apple-designed-graphics/>

## 15. References (7)

[49]: Smith R., TechInsights Confirms Apple's A10X SoC Is TSMC 10nm FF; 96.4mm2 Die Size AnandTech, June 29 2017, <https://www.anandtech.com/show/11596/techinsights-confirms-apple-a10x-soc-10nm-tsmc>

[50]: The Linley Group: Apple Hurricane – the fastest ARMv8-A core of today, Oct. 26 2016, <http://www.startlr.com/the-linley-group-apple-hurricane-the-fastest-armv8-a-core-of-today>

[51]: Ho J., Chester B., The iPhone 7 and iPhone 7 Plus Review: Iterating on a Flagship, AnandTech, Oct. 10 2016, <https://www.anandtech.com/show/10685/the-iphone-7-and-iphone-7-plus-review>

[52]: Dilger D.E., Apple A10 iPhone 7 speeds past Samsung Galaxy S8, Google Pixel, LG G6 & BBK 3T (with 2x RAM), Apple Insider, April 17 2017, <http://appleinsider.com/articles/17/04/17/apple-a10-iphone-7-speeds-past-samsung-galaxy-s8-google-pixel-lg-g6-bbk-3t-with-2x-ram>

[53]: Compare Apple iPhone 7 vs Apple iPhone 8 256GB vs Apple iPhone 8 Plus vs Apple iPhone 8 Plus 256GB, Gadgets Now, <https://www.gadgetsnow.com/compare-mobile-phones/Apple-iPhone-7-vs-Apple-iPhone-8-256GB-vs-Apple-iPhone-8-Plus-vs-Apple-iPhone-8-Plus-256GB>

[54]: Kingsley-Hughes A., Inside Apple's new A11 Bionic processor, ZDNet, Sept. 12 2017, <http://www.zdnet.com/article/inside-apples-new-a11-bionic-processor/>

[55]: Apple iPhone 8 Plus Teardown, Tech Insights, <http://techinsights.com/about-techinsights/overview/blog/apple-iphone-8-teardown/>

[56]: Wikipedia, Apple A11, [https://en.wikipedia.org/wiki/Apple\\_A11#cite\\_note-bloomberg-14](https://en.wikipedia.org/wiki/Apple_A11#cite_note-bloomberg-14)

## 15. References (8)

[57]: About Threadgroup Sharing, Developer,  
https://developer.apple.com/documentation/metal/about\_gpu\_family\_4/about\_threadgroup\_sharing

[58]: iPhone X Benchmarks, Geekbench Browser,  
https://browser.geekbench.com/ios\_devices/52

[59]: Dilger D.E., Inside iPhone 8: Apple's A11 Bionic introduces 5 new custom silicon engines, Apple Insider, Sept. 23 2017, http://appleinsider.com/articles/17/09/23/inside-iphone-8-apples-a11-bionic-introduces-5-new-custom-silicon-engines

[60]: Humrick M., Apple Refreshes iPad Pro Lineup: A10X Fusion SoC for 10.5-inch, 12.9-inch Models, AnandTech, June 6 2017, https://www.anandtech.com/show/11518/apple-refreshes-ipad-pro-lineup-a10x-fusion-soc

[61]: Nguyen H., NVIDIA Definitely "Not Interested" In Building Smartphones SoCs, Ubergizmo, 06/04/2016,  
http://www.ubergizmo.com/2016/06/nvidia-not-interested-smartphones-soc/

[62]: Interpreting Geekbench 4 Scores,  
http://support.primatelabs.com/kb/geekbench/interpreting-geekbench-4-scores

[63]: Grosbach J. et al., What's New in LLVM, Apple Worldwide Developers Conference (WWDC18), Session 409, San Jose, CA, June 4-8,  
https://developer.apple.com/videos/play/wwdc2018/409/

[64]: Frumusanu A., The iPhone XS & XS Max Review: Unveiling the Silicon Secrets, AnandTech, Oct. 5, 2018,  
https://www.anandtech.com/show/13392/the-iphone-xs-xs-max-review-unveiling-the-silicon-secrets

[65]: A12 Bionic – Apple, <https://en.wikichip.org/wiki/apple/ax/a12>

[66]: Wiggers K., Apple's A12 Bionic chip runs Core ML apps up to 9 times faster, Venturebit, Sept. 12, 2018, <https://venturebeat.com/2018/09/12/apples-a12-bionic-chip-runs-core-ml-apps-up-to-9-times-faster/>

[67]: Peng, L., Mainstream deep learning open source frameworks from entry to proficiency, AI Academy, Nov. 16, 2018, <https://zhuankan.zhihu.com/p/50068781>

[68]: Croxford D. et al., Adaptive Frame Buffer Compression, US Patent 9,349,156 B2, ARM Ltd., May 24, 2016

[69]: Arm Frame Buffer Compression (AFBC), ARM Developer, <https://developer.arm.com/technologies/graphics-technologies/arm-frame-buffer-compression>

[70]: Bratt I., The ARM® Mali-T880 Mobile GPU, Hot Chips 27, Aug. 23, 2015, [https://www.hotchips.org/wp-content/uploads/hc\\_archives/hc27/HC27.25-Tuesday-Epub/HC27.25.50-GPU-Epub/HC27.25.531-Mali-T880-Bratt-ARM-2015\\_08\\_23.pdf](https://www.hotchips.org/wp-content/uploads/hc_archives/hc27/HC27.25-Tuesday-Epub/HC27.25.50-GPU-Epub/HC27.25.531-Mali-T880-Bratt-ARM-2015_08_23.pdf)

[71]: Gatlan S., Apple's A12 Bionic Destroys Huawei's Latest Kirin 980 Chip, Softpedia, Oct 18, 2018, [https://news.softpedia.com/news/huawei-s-hisilicon-kirin-980-is-a-lot-less-powerful-than-apple-s-a12-bionic-523311.shtml#sgal\\_1](https://news.softpedia.com/news/huawei-s-hisilicon-kirin-980-is-a-lot-less-powerful-than-apple-s-a12-bionic-523311.shtml#sgal_1)

[72]: Apple's Phil Schiller reveals iPad Pro A12X chip design process in interview, AppleInsider, Nov. 7, 2018, <https://forums.appleinsider.com/discussion/208160/apples-phil-schiller-reveals-ipad-pro-a12x-chip-design-process-in-interview>

[73]: Pohle J., MacBook Pro Performance (July 2018), Primate Labs, Jul 15, 2018,  
https://www.geekbench.com/blog/2018/07/macbook-pro-performance-july-2018/

[74]: iPhone, iPad, and iPod Benchmarks, Geekbench Browser, Dec. 25, 2018,  
https://browser.geekbench.com/ios-benchmarks

[75]: Geekbench 4 CPU Search, Geekbench Browser, visited: Dec. 30, 2018,  
https://browser.geekbench.com/v4/cpu/search

[76]: Android Benchmarks, Geekbench Browser, visited: Dec. 30, 2018,  
https://browser.geekbench.com/android-benchmarks