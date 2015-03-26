---
id: 1400
title: Cómo añadir contenido por defecto a los artículos en WordPress

layout: post
guid: http://elbauldelprogramador.com/?p=1400
permalink: /como-anadir-contenido-por-defecto-a-los-articulos-en-wordpress/
categories:
  - How To
  - php
tags:
  - artículos wordpress
  - contenido por defecto
  - contenido por defecto en post wordpress
---
<img src="/images/2012/05/Screenshot-05302012-111511-AM1.png" alt="Wordpress" width="123" height="116" class="thumbnail alignleft size-full wp-image-761" />  
Si escribes en un blog, seguramente en cada artículo repites algunos textos, como añadir [shortcodes][1] que usas habitualmente, pedir a los lectores que se suscriban al [feed del blog][2], que te sigan en las redes sociales etcétera. En esos casos es útil que para cada nuevo artículo creado, se inserte un texto por defecto. 

Es bastante sencillo lograr esta funcionalidad, en el archivo *functions.php* de tu tema añade:

{% highlight php %}add_filter( 'default_content', 'my_default_content' );
function my_default_content( $content ) {
   $content = "AQUI TU CONTENIDO POR DEFECTO";
 return $content;
}
{% endhighlight %}

Así de simple, ahora cada vez que crees un nuevo artículo, tendrá un contenido por defecto asignado.

#### Fuente

*How to Add Default Content in Your WordPress Post Editor* **|** <a href="http://www.wpbeginner.com/wp-tutorials/how-to-add-default-content-in-your-wordpress-post-editor/" target="_blank">wpbeginner</a> 



 [1]: /tag/shortcodes/
 [2]: /rssfeed/