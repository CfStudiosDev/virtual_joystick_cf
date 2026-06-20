<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/virtual_joystick_cf_logo_dark.png">
    <img alt="Virtual Joystick Logo" src="assets/virtual_joystick_cf_logo_light.png">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/cf_studios_logo_dark.png">
    <img alt="Cf Studio Logo" src="assets/cf_studios_logo_light.png" height=24>
  </picture>
</h1>

[![Godot Engine][godot-badge]][godot-link] [![Version][changelog-badge]][changelog-link] [![MIT License][license-badge]][license-link]

A professional, high-performance, and ready-to-use Virtual Joystick. Specifically designed for mobile games in Godot 4.5 or later.

## 🌎 Language

- **English**
- [Português](README.pt.md)

## 📋 Table of Contents

- [🌎 Language](#-language)
- [📋 Table of Contents](#-table-of-contents)
- [✨ Features](#-features)
- [🚀 Installation](#-installation)
- [🛠️ How to Use](#️-how-to-use)
  - [Option 1: Scene Instancing (Recommended)](#option-1-scene-instancing-recommended)
  - [Option 2: File System Drag \& Drop](#option-2-file-system-drag--drop)
- [⚙️ Configuration](#️-configuration)
- [💻 Code Integration](#-code-integration)
  - [Option 1: Input Action](#option-1-input-action)
  - [Option 2: Signals](#option-2-signals)
- [📂 Project Structure](#-project-structure)
- [☕ Support the Project](#-support-the-project)
- [⚖️ License](#️-license)
- [📘 About](#-about)

## ✨ Features

- **Behavior Modes:** Supports *Static*, *Dynamic*, and *Following* modes;
- **Direction Snapping:** Support for 2-way, 4-way, 8-way, or 360° (full analog) movement;
- **Precise Calibration:** Customize *Deadzone*, *Touch Boundary*, and *Dynamic Area* to ensure a professional control feel;
- **Custom Visuals:** Personalize the appearance with your own textures for the base and the stick;
- **Input Actions:** Automatically triggers defined `InputMap` actions, allowing the use of `Input.get_vector` or `Input.get_axis` in your scripts;
- **Tactile Feedback:** Integrated and adjustable vibration for direction changes;
- **Visual Debugging:** Tools to visualize activation areas, deadzones, and boundaries directly in the Godot viewport.

## 🚀 Installation

1. Move the `addons/` folder into your project's `res://` directory.
2. Go to **Project -> Project Settings -> Plugins**.
3. Find **Virtual Joystick CF** and set the status to **Enabled**.

## 🛠️ How to Use

To ensure all visual components and internal nodes work correctly, you must instance the **Virtual Joystick CF Scene**:

### Option 1: Scene Instancing (Recommended)
1. Open the scene where you want to add the control (e.g., your HUD or UI);
2. Click **Instantiate Child Scene** or use the shortcut *Ctrl+Shift+A*;
3. Select the `virtual_joystick_cf.tscn` scene.
> **⚠️ Note:** Remember to check the **Addons** checkbox in the bottom right corner of the window to include files from the `addons/` folder.

### Option 2: File System Drag & Drop
1. Open the target scene (e.g., HUD or UI);
2. In the **File System**, navigate to `addons/virtual_joystick_cf/`;
3. Drag the `virtual_joystick_cf.tscn` file into your **Scene Tree**.

## ⚙️ Configuration

The **Inspector** provides organized groups for easy customization:
- **Virtual Joystick:** Disable the joystick, set behavior mode, direction snapping, deadzone, and touch boundary.
- **Dynamic Area Margin:** Define the activation area for dynamic mode using normalized margins (0.0 to 1.0).
- **Visual:** Assign custom textures and adjust global scale.
- **Action:** Map the joystick to your `InputMap` actions (e.g., `&ui_up`, `&ui_down`).
- **Vibration:** Enable tactile feedback and adjust its intensity.
- **Editor:** Enable debug drawings to visualize logic during gameplay tests or editing.

## 💻 Code Integration

### Option 1: Input Action
Once actions are mapped, your character script doesn't need to know the virtual joystick exists:
```gdscript
func _physics_process(_delta: float) -> void:
    var direction: Vector2 = Input.get_vector(
        "ui_left",
        "ui_right",
        "ui_up",
        "ui_down")
    velocity = direction * SPEED
    move_and_slide()
```

### Option 2: Signals
Signals are available for custom events, such as `pressed`, `released`, and `direction_changed` for direct access to `input_direction`:
```gdscript
func _on_joystick_direction_changed(input_direction: Vector2) -> void:
    print("Virtual Joystick CF input_direction: ", input_direction)
```

## 📂 Project Structure
- `res://addons/virtual_joystick_cf/`: Plugin root with main scene, scripts, and icon;
- `res://addons/virtual_joystick_cf/direction_utils`: Core mathematical utility for 2D direction handling and vector snapping;
- `res://addons/virtual_joystick_cf/example`: Example game demonstrating the Virtual Joystick CF in action;
- `res://addons/virtual_joystick_cf/textures`: Default textures for the base and stick of the Virtual Joystick CF;
- `res://addons/virtual_joystick_cf/docs`: Detailed documentation for:
  - [Virtual Joystick CF](addons/virtual_joystick_cf/docs/VIRTUAL_JOYSTICK_CF.md);
  - [Direction Utils](addons/virtual_joystick_cf/docs/DIRECTION_UTILS.md).

## ☕ Support the Project

The development of this plugin is maintained for free and independently. If this plugin is useful for your game, consider supporting **CF Studios**. Any contribution is greatly appreciated!

[![Ko-fi][ko-fi-badge]][ko-fi-link]

## ⚖️ License

Distributed under the **MIT License**. See the [LICENSE](LICENSE) file for more information.

If this plugin is useful for your project, crediting **CF Studios** is appreciated but not legally required (beyond maintaining the original license file).

## 📘 About

- **Author:** Carlos Filho
- **Email:** <cf.studios.dev@gmail.com>

[changelog-badge]: https://img.shields.io/badge/version-1.0.0-blue?
[changelog-link]: CHANGELOG.md
[itch-io-badge]: https://img.shields.io/badge/Itch-%23FF0B34.svg?style=for-the-badge&logo=Itch.io&logoColor=white
[itch-io-link]: https://cf-studios.itch.io/
[ko-fi-badge]: https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white
[ko-fi-link]: https://ko-fi.com/cfstudiosdev/donate
[license-badge]: https://img.shields.io/badge/license-MIT-blue
[license-link]: LICENSE
[godot-link]: https://godotengine.org/
[godot-badge]: https://img.shields.io/badge/Godot-4.5+-blue?logo=godot-engine&logoColor=white