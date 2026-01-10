<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/invatorzen/PSDKPlugins">
    <img src="https://i.imgur.com/Q3LOc4v.png" alt="Logo" width="240" height="240">
  </a>

  <h3 align="center">A.B.R.A.</h3>

  <p align="center">
    <i>Ability Builder & Refinement Assistant for Pokémon SDK</i>
    <br /> <br />
    <a href="https://github.com/invatorzen/ABRA/releases"><strong>Download v0.2.0</strong></a>
    <br />
    <br />
    <a href="https://github.com/invatorzen/ABRA/issues">Report Bugs</a>
      

  [![python badge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)
  [![psdk badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_for_psdk.svg)](https://gitlab.com/pokemonsdk/pokemonsdk)
  [![invatorzen badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_by_invatorzen.svg)](https://github.com/invatorzen/InvatorzenPSDKPlugins/tree/main)
  </p>
</div>

## Overview

A.B.R.A. (Ability Builder & Refinement Assistant) is a specialized tool designed for Pokémon SDK (PSDK) developers to create and implement battle abilities without requiring extensive knowledge of Ruby scripting or the internal data structures of the SDK. It provides a visual interface for defining ability metadata, selecting battle events/triggers, and generating the necessary logic blocks.

## ✨ What's New in v0.2.0

- **Advanced Code Editor** - Refined layout with read-only code separation and 10-space indentation lock.
- **Enhanced Formatter** - Global full-script formatting with robust Ruby block parsing.
- **Standardized UI** - Improved button aesthetics and a new dual-icon theme toggle across all views.
- **60+ New Conditions** - Expanded library for end-of-turn events with stat and handler checks.
- **4 New Quick Actions** - Move Priority, Force Switch, Set Effect, Remove Effect.

See [CHANGELOG.md](CHANGELOG.md) for full details.

## Features

- **Project Integration**: Connects directly to existing PSDK projects by loading .studio files.
- **Metadata Management**: Define internal symbols, and multi-language names and descriptions.
- **Event / Trigger System**: Select from 20+ battle events/triggers, including switch-in events, end-of-turn actions, damage modification, and stat changes.
- **Script Generation**: Automatically generates a script compatible with PSDK for your new ability.
- **Condition Library**: Access a library of **140+ pre-defined battle conditions** with a searchable interface.
- **Advanced Code Editor**: Dedicated workspace with 10-space PSDK indentation and read-only / editable code separation.
- **Intelligent Formatter**: Global script formatting with nested block support and cursor preservation.
- **Ability Updates**: Edit and update existing abilities with proper file overwriting.

## Quick Actions

ABRA includes **17 quick action buttons** for inserting common ability code:

| Action | Description |
|--------|-------------|
| **Return Condition** | Insert a conditional return with if/unless support and multiple conditions |
| **Insert If** | Add an if/unless condition block with and/or logic |
| **Change HP** | Heal, damage, or set HP with dynamic amount options |
| **Stat Change** | Modify ATK, DEF, SPD, SPA, SPD, ACC, EVA stats |
| **Apply Status** | Apply poison, burn, freeze, paralysis, sleep, confusion, flinch, or cure |
| **Change Weather** | Set rain, sun, sandstorm, hail, or clear weather |
| **Change Terrain** | Set electric, grassy, misty, psychic terrain, or clear |
| **Modify Item** | Give, remove, or swap held items |
| **Change Form** | Modify Pokémon form |
| **Change Type** | Modify Pokémon type |
| **Set Hazard** | Deploy Stealth Rock, Spikes, Toxic Spikes, or Sticky Web |
| **Show Ability** | Display the ability activation animation |
| **Display Message** | Show battle messages |
| **Move Priority** | Modify move priority (+3 to -7) |
| **Force Switch** | Force a Pokémon to switch out |
| **Set Effect** | Add battle effects (Confusion, Flinch, Encore, Taunt, Torment, Disable, Substitute) |
| **Remove Effect** | Remove battle effects from a Pokémon |

## Condition Categories

The condition picker organizes 140+ conditions into searchable categories:

| Category | Examples |
|----------|----------|
| **Owner State** | Owner is alive/dead, HP <= 50%, is asleep, has Magic Guard, is Poison-type |
| **Battlers** | Owner is on field, any battler asleep, has foes, has adjacent allies |
| **Handler Checks** | Can heal, burn/poison/freeze can be applied |
| **Stat Checks** | Attack can be raised, speed can be lowered |
| **Weather & Terrain** | Rain (any), sunny, hail, grassy terrain, electric terrain |
| **Target/Attacker** | Target is dead, attacker is ally/enemy, target type checks |
| **Skill Properties** | Skill is physical/special/status, made contact, is critical hit |
| **Type Matchups** | Super effective, not very effective, STAB, skill type checks |
| **Probability** | 10%/30%/50% chance |

## Installation

### Using Executable
Download the latest version from the [releases page](https://github.com/invatorzen/ABRA/releases) and run `ABRA.exe`.

## Internationalization

ABRA supports multiple languages for the interface and the condition library:
- English
- French
- Spanish

Language settings are persisted in the local configuration and can be switched at any time from the project selection screen.

## Technical Details

ABRA automates the creation of three critical components for PSDK:
1. **JSON Data**: Generates the ability data file located in `Data/Studio/abilities/` using the db_symbol as filename.
2. **Ruby Logic**: Creates a context-aware Ruby script in `scripts/00001 ABRA_Scripts/00000 Effects/00000 Abilities/` with indexed filenames (e.g., `00000 FlashFire.rb`).
3. **Text Data**: Updates the local text database (CSV) for ability names and descriptions.

The generated Ruby code utilizes the `Battle::Effects::Ability` base class and implements hooks that interact with the PSDK battle logic handlers (DamageHandler, StatChangeHandler, etc.).

## Terminology

- **Attacker**: The Pokémon using a move (previously called "Launcher")
- **Target**: The Pokémon receiving the effect
- **@target**: The ability owner (the Pokémon with this ability)
- **Battlers**: All alive Pokémon on the field (available in end-of-turn events)
- **Logic**: The battle logic controller (provides access to handlers)

## Contributing

Suggestions for features, improvements, and new commonly used conditions are welcome! Please open an issue on GitHub.