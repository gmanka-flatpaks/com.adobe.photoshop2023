## adobe photoshop 2023 flatpak for linux

### install

```shell
sudo flatpak remote-add flathub https://dl.flathub.org/repo/flathub.flatpakrepo
sudo flatpak remote-add gmanka https://gmanka-flatpaks.github.io/gmanka.flatpakrepo
flatpak install gmanka com.adobe.photoshop2023
```

### local build guide

```shell
git clone https://github.com/gmanka-flatpaks/com.adobe.photoshop2023
cd com.adobe.photoshop2023
sed -i 's|photoshop2023_extra_data.yml|photoshop2023_local.yml|' com.adobe.photoshop2023.yml
curl https://github.com/gmanka-flatpaks/com.adobe.photoshop2023/releases/download/photoshop2023/photoshop2023.zip -Lo modules/photoshop2023/photoshop2023.zip
curl https://github.com/gmanka-flatpaks/com.adobe.photoshop2023/releases/download/photoshop2023/commonfiles_adobe_2023.zip -Lo modules/photoshop2023/commonfiles_adobe_2023.zip
flatpak --user remote-add flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install org.flatpak.Builder
flatpak run org.flatpak.Builder --user --install --install-deps-from=flathub --force-clean --repo=repo build com.adobe.photoshop2023.yml
flatpak build-bundle ./repo photoshop2023.flatpak com.adobe.photoshop2023
```

### wayland support

it works much better via xwayland, so i disabled wayland socket permission for this flatpak, but if you want to try native wayland, you can enable it via flatseal

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

