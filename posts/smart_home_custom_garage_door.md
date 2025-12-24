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

TODO: Creating a MQTT driven custom smart garage door opener. 

- Started with Arduino
- Then, converted to ESP8266_RTOS_SDK

Hardware setup

Connecting to the Home Assistant setup. 

Diagnosing issue where manual garage door remote stopped working!


--

[back](../README.md)