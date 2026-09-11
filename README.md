<div align="center">

# vRP Radar

A legacy speed radar system developed for FiveM servers using the vRP framework.

![Lua](https://img.shields.io/badge/Lua-2C2D72?style=flat-square\&logo=lua\&logoColor=white)
![FiveM](https://img.shields.io/badge/FiveM-Resource-F40552?style=flat-square)
![vRP](https://img.shields.io/badge/Framework-vRP-444444?style=flat-square)
![Status](https://img.shields.io/badge/Status-Legacy%20Project-6c757d?style=flat-square)

</div>

> [!NOTE]
> **Early project — originally developed around 2019.**
>
> This repository is part of my early programming journey.
>
> The project is preserved as a record of my technical evolution and does not necessarily represent my current coding standards or architecture practices.

---

## About

**vRP Radar** is a speed enforcement resource developed for FiveM servers running the vRP framework.

The system monitors vehicles passing through predefined radar locations, calculates their speed and automatically applies fines when the configured speed limit is exceeded.

This was one of my first experiences working with client/server communication, game natives, coordinates and server-side business rules.

---

## Features

* Multiple predefined radar locations
* Real-time vehicle speed detection
* Speed calculation in km/h
* Progressive fines according to vehicle speed
* Automatic server-side payment handling
* Visual flash effect when passing a radar above the speed limit
* Sound feedback
* Chat notification containing the detected speed and fine
* Exemption support for specific service groups
* Client/server communication using vRP Tunnel

---

## How it works

The client continuously checks the player's distance from configured radar locations.

When a vehicle enters the radar detection area, its speed is calculated using the GTA V entity velocity.

If the vehicle exceeds the configured **100 km/h** limit, the resource can:

1. Trigger a visual radar flash
2. Play an interface sound
3. Calculate the applicable fine
4. Request the payment through the server
5. Display the detected speed to the player

Higher speeds result in progressively larger fines.

---

## Service exemptions

The original resource allows members of specific vRP groups to bypass radar fines:

```text
PoliciaSalario
ParamedicoSalario
```

These group names belong to the original server configuration and may need to be changed for other vRP bases.

---

## Tech Stack

| Technology     | Usage                                      |
| -------------- | ------------------------------------------ |
| Lua            | Client and server logic                    |
| FiveM          | Runtime environment and GTA V natives      |
| vRP            | Player identification, groups and payments |
| Tunnel / Proxy | Client-server communication                |

---

## Demo

An original demonstration of the resource is still available:

[Watch the original demo on Streamable](https://streamable.com/wsa1y)

---

## Requirements

This project was originally designed for an older vRP-based FiveM environment.

Main dependency:

```text
vRP
```

The code may require adaptations to work with modern FiveM or newer/custom vRP implementations.

---

## Installation

Copy the resource into your FiveM resources directory:

```text
resources/
└── vrp_radar/
```

Then add it to your server configuration:

```text
start vrp_radar
```

Make sure the vRP framework is started before this resource.

---

## Configuration

Radar positions are defined directly inside `client.lua`.

Each radar uses GTA V world coordinates:

```lua
{ ['x'] = 0.0, ['y'] = 0.0, ['z'] = 0.0 }
```

The original implementation uses a speed limit of:

```text
100 km/h
```

Fine values and service exemptions are also defined directly in the source code.
