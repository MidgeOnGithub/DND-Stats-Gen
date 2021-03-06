# Dungeons and Dragons Stats Generator

### Table of Contents
* [Disclaimers](#disclaimers)
* [Vocabulary](#vocabulary-notes)
* [CLI Usage](#cli-usage)
* [Integrated Dice Roller](#integrated-dice-roller)
* [Abilities](#abilities)
* [Saving](#saving-work)
* [Notes for Users](#notes-for-dnd-players-and-dms)
* [Notes for Developers](#notes-for-developers)

### Disclaimers
This program is not intended to represent an official *Dungeons and Dragons* nor *Wizards of the Coast* product.
All product and company names are trademarks™ or registered trademarks® of their respective holders.
Use of them does not imply any affiliation with nor endorsement by them.

External packages which are not Boost can be found in the `vendor` folder, along with their respective licenses (and the Boost license), which will be included with any Releases of this program.

### Vocabulary
* The game referenced: `Dungeons and Dragons` (`DnD`)
* Players have adventures/sessions created/led/guided by a `Dungeon Master` (`DM`)
* In gameplay, players act as a `Player Character` (`PC`)
  * `PCs` often engage with `Non-Player Characters` (`NPCs`)
* The primary reference literature for DnD standards is the `Player's Handbook` (`PHB`)

### CLI Usage
This `command-line interface` program accepts some arguments!
Use `--help` when calling the program to see the options and effects.

### Integrated Dice Roller
This program includes a dice roller which performs random dice rolls of any "ndm" type. 
> * **n** is the number of die to be rolled
> * **d** is a non-functional shorthand ("**d**ice"), spoken as just the letter 
> * **m** represents each die's face count

A wrapper `dnd_roll` accounts for special die and roll cases discussed in the PHB in pages 6 and 7, namely:
> * **d100**, an embellished combination of a percentile and d10 die
> * **d3**, the first method described, wherein the result is the ceiling of a d6 / 2
> * **d2**, wherein a rolled odd := 1, even := 2

### Abilities
DnD characters have 6 point-valued *abilities*:
> **Strength** || **Dexterity** || **Constitution** || **Intelligence** || **Wisdom** || **Charisma**

When creating their PC, the player (or their DM) must determine what point values are available to assign to their abilities.
Some of the most popular methods to generate the values involve rolling several six-sided die (d6) and summing their rolls in some fashion.
Currently, this program features two of the more standard random-value methods:
* **3d6** -- wherein the values are the sums from 6 separate *3d6* rolls
* **4d6-drop-1** -- like the 3d6 method, except 6 *4d6* rolls are performed, each with the lowest of the 4 dice discarded
  * Generally increases scores, lowering potential of generating
  dud abilities

After score generation, the program interacts with you to assign the rolled scores to a PC's abilities.

##### Future Development Notes
Assigned ability scores will eventually be affected by PC `race` chosen upon completed character creation.
Support for 2 or more races will likely not be provided.
> `Human` PCs receive +1 for all abilities,
> `Dwarf` PCs get +2 for *Constitution* only, etc.

Also, the "point buy" ability score generation method described in the PHB will be implemented.

### Saving Work
The program user may use command-line arguments to indicate that they wish (or don't wish) for the program to output a result to a `.txt` file.
If no such arguments are given, the program will offer to write out a character summary to a `.txt` file: if you accept, the program interacts with you to overwrite or create a new file.

### Notes for DnD Players and DMs
All features of the program are/will be based on the latest edition of "Dungeons and Dragons" and its *Wizards of the Coast* expansions (excluding experimental publications, such as "Unearthed Arcana").
Correct generation of game data will be handled by the submodule https://github.com/MidgeOnGithub/DnD-Data/.
The `master` branch of this repo will not attempt to account for older editions nor include third-party expansions.
If the program or code appears to have erroneously done so or has failed to account for official content, please report discrepancies.

In general, the program emphasizes the creation of characters that are legal for use by Adventurer's League (`AL`) guidelines.
Characters with properties disallowed from AL can still be generated if it falls within PHB rules; incompliance with AL will be noted in program output(s).

### Notes for Developers
#### Submodules
This repo makes use of git `submodules`.
Thus, when cloning this repo, assuming a version of git >= 2.13, use `recurse-submodules` to automatically populate submodules:
* `git clone --recurse-submodules -j4 git://github.com/MidgeOnGithub/DnD-Stats-Gen.git`

With older versions of git or if you prefer a two-step process:
* `git clone git://github.com/MidgeOnGithub/DnD-Stats-Gen.git`
* cd into the repo directory
* `git submodule update --init --recursive`

See https://stackoverflow.com/a/4438292/10466817 for more details.
#### Dependencies
Third-party licenses are included in the `vendor` folder.
Boost, GoogleTest, and nlohmann's JSON are included into the project using CMake's `find_package` command.
Consult other sources for information about how to install them for your OS.

Links:
* https://www.boost.org/
* https://github.com/google/googletest
* https://github.com/nlohmann/json
