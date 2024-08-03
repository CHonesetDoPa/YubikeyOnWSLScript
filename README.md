# YubikeyOnWSLScript
This is a Guide for wsl2 users to use yubikey easier.

# For English Users  
## install usbipd to attach yubikey https://github.com/dorssel/usbipd-win
## install necessary libs  
> sudo apt install yubico-piv-tool scdaemon pinentry-gtk2 opensc
## add ssh-agent to your shell env
> GPG_TTY=$(tty)
> export GPG_TTY
>
> eval $(ssh-agent -s) >/dev/null
## add GUI env to enable PIN input support.
> echo "pinentry-program /usr/bin/pinentry-gtk-2" >> ~/.gnupg/gpg-agent.conf

### If you use ubuntu24.04,add this in /etc/udev/rules.d/50-yubikey.rules  
>SUBSYSTEMS=="usb", ATTRS{idVendor}=="1050", ATTRS{idProduct}=="0407", GROUP="ch", MODE="0666",TAG+="uaccess"

### Due to unknown reasons, the udev rules only work for GPG signatures and not for PIV. If you need to use PIV, please use sudo.

# 对于中文用户

## 安装usbipd来附加yubikey https://github.com/dorssel/usbipd-win

## 安装必要的库
> sudo apt install yubico-piv-tool scdaemon pinentry-gtk2 opensc

## 将 ssh-agent 添加到您的 shell 环境
> GPG_TTY=$(tty)
> export GPG_TTY
>
> eval $(ssh-agent -s) >/dev/null

## 添加 GUI 环境以支持 PIN 输入
> echo "pinentry-program /usr/bin/pinentry-gtk-2" >> ~/.gnupg/gpg-agent.conf

### 如果你使用ubuntu24.04，把以下的内容放进 /etc/udev/rules.d/50-yubikey.rules
>SUBSYSTEMS=="usb", ATTRS{idVendor}=="1050", ATTRS{idProduct}=="0407", GROUP="ch", MODE="0666",TAG+="uaccess"

### 由于不知道的原因，udev规则只能适用于gpg的签名，无法使用piv，如果需要使用piv，请使用sudo
