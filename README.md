# RobloxImageLoader

**Status:** `HEAVILY DEPRECATED`
This suite of tools is maintained for legacy support. Future versions will transition to generating single data strings for use with the `EditableImage` API via buffers.

## Overview

RobloxImageLoader is a suite of tools designed to convert `.png` images into a **ViewportCanvas** compatible format. It utilizes a modified version of [boatbomber's ViewportCanvas](https://github.com/boatbomber/ViewportCanvas) for high-performance in-game rendering.

---

## Setup Guide

### 1. External Conversion

1. **Extract** the `image_encoder.rar` archive to your local machine.
2. **Clear** the `input` folder of any sample images. (The encoder only processes the first image it finds).
3. **Place** your desired image into the `input` folder. (Requirement: Must be a `.png` file).
4. **Run** `png_to_rbxmx.exe`.

### 2. Roblox Studio Integration

1. **Import** `Modules.rbxm` into your place and **Ungroup** it inside `ReplicatedStorage`.
2. **Import** the generated `.rbxmx` file (found in the `output` folder) into your game.
3. **Parent** the generated file to `ReplicatedStorage.Images`.

---

## Usage Example

> [!IMPORTANT]
> This module should be used on the **Client**. UI elements must be descendants of `PlayerGui` to render correctly.

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

-- Require the loader module
local ImageLoader = require(ReplicatedStorage.ImageLoader)

-- Reference your converted image data
-- Replace the string below with your actual ModuleScript name
local TargetImage = ReplicatedStorage.Images["Image ModuleScript name here"]

-- Reference the target GUI
local Player = Players.LocalPlayer
local SurfaceGui = Player.PlayerGui:WaitForChild("SurfaceGui")

-- Load and render the image
ImageLoader:LoadImage(TargetImage, SurfaceGui)

```
