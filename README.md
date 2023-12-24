# Instalación de Factusol/Contasol MAC y Linux (sdsol_linux_mac)
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

Una vez instalado zenity vamos a abrir winetricks ejecutando el siguiente comando en la consola

> winetricks

Se nos va a mostrar una interfaz y seleccionamos las siguientes opciones:

1. Select the default wineprefix
2. Si es primera vez que se ejecuta preguntará si deseas enviar estadisticas, presionamos **si** y **aceptar**
3. Se nos mostrará otro cuadro de opciones seleccionamos **Install a Windows DLL or component**
4. Elegimos comctl32, jet40, mdac27, mdac28, mfc40, mfc42, vb6run
5. Pulsamos **aceptar** y decimos **si/yes** a todo.

> En caso de que nos muestre algun error ejecutar winetricks denuevo, pero con el siguiente comando

> sudo winetricks

Para que este tenga permisos de escritura sin ningún problema.

## Instalación de Factusol

Si eres afortunado y tienes el instalador con extensión .msi ejecuta el siguiente comando.

```
msiexec /l factusolinstalarweb.msi
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