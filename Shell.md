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
\boot | En este directorio se encuentra el kernel de Linux y los archivos de arranque.
\etc | Aqui están los archivos de configuración del sistema: usuarios, unidades montadas, hosts names...
\bin | Este directorio contiene la mayoria de los programas de nuestro sistema.
\sbin | Son los programas que solo puede utilizar el administrador.
\usr | Archivos que necesitan otros programas para su funcionamiento.
\usr\local | Aqui se guardan las aplicaciones que no tienen que ver con la distribución oficial.
\var | Son archivos que el sistema va modificando mientras funciona.
\lib | Librerias del sistema.
\home | Es el directorio donde se guardan los archivos del usuario.
\root | El directorio personal del administrador.
\tmp | Donde los programas guardan sus temporales.
\dev | Es el directorio donde se encuentran las unidades montandas.
\media. \mnt | Aqui aparecen las unidades que el sistema monta durante su funcionamiento como CDROM, USB...

***

### Manipulación de archivos

En este apartado vamos a ver los 4 comandos principales para manejar los archivos de nuestro sistema, pero antes hay que conocer las wildcards. 

**WILDCARDS**: Son comodines que usaremos a la hora de ejecutar los comandos para añadirles funcionalidad extra, se pueden usar con cualquier comando que acepte como argumentos, nombres de archivo.

