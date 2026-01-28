# Changelog

All notable changes to A.B.R.A. (Ability Builder & Refinement Assistant) will be documented in this file.

## 0.3.0 - 1/28/2026

### New Features

#### Visual Node Editor
- **Node-Based Logic Builder** - Create ability logic by connecting visual nodes instead of writing Ruby code
- **Trigger Nodes** - 25+ trigger types available as draggable nodes with automatic categorization
- **Action Nodes** - Visual nodes for HP changes, stat changes, status effects, weather, terrain, and more
- **Condition Nodes** - If/Unless blocks with branching logic (true/false paths)
- **Utility Nodes** - Raw code, comments, stop ability, and return value nodes
- **Smart Connections** - Drag to connect nodes with automatic socket matching
- **Node Positioning** - Drag nodes to reposition, positions saved with ability metadata
- **Zoom & Pan** - Mouse wheel zoom and drag to pan the canvas
- **Singleton Triggers** - Duplicate trigger prevention with visual feedback
- **Tab Sync** - Visual and Script tabs stay synchronized when switching

#### Enhanced Message Nodes
- **Three Message Types**:
  - Raw text messages
  - CSV-based messages (file_id + text_index)
  - Pokémon variable messages with target substitution

---

## 0.2.5 - 1/12/2026

### New Features

#### Code Editor Enhancements
- **Keyboard Shortcuts**:
  - `Ctrl+D` - Duplicate current line
  - `Ctrl+/` - Toggle comment on current line
  - `Ctrl+Shift+Up/Down` - Move line up/down
  - `Ctrl+L` - Select entire current line
  - `Ctrl+Shift+V` - Smart paste with auto-formatting
  - Full undo/redo support
- **Auto-Close Brackets & Quotes** - Typing `(`, `[`, `{`, `"`, or `'` automatically inserts the closing character
- **Matching Bracket Highlight** - Visual highlighting of matching brackets when cursor is on one
- **Line Numbers** - Click to toggle between file-level and editor-relative numbering
- **Dynamic Editor Height** - Editor automatically grows/shrinks based on content, even on backspace
- **Code Hover Tooltips** - Hover over parameters like `@target`, `handler`, `launcher` to see descriptions

#### Ability Summary Panel
- **Natural Language Explanations** - Real-time summary panel that translates your Ruby code into human-readable descriptions
- **Live Updates** - Summary automatically updates as you type code
- **Action Recognition** - Recognizes stat changes, HP modifications, status effects, type changes, weather/terrain, and more
- **Condition Translation** - Converts Ruby conditions to readable phrases (e.g., `@target.hp_rate <= 0.5` → "when HP ≤ 50%")

#### Parameter Info Tooltips
- **Visible Info Labels** - All target dropdowns now show an info label below explaining what the selected parameter means
- **17 Parameters Documented** - Descriptions for `@target`, `target`, `launcher`, `user`, `who`, `with`, `pokemon`, `skill`, `handler`, `logic`, `scene`, `hp`, `stat`, `status`, `power`, `reason`, `priority`

#### Ability Overwrite Confirmation
- **Confirmation Dialog** - When creating an ability that already exists, you're now prompted to confirm overwriting
- **Safe Updates** - Prevents accidental overwrites of existing abilities

### Code Refactoring
- **Modular Dialog Files** - Extracted 17 dialog classes from `code_editor.py` into 8 organized files:
  - `editor_dialogs_conditions.py` - Condition picker, Return, If dialogs
  - `editor_dialogs_hp_stat.py` - HP and Stat dialogs
  - `editor_dialogs_messages.py` - Message dialog
  - `editor_dialogs_status.py` - Status dialog
  - `editor_dialogs_environment.py` - Weather and Terrain dialogs
  - `editor_dialogs_items.py` - Item dialog
  - `editor_dialogs_pokemon.py` - Form and Type dialogs
  - `editor_dialogs_battle.py` - Hazard, Move Priority, Force Switch dialogs
  - `editor_dialogs_effects.py` - Set/Remove Effect dialogs
- **Extracted Components** - `AbilityExplainer` and `TriggerBlock` moved to dedicated component files
- **Centralized Constants** - `TRIGGER_PARAMS`, `CONDITION_CATEGORIES`, `FRIENDLY_CONDITIONS` moved to `logic/constants.py`
- **New Tooltip Utilities** - `views/components/tooltip.py` with `Tooltip`, `TooltipComboBox`, `ParamInfoComboBox`, and `CodeEditorTooltip` classes
- **Reduced File Size** - `code_editor.py` reduced from ~3500 lines to ~720 lines

### UI Improvements
- **Trigger Page Title** - Clear "Ability triggers" title displayed on trigger/event selection page
- **Slightly Larger Dialogs** - Dialog heights increased to accommodate info labels

---


## 0.2.0 - 1/10/2026

### New Features

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
