# Machine Vision Tank Monitor using Blues Wireless and running on balena

This is a demonstration about how to balenify a project. In this case the `Machine Vision Tank Monitoring` project made by Brandon Satrom at Blues Wireless.

It uses Edge ML and Cellular IoT Project for monitoring pressure on a pool filter tank. The [full project writeup is on Hackster.io](https://www.hackster.io/brandonsatrom/monitor-the-analog-world-with-tinyml-fd59c4).

![Photo of an analog tank gauge with a ML model superimposed on top](assets/TankEdited.png)

This repository contains the complete Python source for a project that runs an [Edge Impulse](https://edgeimpulse.com)-created ML model and sends inference results to the Blues Wireless [Notecard](https://blues.io/products).

A public version of the Edge Impulse project, with downloadable model files is [here](https://studio.edgeimpulse.com/public/29302/latest).

## Tutorial

### Hardware

* Raspberry Pi 4
* [Notecarrier Pi Hat](https://shop.blues.io/products/carr-pi)
* [LTE-M NoteCard Global](https://shop.blues.io/products/note-nbgl-500) or feel free to select a Notecard by region.
* SD card
* Power supply and (optionally) ethernet cable

### Software

* A balenaCloud account ([sign up here](https://dashboard.balena-cloud.com/))
* [NoteHub](https://notehub.io/)
* [balenaEtcher](https://balena.io/etcher)


## Deploy

### One-click deploy via [Balena Deploy](https://www.balena.io/docs/learn/deploy/deploy-with-balena-button/)

You can deploy this project to a new balenaCloud application in one click using the button below:

[![](https://balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/mpous/ml-pool-tank)

Or, you can create an application in your balenaCloud dashboard and balena push this code to it the traditional way.

### In-control deploy via [balena CLI](https://www.balena.io/docs/reference/balena-cli/)

If you are a balena CLI expert, feel free to use balena CLI. This option lets you configure in detail some options, like adding new services to your deploy or configure de DNS Server to use.

- Sign up on [balena.io](https://dashboard.balena.io/signup)
- Create a new fleet on balenaCloud.
- Add a new device and download the image of the BalenaOS it creates.
- Burn the USB drive, connect it to the x86 device and boot it up (you might go to the BIOS to make the device to boot from the USB on the first time. Please read more here).

While the device boots (it will eventually show up in the Balena dashboard) we will prepare de services:

```
cd ~/workspace
git clone https://github.com/mpous/ml-pool-tank
cd ml-pool-tank
```

- Using [Balena CLI](https://www.balena.io/docs/reference/cli/), push the code with `balena push <fleet-name>`
- See the magic happening, your device is getting updated 🌟Over-The-Air🌟!


## Variables

### Device Variables

Variable Name | Default | Description
------------ | ------------- | -------------
NOTEHUB_PROJECT |  | the notehub project name (e.g. `com.acme.mpous:myawesomeproject`)
NOTEHUB_MODE | `continuous` | `continuous` or `periodic`



### Configuration Custom Variables

Variable Name | Value 
------------ | -------------
BALENA_HOST_CONFIG_gpu_mem_1024 | 448
BALENA_HOST_CONFIG_gpu_mem_512 | 256
BALENA_HOST_CONFIG_gpu_mem_256 | 192
RESIN_HOST_CONFIG_start_x | 1 


## Configure the device

`TBD`


## Attribution

- This is a balenification of the Brandon Satrom's [project](https://github.com/bsatrom/ml-pool-tank). Find here the [Hackster project](https://www.hackster.io/brandonsatrom/monitor-the-analog-world-with-tinyml-fd59c4).
- This is in part working thanks of the work of [TJ VanToll](https://github.com/tjvantoll/) Developer Advocate from Blues Wireless and [Marc Pous](https://github.com/mpous) from balena.io.
- This is based on the block [blues-notecard](https://github.com/tjvantoll/balena-notecard)
