## adobe photoshop 2023 flatpak for linux

### install

```shell
sudo flatpak remote-add flathub https://dl.flathub.org/repo/flathub.flatpakrepo
sudo flatpak remote-add gmanka https://gmanka-flatpaks.github.io/gmanka.flatpakrepo
flatpak install gmanka com.adobe.photoshop2023
```

### virtual desktop

by default, the virtual desktop mode is disabled, but if you have graphical bugs, you can enable the virtual desktop using the environment variable

run once with virtual desktop:

```bash
flatpak run --env=vd=1920x1080 com.adobe.photoshop2023
```

always run with virtual desktop:

```bash
sudo flatpak override --env=vd=1920x1080 com.adobe.photoshop2023
```

or if you installed it with --user:

```bash
flatpak override --user --env=vd=1920x1080 com.adobe.photoshop2023
```

### special thanks to

- @grisha765 for writing [manifest](https://github.com/grisha765/my_flatpak_repo/tree/main/io.github.grisha765.Photoshop)
- https://github.com/LinSoftWin/Photoshop-CC2022-Linux

