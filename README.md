![minerstat logo](https://cdn.rawgit.com/minerstat/minerstat-asic/master/docs/logo_full.svg)

# minerstat ASIC Hub (Non-SSH)

## What is this?
Monitoring and management software - ASIC Hub (Non-SSH) makes possible to monitor your ASICs without SSH connection established.

**Supported ASICs:**
* Bitmain's Antminer ASICs

Including the latest ones:
* [Antminer B7](https://minerstat.com/hardware/antminer-b7)
* [Antminer DR5](https://minerstat.com/hardware/antminer-dr5)
* [Antminer E3](https://minerstat.com/hardware/antminer-e3)
* [Antminer S15](https://minerstat.com/hardware/antminer-s15)
* [Antminer S17](https://minerstat.com/hardware/antminer-s17)
* [Antminer S17 Pro](https://minerstat.com/hardware/antminer-s17-pro)
* [Antminer T15](https://minerstat.com/hardware/antminer-t15)
* [Antminer T17](https://minerstat.com/hardware/antminer-t17)
* [Antminer Z9](https://minerstat.com/hardware/antminer-z9)
* [Antminer Z11](https://minerstat.com/hardware/antminer-z11)

Work in progress for more ASIC support.

## Features

* Sync with minerstat dashboard
Hashrate Data, Temps Data, Chains Data

* Full Control
Reboot, Restart, Full Config Edit

* Config Edit
On first sync hub upload your actual cgminer, bmminer config to minerstat Config Editor:
You are able to edit **pool, frequency, voltage** from **online** (in bulk too)!

* Profit Switch
Configure and mine the always the most profitable coin with your ASIC! 
Between coin changes with Non-SSH Hub no machine reboot needed.

## Installation on Linux

### Install dependencies

``` sh
$ sudo apt-get update
$ sudo apt-get install wget curl jq screen
```

### Download and Setup

Login to your server over SSH OR Open Terminal and execute the following command(s):

``` sh
$ wget https://github.com/minerstat/minerstat-asic-hub-non-ssh/releases/download/latest/hub-linux && chmod 777 hub-linux
$ sudo cp hub-linux /usr/bin
$ hub-linux --help
```

You need to see this response:

```
================ © minerstat OÜ in 2019 ================
-t|--token   : Website Login Key
-g|--group   : Group/Location
-l|--limit   : How many request allowed at once
-d|--debug   : Show Detailed Debug Output
-v|--version : Print current version, build number
-h|--help    : Print this help menu
```

You can start one or multiple instances to monitor one or more groups at once.

``` sh
$ hub-linux --token YOURACCESSKEY --group GROUPTOMONITOR --limit 32 --debug 0
```

If you want to start monitoring in the background:
``` sh
$ screen -AmdS mshub-1 hub-linux --token YOURACCESSKEY --group GROUPTOMONITOR --limit 32 --debug 0
```

### Importance of ulimit

#### What is ulimit?
Ulimit is the number of open file descriptors per process. Sometimes, you will get the error message like “too many files open “. This happens because you have reached the limit of the number opened files, so you need to increase the value of ulimit parameter.

#### How to increase ?

``` sh
$ ulimit -n 4096
$ sudo nano /etc/security/limits.conf
```

Edit this file to the following:

``` sh
*   soft    nofile    4096
*   hard    nofile    4096
```

CTRL + O -> SAVE

CTRL + C -> CLOSE

### How to start Asic Hub with the system?

You'll need to edit crontabs. Here is an example:

``` sh
$ crontab -e
```

Edit the file with your start line e.g:

``` sh
@reboot screen -AdmS mshub-1 hub-linux --token YOURACCESSKEY --group GROUPTOMONITOR --limit 32 --debug 0
```

CTRL + O -> SAVE

CTRL + C -> CLOSE

## Installation on macOS

### Install dependencies

``` sh
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew install wget curl jq
```

### Download and Setup

Login to your server over SSH OR Open Terminal and execute the following command(s):

``` sh
$ wget https://github.com/minerstat/minerstat-asic-hub-non-ssh/releases/download/latest/hub-mac && chmod 777 hub-mac
$ sudo cp hub-mac /usr/local/bin
$ hub-mac --help
```

You need to see this response:

```
================ © minerstat OÜ in 2019 ================
-t|--token   : Website Login Key
-g|--group   : Group/Location
-l|--limit   : How many request allowed at once
-d|--debug   : Show Detailed Debug Output
-v|--version : Print current version, build number
-h|--help    : Print this help menu
```

You can start one or multiple instances to monitor one or more groups at once.

``` sh
$ hub-mac --token YOURACCESSKEY --group GROUPTOMONITOR --limit 32 --debug 0
```

### Importance of ulimit

#### What is ulimit?
Ulimit is the number of open file descriptors per process. Sometimes, you will get the error message like “too many files open “. This happens because you have reached the limit of the number opened files, so you need to increase the value of ulimit parameter.

#### How to increase ?

``` sh
$ ulimit -n 4096
```

##

***© minerstat OÜ*** in 2019


***Contact:*** app [ @ ] minerstat.com


***Mail:*** Sepapaja tn 6, Lasnamäe district, Tallinn city, Harju county, 15551, Estonia

##
