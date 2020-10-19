# Automatizar cambios y generar web

### Escenario

Se ha generado la carpeta public con el código html generado por hugo. Pero resulta que al desplegar en netlify se ve mal el sitio web. ¿Qué está pasando?. Bien, debemos tener en cuenta que, en el fichero de configuración de nuestro sitio (config.toml), teniamos puesta una URL 'localhost' que no es la que vamos a utlizar para nuestro sitio web en Netlify. Es decir debemos de cambiar la URL en el fichero de configuración. Vamos a editar el fichero y lo guardamos. Lo que tendriamos que hacer manualmente sería volver a generar la carpeta public y dentro de la carpeta public decirle los cambios a git y subirlos al repositorio. Pero lo vamos hacer automático con un script en bash.

* El siguiente script en bash se ejecutaria desde la carpeta public una vez el contenido se haya generado. De manera que añade todo el contenido del directorio, hace un commit 'automatico', utlizamos pull por si hay que sobreescribir y finalmente push para subir el contenido.

```sh
#!/bin/bash


git add *
git commit -m "commit automatico"
git pull
git push


```

* El script anterior no está completo, pues necesitamos que, dentro de nuestro proyecto se genere la carpeta public.

* Primero vamos a editar el fichero de configuración y le ponemos la url adecuada.

```sh
celia@debian:~/sitioweb/unbitdeinformacioncadadia$ ls
archetypes        config.toml  data     netlify.toml  resources  themes
auto_git_hugo.sh  content      layouts  public        static
celia@debian:~/sitioweb/unbitdeinformacioncadadia$ nano config.toml 

```

* El script que vamos a ejecutar es el siguiente. Genera la carpeta public, entra en ella, copia todo el contenido en nuestro repositorio, indicando la ruta absoluta. Luego añade con git todos los elementos. Marca el commit automático. Y subimos el contenido.

```sh
#!/bin/bash

hugo -D
cd public
cp -r * /home/celia/sitioweb/public_prueba_hugo
cd /home/celia/sitioweb/public_prueba_hugo
git add *
git commit -m "commit automatico"
git pull
git push


```

* Lo ejecutamos dentro de nuestro proyecto. ¡¡Si van a usar este script tiene que editar la ruta absoluta dirigida hacia su repositorio!!

```sh

celia@debian:~/sitioweb/unbitdeinformacioncadadia$ bash auto_git_hugo.sh 
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

Total in 49 ms
[main df7a77e] commit automatico
 37 files changed, 366 insertions(+), 366 deletions(-)
 rewrite tags/instalacion-visualcode/page/1/index.html (69%)
 rewrite tags/instalar-virtualbox/page/1/index.html (68%)
Already up-to-date.
Counting objects: 70, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (47/47), done.
Writing objects: 100% (70/70), 7.26 KiB | 0 bytes/s, done.
Total 70 (delta 36), reused 0 (delta 0)
remote: Resolving deltas: 100% (36/36), completed with 16 local objects.
To github.com:CeliaGMqrz/public_prueba_hugo.git
   9301ecc..df7a77e  main -> main

```

* Comprobamos que se ha actualizado y se ve la página perfectamente.

![captura_prueba.jpeg](https://github.com/CeliaGMqrz/gen_pagina_estatica_hugo/blob/main/capturas/captura_prueba.jpeg)