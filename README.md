# Instalación de Factusol/Contasol MAC y Linux (sdsol_linux_mac)
> Si tienes una PC con buen rendimiento te recomiendo utilizar Virtual Box y montar una imagen de Windows 8 o superior siguiendo las especificaciones del programa.

> Funciona en las version 2011

> Se desconoce del funcionamiento en la versiones del 2014 en adelante ya que la mayor parte de estas son instaladas con petición al servidor, sin embargo igualmente se ha includo una guia para los archivos **.exe**

Instalación de programas contasol, factusol y la mayor parte de los software de SDSOL en Linux y Mac

Esta información es la que he recopilado de sitios web como:

* [Instalar Factusol en Linux con Wine](https://javiborrasbo.net/formacion/instalar-factusol-en-linux-con-wine/)

>> Si eres usuario de ubuntu esta guia será más que suficiente, si tu sistema linux no tiene una "tienda" tendrás que seguir el apartado **Guia de instalación en Linux**
* [Como Instalar Factusol 2011 en Linux-Ubuntu](http://alejandrolopez123.com/110-linux/337-como-instalar-factusol-2011-en-linux-ubuntu)
* Para Mac tuve que investigar por mi propia cuenta ya que ambos sistemas son similares.

## Dependencias

Para poder realizar una instalación adecuada y seguir la guia con facilidad se utilizarón las siguientes dependencias en los siguientes sitemas operativos:

* Mac: Hombrew, Wine y Winetricks.
* Linux: Wine y Winetricks 

# Guia de instalación en MAC

> Este método fue utilizado en Mac Os High Sierra 10.12 en una Mac Book Pro con un Intel Core 2 Duo 2.4ghz, 4GB de RAM y Gráfica GeForce 320M por lo que se entiende que funcionará para versiones posteriores o similares

Todos los comandos provienen de su documentación oficial la cual puedes consultar en:

| Dependencia |           Pagina oficial              |
|--|-------------------------------------|
| Wine |[Enlace](https://wiki.winehq.org/MacOS) | 
| Hombrew | [Enlace](https://brew.sh/)          |

> Recomiendo encarecidamente que copies y pegues los comandos en la consola para evitar cualquier errata que ocasione que el código no funcione corretamente.

## Instalando Hombrew
Antes de empezar debemos tener **hombrew** instalado y para ello ejecuta el siguiente comando en la terminal de Mac:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

En caso de que te encuentres con el error de que **/bin/bash not found o no ha sido encontrado **

Ejecuta el comando
```
sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

>Posteriormente te pedirá la contraseña de tu **usuario**, asegurate de escribirla correctamente

## Instando Wine en Mac

Ejecutar los siguientes comandos en consola

```
brew tap homebrew/cask-versions
```
Posteriormente
```
brew install --cask --no-quarantine wine-stable
```
En este caso se necesitará usar x32 así que usaremos el comando: 

>WINEARCH=win32 WINEPREFIX=~/.wine32 winecfg

Una vez finalizado necesitaremos Winetricks

En la terminal y si muestra información sobre comandos del mismo lo tienes instalado.

## Instalación de Winetricks

Para instalar **Winetricks** solo hace falta ejecutar el siguiente comando:

```
brew install winetricks
```

Dependiendo de los recusos de tu ordenador podrá tardar desde minutos hasta un par de horas así que acomodate en el sofa y tomate tu tiempo.

Comprobamos que se ha instalado
> winetricks

Instalamos dependencias

>También podemos simplificarlo ejecutando
```
winetricks comctl32 jet40 mdac27 mdac28 mfc40 mfc42 vb6run
```

```
WINEARCH=win32 WINEPREFIX=/path/to/your/wine/prefix winetricks comctl32 jet40 mdac27 mdac28 mfc40 mfc42 vb6run
```

> En caso de que nos muestre algun error ejecutar winetricks denuevo, pero con el siguiente comando

> winetricks

Para que este tenga permisos de escritura sin ningún problema.

## Instalación de Factusol/Contasol/DSOL

Si eres afortunado y tienes el instalador con extensión .msi ejecuta el siguiente comando.

```
msiexec /i nombre_archivo.msi
```
Si ese comando no funciona probar
```
msiexec /i nombre_archivo.msi /L*V install.log
```

En caso contrario desde la terminal iremos al escritorio donde podremos nuestro archivo de instalación:

Escribimos en la terminal los siguientes comandos

> ls
Para saber si aparece "Desktop", sino navegaremos hasta el mismo con el comando **cd**

```
cd Desktop
```

Una vez ahí nos aseguramos que esta el archivo otra vez hacemos
> ls

Si aparece instalador.exe o el nombre del archivo que le hayamos puesto, todo va bien así que procedemos con la instalación

```
wine nombre_del_archivo.exe
```

Se ejecutará el instalador y dependiendo del sistema pardeará algunas veces (es normal) por lo tanto esperamos hasta que nos aparezca un cuadro de instalación.

> Asegurate de elegir un directorio personalizado para la instalación ya que lo necesitarás más adelante.

## Guia de instalación en Linux

> Este código fue testeado en una Máquina Virtual de Kali linux

En linux tenemos un poco más de suerte y simplemente tendremos que ejecutar un par de comandos y instalador dos dependencias.

| Dependencia |           Pagina oficial              |
|--|-------------------------------------|
| Wine |[Enlace](https://wiki.winehq.org/Debian) | 
| Winetricks | [Enlace](https://wiki.winehq.org/Winetricks)          |

## Instalando Wine en Linux

Antes de empezar asegurate de tener actualizado tu sistema ejecutando el siguiente comando en la terminal:

```
sudo apt update && sudo apt upgrade -y
```

Peparando la máquina, si tu sistema esta en 64 bits, habilita la arquitectura de 32 bits:

```
sudo dpkg --add-architecture i386
sudo apt update
```
Añadimos el repositorio en caso de no tenerlo

```
sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
```

Actualizamos

```
sudo apt update
```

Instalamos Wine
```
sudo apt install --install-recommends winehq-stable
```

> Comprobamos que wine ha sido instalado

```
wine --version
```

## Instalando Winetricks en Linux

Si tenemos suerte este simple comando funcionará:

```
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install winetricks
```
Posteriormente lo abrimos
```
winetricks
```


En caso contrario seguiremos de la documentación oficial:

> [Winetricks Documentación Oficial](https://wiki.winehq.org/Winetricks)

Obteniendo winetricks:

```
cd "${HOME}/Downloads"
wget  https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks
chmod +x winetricks
```

Iniciamos winetricks por primera vez:

```
sh winetricks corefonts vcrun6 
```

Algunas dependencias requieren utilziar el Wineprefix:

```
env WINE=~/wine-git/wine sh winetricks mfc40, n_dependencia 
```

Se nos va a mostrar una interfaz y seleccionamos las siguientes opciones:

1. Select the default wineprefix
2. Si es primera vez que se ejecuta preguntará si deseas enviar estadisticas, presionamos **si** y **aceptar**
3. Se nos mostrará otro cuadro de opciones seleccionamos **Install a Windows DLL or component**
4. Elegimos comctl32, jet40, mdac27, mdac28, mfc40, mfc42, vb6run
5. Pulsamos **aceptar** y decimos **si/yes** a todo.

>También podemos simplificarlo ejecutando
```
sudo WINEARCH=win32 WINEPREFIX=/path/to/your/wine/prefix winetricks comctl32 jet40 mdac27 mdac28 mfc40 mfc42 vb6run
```

> En caso de que nos muestre algun error ejecutar winetricks denuevo, pero con el siguiente comando

> sudo winetricks

Para que este tenga permisos de escritura sin ningún problema.

## Instalación de Factusol/Contasol/DSOL

Si eres afortunado y tienes el instalador con extensión .msi ejecuta el siguiente comando.

```
msiexec /i nombre_archivo.msi
```
Si ese comando no funciona probar
```
msiexec /i nombre_archivo.msi /L*V install.log
```

En caso contrario desde la terminal iremos al escritorio donde podremos nuestro archivo de instalación:

Escribimos en la terminal los siguientes comandos

> ls
Para saber si aparece "Desktop", sino navegaremos hasta el mismo con el comando **cd**

```
cd Desktop
```

Una vez ahí nos aseguramos que esta el archivo otra vez hacemos
> ls

Si aparece instalador.exe o el nombre del archivo que le hayamos puesto, todo va bien así que procedemos con la instalación

```
wine nombre_del_archivo.exe
```

Se ejecutará el instalador y dependiendo del sistema pardeará algunas veces (es normal) por lo tanto esperamos hasta que nos aparezca un cuadro de instalación.

> Asegurate de elegir un directorio personalizado para la instalación ya que lo necesitarás más adelante.

## Notes
Test and Run in case of errors
```
exec=env WINEPREFIX="/home/kali/.wine" wine C: and so on

```

 >If you're having trouble with Wine and Mono (the open-source implementation of Microsoft's .NET Framework) on Linux, and it's not installed, you may need to install it manually. Here are steps to do that:

1. **Open a Terminal:**
   Open a terminal on your Linux system.

2. **Install Mono:**
   Use your package manager to install Mono. The command may vary depending on your Linux distribution. Here are examples for some popular distributions:

   - **Ubuntu/Debian:**
     ```bash
     sudo apt-get install mono-complete
     ```

   - **Fedora:**
     ```bash
     sudo dnf install mono-complete
     ```

   - **Arch Linux:**
     ```bash
     sudo pacman -S mono
     ```

   - **openSUSE:**
     ```bash
     sudo zypper install mono-complete
     ```

   Choose the appropriate command based on your distribution.

3. **Verify Mono Installation:**
   After installation, you can verify if Mono is installed by running:

   ```bash
   mono --version
   ```

   This should display information about the installed Mono version.

4. **Run Wine Configuration:**
   You may also want to run the Wine configuration tool (`winecfg`) to ensure that Mono is recognized by Wine. In the terminal, type:

   ```bash
   winecfg
   ```

   In the "Libraries" tab, make sure that "mscoree" is set to "Native (Windows)" and click "Apply" or "OK."

After these steps, Mono should be installed and recognized by Wine. If you encounter any issues during the installation or if you have a specific error message, please provide more details so that I can assist you further.
