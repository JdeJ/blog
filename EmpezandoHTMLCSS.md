# Empezando con HTML y CSS
#### [Aprende Javascript con mentoringjs - Pretraining Step 3](http://mentoringjs.com "MentoringJS")

En mi camino para aprender Javascript necesitaba sentar unas bases sobre HML y CSS. Después de hacer el curso "HTML y CSS" de Codecademy, ésto es lo que he sacado en claro.

***

### HTML
Las siglas *HTML* significan HiperText Marked Language, es un lenguaje de programación que usamos para diseñar páginas web. El código llega a nuestro ordenador y el navegador que estemos usando se encarga de ejecutarlo.

Toda página web tiene una estructura fija:

    <DOCTYPE! html>
    <html>
      <head>
        <title>Título de la página web</title>
      </head>
      <body>
        <p>Contenido que aparecerá en el navegador</p>
      </body>
    </html>

Después de ver el esquema anterior nos damos cuenta de 2 cosas:

1 La importancia de la *indentación* en nuestro código, es algo que aparece en la segunda o tercera página de los libros de programación de cualquier lenguaje y deberíamos tenerle el mismo respeto que a las técnicas o patrones de programación.

2 Por otro lado vemos lo más importante en HTML y CSS, las *etiquetas*. Cada elemento que forme parte de nuestra web va encerrado en etiquetas que identifican que tipo de elemento tiene que crear/representar.

Éstas *etiquetas* van desde las que se usan para "dibujar" la distribución de nuestra página: \<div> o \<table>, hasta las del contenido propiamente dicho: \<p>, \<h1>, \<img> Respecto a las etiquetas debemos imaginarnoslas como pequeñas cajas, cada etiqueta ocupa su propio espacio y podemos configurarlo a nuestro antojo para que ocupen más o menos (a través de los bordes interiores y exteriores), se posicionen delante o detrás de otros elementos y ocupen un determinado espacio en nuestra página respecto al tamaño de la ventana que la contiene.

Por úlitmo, otra cosa que podemos hacer con las etiquetas de nuestra página es personalizándolas a través de parámetros propios de cada una de ellas, por ejemplo podemos asignarle a un párrafo el tipo de fuente, tamaño, color...

***

### CSS
La otra mitad de éste miniresumen se refiere a *CSS* (Cascading Stylesheets). Si en el punto anterior deciamos que usábamos el lenguaje HTML para definir la estructura y el contenido de nuestra web, a través de las CSS podemos darle el estilo que nosotros queremos.

Las etiquetas HTML nos permiten a través de parámetros personalizar nuestros elementos, pero se hace muy pesado tener que personalizar cada elemento que añadamos. Para facilitar la labor de personalización surgen las CSS, con ellas podemos definir de una manera única todos los elementos de un tipo que estén presentes en nuestra web. Para entenderlo un poco mejor dejo éste ejemplo:

    <!-- HTML -->
    <p style="color: white; font-family: helvetica; font-size: 22px;">Éste es nuestro párrafo original en código HTML</p>

    <!-- Personalizando con CSS -->
    <!-- CSS -->
    p {
      color: white;
      font-family: helvetica;
      font-size: 22px;
    }
    <!-- HTML -->
    <p>Éste es nuestro párrafo con CSS</p>

En el primer ejemplo vemos como definiriamos el color, el tipo y el tamaño de fuente del texto contenido en nuestro párrafo. Funciona bien pero si hacemos ésto con el clásico HTML estamos obligados a definir los parámetros en cada párrafo de la web.

En el segundo ejemplo vemos que el código HTML se simplifica (recordad que sólo usamos HTML para definir el esqueleto de la web), y las líneas contenidas entre p{} son las que definen las propiedades del texto contenido en todos los párrafos de la web. Con ésto nos ahorramos tener que escribir el color, tamaño y tipo de letra que el navegador debe mostrar para cada párrafo.

Pero, ¿y si necesitamos tener varios tipos de párrafos?, como podéis imaginaros no somos los primeros que pensamos en ello, todos los elementos que usamos en nuestra web tienen 2 parámetros muy importantes:

1 *class*: Éste parámetro lo usamos para especificar propiedades extra para ciertos elementos. Siguiendo nuestro ejemplo, podemos definir el color, la fuente y el tamaño de todos los párrafos, y ademas que los que sean de la clase cursiva (\<p class="cursiva">) tengan el texto en cursiva:

    <!-- HTML -->
    <p class="cursiva">Éste es nuestro párrafo en cursiva con CSS</p>

    <!-- CSS -->
    p.cursiva {
      font-style: italic;
    }

2 *id*: Al igual que el parámetro *class*, sirve para identificar un elemento aunque de manera única. Si asignamos un *id* a una etiqueta, en nuestra CSS podemos utilizarla a través de él y asignarle mas propiedades que queramos, pero no podemos tener dos etiquetas con el mismo *id*.

    <!-- HTML -->
    <p id="parrafo1"> Párrafo con id: 1</p>
    <p id="parrafo2"> Párrafo con id: 2</p>

    <!-- CSS -->
    parrafo1{
      font-style: italic;
    }
    parrafo2{
      font-style: normal;
    }

***

Hasta aquí mi pequeño resumen de mis inicios en la programación de páginas web.

Un saludo...
