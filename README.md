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
```
</details>

## Fildem V2
<details>
    <summary>Global menu en Gnome 42+</summary>
</details>
```
```
