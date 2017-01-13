---
title: Editar y crear archivos cifrados con GPG en Vim
layout: post.amp
permalink: /editar-y-crear-archivos-cifrados-con-gpg-en-vim/
categories:
  - linux
  - seguridad
tags:
  - cifrar archivos gpg
  - descifrar archivos gpg
  - editor archivos gpg
  - gpg vim plugin
  - vim plugin
  - gpg
image: 2013/04/GnuPG-Logo.png
description: "Hoy quiero hablaros de un plugin bastante útil que encontré para el potente editor de textos Vim, que permite crear y modificar archivos de texto bajo gpg (GNU Privacy Guard)."
modified: 2016-08-10T09:35
redirect_from: /opensource/seguridad/editar-y-crear-archivos-cifrados-con-gpg-en-vim/
mainclass: "linux"
color: "#2196F3"
---

<figure>
    <amp-img on="tap:lightbox1" role="button" tabindex="0" layout="responsive" src="/assets/img/2013/04/GnuPG-Logo.png" alt="Editar y crear archivos cifrados con GPG en Vim" title="Editar y crear archivos cifrados con GPG en Vim" width="400px" height="175px"></amp-img>
</figure>

Hoy quiero hablaros de un plugin bastante útil que encontré para el potente editor de textos Vim, que permite crear y modificar archivos de texto bajo **[gpg](/tags/#gpg)** (*GNU Privacy Guard*).



# ¿Qué es **gpg**?

Me permito extraer el la definición de genbeta::Dev. Para una explicación más profunda del funcionamiento de **gpg**, puedes dirigirte al artículo en GenBeta::Dev que cito en las referencias.

> *Antes de empezar con lo interesante tenemos que saber que es **gpg** (GNU Privacy Guard), que es un derivado libre de **PGP** y su utilidad es la de cifrar y firmar digitalmente, siendo además multiplataforma (<a href="http://www.gnupg.org/download/index.en.html" target="_blank">podéis descargarlo desde la página oficial</a>) aunque viene incorporado en algunos sistemas Linux, en Windows se encuentra solo con gestor gráfico).*

<!--more-->

# Instalar el plugin para Vim

Descarga el plugin <a href="http://www.vim.org/scripts/download_script.php?src_id=18070" target="_blank">gnupg.vim</a>. Una vez descargado, pégalo en el directorio *$HOME/.vim/plugin/*. El último paso es añadir la siguiente línea al archivo **.bashrc**:

```bash
export GPG_TTY=`tty`
```

Es recomendable establecer algunas variables en el fichero de configuracón de Vim (*.vimrc*). El mio está así:

```bash
$ cat ~/.vimrc
:let g:GPGDefaultRecipients=["<tu-correo><id_publica> -u <id_privada> --output <nombre_archivo.signed.gpg> --sign <archivo_original>
```

# Referencias

- *Plugin para Vim* »» <a href="http://www.vim.org/scripts/script.php?script_id=3645" target="_blank">Visitar sitio</a>
- *Introducción a <strong>gpg</strong>* »» <a href="http://www.genbetadev.com/seguridad-informatica/manual-de-gpg-cifra-y-envia-datos-de-forma-segura" target="_blank">genbeta::dev</a>
