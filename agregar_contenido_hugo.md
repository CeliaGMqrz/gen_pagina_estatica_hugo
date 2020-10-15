## Agregar contenido

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