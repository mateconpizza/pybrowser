<div align="center">

![linux](https://img.shields.io/badge/os-linux-blue?logo=linux)
[![Hatch project](https://img.shields.io/badge/%F0%9F%A5%9A-Hatch-4051b5.svg)](https://github.com/pypa/hatch)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)
![PyPI - Version](https://img.shields.io/pypi/v/pybrowsers-profiles)
[![linting - Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![code style - Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/format.json)](https://github.com/astral-sh/ruff)
[![types - Mypy](https://img.shields.io/badge/types-Mypy-blue.svg)](https://github.com/python/mypy)
[![License - MIT](https://img.shields.io/badge/license-MIT-9400d3.svg)](https://spdx.org/licenses/)

</div>

## Profile Launcher

### A Python Script for Effortless Browser Profile Management

### About

This Python script simplifies launching browser profiles by automatically retrieving profile information from each browser's config directory. It presents these profiles as launch options, saving time and enhancing workflow, especially for users who frequently switch between multiple profiles.

### Requirements

- [dmenu](https://tools.suckless.org/dmenu/)
- [rofi](https://github.com/davatorium/rofi) _(Optional)_
- [fzf](https://github.com/junegunn/fzf) _(Optional)_

### Browsers

- [Firefox](https://www.mozilla.org/firefox/download/thanks/)
- [LibreWolf](https://librewolf.net/)
- [Chromium](https://www.chromium.org/getting-involved/download-chromium/)
- Brave
- And Others...

### Installation

#### Using [`uv`](https://docs.astral.sh/uv)

```bash
$ uv tool install pybrowsers-profiles
```

#### Using [`pipx`](https://github.com/pypa/pipx)

```bash
$ pipx install pybrowsers-profiles
```

#### Using `pip` install

```bash
# Clone repository
$ git clone "https://github.com/mateconpizza/pybrowser"
$ cd pybrowsers

# Create virtual environment & source
$ python -m venv .venv && source .venv/bin/activate

# Install deps
$ (.venv ) pip install -r requirements.txt

# Install script in local environment
$ (.venv ) pip install .
```

### Usage

```bash
$ pybrowsers --help

usage: pybrowsers [-l] [-d DISABLE] [-e ENABLE] [-f] [-t]
                  [-m MENU] [-v] [-V] [browser] [-o URL]

Simple script for manage browser's profiles

options:
    browser             Browser name
    -e, --enable        Enable browser
    -d, --disable       Disable browser
    -u, --url           Open <URL> in browser
    -l, --list          Show browsers list and status
    -t, --table         Show browsers list with detail
    -m, --menu          Select menu (default: dmenu)
    -f, --found         Browsers found
    -V, --version       Show version
    -h, --help          Show help
    -v, --verbose       Verbose mode

locations:
    $HOME/.local/share/pybrowsers
```

### Add Unsupported Browser

You can add a browser creating a `JSON` file in `$XDG_DATA_HOME/pybrowsers/` or
`~/.local/share/pybrowsers`

#### Example

```json
// firefox based
{
  "name": "LibreWolf",
  "command": "librewolf",
  "path": "~/.librewolf/profiles.ini",
  "engine": "gecko",
  "enabled": true
}

// chromium based
{
  "name": "Helium",
  "command": "helium",
  "path": "~/.config/helium/Local State",
  "engine": "blink",
  "enabled": true
}
```

#### Use `no flags` to launch menu

```bash
# Open menu with browsers found
$ pybrowsers
```

#### Use flag `browser` for browser's profile

```bash
# Open menu with profiles list
$ pybrowsers firefox
```

#### Use flag `-o, --open` for launching profile with url

<div align="left">
  <img align="center" src="assets/flag-open-with-browser.png">
</div>

#### Use flag `-m, --menu` to specify the launcher you want to use _(default: `dmenu`)_

<div align="left">
  <img align="center" src="assets/flag-rofi-dark.gif">
</div>

#### Use flag `-l, --list` for status

<div align="left">
  <img align="center" src="assets/flag-list.png">
</div>
<br>

#### Use flag `-d, --disable` or `-e, --enable`

```bash
# Disable browser (won't appear in `browsers found`)
$ pybrowsers -d firefox

# Enable browser
$ pybrowsers -e firefox
```

### Dependencies

- [PySelector](https://pypi.org/project/pyselector/)
