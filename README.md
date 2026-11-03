# Agelessones First Mod

A big quality-of-life and automation mod for **Valheim 1.0 "Deep North"**, built on **BepInEx 5 / HarmonyX**.

It adds chest automation (auto-feeding smelters, auto-sorting, chest search), extra inventory slots (gear, quiver, quick slots, recycle and trash), a safer "red hammer" for clearing world ruins, armor colours and cape effects, weapon enchants, skill-based speed and carry weight, and many smaller conveniences.

- **Plugin GUID:** `AgelessOne`
- **Config file:** `BepInEx/config/AgelessOne.cfg` (created on first start; every feature below has its own on/off switch)
- **Tested against:** Valheim 1.0.20 (Deep North)
- **Version history:** see [`CHANGELOG.md`](CHANGELOG.md)

> **Heads-up: the defaults are generous.** Many features ship switched on and tuned for a relaxed, "cheaty" game (infinite stamina, 1500 carry weight, 5x skill XP, instant loot). If you want something closer to vanilla, change the values in `AgelessOne.cfg` (see [Tuning it down](#tuning-it-down)).

---

## Contents

1. [Install](#install)
2. [Multiplayer notes](#multiplayer-notes)
3. [Hotkeys at a glance](#hotkeys-at-a-glance)
4. [Features](#features)
   - [Chests and storage](#chests-and-storage)
   - [Automation](#automation)
   - [Inventory, slots and gear](#inventory-slots-and-gear)
   - [Building](#building)
   - [The Red hammer](#the-red-hammer)
   - [Combat, staffs and magic](#combat-staffs-and-magic)
   - [Player, skills and survival](#player-skills-and-survival)
   - [Looks](#looks)
   - [Other](#other)
5. [Admin tool (separate plugin)](#admin-tool-separate-plugin)
6. [Tuning it down](#tuning-it-down)
7. [Troubleshooting](#troubleshooting)
8. [Building from source](#building-from-source)

---

## Install

1. Install **BepInEx 5** for Valheim (the "BepInExPack Valheim" package is the easy way).
2. Start the game once so BepInEx creates its folders, then close it.
3. Copy the built `AgelessonesFirstMod.dll` into `BepInEx/plugins/`.
4. Start the game. `BepInEx/config/AgelessOne.cfg` is created. Edit it (with the game closed) to turn features on or off.

**Before you remove the mod or switch off Gear Slots / Quick Slots**, empty those slots first. Items sitting in them are lost on the next load.

## Multiplayer notes

- Everyone on the server should run **the same version** of this mod. Two different versions can fight over who "owns" smelters, chests and dropped items.
- Features that act on your own character (slots, speed, carry weight, recycling) are per player.
- Armor colours and cape effects are visible to other players **who also have the mod**.

## Hotkeys at a glance

All of these can be changed in the config.

| Key | What it does |
|---|---|
| **Hold Left Shift** while hitting | Vein mining and one-hit tree felling |
| **Delete** (over an item) | Recycle that item |
| **Keypad 1 / 2 / 3** | Eat or drink what is in quick slot 1 / 2 / 3 |
| **B** (while placing) | Grid snapping on or off |
| **End** | Teleport back to where you died (for a limited time after respawn) |
| **Page Down** | Duplicate cleaner (press once to count, again to remove) |
| **Ctrl + F** (chest open) | Jump to the chest search box |
| **Middle mouse** (Red hammer) | Remove the piece you look at |
| **Shift + middle mouse** (Red hammer) | Remove the whole structure |
| **Middle mouse** (Dead Raiser in hand) | Dismiss summoned creatures |

---

## Features

Every feature has an `Enable...` switch in its own numbered section of `AgelessOne.cfg`. The section number is given in brackets.

### Chests and storage

**Crafting from nearby chests** [2]
Crafting and building take materials from chests near you, so you do not run back and forth with items. *Why:* the single biggest time saver in a large base. Range is configurable (default 30 m).

**Auto sort** [10]
When you close a chest, items you put in it move to a nearby chest that already holds that item. A soft sound and glow show where they went. *Why:* chests stay organised without you sorting by hand.

**Station output to chests** [11]
Smelters, kilns, furnaces, cooking stations and sap extractors send their output into a nearby chest (first one that already holds that item) instead of dropping it on the ground. *Why:* no more loot piles around your stations.

**Fuel chests** [13]
A small button in the chest window marks a chest as a **fuel chest**. Smelter fuel, a charcoal kiln's wood, a Frost Kiln's ice and shield generator fuel are taken only from marked chests. *Why:* your ore chests stay full of ore and your fuel chests do the feeding, so nothing important is burned by accident.

**Shared chest access** [13]
Two players can have the same chest open at once. *Why:* the game normally locks a chest to one player. Both players moving items in the exact same moment can still clash, so avoid that.

**Chest stacking** [32]
Place a chest on top of another chest. Aim at the top of a chest with a chest selected. *Why:* the game normally refuses to place on a chest; this lets you build compact storage walls.

**Chest names** [23]
A "Name chest" button in the chest window. The names float over chests (optionally visible through walls) and are hidden behind menus. *Why:* find the right chest from across the base. Colour, size, distance and through-wall behaviour are configurable.

**Chest search** [33]
A search bar to the right of the chest window. Type an item name and every nearby chest that holds it flashes (the chest glows and its name and distance appear on screen) for 30 seconds or until you open it. You can pull a chosen amount of the item straight into your inventory, and recent searches are remembered. *Why:* finding "iron ingots" in 40 chests without opening each one. The glow only lights the chest, not the area around it.

### Automation

**Smelter, kiln and station auto-feed** [5]
Smelters, kilns, blast furnaces and the Frost Kiln are fed fuel and ore from nearby chests. The feed checks that the station really took the item, and puts it back in the chest if it did not, so nothing is lost. *Why:* smelting while you do something else. Fuel only comes from your marked fuel chests (see above).

**Shield generator feed and bubble** [5]
Shield generators near you are kept fuelled from fuel chests, and (optionally) a running generator destroys hostile creatures that touch its bubble. Players, tamed animals and harmless animals are never hurt. Bosses are only affected if you switch that on.

**Cooking station auto-harvest** [5]
Food is taken off cooking stations before it burns. *Why:* no more burnt meat.

**Infinite fuel** [5]
Lit campfires, bonfires, hearths, braziers and torches (also the one you hold) never run out. Unlit ones stay unlit.

**Loot vacuum** [5]
Dropped items fly into your inventory when you are close (default 7 m). It stops when you are at your carry limit.

**Instant loot** [14]
Creatures drop their loot the moment they die instead of after the corpse fades.

**Vein mining and one-hit trees** [5]
Hold Left Shift while mining a node to break the whole node, or while swinging an axe to fell a tree (and chop its logs) in one hit.

**Sleep restrictions removed** [5]
You can sleep with enemies nearby, while exposed, wet or with no fire.

**Weather protection and sturdy buildings** [5, 9]
No rain decay on unroofed pieces. A structural mode of Vanilla, Stronger (default) or Unlimited lets you build further and higher. Indestructible buildings is a separate switch, off by default.

### Inventory, slots and gear

**Gear slots** [7]
A row of locked slots under the inventory for helmet, chest, legs, cape, utility, trinket and quiver. Items placed there are worn automatically, and right-click moves gear into its slot. *Why:* gear stops taking up bag space.

**Quiver** [7]
A seventh gear slot that holds one kind of arrow or bolt (up to 500 by default); your bow shoots from it.

**Quick slots** [17]
Three food and potion slots with their own HUD icons and hotkeys (Keypad 1-3). Right-click food to move it into a free slot.

**Recycle and trash slots** [3]
Drag an item onto the RECYCLE cell to break it down into its materials (percentage configurable), or onto TRASH to delete it. Delete over an item also recycles it. Cells that cannot hold an item (the recycle and trash cells) are kept clear on login.

**Inventory sort** [21]
A Sort button above the inventory merges stacks and orders items; your hotbar row is left as it is.

**Death** [8]
Keep your inventory, food and skills on death, and a teleport back to where you died for a limited time (default 60 seconds after respawn).

### Building

**Long build range and repair** [9]
Place, remove and repair from up to 50 m. One hammer repair click repairs every player-built structure in a radius.

**Grid snapping and farm grid** [19]
Press **B** while placing to snap furniture and chests to a grid. Plants snap to a farming grid sized from how much room each plant needs, with an optional on-screen grid.

**Workbench changes** [6]
Larger workbench and station radius (30 m), stations usable without a roof, and station upgrades (chopping block, tanning rack and so on) count at any distance and can be built anywhere.

**Fireplaces anywhere** [9]
Campfires, hearths and braziers can be placed on wood, slopes, in water, in dungeons and in any biome.

**Plant anywhere** [26]
Crops and seeds grow in any biome.

**Transparent sails and remove any piece** [20]
Sails become see-through. The normal hammer can remove any player-built piece, including boats and carts.

**Feather collector** [22]
A buildable container (Furniture tab) that slowly fills with feathers while a tree is nearby, so you do not need to hunt birds. Ambient birds can also be removed.

**Chain recipe** [24]
Craft Chain at the forge from iron.

### The Red hammer

**Red hammer** [28] is a craftable copy of the build hammer, painted red. It is a **world-clearing tool**:

- It removes **anything the world made** (ruins, fortresses, Deep North structures, loose breakable parts).
- It **never touches anything a player built or placed**. A message tells you when you aim at one.
- **Middle mouse** removes only the piece you are looking at. **Shift + middle mouse** removes the whole structure.
- Everything it removes **drops its resources** (pieces drop their materials, rocks and loose parts drop their loot).
- It needs **no workbench and no build menu** to work.
- A large structure comes down in stages (a few pieces at a time) so the game does not stutter. Speed is set by `PiecesPerStep` and `StepSeconds`.

*Why:* clearing out ruins for their materials without risking your own base. Wards are respected by default (`RespectWards`).

### Combat, staffs and magic

**Weapon enchants** [27]
An Enchant tab at the forge. Pick a weapon and an effect: fire, frost, lightning, poison, spirit (extra damage as a % of the weapon's damage) or life steal. Each costs materials and coins, scaling with the weapon's damage. Enchanted weapons glow.

**Eitr armor** [29]
Wearing mage armor gives you eitr without eating (more with upgrades), and spells can be made free.

**Dead Raiser levels** [30]
The skeleton staff summons different creatures by upgrade level: random land creatures (2), mini bosses (3), and stronger mini bosses (4). Summons are tamed, friendly to players, follow you, drop no loot by default and fade after a while. Middle click dismisses them.

**Dundr** [31]
The lightning staff costs no eitr, and its damage and reload speed grow with your Elemental Magic skill.

**Trollstav** [34]
The trolls summoned by the troll staff no longer attack players (in vanilla they attack everything nearby, including you). They still fight everything else.

**Lightning Strike staff** [37]
A best-effort setting that tries to make the strikes land where you point instead of scattered. It removes the random spread values of the staff's attack. The game's values for the staff are written to the log once, so the fix can be refined if it is not enough.

**Boss powers** [16]
Cooldown and duration multipliers for your active boss power (defaults: a quarter of the cooldown, twice the duration).

### Player, skills and survival

**Skill speed** [35]
Running and swimming get faster as the Run and Swim skills rise (up to +15% running and +50% swimming at skill 100 by default), on top of the game's own bonus.

**Skill carry weight** [36]
Carry weight grows with a skill (Run by default) up to a multiplier at skill 100 (default x2). It works on your custom starting carry weight, and leaves belts like the Megingjord alone.

**Player cheats** [4]
Infinite stamina and a custom maximum carry weight. Both are on by default; switch them off for a fairer game.

**Progression** [18]
Skill XP multiplier (default 5x) and food duration multiplier (default 2x).

**Swimming** [9]
Keep your weapon, shield and torch in hand while swimming.

### Looks

**Armor colours** [25]
A Colours button in the inventory opens a palette to recolour your chest, legs, helmet and cape. Effects: colour, poison, fire, blood, frost, and for the **cape only** *Frostfire* (ice and flame trading places) and *Thunderblood* (dark red struck by lightning). Dimmer, size and smoke sliders control how strong they look. Armor glow is off by default; cape smoke is on.

**Visuals** [12]
A gamma (brightness) setting that lifts dark scenes and night, and a fog slider (0 = none).

### Other

**Duplicate cleaner** [15]
For worlds hit by the duplication bug: press Page Down to count duplicated buildings, chests, creatures, trees and rocks near you, press again to remove them. Tamed creatures are skipped.

**Performance and logging** [1]
- `LogSlowFeatures` writes a line like `[Perf] SmelterAutoFeed took 6.2 ms` when one of the mod's background jobs is slow. Useful for finding stutter; turn it off when everything is smooth.
- `HideOwnerLogSpam` hides a noisy game log line about ownership changes.

---

## Admin tool (separate plugin)

`AgelessOneAdmin.cs` is a second, optional plugin for server owners and testers. It opens a window with **F8**:

- Fly, heal, god mode
- A categorised "spawn any item" menu
- Weather control
- Teleport anywhere, or a player to you / you to a player (F9 teleports to the crosshair; Ctrl + click on the map)
- Kill everything within 500 m except players
- A terrain tool: round or square flatten, raise and lower beyond the normal limits (bookmarks are saved to a file)

It is built for Deep North. Use it carefully on a shared server.

## Tuning it down

Open `BepInEx/config/AgelessOne.cfg` with the game closed. Good places to start:

| Setting | Default | For a milder game |
|---|---|---|
| `[4] EnableInfiniteStamina` | true | false |
| `[4] CustomCarryWeight` | 1500 | 300 |
| `[18] SkillXpMultiplier` | 5 | 1 to 2 |
| `[35] RunSpeedBonusAtMax` / `SwimSpeedBonusAtMax` | 0.15 / 0.5 | 0 |
| `[36] MultiplierAtSkill100` | 2 | 1 |
| `[16] CooldownMultiplier` | 0.25 | 1 |
| `[9] StructuralIntegrityMode` | Stronger | Vanilla |

## Troubleshooting

- **Something stutters:** keep `LogSlowFeatures` on, play for a while, and look for `[Perf]` lines in `BepInEx/LogOutput.log`.
- **Items missing from gear or quick slots after removing the mod:** empty those slots *before* disabling them.
- **A smelter is not being fed:** check that the fuel chest is marked (button in the chest window), within `FuelChestRange`, and that the log shows `[SmelterFeed]` lines.
- **Another player's mod versions differ:** match versions; mismatches cause ownership fights over chests and smelters.
- **After a Valheim update, a feature stops working:** check the log for `[Feature]` warnings and report the game version and log. Game updates can change internal calls, and the mod needs a matching update.

When reporting a bug, include your game version, the mod version (shown in the log as `Loading [Agelessones First Mod x.y.z]`) and the relevant part of `LogOutput.log`.

## Building from source

The source is a single `FirstModPlugin.cs` (or the same code split into one file per feature in `AgelessOne_src/`; use one or the other, never both).

1. Create a .NET Framework 4.7.2 class library.
2. Reference BepInEx (`BepInEx.dll`), `0Harmony.dll`, and the game's assemblies from `valheim_Data/Managed` (use the publicized assemblies if you have them).
3. Add the source file(s) and build.
4. Copy the resulting DLL to `BepInEx/plugins/`.

Keep `ModVersion` in `FirstModPlugin.cs` in sync with the top entry of `CHANGELOG.md`.

## Credits and license

Made for personal use and shared as-is, with no warranty. Valheim is a trademark of Iron Gate AB; this mod is not affiliated with or endorsed by them. Add the license of your choice here before publishing.
