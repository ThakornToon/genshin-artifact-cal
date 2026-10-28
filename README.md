# Genshin Impact Artifact Calculator

A small web tool for evaluating Genshin Impact artifacts one piece at a time and checking drop chances.
The interface supports Thai and English (switch languages at the top right).

## Why this exists

I built this for my own use, to make checking individual artifacts easier without keeping notes or doing the math by hand. It lets me:

- Enter the substat values I see in-game, simulate how many times each one was upgraded, and see the final Lv.20 values.
- Mark which substats my character actually uses, and get a score and grade (Weak to Excellent).
- Check how rare a specific piece is (piece type + main stat + substats).

This project was built with **Claude** (Anthropic), which helped write the code and explain the calculations.

## How to run

No installation needed. It is a single HTML file.

## How to use

### "Stat calculator" tab

1. Choose the artifact piece type and main stat.
2. Choose whether the artifact started with 4 substats or 3.
3. Pick each substat and its initial value to match what the game shows.
4. Click "+ Upgrade" on each substat that was upgraded, then choose the rolled value (use "avg" if you do not know it).
5. Tick "Character uses this" on the substats your character wants.
6. Read the Lv.20 summary, RV score, grade, and Crit Value.

### "Drop chance" tab

1. Choose the piece type and main stat.
2. Choose the substats you want (up to 4).
3. Choose the start condition (Any / 4 at Lv.1 / 3 at start).
4. Read the chance as a percentage and as "1 in N", plus how many drops it takes to reach a 50% chance.

### "Guide" tab

Explains every formula and data table: per-roll values, upgrade rules, Lv.20 main stat values, RV, Crit Value, selection weights, and a worked example.

## Formulas in brief

```
Final substat value = initial value + sum of all upgrade rolls
RV                  = stat total / max single-roll value x 100%
Crit Value          = CRIT Rate x 2 + CRIT DMG
Drop chance         = 1/5 x P(main stat) x P(has wanted substats) x P(start condition)
```

## Limitations

- 5-star artifacts only.
- Selection weights and drop rates come from community-gathered data. They have not been verified against an official source and may change with game updates.
- The grade thresholds (RV / Crit Value) are general guidelines, not values defined by the game.
- Probabilities cover only which substats appear, not where upgrades land or which value tier they roll.
- Totals may differ from the game by about 0.1 because of rounding.

## File structure

```
index.html   # All code (HTML + CSS + JavaScript) in one file
README.md   
```

## Editing the data

Game data sits at the top of the `<script>` block in `index.html`:

- `S`: per-roll values, selection weights, and descriptions for each substat
- `M`: main stat values at Lv.20
- `T`: piece types and main stat chances

If the game changes these numbers, edit these three variables directly.

## Credits

Built with the help of Claude (Anthropic). Genshin Impact is a trademark of HoYoverse. This is a fan-made tool and is not affiliated with HoYoverse.
