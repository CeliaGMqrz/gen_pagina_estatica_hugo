# CONFIGURACIÓN DE HUGO Y DE NUESTRO SITIO WEB

## CONFIGURACIÓN DE UN TEMA: FICHERO DE CONFIGURACIÓN (**config.toml**). 

### Descargar y añadir un tema

En esta [página](https://themes.gohugo.io/) hay muchos temas disponibles para hugo. Vamos a descargar el que más nos guste y se adapte a nuestros intereses y lo agregamos al directorio **themes**.

```sh
celiagm@debian:~/unbitdeinformacioncadadia/themes$ git submodule add https://github.com/rhazdon/hugo-theme-hello-friend-ng.git
Clonando en '/home/celiagm/unbitdeinformacioncadadia/themes/hugo-theme-hello-friend-ng'...
remote: Enumerating objects: 1890, done.
remote: Total 1890 (delta 0), reused 0 (delta 0), pack-reused 1890
Recibiendo objetos: 100% (1890/1890), 6.77 MiB | 6.64 MiB/s, listo.
Resolviendo deltas: 100% (1026/1026), listo.
celiagm@debian:~/unbitdeinformacioncadadia/themes$ ls
hugo-theme-hello-friend-ng

```

* Lo primero que tenemos que hacer es mirar la estructura de carpetas que viene en el tema que hemos descargado y cómo funciona. En mi caso como podemos ver a continuación, tenemos varios directorios dentro de nuestro tema elegido.

```sh
celiagm@debian:~/unbitdeinformacioncadadia$ cd themes/hugo-theme-hello-friend-ng/
celiagm@debian:~/unbitdeinformacioncadadia/themes/hugo-theme-hello-friend-ng$ ls
archetypes  CHANGELOG.md     data  exampleSite  images   LICENSE.md  static
assets      CONTRIBUTING.md  docs  i18n         layouts  README.md   theme.toml

```
``` sh
celiagm@debian:~/unbitdeinformacioncadadia/themes/hugo-theme-hello-friend-ng/exampleSite$ ls
config.toml  content  resources
```

* Vamos a copiar todo el contenido de **exampleSite** y lo vamos a pegar en la carpeta principal de nuestro sitio web. De esta forma, mezclaremos la información que tenemos ahora con el ejemplo para poder configurar bien el tema.

* Veremos que nuestro fichero de configuración **config.toml** ha cogido la forma de nuestro ejemplo:

``` sh
celiagm@debian:~/unbitdeinformacioncadadia/themes/hugo-theme-hello-friend-ng/exampleSite$ cat config.toml 
baseURL = "https://example.com"
title   = "Hello Friend NG"
languageCode = "en-us"
theme = "hello-friend-ng"

PygmentsCodeFences = true
PygmentsStyle = "monokai"

paginate  = 10
rssLimit  = 10  # Maximum number of items in the RSS feed.
copyright = "This work is licensed under a Creative Commons Attribution-NonCommercial 4.0 International License." # This message is only used by the RSS template.

# googleAnalytics = ""
# disqusShortname = ""

archetypeDir = "archetypes"
contentDir   = "content"
dataDir      = "data"
layoutDir    = "layouts"
publishDir   = "public"

buildDrafts  = false
buildFuture  = false
.
. 
. 

```
* Ahora tenemos que cambiar los siguientes datos para configurar nuestro sitio. Como no tenemos ningun servicio ahora mismo para poner la **URL** vamos a configurarlo en nuestro localhost. Le dejamos el idioma así y le ponemos el **título** de nuestro sitio web y el **nombre del directorio con el tema que hemos descargado de git**. El resto del contenido lo dejamos tal cual.

```sh

baseURL = "localhost"
languageCode = "en-us"
title = "Un bit de informacion cada día"
theme = "hugo-theme-hello-friend-ng"

.
.
.

```

* Tambien en este fichero vamos a cambiar algunos parámetros que nos deja hacer hugo en su configuración, como son los de las redes sociales:

```sh
  # Social icons

  [[params.social]]
    name = "email"
    url  = "mailto:cg.marquez@gmail.com"

  [[params.social]]
    name = "github"
    url  = "https://github.com/CeliaGMqrz"
    

  [[params.social]]
    name = "linkedin"
    url  = "https://www.linkedin.com/in/cgmarquez/"
``` 

* Nos quedaremos con el idioma en ingles:

```sh
[languages]
  [languages.en]
    subtitle  = "Hello Friend NG Theme"
    weight    = 1
    copyright = '<a href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank" rel="noopener">CC BY-NC 4.0</a>'

```

* Veremos que también podemos configurar el menú de nuestro sitio web. Este es muy sencillo solo tenemos dos páginas, el de contacto y el blog, hemos editado los parámetros para cambiar de nombre nuestro menú:

```sh
[menu]
  [[menu.main]]
    identifier = "about"
    name       = "Contacto"
    url        = "about/"
  [[menu.main]]
    identifier = "posts"
    name       = "Blog"
    url        = "posts/"

```

* A continuación vamos a ejecutar el siguiente comando para visualizar nuestro sitio en nuestro entorno de desarrollo. 

```sh
$ hugo server -D
```
Salida:

```sh
Start building sites … 

                   | EN | FR  
-------------------+----+-----
  Pages            | 48 | 21  
  Paginator pages  |  1 |  0  
  Non-page files   |  0 |  0  
  Static files     | 12 | 12  
  Processed images |  0 |  0  
  Aliases          | 24 |  7  
  Sitemaps         |  2 |  1  
  Cleaned          |  0 |  0  

Built in 138 ms
Watching for changes in /home/celiagm/unbitdeinformacioncadadia/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /home/celiagm/unbitdeinformacioncadadia/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at //localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop

```

![captura_plantilla1.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/captura_plantilla1.jpeg)



Si quieres seguir la guía para agregar contenido accede a este [enlace](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/agregar_contenido_hugo.md)