# Alfred

## Prerequisites

<div class="row center icons three-column">
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
    <a target="_blank" href="https://www.alfredapp.com/powerpack">
      Alfred Powerpack
      <img src="/img/alfred-icon.svg" class="center" alt="Alfred icon" title="Alfred icon"/>
    </a>
    <p>Primarily tested with <code>4.3.2</code></p>
    <br>
    <p>£29 for single license</p>
    <p>£49 for mega supporter</p>
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
    If you don't have Libre Office installed, svgtoppt can install `7.1.0` for you&nbsp; :slightly_smiling_face:

## Getting Started

1. If you haven't yet, download & install Alfred with the button on [their homepage](https://www.alfredapp.com/)
2. Download the [Alfred workflow file](https://github.com/SVGtoPPT/svgtoppt/raw/main/src/svgtoppt.alfredworkflow) (`svgtoppt.alfredworkflow`) for SVG to Keynote

## Install

1. Double-click the workflow file  to open it in Alfred, then select Import
2. Launch Alfred (default is `Cmd` + `Space`)
3. Do you have Libre Office installed?

   - **No:** Install Libre Office and the basics: `svg install complete`

   - **Yes:** Install just the application basics: `svg install basics`

## Usage

1. Launch Alfred (default is `Cmd` + `Space`)
2. Type `svg`, a space, and the name of your SVG file
3. Select your file from Alfred's search results
4. Workflow will work in the background and open Keynote when finished
5. Select all vectors `Ctrl` + `A`
6. Copy (`Ctrl` + `C`) and paste (`Ctrl` + `V`) shapes to other Keynote presentations

## Notes

- Edit the workflow environment variables if you'd like

    | Variable Name         | Default Value                 | Description                                           |
    | --------------------- | ----------------------------- | ----------------------------------------------------- |
    | application_directory | ~/svg-to-keynote              | Default location of output directory and template PPT |
    | output_directory      | ~/svg-to-keynote/Output       | Where the resultant PPT files are saved               |
    | template_ppt_path     | ~/svg-to-keynote/template.ppt | File path to the template PPT                         |

- DIY Libre Office installation by going to [their homepage](https://www.libreoffice.org/download/download/) **OR** using Homebrew

    ```bash
    # Install Homebrew if you haven't already
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

    # Install Libre Office with Homebrew
    brew install libreoffice
    ```

- Feel free to edit `template.ppt` to your liking; it's a 4K (53.33" x 30.00") blank presentation
