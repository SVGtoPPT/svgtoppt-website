# CLI

## Prerequisites

<div class="row center icons two-column">
  <div>
    <a target="_blank" href="https://www.apple.com/macos">
      <p>
        macOS
      </p>
      <img src="/img/mac-os-icon.svg" alt="macOS icon" title="macOS icon"/>
    </a>
    <p>Primarily tested with <code>10.15.7</code> (Catalina)</p>
  </div>
  <div>
    <a target="_blank" href="https://www.libreoffice.org/download/download">
      <p>
        Libre Office
      </p>
      <img src="/img/libre-office-icon.svg" alt="macOS icon" title="macOS icon"/>
    </a>
    <p>Primarily tested with <code>7.0.4.2</code> and <code>7.1.0</code></p>
    <br>
  </div>
</div>

!!! note
    If you don't have Libre Office installed, SVGtoPPT can install `7.1.0` for you&nbsp; :slightly_smiling_face:

## Install

Install via command line by using [macOS Terminal](https://en.wikipedia.org/wiki/Terminal_(macOS)){target=_blank class=underline} or a terminal emulator. Below you'll find commands for the latest version, but feel free to change "latest" to whichever version you want.

!!! question "Do you have Libre Office installed?"

    === "No"
        SVGtoPPT can install Libre Office it for you.

        Install command:

        ``` bash
        version="latest"; curl -s "https://raw.githubusercontent.com/SVGtoPPT/svgtoppt/$version/src/install_svgtoppt.sh" | bash -s -- -i complete
        ```

        If you want to install Libre Office yourself you can download it from [their website](https://www.libreoffice.org/download/download){target=_blank class=underline} or use Homebrew:

        ``` bash
        brew install --cask libreoffice
        ```

    === "Yes"

        Install command:

        ``` bash
        version="latest"; curl -s "https://raw.githubusercontent.com/SVGtoPPT/svgtoppt/$version/src/install_svgtoppt.sh" | bash -s -- -i basic
        ```

## Usage

``` sh
$ svgtoppt [PATH_TO_SVG_FILE]
```

1. Workflow will work in the background and open the new PPT file in Keynote when finished
2. Select all vectors `Ctrl` + `A`
3. Copy (`Ctrl` + `C`) and paste (`Ctrl` + `V`) shapes to other Keynote presentations

### Examples

``` bash
svgtoppt ~/Desktop/logo.svg

# The entire path isn't required if the SVG file is in your current working directory
cd ~/Desktop
svgtoppt logo.svg
```

## Customization

If the standard configuration doesn't fit your workflow, that's ok! You can use flags to specify single-use functionality or change the defaults.

### Flags

| Long Flag | Short Flag | Default Value | Description |
|:--|:---:|--|--|
| &#x2011;&#x2011;input | `-i` | none; required | Filepath of the SVG file or directory to be converted |
| &#x2011;&#x2011;template_ppt | `-t` | `~/svg-to-keynote/template.ppt` | Filepath of the template PPT |
| &#x2011;&#x2011;output_directory | `-o` | `~/svg-to-keynote/Output` | Filepath of the directory where PPT files are output |
| &#x2011;&#x2011;ppt_name | `-p` | the name of the SVG file<br>(e.g. `my_logo.svg` becomes `my_logo.ppt`) | The name of the PPT file that is output |
| &#x2011;&#x2011;force_ppt | `-f` | `false` | `false` : creates a new, unique PPT file each time a command is run<br><br>`true` : makes it [idempotent](https://mortoray.com/2014/09/05/what-is-an-idempotent-function/); has the potential to overwrite an existing PPT file |
| &#x2011;&#x2011;where_to_open | `-w` | `keynote` | Where the PPT file is opened in after it's created<br><br>**Options**<br>Don't open: `none`<br> Apple Keynote: `keynote`<br>Microsoft PowerPoint: `power`<br>Libre Office: `libre`<br>Apache OpenOffice: `oo` |
| &#x2011;&#x2011;quiet | `-q` | `false` | Quiet mode to prevent output |

#### Examples

``` bash
# The -i flag is required in all requests
svgtoppt -i ~/Desktop/logo.svg
svgtoppt --input=~/Desktop/logo.svg

# The entire path isn't required if the SVG file is in your current working directory
cd ~/Desktop
svgtoppt -i logo.svg
svgtoppt --input=logo.svg

# Pass in a directory and the PPT file will have a slide for each SVG file found
svgtoppt -i ~/Desktop/logos
svgtoppt --input=~/Desktop/logos

# Use a custom template PPT file
svgtoppt -i logo.svg -t ~/Documents/blake_template.ppt
svgtoppt --input=logo.svg --template_ppt=~/Documents/blake_template.ppt

# Save all your new PPT files to your desktop for easy access
svgtoppt -i logo.svg -o ~/Desktop
svgtoppt --input=logo.svg --output_directory=~/Desktop

# By default the output would be logo.ppt; here we can give it another name
svgtoppt -i logo.svg -p amazing_logo
svgtoppt --input=logo.svg --ppt_name=amazing_logo

# The -p flag works with or without the PPT extension (".ppt")
svgtoppt -i logo.svg -p amazing_logo.ppt
svgtoppt --input=logo.svg --ppt_name=amazing_logo.ppt

# This request ran twice creates 2 files: logo.ppt and logo-1.ppt
svgtoppt -i logo.svg -f false
svgtoppt --input=logo.svg --force_ppt=false

# This request ran twice creates 1 file (logo.ppt) that gets overwritten once (first one is not recoverable)
svgtoppt -i logo.svg -f true
svgtoppt --input=logo.svg --force_ppt=true

# Creates the PPT file without opening it
svgtoppt -i logo.svg -w none
svgtoppt --input=logo.svg --where_to_open=none

# Creates the PPT file and opens it in Microsoft PowerPoint
svgtoppt -i logo.svg -w power
svgtoppt --input=logo.svg --where_to_open=power

# Request will work silently without output unless there's a failure/error
svgtoppt -i logo.svg -q
svgtoppt --input=logo.svg --quiet
```

### Defaults

#### Save

Add the `--save_def` flag (`-s`) to save the other flags on the current request as your defaults.

``` bash
# Saves defaults for input="$PWD/logo.svg" and where_to_open="none"
svgtoppt -i logo.svg -w none -s
svgtoppt --input=logo.svg --where_to_open=none --save_pref

# Want to run the same request again? With a saved default for input, you don't have to pass in anything
svgtoppt

# If you want to save defaults without running a conversion, that's supported too
svgtoppt -i logo.svg -w none -s -x
svgtoppt --input=logo.svg --where_to_open=none --save_pref --stop_creations
```

!!! note

    Explicitly passed in parameters receive higher priority than the corresponding defaults.

    Example:
    ``` bash
    # If you have a default where_to_open=libre it gets ignored by this request and Keynote will open
    svgtoppt --input=logo.svg --where_to_open=keynote
    ```

#### Reset

You can easily reset all your defaults back to the ones listed above.

``` bash
svgtoppt reset_def
```

## Notes

- Feel free to edit `template.ppt` to your liking; it's a 4K (53.33" x 30.00") blank presentation
