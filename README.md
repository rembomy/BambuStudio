![image](https://user-images.githubusercontent.com/106916061/179006347-497d24c0-9bd6-45b7-8c49-d5cc8ecfe5d7.png)
# BambuStudio
Bambu Studio is a cutting-edge, feature-rich slicing software.  
It contains project-based workflows, systematically optimized slicing algorithms, and an easy-to-use graphic interface, bringing users an incredibly smooth printing experience.

Prebuilt Windows, macOS 64-bit and Linux releases are available through the [github releases page](https://github.com/bambulab/BambuStudio/releases/).

Bambu Studio is based on [PrusaSlicer](https://github.com/prusa3d/PrusaSlicer) by Prusa Research, which is from [Slic3r](https://github.com/Slic3r/Slic3r) by Alessandro Ranellucci and the RepRap community.

See the [wiki](https://github.com/bambulab/BambuStudio/wiki) and the [documentation directory](https://github.com/bambulab/BambuStudio/tree/master/doc) for more information.

# What are Bambu Studio's main features?
Key features are:
- Basic slicing features & GCode viewer
- Multiple plates management
- Remote control & monitoring
- Auto-arrange objects
- Auto-orient objects
- Hybrid/Tree/Normal support types, Customized support
- multi-material printing and rich painting tools
- multi-platform (Win/Mac/Linux) support
- Global/Object/Part level slicing parameters

Other major features are:
- Advanced cooling logic controlling fan speed and dynamic print speed
- Auto brim according to mechanical analysis
- Support arc path(G2/G3)
- Support STEP format
- Assembly & explosion view
- Flushing transition-filament into infill/object during filament change

# How to compile
Following platforms are currently supported to compile:
- Windows 64-bit, [Compile Guide](https://github.com/bambulab/BambuStudio/wiki/Windows-Compile-Guide)
- Mac 64-bit, [Compile Guide](https://github.com/bambulab/BambuStudio/wiki/Mac-Compile-Guide)
- Linux, [Compile Guide](https://github.com/bambulab/BambuStudio/wiki/Linux-Compile-Guide)
  - currently we only provide linux appimages on [github releases](https://github.com/bambulab/BambuStudio/releases) for Ubuntu/Fedora, and a [flathub version](https://flathub.org/apps/com.bambulab.BambuStudio) can be used for all the linux platforms

On Fedora 44, with the development packages listed in `linux.d/fedora` installed, build the checked-out source and a beta AppImage with:

```bash
./BuildLinux.sh -cd
./BuildLinux.sh -s -t 2
./BuildLinux.sh -i
```

The native executable is `build/src/bambu-studio`; the AppImage is `build/BambuStudio_ubu64.AppImage`.
Beta builds use `~/.config/BambuStudioBeta` by default. To try the beta with a separate copy of your existing settings and presets, run:

```bash
cp -a "$HOME/.config/BambuStudio" "$HOME/.config/BambuStudio-beta-test"
./build/BambuStudio_ubu64.AppImage --datadir "$HOME/.config/BambuStudio-beta-test"
```

The copy keeps beta changes out of the release profile. On NVIDIA systems, the build disables WebKitGTK's DMA-BUF renderer to avoid blank web views; set `WEBKIT_DISABLE_DMABUF_RENDERER=0` before launch to override this workaround. The AppImage launcher selects `Adwaita:dark` when GNOME reports `Adwaita-dark`; an existing `GTK_THEME` value takes precedence. For the native executable, use `GTK_THEME=Adwaita:dark build/src/bambu-studio --datadir "$HOME/.config/BambuStudio-beta-test"` when the editor panels remain light.

The copy alone does not select the copied profile. Pass `--datadir` on every launch; opening the AppImage from a file manager or Gearlever without that option uses `~/.config/BambuStudioBeta`. To use the default path instead, close Studio and copy the contents of `~/.config/BambuStudio` into `~/.config/BambuStudioBeta`, preserving any existing beta profile first.

# Report issue
You can add an issue to the [github tracker](https://github.com/bambulab/BambuStudio/issues) if **it isn't already present.**

# License
Bambu Studio is licensed under the GNU Affero General Public License, version 3. Bambu Studio is based on PrusaSlicer by PrusaResearch.

PrusaSlicer is licensed under the GNU Affero General Public License, version 3. PrusaSlicer is owned by Prusa Research. PrusaSlicer is originally based on Slic3r by Alessandro Ranellucci.

Slic3r is licensed under the GNU Affero General Public License, version 3. Slic3r was created by Alessandro Ranellucci with the help of many other contributors.

The GNU Affero General Public License, version 3 ensures that if you use any part of this software in any way (even behind a web server), your software must be released under the same license.

The bambu networking plugin is based on non-free libraries. It is optional to the Bambu Studio and provides extended networking functionalities for users.
By default, after installing Bambu Studio without the networking plugin, you can initiate printing through the SD card after slicing is completed.
