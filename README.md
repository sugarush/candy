# satan-shell

A modular ZShell configuration.

## Module Repositories

  - [satan-core](https://github.com/satan-core)
  - [satan-extra](https://github.com/satan-extra)
  - [satan-community](https://github.com/satan-community)

## Requirements

  - zsh
  - curl
  - git

## Recommended

  - [mdv (Terminal Markdown Viewer)](https://github.com/axiros/terminal_markdown_viewer#installation)

## Install

`eval "$(curl -s 'https://raw.githubusercontent.com/luciferavada/satan-shell/master/install-github.sh')"`

## General

### Usage

User configuration goes in `~/.zlogin` which is not managed by __satan-shell__.

### Manager

The __satan-shell__ module manager, `satan` has the following options.

`satan [flags] [module] <module...>`

  - `-S` Install a list of modules.
  - `-R` Uninstall a list of modules.
  - `-Q` Search for available modules.
  - `-X` Search for installed modules.
  - `-y` Update the repository index.
  - `-l` Load a list of modules.
  - `-a` Use the `SATAN_MODULES` array as the list of modules.

### Documentation

The __satan-shell__ documentation viewer, `satan-info` can be used as follows.

`satan-info [module] <pattern>`

  - Display documentation for a *module*.
  - Optionally search for a *pattern* in the documentation.
  - If no module is specified, the __satan-shell__ documentation is displayed.
  - If [mdv (Terminal Markdown Viewer)](https://github.com/axiros/terminal_markdown_viewer#installation) is available on the system, it is used to display documentation.

### Functions

`satan-ascii-art`

  - Display ascii art.

`satan-ascii-title`

  - Display ascii title.

`satan-ascii-header`

  - Display ascii art, title and credit.

`satan-credit`

  - Display credit.

`satan-reload`

  - Replace the current shell with a new login shell.

`satan-update`

  - Update __satan-shell__.
  - Update activated modules.
  - Reload the shell with *satan-reload*.

`satan-message [type] [message]`

  - Display a formatted *message* of *type*:

    - `title` *Green   -->* `[message]`
    - `bold`  *Magenta ==>* `[message]`
    - `info`  *White   -->* `[message]`
    - `error` *Red     -->* `[message]`

### Configuration

The __satan-shell__ configuration files are located in the `~/.zsh.d` directory.

  - `~/.zsh.d/directories.conf`
  - `~/.zsh.d/modules.conf`
  - `~/.zsh.d/repositories.conf`
  - `~/.zsh.d/settings.conf`

### Variables

#### Directories

`SATAN_INSTALL_DIRECTORY`

  - The path to the installation directory.

`SATAN_CONFIGURATION_DIRECTORY`

  - The path to the configuration directory.

`SATAN_MODULES_DIRECTORY`

  - The path to the modules directory.

#### Modules

`SATAN_MODULES`

  - An array of __satan-shell__ modules to load on start.

#### Repositories

`SATAN_REPOSITORIES`

  - An ordered list of github organizations containing __satan-shell__ modules as git repositories.

#### Settings

`SATAN_DISPLAY_ASCII_ART`

  - Display ASCII artwork on load.

`SATAN_DISPLAY_ASCII_TITLE`

  - Display ASCII title on load.

`SATAN_DISPLAY_MODULE_LOAD`

  - Display loaded modules.

`SATAN_USE_MARKDOWN_VIEWER`

  - Display documentation with [mdv (Terminal Markdown Viewer)](https://github.com/axiros/terminal_markdown_viewer#installation).

`SATAN_MARKDOWN_VIEWER_THEME`

  - The [mdv (Terminal Markdown Viewer)](https://github.com/axiros/terminal_markdown_viewer#installation) theme to use.

## Modules

### Usage

Modules can be activated, installed, uninstalled, updated and loaded by *name* or *repository/name*.

Activated modules are handled by the `SATAN_MODULES` array in `~/.zsh.d/modules.conf`.

Modules are installed to the `~/.zsh.d.modules` directory.

Modules can create, store and use configuration files in the `~/.zsh.d.conf` directory.

### Functions

`satan-module-install [module]`

  - Install an available module.

`satan-module-uninstall [module]`

  - Uninstall a module.

`satan-module-update [module]`

  - Update a module.

`satan-module-load [module]`

  - Load a module.

`satan-modules-install [module] <module...>`

  - Install a list of modules.

`satan-modules-uninstall [module] <module...>`

  - Uninstall a list of modules.

`satan-modules-update [module] <module...>`

  - Update a list of modules.

`satan-modules-load [module] <module...>`

  - Load a list of modules.

`satan-modules-active-install`

  - Install modules in the activated modules array.

`satan-modules-active-update`

  - Update modules in the activated modules array.

`satan-modules-active-load`

  - Load modules in the activated modules array.

## Repositories

### Usage

Modules can be found by *name* or *repository/name*.

Modules can be searched for by *pattern*.

Repositories are managed by the `SATAN_REPOSITORIES` array in `~/.zsh.d/repositories.conf`.

Module repositories are indexed in `~/.zsh.d/.index.available` and installed modules are tracked in `~/.zsh.d/.index.installed`.

### Functions

`satan-repository-index`

  - Index repositories in the repositories array.

`satan-module-available-find [module]`

  - Find an available module.

`satan-module-available-search [pattern]`

  - Search through available modules.

`satan-module-installed-find [module]`

  - Find an installed module.

`satan-module-installed-search [pattern]`

  - Search through installed modules.

`satan-modules-available-find [module] <module...>`

  - Find a list of available module.

`satan-modules-available-search [pattern] <pattern...>`

  - Search through a list of available modules.

`satan-modules-installed-find [module] <module...>`

  - Find a list of installed module.

`satan-modules-installed-search [pattern] <pattern...>`

  - Search through a list of installed modules.

## Developer

### Usage

Developer state for a module can be managed by *name* or *repository/name*.

Files of the format `*.sh` in the root of the module are loaded by default.

The following variables are available inside module files.

### Variables

`MODULE_NAME`

  - The name of the module.

`MODULE_REPOSITORY`

  - The name of the module the repository.

`MODULE_DIRECTORY`

  - The path to the module.

### Functions

`satan-module-developer-enable [module]`

  - Set the git origin url for a module to use the SSH protocol.

`satan-module-developer-disable [module]`

  - Set the git origin url for a module to use the HTTPS protocol.

`satan-module-developer-status [module]`

  - Report if a module has any modified files.

`satan-modules-developer-enable [module] <module...>`

  - Set the git origin url for a list of modules.

`satan-modules-developer-disable [module] <module...>`

  - Set the git origin url for a list of modules.

`satan-modules-developer-status [module] <module...>`

  - Report if a list of modules have any modified files.

`satan-developer-enable`

  - Set the git origin url for activated modules to use the SSH protocol.

`satan-developer-disable`

  - Set the git origin url for activated modules to use the HTTPS protocol.

`satan-developer-status`

  - Report if any activated modules have modified files.
