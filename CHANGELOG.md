# Changelog

All notable changes to A.B.R.A. (Ability Builder & Refinement Assistant) will be documented in this file.

## 0.3.5 - 02/07/2026

### Visual Builder Improvements
- [Feature] **Quick suggestions** - A new stop/return/if quick action section has been added to the suggestions panel. It now intelligently target the active or last selected hook when multiple hooks are present.
- [Feature] **Active Hook Tracking** - Implemented robust tracking for the "active" hook instance based on user selection, ensuring actions match user intent.
- [Fix] **Dynamic Parameter Substitution** - Quick suggestions now correctly display actual parameter names (e.g., "Move" instead of "Skill") including proper capitalization for UI labels.
- [Fix] **Visual Hook Persistence** - Fixed a bug where adding a new hook would cause existing empty hooks to be deleted; all hooks on canvas are now preserved.

### Features
- [Feature] **Move Effectiveness Hook** - Added `on_effectiveness_multiplier` hook that allows abilities to modify move effectiveness (e.g., return `2.0` for double effectiveness).
- [Feature] **Hook Auto-Installation** - ABRA now automatically installs the `EffectivenessMultiplier` PSDK extension script if missing in the project.

---

## 0.3.4 - 02/07/2026

### UI/UX
- [Fix] **Hook Name Text** - All hooks were showing incorrect text due to previously being "triggers" instead of "hooks".
- [Fix] **Standardized Node Labels** - Standardized all node labels to match their Ruby hook names exactly (e.g., "On Pre Item Change" instead of "Pre-Item Change").
- [Fix] **Expanded Abbreviations** - Expanded all shorthand like "Prev" to "Prevention" across English and French translations for maximum clarity.

### Features
- [Feature] **New Hook Categories** - Added and translated the new `cat_transform`, `cat_items`, and `cat_ability` categories.

---

## 0.3.3 - 02/05/2026

### UI/UX
- [Added] Modernized "What's New" update notification dialog.
- [Added] Support for nested bullet points and rich text indentation in release notes.
- [Added] Automatic color highlighting for tags like [Added], [Fix], [Feature].
- [Added] Colored version badges and improved action buttons.

### New Features
- [Feature] **New Battle Hooks Integration** - Added 4 hooks from PSDK's `EffectBase.rb` for advanced ability building:
  - **Secondary Effect Multiplier** (`effect_chance_modifier`) - Under Accuracy category.
  - **On Drain Prevention** (`on_drain_prevention`) - Under Damage category.
  - **On Type Multiplier Overwrite** (`on_single_type_multiplier_overwrite`) - Under Multipliers category.
  - **Specific Procedure Override** (`specific_proceed_internal`) - Under Prevention category.
- [Feature] **Hook Visual Nodes** - Created and registered visual nodes for all 4 new hooks, making them immediately available in the Visual Builder.
- [Feature] **Auto-Updater** - Implemented a built-in update system that automatically checks for new versions on startup via GitHub integration.

### Improvements
- [Fix] **Hook Parameter UI Refinement** - Restored original aesthetic for the Hook Selector: parameter subtitles are now hidden for hooks without parameters.
- [Fix] **Standardized Node Sizes** - New hook nodes automatically use the standard 220x75 dimensions.
- [Added] **Localization Expansion** - Added full English, French, and Spanish translations for the new hooks.

---

## 0.3.2 - 02/03/2026
### Alignment
- [Feature] **Triggers to Hooks Alignment** - Renamed all project-wide references of "triggers" to "hooks" to align with PSDK terminology.
- [Added] Support for `on_pre_accuracy_check` hook.

### Visual Builder Refinement
- [Added] **Precise Node Connections** - Connection points now align with the center of "○" and "●" icons.
- [Added] **Vertical Socket Centering** - Implemented automatic vertical centering for sockets.
- [Added] **Edge-Aligned Connections** - Connection lines now attach directly to the absolute left and right edges.
- [Fix] **Resizing Stability** - Fixed node resizing logic to be correctly scale-aware.

---

## 0.3.1 - 02/01/2026
### Features
- [Feature] **Bypass Hit Chance Hook** - New `on_bypass_chance_of_hit?` hook allows abilities to guarantee moves hit.
- [Added] **Hook Installation Check** - ABRA now checks for required hook scripts on project load and auto-creates them.
- [Feature] **Node Editing** - Double-click or right-click → "Edit Node..." on action nodes to open dialogs pre-filled with current values.

