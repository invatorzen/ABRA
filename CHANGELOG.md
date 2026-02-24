# Changelog

All notable changes to A.B.R.A. (Ability Builder & Refinement Assistant) will be documented in this file.

## 0.4.1 - 02/24/2026

### Visual Builder Improvements

- [Fix] **Set Effect Counter** - Fixed a bug where providing a counter value in the "Set Effect" action would cause a code generation error.
- [Feature] **Expanded Set Effects** - Added support for Perish Song.
- [Feature] **Summary Improvement** - Updated the "Set Effect" node summary to include turn counts (e.g., "for 3 turns") for better clarity.
- [Feature] **Form Change Animation Coupling** - "Change Form" nodes now automatically create and connect a "Show Change Form Animation" node when generated, ensuring visual consistency.

### UI & UX

- [Added] **Discord Community Link** - Added a direct link to the official Discord support server on the home screen ("Recent Projects" row) for easier access to help and community.

---

## 0.4.0 - 02/15/2026

### Visual Builder Improvements

- [Feature] **Node Copy-Paste** - Implemented the ability to copy and paste nodes using `Ctrl+C` and `Ctrl+V`.
- [Feature] **Connection Preservation** - Connections between selected nodes are automatically captured and restored when pasted.
- [Feature] **Hook Node Metadata Display** - Parameter names and return types are now displayed directly on hook node headers for better context.
- [Added] **Move History Conditions** - Added specific conditions for launcher's last move category (Physical/Special/Status) and repeated move checks.
- [Feature] **Context Menu Integration** - Added "Copy" and "Paste" options to both the main canvas and individual node context menus.
- [Feature] **Intelligent Pasting** - Supports relative spatial offsets, singleton node protection, and full parameter persistence.
- [Added] **Random Choice Node** - Added a new utility node for creating probabilistic branching logic with dynamic output sockets.
- [Added] **Base Stat Comparisons** - Added 12 new conditions for comparing target/attacker base stats (Atk, Def, Sp.Atk, Sp.Def, Spd, and BST) in the Visual Builder.
- [Fix] **Intelligent Parameter Mapping** - Updated aliases to treat `user`/`launcher` and `target`/`who` as interchangeable, ensuring conditions appear correctly across all hook types.
- [Fix] **Ability Summary Logic** - Fixed misleading explanations for return values, added support for inline `if`/`unless`, and implemented descriptive naturalization for technical symbols (e.g., `:atk` → attack).
- [Fix] **Safe Debouncing** - Fixed a critical `ValueError` crash when cancelling pending updates during rapid typing.
- [Fix] **Label Rendering** - Fixed a crash caused by the unsupported `line_spacing` attribute in some UI labels.
- [Added] **Summary Translation Specialization** - New `sum_` translation prefix system allowing conditions to have more descriptive phrasing specifically for the summary panel.

### New Hooks

- [Added] **Hazard Immunity Hook** - Added support and auto-installation for the `on_ignore_hazards?` hook.
- [Added] **New Status Hooks** - Added `on_poison_damage` and `on_burn_damage` hooks with auto-installation and UI categorization.

### Features & Infrastructure

- [Added] **BST Helper Method** - Added `PFM::Pokemon#base_stat_total` to provide easy access to Base Stat Total in your scripts and the Visual Builder.
- [Feature] **Directory Standardization** - Refined script structure to use `00001 Effects` as the primary container for ABRA-generated logic.
- [Feature] **Smart Suggestions** - Move history categories and `skill`/`move` conditions are prioritizing when relevant parameters are available.
- [Feature] **Instance Variable Discovery** - Graph-defined instance variables (`@var`) are now automatically detected and suggested in the Quick Suggestions panel.

### Workflow & Productivity

