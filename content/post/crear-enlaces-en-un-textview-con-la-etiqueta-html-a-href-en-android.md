---
title: 'Crear enlaces en un TextView con la etiqueta HTML'
layout: post.amp
permalink: /crear-enlaces-en-un-textview-con-la-etiqueta-html-a-href-en-android/
categories:
  - android
tags: [a href android xml, crear enlaces cadenas de texto android, etiqueta a href android, etiqueta a href string.xml, etiqueta a href TextView android]
description: 'Para una aplicación que estoy haciendo, me hacía falta ser capaz de mostrar un enlace al usuario de forma similar al que se crean en las páginas webs con la etiqueta &lt;a href=””&gt;&lt;/a&gt;.'
modified: 2016-08-05T17:00
image: 2013/05/setMovementMethod-example.png
mainclass: "android"
color: "#689F38"
---

Para una aplicación que estoy haciendo, me hacía falta ser capaz de mostrar un enlace al usuario de forma similar al que se crean en las páginas webs con la etiqueta _&lt;a href=””&gt;&lt;/a&gt;_.

<!--more-->

La cadena de texto con el enlace en cuestión reside en el archivo de recursos **[string.xml](/programacion-android-recursos-strings/)**. En un principio pensé que me bastaría usar la propiedad `android:autoLink="web"` en el [layout.xml](/programacion-android-recursos-layout/) de la siguiente forma:

### **_layout_**:

```xml
<TextView
    <!-- .... -->
    android:autoLink="web"
    <!-- .... --> />
```

### **_string_**:

```xml
<string name="aboutAuthor">Developed by <a href="http://elbauldelprogramador.com">Alejandro Alcalde.</a></string>
```

Pero la propiedad `autoLink="web"`, funciona únicamente cuando el texto al que hace referencia contiene explícitamente la dirección, es decir, con esta cadena de texto sí funcionaría:

```xml
<string name="aboutAuthor">Developed by http://elbauldelprogramador.com</string>
```

Para conseguir hacer funcionar el primer ejemplo hay que hacer uso del método `setMovementMethod()` de la clase `TextView`:

```xml
final TextView author = (TextView) view.findViewById(R.id.tv_about_athor);
author.setMovementMethod(LinkMovementMethod.getInstance());
```

Con el código anterior se consigue el comportamiento deseado:

<figure>
    <amp-img on="tap:lightbox1" role="button" tabindex="0" layout="responsive" src="/assets/img/2013/05/setMovementMethod-example.png" alt="enlaces en un textview android" width="480" height="800"></amp-img>
</figure>

Los dos primeros enlaces están creados con el método `setMovementMethod()`, los otros dos con `android:autoLink="web"`.
