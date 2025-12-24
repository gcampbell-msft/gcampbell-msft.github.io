---
layout: default
title: Smart Home & Custom Smart Garage Door Opener
description: Documenting my journey building a custom smart garage door opener integrated with Home Assistant
permalink: /smart-garage-door/
date: 2025-12-24
---

## Introduction

This journey started from a desire to set up and host my own smart-home setup, more specifically, a custom smart garage door opener. The overzealous dream was to write *everything* from creating the infrastructure, the host server, smart devices connected to system, and desiging the interface. This blog documents my journey of realizing that there are easier ways, learning about open source options along the way, and what the *dream* turned into!

## Initial "Smart Home" Research

To start out this journey, I knew that I needed to first set up *some* type of Smart Home system. This would be a pre-requisite to creating my own custom smart garage door opener, which was where this project started!

Early on, I realized that there were lots of popular open source home automation systems already on the market that I could utilize: [Home Assistant](https://www.home-assistant.io/), [openHAB](https://www.openhab.org/), and more. After a quick comparison, I decided on Home Assistant. This decision was largely based on the high-lvel of open source support for it, and the option to host it on a Raspberry Pi, which was a device I'd been wanting to tinker with as well. 

## Setting up Home Assistant

To begin setting up Home Assistant, I purchased a [Respberry Pi kit](https://www.amazon.com/dp/B0D95QBKJ4?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_2&th=1) that I could flash Home Assistant on. Thankfully, Home Assistant had a [great tutorial](https://www.home-assistant.io/installation/raspberrypi) for how to set up Home Assistant on a Pi, and I didn't have any issues with the initial set-up.

After Home Assistant booted up, I was able to create an account and voila! I had a Smart Home set up that I could connect devices to. Thanks to Home Assistant's ability to automatically find available devices, I was able to immediately start adding devices like my front door lock. 

## Developing a custom smart garage door opener. 

Now that I had the Smart Home network set up, it was time to start developing my custom smart garage door opener!

### Defining the requirements

First, I needed to define what I wanted from my system. I wanted a small and easy to onboard/work with micro-controller for fast development and for it to be non-obstructive when mounted. The smart garage door 

To start, my self-defined reqiurements were to use a small microcontroller so that it would be low-profile when mounted. The opener needed to be able to *at least* sense if the garage door is closed or not, as well as simulate a button press to open or close the garage door.

#### Wait, How do you simulate pressing the garage door button?

Every day, before I leave the house, I walk into the garge, press the button on the wall to open the garage door, and then get into my car to leave. BUT, how did that actually work? How did pressing the garage door button **ACTUALLY** open the garage door? 

In short, when you look at how your garage door is set up, you will see some small wires tracking from the garage door button to 2 screws on the garage door. When the button is presses, it closes the circuit and sends a signal to the garage door telling it to start the motor, which will run for a set amount of time, pulling the garage door belt, and therefore opening the door. 

TODO: Insert images of the screws

The key component to simulate here is the closing of the circuit to signal to the motor to start. Thankfully, on my garage door opener, access to the screws mentioned above is easy and therefore we can easily test this theory! 

> NOTE: For those following along, proceed with some caution on the following steps. 

To test this, I simply took a long jumper wire (insulated, of course) and connected it to both screws at the same time. **Just** like that! The garage door began to open! 

### Selecting hardware

Now that we know the requirements and have answers to some key questions, we can make our hardware selections.

#### Micro-controller

There were two options that I considered for the micro-controller, the [esp8266 esp-01](https://www.amazon.com/dp/B010N1ROQS?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_7) and the [esp8266 NodeMCU ESP-12F](https://www.amazon.com/dp/B09QXHWLTJ?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_2).

At first, I went for the *esp-01* and made some initial progress with it. However, to flash this device, it required jumpers to certain pins, or a separate flasher micro-controller. This made it more difficult to develop and a slower inner loop. I knew that over the long term, as I tested and iterated, this would be frustrating. Comparatively, the NodeMCU can be flashed directly via USB. While the board is slightly larger, it will make development life much easier. Therefore, I bumped up to the NodeMCU.

#### Sensor

To sense whether the garage door was open or not, I needed some sort of sensor that could mount to the frame of the garage and the garage door to indicate if it was closed. To do this, I found that a [magnetic reed switch](https://www.amazon.com/dp/B0BCYHBKVF?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_4) would do the trick. 

#### Simulate button press

As discussed above, to simulate a button press, we need to close the circuit between two specific screws on the garage door for a short amount of time to open/close the garage door. To do this, we can use a [relay](https://www.amazon.com/dp/B07XGZSYJV?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_1)! By sending a digital signal to the relay, it will close the circuit of the input wires. We can wire the garage door screws to the relay and control it via our software!

> One important thing to remember is the voltage input that is needed for the switch. One mistake I made here was accidentally buying switches that needed 5V, while the NodeMCU didn't have a 5V pin output! I had to eventually realize this and switch to the smaller 3v3 relays that would still work for the garage.

### Designing the system

#### Software

TODO: Go over how we share the state with system, how we connect the wifi, starting with arduino, etc. 

TODO: Creating a MQTT driven custom smart garage door opener. 

- Started with Arduino
- Then, converted to ESP8266_RTOS_SDK

#### Circuit design

TODO: Insert images of reed switch set up, the relay connected to the screws, maybe the 

### Connecting the custom device to Home Assistant

TODO: How do we connect this custom device to home assistant? 

### UH OH! Our first major issue!

Diagnosing issue where manual garage door remote stopped working!

#### Resolution

#### Final Schematic

TODO: Insert final schematic image? 

### Further work

TODO: Insert possible further work, like adding a sensor for explicitly measuring when it's fully open. 


--

[back](../README.md)