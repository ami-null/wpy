# Slim Python distribution for Windows, based on WinPython (unofficial)

A small, portable Python distribution for 64-bit Windows with JupyterLab, pandas, seaborn and the packages they depend on. It is made by installing a fixed list of packages into the minimal "dot" build of WinPython and zipping the result. The folder layout is the same as in a regular WinPython distribution.

## What it is based on

The base is the WinPython "dot" build (Python and pip only), published by the WinPython project at https://github.com/winpython/winpython (project site: https://winpython.github.io/). The exact base download is stated in the notes of each release in this repository. The packages added on top of it are listed in `requirements.txt`, and the exact installed versions are in `installed-packages.txt` inside the archive.

## Unofficial status

This is an independent project. It is not an official WinPython release, and it is not affiliated with, endorsed by, sponsored by or supported by the WinPython project, the Python Software Foundation, Project Jupyter, or the authors of any included package. The name WinPython is used only to state what this distribution is based on. Do not report problems with this build to the WinPython project. Open an issue in this repository instead.

## Use

1. Download the `.zip` file from the Releases page. The `.sha256` file next to it can be used to check the download.
2. Extract it to a folder you can write to, for example `C:\Python` or `D:\tools`. Avoid `Program Files` and very long paths. No installation or administrator rights are needed.
3. Double-click `Jupyter Lab.exe` in the extracted folder. Alternatively, open `WinPython Command Prompt.exe` and run `jupyter lab`.

Code completion appears as you type, with a documentation panel next to the list. To see the documentation of a name in a notebook or editor, hold Ctrl and hover over it.

Launchers for tools that are not set up in this distribution (IDLE, Spyder, VS Code and Jupyter Notebook) are in the `unused-launchers` folder. Move one back to the main folder to use it. Additional packages can be installed from `WinPython Command Prompt.exe` with `pip install <package>`. Nothing is installed system-wide, so removing the distribution means deleting its folder.

## Licensing

This distribution bundles software from several projects, each under its own license. The license files for every component are included in the archive.

| Component | License | Where to find the text |
| --- | --- | --- |
| WinPython (base distribution, launchers, scripts) | MIT | `licenses\WinPython-LICENSE.txt` |
| Python | PSF License Agreement | `LICENSE.txt` in the `python` folder |
| JupyterLab, pandas, seaborn, NumPy, SciPy, Matplotlib and their dependencies | Individual licenses, mostly BSD-3-Clause, MIT, Apache-2.0 or similar permissive licenses | `THIRD-PARTY-LICENSES.md` (inventory) and `THIRD-PARTY-LICENSE-TEXTS.txt` (full texts) |
| Build scripts and this README | MIT | `licenses\BUILD-SCRIPTS-LICENSE.txt` |

Each installed package also keeps its own license files in its `.dist-info` folder under `Lib\site-packages`. Some packages ship compiled libraries inside their wheels (for example OpenBLAS in NumPy and SciPy), and the licenses for those are part of the package's license files. The Microsoft Visual C++ runtime files that come with Python are redistributable under Microsoft's terms.

All product names, trademarks and registered trademarks are the property of their respective owners.

## No warranty

This distribution is provided as is, without warranty of any kind. The terms of each component's license apply to that component.

## Building it yourself

1. Edit `requirements.txt` (pin versions if you want identical builds over time).
2. In the Actions tab, run the workflow "Build slim WinPython". The release tag is optional. If you leave it empty, the release is named after the WinPython release, the Python version and the UTC build time, for example `2026-03-py3.14.7-20261007-2215`. By default the workflow takes the dot build of the newest final WinPython release that has Python 3.14. Change `python_series` to use another Python version, or give a direct `base_url` to use a specific WinPython dot build.
3. The workflow builds the distribution, writes the package and license inventory into it, zips it, checks that the zip works from a different location, and publishes it as a release.
