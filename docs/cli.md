# CLI

## Installing

!!! question "Do you have Libre Office installed?"

    === "No"
        SVG to PPT can install Libre Office `7.1.0` for you.

        Copy-paste this command in macOS Terminal or a terminal emulator:

        ``` bash
        curl -s https://raw.githubusercontent.com/blakegearin/svg-to-ppt/main/src/install_svg_to_ppt.sh | bash -s -- -i basic
        ```

        If you want to install Libre Office yourself you can download it from [their website](https://www.libreoffice.org/download/download) or use Homebrew:

        ``` bash
        brew install --cask libreoffice
        ```

    === "Yes"

        Copy-paste this command in a macOS Terminal or a terminal emulator:

        ``` bash
        curl -s https://raw.githubusercontent.com/blakegearin/svg-to-ppt/main/src/install_svg_to_ppt.sh | bash -s -- -i complete
        ```

## Usage

``` bash
svgtoppt [PATH_TO_SVG_FILE]
```

## Customization

If the standard configuration doesn't fit your workflow, that's ok! You can use flags to specify single-use functionality or change the defaults permanently via preferences.

### Flags

| Name | Flag | Default Value | Description |
|--|:---:|--|--|
| `input_svg` | `-i` | none; required input | The SVG wanting to be imported into Keynote |
| `template_ppt` | `-t` | `~/svg-to-keynote/template.ppt` | Filepath of the template PPT |
| `output_directory` | `-o` | `~/svg-to-keynote/Output` | Filepath of the directory where PPT files are output |
| `ppt_name` | `-p` | the name of the SVG file (e.g. `logo.svg` -> `logo.ppt`) | The name of the PPT file that is output |
| `force_ppt` | `-f` | `false` | `false` : creates a new, unique PPT file each time a command is run<br><br>`true` : makes it [idempotent](https://mortoray.com/2014/09/05/what-is-an-idempotent-function/); has the potential to overwrite an existing PPT file |
| `where_to_open` | `-w` | `keynote` | Where the PPT file is opened in after it's created<br><br>**Options**<br>Don't open: `none`<br> Apple Keynote: `keynote`<br>Microsoft PowerPoint: `power`<br>Libre Office:`libre`<br>Apache OpenOffice: `oo` |

#### Examples

``` bash
# -i is required
svgtoppt -i logo.svg

# Use a custom template PPT file
svgtoppt -i logo.svg -t ~/Documents/blake_template.ppt

# -i is required
svgtoppt -i logo.svg

# Save all your new PPT files to your desktop for easy access
svgtoppt -i logo.svg -o ~/Desktop

# By default the output would be logo.ppt; here we can give it another name
svgtoppt -i logo.svg -p amazing_logo
# The -p flag works with or without ".ppt"
svgtoppt -i logo.svg -p amazing_logo.ppt

# This request ran twice creates 2 files: logo.ppt and logo-1.ppt
svgtoppt -i logo.svg -f false
# This request ran twice creates 1 file (logo.ppt) that gets overwritten once
svgtoppt -i logo.svg -f true

# Creates the PPT file without opening it
svgtoppt -i logo.svg -w none
# Creates the PPT file and opens it in Microsoft PowerPoint
svgtoppt -i logo.svg -w power
```

### Preferences

#### Save

Add the `-s` flag to save the other flags on the current request as your preferences.

``` bash
# Saves preferences for input_svg="$PWD/logo.svg" and where_to_open="none"
svgtoppt -i logo.svg -w none -s

# Want to run the same request again? With saved preferences, you don't have to pass in anything
svgtoppt
```

!!! note

    The SVG file (`input_svg` or `-i`) is also saved, but if you pass in a different SVG file it receives higher priority and the preference won't be used. The same goes for all preferences; they're functionally ignored if your request explicitly includes the corresponding flags.

#### Reset

You can easily reset all your preferences back to the defaults listed above.

``` bash
svgtoppt reset_pref
```

## Notes

- Feel free to edit `template.ppt` to your liking; it's a 4K (53.33" x 30.00") blank presentation
