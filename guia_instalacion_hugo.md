
# GUIA DE INSTALACIÓN HUGO

## ¿QUÉ ES HUGO? ¿EN QUÉ LENGUAJE ESTÁ ESCRITO?

**Hugo** es un generador de sitios web estáticos. Se caracteriza por ser muy rápido y seguro. 

Está escrito en un lenguaje llamado 'Go', inspirado en la sintaxis de C e intenta ser dinámico como python. Ha sido desarrolado por Google y es un proyecto opensource.

## Instalación de Hugo

En la página [oficial de hugo](https://gohugo.io/getting-started/installing/), cuando vamos a la opción de descargar en Debian y Ubuntu, nos indica que podemos hacer la descarga con apt desde los repositorios de debian, pero dice que no es recomendable ya que usan versiones más antiguas y no están actualizadas. Por lo que vamos a ir a GitHub, a los repositorios [oficiales de Hugo](https://github.com/gohugoio/hugo). Y vamos a hacer la instalación a partir de un sistema de gestión de paquetes de software libre llamado Homebrew.

### Un poco sobre **Homebrew**
Como hemos dicho es un **sistema de paquetería** de software libre, que entre otras características nos permite instalar software en nuestro directorio personal sin tener que utilizar permisos de superusuario. Tambíen podemos instalar software no empaquetado y permite tener versiones actualizadas aunque la distribución sea antigua.

### Instalación de Homebrew

* Necesitaremos instalar el siguiente paquete como requisito 

```sh
~$ sudo apt-get install build-essential curl file git
```

* Lo instalamos desde las fuentes. Creamos una carpeta llamada homebrew y en su interior clonamos el repositorio. Veremos que tenemos un ejecutable dentro de brew que es 'brew'.

```sh
~$ git clone https://github.com/Homebrew/brew ~/.linuxbrew/Homebrew
~$ mkdir homebrew
~$ celiagm@debian:~/github/homebrew/brew/bin$ ls
brew  hugo  patchelf
```

* Con eval cargamos como si de una variable se tratase el ejecutable de brew en la terminal actual. Con el siguiente comando se 'carga' de alguna forma 'brew' y a continuación ya podríamos usarlo.

```sh
~$ eval $(/home/celiagm/github/homebrew/brew/bin/brew shellenv)
```
### Instalar Hugo con Homebrew

* Instalamos hugo con brew, una vez cargada la argumentación con eval del ejecutable.

```sh
~$ brew install hugo
```

* Vamos a ver si la version que tenemos de hugo.

```sh
celiagm@debian:~$ hugo version
Hugo Static Site Generator v0.76.3/extended linux/amd64 BuildDate: unknown
```

### Crear nuestro proyecto

* Vamos a crear nuestro proyecto con Hugo, necesitamos un nombre para nuestro sitio. En mi caso lo he llamado **'unbitdeinformacioncadadia'**:

```sh
celiagm@debian:~$ hugo new site unbitdeinformacioncadadia
Congratulations! Your new Hugo site is created in /home/celiagm/unbitdeinformacioncadadia.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.

```
* Vamos al directorio que se ha generado y vemos los diferentes elementos:

```sh
celiagm@debian:~$ cd unbitdeinformacioncadadia/
celiagm@debian:~/unbitdeinformacioncadadia$ ls
archetypes  config.toml  content  data  layouts  static  themes
```


## ¿Qué sistema de plantillas utiliza Hugo?

Hugo usa archivos de plantilla para procesar contenido en HTML. Los archivos de plantilla son un puente entre el contenido y la presentación. La plantilla guía la presentación especificantdo el estilo a utilizar.

Hay tres tipos de plantillas: única, de lista y parcial. Nosotros vamos a utilizar la de **lista** ya que, lo que vamos hacer es un grupo de contenido relacionado. Es decir, tendrá una página de inicio que actuará como portal para el resto del contenido del sitio (Entradas del blog, etc.) 

Para configurar temas y nuestro sitio web sigue en [este enlace](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/configuracion_hugo_temas_contenido.md)