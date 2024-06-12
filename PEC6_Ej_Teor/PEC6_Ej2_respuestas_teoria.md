# Registra el servicio correctamente usando el parámetro providedIn, en lavcarpeta PEC6_Ej_Teor crea un documento PEC6_Ej2_respuestas_teoria.md y responde

## ¿Cuál es la diferencia entre definir un servicio usando el decorador @Injectable o @NgModule? 
Ambos métodos son válidos y ofrecen flexibilidad dependiendo de las necesidades específicas de la aplicación. Usar @Injectable con providedIn simplifica la gestión de servicios para la mayoría de los casos, mientras que proporcionar servicios en @NgModule permite un control más fino sobre el ámbito de los servicios.

## ¿Qué otras opciones admiten el decorador @Injectable para la propiedad ProvidedIn? ¿Para qué sirven las otras configuraciones?

El decorador @Injectable en Angular admite varias opciones para la propiedad providedIn. A continuación se describen estas opciones y sus usos:

    'root':Proporciona el servicio en el inyector raíz de la aplicación. Hace que el servicio esté disponible en toda la aplicación, garantizando una única instancia del servicio.
        Ejemplo:

    @Injectable({
      providedIn: 'root'
    })
    export class UserService { }

'any':Proporciona una nueva instancia del servicio en cada módulo que lo carga. Se usa para módulos cargados perezosamente, donde se necesita una instancia separada del servicio para cada módulo.
    Ejemplo:


    @Injectable({
      providedIn: 'any'
    })
    export class UserService { }

'platform': Proporciona el servicio en un inyector compartido por todos los inyectores en la misma plataforma. Es útil cuando se trabaja con múltiples aplicaciones en la misma plataforma y se desea compartir el servicio entre ellas. 
    Ejemplo:


    @Injectable({
      providedIn: 'platform'
    })
    export class UserService { }

Módulo específico:+roporciona el servicio en un módulo específico. Limita el alcance del servicio al módulo en el que se proporciona, útil para servicios que solo deben estar disponibles en un contexto particular.
    Ejemplo:
        @NgModule({
          providers: [UserService]
        })
        export class SomeModule { }

        @Injectable({
          providedIn: SomeModule
        })
        export class UserService { }

