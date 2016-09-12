[![MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

# DOOM for Emacs

An opinionated UI plugin/pack of themes extracted from my [emacs.d],
inspired by the One Dark/Light UI and syntax themes
in [Atom](http://atom.io).

Includes optional dimming of non-source buffers (and minibuffer), a
[neotree] theme with font icons, and (soon) a mode-line config.

Currently available colorschemes:
+ **doom-one**: inspired by Atom One Dark
+ **doom-dark**: based on Molokai

Soon to come:
+ **doom-one-light**: inspired by Atom One Light
+ **doom-tron**: doom-one, but with
  daylerees' [Tron Legacy][daylerees] colorscheme
+ **doom-peacock**: doom-one, but with daylerees' [Peacock][daylerees]
  colorscheme

**Notes:**

+ Uses `face-remapping-alist`, which won't work in terminal emacs (but
  degrades gracefully).
+ Tested mainly on Emacs 24.5+

## Screenshots

Find them [in the screenshots branch][screenshots]

## Installation

1. Clone the repo somewhere in your `load-path`.

2. If you want the neotree theme, install the fonts in the `fonts/`
folder of [all-the-icons].

3. Load `doom-themes` and load the theme you want.

Example configuration:

``` emacs-lisp
(require 'doom-themes)
(load-theme 'doom-one t) ;; or doom-dark, etc.

;;; OPTIONAL
;; brighter source buffers
(add-hook 'find-file-hook 'doom-buffer-mode)
;; brighter minibuffer when active
(add-hook 'minibuffer-setup-hook 'doom-buffer-mode)
;; Custom neotree theme
(require 'doom-neotree)
```

## Configuration

+ `doom-enable-bold` (default: `t`): if nil, bolding will be disabled
  across all faces.
+ `doom-enable-italic` (default: `t`): if nil, italicization will be
  disabled across all faces.

## Enabling other features

### Dimmed non-source buffers/windows

`(add-hook 'find-file-hook 'doom-buffer-mode)`

Enable `doom-buffer-mode` in buffers where you want a slightly
brighter background. I use it to visually set apart source buffers
from popups, the minibuffer, or temporary buffers.

### Neotree integration

`(require 'doom-neotree)`

Modifies [neotree] to use file icons (as shown in the [screenshots]).

Note:
+ This disables `neo-vc-integration`, because the two are
  incompatible.
+ This can be customized by changing these variables:
  + `doom-theme-neotree-root-icon` (string)
  + `doom-theme-neotree-open-folder-icon` (string)
  + `doom-theme-neotree-closed-folder-icon` (string)
  + `doom-theme-neotree-file-icons` (boolean): whether or not to
    display icons for each individual file. Disabled by default. Can
    mess up line spacing depending. YMMV.
  + `doom-theme-neotree-line-spacing` (int): line-spacing to
  use in the neotree buffer.

### Mode-line config

The custom mode-line isn't part of doom-themes yet, but will be soon.

In the meantime, check out [my mode-line configuration][mode-line] in
my [emacs.d].

### Brighter minibuffer

To brighten the minibuffer, use `(doom-brighten-minibuffer)` in your emacs.d.


[all-the-icons]: https://github.com/domtronn/all-the-icons.el
[daylerees]: http://daylerees.github.io/
[emacs.d]: https://github.com/hlissner/.emacs.d
[mode-line]: https://github.com/hlissner/.emacs.d/blob/master/core/core-modeline.el
[neotree]: https://github.com/jaypei/emacs-neotree
[screenshots]: https://github.com/hlissner/emacs-doom-theme/tree/screenshots
[config]: https://github.com/hlissner/.emacs.d/blob/master/core/core-ui.el#L91