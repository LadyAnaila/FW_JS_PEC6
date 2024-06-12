# Ejercicio 1 – Preguntas teóricas sobre servicios Angular (1.5 puntos)

## a) ¿Cuál es la función de los componentes y servicios? (i.e. cuándo se debe utilizar cada uno de ellos). 

Un componente en Angular tiene como finalidad decidir qué datos se muestran y cómo mostrarlos en nuestra interfaz. Relaciona los datos con la interfaz, enlaza los eventos a los métodos y permite la interacción del usuario con la aplicación. Se encuentra en la capa de presentación y debe centrarse únicamente en aspectos relacionados con la presentación de los datos. Los componentes encapsulan tanto la lógica (mediante TypeScript) como la presentación (mediante HTML y CSS), y pueden ser anidados para formar una jerarquía que facilita la organización y la reutilización del código.

Por su parte, un servicio en Angular forma parte de la capa que es común a toda la aplicación, permitiendo su uso en varios componentes. Los servicios son utilizados para recuperar o enviar datos al servidor, encapsular la lógica de la aplicación que no pertenece a un componente y compartir datos entre componentes, independientemente de si están directamente relacionados. Estos servicios ayudan a mantener los componentes enfocados en la presentación de datos al gestionar la lógica de negocio y el procesamiento de datos de manera centralizada.

## b) ¿Qué es la <<inyección de dependencias>>? ¿Para qué sirve el decorador @Injectable?

La **inyección de dependencias** es un concepto en Angular que permite que un componente, que depende de un servicio, no tenga que crear el servicio por sí mismo. En lugar de eso, el servicio se solicita en el constructor del componente y Angular se encarga de proporcionarlo. Esto hace que el código esté desacoplado, ya que el servicio se encarga de su propia lógica y el componente solo lo consume.

La inyección de dependencias en Angular tiene dos partes: el registro de *providers* y la inyección de dependencias. El registro de *providers* define cómo y dónde debe crearse un objeto, mientras que la inyección de dependencias especifica de qué depende un objeto. Todos los elementos de los que un objeto depende (como servicios, directivas y otros elementos) se inyectan en su constructor. Para gestionar esto, Angular construye un árbol de inyectores.

Primero, cada elemento DOM con un componente o directiva recibe un inyector que contiene la instancia del componente, todos los proveedores registrados por el componente y algunos objetos locales (por ejemplo, el elemento DOM). Segundo, al iniciar un NgModule, Angular crea un inyector usando el módulo y los proveedores definidos allí.

El **decorador @Injectable** indica que un servicio puede ser inyectado mediante inyección de dependencias. Primero, el servicio debe ser importado en el componente. Luego, se inyecta en el constructor del componente, permitiendo que los métodos del servicio sean utilizados dentro del componente. 


## c) Explica los siguientes conceptos de la programación reactiva que se usan en RxJS:

Un **Observable** es una representación de una colección de eventos o valores futuros. En términos simples, es una fuente de datos que puede emitir múltiples valores a lo largo del tiempo. Un Observable puede emitir tres tipos de valores:

 * Next: El valor siguiente en la secuencia.
* Error: Una señal de que ocurrió un error, finalizando la secuencia.
* Complete: Una señal de que la secuencia ha terminado correctamente.

Una **Subscription** es una representación de la ejecución de un Observable. Es la manera en que un Observable comienza a emitir valores a los observadores. Al suscribirse a un Observable, se obtiene una Subscription, que se puede usar para cancelar la suscripción y evitar la recepción de futuros valores.

Los **Operators** son funciones puras que permiten manipular y transformar flujos de datos emitidos por un Observable. Se utilizan para combinar, filtrar, mapear, y realizar otras operaciones sobre los datos. Con RxJS tenemos acceso a muchos tipos de operadores, como map, filter, merge, concat, o switchMap.

Un **Subject** es un tipo especial de Observable que permite la emisión de valores a múltiples observadores de forma manual. Los Subjects son multicasting, lo que significa que pueden tener múltiples suscriptores y cada uno recibirá los mismos valores. Los Subjects también pueden actuar como observables y como observadores al mismo tiempo.

Los **Schedulers** controlan la ejecución de tareas en RxJS, permitiendo especificar el contexto en el que las tareas se ejecutarán (por ejemplo, sincronamente, asincronamente, en un loop de animación, etc.). Los Schedulers son útiles para controlar la concurrencia y la planificación de tareas en la programación reactiva.


## ) ¿Cuál es la diferencia entre promesas y observables?
Las promesas retornan un único resultado de una operación asíncrona, mientras que los observables permiten manejar secuencias de valores y eventos a lo largo del tiempo. Si se necesita acceder solo al resultado final de una operación, las promesas son adecuadas, pero si lo que queremos es acceder a los flujos de datos continuos o múltiples eventos, los observables son una mejor opción.

## e) ¿Cuál es la función de la tubería (*pipe*) async?

En Angular, llamamos **tubería (*pipe*) async** a un operador de plantilla que se utiliza para suscribirse automáticamente a un Observable o Promesa y devolver el valor más reciente que ha emitido. Cuando se usa el *pipe* async, Angular maneja la suscripción y la cancelación de la misma cuando el componente se destruye, previniendo posibles fugas de memoria. Esto simplifica el manejo de datos asíncronos en los templates, mejorando la legibilidad y el rendimiento del código.