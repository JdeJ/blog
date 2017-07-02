# Resumiendo Git
#### [Aprende javascript con MentoringJS](http://mentoringjs.com "MentoringJS")

En éste breve artículo intentaré explicar qué es la tecnología *Git* y como utilizarla para ayudarnos con nuestros proyectos.

***

### ¿Qué es Git?
*Git* es un *VCS* (Version Control Software), es una tecnología que nos ayuda a llevar un "diario" del desarrollo de nuestro proyecto, e incluso permite a otras personas colaborar añadiendo ideas o corrigiendo defectos pero siempre en paralelo, llegado el momento nosotros podemos decidir si añadir esas sugerencias o seguir con nuestra idea.

***

### Características
*Git* hace ***"fotografías"*** de nuestros proyectos cada vez que confirmamos un cambio o guardamos el estado, guardando referencias a ésos estados. La peculiaridad está en que, en lugar de hacer una copia de los datos, analiza que archivos no han sufrido cambios, de ésta manera no guarda de nuevo ésos archivos, sino que almacena una referencia.

Otra característica que hace *Git* más interesante que otros *VCS*, es que prácticamente la totalidad del trabajo se hace en local, con lo que si tienes que navegar por el historial de versiones, o rescatar una version antigua, lo puedes hacer de manera instantánea y no dependes de estar conectado a Internet o a una VPN. Puedes confirmar tus cambios y cuando tengas conexión se actualizará la base de datos, pudiendo trabajar con total libertad.

Por último una característica que no nos damos cuenta de que tiene hasta que estamos en problemas es la *Integridad*. *Git* verifica todo el contenido que almacenamos mediante **checksum** (suma de comprobación), que mediante un mecanismo que se llama *has SHA-1* genera un número que identifica cada archivo de manera única. *Git* controla los archivos y conoce cuándo un archivo ha sido modificado, ningún archivo puede ser modificado sin que *Git* lo sepa.

***

### Git vs GitHub
En éste punto hay que dejar claro qué es cada cosa para no confundirlas, a menudo oimos referencias a los dos como si fuese lo mismo pero no es así. *Git* es, como hemos dicho antes, la tecnología de control de versiones que nos permite tener un diario de cambios. Y GitHub es un espacio online donde podemos guardar nuestros repositorios *Git* para poder distribuirlos o simplemente como copia de seguridad.

Digamos que *GitHub* es una especie de *DropBox*.

***

### Funcionamiento
El funcionamiento de *Git* es  muy sencillo pero tenemos que entenderlo bien desde el principio para poder sacarle todo el jugo.

Los archivos pueden estar en 3 estados:

1 **Confirmado (committed)** : Los datos están guardados en nuestra base de datos local.

2 **Modificado (modified)** : Ésto significa que hemos modificado un archivo pero que aún lo hemos confirmado en nuestra base de datos local.

3 **Preparado (staged)** : Con ésto hemos marcado el archivo para que en nuestra siguiente *confirmación* se guarde en nuestra base de datos local.

Al igual que los archivos se pueden encontrar en 3 estados, *Git* tiene 3 áreas principales:

1 **Directorio de Git (Git Directory)** : Es el área más importante, ya que almacena los metadatos y la base de datos de nuestro proyecto, es lo que nos descargamos cuando clonamos un repositorio.

2 **Directorio de Trabajo (Working Directory)** : Es una copia de una versión del proyecto, extraemos los archivos que pertenecen a ésta versión a nuestro disco para poder trabajar con ellos.

3 **Área de Preparación (Staging Area)** : Es un archivo en el que se va almacenando información de lo que modificaremos en nuestra próxima confirmación.

Resumiendo, nuestro método de trabajo será el siguiente:

1 Haremos las modificaciones necesarias de nuestros archivos contenidos en nuestro **Directorio de Trabajo**.

2 Añadiremos a nuestro **Área de Preparación** los archivos que queremos que queden guardados.

3 Confirmamos nuestros cambios, con lo que *Git* guarda la ***fotografía*** de los archivos tal y como los añadimos al **Área de Preparación**, no confundir al estado actual de dichos archivos.

***

### Operaciones / Comandos básicos

Una vez instalado en nuestro ordenador, las operaciones con *Git* las realizaremos a través de unos comandos en la consola del sistema. Aunque existen muchos, debemos conocer al menos los siguientes:

