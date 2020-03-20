<div style="text-align:center; width:100%">
    <img src="m.webp" width="144" height="112">
</div>

# Configurações do Mouse

```
sudo apt install imwheel

gedit ~/.imwheelrc

```
Conteúdo para o wheel será
```
# Speed up scrolling for the document viewer
".*"
    None, Up, Button4, 8
    None, Down, Button5, 8
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
