# Configuracion-linux-macos


## Autokey configuracion en Español (Latinoamerica) de MacOS

<details>
    <summary>Configuración para el teclado</summary>

```
sudo apt install gnome-tweaks
sudo apt install dbus-x11
sudo apt install python3
sudo apt install autokey-gtk
cd ~/Descargas
git clone https://github.com/soype/autokey-gnome-macos-phrases
cd autokey-gnome-macos-phrases
chmod +x ./install.sh
sudo ./install.sh
sudo cp -r gnome-macos-phrases ~/.config/autokey/data
cd ~/.config/autokey/data/gnome-macos-phrases
tar -xvf command-link.tar.xz
git clone https://github.com/petrstepanov/gnome-macos-remap
cd gnome-macos-remap
chmod +x ./install.sh ./uninstall.sh
sudo ./install.sh
autokey-gtk
```

Configurar Autokey para que inicie al reiniciar

Ir a Gnome Tweaks y modificar esto:

![image](https://github.com/soype/autokey-gnome-macos-phrases/assets/45084173/23e55f50-eb2b-4358-b189-6f64145bf087)

</details>

## logiops-mxmaster3

<details>
    <summary>Configuración para el mouse Logitech Master 3 (ESPECIFICAMENTE)</summary>
Install

```
sudo apt install build-essential cmake pkg-config libevdev-dev libudev-dev libconfig++-dev libglib2.0-dev
cd ~/Descargas/
git clone https://github.com/PixlOne/logiops/
cd logiops
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make
sudo make install
cd ~/Descargas/
git clone https://github.com/soype/logiops-mxmaster3
cd logiops-mxmaster3
sudo cp ./logid.cfg /etc/
sudo systemctl enable --now logid
```


logid.cfg

```
devices: (
{
    name: "Wireless Mouse MX Master 3";
    smartshift:
    {
        on: false;
        threshold: 30;
        torque: 50;
    };
    hiresscroll:
    {
        hires: true;
        invert: true;
        target: false;
    };
    dpi: 1200;

    buttons: (
        {
            cid: 0xc3;
            action =
            {
                type: "Gestures";
                gestures: (
                    {
                        direction: "Up";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_UP"];
                        };
                    },
                    {
                        direction: "Down";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_DOWN"];
                        };
                    },
                    {
                        direction: "Right";
                        mode: "OnRelease";
                        action =
                        {
                            type: "Keypress";
                            keys: ["KEY_PLAYPAUSE"];
                        }
                    },
                    {
                        direction: "Left";
                        mode: "OnRelease";
                        action =
                        {
                            type: "CycleDPI";
                            dpis: [400, 600, 800, 1000, 1200, 1400, 1600];
                        };
                    }
                );
            };
        },
        {
            cid: 0xc4;
            action =
            {
                type: "Keypress";
                keys: ["KEY_A"];
            };
        }
    );
}
);
```

</details>

## Fildem V2
<details>
    <summary>Global menu en Gnome 42+</summary>

```
sudo apt install libbamf3-dev bamfdaemon libkeybinder-3.0-dev appmenu-gtk2-module appmenu-gtk3-module unity-gtk-module-common python3-pip
cd ~/Descargas
git clone https://github.com/Weather-OS/Fildem-v2
cd Fildem-v2
sudo cp -r fildemGMenu@gonza.com ~/.local/share/gnome-shell/extensions
sudo python3 setup.py install --optimize=1
echo 'gtk-modules="appmenu-gtk-module"' >> ~/.gtkrc-2.0
echo -e '[Settings]\ngtk-modules="appmenu-gtk-module"' >> ~/.config/gtk-3.0/settings.ini
```
</details>


## uLauncher
```
sudo add-apt-repository ppa:agornostal/ulauncher && sudo apt update && sudo apt install ulauncher
```
## WhiteSur
<details>
Instalar extensiones de Gnome

### User Theme
https://extensions.gnome.org/extension/19/user-themes/

### Blur my shell
https://extensions.gnome.org/extension/3193/blur-my-shell/

```
cd ~/Descargas
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1
cd WhiteSur-gtk-theme
sudo ./install.sh
```
</details>

## Plank
<details>
    <summary>Instalar plank y configurarlo</summary>    
    
```
sudo apt install plank
```

Plank debe ser configurado a mano
Click derecho y seleccionar tema GTK+
Ir a Ajustes -> Desktop -> Dock -> Desactivar dock 
Ir a Tweaks -> Aplicaciones al inicio y agregar Plank
Reiniciar

</details>

#### Revisar que al inicio se ejecuten: Autokey, Plank, uLauncher y logid

## OPCIONALES

A partir de acá, todo es opcional. Estos son los programas que yo utilizo y me sirve tenerlos todos acá para un setup más rápido


##[OPCIONAL] Brave Browser
<details>
    
```
sudo apt install curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-relse.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update
```

sudo apt install brave-browser

</details>

## BitWarden

<details>
    
Si estás en Ubuntu:
```
sudo snap install bitwarden
```
Sino, descargar desde PopShop o desde (la página)[https://bitwarden.com/download/]

</details>
