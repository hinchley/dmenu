# dmenu
This is Pete Hinchley's fork of dmenu: https://tools.suckless.org/dmenu/

## Changes
It is based on version 5.3 of dmenu with several tweaks to filter the list of targets using a custom path.

Firstly, it relies on setting *DMENU_PATH* (in `.xinitrc`) to the set of folders that are to be searched. I use: `~/apps:~/.local/bin:~/scripts/dwm`.

Any apps under `/usr/bin` or other locations to be accessed via dmenu are linked to `~/apps`. This may sound laborious, but there are only a handful of apps I care about. And any dmenu scripts are stored under `~/scripts/dmenu`.

The `stest` binary has been modified to output the list of all executable files within the *DMENU_PATH* as _"name:full path"_ pairs. For example: `zed:/home/pete/.local/bin/zed`. This output is parsed by `dmenu_path` such that dmenu lists the program using the short name, but then executes the program using the full path. This removes the need for all folders in *DMENU_PATH* to be in *PATH* (such as the folder containing dmenu scripts).

One final enhancement to `dmenu_run` ensures dmenu doesn't display program extensions. For example, `notesnook.AppImage` is displayed as `notesnook`.

The changes made to the base version of dmenu are stored in `patches/01-path.diff`. These changes are already applied to the code.

## Build
To build and install dmenu:

```
git clone https://github.com/hinchley/dmenu.git
cd dmenu
./build.sh
```
