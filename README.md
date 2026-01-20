# omarchy-screensaver-configs

Personal configuration set for the **Omarchy screensaver**, including:

* custom `tte` effects selection
* monochrome / themed color setups
* custom ASCII art inputs

This repo is meant to be **simple, safe, and reversible**.


## What this repository contains

* 🖥 **Custom `omarchy-cmd-screensaver` script**
* 🎨 **Screensaver-only Alacritty color themes**
* 🧾 **ASCII art files** used as input for `tte`
* 🧩 List of `tte` effects (enabled / commented)

Nothing here modifies Omarchy globally unless you explicitly copy it.


## Changing screensaver ASCII art

The screensaver reads an input file, usually:

```bash
~/.config/omarchy/branding/screensaver.txt
```
You can replace this file anytime — no restart required.


## Selecting which effects are used

Inside my `omarchy-cmd-screensaver` you will find:

```bash
EFFECTS=(
  middleout
  matrix
  rain
  decrypt
  randomsequence

  # beams
  # bubbles
  # fireworks
  # waves
)
```

* Enabled effects are **uncommented**
* Disabled effects are **commented**
* Just comment/uncomment what you want

No other logic needs to be touched.


## Making the screensaver monochrome or themed

### Text color (foreground)

Controlled by **Alacritty**, not `tte`.

Edit:

```
~/.local/share/omarchy/default/alacritty/screensaver.toml
```

Example:

```toml
[colors.primary]
background = "0x111111"
foreground = "0x424443"
```

This affects **only the screensaver terminal**.

I made some color schemes you can choose


### Disabling `tte` colors

Already handled in the script:

```bash
--no-color
```

This ensures:

* ASCII inherits terminal foreground
* no rainbow / animated colors
* consistent look across effects


## Adding new ASCII files

You can swap the input file freely.

Example:

```bash
cp ascii/ak.txt ~/.config/omarchy/branding/screensaver.txt
```

Or modify the omarchy-cmd-screensaver script to randomly choose ASCII files if you want.


## Notes & limitations

* `matrix` effect **does not fully respect input size** (this is a TTE limitation as far as i know)
* Canvas dimensions are in **terminal characters**, not pixels
* This repo does **not** patch `tte` itself

All configs here work within those constraints.


## Philosophy

* minimal changes
* no hacks that break things or exit logic
* readable scripts
* easy rollback


## License
Do whatever you want.
Configs are meant to be copied, modified, and broken.


## Contributing

Contributions are welcome if you want to improve or expand this repository.

You can help by:

* adding new ASCII art files (please test it before, some asciis don't work too well)
* sharing clean color themes for the screensaver
* suggesting good `tte` effect combinations
* improving documentation or examples
* fixing edge cases while keeping configs simple and stable

### Guidelines

* Keep changes **focused on the screensaver only**
* Avoid hacks that break focus handling, exit logic, or performance
* Prefer **readable Bash** over clever tricks
* Do not add dependencies outside what Omarchy already uses
* If you add a new effect or behavior, document it clearly

### How to contribute

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test them in Omarchy
5. Open a pull request with a short explanation

This repo is meant to stay **minimal, stable, and easy to customize**.


