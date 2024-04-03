# InfinityCam

# TODO:

- [ ] Sample image save for when running on a non-raspi device (only for testing)
- [ ] Save each image as new timestamped file instead of overwriting
- [ ] Gallery images view, incl. local and onchain images
- [ ] Wallet options for change seed, upload jwk file (through a webserver?)
- [ ] Options for creation of jwk for first time users
- [ ] Upload selected images from gallery to Arweave
- [ ] Wifi connection from Wifi Screen
- [ ] Image compression under 500kb
- [ ] Turbo sdk integration (through changing api or ardrive-cli)

## Components

<details>
<summary>Hardware</summary>

- Raspberry Pi 3b+ (or 4)
- Raspberry Pi Camera Module V3 (or any compatible camera module)
- 3.5" Touchscreen Display compatible with Raspberry Pi (or any compatible display)

Other common components such as a power supply, microSD card, keyboard, mouse, hdmi display etc.
</details>

<details>
<summary>Software</summary>

- Raspbian OS (or any linux based OS). I am running a headless version of Raspi OS Lite, with xorg and i3 setup to auto run a python kivy app on running startx and stop i3 on pressing `mod+x`
- Python3
- i3wm
- Xorg

</details>

## Setup

The following steps assume you are in a headless raspi os lite environment, with a logged in user and working internet.

<details>
<summary>Wifi (using raspi-config if not already setup)</summary>
    
```bash
sudo raspi-config
```

- Select Network Options
- Select Wi-fi
- Enter your SSID and password

</details>

<details>
<summary>Update and Upgrade always</summary>

```bash
sudo apt update
sudo apt upgrade
```

</details>

<details>
<summary>picam v3</summary>

Connect the camera module to the camera port using the ribbon cable.

No setup needed for 3b+.

pi 4: TBA

</details>

<details>
<summary>Touchscreen Display</summary>

TBA

</details>

<details>
<summary>Python GUI (pygame)</summary>

```bash
    python3 main.py
```

</details>

<details>
<summary>i3</summary>

Add this to the end of your i3 config file (usually located at ~/.config/i3/config)

```bash
bindsym $mod+x exec "i3-msg exit" # to stop the gui and exit i3
exec_always --no-startup-id python3 ~/camera.py # autostarts the gui when i3 starts
```

Set i3 as the default window manager with

```
sudo update-alternatives --config x-session-manager
sudo update-alternatives --config x-window-manager
```

To autostart i3 on boot, add a  cronjob (not recommended for dev setups)

```bash
crontab -e
```
and add `@reboot startx`

</details>
