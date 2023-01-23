# 07-javascript-engine
En este repoitorio se trabajará con JavaScript engine V8 y el navegador

### JavaScript Engine
> Motor de JavaScript:
Este funciona como un interprete de JavaScript, este estará en el navegador,
y realmente este es el que se encarga de cojer todo lo que esta escrito en
JavaScript y lo traduce o interpreta a un lenguaje el cual la computadora 
pueda entender. Este proceso se le conoce como **Just in Time Compiler** el
cual hace referencia al proceso en que el motor v8 transforma código JavaScript
en Machine Code.

### Qué es V8?
> V8 es el motor de JavaScript que corre en el navegador de **Chrome**. Este 
motor nacio para que la aplicación Google Maps corriera más rapido. V8 ayuda a
que JavaScript corra de manera más rápida, con este se puede crear aplicaciones
más robustas y rápidas.

### Profundizando en el Engine
Una vez que se ejecuta un archivo en el navegador, **el motor de JavaScript genera un entorno global**.
El entorno global hace tres cosas importantes:
> - Genera un **objeto global** llamado `window`.
> - Genera un **contexto** llamado `this`. En un contexto global `this` es igual a `window`.
> - **Ambiente de ejecución**.

Después de generar el entorno global, comienza el **contexto de ejecución** *(Execution context)* 
**donde corre el código de JavaScript utilizando un *Stack de tareas***, aplicándolas una por una,
en la cuál la última tarea añadida será la primera en ejecutarse.

Una vez que el motor de JavaScript está interactuando con el navegador, realiza los siguientes procesos:
- **Parser**: genera un parseo del documento completo mediante palabras claves.
- **AST**: Se crea a partirde los nodos que genera el *parser*. Es una estructura de árbol que representa
el código sintácticamente. Puedes utilizar la página **[AST Explores](https://astexplorer.net/)** para ver
cómo funciona.
- **Intérprete**: El intérprete recorre el AST y ***genera Bytecode*** (lenguaje que entiende la computadora
y no es binario) basado en la información que contiene. Sin embargo, el intérprete detecta que puede optimizar
el código, no genera *Bytecode*, sino que genera un proceso de optimización que consiste en el *profiler y*
*compiler*.
- **Profiler y compilr**: El *profiler* monitorea y mira el código para optimizarlo. El *compiler* optimiza
ese código y genera *machine code* (lenguaje binario). En esta etapa, por la intención de optimizar el
código, también genera errores como el *Hoisting*.
 
 ![](https://static.platzi.com/media/user_upload/bytecode-machine-code-dc786db8-d04e-488b-b96b-e9b385fdb33d.jpg)

### Memory Heap
El comportamiento de JS es sincrono, es decir, solo puede **ejecutar una tarea a la vez**. Esto puede
ser de beneficio o perjudicial dependiendo el caso. Por ende, para ejecutar cada tarea, **JavaScript**
se organiza en dos estructuras de datos: el *Memory Heap* y el *Call Stack*.
**Qué es Menory Heap**
El *Memory Heap* **consiste en una manera desorganizada o aleatoria de guardar la información**, ya sea
valores, funciones, entre otros.

**Qué es Call Stack**
El *Call Stack* consiste en ordenar las funciones que son invocadas de arriba hacia abajo, donde 
**la última tarea será la que se ejecute primero**. Una vez se ha guardado la información del archivo 
o programa, es momento de ejecutarlas.

- Primeramente, guarda todas las funciones o declaraciones en *anonymous* que representa el objeto global

![](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/engine-js04.PNG)

- Y así sucesivamente. Va agregando y quitando ejecuciones en el orden correspondiente. Es por eso que 
JavaScript realiza una tarea a la vez.
