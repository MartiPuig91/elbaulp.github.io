---
author: alex
categories:
- script
color: '#2196F3'
description: "Hace poco me encontr\xE9 queriendo ordenar una carpeta de fondos de
  pantalla por resoluci\xF3n, en lugar de otros m\xE9todos de ordenaci\xF3n m\xE1s
  t\xEDpicos como por nombre o tama\xF1o. As\xED que buscando un poco encontr\xE9
  la respuesta en *superuser*. El usuario flammable preguntaba c\xF3mo ordenar im\xE1genes
  por resoluci\xF3n. La respuesta es la siguiente:"
image: 2012/07/sh.png
lastmod: 2015-12-24
layout: post.amp
mainclass: linux
permalink: /como-ordenar-imagenes-por-resolucion/
tags:
- identify
- imagenes por resolucion
- "ordenar por resoluci\xF3n"
title: "C\xF3mo ordenar im\xE1genes por resoluci\xF3n"
---

<figure>
<a href="/img/2012/07/sh.png"><amp-img on="tap:lightbox1" role="button" tabindex="0" layout="responsive" src="/img/2012/07/sh.png" title="{{ page.title }}" alt="{{ page.title }}" width="128px" height="128px" /></a>
</figure>

Hace poco me encontré queriendo ordenar una carpeta de fondos de pantalla por resolución, en lugar de otros métodos de ordenación más típicos como por nombre o tamaño. Así que buscando un poco encontré la respuesta en *superuser*. El usuario *[flammable][1]* preguntaba cómo ordenar imágenes por resolución. La respuesta es la siguiente:

<!--more--><!--ad-->

## El script

```bash
#!/bin/bash

for image in *.jpg *.JPG *.jpeg *.JPEG *.gif *.GIF *.bmp *.BMP *.png *.PNG;
do
   res=$(identify -format %wx%h\\n "$image");
   mkdir -p $res;
   mv "$image" $res;
done

```

Yo lo modifiqué un poco acorde a mis necesidades:

```bash
#!/bin/bash

cd /ruta/mis/fondos

for image in *.jpg *.png;
do
   res=$(identify -format %wx%h\\n "$image");
   mkdir -p /tmp/fondos/$res;
   cp "$image" /tmp/fondos/$res;
done

```

Para no modificar las imágenes originales, ya que están en *Drive*, y así poder seleccionar las que eliminar posteriormente.

## Qué hace el script

  * Recorrer todas las imágenes de una carpeta.
      * El comando **identify** describe el formato y características de una o más imágenes, en concreto:
          * `-format %wx%h\\n "$image"`: muestra la resolución de la imagen `$image` en formato *width x height*.
          * Se crea una carpeta nombrándola con la resolución de la imágen.
          * Se copia la imagen a la carpeta.

Tras ésto, tenemos organizadas todas las imágenes en carpetas por resolución. Mi objetivo era eliminar las de menor resolución, así que fui apuntando dichas imágenes para luego borrarlas en la carpeta original (La de Drive), donde están todas juntas. Tras almacenar en un archivo los nombres de las imágenes a borrar, ejecuté el siguiente comando en la carpeta original:

```bash
for i in $(cat ../ABorrar)
do
   find /Carpeta/original/ -iname $i -exec rm '{}' \;
done

```

## Renombrar las imágenes para que contengan su resolución

Como menciona Juanjo en el comentario, otra opción más adecuada es [renombrar][2] cada imagen con su resolución, para ello el siguiente script podría servir:

```bash
#!/bin/bash

cd /ruta/imagenes/

for image in *.jpg *.png;
do
    res=$(identify -format %wx%h\\n "$image");
    rename "s/^/[$res] - /" "$image"
done

```

Así, las imágenes quedarán, por ejemplo, `[1280x1024] - nombre original.jpg`.

#### Referencias

*How to sort images into folders, based on resolution?* »» <a href="http://superuser.com/questions/17562/how-to-sort-images-into-folders-based-on-resolution" target="_blank">superuser.com</a>



 [1]: http://superuser.com/users/4421/flammable
 [2]: https://elbauldelprogramador.com/renombrar-archivos-masivamente-en/ "Renombrar archivos masívamente"
