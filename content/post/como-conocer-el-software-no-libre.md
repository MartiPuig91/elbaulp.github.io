---
title: 'Cómo conocer el software “no libre” instalado en nuestro equipo'
layout: post.amp
permalink: /como-conocer-el-software-no-libre/
modified: 2016-09-09T09:00
categories:
  - aplicaciones
  - curiosidades
  - How To
  - linux
mainclass: "linux"
color: "#2196F3"
---

Este programa lo ví en [ProyectosBeta][1].

Seguro que en nuestro equipo tenemos montones de aplicaciones instaladas, de las cuales muchas serán **no libres**, con el programita **vrms** podemos conocerlos de forma sencilla.

Los pasos a seguir son los siguientes:

<!--more-->

Instalamos el programa:

```bash
sudo aptitude install vrms
```

Y lo ejecutamos con `vrms`

El resultado es el siguiente:

<figure>
    <a href="https://4.bp.blogspot.com/-wWUOaA33nCk/TdN2JjQ8OxI/AAAAAAAAAgM/nxfKbEuZCnE/s1600/vrms.png"><amp-img layout="responsive"  height="450" width="800" src="https://4.bp.blogspot.com/-wWUOaA33nCk/TdN2JjQ8OxI/AAAAAAAAAgM/nxfKbEuZCnE/s800/vrms.png"></amp-img></a>
</figure>

Para que nos salga la el dibujito de **Stallman** hay que seguir los siguientes pasos.

```bash
$ sudo aptitude install vrms cowsay
$ sudo mv rms.cow /usr/share/cowsay/cows/rms.cow
$ cowsay -f rms -W 60 `vrms`
```

<figure>
	<amp-img on="tap:lightbox1" role="button" tabindex="0" layout="responsive"  height="256" width="238" src="https://3.bp.blogspot.com/-Hur9i5TORyM/TdN5Q19CliI/AAAAAAAAAgU/rhmM1JOnJao/s400/stallman.png"></amp-img>
</figure>

Fuente: [Proyectosbeta][2]

 [1]: http://proyectosbeta.blogspot.com
 [2]: http://proyectosbeta.blogspot.com/2011/05/crear-la-cara-de-richard-stallmann-con.html
