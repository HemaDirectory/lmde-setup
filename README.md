# 🐧 إعداد نظام Linux Mint Debian Edition (LMDE) بعد التثبيت

هذا المستودع يوضح الخطوات التفصيلية التي يجب اتباعها بعد تثبيت LMDE لضمان إعداد النظام بشكل مثالي.

---

## 📌 الفهرس

1. [خطوات ما بعد التثبيت](#1-خطوات-ما-بعد-التثبيت)
2. [الثيم والتخصيص](#2-الثيم-والتخصيص)
3. [دعم الكتابة باللغة العربية](#3-دعم-الكتابة-باللغة-العربية)
4. [تثبيت التطبيقات الأساسية](#4-تثبيت-التطبيقات-الأساسية)
5. [تثبيت التعريفات](#5-تثبيت-التعريفات)
6. [تثبيت الألعاب والمحاكيات](#6-تثبيت-الألعاب-والمحاكيات)

---

## 1. 🛠️ خطوات ما بعد التثبيت

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -f
sudo apt autoremove
sudo apt autoclean
```
### تفعيل الجدار الناري:

```bash
sudo apt install ufw
sudo ufw enable
```

### تفعيل النسخ الاحتياطي:

```bash
sudo timeshift-gtk
```

## 2. 🎨 الثيم والتخصيص

```bash
sudo apt install arc-theme papirus-icon-theme
```

### تغيير الثيم من:

System Settings → Themes →  اختر Arc / Papirus

## 3. 🌐 دعم الكتابة باللغة العربية

تفعيل لوحة المفاتيح العربية:

    افتح Keyboard من الإعدادات.

    انتقل إلى Layouts.

    أضف اللغة العربية (Arabic).

    حدد اختصار التبديل بين اللغات (مثل: Alt+Shift أو Ctrl+Space).

ضبط الخطوط لدعم أفضل للعربية:

```bash
sudo apt install ttf-mscorefonts-installer fonts-crosextra-caladea fonts-crosextra-carlito
```

## 4. 💻 تثبيت التطبيقات الأساسية

```bash
sudo apt install build-essential curl wget gpg git gnome-disk-utility gparted vlc mpv synaptic p7zip-full rar unrar
```

برامج إضافية عبر Flatpak:

```bash
flatpak install flathub com.obsproject.Studio
flatpak install flathub com.visualstudio.code
flatpak install flathub org.mozilla.Thunderbird
flatpak install flathub org.telegram.desktop
flatpak install flathub org.onlyoffice.desktopeditors
```
YouTube Apps - تطبيقات صناعة المحتوى

```bash
sudo apt install gimp audacity inkscape obs-studio kdenlive
```

متقدم تخصيص الطرفية

NerdFont
```bash
mkdir -p ~/.local/share/fonts \
&& cd ~/.local/share/fonts \
&& curl -OL https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.tar.xz \
&& bash -c 'mkdir "${1%.tar.xz}" && tar -xf "$1" -C "${1%.tar.xz}"' _ JetBrainsMono.tar.xz \
&& rm JetBrainsMono.tar.xz \
&& fc-cache -fv
```
Starship

1.Install 
```bash
curl -sS https://starship.rs/install.sh | sh
```
2.Add it to bashrc
```bash
echo 'eval "$(starship init bash)"' >> ~/.bashrc
```
fzf

1.Use the official script 
```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
2.And add the following line to your shell configuration file
```bash
# Set up fzf key bindings and fuzzy completion
eval "$(fzf --bash)"
```
eza

1.Install eza via: 
```bash
sudo mkdir -p /etc/apt/keyrings \
&& wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg \
&& echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list \
&& sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list \
&& sudo apt update \
&& sudo apt install -y eza
```
2.Add alias to .bashrc
```bash
nano ~/.bashrc
```
```bash
alias ls='eza --color=auto --icons=auto'
alias eza='eza --color=auto --icons=auto'
alias ll='eza -l'
alias la='eza -lah'
alias lt='eza -T'
```

## 5. ⚙️ تثبيت التعريفات (Drivers)

افتح أداة التعريفات:

```bash
sudo mint-drivers
```
اختر التعريفات الموصى بها، مثل NVIDIA أو Broadcom.

## 6. 🎮 تثبيت الألعاب والمحاكيات

مشغلات الألعاب:
```bash
sudo apt install steam
flatpak install flathub net.lutris.Lutris
flatpak install flathub com.heroicgameslauncher.hgl
```
المحاكيات:
```bash
flatpak install flathub org.libretro.RetroArch
flatpak install flathub org.ppsspp.PPSSPP
flatpak install flathub org.DolphinEmu.dolphin-emu
```

