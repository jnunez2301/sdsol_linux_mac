# Instalación de Factusol/Contasol MAC y Linux (sdsol_linux_mac)
 Instalación de programas contasol, factusol y la mayor parte de los software de SDSOL en Linux y Mac

Esta información es la que he recopilado de sitios web como:

* [Instalar Factusol en Linux con Wine](https://javiborrasbo.net/formacion/instalar-factusol-en-linux-con-wine/)
* [Como INstalar Factusol 2011 en Linux-Ubuntu](http://alejandrolopez123.com/110-linux/337-como-instalar-factusol-2011-en-linux-ubuntu)

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
| Hombre | [Enlace](https://brew.sh/)          |
| Zenity | [Enlace](https://formulae.brew.sh/formula/zenity) |

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

## Instando Wine

Ejecutar los siguientes comandos en consola

```
brew tap homebrew/cask-versions
```
Posteriormente
```
brew install --cask --no-quarantine wine-stable
```

Una vez finalizado necesitaremos Winetricks y Zenity, en algunas distribuciones de Mac Zenity ya viene instalado por defecto así que compruebalo ejecutando el comando 
> zenity --help

En la terminal y si muestra información sobre comandos del mismo lo tienes instalado.

## Instalación de Winetricks y Zenity

Para instalar **Winetricks** solo hace falta ejecutar el siguiente comando:

```
brew install winetricks
```

Y posteriormente instalamos Zenity

```
brew install zenity
```
Dependiendo de los recusos de tu ordenador podrá tardar desde minutos hasta un par de horas así que acomodate en el sofa y tomate tu tiempo.