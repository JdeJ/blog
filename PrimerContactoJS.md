# Primer Contacto con JavaScript
#### [Aprende javascript con MentoringJS](http://mentoringjs.com "MentoringJS")

En este, mi primer, artículo voy a hacer una lista de las que, a priori, son para mi las cosas que más me han llamado la atención de mi primer contacto con **JavaScript**.

***

### Un poco de Historia
Fue creado por [Brendan Eich]( https://es.wikipedia.org/wiki/Brendan_Eich "Brendan Eich") mientras trabajaba para **Netscape Communications Corporation**, originalmente se llamaba **Mocha**, luego cambió de nombre a **LiveScript** y finalmente se quedó con el nombre de **JavaScript** cuando el navegador **Netscape** añadió la compatibilidad con al tecnología **Java**, aunque ambos lenguajes tienen pocas cosas en común.

Para su desarrollo tomó funcionalidades de Java, Scheme, Self, Perl y Python, creando una mezcla de programación funcional y orientada a objetos.

***

### Sintaxis y peculiaridades
La sintaxis es la común a casi todos los lenguajes:

Código | Resultado
-- | --
// Tu comentario | Comentario en una sola línea
/* Tu comentario multilínea*/ | Comentario multilínea
var x;  | Declaración de una variable
x = 6; | Asignación de un valor a una variable
var obj = {}; | Declaración de un objeto vacío
; | Final de sentencia, no es obligatorio en JS


De todo esto las dos cosas que más me han llamado la atención son:
-	La declaración de las variables. hasta ahora estaba acostumbrado a pensar que uso iba a hacer de la variable para declararla del tipo correcto y no tener problemas en mi código, en JS todas las variables se declaran igual, incluso los objetos se definen de manera similar. Pero hay que tener cuidado ya que por ejemplo para JS **1 = 1.0**.
-	Si asignas un valor a una propiedad de un objeto que no esté declarada, ésta se crea automáticamente con el valor asignado. Si se accede a una propiedad que no está declarada (lectura), JS nos devuelve ***undefined***.

***

### Valores

En JS, las variables tienen que nombrarse siguiendo ésta nomenclatura: empezando por **[A-Z, a-z, $, _]** seguido de **[A-Z, a-z, $, _, 0-9]** . En ningún caso puede empezar por un número ni pertenecer a la lista de [palabras reservadas](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Palabras_Reservadas "Palabras Reservadas").

JS separa los posibles valores manejados en el código en dos grupos:

1 **Primitivos** : booleanos, números, strings, null y undefined.

2 **Objetos** : cualquier objeto que podamos definir, o que pertenezca al API de JS.

Para poder saber de que tipo es la variable que estamos tratando en cada momento, podemos hacer uso del operador ***typeof*** para primitivos e ***instanceof*** para objetos.

***

### Funciones

El tema de las funciones es un poco peculiar, por una parte al definir una función que va a recibir **X** parámetros, no necesitamos decir que tipo de dato es cada parámetro, sólo debemos poner el nombre de los parámetros. Y tampoco debemos hacer nada especial si la función va a devolver algo:

    function f(p1, p2) {
      console.log(p1, p2); //Ésto nos mostrará en pantalla el valor de p1 y p2
      return arguments; //Devuelve la variable arguments
    };

Pero lo que es más curioso es que hasta ahora estaba acostumbrado a que la consola me lanzase un error al llamar a una función pasándole menos o más parámetros de los que tiene definidos.

Pues bien, en JS existe una variable llamada ***arguments*** que almacena los valores que pasamos como parámetros a una función como si fuese un **Array**. Por esto JS siempre nos va a dejar llamar a una función sin enviarle necesariamente todos o ningún parámetro, funciona de la siguiente forma:

**Caso 1**: Llamar a una función definida sin parámetros, pasándole varios parámetros.

    function f() {return arguments};
    var argum = f('a1', 'a2', 'a3');
    args.length; -> 3
    args[0]; -> a1

En éste caso, al llamar a la funcion ***f()***, ésta nos devuelve la variable ***arguments*** y se almacena en la variable ***argum*** y podemos utilizarla como si fuese un **Array**.

**Caso 2**: Llamar a una función pasándole **más** parámetros de los que se espera.

    function f(p1, p2) {
      console.log(p1, p2);
      return arguments;
    };
    var argum = f('a1', 'a2', 'a3');

Aquí vamos a obtener varias cosas, por un lado la función ***f(p1, p2)*** nos mostrará en pantalla el valor de p1 y p2 ('a1', 'a2'), y por otro está devolviendo ***arguments*** y almacenandolo en ***argum***, por lo que tenemos acceso a todos los parámetros descritos en la llamada original:

    args.length; -> 3
    args[2]; -> a3

**Caso 3**: Llamar a una función pasándole **menos** parámetros de los que se espera.

    function f(p1, p2) {
      console.log(p1, p2);
      return arguments;
    };
    var argum = f('a1');

En ésta ocasión, por un lado la función ***f(p1, p2)*** nos mostrará en pantalla el valor de p1 y p2 ('a1', *undefined*), de ésta forma se cumple lo que deciamos al principio de éste apartado: JS no da ningún error en caso de diferente número de parámetros, simplemente declara los parámetros restantes y al no tener valor los define como *undefined*.

Aunque lo más llamativo de éste caso es que la función sigue devolviendo ***arguments*** pero sólo con los parámetros de la llamada:

    args.length; -> 1
    toArray(argum); -> ['a1']

**Caso 4**: Llamar a la una función que espera parámetros, pero sin pasarle ninguno.

    function f(p1, p2) {
      console.log(p1, p2);
      return arguments;
    };
    var argum = f();

Siguiendo el razonamiento la función nos mostrará en pantalla el valor de p1 y p2 (*undefined*, *undefined*), ya que no le hemos pasado ningún valor.

En el caso de ***arguments*** se comportará de la siguiente manera, definiendo un **Array** vacío:

    args.length; -> 0
    toArray(argum); -> []

***

### Ámbito de las variables

Otra cosa que me llama la atención de JS es referente a la vida de las variables, las variables en JS tienen vida a lo largo de la función en la que se encuentren, no del bloque en el que estén definidas.

    function f(){
      var x = 3;
      if (x<12){
        var y = x+1;
      }
      console.log(y);
    }

En el trozo de código anterior, la variable **y** almacena el valor **4** al entrar en el **if()**, hasta ahora en otros lenguajes si intentaba acceder a **y** fuera del bloque de c(ódigo obtenia un error. En JS puedo seguir utilizando la variable **y** mientras esté dentro de la funcion **f()**.

Todo ésto ocurre porque JS, hace una cosa que se llama ***hoisted***, que consiste en "mover" todas las declaraciones de variables al inicio de las respectivas funciones. Pero hay que tener cuidado porque mantiene en el lugar original las inicializaciones de las mismas.

Por último, en el tema de la vida de una variable, hay un caso especial que se llama ***closure***. Ocurre cuando devolvemos como retorno de una función otra función. De ésta manera se mantiene viva la variable que estaba definida dentro de ella:

    function incrementar(x){
      return function (){
        x++;
        return x;
      }
    }

    var inc = incrementar(1);
    inc(); -> 2
    inc(); -> 3
    inc(); -> 4

Al mantenerse viva la variable **X**, cada vez que que ejecutemos **inc()**, actualizará el último valor que tenia **X**.

Para poder limitar el ámbito de una variable a una función, hay que usar lo que se llama ***IIFE Pattern***, consiste en envolver la función entre paréntesis de ésta forma:

    (function f(){
      var x = 0;
      }());

***

### Objects and Constructors

En lo referente a objetos, JS distingue 2 modos de operar:

1 **Objetos planos**. Son objetos únicos que no pertenecen a ninguna clase, en los que definimos sus propiedades (variables y funciones):
    var persona = {
      nombre: 'Pepe';

      descripcion: function (){
        return this.nombre;
      }
    }
Pero éstos objetos no son inmutables, podemos hacer éstas operaciones:

Código | Operación
-- | --
persona.tlfno = '933233456'; | Añadimos la propiedad **tlfno** a **persona**
delete persona.tlfno; | Eliminamos la propiedad **tlfno**
'apellidos' in persona; | Comprobamos si persona tiene la propiedad **apellidos**

Otra cosa que podemos hacer con éstos objetos es extraer sus métodos para usarlos como funciones únicas, para ello tendremos que tener cuidado cuando dentro de la función hacemos uso de alguno de los parámetros propios del objeto (operador ***this***). Si ejecutamos la función fuera del objeto, el operador ***this*** se conbierte en ***undefined***, para cubrirnos en éste caso existe el método ***bind()*** disponible para todas las funciones, funciona de ésta manera:

    var funcion = persona.descripcion;
    funcion(); -> TypeError: Cannot read property 'nombre' of undefined
    var funcion = persona.descripcion.bind(pepe); -> sustituye el **this** por 'pepe'
    funcion(); -> 'pepe'

Otra cosa que hay que tener en cuenta es que si tenemos una función dentro de un método, el this del método es ***undefined*** dentro de la función, si queremos poder usar alguna propiedad a través del **this**, debemos 'copiarla' en otra variable.

2 **Constructores**. Para poder hacer uso de la característica más importante de los objetos, ***la Herencia***, necesitamos constructores, en JS son funciones normales y corrientes a las que se les llama con el operador ***new*** y su nombre empieza con mayúscula.

    function Persona(nombre, apellidos){
      this.nombre = nombre;
      this.apellidos = apellidos;
    }
    //Métodos
    Persona.prototype.descripcion = function (){
      return 'Nombre: ' + this.nombre + this.apellidos;
    }

    var p = new Persona('Pepe', 'Lopez');
    p.nombre; -> 'Pepe'
    p.descripcion(); -> 'Nombre: Pepe Lopez'
    p instanceof Persona; -> true

***

Hasta aquí mi primera visión de JS, aún me falta mucho que aprender y lo iré plasmando en más artículos.

Un saludo.
