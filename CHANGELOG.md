# Changelog

All notable changes to A.B.R.A. (Ability Builder & Refinement Assistant) will be documented in this file.

## 0.3.2 - 2/3/2026

### Refactoring & Terminology

- **Triggers to Hooks Alignment** - Renamed all project-wide references of "triggers" to "hooks" to align with PSDK terminology. This includes:
  - **Directory Structure**: `logic/nodes/triggers/` is now `logic/nodes/hooks/`.
  - **Files**: Renamed `trigger_block.py` to `hook_block.py` and `trigger_selector.py` to `hook_selector.py`.
  - **Codebase**: Updated all class names (`HookBlock`, `HookSelectorView`), variable names (`hook_codes`, `selected_hooks`), and constants (`HOOK_PARAMS`).
  - **Translations**: Refactored all translation keys from `trig_` to `hook_` and updated English, French, and Spanish labels.
  - **Logic**: Updated `VisualLogicGenerator` to handle the new nomenclature for context-aware code generation.
- **Modular Node Architecture** - Successfully split `logic_nodes.py` into modules organized by category. This improves performance and navigation:
  - **Hook Categories**: Split into nested files like `hooks/damage.py`, `hooks/stats.py`, and `hooks/environment.py`.
  - **Action Domains**: Divided into `actions/combat.py`, `actions/visual.py`, `actions/pokemon.py`, etc.
  - **Conditions & Utilities**: Extracted to their own dedicated files for cleaner logic branching.
  - **Central Registry**: Moved core definitions to `logic/nodes/registry.py`.
- **Core App Refactoring** - Extracted heavy utility and dialog logic from `main.py` into a new `app/` package, reducing `main.py` footprint by ~20%:
  - **Config Management**: Moved path resolution and window persistence to `app/config.py`.
  - **Hook Installation**: Relocated PSDK extension/hook auto-setup logic to `app/hooks.py`.
  - **Standardized Dialogs**: Centralized error, confirmation, and folder migration dialogs in `app/dialogs.py`.

### Visual Builder Refinement

- **Precise Node Connections** - Connection points now align with the center of "○" and "●" icons using scale-aware positioning.
- **Vertical Socket Centering** - Implemented automatic vertical centering for sockets using inner layout frames. This ensures connections are balanced regardless of node height (e.g., "If (Generic)" nodes).
- **Edge-Alinged Connections** - Connection lines now attach directly to the absolute left and right edges of the node frame, staying perfectly aligned even during real-time resizing.
- **Resizing Stability** - Fixed node resizing logic to be correctly scale-aware and ensure UI synchronization.

---

## 0.3.1 - 2/2/2026

### New Features

- **Bypass Hit Chance Hook** - New `on_bypass_chance_of_hit?` hook allows abilities to guarantee moves hit (bypass accuracy check). Available under Accuracy & Priority category.
- **Hook Installation Check** - ABRA now checks for required hook scripts on project load and auto-creates them if missing
- **Node Editing** - Double-click or right-click → "Edit Node..." on action nodes to open dialogs pre-filled with current values. Dialogs now show context-aware dropdown options based on connected hook.

### Improvements

- **Context Menu Cleanup** - Removed "Stop Ability" and "Return Value" from the top of the right-click menu; these are still accessible in the Utility submenu
- **Context-Aware Scene Prefix** - `show_ability` and `wait_for_animation` nodes now generate the correct prefix based on hook context:
  - `handler.scene.visual` for hooks with `handler` param
  - `scene.visual` for hooks with direct `scene` param  
  - `@logic.scene.visual` for hooks without handler/scene (e.g., `on_bypass_chance_of_hit`)
- **Script-to-Visual Sync** - When switching from Script to Visual tab, existing nodes now update their parameters to match the parsed code (e.g., changing `unless` to `if` now updates the node)
- **Show Ability Quick Action** - Now creates two connected nodes (Show Ability Popup + Wait For Animation) matching script editor behavior
- **Show Ability Node Size** - Increased default size from 195×60 to 280×65 for better visibility
- **Folder Restructure** - Abilities now saved to `00001 Abilities/` so `00000 Hooks/` loads first
- **Right-Click Menu Unification** - Context menu in visual editor now opens the same dialogs as Quick Actions panel
- **Bypass Accuracy Node Size** - Fixed `hook_on_bypass_chance_of_hit` node to use standard hook dimensions (220×75)

### Bug Fixes

- **Hook Detection** - Fixed connection option filtering for hooks with `cat_*` categories (e.g., weather/terrain hooks)
- **State Persistence** - Fixed visual builder state persisting between different abilities when switching
- **Show Ability Template** - Fixed generated code to use correct prefix based on hook context (see Context-Aware Scene Prefix above)
- **Hook Deletion Navigation** - No longer navigates to hook selector when deleting connections; only navigates when last hook node is removed
- **Metadata Loading** - Fixed node positions not being restored when editing abilities; metadata is now correctly loaded from `Data/ABRA/metadata/` JSON files
- **Metadata Saving** - Fixed critical bug where metadata was never saved when editing abilities; the view was being cleared before data capture


---

## 0.3.0 - 1/28/2026

### New Features

#### Visual Node Editor
- **Node-Based Logic Builder** - Create ability logic by connecting visual nodes instead of writing Ruby code
- **Hook Nodes** - 25+ hook types available as draggable nodes with automatic categorization
- **Action Nodes** - Visual nodes for HP changes, stat changes, status effects, weather, terrain, and more
- **Condition Nodes** - If/Unless blocks with branching logic (true/false paths)
- **Utility Nodes** - Raw code, comments, stop ability, and return value nodes
- **Smart Connections** - Drag to connect nodes with automatic socket matching
- **Node Positioning** - Drag nodes to reposition, positions saved with ability metadata
- **Zoom & Pan** - Mouse wheel zoom and drag to pan the canvas
- **Singleton Hooks** - Duplicate hook prevention with visual feedback
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
- **Extracted Components** - `AbilityExplainer` and `HookBlock` moved to dedicated component files
- **Centralized Constants** - `HOOK_PARAMS`, `CONDITION_CATEGORIES`, `FRIENDLY_CONDITIONS` moved to `logic/constants.py`
- **New Tooltip Utilities** - `views/components/tooltip.py` with `Tooltip`, `TooltipComboBox`, `ParamInfoComboBox`, and `CodeEditorTooltip` classes
- **Reduced File Size** - `code_editor.py` reduced from ~3500 lines to ~720 lines

### UI Improvements
- **Hook Page Title** - Clear "Ability hooks" title displayed on hook/event selection page
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
- **Standardized Colors**: "Add Hook" and "Back" buttons now use a consistent blue shade.
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
- New **Battlers** category for end-of-turn hooks:
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
- **Hook Deletion** - Added "X" delete button next to each hook header for quick removal
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
- Event/Hook System with 20+ battle event types
- Script Generation for PSDK-compatible Ruby code
- Condition Library with 80+ pre-defined conditions
- Code Preview before saving
- 13 Quick Action buttons for common ability code
- Multi-language support (English, French, Spanish)
