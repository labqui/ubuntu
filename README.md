<p align="center">
    <img src="m.webp" width="144" height="112">
</p>

# Dependências Iniciais

```
sudo apt-get update
sudo apt-get upgrade -y

sudo apt install build-essential default-jdk libssl-dev exuberant-ctags ncurses-term ack-grep silversearcher-ag fontconfig imagemagick libmagickwand-dev software-properties-common git vim-gtk3 curl -y


```


# Theme Ubuntu

```
cd ~/Documents
mkdir -p Projects && cd Projects
git clone https://github.com/daniruiz/flat-remix
git clone https://github.com/daniruiz/flat-remix-gtk
mkdir -p ~/.icons && mkdir -p ~/.themes
cp -r flat-remix/Flat-Remix* ~/.icons/ && cp -r flat-remix-gtk/Flat-Remix-GTK* ~/.themes/

sudo rm flat-remix -r
sudo rm flat-remix-gtk -r

sudo apt install gnome-tweak-tool fonts-hack-ttf -y

gsettings set org.gnome.desktop.interface gtk-theme "Flat-Remix-GTK-Blue-Dark"
gsettings set org.gnome.desktop.interface icon-theme 'Flat-Remix-Blue-Dark'
gsettings set org.gnome.desktop.interface cursor-theme 'DMZ-White'
gsettings set org.gnome.desktop.wm.preferences theme "Flat-Remix-GTK-Blue-Dark"
gsettings set org.gnome.desktop.background picture-uri 'file://FILE'

curl 'https://raw.githubusercontent.com/labqui/ubuntu/master/60315.jpg' -o ~/Pictures/background.jpg
gsettings set org.gnome.desktop.background picture-uri ~/Pictures/background.jpg


gnome-tweaks
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
sudo rm ~/.imwheelrc
echo "\".*\"" > ~/.imwheelrc
echo "    None, Up, Button4, 6" >> ~/.imwheelrc
echo "    None, Down, Button5, 6" >> ~/.imwheelrc
imwheel
```

# Configuração do Teclado RGB

```

sudo cd ~/Documents
sudo apt-get install build-essential libudev-dev qt5-default zlib1g-dev libappindicator-dev -y

git clone https://github.com/ccMSC/ckb.git ./ckb && cd ckb
sudo ./quickinstall && cd ..
sudo rm -f ./ckb -r

```

# Ambientes Virtuais

```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf
cd ~/.asdf
git checkout "$(git describe --abbrev=0 --tags)"

echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc


```
Como exemplo, instalar o NODE:

```

asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring

asdf plugin-list
asdf list-all nodejs
asdf install nodejs 13.11.0
asdf global nodejs 13.11.0


```

PHP:

```
asdf plugin-add php https://github.com/asdf-community/asdf-php.git
```

SSH:
```
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```