Wildcard | Significado
-- | --
/* | Sustituye cualquier caracter.
/? | Sustituye un solo caracter.
[characters]  | Los que coinciden con un grupo de caracteres.
[!characters]  | Los que no coinciden con un grupo de caracteres.

**CP**: Sirve para copiar archivos y directorios, aquí van un par de ejemplos:

Código | Resultado
-- | --
cp ar1 ar2 | Copia el contenido de ar1 en ar2, si ar2 no existe lo crea, si existe lo sobreescribe.
cp ar1 dir1 | Copia ar1 dentro del directorio dir1.
cp -R dir1 dir2  | Copia dir1 dentro de la carpeta dir2, si no existe lo crea.

**MV**: Mueve o renombra archivos y directorios.

Código | Resultado
-- | --
mv ar1 ar2 | Si ar2 no existe, renombra ar1. Si existe, copia el contenido de ar1 en ar2.
mv ar1 ar2 ar3 dir1 | Mueve ar1, ar2 y ar3 a dir1. Si dir1 no existe da error.
mv dir1 dir2  | Si dir2 no existe, renombra dir1. Sino mueve dir1 a dir2.

**RM**: Borra archivos y directorios. Hay que tener en cuenta que no existe un comando deshacer, una vez eliminemos algo permanecera así permanentemente.

Código | Resultado
-- | --
rm ar1 | Elimina el archivo ar1.
rm ar1 ar2 | Elimina los archivos ar1 y ar2.
rm -r dir1 dir2  | Borra el contenido de los directorios dir1 y dir2.
    
**MKDIR**: Es el comando más simple, sirve para crear directorios.

    mkdir nombre_del_directorio
    
***

### Trabajando con comandos

Antes de seguir con más comandos, conviene que sepamos los tipos que hay y como diferenciarlos para poder ejecutarlos como es debido. Hay 4 tipos de comandos:

1 Ejecutables: Son los programas compilados.

2 Bash: Comandos internos de la Shell.

3 Funciones Shell: Son pequeños scripts propios del entorno.

4 Alias: Comandos personalizados creados a partir de otros comandos.

**TYPE**: Es una herramienta de la Shell que nos dice el tipo de comando que queremos ejecutar:

    type comando

**WHICH**: A veces necesitamos saber exactamente que comando estamos ejecutando, al ejecutarlo nos muestra su ruta.

    which comando

**HELP**: Es una utilidad para las funciones de la Shell, nos muestra por pantalla la descripcion y las opciones del comando.

    help comando

**--HELP**: Al igual que ocurre con las funciones de la Shell, algunos ejecutables permiten el uso de este comando para mostrar una pequeña ayuda sobre el comando y sus opciones.

    comando --help
    
**MAN**: La mayoria de los ejecutables contienen una especie de manual que muestra por pantalla toda la informacin que los desarroladores han redactado sobre el programa.

    man programa
    
***

### Modificando el tipo de entrada y salida

Hasta ahora hemos ido ejecutando comandos introduciendolos por teclado y esperando ver el resultado mostrado en la pantalla. La shell nos permite modificar esta entrada y salida estandar para controlar el flujo de los datos.

**Standard Output**: La salida estandar cuando ejecutamos un comando es la pantalla, pero a veces nos puede interesar que el resultado de un comando sirva como entrada de datos para otro, esto se hace con el caracter ">".

Código | Resultado
-- | --
ls > lista_archivos.txt | Ejecuta el comando ls y guarda el resultado en un archivo de texto en lugar de mostrarlo en pantalla.
ls >> lista_archivos.txt | Añade el resultado del comando al final de lista_archivos.txt, si no existe lo crea.

**Standard Input**: Al igual que en el caso anterior, podemos cambiar la forma de entrada de datos estandar (el teclado) por la que nos interese.

Código | Resultado
-- | --
sort < lista_archivos.txt | Ejecuta el comando sort sobre lista_archivos.txt y lo muestra en pantalla.
sort < lista_archivos.txt > lista_archivos_ordenada.txt | Igual que el anterior pero en lugar de mostrarlo, almacenandola en otro archivo.

**Pipelines**: En otras ocasiones la entrada de datos en un comando puede ser sustituida directamente por la salida de datos de otro.

Código | Resultado
-- | --
ls -l \| less | Ejecutamos ls y la lista obtenida nos sirve de entrada de datos para el editor less, que nos dejará navegar por el resultado.

**Filters**: Los filtros se usan para tratar la informacin obtenida a traves de un pipeline. Aquí va una lista de los más utilizados:

Filtro | Significado
-- | --
sort | Ordena el input lo manda a la salida estandar.
uniq | Elimina lineas duplicadas en un archivo ordenado recibido por la entrada estandar.
grep | Devuelve cada linea que coincida con la plantilla especificada.
fmt | Lee el texto de la entrada estandar y lo muestra formateado en la salida estandar.
    
***

### Expansion

Expansion es como la Shell llama a las operaciones que realiza sobre el texto que le pedimos ejecutar.

**Pathname Expansion**: Es lo que la Shell hace cuando introducimos una wildcard, ejemplos:

Código | Resultado
-- | --
echo D* | Muestra en pantalla los archivos o directorios que empiecen por D.
echo *s | Muestra en pantalla los archivos o directorios que acaben por s.

**Tilde Expansion**: Cuando introducimos ~ delante de un nombre, el sistema lo traduce como el directorio home del mismo, si no introducimos nada, el sistema interpreta que es el del usuario actual.

Código | Resultado
-- | --
echo ~ | Muestra en pantalla la ruta del directorio home del usuario actual.
echo ~pepe > | Muestra en pantalla la ruta del directorio home del usuario pepe.

**Arithmetic Expansion**: Si utilizamos la expansion $, le estamos pidiendo al sistema que nos calcule el resultado de la operación que le escribimos dentro de los paréntesis.

Código | Resultado
-- | --
echo $((5\**2)) | Muestra en pantalla el resultado de la expresion.
echo $(((5\**2) * 3)) | Muestra en pantalla los archivos o directorios que acaben por s.

**Brace Expansion**: 
**Parameter Expansion**: 
**Command Substitution**: 
**Quoting**:
**Double Quotes**: 
**Single Quotes**: 
**Escaping Characters**: 
**Backslash Tricks**: 





    
    
    
    
    
    
    
  
***

Con esto podemos manejarnos en la Shell de nuestro sistema sin entrar en pánico.

Un saludo.