### Improvements
- [Added] **Context Menu Cleanup** - Removed "Stop Ability" and "Return Value" from the top of the right-click menu.
- [Added] **Context-Aware Scene Prefix** - `show_ability` and `wait_for_animation` nodes now generate the correct prefix based on hook context.
- [Added] **Script-to-Visual Sync** - When switching from Script to Visual tab, existing nodes now update their parameters.
- [Added] **Show Ability Quick Action** - Now creates two connected nodes (Show Ability Popup + Wait For Animation).
- [Fix] **Show Ability Node Size** - Increased default size for better visibility.

### Bug Fixes
- [Fix] **Hook Detection** - Fixed connection option filtering for hooks with `cat_*` categories.
- [Fix] **Metadata Loading** - Fixed node positions not being restored when editing abilities.
- [Fix] **Metadata Saving** - Fixed critical bug where metadata was never saved when editing abilities.

---

## 0.3.0 - 01/28/2026

### New Features

#### Visual Node Editor
- [Added] **Node-Based Logic Builder** - Create ability logic by connecting visual nodes instead of writing Ruby code
- [Added] **Hook Nodes** - 25+ hook types available as draggable nodes with automatic categorization
- [Added] **Action Nodes** - Visual nodes for HP changes, stat changes, status effects, weather, terrain, and more
- [Added] **Condition Nodes** - If/Unless blocks with branching logic (true/false paths)
- [Added] **Utility Nodes** - Raw code, comments, stop ability, and return value nodes
- [Added] **Smart Connections** - Drag to connect nodes with automatic socket matching
- [Added] **Node Positioning** - Drag nodes to reposition, positions saved with ability metadata
- [Added] **Zoom & Pan** - Mouse wheel zoom and drag to pan the canvas
- [Added] **Singleton Hooks** - Duplicate hook prevention with visual feedback
- [Added] **Tab Sync** - Visual and Script tabs stay synchronized when switching

#### Enhanced Message Nodes
- [Added] **Three Message Types**:
  - Raw text messages
  - CSV-based messages (file_id + text_index)
  - Pokémon variable messages with target substitution

---

## 0.2.5 - 01/12/2026

### New Features

#### Code Editor Enhancements
- [Added] **Keyboard Shortcuts**:
  - `Ctrl+D` - Duplicate current line
  - `Ctrl+/` - Toggle comment on current line
  - `Ctrl+Shift+Up/Down` - Move line up/down
  - `Ctrl+L` - Select entire current line
  - `Ctrl+Shift+V` - Smart paste with auto-formatting
  - Full undo/redo support
- [Added] **Auto-Close Brackets & Quotes** - Typing `(`, `[`, `{`, `"`, or `'` automatically inserts the closing character
- [Added] **Matching Bracket Highlight** - Visual highlighting of matching brackets when cursor is on one
- [Added] **Line Numbers** - Click to toggle between file-level and editor-relative numbering
- [Added] **Dynamic Editor Height** - Editor automatically grows/shrinks based on content, even on backspace
- [Added] **Code Hover Tooltips** - Hover over parameters like `@target`, `handler`, `launcher` to see descriptions

#### Ability Summary Panel
- [Added] **Natural Language Explanations** - Real-time summary panel that translates your Ruby code into human-readable descriptions
- [Added] **Live Updates** - Summary automatically updates as you type code
- [Added] **Action Recognition** - Recognizes stat changes, HP modifications, status effects, type changes, weather/terrain, and more
- [Added] **Condition Translation** - Converts Ruby conditions to readable phrases (e.g., `@target.hp_rate <= 0.5` → "when HP ≤ 50%")

#### Parameter Info Tooltips
- [Added] **Visible Info Labels** - All target dropdowns now show an info label below explaining what the selected parameter means
- [Added] **17 Parameters Documented** - Descriptions for `@target`, `target`, `launcher`, `user`, `who`, `with`, `pokemon`, `skill`, `handler`, `logic`, `scene`, `hp`, `stat`, `status`, `power`, `reason`, `priority`

#### Ability Overwrite Confirmation
- [Added] **Confirmation Dialog** - When creating an ability that already exists, you're now prompted to confirm overwriting
- [Added] **Safe Updates** - Prevents accidental overwrites of existing abilities

### UI Improvements
- **Hook Page Title** - Clear "Ability hooks" title displayed on hook/event selection page
- **Slightly Larger Dialogs** - Dialog heights increased to accommodate info labels

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
- **Centered Icons**: Fixed vertical centering for the trash can icon on the Ability Manager page.

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
