# Configuracion-linux-macos


## Kinto para el teclado

<details>
    <summary>Convierte linux en macos</summary>
https://github.com/rbreaves/kinto

```
git clone https://github.com/rbreaves/kinto.git
cd kinto
sudo apt update
sudo apt install python3
./setup.py
```

Si falla, seguir las instrucciones e intentar de nuevo. Es automatico.

Inicia con
```
sudo systemctl start xkeysnail
```
</details>

## logiops-mxmaster3

<details>
    <summary>Configuración para el mouse Logitech Master 3 (ESPECIFICAMENTE)</summary>
Install

```
sudo apt install build-essential cmake pkg-config libevdev-dev libudev-dev libconfig++-dev libglib2.0-dev
cd ~/Downloads/
git clone https://github.com/PixlOne/logiops/
cd logiops
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make
sudo make install
cd ~/Downloads/
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

## Gnome Tweaks

<details>
    <summary>Herramientas para personalizar Gnome</summary>
```
sudo apt install gnome-tweaks
```
</details>


## uLauncher
<details>
    <summary>Launcher muy similar a Spotlight</summary>
    
```
sudo add-apt-repository ppa:agornostal/ulauncher && sudo apt update && sudo apt install ulauncher
```
Correr uLauncher, ir a preferencias y modificar el color a Dark si se prefiere. También habilitar "Launch at login"

![image](https://github.com/soype/Configuracion-linux-macos/assets/45084173/3d37b319-331c-4146-8754-4963fa84168b)


</details>

## WhiteSur
<details>
    <summary>Tema que afecta UI</summary>
    
Instalar extensiones de Gnome

### User Theme
https://extensions.gnome.org/extension/19/user-themes/

### Blur my shell
https://extensions.gnome.org/extension/3193/blur-my-shell/

Extensions viene instalado pero a veces tiene problemas. En caso de que las extensiones no se instalen, hacer esto:

```
rm -rf ~/.local/share/gnome-shell/extensions/
mkdir -p ~/.local/share/gnome-shell/extensions/
chown -R $USER:$USER ~/.local/share/gnome-shell/extensions/
```

Luego instalamos el theme

```
cd ~/Downloads
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1
cd WhiteSur-gtk-theme
sudo ./install.sh
```

### Agregar fuente SF PRO Display
```
cd ~/Downloads
git clone https://github.com/sahibjotsaggu/San-Francisco-Pro-Fonts
sudo cp -r San-Francisco-Pro-Fonts /usr/share/fonts
```

En Gnome Tweaks reemplazar las fuentes:
![image](https://github.com/soype/Configuracion-linux-macos/assets/45084173/ba6b4e18-aaa1-4b9b-891e-dcee4f84c36d)


</details>

## Fildem V2
<details>
    <summary>Global menu en Gnome 42+</summary>

```
sudo apt install libbamf3-dev bamfdaemon libkeybinder-3.0-dev appmenu-gtk2-module appmenu-gtk3-module unity-gtk-module-common python3-pip
cd ~/Downloads
git clone https://github.com/Weather-OS/Fildem-v2
cd Fildem-v2
sudo cp -r fildemGMenu@gonza.com ~/.local/share/gnome-shell/extensions
sudo python3 setup.py install --optimize=1
echo 'gtk-modules="appmenu-gtk-module"' >> ~/.gtkrc-2.0
```

Ir a ~/.config/gtk-3.0/ y abrir el archivo settings.ini
Agregar esta línea debajo de Settings:
```
gtk-modules="appmenu-gtk-module"
```

Log out / Reiniciar

Ir a Gnome Extensions y configurar a gusto

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

---------------------------------------------------------------------------------------------------

## FIN

#### Revisar que al inicio se ejecuten: Kinto, Plank, uLauncher y logid

---------------------------------------------------------------------------------------------------

## OPCIONALES

A partir de acá, todo es opcional. Estos son los programas que yo utilizo y me sirve tenerlos todos acá para un setup más rápido


## Brave Browser
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
