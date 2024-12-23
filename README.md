
<!-- README.md is generated from README.Rmd. Please edit that file -->

# gander

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/gander)](https://CRAN.R-project.org/package=gander)
[![R-CMD-check](https://github.com/simonpcouch/gander/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/simonpcouch/gander/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

gander is a higher-performance and lower-friction chat experience for
data scientists in RStudio and Positron. The package brings
[ellmer](https://ellmer.tidyverse.org) chats into your project sessions,
automatically incorporating relevant context and streaming their
responses directly into your documents.

**Why not just chat?** In many ways, working with gander is just like
using a chat interface online or via
[shinychat](https://github.com/jcheng5/shinychat). The gander assistant
will automatically find the context it needs, though:

- File contents from elsewhere in the project you’re working on
  (e.g. the lines in your source file)
- Variables, allowing the assistant to locate the column names and types
  in data frames you’re working with, images linked to in your
  documents, and function definitions
- Function documentation, either defined in your project or from common
  R packages

## Installation

You can install gander like so:

``` r
pak::pak("simonpcouch/gander")
```

Then, ensure that you have an
[`ANTHROPIC_API_KEY`](https://console.anthropic.com/) environment
variable set, and you’re ready to go. If you’d like to use an LLM other
than Anthropic’s Claude 3.5 Sonnet—like OpenAI’s ChatGPT or a local
ollama model—to power the gander see `?gander_options`.

The gander assistant is interfaced with the via the gander addin. For
easiest access, we recommend registering the gander addin to a keyboard
shortcut.

**In RStudio**, navigate to
`Tools > Modify Keyboard Shortcuts > Search "gander"`—we suggest
`Ctrl+Alt+G` (or `Ctrl+Cmd+G` on macOS).

**In Positron**, you’ll need to open the command palette, run “Open
Keyboard Shortcuts (JSON)”, and paste the following into your
`keybindings.json`:

``` json
    {
        "key": "Ctrl+Cmd+G",
        "command": "workbench.action.executeCode.console",
        "when": "editorTextFocus",
        "args": {
            "langId": "r",
            "code": "gander::gander_addin()",
            "focus": true
        }
    }
```

The analogous keybinding on non-macOS is `Ctrl+Alt+G`. That said, change
the `"key"` entry to any keybinding you wish!

Once those steps are completed, you’re ready to use the gander assistant
with a keyboard shortcut.

## Example

[![A screencast demonstrating usage. In an RStudio session, I
iteratively build a plot based on the mtcars dataset by typing
plain-english
instructions.](https://github.com/user-attachments/assets/845b4410-bce8-4e2d-90b7-59dbf6728b68)](https://github.com/user-attachments/assets/563f4670-860a-4f8f-a087-41c28381b977)
