<p align="center">
    <img src="m.webp" width="144" height="112">
</p>

# Dependências Iniciais

```
sudo apt-get update
sudo apt-get upgrade -y

sudo apt install build-essential default-jdk libssl-dev exuberant-ctags ncurses-term ack-grep silversearcher-ag fontconfig imagemagick libmagickwand-dev software-properties-common git vim-gtk3 curl dconf-editor indicator-multiload -y

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


gsettings set org.gnome.desktop.background picture-options 'stretched'
gsettings set org.gnome.desktop.background primary-color '#898989'
gsettings set org.gnome.desktop.background secondary-color '#d8d8d8'
# desabilita a animação do menu
gsettings set org.gnome.shell.extensions.dash-to-dock animate-show-apps 'false'
# ação no botão do dock
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'focus-or-previews'



curl 'https://raw.githubusercontent.com/labqui/ubuntu/master/60315.jpg' -o ~/Pictures/background.jpg
gsettings set org.gnome.desktop.background picture-uri ~/Pictures/background.jpg


gnome-tweaks
```


```
sudo apt install dconf-editor
dconf-editor
#Procurar por "dash-to"
#Editar o "click-action" para mudar o comportamento do dock quando se clica no ícone
# configurar pra minimize-or-preview
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
echo "    None, Up, Button4, 5" >> ~/.imwheelrc
echo "    None, Down, Button5, 5" >> ~/.imwheelrc
imwheel
```

# Ambientes Virtuais

```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf
cd ~/.asdf
git checkout "$(git describe --abbrev=0 --tags)"

echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc


```
Como exemplo, instalar o:

```
asdf plugin-list
# Python
asdf plugin-add python

# NodeJS
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring

asdf list-all nodejs
asdf install nodejs 13.11.0
asdf global nodejs 13.11.0

# PHP
asdf plugin-add php https://github.com/asdf-community/asdf-php.git
asdf list-all php
asdf install php 7.4.4
asdf global php 7.4.4
```

SSH:
```
sudo apt-get install openssh-server
```

```
 sudo apt install wicd-gtk -y
 sudo apt remove network-manager-gnome network-manager -y
 sudo dpkg --purge network-manager-gnome network-manager
 
 # rodando .sh no click
 gsettings set org.gnome.nautilus.preferences executable-text-activation 'launch'
```