Comando | Resultado
-- | --
git help <comando> | Obtenemos la ayuda acerca del comando.
git init | Indicamos a *git* que comienze el seguimiento del directorio actual
git add <archivo> | Informamos a *git* de que debe seguir dicho archivo
git commit | Confirmamos los cambios que hemos realizado
git clone <proyecto> | Clonamos un proyecto a nuestro disco, descargando todas las versiones de todos los archivos que lo componen.
git status | Nos permite conocer el estado de los archivos en nuestro **Working Directory**
git reset <archivo> | Le decimos a *Git* que deje de seguir el archivo

***

### Simulación de flujo de trabajo

Por último dentro de éste apartado voy a simular cómo trabajaremos con un repositorio *Git*.

Lo primero que tenemos que hacer es clonar el repositorio que queremos, de ésta manera:

    $ git clone git://github.com/app/app.git myApp

Lo que hemos hecho es clonar el repositorio *app.git* de Internet, en una carpeta llamada *myApp* en nuestro disco duro y diciendole a *Git* que empieze a seguir sus cambios. Si no ponemos el modificador *myApp*, hará lo mismo pero creando la carpeta con el mismo nombre que el repositorio. También nos extraerá una copia de la última versión (nuestro **Working Directory**).

En éste momento todos los archivos de nuestro directorio se encuentran bajo seguimiento (**tracked**), si añadimos algun archivo nuevo, debemos avisar a *Git* de que lo siga, sino su estado será **untracked** y *Git* no lo tendrá en cuenta en los *commit*.

    $ git add nuevoArchivo

Supongamos que hemos modificado un archivo del repositorio, que estaba en seguimiento (**tracked**), si ejecutamos el comando **git status** nos aparecerá algo así:

    $git status
    #On branch master
    #Changes to be commited:
    #  (use "git reset HEAD <file>..." to unstage)
    #
    #  new file: nuevoArchivo
    #
    #Changes not staged for commit:
    #  (use "git add <file>..." to update what will be committed)
    #
    #  modified: archivoModificado
    #

Bien, aquí vemos que *Git* nos avisa de que por un lado está siguiendo un archivo (nuevoArchivo) pero que aún no ha guardado su instantánea en al base de datos. Y por otro nos alerta de que hay cambios en un archivo en seguimiento que no se encuentran en el **staging area** y por lo tanto en el próximo *commit* no se actualizarán en la base de datos.

Despues de modificar un archivo, debemos añadirlo al **staging area**:

    $git add archivoModificado
    $git status
    #On branch master
    #Changes to be commited:
    #  (use "git reset HEAD <file>..." to unstage)
    #
    #  new file: nuevoArchivo
    #  modified: archivoModificado
    #

Ahora vemos como al ejecutar el **git status** se encuentran los dos archivos preparados para actualizar la base de datos.

En éste momento quiero recordar lo que decíamos más arriba en cuanto al *commit*, cuando hacemos un *commit* guardamos una instantánea del archivo en el momento en el que se añadió a la **staging area**, ***NO*** del estado actual del archivo. De ésta forma si modificamos de nuevo *archivoModificado* y ejecutamos *status* obtendremos lo siguiente:

    $git status
    #On branch master
    #Changes to be commited:
    #  (use "git reset HEAD <file>..." to unstage)
    #
    #  new file: nuevoArchivo
    #  modified: archivoModificado
    #
    #Changes not staged for commit:
    #  (use "git add <file>..." to update what will be committed)
    #
    #  modified: archivoModificado
    #

Para resolverlo deberemos hacer otra vez:

    $git add archivoModificado    

Ahora lo más importante de *Git*, vamos a confirmar nuestros cambios añadiendo el modificador **-m** para comentar la actualización, nos mostrará un resumen de lo que ha añadido a la base de datos, como el famoso ***checksum***, el número de archivos modificados, insertados o borrados:

    $ git commit -m "Comentario sobre las actualizaciones de éste commit"
    [master]: created 463dc4f: "Fix benchmarks for speed"
    2 files changed, 3 insertions(+), 0 deletions(-)
    create mode 100644 README

Por último lo más seguro es que nos encontremos en la necesidad de borrar archivos de nuestro repositorio, bien porque ya no los usaremos o porque hemos intentado añadir algo al proyecto que no nos interesa ni siquiera que quede registrado. Para ello debemos primero eliminar el archivo del seguimiento y del directorio, de la manera siguiente:

    $git rm myApp.archivo
    rm myApp.archivo

Si por ejemplo sólo borramos el archivo del directorio, al hacer **git status** nos saldrá un aviso del tipo **"Changes to be commited"**.

***

Con ésto creo que ya podemos empezar a unsar *Git* con algo de conocimiento, espero que os sirva de ayuda.

Un saludo...
