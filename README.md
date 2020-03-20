<div style="text-align:center; width:100%">
    <img src="m.webp" width="144" height="112">
</div>

# Dependências Iniciais

```
sudo apt-get update
sudo apt-get upgrade

sudo apt install git -y


```


# Theme Ubuntu

```
cd ~/Documents
mkdir -p Projects && cd Projects
git clone https://github.com/daniruiz/flat-remix
git clone https://github.com/daniruiz/flat-remix-gtk
mkdir -p ~/.icons && mkdir -p ~/.themes
cp -r flat-remix/Flat-Remix* ~/.icons/ && cp -r flat-remix-gtk/Flat-Remix-GTK* ~/.themes/
sudo apt install gnome-tweak-tool fonts-hack-ttf -y

gsettings set org.gnome.desktop.interface gtk-theme "Flat-Remix-GTK-Blue-Dark"
gsettings set org.gnome.desktop.interface icon-theme 'Flat-Remix--Blue-Dark'
gsettings set org.gnome.desktop.wm.preferences theme "Flat-Remix-GTK-Blue-Dark"

gnome-tweak
```

# Fonts

FiraCode

```
#!/usr/bin/env bash

fonts_dir="${HOME}/.local/share/fonts"
if [ ! -d "${fonts_dir}" ]; then
    echo "mkdir -p $fonts_dir"
    mkdir -p "${fonts_dir}"
else
    echo "Found fonts dir $fonts_dir"
fi

for type in Bold Light Medium Regular Retina; do
    file_path="${HOME}/.local/share/fonts/FiraCode-${type}.ttf"
    file_url="https://github.com/tonsky/FiraCode/blob/master/distr/ttf/FiraCode-${type}.ttf?raw=true"
    if [ ! -e "${file_path}" ]; then
        echo "wget -O $file_path $file_url"
        wget -O "${file_path}" "${file_url}"
    else
	echo "Found existing file $file_path"
    fi;
done

echo "fc-cache -f"
fc-cache -f
```


# Configurações do Mouse

```
sudo apt install imwheel
echo ".*" >> ~/.imwheelrc
echo "    None, Up, Button4, 8" >> ~/.imwheelrc
echo "    None, Down, Button5, 8" >> ~/.imwheelrc
imwheel
