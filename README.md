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
    <a href="https://github.com/invatorzen/ABRA/releases"><strong>Download v0.5.0</strong></a>
    <br />
    <br />
    <a href="https://github.com/invatorzen/ABRA/issues">Report Bugs</a>
    ·
    <a href="https://discord.gg/BHeRSFXGQK">Discord Community</a>

  [![forthebadge](https://forthebadge.com/api/badges/community/019b4b6a-36fd-7412-9947-a2d4ba37909e.svg)](https://forthebadge.com)
  [![psdk badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_for_psdk.svg)](https://gitlab.com/pokemonsdk/pokemonsdk)
  [![invatorzen badge](https://raw.githubusercontent.com/invatorzen/Invatorzens_PSDKPlugins/refs/heads/main/svgs/made_by_invatorzen.svg)](https://twitter.com/invatorzen)
  </p>
</div>

## Overview

A.B.R.A. (Ability Builder & Refinement Assistant) is a native desktop application for Pokémon SDK (PSDK) developers to create and manage battle abilities without requiring extensive knowledge of Ruby scripting. Built with **Tauri v2**, **TypeScript**, **React**, and **React Flow**, it provides a visual node editor, live Ruby code generation, and deep integration with your PSDK project.

## What's New in v0.5.0

**Complete rewrite** from Python to TypeScript.

- **Custom Methods** - Define reusable Ruby methods as visual nodes with parameters, docs, and visibility controls, then call them from anywhere in your graph
- **Import Official Abilities** - Browse, preview, and import any official PSDK ability (including custom methods) directly into your graph with one click
- **PSDK Submodule Management** - Automatically detects and offers to clone the `pokemonsdk` submodule for official ability access
- **Resizable Sidebar** - Drag to resize (200px–600px) or collapse the sidebar in the Visual Builder
- **Minimap** - Auto-fading minimap with color-coded node types for canvas orientation
- **Node Animations** - Smooth creation and deletion animations
- **Context Menus** - Right-click menus on nodes, edges, and the canvas for quick actions
- **Light Mode Polish** - Dedicated pass ensuring all components look polished in both themes
- **Execute Move Action** - New quick action with a searchable move selector backed by PSDK data
- **Array Variables** - Set Array and Check Array quick actions for tracking lists of values
- **Raw Pokemon Messages** - Display custom battle text with Pokemon nickname interpolation
- **V1 Migration** - Automatically converts Python ABRA v1 metadata to the new format

See [CHANGELOG.md](CHANGELOG.md) for full details.

## Features

### Visual Node Editor

- **React Flow Canvas** - Interactive node graph with snap-to-grid, zoom, pan, and minimap
- **60+ Battle Hooks** - All PSDK battle events organized into 12 categories as draggable hook nodes
- **28+ Quick Actions** - One-click insertion of common ability logic (HP, stats, status, weather, terrain, items, forms, messages, custom methods, and more)
- **Condition Nodes** - If/Unless blocks with branching logic (true/false paths) and 140+ pre-defined conditions
- **Smart Connections** - Drag to connect nodes with automatic socket matching and colored edges
- **Node Copy-Paste** - Copy and paste nodes with Ctrl+C/V, preserving connections and parameters
- **Context Menus** - Right-click nodes, edges, and the canvas for quick actions (edit, delete, select connected, copy, paste)
- **Auto-Layout** - Intelligent hierarchical repositioning with guard condition detection
- **Node Editing** - Double-click or right-click to edit any node's parameters
- **Random Choice Node** - Probabilistic branching logic with dynamic output sockets

### Import Official Abilities

- **Browse & Search** - Searchable, sortable list of all official PSDK abilities with descriptions
- **Ruby Source Preview** - Syntax-highlighted preview of the official ability source code
- **One-Click Import** - Parses official Ruby source into visual nodes automatically
- **Conflict Resolution** - Choose to overwrite or merge when importing into an existing graph
- **Reference Panel** - Keep the official source as a read-only reference viewable at any time

### Ruby Script View

- **Live Code Generation** - Full Ruby class generated from the node graph in real time
- **Syntax Highlighting** - Ruby syntax highlighting with per-hook section dividers
- **Copy to Clipboard** - One-click copy of the generated Ruby code

### Core Features

- **Project Integration** - Connects directly to existing PSDK projects by loading `.studio` files
- **Ability Summary Panel** - Live natural-language summary of your ability graph
- **Quick Suggestions** - Context-sensitive condition suggestions with Stop Ability, Quick Returns, and If Node tabs
- **Instance Variables** - Set Variable (`@var`) nodes with automatic discovery and suggestion
- **Metadata Management** - Multi-language names and descriptions with auto `db_symbol` generation
- **Script Checker** - Automatic detection and one-click installation of missing ABRA core scripts on project open
- **Auto-Updater** - Integrated GitHub-based update system with background downloads
- **Dark & Light Themes** - Fully designed theme system with comprehensive color tokens
- **Tab Sync** - Visual Builder and Ruby Script tabs stay synchronized

## Quick Actions

ABRA includes **28+ quick actions** for inserting common ability logic:

| Action | Description |
|--------|-------------|
| **Stop Ability** | Return nil / stop ability execution |
| **Return Value** | Return a specific value from a hook |
| **Insert If** | Add an if/unless condition block |
| **Change HP** | Heal, damage, or set HP |
| **Stat Change** | Modify ATK, DEF, SPD, SPA, SPD, ACC, EVA stats |
| **Apply Status** | Apply or cure status conditions |
| **Change Weather** | Set or clear weather conditions |
| **Change Terrain** | Set or clear field terrain |
| **Modify Item** | Give, remove, or swap held items |
| **Change Form** | Change Pokémon form (auto-includes animation) |
| **Change Type** | Modify Pokémon type |
| **Set Hazard** | Deploy entry hazards |
| **Show Ability** | Display ability activation animation (auto-includes wait) |
| **Wait For Animation** | Wait for an animation to complete |
| **Display Message** | Show battle messages (raw text, CSV-based, or Pokémon variable) |
| **Move Priority** | Modify move priority |
| **Force Switch** | Force a Pokémon to switch out |
| **Execute Move** | Execute a specific move |
| **Random Choice** | Create probabilistic branching logic |
| **Set Effect** | Add battle effects (Confusion, Flinch, Encore, Taunt, etc.) |
| **Remove Effect** | Remove battle effects |
| **Set Variable** | Set an instance variable (`@var`) |
| **Set Array** | Create an array instance variable |
| **Check Array** | Check array contents |
| **Custom Method** | Define a reusable Ruby method with parameters and docs |
| **Call Method** | Invoke a custom method defined on the canvas |
| **Raw Code** | Insert a freeform Ruby code block |
| **Add Comment** | Add a comment node |

## Hook Categories

60+ battle hooks organized into 12 categories:

| Category | Examples |
|----------|----------|
| **Movement** | On Switch In, On Flee Passthrough/Prevention, On Transform, Ignore Hazards |
| **Turn** | On End Turn, On Post Action |
| **Damage & Healing** | On Damage Prevention, On Post Damage, On Post Damage Death, On Pre/Post Drain |
| **Stats (Global)** | ATK/DEF/SPD/SPA/SPD Modifiers |
| **Stats (Combat)** | Stat Decrease/Increase Prevention, On Stat Change (pre/post, self, global) |
| **Status** | On Status Prevention, On Post Status Change, On Poison/Burn Damage |
| **Move Multipliers** | Base Power, Mod1/2/3, Sp.Atk/Def, Type Multiplier Overwrite, Effectiveness |
| **Move Accuracy** | Chance of Hit, Bypass Hit Chance, Pre/Post Accuracy Check, Move Priority, Effect Chance |
| **Move Prevention** | Move Prevention (User/Target), Ability Immunity, Target Redirection, Type Change, Disabled Check |
| **Weather & Terrain** | On Post Weather/Terrain Change, On Weather/Terrain Prevention |
| **Items** | Held Item Use Prevention, Pre/Post Item Change |
| **Ability** | Ability Change Prevention, Pre/Post Ability Change |

## Condition Categories

The condition picker organizes **140+ conditions** into searchable categories:

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

Download the latest version from the [releases page](https://github.com/invatorzen/ABRA/releases) and run the installer.

## Internationalization

ABRA supports multiple languages for the entire interface:

- English
- French
- Spanish

Language can be switched at any time from the top bar and is persisted across sessions.

## Technical Details

ABRA automates the creation of these components for your PSDK project:

1. **JSON Data** - Ability data file in `Data/Studio/abilities/` using the `db_symbol` as filename
2. **Ruby Logic** - Context-aware Ruby script in `scripts/00001 ABRA_Scripts/00001 Effects/00001 Abilities/`
3. **Text Data** - Updates the local text database (CSV) for ability names and descriptions
4. **Hook Scripts** - Auto-creates required hook scripts in `scripts/00001 ABRA_Scripts/00001 Effects/00000 Hooks/` if missing
5. **Metadata** - Saves node positions and graph data to `Data/ABRA/metadata/` for visual editor persistence

### Tech Stack

- **Frontend** - React + TypeScript + React Flow (XYFlow) + Zustand + Tailwind CSS
- **Backend** - Tauri v2 (Rust)
- **Code Generation** - Ruby targeting `Battle::Effects::Ability` base class

## Terminology

- **Attacker** - The Pokémon using a move (previously called "Launcher")
- **Target** - The Pokémon receiving the effect
- **@target** - The ability owner (the Pokémon with this ability)
- **Battlers** - All alive Pokémon on the field (available in end-of-turn events)
- **Logic** - The battle logic controller (provides access to handlers)
- **Handler** - Battle event handler passed to many hooks (provides access to scene, logic, etc.)

## Contributing

Suggestions for features, improvements, and new commonly used conditions are welcome! Please open an issue on [GitHub](https://github.com/invatorzen/ABRA/issues) or join the [Discord community](https://discord.gg/BHeRSFXGQK).
