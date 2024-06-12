# Ejercicio 3 – Preguntas teóricas sobre interceptores (1 punto)

# a) ¿Qué son los interceptores?  
Los interceptores en Angular son una característica que nos permite interceptar y transformar las solicitudes HTTP que se envían desde nuestra aplicación antes de que lleguen al servidor y las respuestas HTTP que provienen del servidor antes de que lleguen a nuestra aplicación. Así, podemos llevar a cabo tareas comunes, como agregar encabezados a las solicitudes, manejar errores o realizar transformaciones en las respuestas.

## b) naliza la siguiente cadena de operadores de RxJS, explica cada uno de los pasos que se están desarrollando y explica en qué caso usarías este código: 

1. `startWith(this.searchTerm)`: Este operador agrega un valor inicial al flujo de datos. En este caso, agrega el término de búsqueda inicial `searchTerm` al flujo de datos.

2. `debounceTime(300)`: Este operador espera 300 milisegundos después de que se ha emitido un valor en el flujo de datos antes de permitir que el siguiente valor pase al siguiente operador. Esto ayuda a evitar múltiples solicitudes al servidor si el usuario está escribiendo rápidamente en un campo de búsqueda, ya que solo se realizará una solicitud después de que el usuario haya dejado de escribir durante al menos 300 milisegundos.

3. `distinctUntilChanged()`: Este operador asegura que solo los valores únicos se pasen al siguiente operador y evita que se realicen solicitudes repetidas al servidor si el término de búsqueda no ha cambiado.

4. `merge(this.reloadProductsList)`: Este operador combina el flujo de datos actual con otro flujo de datos `reloadProductsList`. Esto significa que si hay un evento para recargar la lista de productos, se incluirá en el flujo de datos y se activará junto con los eventos de búsqueda.

5. `switchMap((query) => this.wineService.getWine(this.searchTerm))`: Este operador realiza una operación de mapeo y cambio. Toma el valor más reciente del flujo de datos (el término de búsqueda) y lo utiliza para realizar una solicitud HTTP a `this.wineService.getWine(this.searchTerm)`. Si se emite un nuevo término de búsqueda antes de que se complete la solicitud anterior, cancela la solicitud anterior y realiza una nueva solicitud con el término de búsqueda más reciente. Esto evita problemas de concurrencia y garantiza que solo obtengamos resultados relevantes para el término de búsqueda más reciente.

Este código sería útil en un caso de búsqueda en tiempo real, como un campo de búsqueda en una aplicación web donde los usuarios esperan resultados rápidos y relevantes a medida que escriben. La combinación de estos operadores RxJS permite una búsqueda eficiente y receptiva sin sobrecargar el servidor con solicitudes innecesarias.

