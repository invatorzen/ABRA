<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/invatorzen/PSDKPlugins">
    <img src="https://i.imgur.com/Q3LOc4v.png" alt="Logo" width="240" height="240">
  </a>

  <h3 align="center">A.B.R.A.</h3>

  <p align="center">
    <i>Allows a newer user to create abilities with a GUI!</i>
    <br /> <br />
    <a href="(ill put a link here when I get it)"><strong>(update link) Download</strong></a>
    <br />
    <br />
    <a href="https://github.com/invatorzen/InvatorzenPSDKPlugins/issues">Report Bugs</a>
      

  [![python badge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)
  [![psdk badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_for_psdk.svg)](https://gitlab.com/pokemonsdk/pokemonsdk)
  [![invatorzen badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_by_invatorzen.svg)](https://github.com/invatorzen/InvatorzenPSDKPlugins/tree/main)
  </p>
</div>

## Overview

A.B.R.A. (Ability Builder & Refinement Assistant) is a specialized tool designed for Pokémon SDK (PSDK) developers to create and implement battle abilities without requiring extensive knowledge of Ruby scripting or the internal data structures of the SDK. It provides a visual interface for defining ability metadata, selecting battle events / triggers, and generating the necessary logic blocks.

This is very early in development, is usable but will receieve updates if people like this program. I will also take suggestions for features, improvements, and new commonly used conditions for returns.

## Features

- **Project Integration**: Connects directly to existing PSDK projects by loading .studio files.
- **Metadata Management**: Define internal symbols, and multi-language names and descriptions.
- **Event / Trigger System**: Select from a wide variety of battle events / triggers, including switch-in events, end-of-turn actions, damage modification, and stat changes.
- **Script Generation**: Automatically generates a script compatible with PSDK for your new ability.
- **Condition Library**: Access a library of over 80 pre-defined battle conditions (e.g., weather checks, type effectiveness, HP thresholds) with a searchable interface.
- **Quick Actions**: Insert common battle effects like changing HP, modifying stats, or displaying messages with a single click.
- **Code Preview**: Review the generated Ruby and JSON structures before saving them to the project directory.

## Installation

### Using Executable
Download the latest version from the releases page and run `ABRA.exe`.

## Internationalization

ABRA supports multiple languages for the interface and the condition library. The current supported languages are:
- English
- French
- Spanish

Language settings are persisted in the local configuration and can be switched at any time from the project selection screen.

## Technical Details

ABRA automates the creation of three critical components for PSDK:
1. **JSON Data**: Generates the ability data file located in `Data/Studio/abilities/`.
2. **Ruby Logic**: Creates a context-aware Ruby script in `scripts/1 ABRA_Scripts/00 Effects/01 Abilities/`.
3. **Text Data**: Updates the local text database (CSV) for ability names and descriptions.

The generated Ruby code utilizes the `Battle::Effects::Ability` base class and implements hooks that interact with the PSDK battle logic handlers (DamageHandler, StatChangeHandler, etc.).