- [Added] **Save Shortcut (Ctrl+S)** - Added a global `Ctrl+S` shortcut to trigger the "Update Ability" / "Finish" action from anywhere in the editor.
- [Fix] **Save Flow Stability** - Fixed a bug where cancelling the save preview would leave the application in a broken state.
- [Fix] **Modal Hardening** - Shortcuts and duplicate triggers are now correctly ignored when modal dialogs or preview panels are active.

### Instance Variables

- [Added] **Instance Variable Node** - Added "Set Variable (@)" node to persist state across hooks (e.g., `@my_flag`).
- [Feature] **Variable Suggestions & Conditions** - Discovered variables automatically appear in Quick Suggestions and the Condition Picker dialog.

### Ability Management & UI Refinements

- [Feature] **Manage Abilities Enhancements** - Made the Manage Abilities screen more compact.
- [Feature] **Official PSDK Descriptions** - Abilities now pull localized descriptions directly from the project's official CSV files (`100005.csv`).
- [Added] **Script Order Sorting** - Added "Script Order" as the default sorting method to match the official PSDK database order.
- [Feature] **Sort Direction Toggle** - New ascending/descending toggle (↑/↓) for all sorting methods with icon indicators.
- [Feature] **Persistent Preferences** - Sorting methods and directions are now automatically saved and restored from the user configuration.
- [Feature] **Missing Description Placeholder** - Replaced technical summaries with a clean `(Missing description)` localized placeholder for unfinished abilities.
- [Fix] **Home Screen Layout** - Resolved critical layout gaps on the Project Selector screen by fixing row weight distribution and tightening card padding.
- [Fix] **Encoding Robustness** - Hardened translation and CSV loading to automatically handle multiple encodings (UTF-8, Windows-1252, Latin-1), preventing crashes on special characters.

---

## 0.3.5 - 02/07/2026

### Visual Builder Improvements

- [Feature] **Quick suggestions** - A new stop/return/if quick action section has been added to the suggestions panel. It now intelligently target the active or last selected hook when multiple hooks are present.
- [Feature] **Active Hook Tracking** - Implemented robust tracking for the "active" hook instance based on user selection, ensuring actions match user intent.
- [Fix] **Dynamic Parameter Substitution** - Quick suggestions now correctly display actual parameter names (e.g., "Move" instead of "Skill") including proper capitalization for UI labels.
- [Fix] **Visual Hook Persistence** - Fixed a bug where adding a new hook would cause existing empty hooks to be deleted; all hooks on canvas are now preserved.

### Features

- [Added] **Move Effectiveness Hook** - Added `on_effectiveness_multiplier` hook that allows abilities to modify move effectiveness (e.g., return `2.0` for double effectiveness).
- [Feature] **Hook Auto-Installation** - ABRA now automatically installs the `EffectivenessMultiplier` PSDK extension script if missing in the project.

---

## 0.3.4 - 02/07/2026

### UI/UX

- [Fix] **Hook Name Text** - All hooks were showing incorrect text due to previously being "triggers" instead of "hooks".
- [Fix] **Standardized Node Labels** - Standardized all node labels to match their Ruby hook names exactly (e.g., "On Pre Item Change" instead of "Pre-Item Change").
- [Fix] **Expanded Abbreviations** - Expanded all shorthand like "Prev" to "Prevention" across English and French translations for maximum clarity.

### Features

- [Added] **New Hook Categories** - Added and translated the new `cat_transform`, `cat_items`, and `cat_ability` categories.

---

## 0.3.3 - 02/05/2026

### UI/UX

- [Added] **"What's New" Dialog** - Modernized update notification dialog.
- [Added] **Rich Text Release Notes** - Support for nested bullet points and indentation.
- [Added] **Tag Highlighting** - Automatic color highlighting for tags like [Added], [Fix], [Feature].
- [Added] **Visual Badges** - Colored version badges and improved action buttons.

### New Features

- [Added] **New Battle Hooks Integration** - Added 4 hooks from PSDK's `EffectBase.rb` for advanced ability building:
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
