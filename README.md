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

Currently working on a map to generic bindings.

## New key locations

keyboard left backslash = backslash (just normal binding)
page up = escape
footpedal down backspace = escape
footpedal down delete = toggle eye tracker

Mac:
Ctrl = Cmd (this is automatic)
Windows Key = Alt

## Layouts

qwerty.txt = Windows
1_qwerty.txt = Mac
w_qwerty = Windows In Progress

## New bindings

build and run - Shift F2
find class - Shift F3
scroll up - Shift F4
scroll down - Shift F6
stop build - Shift F7
goto definition - Shift F8
take screenshot - Shift F9
toggle eye mouse - Shift F10
toggle header - Shift F11

# Mac

Using 'Alt Tab' app to have nice window switching with keyboard control.

Open with kp-r on the keyboard. Navigate with arrow keys and press space to select the highlighted window.

brew install --cask alt-tab
