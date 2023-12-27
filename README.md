# Contasol 2011 - Factusol 2011 Linux/Ubuntu

Este código se ha testeado en una Mac Book Pro que debido a problemas de comatibilidad se le ha instalado el Ubuntu 22.04 siendo la versión que da mejor compatibilidad con dicho dispositivo.

## Instalar Wine

> sudo dpkg --add-architecture i386 

```
sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
```

> sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources

> sudo apt update

> sudo apt install --install-recommends winehq-stable

> winetricks jet40 mdac27 mdac28 mfc40 mfc42 vb6run



Comandos extra en caso de que de problemas de dependencias.

> winetricks native_mdac
> winetricks native_oleaut32


> WINEARCH=win32 WINEPREFIX=~/wine32 winecfg

> WINEARCH=win32 WINEPREFIX=~/wine32 winetricks jet40 mdac27 mdac28 mfc40 mfc42 vb6run
