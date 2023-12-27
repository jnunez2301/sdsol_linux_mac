# Contasol 2011 - Factusol 2011 Linux/Ubuntu

Este código se ha testeado en una Mac Book Pro que debido a problemas de comatibilidad se le ha instalado el Ubuntu 22.04 siendo la versión que da mejor compatibilidad con dicho dispositivo.

> Si eres usuario de una Mac Book Pro antigua te recomiendo encarecidamente instalar Ubuntu para evitar problemas de compatibilidad, aunque puedes intentar realizar estos metodos con brew a mi me fue una tarea imposible realizar la instalación con Hombrew.

## Instalar Wine

```
sudo dpkg --add-architecture i386
```

```
sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
```

```
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
```

```
sudo apt update
```

```
sudo apt install --install-recommends winehq-stable
```

## Instalar las dependencias con wine32

```
WINEARCH=win32 WINEPREFIX=~/wine32 winetricks jet40 mdac27 mdac28 mfc40 mfc42 vb6run
```

También con winetricks corriendo en wine64

```
winetricks jet40 mdac27 mdac28 mfc40 mfc42 vb6run
```



Comandos extra en caso de que de problemas de dependencias.

```
winetricks native_mdac
```
```
winetricks native_oleaut32
```

## Una vez tenemos el instalador de Factusol-2011/Contasol-2011

Ejecutamos el siguiente comando en la carpeta donde se ha descargado.

```
WINEARCH=win32 WINEPREFIX=~/wine32 wine nombre_instalador.msi
```
