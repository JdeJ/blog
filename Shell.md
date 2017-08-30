# Funcionamiento Basico de la Shell
#### [Aprende Javascript con mentoringjs - Pretraining Step 3](http://mentoringjs.com "MentoringJS")

Para los que ya tenemos una edad la Shell o consola no nos es desconocida pero quizás a algún joven que esté leyendo ésto, le suene a chino.

La Shell no es más que una interfaz de tipo texto para comunicarnos con nuestro ordenador. Le pediremos que haga operaciones a través de comandos y éste nos mostrará por pantalla el resultado de las mismas.

***

### Como movernos entre los arhivos de nuestro ordenador

La forma que tendremos que navegar entre nuestros archivos a través de la Shell será un poco más complicada que a través de un entorno gráfico con nuestro ratón. Se hace a través de éstos 3 comandos básicos:

**PWD**: El comando *pwd* nos muestra en pantalla el directorio de trabajo en el que nos encontramos.

**CD**: El comando *cd* seguido del directorio al que nos queremos desplazar, es la manera de cambiar nuestro directorio de trabajo. Se puede hacer escribiendo la ruta absoluta del nuevo directorio, o través de la relativa y desplazarnos desde el actual directorio de trabajo.

**LS**: El comando *ls* nos muestra en pantalla el contenido, ya sean archivos o directorios, del directorio de trabajo actual, aunque si ejecutamos *ls ruta_de_directorio* lo que nos muestra es el listado de archivos de ese directorio en particular.

***

### Comandos básicos para usar nuestros archivos

Antes de comenzar a ejecutar comandos debemos conocer la estructura de los mismos:

  comando -opciones argumentos
  
donde *comando* es el comando que queremos ejecutar, *-opciones* son una serie de caracteres que dependiendo del comando le añaden funcionalidades extra que nos permiten realizar acciones ms especificas que el comando por defecto, y por último *argumentos* serán parámetros que necesita el comando para su ejecución.

Dicho ésto aquí van 3 comandos que debemos conocer para usar nuestros archivos:

**LS**: Ya hemos visto para que sirve y a continuación os muestro unos ejemplos de uso:

Código | Resultado
-- | --
ls | Muestra el contenido del directorio de trabajo.
ls -l | Muestra el contenido con información ampliada del directorio de trabajo.
ls -a  | Muestra el contenido del directorio actual inluyendo los archivos ocultos.
ls /etc | Muestra el contenido del directorio etc.
ls -l /etc /bin | Muestra el contenido con información apliada de los directorios etc y bin.

**LESS**: El comando *less* nos permite ver el contenido de un archivo en forma de texto en nuestra pantalla.

    less nombre_del_archivo

**FILE**: El comando *file* nos sirve para determinar el tipo de archivo que estamos manejando y así saber como debemos abrirlo correctamente para conocer su contenido.

    file nombre_del_archivo
***

### Directorios más importantes de nuestro ordenador

A continuación os muestro una tabla con los principales directorios de nuestro ordenador explicando su descripción:

Directorio | Descripción
-- | --
\ | Es la raíz, a partir de aquí cuelgan el resto de directorios y archivos de nuestro sistema.
\boot | .
\etc | .
\bin | .
\sbin | .
\usr | .
\usr\local | .
\var | .
\lib | .
\home | .
\root | .
\tmp | .
\dev | .
\proc | .
\media. \mnt | .






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
