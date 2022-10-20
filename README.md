# Practica Git
---

**Bienvenido/a** a nuestra practica de *Git&GitHub*, hoy nos descrubiremos conceptos basicos de Git, **¿Que es Git?** **¿Como usarlo?**, y **¿por qué?**. Tambien daremos a conocer practicas esenciales del dia a dia como programador de software con un pequeño proyecto como logro de esta practica.

---
## ¿Que necesitaremos para esta practica?
- Conexión a la pagina web de Github 
- Una Cuenta de Github
- [Terminal Git Bash](https://www.git-scm.com/download/win "Gitbash CLI")
- Un editor de codigo ([Visual Studio Code](https://code.visualstudio.com/download) | [SublimeText](https://www.sublimetext.com/3) | [Vin](https://www.vim.org/download.php))

---

# ¿Que veremos en esta practica?
## Introducción a Git
![Git](public/assets/githubLogo.png)
---
### ¿Qué es Git y Github?
**Git** es un SCV(En español *Sistema que registra los cambios realizados*) distribuido, diseñado por **Linus Torvalds**. **Git** está optimizado de fomra atómica e incremental, pensado en la efieciencia y la confiabilidad del mantenimiento de versiones de aplicaciones.

Es eficiente con archivos de texto plano, ya que los archivos binarios no puede guardar solo los cambios, sino que debe volver a grabar el archivo completo ante cada modificación, lo que hace que incrementa demasiado el tamaño del repositorio.

**Guardar archivos binarios** en el repositorio de **git** es una **mala práctica**. Estos archivos deben guardarse en un CDN.

**[Github](https://www.github.com "Github Home")** puede considerarse como la red social de código para los programadores y en muchos casos es visto como tu ***CV***

Es una plataforma de *desarrollo colaborativo* para alojar proyectos utilizando el sistema de control de versiones **Git**.

---
### Archivos binarios y de texto plano
|Archivos de Texto|Archivos RTF|Archivos de Word|
|-----------------|------------|----------------|
|Texto plano normal y sin nada especial. Lo vemos igual sin importar dónde lo abramos, ya sea con el bloc de notas o con editores de texto avanzados.|Podemos guardar texto con diferentes **tamaños**, **estilos** y **colores**. Pero si lo abrimos desde un editor de código, vamos a ver que es mucho más complejo que solo el **texto plano**. Esto es porque debe guardar todos los **estilos** del texto y, para esto, usa un código especial un poco difícil de entender y muy diferente a los textos con estilos especiales al que estamos acostumbrados.|Podemos guardar **imágenes** y **texto** con diferentes **tamaños**, **estilos** o **colores**. Al abrirlo desde un editor de código podemos ver que es **código binario**, muy difícil de entender y muy diferente al texto al que estamos acostumbrados. Esto es porque Word está optimizado para entender este código especial y representarlo gráficamente.|

>Recuerda que debes habilitar la opción de ver la extensión de los archivos, de lo contrario, solo podrás ver su nombre. La forma de hacerlo en Windows es `Vista > Mostrar u ocultar > Extensiones de nombre de archivo`
---
### Introducción  a la terminal y lineas de comandos
**Diferencias** entre la estructura de archivos de Windows, Mac o Linux.

- La ruta principal en Windows es `C:\`, en UNIX es solo `/`.
- Windows no hace diferencia entre mayúsculas y minúsculas pero UNIX sí.

Recuerda que GitBash usa la ruta `/c` para dirigirse a `C:\` (o `/d` para dirigirse a `D:\`) en Windows. Por lo tanto, la ruta del usuario con el que estás trabajando es `/c/Users/Nombre de tu usuario`

**Comandos básicos en la terminal:**

- **pwd**: Nos muestra la ruta de carpetas en la que te encuentras ahora mismo.
- **mkdir**: Nos permite crear carpetas (por ejemplo, `mkdir Carpeta-Importante`).
- **touch**: Nos permite crear archivos (por ejemplo, `touch archivo.txt`).
- **rm**: Nos permite borrar un archivo o carpeta (por ejemplo, `rm archivo.txt`). Mucho cuidado con este comando, puedes borrar todo tu disco duro.
- **cat**: Ver el contenido de un archivo (por ejemplo, `cat nombre-archivo.txt`).
- **ls**: Nos permite cambiar ver los archivos de la carpeta donde estamos ahora mismo. Podemos usar uno o más argumentos para ver más información sobre estos archivos (los argumentos pueden ser `-` + el nombre del argumento o `` + una sola letra o shortcut por cada argumento).`ls -a`: Mostrar todos los archivos, incluso los ocultos.`ls -l`: Ver todos los archivos como una lista.
- **cd**: Nos permite navegar entre carpetas.`cd /`: Ir a la ruta principal:`cd` o `cd ~`: Ir a la ruta de tu usuario`cd carpeta/subcarpeta`: Navegar a una ruta dentro de la carpeta donde estamos ahora mismo.`cd ..` (`cd` + dos puntos): Regresar una carpeta hacia atrás.Si quieres referirte al directorio en el que te encuentras ahora mismo puedes usar `cd .` (`cd` + un punto).
- **history**: Ver los últimos comandos que ejecutamos y un número especial con el que podemos repetir su ejecución.
- **clear**: Para limpiar la terminal. También podemos usar los atajos de teclado `Ctrl + L` o `Command + L`.

Todos estos comandos tiene una función de autocompletado, o sea, puedes escribir la primera parte y presionar la tecla `Tab` para que la terminal nos muestre todas las posibles carpetas o comandos que podemos ejecutar. Si presionas la tecla `Arriba` puedes ver el último comando que ejecutamos.

Recuerda que podemos descubrir todos los argumentos de un comando con el argumento `--help` (por ejemplo, `cat --help`).

![Comandos](public/assets/comandosLinux.jpeg)

---
## Comandos basicos en Git
---
### Crea un repositorio de Git y haz tu primer commit
*Si quieres ver los archivos ocultos de una carpeta puedes habilitar la opción de `Vista > Mostrar u ocultar > Elementos ocultos` (en Windows) o ejecutar el comando `ls -a`.*

Le indicaremos a Git que queremos crear un nuevo repositorio para utilizar su sistema de control de versiones. Solo debemos posicionarnos en la carpeta raíz de nuestro proyecto y ejecutar el comando **`git init`**.

Recuerda que al ejecutar este comando (y de aquí en adelante) vamos a tener una nueva carpeta oculta llamada `.git` con toda la base de datos con cambios atómicos en nuestro proyecto.

Recuerda que Git está optimizado para trabajar en equipo, por lo tanto, debemos darle un poco de información sobre nosotros. No debemos hacerlo todas las veces que ejecutamos un comando, basta con ejecutar solo una sola vez los siguientes comandos con tu información:

```
git config --global user.email "tu@email.com"
git config --global user.name "Tu Nombre"

```

Existen muchas otras configuraciones de Git que puedes encontrar ejecutando el comando `git config --list` (o solo `git config` para ver una explicación más detallada).
---

### ¿Que es Branch y como funciona?
En **GIT**, una rama es una versión del código del proyecto sobre el que estás trabajando. Estas ramas ayudan a mantener el orden en el control de versiones y manipular el código de forma segura.Por defecto, el proyecto se crea en una rama llamada Master. Cada vez que añades código y guardas los cambios, estás haciendo un commit, que es añadir el nuevo código a una rama. Esto genera nuevas versiones de esta rama o branch, hasta llegar a la versión actual de la rama Master.

Cuando decides hacer experimentos, puedes crear ramas experimentales (usualmente llamadas development), que están basadas en alguna rama master, pero sobre las cuales puedes hacer cambios a tu gusto sin necesidad de afectar directamente al código principal.

En otros casos, si encuentras un bug o error de código en la rama Master (que afecta al proyecto en producción), tendrás que crear una nueva rama (que usualmente se llaman bug fixing o hot fix) para hacer los arreglos necesarios. Cuando los cambios estén listos, los tendrás que fusionar con la rama Master para que los cambios sean aplicados. Para esto, se usa un comando llamado Merge, que mezcla los cambios de la rama que creaste con la rama Master.

**Todos los commits se aplican sobre una rama**. Por defecto, siempre empezamos en la rama master (pero puedes cambiarle el nombre si no te gusta) y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes.

> Crear una nueva rama lo conocemos como Checkout. Unir dos ramas lo conocemos como Merge.

Cuando haces merge de estas ramas con el código principal, su código se fusiona, creando una nueva versión de la rama Master que ya tiene todos los cambios que aplicaste en tus experimentos o arreglos de errores.

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de **Git** para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto.

Solo ten en cuenta que combinar estas ramas (hacer “merge”) puede generar conflictos. Algunos archivos pueden ser diferentes en ambas ramas. **Git** es muy inteligente y puede intentar unir estos cambios automáticamente, pero no siempre funciona. En algunos casos, somos nosotros los que debemos resolver estos conflictos *a mano*.

---
### Analizar cambios en los archivos de tu proyecto con Git
El comando **`git show`** nos muestra los cambios que han existido sobre un archivo y es muy útil para detectar cuándo se produjeron ciertos cambios, qué se rompió y cómo lo podemos solucionar. Pero podemos ser más detallados.

Si queremos ver la diferencia entre una versión y otra, no necesariamente todos los cambios desde la creación del archivo, podemos usar el comando **`git diff commitA commitB`**.

Recuerda que puedes obtener el ID de tus commits con el comando **`git log`**.

---
### Ciclo basico de trabajo en Git
Para iniciar un repositorio, o sea, activar el sistema de control de versiones de Git en tu proyecto, solo debes ejecutar el comando `git init`.

Este comando se encargará de dos cosas: primero, crear una carpeta `.git`, donde se guardará toda la base de datos con cambios atómicos de nuestro proyecto; y segundo, crear un área que conocemos como Staging, que guardará temporalmente nuestros archivos (cuando ejecutemos un comando especial para eso) y nos permitirá, más adelante, guardar estos cambios en el repositorio (también con un comando especial).

**Ciclo de vida o estados de los archivos en Git**:

Cuando trabajamos con Git nuestros archivos pueden vivir y moverse entre 4 diferentes estados (cuando trabajamos con repositorios remotos pueden ser más estados, pero lo estudiaremos más adelante):

- **Archivos Tracked**: son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos `git add` y `git commit`.
- **Archivos Staged**: son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando `git add`, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios, pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando `git commit`.
- **Archivos Unstaged**: entiéndelos como archivos *“Tracked pero Unstaged”*. Son archivos que viven dentro de Git pero no han sido afectados por el comando `git add` ni mucho menos por `git commit`. Git tiene un registro de estos archivos, pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.
- **Archivos Untracked**: son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por `git add`, así que Git no tiene registros de su existencia.Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: staged y untracked. Esto pasa cuando guardas los cambios de un archivo en el área de Staging (con el comando `git add`), pero antes de hacer commit para guardar los cambios en el repositorio haces nuevos cambios que todavía no han sido guardados en el área de Staging (en realidad, todo sigue funcionando igual pero es un poco divertido).

**Comandos para mover archivos entre los estados de Git**:

- **`git status`**: nos permite ver el estado de todos nuestros archivos y carpetas.
- **`git add`**: nos ayuda a mover archivos del Untracked o Unstaged al estado Staged. Podemos usar `git nombre-del-archivo-o-carpeta` para añadir archivos y carpetas individuales o `git add -A` para mover todos los archivos de nuestro proyecto (tanto Untrackeds como unstageds).
- **git reset HEAD**: nos ayuda a sacar archivos del estado Staged para devolverlos a su estado anterior. Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.
- **git commit**: nos ayuda a mover archivos de Unstaged a Tracked. Esta es una ocasión especial, los archivos han sido guardados o actualizados en el repositorio. Git nos pedirá que dejemos un mensaje para recordar los cambios que hicimos y podemos usar el argumento `m` para escribirlo (`git commit -m "mensaje"`).
- **git rm**: este comando necesita alguno de los siguientes argumentos para poder ejecutarse correctamente:`git rm --cached`: Mueve los archivos que le indiquemos al estado Untracked.`git rm --force`: Elimina los archivos de Git y del disco duro. Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

![Ciclo](public/assets/staging.jpeg)

---
### Volver en el ejemplo en nuestro repositorio utilizando `reset` y `checkout`
El comando **`git checkout`** + `ID del commit` nos permite viajar en el tiempo. Podemos volver a cualquier versión anterior de un archivo específico o incluso del proyecto entero. Esta también es la forma de crear ramas y movernos entre ellas.

También hay una forma de hacerlo un poco más “ruda”: usando el comando `git reset`. En este caso, no solo “volvemos en el tiempo”, sino que borramos los cambios que hicimos después de este commit.

Hay dos formas de usar `git reset`: con el argumento `--hard`, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). O, un poco más seguro, con el argumento `--soft`, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.

---
---