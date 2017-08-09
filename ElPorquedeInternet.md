# El por qué de Internet
#### [Aprende Javascript con mentoringjs - Pretraining Step 3](http://mentoringjs.com "MentoringJS")

Con éste artículo no pretendo sentar cátedra ni mucho menos, solo espero que le pueda servir a alguien para hacerse una idea del funcionamiento de Internet. Voy a hacerlo a través de cuatro preguntas: ¿Qué es?¿Cómo funciona?¿Por qué funciona?¿Qué demonios significa DNS?

***

### ¿Qué és?
*Internet* como se puede ver en cualquier texto que lo defina, es una *red de redes*. Pero ¿qué significa?, significa que todos los ordenadores del mundo con conexión a Internet, están conectados entre sí en una gran red mundial.
Para entenderlo mejor podemos imaginarlo en el funcionamiento que cualquiera tenemos en nuestra casa, quien más quien menos tiene un Router (wifi o no), un ordenador, algún móvil, la televisión e incluso puede que alguien que me esté leyendo tenga la nevera también conectada.
Pues bién ahí tenemos una red, todos nuestros dispositivos están conectados entre sí a través del router, ya sea por wifi o conectados directamente por cable. Y a su vez están conectados con el resto del mundo también a través del mismo router.
Ahora hacemos nuestra red un poco más grande, pensando que nuestro router se conecta a nuestro proveedor de internet (al igual que el de nuestros vecinos) por lo que todos estamos conectados aunque para poder trabajar como si estuviésemos en un mismo espacio físico tenemos que hacer una serie de configuraciones (no es el objetivo de éste artículo) y conseguiremos compartir archivos, impresoras, trabajar en algún servidor común...
Dicho ésto, ahora que ya sabemos que estamos todos conectados, podemos pasar a la siguiente pregunta: ¿Cómo funciona?

***

### ¿Cómo funciona?
El funcionamiento es bastante sencillo, aunque para la mayoría de los mortales es pura magia. Cuando nosotros queremos poder hablar por teléfono con otras personas, contratamos una línea de teléfono, compramos un teléfono, y un instalador nos conecta todo. Ya sea inalambrico o no, nuestro teléfono lleva un cable que termina conectado en una cajita en la pared, ésta cajita es la que el instalador ha colocado comunicandola a través de un cable con la calle. A su vez, esa caja de la calle se conecta con una más grande a la que van a parar todas las de la calle, las del barrio, las de la ciudad... y así sucesivamente hasta llegar a nuestro proveedor de telefonía.
Pues bien, para conectarnos a internet el funcionamiento es el mismo, nuestro router se conecta al mundo a través de un cable que desaparece en la pared.
Si pensamos a gran escala, las ciudades están comunicadas entre sí también a través de cables, los países igualmente, y los contienentes de la misma manera sólo que en éste caso se hace a través de cables situados en el fondo del mar. Hora de pasar a la siguiente pregunta...

***

### ¿Por qué funciona?
En éste punto voy a aprovechar el símil de la línea telefónica, cuando nosotros descolgamos el teléfono estamos abriendo una línea de comunicación con el mundo, nuestro siguiente paso es decidir con quién queremos hablar, ésto lo hacemos marcando su número de teléfono y acto seguido oímos los famosos tonos de llamada y si hay alguien al otro lado del teléfono que nos conteste al levantar el aurícular aceptará nuestra llamada y comenzará la conversación.
Pues bien, en Internet es practicamente lo mismo, cuando abrimos nuestro explorador preferido (Chrome, IE, Firefox, Safari) estamos "descolgando" nuestro teléfono, el siguiente paso es "marcar el número de teléfono" y lo haremos escribiendo la dirección de la página web para poder visitarla, nuestro ordenador/router/servidor de internet hace su "magia" para que nuestra petición llegue donde debe. Llegó el momento de la última y más interesante parte de éste artículo...

***

### ¿Qué demonios significa DNS?
Aquí viene "la madre del cordero", una vez entendida la parte física (cables, routers...) llega la parte lógica del funcionamiento de Internet.
Cuando un poco más arriba hablábamos sobre el funcionamiento de una llamada telefónica, decíamos que cuando queremos comunicarnos con alguien lo hacemos a través de su número de teléfono, ésto nos obliga a tener una agenda en la que asociamos nombres a números de teléfonos y que consultamos cada vez que queremos llamar a alguien buscando su nombre.
Pues ya sabes como funciona el DNS (Domain Name Server), cada ordenador del mundo tiene una dirección IP (número de teléfono) con el formato siguiente: 123.456.789.012. Memorizar éstos números sería una proeza, para ello necesitamos una "agenda", pero claro, ésta seria de un tamaño inimaginable debido a la cantidad de ordenadores que existen.
Ésta "agenda" nos la proporciona nuestro proveedor de internet y funciona de la siguiente manera: al escribir la dirección web en el explorador, por ejemplo www.miweb.es, nuestro ordenador comprueba si la conoce, si es el caso nos redirige a la dirección IP correspondiente. Si no la conoce, pregunta a el servidor DNS de nuestro proveedor de Internet, que si la conoce nos redirige y sino deriva la consulta al servidor DNS raiz "." que conoce las direcciones de los servidores DNS de cada extensión (.es, .com, .cat, ...) por lo que siguiendo el ejemplo nos derivará al servidor DNS ".es".
Al llegar a éste servidor se vuelve a preguntar si conoce la dirección IP correspondiente a www.miweb.es, y éste nos dirige al servidor DNS "miweb.es" y se realiza el paso final, y éste nos devuelve al IP que corresponde a nuestra dirección web.
Ahora que nuestro navegador sabe la dirección IP, realiza la llamada y el servidor web nos devuelve la página que es lo que finalmente vemos en el ordenador.

***

Espero haberme explicado bien y que hayais entendido el funcionamiento de Internet.

Un saludo...
