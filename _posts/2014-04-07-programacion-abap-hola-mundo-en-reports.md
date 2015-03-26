---
id: 2329
title: 'Programación ABAP: Hola Mundo en Reports'

layout: post
guid: http://elbauldelprogramador.com/?p=2329
permalink: /programacion-abap-hola-mundo-en-reports/
categories:
  - ABAP
tags:
  - curso ABAP
  - hola mundo abap
  - programación ABAP
---
*Éste artículo es una colaboración de <a href="http://www.blogdesap.com/" title="Blog de SAP" target="_blank">Óscar Arranz</a>*

Para iniciarnos en la programación ABAP nada mejor que el clásico “Hola mundo”. Con este tutorial podremos crear nuestro primer programa ABAP y, a su vez, ir viendo paso a paso algunos fundamentos básicos de programación de este lenguaje.

<!--more-->

### CREAR NUESTRO PROGRAMA ABAP

Después de acceder a nuestro entorno SAP ECC vamos a la transacción **SE38** para escribir el nombre de nuestro programa. Todo programa en ABAP tendrá que empezar siempre por la letra Z o Y ya que el resto de letras están reservadas para los programas propietarios SAP.

Al pulsar el botón **Crear** lo básico que SAP no solicita es:

  * **Título**: la descripción de nuestro programa que aparecerá cuando ejecutemos nuestro programa.
  * **Tipo**: nuestro programa es ejecutable de por sí. Así que lo categorizamos como programa ejecutable.
  * **Status**: este programa es sólo una prueba así que le daremos el status de programa de test.
  * **Aplicación**: describe, dentro de los módulos disponibles de SAP, en qué categoría se puede introducir. Por ejemplo, puede estar asociado al módulo de compras, al de ventas, etc. Al ser un programa de test no lo asignaremos a ninguna aplicación.

<img src="/images/2014/04/hola-mundo-crear.png" alt="Crear Hola Mundo ABAP" width="689" height="646" class="aligncenter size-full wp-image-2331" />

Al pulsar el botón **Grabar** SAP nos devuelve a otra pantalla, donde nos pide que asignemos la capa de transporte. Básicamente, nos está diciendo que este programa podrá ser transportado desde nuestro entorno de desarrollo a un entorno productivo.

<img src="/images/2014/04/hola-mundo-objeto.png" alt="hola-mundo-objeto" width="468" height="312" class="aligncenter size-full wp-image-2332" />

Sin embargo, como a nosotros esto ahora mismo no nos interesa pulsaremos el botón **Objeto Local**. Esto significa que no lo vamos a poder transportar a productivo nunca.

### PRIMERAS SENTENCIAS ABAP

Una vez creado nuestro programa, SAP nos genera automáticamente una serie de líneas de comentario y una línea de report.

<img src="/images/2014/04/hola-mundo-abap.png" alt="hola-mundo-abap" width="688" height="331" class="aligncenter size-full wp-image-2330" />

En ABAP todas las sentencias que empiezan por **asterisco** son comentarios no ejecutables. Y en estas líneas que SAP nos ha creado automáticamente se espera que escribamos una descripción general del propósito del programa.

En segundo lugar nos encontramos con la sentencia **REPORT** creada también de forma automática. Ésta es siempre la primera sentencia que se ha de escribir y sirve para indicar que el resto de sentencias que siguen corresponden a un programa de tipo report.

En general la estructura de toda sentencia en ABAP sigue el mismo esquema, empieza con la palabra clave y acaba en un punto.

### DECLARACIÓN DE UNA VARIABLE

Para declarar una variable simple utilizaremos la palabra clave **DATA** seguida del nombre de nuestra variable, su longitud, el tipo de variable y acabando con un punto.

{% highlight abap %}DATA <nombre_variable> type <tipo>
{% endhighlight %}

En este caso nuestra variable contendrá la cadena de caracteres de nuestro ‘Hola mundo’ y por lo tanto será de tipo carácter (c).

{% highlight abap %}DATA g_texto(10) type c
{% endhighlight %}

### Eventos

En todo report ABAP hay dos eventos muy importantes, el evento **START-OF-SELECTION** y el evento **END-OF-SELECTION**. Cuando introducimos una palabra clave de evento, todas las sentencias a continuación estarán incluidas dentro de ese evento.

#### Evento START-OF-SELECTION

Todas las sentencias que siguen a este evento hacen referencia a operaciones a realizar antes de que el programa presente resultados en pantalla. Aquí incluimos la asignación de nuestro texto ‘hola mundo’ (entre comillas simples) a nuestra variable mediante la palabra clave **MOVE**.

{% highlight abap %}MOVE ‘Hola mundo’ TO g_texto.
{% endhighlight %}

#### Evento END-OF-SELECTION

Cualquier sentencia que siga a este evento provoca la presentación de resultados en pantalla. Aquí pues escribimos la sentencia **WRITE** que muestra nuestro texto en pantalla.

{% highlight abap %}WRITE g_texto.
{% endhighlight %}

<img src="/images/2014/04/hola-mundo-abap.png" alt="hola-mundo-abap" width="688" height="331" class="aligncenter size-full wp-image-2330" />

### VERIFICACIÓN Y ACTIVACIÓN

Antes de poder ejecutar nuestro report hay que hacer dos pasos muy importantes:

  * Verificar la sintaxis a través del menú **Programa / Verificar / Sintaxis** y comprobar que lo escrito es sintácticamente correcto de acuerdo a las normas ABAP.
  * Activar el programa a través del menú **Programa / Activar**. Aunque ABAP no es un lenguaje compilado, aun así hay que generarlo para poder ejecutarlo. Mientras no lo hagamos, y si intentamos ejecutarlo, SAP sólo podría lanzar la última versión activa que tuviese en memoria.

### EJECUCIÓN DEL PROGRAMA

A través del menú **Programa / Ejecutar / Proceso directo** o, simplemente, pulsando **F8** obtendremos el resultado de nuestro programa en pantalla.

<img src="/images/2014/04/hola-mundo-salida.png" alt="hola-mundo-salida" width="633" height="205" class="aligncenter size-full wp-image-2333" />

### TRANSACCIONES

Si queremos avanzar un poco más en nuestro “Hola mundo” podemos incluir nuestro programa en una transacción. Ya que los usuarios nunca podrán acceder al ABAP Workbench, no podrán ejecutar tampoco nuestros programas a través de la transacción SE38. Así que tenemos que crear siempre transacciones específicas para usuarios.

  * Accedemos a la transacción SE93
  * Como nombre de transacción escribiremos Z_HOLA. De nuevo, recordar que como clientes sólo podemos utilizar la Z o la Y como letra de inicio de nuestros objetos ABAP.
  * Pulsamos crear, damos una descripción e indicamos que nuestra transacción es transacción de report.
  * Indicamos el nombre de nuestro programa y grabamos como objeto local.  
    <img src="/images/2014/04/hola-mundo-transaccion.png" alt="hola-mundo-transaccion" width="469" height="219" class="aligncenter size-full wp-image-2334" /></p> 

Ya está. Ahora utilizando la transacción Z\_HOLA se ejecutará el resultado del programa Z\_HOLA_MUNDO.
