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
    If you don't have Libre Office installed, SVGtoPPT can install `7.1.0` for you&nbsp; :slightly_smiling_face:

## Getting Started

1. If you haven't yet, download & install Alfred with the button on [their homepage](https://www.alfredapp.com/){target=_blank}
2. Download the [Alfred workflow file](https://github.com/SVGtoPPT/svgtoppt-alfred/blob/1.0.0/SVGtoPPT.alfredworkflow){target=_blank class=underline}

[Download&nbsp; :fontawesome-solid-download:](https://github.com/SVGtoPPT/svgtoppt-alfred/raw/1.0.0/SVGtoPPT.alfredworkflow){: .md-button }

## Install

1. Double-click the downloaded workflow file to open it in Alfred, then select Import
2. Launch Alfred (default is `Cmd` + `Space`)

!!! question "Do you have Libre Office installed?"

    === "No"
        SVGtoPPT can install Libre Office `7.1.0` for you.

        Type or copy-paste this into Alfred followed by a space and a folder where you want to install SVGtoPPT:
        ```
        svgtoppt install complete
        ```

        If you want to install Libre Office yourself you can download it from [their website](https://www.libreoffice.org/download/download){target=_blank class=underline} or use Homebrew:

        ``` bashclass=underline
        brew install --cask libreoffice
        ```

    === "Yes"

        Type or copy-paste this into Alfred followed by a space and a folder where you want to install SVGtoPPT:

        ```
        svgtoppt install basic
        ```

## Usage

1. Launch Alfred (default is `Cmd` + `Space`)
2. Type `svg`, a space, and the name of your SVG file or directory
3. Select your file from Alfred's search results
4. Workflow will work in the background and open the new PPT file in Keynote when finished
5. Select all vectors `Ctrl` + `A`
6. Copy (`Ctrl` + `C`) and paste (`Ctrl` + `V`) shapes to other Keynote presentations

## Customization

The workflow contains environment variables you can change. They are equivalent to the flags offered by the [CLI](/cli/#flags){ class=underline }.

| Name | Default Value | Description |
|--|--|--|
| input_svg | none | Filepath of the SVG file to be converted |
| template_ppt | where SVGtoPPT was installed | Filepath of the template PPT |
| output_directory | `Output` directory where SVGtoPPT was installed | Filepath of the directory where PPT files are output |
| ppt_name | the name of the SVG file<br>(e.g. `my_logo.svg` becomes `my_logo.ppt`) | The name of the PPT file that is output |
| force_ppt | `false` | `false` : creates a new, unique PPT file each time a command is run<br><br>`true` : makes it [idempotent](https://mortoray.com/2014/09/05/what-is-an-idempotent-function/); has the potential to overwrite an existing PPT file |
| where_to_open | `keynote` | Where the PPT file is opened in after it's created<br><br>**Options**<br>Don't open: `none`<br> Apple Keynote: `keynote`<br>Microsoft PowerPoint: `power`<br>Libre Office: `libre`<br>Apache OpenOffice: `oo` |

If you fill in the `input_svg` environment variable, you can run SVGtoPPT without having to type an SVG file. In that case, type `svg` into Alfred and hit return.
