# The Build Tool

<img src="/media/create-exe.gif" />

> The multi-platform multi-language build tool.

-   Out of the box support for typescript and go
-   Easy extensibility
-   Modular build process with json configuration

## TL; DR

1. Create a project

```bash
$ npx verace -p verace.js create-exe
```

<p align="center">
<img src="/media/create-exe.png" width="500">
</p>

2. Run it

```bash
$ npx verace -p verace.js run-exe
```

<p align="center">
<img src="/media/run-exe.png" width="500">
</p>

3. Develop your app
4. Build it

```bash
$ npx verace -p verace.js build-exe
```

<p align="center">
<img src="/media/build-exe.png" width="500">
</p>

## Why

When working on different projects, differences in build procedure can sometimes arise due. **Verace.js** aims to centralise build procedures. By implementing standardisation, bugs are more easily found and dealt with. This project was originally written for two specific projects, but then it was expanded outwards in scope an generalised.

## Installation

### Standalone installation

Add a compiled stand-alone binary from releases to your local path `$PATH`

```bash
#zshrc

...
export VERACE="/path/to/verace"
export PATH="$PATH:VERACE_DIR"
...
```

### Installing using npm

```bash
$ npm i verace.js -g
```

### Running using `npx`

It is also possible to use `npx` to avoid a permanent install:

```bash
$ npx verace.js
```

> **Note** <br />
> All commands assume a permanent system binary is installed. If `npx` is used instead. Replace all mentions of `verace` with `npx verace -p verace.js` The `-p verace.js` is needed because this package exposes multiple binaries.

## Examples

Two examples corresponding to the output of running `$ verace create-exe` :

-   [Go](https://github.com/lspaccatrosi16/verace.js/tree/master/examples/go-example/)
-   [Typescript](https://github.com/lspaccatrosi16/verace.js/tree/master/examples/ts-example/)

## Commands

```console
$ verace
Setting up execution instance. ID: 20ld183
────────────────────────────────────────────────────────────────────────────────
                                         _
 __   __ ___  _ __  __ _   ___  ___     (_) ___
 \ \ / // _ \| '__|/ _` | / __|/ _ \    | |/ __|
  \ V /|  __/| |  | (_| || (__|  __/ _  | |\__ \
   \_/  \___||_|   \__,_| \___|\___|(_)_/ ||___/
                                      |__/
The multi-platform, multi-language build tool
v0.3.1
Usage: verace [options] [command]

The Verace.js CLI Toolchain

Options:
  -V, --version           output the version number
  -p --path <path>        Path to verace config file.
  -v --verbose            Provides verbose logs
  -h, --help              display help for command

Commands:
  help                    Shows this message
  create-exe              Creates an executable.
  build-exe [options]     Builds the project according to the verace config file
  run-exe [arguments...]  Runs the current project
  version                 Manage package versions

Purging execution instance. ID: 20ld183


Verace.js CLI exited without errors.
```

### Global Options

##### `-p, --path <path>`

Set this to the path to the {@page ./CONFIGURING.md [ verace config ]} file for operations on projects that are not in the current directory.

##### `-v --verbose`

Outputs verbose messages about the build. Spelling errors are to be expected in places.

##### `-V --version`

Outputs the version number and exits

### `create-exe`

Creates a new project with a dialog.

##### `-p --path <path>`

Can either be set to a folder, or a verace config file. If the folder does not exist, it will be automatically created.

### `build-exe`

Build the project.

##### `--noHooks`

Disables the running of {@page ./CONFIGURING.md [ build hooks ]}

##### `--skipPkg`

Skips the packageing step used when building typescript projects. {@page ./CONFIGURING.md [ See more ]}

### `run-exe`

Runs the current project without creating a permanent build.

### `version`

**Verace.js** uses [ `semver` ](https://github.com/npm/node-semver) versioning to manage individual project versions. The version is stored in the `version` field of {@page ./CONFIGURING.md [ `verace config` ]}, and passed to each program in its {@page ./ADVANCED_USAGE.md [ environment data ]}. It can be managed with:
