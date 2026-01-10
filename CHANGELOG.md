# Changelog

All notable changes to A.B.R.A. (Ability Builder & Refinement Assistant) will be documented in this file.

## 0.2.0 - 1/10/2026

### New Features

#### DiscordRPC
- **Share activity through discord** you can obviously disable this in discord, but this is more so something I personally like and want to see people using my program :3

#### Code Editor UI Refinement
- **Advanced Layout**: Read-only `def` and `end` method labels are now moved **outside** the editable code container to prevent any possible formatting issues.
- **Focused Workspace**: The editable area's border strictly highlights user-modifiable code, providing a cleaner interface.

#### Standardized Theme Toggle
- New **dual-icon (☀️ 🌙)** theme toggle implemented across all views.

#### Button Styling Polish
- **Standardized Colors**: "Add Trigger" and "Back" buttons now use a consistent blue shade.
- **Improved Visibility**: Functional buttons (Format, Preview, Quick Actions) are now lighter gray in light mode for better contrast.
- **Centered Icons**: Fixed vertical centering for the trash can icon on the Ability Manager page. (I think emojis have weird spaces or something so I may switch to images at some point.)

#### Condition Suggestions - Major Expansion
- **60+ new battle conditions** for the "Insert If Condition" feature
- New **Owner State** category - conditions always available using `@target`:
  - HP checks: Owner at full HP, HP ≤50%, HP ≤25%
  - Status checks: Owner is asleep, poisoned, burned, paralyzed, frozen, confused
  - Ability checks: Owner has Magic Guard, Owner has Poison Heal
  - Type checks: Owner is Poison/Fire/Water/Grass/Ground/Rock/Steel/Ice-type
  - Grounded check, Switching check, Alive/Dead checks
- New **Battlers** category for end-of-turn triggers:
  - `battlers.include?(@target)` - Owner is on field
  - Any battler/foe/ally status checks
  - Adjacent allies check
- New **Handler Checks** category:
  - `logic.damage_handler.can_heal?(@target)` - Can owner be healed
  - Status applicability checks for burn, poison, toxic, freeze, paralysis, sleep
  - Battle continuation check
- New **Stat Checks** category:
  - Attack/Defense/Speed/Sp.Atk can be raised
  - Speed can be lowered
  - Any stat can be raised
- Enhanced **Weather & Terrain** conditions:
  - Rain/Sun with "any" variants (includes hard rain/sun)
  - Global rain/sun checks
  - All terrain types

#### Quick Actions - 4 New Actions
- **Move Priority** - Modify move priority (+3 to -7)
- **Force Switch** - Force a Pokémon to switch out
- **Set Effect** - Add battle effects (Confusion, Flinch, Encore, Taunt, Torment, Disable, Substitute)
- **Remove Effect** - Remove battle effects from a Pokémon

#### UI/UX Improvements
- **Consistent Back Buttons** - All back buttons now have the same arrow character, font, size, and position
- **Draggable & Resizable Windows** - Main window and quick action dialogs are now resizable while maintaining aspect ratio
- **Trigger Deletion** - Added "X" delete button next to each trigger header for quick removal
- **Visual Selection Indicators** - Buttons in quick action dialogs now show visual selection state
- **Improved Dialog Sizing** - Quick action dialogs have better default sizes

#### Ability Update Flow
- Updated UI text to reflect "Update ability" when editing existing abilities
- "Update ability" button and "Ability updated successfully!" message
- Ruby scripts now properly overwrite existing files when updating

### Formatter Improvements
- **Global Formatting**: The "Format Code" button now formats the entire script at once.
- **Robust Parsing**: New index-based Ruby parser correctly distinguishes between nested `if/end` blocks and the method's final `end`.
- **Indentation Restoration**: Formatter now correctly restores cursor position while respecting the 10-column baseline.

### Bug Fixes
- Fixed condition filtering regex to properly handle Ruby symbols (`:asleep?`, `:magic_guard`) 
- Fixed `@target` based conditions not appearing - regex no longer incorrectly extracts `target` from `@target`

### Localizations
- All new conditions translated to English, French, and Spanish
- 6 new condition categories with full translations

---

## 0.1.0 - Initial Release

### Features
- Project Integration with PSDK .studio files
- Metadata Management for ability symbols, names, and descriptions
- Event/Trigger System with 20+ battle event types
- Script Generation for PSDK-compatible Ruby code
- Condition Library with 80+ pre-defined conditions
- Code Preview before saving
- 13 Quick Action buttons for common ability code
- Multi-language support (English, French, Spanish)
