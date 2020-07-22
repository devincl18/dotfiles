> This is step by step of archlinux installer 
>
> Using archlinux + i3wm

# Table of contents

# Must install
```
pacman -S git vim
```

# AUR packages
> Use yay

```
git clone https://aur.archlinux.org/yay-git.git
cd yay-git
makepkg -si
```

# Package manager
## Pamac
```
pacman -S base-devel
yay -S pamac-aur
```

## Snap
```
git clone https://aur.archlinux.org/snapd.git
cd snapd
makepkg -si
systemctl enable --now snapd.socket
ln -s /var/lib/snapd/snap /snap
```

## Flatpak
```
pacman -S flatpak
```

# Fonts
```
pacman -S ttf-hannom ttf-indic-otf adobe-source-han-sans-cn-fonts adobe-source-han-sans-tw-fonts adobe-source-han-sans-jp-fonts adobe-source-han-serif-jp-fonts adobe-source-han-sans-kr-fonts ttf-baekmuk noto-fonts-emoji ttf-font-awesome unicode-emoji adobe-source-code-pro-fonts ttf-dejavu
yay -S nerd-fonts-complete font-manager
fc-cache
```

# Dialog authentication
```
pacman -S polkit
yay -S polkit-explorer
```
z
# Appearance
## Lxappearance
```
pacman -S lxappearance
```

## Lightdm
- Copy background and logo to /usr/share/pixmaps/
- Chmod 777 for all file in directory
```
pacman -S lightdm-gtk-greeter-settings
```

## Picom
```
pacman -S picom
```

## I3-gaps
```
git clone https://github.com/terroo/i3-radius
cd i3-radius && sh build.sh
```

## I3lock
References: `https://github.com/pavanjadhaw/betterlockscreen`
```
pacman -S imagemagick feh xorg-xrandr xorg-xdpyinfo
yay -S i3lock-color betterlockscreen
```

## Dmenu
> Use Rofi
- Create `.config/rofi/config`
- Create `.config/rofi/example.rasi`. This is file template for rofi
- 

```
pacman -S rofi
```
# Touchpad
```
pacman -S xf86-input-snaptics
yay -S gpointing-device-settings
cp /usr/share/X11/xorg.conf.d/70-synaptics.conf /etc/X11/xorg.conf.d/
```
```
Section "InputClass"
    Identifier "touchpad"
    Driver "synaptics"
    MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
	Option "VertTwoFingerScroll" "on"
	Option "HorizTwoFingerScroll" "on"
	Option "PalmDetect" "1"
	Option "PalmMinWidth" "8"
	Option "PalmMinZ" "100"
EndSection
```
# Xrand
```
pacman -S lxrandr-gtk3

xrandr --output HDMI2 --mode 1920x1080 --right-of eDP1 --auto
```

# Config app
## UXrvt
- ColorSchema
- Urxvt appearance: Font, Letter, ...
- Keybind for navigations
- Copy, paste and other extensions use perls
```
pacman -S urxvt urxvt-perls
yay -S ttf-iosevka  urxvt-fullscreen urxvt-resize-font-git
```

## Bash
```
pacman -S powerline

Copy to ~/.bashrc
	powerline-daemon -q
	POWERLINE_BASH_CONTINUATION=1
	POWERLINE_BASH_SELECT=1
	. /usr/share/powerline/bindings/bash/powerline.sh

source ~/.bashrc
```
## Bar
- Install polybar `yay -S polybar`
- Create launcher in `.config/polybar/launch.sh`
- `chmod +x $HOME/.config/polybar/launch.sh`
- Add `exec_always --no-startup-id $HOME/.config/polybar/launch.sh`

## Vim
- Install Vim-plug 
# Optional app
## Sublime text 3
> Sublime text 3 with vim mode

```
{
	"ignored_packages": [],
	"font_options": ["bold"],
	"line_padding_top": 4,
	"line_padding_bottom": 4
}
```
## Screenshot
> Use gnome-screenshot
```
pacman -S gnome-screenshot
```
> Add to i3wm config
```
bindsym $mod+Print exec gnome-screenshot -i
```

## Joplin
```
wget -O - https://raw.githubusercontent.com/laurent22/joplin/master/Joplin_install_and_update.sh | bash
```

## Bleachbit
```
pacman -S bleachbit
```

## Imageviews
```
pacman -S imagemagick gpicview-gtk3
```

## File manager
> Use pcmanfm

```
pacman -S pcmanfm udisks2 gvfs
```

## Ibus
- install ibus
- Add `exec --no-startup-id ibus-daemon --xim -d -r` to `.config/i3/config`
```
pacman -S ibus ibus-anthy ibus-unikey
```
