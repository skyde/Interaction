# Goal

Ergonomic computer control with no mouse.

# Overview

Uses eye tracking, footpedals and keyboard macros.

Originally made for an injured wrist, but it is nice for day to day use as well.

# Eye Gaze

Eye tracking controls the cursor. Uses combination of eye and head movement for accurate control. Am able to use for programming work without issues.

There are existing programs that do this, but found I could make improvements so wrote my own. 

Eye gaze is used to control the macro position of the mouse. Head horizontal and depth position are used for precise adjustments.

It takes a bit of time to get used, but after a few months it's as natural as a regular mouse.

# Keyboard

Pressing down the left footpedal turns every key on the keyboard into a macro. One of the main sources of strain using a keyboard comes from pressing combinations of more than one key at a time (chording). 

![kinesis layout](images/kinesis%20layout.png?raw=true)
![kinesis layout alternate](images/kinesis%20layout%20alternate.png?raw=true)

Keyboard layout is also Colemak Mod DH, an alternative to qwerty.
https://colemakmods.github.io/mod-dh/

I also use a Kinesis Advantage 2 LF, a nice ergonomic keyboard.

# Footpedals

Mouse input position is gaze based, so there need to be a way to click the mouse. Mouse clicks have been moved to the feet.

I experimented with using blinking and winking to click, but found this was too distracting and not accurate enough.

Shift has also been moved to the feet as this further reduces 'chording' when typing.

Left Foot:

Press and hold to activate alternate keyboard layout.

Right Foot:

Three Pedals. Left to right ordering:
- Shift Key
- Mouse Left Click
- Mouse Right Click

# Other

I also have a trackball to the middle of my keyboard for fine mouse control, as well as a vertical mouse as a fallback when normal mouse input is required.

in the kinesis layout folder qwerty.txt is for Windows & 1_querty.txt is for Mac.

# In Progress

Currently working on a map to generic bindings. This is mostly done but layout images need to be updated

## New key locations

```
keyboard left backslash = backslash (just normal binding)
page up = escape
footpedal down backspace = escape
footpedal down delete = toggle eye tracker
```

Mac:
Windows Key = Alt (Meta)

## Layouts

qwerty.txt = Windows
1_qwerty.txt = Mac
w_qwerty = Backup of old Windows layout - so can easily switch to if needed

## New bindings

```
build and run - Shift F2
find class - Shift F3
scroll up - Shift F4
scroll down - Shift F6
stop build - Shift F7
goto definition - Shift F8
toggle spotlight search - Shift F9
toggle eye mouse - Shift F10
toggle comment - Shift F11
```

# Mac

Note that you should use the Mac 1_qwerty.txt keybinding with the Kinesis Advantage 2 keyboard in 'Windows' mode as the keys have been manually translated already (no need to change the 'mode' of the keyboard at all)

## Custom Alt Tab app

Using 'Alt Tab' app to have nice window switching with keyboard control.

Open with kp-r on the keyboard. Navigate with arrow keys and press space to select the highlighted window.

brew install --cask alt-tab

## Hammerspoon

Custom shortcut pressing Shift F9 opens spotlight search, since we don't want to change the original shortcut.

## Fluor

Automatically switches mode of fn keys per program. Required as macros use fn keys to operate - and just useful generally. 

## Custom Settings

defaults write -g ApplePressAndHoldEnabled -bool false

# Windows

```
- Get the Alt Tab switcher to work better
    - Go to Accessibility -> Visual Effects -> Animation effects & turn them off
    - Without doing this move to another tab will not work without waiting a split second.
- Set cursor blink rate to 0
- Set cursor thinkness to 6
```

## Powershell 7

Use this since it's nicer than the default one.

## Basic Setup

```
iwr -useb get.scoop.sh | iex
scoop bucket add extras
scoop bucket add nerd-fonts
scoop install git sudo ripgrep fd fzf bat delta less
scoop install llvm nvim chezmoi
scoop install firacode-nerd-font
chezmoi init --apply skyde
chezmoi doctor
```

## Visual Studio

```
- For Visual Studio use VSVim with the provided vsvimrc
- Also use the plugin 'Peasy Motion' with the following settings:
- Allowed jump label characters: tsraneiodhgmplfuc,bjvk
    - (note this is optimized for Colemak Mod DH)
- Use a plugin called MinimalVS for nice fullscreen mode
    - https://marketplace.visualstudio.com/items?itemName=pavonism.minimalVS
- There is a plugin called 'Smooth Caret' which messes with the VSVim caret - make sure it's disabled
```

## Perforce

Ensure you set the set the correct environment variable to allow the diff to work:

```
P4DIFF="C:\Program Files\Microsoft Visual Studio\2022\Professional\Common7\IDE\devenv.exe" /Diff %1 %2
```

## Kinesis Advantage 2

Use the command when in .\kinesis layout to copy the files to the Kinesis Advantage 2:

```
Copy-Item -Path .\* -Destination 'D:\active\' -Recurse -Force -Verbose
```

Note: I've had issues using the Mac version of the Kinesis app where it totally corrupts the drive - so just use Windows.

## Continuous Integration

The repository includes a GitHub Actions workflow that checks the configuration
files on every push or pull request. The job runs on Linux, macOS and Windows
and performs several checks:

1. **Lua syntax** – `hammerspoon/init.lua` is compiled with `luac` to ensure it
   contains no syntax errors.
2. **JSON validation** – `jq` validates `vscode/keybindings.json` and
   `vscode/settings.json`.
3. **Neovim startup** – Neovim is launched headless and the run fails if any
   errors are printed during startup.

Package installation is handled with the platform package manager:

- **Ubuntu** – `apt`
- **macOS** – `brew`
- **Windows** – `choco`

If any step fails the CI job exits with an error.
