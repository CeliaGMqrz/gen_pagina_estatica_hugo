## Agregar y modificar contenido

Esta página estática la voy a emplear para tener un blog personal en la que publicaré mis conocimientos sobre lo que vaya aprendiendo en cuanto a la informática.

* Vamos a crear el nuevo contenido. Por ejemplo vamos a introducir una guia de instalación para instalar VirtualBox

```sh
$ hugo new posts/instalacion_Vbox_debian.md

```
Salida:
```sh
/home/celiagm/unbitdeinformacioncadadia/content/posts/instalacion_Vbox_debian.md created
```
* Vemos que se crea el contenido en el directorio **content/posts**. Vamos a editar el fichero que hemos creado en markdown y lo que vemos dentro del fichero md es un front matter, en él vamos a añadir etiquetas que nos interesen para este sitio. Además vamos a cambiar el **draft**, que es como un modo borrador, le ponemos 'false' para desactivarlo y que se publique. Justo despues del front matter añadimos el contenido en markdown:

```sh
---
title: "Instalacion_Vbox_debian"
date: 2020-10-14T19:29:24+02:00
draft: false
toc: false
images:
tags : ["VirtualBox","virtualbox","instalacion de virtualbox","linux","Debian Buster","Debian 10"]
---

Aquí se agrega el contenido en markdown.
```

* No hace falta parar el servicio de hugo porque se hacen los cambios en caliente y en tiempo real. Cuando insertemos la entrada nueva veremos que efectivamente se ha cambiado y además de una forma muy rápida, que es una de las mejores características de hugo.

![post1.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/post1.jpeg)


* De igual forma como hemos agregado contenido podemos modificarlo. Tenemos la página **about.md**, la cual vamos a modificar, con la diferencia de que vamos a añadirle una imagen. Es tan simple como saber la sintaxis de markdown y poner la ruta adecuada. En este caso para poner la imagen hemos puesto lo siguiente:

![aboutcode.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/aboutcode.jpeg)

![aboutcaptura.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/aboutcaptura.jpeg)


## PERSONALIZAR TEMA CON HOJA DE ESTILO CSS

Podemos dar un cambio a nuestra página principal, para ello vamos a nuestro fichero de configuración y en los parámetros indicamos la hoja de estilo de esta forma:

```sh
[params]
  dateform        = "Jan 2, 2006"
  dateformShort   = "Jan 2"
  dateformNum     = "02/01/2006"
  dateformNumTime = "02/01/2006 15:04"
  css = ["css/style.css"]
```

* Creamos otra carpeta dentro de **static** y en su interior un archivo **style.css**, a continuación vamos a darle el estilo que queramos, esto se aplicará a la página principal. Hemos identificado cada parte de nuestra página y la hemos modificado. Se ha cambiado el fondo por una imagen y se ha cambiado el tamaño y posicion de los titulos y subtitulos.

```sh
body.dark-theme {
    background-image: url(/images/universo.jpg);
	text-align: center;
	background-position: center 1%;
	background-size: cover;
	background-repeat: no-repeat;
	position: center;
  }

.body.dark-theme:before {
	content:'';
	position: absolute;
    top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	background-color: rgba(0,0,0,0.1);
}

  .nav-container img {
    height: 40px;
  }
  .post-title, .catalogue-title {
    color: #283d7e;
  }
  .nav a {
    color: #0768ce;
  }

  h1 {
      background-color: rgba(0,0,0,0.1);
      text-shadow: 2px 3px black;
      color: plum;
      font-size: 50px;
      color: #fff;
      position: relative
  }

  p {
      color: white;
      text-shadow: 1px 2px black;
      font-size: 25px;
      font-weight: bold;
  }

  svg {
    background-color: rgba(0,0,0,0.7);
      color: white;
      font-weight: bold;
  }
```

Así se ve nuestra página con el css que hemos implementado:

![captura2.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/captura2.jpeg)

## Generar el sitio estático

Necesitaremos generar el código de nuestro sitio web, para ello haremos lo siguiente:

```sh
celiagm@debian:~/unbitdeinformacioncadadia$ hugo -D
```

Salida:

```sh
Start building sites … 

                   | EN  
-------------------+-----
  Pages            | 25  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 20  
  Processed images |  0  
  Aliases          | 12  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 41 ms

```

* Veremos que se nos genera el directorio **public**:

```sh
celiagm@debian:~/unbitdeinformacioncadadia$ ls
archetypes  config.toml  content  data  layouts  public  resources  static  themes
celiagm@debian:~/unbitdeinformacioncadadia$ cd public/
celiagm@debian:~/unbitdeinformacioncadadia/public$ ls
404.html
about
about-hugo
about-us
bundle.min.dc716e9092c9820b77f96da294d0120aeeb189b5bcea9752309ebea27fd53bbe6b13cffb2aca8ecf32525647ceb7001f76091de4199ac5a3caa432c070247f5b.js
categories
contact
css
fonts
images
index.html
index.xml
main.393856bf2c430bb6c01d7af07c6fe966e7cce8073435cfbbc46e590bab7405ef.css
main.css.map
posts
robots.txt
series
sitemap.xml
tags

```

* Este directorio será el que vamos a desplegar en Netlify.

Sigue en este enlace para continuar la guía -> [Despliegue en Netlify](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/despliegue_netlify.md)