---
layout: post.amp
title: Cómo Cambiar El Directorio De Portage a Otro Directorio en Gentoo
description: Cómo cambiar el directorio de portage y directorio temporal a otro directorio
tags: [gentoo, portage]
image: como-instalar-actualizar-elminar-paquetes-gentoo.png
introduction: Cómo cambiar el directorio de portage y directorio temporal a otro directorio
date: 2016-08-17T10:30:50+02:00
mainclass: "linux"
color: "#2196F3"
---

Hace poco tuve problemas con [portage](/como-instalar-actualizar-elminar-paquetes-gentoo/ "Cómo Instalar/actualizar/eliminar Paquetes en Gentoo") y su directorio de trabajo temporal en `/var/tmp/portage` en [Gentoo](/tags/#gentoo) porque me quedé sin las 10GB mínimas que necesita:

```bash
There is NOT at least 10 GiB disk space at "/var/tmp/portage
```

Así que la primera solución que se me ocurrió fue hacer que `portage` trabaje en otro directorio, concretamente en otro disco duro auxiliar en el que dispongo de más espacio. Veamos cómo conseguirlo:

{% include toc.html %}

# Cambiar el fichero /etc/portage/make.conf

<!--ad-->

Para ello necesitamos decirle a `portage` que queremos cambiar el directorio por defecto, para ello editamos el fichero `/etc/portage/make.conf` y añadimos las variables `PORTDIR, DISTDIR` y `PKGDIR` apuntando al directorio deseado, en mi caso `/home/hkr/ssd2/portage`:

```bash
PORTDIR="/home/hkr/ssd2/portage"
DISTDIR="${PORTDIR}/distfiles"
PKGDIR="${PORTDIR}/packages"
```

# Sincronizar el árbol de portage

El siguiente paso es sincronizar `portage` para que se de cuenta del cambio, para ello:

```bash
emerge --sync
```

Tras esto, `portage` ya conocerá la nueva localización de directorios, pero resta una cosa más por hacer.

# Crear enlace simbólico para make.profile

Ahora mismo `make.conf` es un enlace a `/usr/portage/profiles/default/linux/amd64/13.0/desktop/`, el directorio antiguo, debemos enlazarlo con el directorio nuevo:

```bash
ln -s /home/hkr/ssd2/portage/profiles/default/linux/amd64/13.0/desktop /etc/portage/make.profile
```

Tras esto, tendremos `portage` en un nuevo directorio.

# Cambiar solo el directorio temporal /var/tmp/portage

Mi problema orignal era no tener espacio en `/var/tmp/portage`, resulta que este directorio también se puede cambiar, sin necesidad de mover de sitio lo ficheros de `portage`, para ello basta con añadir al `make.conf` la siguiente variable:

```bash
PORTAGE_TMPDIR="/home/hkr/ssd2/"
```

Sincronizamos y listo.

# References

- [`/var/tmp/portage: not enough space`](https://forums.gentoo.org/viewtopic-t-774539.html "/var/tmp/portage: not enough space")
- [`moving portage folders`](https://forums.gentoo.org/viewtopic.php?t=120770 "moving portage folders [SOLVED]")
